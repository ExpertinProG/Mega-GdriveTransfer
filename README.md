
# Transfer Files From MEGA to Google Drive

This project provides a Google Colab notebook to transfer files from MEGA to Google Drive using MEGAcmd. It includes steps to install necessary dependencies, mount Google Drive, and transfer files seamlessly.

## Features

- **Direct Transfer**: Move files directly from MEGA to Google Drive.
- **Interactive Widgets**: Monitor the transfer progress interactively.
- **MEGA Pro Account Support**: Sign in to MEGA to avoid transfer quota exceeded errors.

## Getting Started

### Prerequisites

- A Google account to access Google Drive.
- Basic knowledge of Python and Google Colab.

### Installation

1. **Clone the Repository**: Clone this repository to your local machine or open it directly in Google Colab.

2. **Install MEGAcmd**: Run the following commands to install MEGAcmd:
    ```python
    !apt-get -y update
    !apt-get -y install libc-ares2 libmediainfo0v5 libzen0v5
    !curl -sL -o /var/cache/apt/archives/libssl1.1.deb http://archive.ubuntu.com/ubuntu/pool/main/o/openssl/libssl1.1_1.1.1f-1ubuntu2_amd64.deb
    !dpkg -i /var/cache/apt/archives/libssl1.1.deb
    !curl -sL -o /var/cache/apt/archives/MEGAcmd.deb https://mega.nz/linux/MEGAsync/xUbuntu_21.10/amd64/megacmd-xUbuntu_21.10_amd64.deb
    !dpkg -i /var/cache/apt/archives/MEGAcmd.deb
    ```

### Usage

1. **Mount Google Drive**: Mount your Google Drive to save the downloaded files:
    ```python
    from google.colab import drive
    drive.mount('/content/drive', force_remount=True)
    ```

2. **Sign In to MEGA**: If you have a MEGA Pro account, sign in to avoid transfer quota exceeded errors:
    ```python
    EMAIL = "your_mega_email"
    PASSWORD = "your_mega_password"
    !mega-login $EMAIL $PASSWORD
    ```

3. **Transfer Files**: Transfer files from MEGA to Google Drive:
    ```python
    MegaUrl = "your_mega_file_or_folder_link"
    TransferLocationOfGdrive = "/content/drive/My Drive"
    !mega-get $MegaUrl $TransferLocationOfGdrive
    ```

## License

This project is licensed under the MIT License.

---
