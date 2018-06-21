

### Problem

The desktop image must be changed

### Solution

Use a low-level Windows hook to set the background

### Sample Code

(:source lang=C#:)<pre class="escaped">
[DllImport("user32")]
static extern bool SystemParametersInfo(int uiAction, int uiParam, string pvParam, bool fWinIni);
const int SPI_SETDESKWALLPAPER = 0x14;

// in code
// ensure fileName is a bitmap (of the format ImageFormat.Bmp)
SystemParametersInfo(SPI_SETDESKWALLPAPER, 0, fileName, true);
</pre>
