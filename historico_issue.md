<h1>Describe the bug</h1>

<b>Auto-boot Failure:</b> When powering on the console with the drive connected, it does not boot into PSBBN automatically. If FMCB is connected, it boots FMCB (requiring me to manually find and launch the PSBBN ELF via wLaunchELF). If no memory card is connected, the console simply boots to the standard unmodded PS2 browser menu.

<b>Black Screen on Boot:</b> When launching any installed game, or even the OPL app listed in the PSBBN interface, the screen goes black, the HDD LED stops blinking entirely, and the console hangs. The OPL app only works if launched completely outside of PSBBN. I managed to successfully boot Need for Speed Most Wanted once, but the very next day, without changing any settings, the black screen issue returned.

<h2>Hardware setup</h2>

<b>Console:</b> PS2 Fat (SCPH-39001);

<b>Modchip:</b> None (Original/Locked console);

<b>Network Adaptor:</b> Original Sony Network Adaptor (modded with SATA board upgrade (Bitfunx));

<b>Storage Tested:</b> 120GB SATA SSD, 250GB 2.5" HDD, and a 500GB 3.5" HDD;

<b>Boot Method:</b> Free McBoot (FMCB) v1.966 on MC1 (Slot 2) or MC0 (Slot 1).

<h2>Software versions</h2>

<b>Project Version:</b> PSBBN Definitive Project v4.2.0;

<b>Disk Format:</b> APA-Jail;

<b>OPL Version:</b> Bundled OPL 1.2.0 Beta (exFAT support) from v4.2.0 release.

<h2>Troubleshooting already performed</h2>

<b>Installation environments:</b> Completely wiped and formatted the drives from scratch, and installed PSBBN on both Windows 11 and Arch Linux. The exact same errors occur regardless of the OS used for installation;

<b>Storage drives:</b> Tested on 3 completely different physical drives (the SSD, the 2.5" HDD, and the 3.5" HDD) with identical failures on all of them;

<b>Memory Card conflicts:</b> Removed the memory card as soon as PSBBN initiates from the SSD (not just before launching a game). This guarantees that PSBBN runs entirely without the memory card inserted to avoid any rogue conf_opl.cfg or FMCB resident patches. The black screen persists;

<b>OPL replacement:</b> Swapped the bundled 10MB OPL ELF in hdd0:/__system/launcher/ with a smaller, known-working 1.1MB OPL ELF from my memory card. The black screen on launch still happens;

<b>Alternative Installers/Launchers:</b> Tried installing games via NHDDL and configuring PSBBN to use a different system/launcher instead of the default OPL. The black screen on game boot persists regardless of the chosen launcher.

<b>NOTE:</b> I strictly followed every step for both the PSBBN installation onto the SSD/HDD and the game installation process, exactly as described in the latest version of this project's README.

<b>Below are all the log files that might be helpful in investigating this issue:</b>

<b>Brief note about the logs:</b> Some of the attached files contain older entries. For instance, the setup.log file shows some installation errors at the beginning that occurred yesterday on my PC, but those issues were already fixed and resolved, as shown towards the end of the log.

