# アプリケーションのインストール

あなたはNyarch Linuxにおいて複数のアプリケーションインストール方法を選択することが可能です。これを「パッケージングフォーマット」と呼びます。
このページでは、パッケージ形式の違いとそれらのインストールおよび管理方法について説明しています。

サポートされているパッケージ:

1. [Arch Linux Packages](#arch-linux-packages) (pacman, .tar.zst)
2. [Flatpaks](#flatpaks) (Store, .flatpakref, .flatpak)
3. [AppImages](#appimages) (.appimage)
4. [Arch User Repository](#arch-user-repository) (yay & paru)

## Arch Linux Packages 
ほぼすべての Linux ディストリビューションにはパッケージマネージャーがあり、コンピュータ上のパッケージのインストール、削除、更新を支援します。

Arch Linux では、パッケージマネージャは `pacman`です。

様々な理由により、pacmanはターミナル経由及び管理者権限でのみ使用する必要があります。

以下は `pacman` の基本的な使い方です。より詳細な手順をご希望の場合は、[pacman on the Arch Wiki](https://wiki.archlinux.org/title/Pacman )をご確認ください。

### パッケージのインストール方法
```bash
sudo pacman -S package
```
例として、`firefox`をインストールしたい場合、このように入力します
```bash
sudo pacman -S firefox
```

### パッケージを削除する方法
```bash
sudo pacman -R package
```
依存関係も削除したい場合は、`-Rns` を使用できます。

### すべてのパッケージを更新する方法
```bash
sudo pacman -Syu
```
### パッケージの検索方法
```bash
sudo pacman -Ss package
```

## Flatpaks
Flatpak は、**sandboxed** 環境でアプリケーションをインストールできる特別なパッケージングフォーマットです。

これは、スマートフォンで行うように、アプリケーションが持っている権限を簡単に管理できることを意味します。

フラットパックにはいくつかの長所と短所があります。

- 利点：
- すべてのLinuxディストリビューションで動作します
- 権限を管理できます
- ストアから簡単にインストールできます
- 管理者権限なしでアプリケーションをインストールできます
- 欠点：
- ネイティブパッケージに比べて、より多くのディスク容量を占有します。
- サンドボックス内で実行できないソフトウェアに対して、時々問題が生じます。
- ターミナルプログラムで使用する場合、しばしば追加の手順が必要です。
  
### Flatpakはいつインストールすべきですか？
- ソフトウェアが主にFlatpakとして実行されることになっている場合（例：Bottles）
- 信頼できないソフトウェアをインストールする場合（その権限を管理できます）
- GTK/Gnome アプリケーションの場合（Nyarch がランタイムを出荷し、インストールが速いため）
- ソフトウェアが端末で実行されない場合
### Flatpakを使用したインストール
#### Gnome Software
**Gnome Software** を使用して、flatpak アプリケーションを検索、インストール、アンインストール、更新できます。

![immagine](https://github.com/user-attachments/assets/34132dbc-f032-475b-90f9-1eec75f1eabd )
![immagine](https://github.com/user-attachments/assets/e2da8b38-7de6-44d3-a045-7a1b5fd4291a )
#### Flathubからアプリケーションをインストールする
Flatpakは[Flathub](https://flathub.org/)で見つけることができます。そこからアプリケーションをインストールすると、ブラウザが `.flatpakref` ファイルをダウンロードします。これをクリックすると、Gnome Software でアプリケーションが開きます。

**Note**: Flathub のすべてのアプリケーションは Gnome Software にもインストールされています。
#### コマンドライン
```bash
flatpak install application.id
```
例えば、Flatpak を使用して Firefox をインストールする場合
```bash
flatpak install org.mozilla.firefox
```
コマンドラインを使用すれば、`.flatpak` ファイルもインストールできます。
このように実行してください。
```bash
flatpak install file.flatpak
```

また、`.flatpak` ファイルをダブルクリックすると、Gnome Software が開き、インストールできます。

### Flatpak の権限管理
Flatseal を使用して、Flatpak の権限を管理できます。


## Appimages
**Appimages** は、すべての Linux ディストリビューションで実行できる特別なフォーマットです。

- 利点：
- すべてのLinuxディストリビューションで動作します。
- 欠点：
- 他のアプリケーションとライブラリを共有しません。
- 一般的に遅いです。
- 多くの場合、テーミングをサポートしていません。

他に利用可能なパッケージング形式がある場合、一般的にappimagesの使用は推奨されません。
**代替手段がない場合にのみ**、appimages を使用してください。
### Installing and managing Appimages
After downloading an appimage, you can double-click on it and it will launch **GearLever**.

GearLever is a simple software that helps you install and uninstall appimages. 
You can choose to run the appimage once without installing or add it to the app menu.

#### Running appimages from command line
You can also straight up run an appimage from the command line by:
1. Giving it the permission to be executed
```bash
chmod +x application.appimage
```
2. Running it
```bash
./application.appimage
```

## Arch User Repository
The [AUR](https://aur.archlinux.org/ ) (Arch User Repository) is a big community-driven store for packages that aren't officially supported by Arch Linux. **If an application exists, it's very likely that you will find it in the AUR.**

Nyarch Linux is fully compatible with the AUR, since it uses default Arch Linux repositories.

**Warning**: The packages on the AUR are uploaded by users, so they might not be safe. It's suggested to always check if they are trustable from the package builds.

### Installing a package
To install an AUR package, you need an [AUR Helper](https://wiki.archlinux.org/title/AUR_helpers ).

By default, Nyarch Linux ships `yay` as the default AUR helper. (Or `nyay` because lol nya)

To install an AUR package, you can run
```bash
yay -S package
```
For example,
```bash
yay -S zen-browser-bin
```

##### Updating packages
```bash
yay
```
Updates all packages from the AUR

### Using paru
`paru` is a feature-rich AUR helper written in Rust, the successor to `yay`, providing safer defaults and more active maintenance.

To install `paru`, you can run:
```bash
sudo pacman -S --needed base-devel git
git clone https://aur.archlinux.org/paru.git 
cd paru
makepkg -si
```

##### Installing packages with paru
`paru` uses syntax similar to `pacman`, making it easy to pick up.

To install an AUR package, you can run:
```bash
paru -S package
```
For example,
```bash
paru -S chrome
```

##### Updating packages
```bash
paru
```
or
```bash
paru -Syu
```
This updates all packages from both official repositories and the AUR.

##### paru tips
- **Exit review**: Press q to exit during review
- **View PKGBUILD**: `paru -Gp package` lets you view the package build script before installation
- **View AUR comments**: `paru -Gc package` lets you view comments from other users about the package
- **Interactive search**: Running `paru searchterm` directly lets you search interactively and select for installation
- **Skip review**: `paru -S package --skipreview` (not recommended for untrusted packages)

### Guide to Package names
You might encounter multiple packages for the same program. This is an example for Vesktop:
![immagine](https://github.com/user-attachments/assets/e38667d5-a46a-4d39-8205-ad3ee276d90b )

Based on the suffix:

- `-git`: This package is built from the latest code in the Git repository. It might not be stable, but you'll get the latest features and updates. Also, it will **compile the package**

- `-bin`: This package is a binary package, which means it's **pre-compiled** and ready to use. You don't need to build it from source
- If there's no suffix, it usually means that the package is the "release" version. In other words, it's the latest stable version of the software, without any suffixes or prefixes.
```
