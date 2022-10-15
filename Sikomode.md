# Sikomode challenge

## Static

- Exec type : PE x64

- SHA256 : `3aca2a08cf296f1845d6171958ef0ffd1c8bdfc3e48bdd34a605cb1f7468213e`
  
  - VirusTotal yield for malware Type : Backdoor

- Sections
  
  - Nothing particular but some offsets are wierd (placement)

- Strings 
  
  - `cdn.altimiter.local/feed?post=` could be C2 address
  
  - `Desktop/cosmo.jpeg`  could be persistence vector
  
  - `toRC4` function ; used to secure communications ?
  
  - `genKeyStream` function : used to generate the key for RC4 communications ? 
  
  - Weird string only number ; perfect distribution
  
  - Wierd string XML file describing file ? name is set to `Microsoft.Windows.Common-Controls` and public token `6595b64144ccf1df`
  
  - Libs : 
  
  - ![](/home/gsd/.config/marktext/images/2022-09-11-14-33-00-image.png)

- Cutter 
  
  - Graph
  
  - ![](/home/gsd/.config/marktext/images/2022-09-11-14-40-55-image.png)
  
  - Houdini function is called in every path ; clearing out ?
  
  - Only one path leads to StealStuff function

## Dynamic

- Running the file with nc open on port 8080 opens connection on this domain  `update.ec12-4-109-278-3-ubuntu20-04.local` dynamically generated