[setup.log](https://github.com/user-attachments/files/33358740/setup.log)
[extras.log](https://github.com/user-attachments/files/33358737/extras.log)
[media.log](https://github.com/user-attachments/files/33358741/media.log)
[update.log](https://github.com/user-attachments/files/33358743/update.log)
[game-installer.log](https://github.com/user-attachments/files/33358738/game-installer.log)
[hosdmenu.log](https://github.com/user-attachments/files/33358742/hosdmenu.log)
[PSBBN-installer.log](https://github.com/user-attachments/files/33358739/PSBBN-installer.log)



<h3>CosmicScale (dev)</h3>
You are definitely experiencing a hardware issue. Since you have ruled out the drive, you should shift you focus to the network adapter, SATA mod, and console. Issues like you are describing are usually caused by signal loss.

1. Check the SATA mod. Make sure the ribbon cable is fully inserted and seated correctly.
2. Check that the connectors on the console and network adapter are clean and free of dust and dirt. They can be cleaned with isopropyl alcohol.
3. Ensure the network adapter and drive are securely connected to the console.
4. It could be a dodgy SATA board. Try replacing it.
5. Replace the networks adapter.
6. Replace the console.



<h3>ViniciusPetto</h3>
Hi there, thanks for the quick reply and the troubleshooting suggestions!

I completely understand why this strongly resembles a physical hardware or signal loss issue, but I have concrete evidence that points away from a physical failure.

Before attempting this installation with APA-Jail and v4.2.0, I used this exact same hardware setup (the same PS2, same Original NA, same SATA Mod, and this exact same SSD) formatted in the classic APA standard. I installed two games using HDL Game Installer (one via SMB network and one ripped directly from the disc drive). Both games booted and ran flawlessly using a standard OPL build. I experienced zero black screens, freezes, or read errors.

Just to be absolutely thorough based on your advice, I already double-checked the SATA mod's ribbon cable seating and performed a deep clean on the console and NA connectors using isopropyl alcohol. The physical connectors are firmly secured, both between the SSD and the Network Adapter, and between the Network Adapter and the PS2.

Since the hardware operates perfectly under the classic APA format, but fails exclusively under the PSBBN v4.2.0 (APA-Jail/exFAT) environment regardless of whether I use the bundled OPL or NHDDL as the launcher, it points to a software-level compatibility issue with this specific release's architecture.



<h3>CosmicScale (dev)</h3>
Unfortunately, I don't think there's going to be anything I can do to help. The logs confirm that the install was successful and there are thousands of users running the game installer every week without issues. If the issue isn't hardware related, then the issue is unique to your setup and there's no way for me to troubleshoot that.


<h3>ViniciusPetto</h3>
No problem, I completely understand. Since it seems to be a unique edge case with my setup, I just have two quick final questions before I figure out my next steps:

- Do you know if there are other users successfully running this specific v4.2.0 (APA-Jail) release using Original Network Adapters combined with SATA mods?

- If I remove the SATA mod, reinstall the original IDE board to the Network Adapter, and use a classic IDE HD instead, do you think that would bypass this issue and work correctly?

Thanks again for taking the time to look into the logs and for your help!


<h3>CosmicScale (dev)</h3>
> * Do you know if there are other users successfully running this specific v4.2.0 (APA-Jail) release using Original Network Adapters combined with SATA mods?

Yes, there will be thousands using that exact setup, including me. It is the recommended setup.

> * If I remove the SATA mod, reinstall the original IDE board to the Network Adapter, and use a classic IDE HD instead, do you think that would bypass this issue and work correctly?

You can give it a go. IDE HDDs 40 GB or larger are compatible but they can be a bit hit or miss due to their age. For that reason, the SATA adapter and a SATA drive is recommended.


<h3>ViniciusPetto</h3>
Thanks for the clarification! That’s really good to know. Even though my current setup matches the recommended configuration, I have one last idea I'd like to run by you.

What if I use your project's script exclusively to format the SSD and install the PSBBN interface, but instead of using it to install the games, I use tools like HDL Game Installer or HDL Batch Installer to transfer the games to the drive?

Do you think installing the games through those standard tools could bypass the boot issue when I launch them from PSBBN? Or would those installers conflict with the APA-Jail/exFAT partition structure created by your script?


<h3>CosmicScale (dev)</h3>
Those tools are not compatible with this project. However, you do not need to use the game installer if you do not want to. You can just drag and drop games directly to the exFAT partition and just use OPL. Although, that kinda defeats the point of using this project tbh.


<h3>ViniciusPetto</h3>
Got it, thanks for confirming! I completely agree that just dragging and dropping for OPL defeats the purpose of having the awesome PSBBN interface.

I really appreciate all your time and guidance in helping me troubleshoot this issue. I've decided to fork the repository to dive into the code and tinker with it on my end. I want to test a few modifications to the scripts to see if I can get it to play nicely with my specific setup. It will just be a personal fork for my own testing, so it won't affect anything on the main branch at all.

I'll reach out again in case I discover anything new or make any progress. Should I manage to figure out a software-level fix, I'd love to contribute it back to help make the project even more robust against edge cases. On the other hand, if it ultimately turns out to be a hidden hardware quirk on my end, I'll let you know so we can officially put this to rest without any unnecessary code tweaks.

Thanks again for all the hard work on this amazing project!
