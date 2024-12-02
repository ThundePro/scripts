# Шлях для збереження зображення
$wallpaperPath = "$env:USERPROFILE\Desktop\wallpaper.jpg"

# URL зображення
$imageUrl = "https://armyinform.com.ua/wp-content/uploads/2022/02/7f385fb6add8ffd597017be7260e83d8.jpg"

# Завантаження зображення
Invoke-WebRequest -Uri $imageUrl -OutFile $wallpaperPath

# Встановлення зображення як шпалер
Add-Type -TypeDefinition @'
using System;
using System.Runtime.InteropServices;
public class Wallpaper {
    [DllImport("user32.dll", CharSet = CharSet.Auto)]
    public static extern int SystemParametersInfo(int uAction, int uParam, string lpvParam, int fuWinIni);
    public static void SetWallpaper(string path) {
        const int SPI_SETDESKWALLPAPER = 20;
        const int SPIF_UPDATEINIFILE = 0x01;
        const int SPIF_SENDWININICHANGE = 0x02;
        SystemParametersInfo(SPI_SETDESKWALLPAPER, 0, path, SPIF_UPDATEINIFILE | SPIF_SENDWININICHANGE);
    }
}
'@ -Language CSharp
[Wallpaper]::SetWallpaper($wallpaperPath)
