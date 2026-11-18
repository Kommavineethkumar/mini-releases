# Mini desktop downloads

Mini brings Notes, Editor, Browser, Terminal, and other mini apps into one desktop workspace. **The first public beta is forthcoming.** The public Releases index is the canonical source for beta packages, signing status, and version-specific installation notes. [View GitHub Releases](https://github.com/Kommavineethkumar/mini-releases/releases).

## Planned desktop builds

| System | Direct distribution |
| --- | --- |
| macOS 13+ on Apple silicon or Intel | Universal disk image. The planned beta is unnotarized, so Gatekeeper may block first launch. |
| Windows 10 or 11 on x64 | Per-user installer. Windows may report an unknown publisher for the planned unsigned build, and SmartScreen may block launch. |
| Linux on x64 | Debian package targeting Ubuntu 24.04 or compatible systems. Requires glibc 2.39+ and the WebKitGTK 4.1 runtime (2.42+). |

## Use Mini on a phone

Keep Mini running on your computer. Open Relay in Mini, choose **Pair another device**, then open the pairing link in your phone’s browser. The workspace runs on the paired computer.

## Verify a release before installing

1. Open the beta’s entry in GitHub Releases. Download your package, `SHA256SUMS`, and its detached signature, `SHA256SUMS.minisig`, from that entry.
2. Save the [Mini public key file](mini.pub) as `mini.pub`. Use your system’s SHA-256 command below with `mini.pub` as the filename. Its full file digest should be `2fdfe0b47e9cba1ffad73362ec8e612a3cef487f87b1928b75299ecf52109659`. Confirm that digest through the maintainer’s separately managed channel before trusting the key.
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
