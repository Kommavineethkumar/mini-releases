# Mini desktop downloads

[Official download page](https://mini-platform-downloads.web.app/)

Mini brings Notes, Editor, Browser, Terminal, and other mini apps into one desktop workspace. Download **0.1.1-beta.1** for macOS, Windows or Linux, then [verify the package with Minisign](#verify-a-release-before-installing) before opening it. [Release notes and assets](https://github.com/Kommavineethkumar/mini-releases/releases/tag/v0.1.1-beta.1).

## Desktop downloads

| System | Packages and requirements |
| --- | --- |
| macOS 13+ on Apple silicon or Intel | [Universal .dmg](https://github.com/Kommavineethkumar/mini-releases/releases/download/v0.1.1-beta.1/Mini-0.1.1-beta.1-macos-universal.dmg) · [Universal .zip](https://github.com/Kommavineethkumar/mini-releases/releases/download/v0.1.1-beta.1/Mini-0.1.1-beta.1-macos-universal.zip). Gatekeeper may block first launch because this beta is unnotarized. |
| Windows 10 or 11 on x64 | [Per-user setup](https://github.com/Kommavineethkumar/mini-releases/releases/download/v0.1.1-beta.1/Mini-0.1.1-beta.1-windows-x64-setup.exe) · [Portable ZIP](https://github.com/Kommavineethkumar/mini-releases/releases/download/v0.1.1-beta.1/Mini-0.1.1-beta.1-windows-x64-portable.zip). Windows may report an unknown publisher for these unsigned downloads. The window requires Microsoft WebView2. |
| Linux on x64 | [Get the .deb, AppImage, or tar archive](https://github.com/Kommavineethkumar/mini-releases/releases/tag/v0.1.1-beta.1) from the release assets. All three require glibc 2.39+ and WebKitGTK 4.1 (2.42+) on Ubuntu 24.04 or a compatible system. |

## Use Mini on a phone

Keep Mini running on your computer and keep it online. In Relay, choose **Pair another device**. Open the pairing link on your phone or paste it into [Mini Relay](https://mini-relay.web.app/). The workspace runs on the paired computer.

## Verify a release before installing

1. Open the [beta release assets](https://github.com/Kommavineethkumar/mini-releases/releases/tag/v0.1.1-beta.1). Download your package, `SHA256SUMS`, and its detached signature, `SHA256SUMS.minisig`, from that entry.
2. Save the [Mini public key file](https://mini-platform-downloads.web.app/mini.pub) as `mini.pub`. Use your system’s SHA-256 command below with `mini.pub` as the filename. Its full file digest should be `2fdfe0b47e9cba1ffad73362ec8e612a3cef487f87b1928b75299ecf52109659`. Confirm that digest through the maintainer’s separately managed channel before trusting the key.
3. With Minisign installed, run the following in the download folder.

   ```sh
   minisign -Vm SHA256SUMS -p mini.pub
   ```

4. After Minisign verifies the signature, compute the SHA-256 digest of the package. Replace `PACKAGE` with its actual filename.

   | System | Command |
   | --- | --- |
   | macOS | `shasum -a 256 "PACKAGE"` |
   | Windows (PowerShell) | `Get-FileHash -Algorithm SHA256 -LiteralPath "PACKAGE"` |
   | Linux | `sha256sum "PACKAGE"` |

5. Match the entire digest to the line for that exact filename in the authenticated list. Install only after both checks pass.

## Support

If a verification file is missing, a check fails, or your system blocks installation, stop and open a public issue. Include the release tag, operating system, package filename, and exact warning. Remove personal details and pairing links before posting. [Mini release issues](https://github.com/Kommavineethkumar/mini-releases/issues).
