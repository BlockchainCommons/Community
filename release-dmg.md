# How to Make an Ad-Hoc DMG Release for Mac

###### tags: `how-to`

_To create a DMG for release:_

## Create a Release Archive

1. In Xcode, ensure that the "Archive" sceheme produces a "Release" build configuration by clicking on the app name in the title bar and choosing "Edit Scheme" and then "Archive". (This should be set properly.)

2. Change the target from "My Mac" to "Any Mac".

3. Make sure you have the "Developer ID Application" cert for the team with private key. Someone who already has it will need to export it to you. If that can't be done, have the owner of the Apple account create a new Developer ID Application from a Cert Signing Request that you supply.

4. Choose "Product > Archive" to Archive.

## Notarize Your App

5. Choose "Distribute App" from the "Archives" screen, then use "Custom" [Next] / "Developer ID" for your method of distribution. Choose "Upload" and "Automatically Manage Signing" and (again) "Upload". (This is effectively ad-hoc release for the Mac: it doesn't go through the app store.)

_If the Upload works, great, you should wait around a bit, and then your copy of the app you should be notarized. After you've been alerted that your app is notarized, choose "Distribute > Copy App" from the Organizer. Double-check the name as noted in 8a. Then skip to step 11._

_But Apple's upload functions for notarization and for submission of Apple apps have been flaky for years. If it doesn't upload, instead follow the following steps, 6-10:_

6. "Export" your archive. (You can do this from the failed Upload screen, or you can just cut out the middle-man by choosing "Distribute App > Copy App" instead of attempting the constantly failing "Upload" at all, but if you do the latter, you'll need to create a zip of the app by hand before  you go to step 9, so maybe it's better to just go through the failed-upload process.)

### One-Time: Setup an App-Specific Password

7. On a one-time basis, setup a 2FA password in your keychain to allow command-line running of the notarization tools:

7a. Generate a 2FA "app-specific password" for notarytool from the accountid Apple site:
https://appleid.apple.com/account/manage

Make sure to mark it down, because you won't be able to look it up again.

7b. Enter that app-specific password into your keychain:
```
$ xcrun notarytool store-credentials "AC_PASSWORD" --apple-id "<apple-ID>" --team-id <YZHG975W3A for BCC or your team-id> --password <2fa_pass_from_apple>
```
7c. As noted, this is one time. Once you've got all this setup, you won't have to repeat step 7 on future distributions.

### Continue with Notarization

8. "cd" to your archive directory.

8a. At this time, you should probably make sure you're happy with the app name. It should be an app name with spaces, such as "Gordian Server". It should not have a version number. It should stay consistent across versions.

9. Run notary tool on the ZIP file found in the archive directory, using the credential you added to your keychain:
```
$ xcrun notarytool submit <your-app.zip>  --keychain-profile "AC_PASSWORD" --wait --webhook "https://example.com/notarization"
```

10. When it completes, staple your authorization to the `app` (not the `zip`).

```
$ xcrun stapler staple <your-app.app/>
```

### Create Your DMG

The `create-dmg` program is the easiest way to make an attractive DMG that is sized correctly.

11. If you haven't already, install `create-dmg` with Brew:
```
$ brew install create-dmg
```

12. Use a command like the following to create your DMG:
```
$ create-dmg --volname "Gordian Server 1.0.1" --background  ~/Dropbox/Blockchain\ Commons/Images/DMGs/drag.jpg --window-pos 200 120 --window-size 640 480 --icon-size 100 --icon "Gordian Server.app" 50 100 --hide-extension "Gordian Server.app" --app-drop-link 400 100 gordian-server-1.0.0.dmg ~/Desktop/Gordian\ Release/
```
Adjust for the name of your App, the name of your DMG, and the name of your background image. You might potentially need to fiddle with the app position and the `app-drop-link` position, after you see what it looks like.

12a. Again, check on names. The name of the DMG should be a hyphen separated versioned variant of the name, e.g., gordian-server-1.0.0.dmg. The image it opens should similarly be versioned, but with spaces, e.g., "Gordian Server 1.0.0".

### Sign & Checksum

13. Sign your DMG
```
$ gpg --sign --armor --detach-sig <your-app.dmg>
```
You'll need to change the DMG name as appropriate.

Who signs? Right now the Release Manager and the Organization Owner are signing. If there's more than one signature, rename them: `your-app.user.pubkey.dmg.asc`.

14. Checksum your DMG
```
$ shasum <your-app.dmg> > SHA256SUMS
```
You'll need to change the DMG name as appropriate.

15. Sign your Checksum
```
gpg --sign --armor --detach-sig SHA256SUMS 
```

16. Check your Signatures
```
$ gpg --verify <your-app.dmg.asc> <your-app.dmg>
gpg: error reading symlink '/proc/curproc/file': No such file or directory
gpg: Signature made Wed Oct 27 09:31:57 2021 HST
gpg:                using RSA key A4889A09F9819D8C054004507EC6B928606F27AD
gpg: Good signature from "Shannon Appelcline <shannon.appelcline@gmail.com>" [ultimate]

$ gpg --verify SHA256SUMS.asc SHA256SUMS
gpg: error reading symlink '/proc/curproc/file': No such file or directory
gpg: Signature made Wed Oct 27 09:34:57 2021 HST
gpg:                using RSA key A4889A09F9819D8C054004507EC6B928606F27AD
gpg: Good signature from "Shannon Appelcline <shannon.appelcline@gmail.com>" [ultimate]
```
### Signing Alternative

If you are signing with an SSH key instead of a GPG key, the process looks more like this:
```
$ ssh-keygen -Y sign -n file -f ~/.ssh/sign_id_ed25519-DragonBook.local-ShannonA-2024-01-31@github SHA256SUMS
$ mv SHA256SUMS.sig SHA256SUMS.shannona.ssh-1oCAdW5UY7LtbO723rCxI3YqfFDWf2SqJpu6EebgaKM.sig
```
It can then be checked as follows:
```
$ cat SHA256SUMS | ssh-keygen -Y check-novalidate -n file -f ~/.ssh/sign_id_ed25519-DragonBook.local-ShannonA-2024-01-31@github.pub -s SHA256SUMS.shannona.ssh-1oCAdW5UY7LtbO723rCxI3YqfFDWf2SqJpu6EebgaKM.sig
```

### New Release Test

17a. Test Out Creating a tag by hand

```
git tag -s v1.1.1
```

Test it with:

```
git tag -v v1.1.1
```

If it works, `git push` and then grab the tag when you do the release in #17, below.

### Create the Release & Upload

17. Create a new release on the releases page for your repo

For example:
```
https://github.com/BlockchainCommons/GordianServer-macOS/releases
```

18. Be sure to "Choose a Tag", type in the new tag for your release (e.g., "v1.0.0"), and then click "Create New Tag" at the bottom of that pop-up so that it actually gets created.

19. Add your DMG, your DMG signature, the SHASUM, and your SHASUM signature.

When uploading the DMG for the release, be sure to upload the DMG file, *not* the opened Disk Image.

20. Announce the release!
