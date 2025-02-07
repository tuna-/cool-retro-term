# cool-retro-term

cool-retro-term is a terminal emulator which mimics the look and feel of the old cathode tube screens. [Upstream](https://github.com/Swordfish90/cool-retro-term)

Since the upstream has not update in years, there is no binary for Apple Silicon (arm64) Macs. **This fork is to provide a binary for Apple Silicon Macs, built directly from the source code using GitHub Actions.** [Background](https://github.com/Swordfish90/cool-retro-term/issues/656#issuecomment-2560849246)

## Installing

If you want a ready-to-use binary, you can download it from the [Releases Page](https://github.com/charlie0129/cool-retro-term/releases). Download the dmg and drag `cool-retro-term.app` to your `Applications` folder.

<img width="945" alt="image" src="https://github.com/user-attachments/assets/6b175dc1-6188-4f39-aee4-ac69ed8a7bef" />

If necessary, *right-click* (*control-click*) `cool-retro-term.app` and select *Open* to bypass the security warning.

> [!NOTE]
> Remove quarantine if you cannot open the app even if you *right-click-open*'d it: `sudo xattr -r -d com.apple.quarantine /Applications/cool-retro-term.app`

<img width="610" alt="image" src="https://github.com/user-attachments/assets/e9543946-e414-43fa-94a5-e12627ecc0ec" />

See it running on a arm64 Mac:

![image](https://github.com/user-attachments/assets/0295ae46-08eb-485c-baa9-5637f810068e)

## Building

If you don't trust the binary I provided, you can fork this repo and let GitHub Actions build it for you. The binary will be uploaded as an artifact to the corresponding job.

After you enable GitHub Actions in your fork, you can use `workflow_dispatch` to trigger the build manually.

<img width="1030" alt="image" src="https://github.com/user-attachments/assets/4e968850-4d4d-4375-9832-7684aea4527a" />

Download the artifact (containing the `.dmg`) from the corresponding job.

<img width="1032" alt="image" src="https://github.com/user-attachments/assets/f1bb3f52-ac99-44f7-9135-ac2cbd64d5dc" />

