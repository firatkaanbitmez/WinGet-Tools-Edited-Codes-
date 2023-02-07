class Software {
    [string]$Name
    [string]$Id
    [string]$Version
    [string]$Match
	[string]$Source
}

$upgradeResult = winget search vlc | Out-String

$lines = $upgradeResult.Split([Environment]::NewLine)

# Find the line that starts with Name, it contains the header
$fl = 0
while (-not $lines[$fl].StartsWith("Name"))
{
    $fl++
}

# Line $i has the header, we can find char where we find ID and Version
$idStart = $lines[$fl].IndexOf("Id")
$versionStart = $lines[$fl].IndexOf("Version")
$MatchStart = $lines[$fl].IndexOf("Match")
$sourceStart = $lines[$fl].IndexOf("Source")

# Now cycle in real package and split accordingly
$upgradeList = @()
For ($i = $fl + 1; $i -le $lines.Length; $i++) 
{
    $line = $lines[$i]
    if ($line.Length -gt ($SourceStart + 1) -and -not $line.StartsWith('-'))
    {
        $name = $line.Substring(0, $idStart).TrimEnd()
        $id = $line.Substring($idStart, $versionStart - $idStart).TrimEnd()
        $version = $line.Substring($versionStart, $MatchStart - $versionStart).TrimEnd()
        $Match = $line.Substring($MatchStart, $sourceStart - $MatchStart).TrimEnd()		
		$Source = $line.Substring($SourceStart ).TrimEnd()
        $software = [Software]::new()
        $software.Name = $name+",";
        $software.Id = $id+",";
        $software.Version = $version+",";
        $software.Match = $Match+",";
		$software.Source = $Source+",";
        $upgradeList += $software
    }
}

$upgradeList | Format-Table