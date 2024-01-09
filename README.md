## Submitting Patches ##
Our project is open source, and patches are always welcome!
You can send patches by using:

Pull request, right here on git.

Contact us at https://rebrand.ly/teamwin-recovery-zulip-community

## Maintaining Authorship ##
Maintaining authorship is a very important aspect of working with Open Source code. If you wish to submit a patch/fix
from anywhere else (another ROM, project, etc.), it is imperative that you maintain the ownership of the person whose
work you are seeking to include. Doing so will ensure that credit is given where it is deserved, and
the [principles of open source](http://opensource.org/docs/osd)
are upheld. Your contribution to the project will still be recognized as you will forever be listed as the committer.

If you manually cherry pick a patch/fix then you will need to add the original author prior to pushing to
our [gerrit](https://gerrit.twrp.me). This is a very easy task to perform, and is usually done after you commit a
patch/fix locally. This is accomplished after you type in `git commit -a` , type in the commit message and save. You
would then do the following:

```bash
git commit --amend --author "Author <email@address.com>"
```

So it should look like this once you get all of the author's information:

```bash
git commit --amend --author "Spencer McGillicuddy <spencer.the.bestest@gmail.com>"
```

Alternatively, adding as part of the original `git commit` message is preferred and done like the following:

```bash
git commit --author="Author <email@address.com>" -m "[commit message]"
```

This saves time, and when part of your normal routine, prevents the infamous "ermahgerd I forgot to add authorship - let
me fix it because I was found out!" message.


## Getting Started ##
To get started with AOSP sources to build TWRP, you'll need to get familiar
with [Git and Repo](https://source.android.com/source/using-repo.html).

To initialize your local repository using the AOSP trees to build TWRP, use a command like this:

    repo init -u https://github.com/minimal-manifest-twrp/platform_manifest_twrp_aosp.git -b twrp-12.1

To initialize a shallow clone, which will save even more space, use a command like this:

    repo init --depth=1 -u https://github.com/minimal-manifest-twrp/platform_manifest_twrp_aosp.git -b twrp-12.1

Then to sync up:

    repo sync

Then to setup the build:

     cd <source-dir>; export ALLOW_MISSING_DEPENDENCIES=true; . build/envsetup.sh; lunch twrp_<device>-eng

The build target is dependent on the device, and should reflect the location of stock recovery on the device. Issue the build command that applies to your device:
- Recovery partition: `mka recoveryimage`
- Boot image ramdisk: `mka bootimage`
- Vendor_boot image ramdisk: `mka vendorbootimage`

### Special Notes for this branch
- Device makefile in the device tree and dependencies file should use the "twrp" prefix.
- FDE decryption is not presently supported in this branch.
