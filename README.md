## Ghidra PS4 Loader by golden

This is a simple module for Ghidra to support loading PlayStation 4 ELF files. 
Builds are available as workflow artifacts in the **Actions** tab. Tagged versions are published as extension ZIPs in the **Releases** tab.

#### Automated builds and releases
The GitHub Actions workflow builds on pushes, pull requests, and manual runs. It uses **Ghidra 9.0.4, Java 11, and Gradle 5.0** to match this loader's legacy Ghidra APIs; the resulting extension is not intended for current Ghidra releases.

To publish a release after the workflow is on GitHub, push a version tag pointing to the commit you want to release:

```sh
git tag v1.0.0
git push origin v1.0.0
```

After a successful build, the workflow creates a GitHub Release with generated notes and attaches the ZIP from `dist`. Re-running a tag build replaces the matching asset. Branch builds and manual runs only upload Actions artifacts; they do not publish releases. No additional secrets are required: publishing uses the repository's built-in `GITHUB_TOKEN`.

#### Installation
0. Build with gradle, find the zip file in `dist` folder
1. Extract the zip file to `Ghidra/Extensions`
2. Start Ghidra
3. Drag and drop PlayStation 4 binary into Ghidra (such as a game eboot)
4. Select PlayStation 4 ELF in the Format field
5. Press OK
6. ??
7. Profit.

#### Common Issues
~ If you are missing the `ps4database.xml` file, then the option to load a PlayStation 4 ELF will not show up.  
~ Make sure your ELF is decrypted.  
~ Make sure your ELF does not have the Sony header that is in encrypted ELF files.  

#### TODO
~ I want to add a lot of features. Want to help? Please open an issue with an idea or submit a pull request!  
~ Use StructConverter and show Sony and ELF header structures  
~ Change region name from RAM to something else?  
~ Make it so that imports are valid code, so it doesn't mess with decompiler  

#### Credits
Credits to Z80 and SocraticBliss for general development.  
Major credits to xerpi for his Vita script, aerosoul94 for his dynlib project and database format, and Adubbz for his Switch loader. I was lazy to learn everything about Ghidra from scratch!
