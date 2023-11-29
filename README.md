# Plasma AppImage Integration

Enhance the AppImage user experience on the plasma desktop environment. It's build on top of
AppImageServices and `libappimage` being compatible with other solutions like AppImageLauncher.
 

Features:
- Creation/Removal of launcher entries for application files
- System wide (all users) application installation
- Updates lookup and installation
- Application metada shown in the details view
- Launch assistant to skip the give execution permission step before running an AppImage

## Usage

After installing `plasma-appimage-integration` from sources you will also need to install AppImageServices. 
Instructions are provided in the **Build** section. If you installed it from the binaries provided, AppImageServices 
will be already installed.

As AppImageServices depends on DBus and it runs on user space you must ensure having such feature available on 
your system. Debian, Ubuntu and derivatives user will have to install `dbus-user-session` and restart the system
for it to be enable.

To use this software just open Dolphin (the kde file browser) and you will get AppImage files thumbnails, 
enhanced metadata and file item actions to easily mange your applications.  

## Build
**Dependencies (Fedora 38)**
- cmake (>=3.12)
- extra-cmake-modules
- gcc (>=4.8)
- qt5-qtbase-devel
- kf5-kxmlgui
- kf5-ki18n
- kf5-kio
- kf5-kio-devel
- kf5-ktextwidgets
- kf5-ktextwidgets-devel
- kf5-knotifications-devel
- kf5-kfilemetadata-devel

----------------

Non Fedora

- Qt5::Core
- Qt5::Widgets
- Qt5::Network
- Qt5::DBus
- KF5::XmlGui 
- KF5::I18n 
- KF5::KIO 
- KF5::TextWidgets
- KF5::Notifications
- KF5::FileMetaData

```bash
git clone https://github.com/zzahkaboom24/plasma-appimage-integration
cd plasma-appimage-integration
mkdir build
cd build
cmake -DCMAKE_INSTALL_PREFIX=`kf5-config --prefix` ..
make -j`nproc`
sudo make install

# Install AppImage Services
cd ..
cd required-appimage
chmod +x appimage-services.AppImage
./appimage-services.AppImage self-install
```
