# ScreenMakerAPI

ScreenMakerAPI allows you to easily create custom screens with sprites for mods and pb scripts

![ScreenMakerAPI](https://github.com/Norax64/ScreenMakerAPI/blob/main/Images/ScreenMakerAPI.jpg)

## Getting started

```C#
using Sandbox.Game.GameSystems.TextSurfaceScripts;
using System;
using VRage.Game.ModAPI;
using VRageMath;
using ScreenMakerAPI;

namespace ExampleScreenMakerAPI
{
    [MyTextSurfaceScript("ScreenMakerAPI", "ScreenMakerAPI")]
    public class TSS_ScreenMakerAPI : MyTextSurfaceScriptBase
    {
        private readonly ScreenMakerAPI m_screen;
        
        public TSS_ScreenMakerAPI(IMyTextSurface surface, IMyCubeBlock block, Vector2 size) : base(surface, block, size)
        {
            m_screen = new ScreenMakerAPI(surface);
        }
        public override ScriptUpdate NeedsUpdate => ScriptUpdate.Update100;
        public override void Dispose() => base.Dispose();
        public override void Run()
        {
            try
            {
                m_screen.ShowGrid();
                m_screen.AddText("Hello Word !", new Vector2(0.5f, 0.5f), 1.0f, TextAlignment.CENTER, "White", new Color(120, 120, 120));
                m_screen.Dispose();
            }
            catch
            {
                MyAPIGateway.Utilities.ShowMessage("ScreenMakerAPI", e.Message);
            }
        }
    }
}
```

***

### AddText

<details>

<summary>Show</summary>

`AddText(text, pos, size, align, fontId, color1, color2, ratio)`

`string text` custom text

`Vector2 pos` position on screen (ratio between 0 to 1 or pixel)

`float size` text size

`string fontId` font Id

`TextAlignment align` alignment

`Color color1` Primary color

`Color color2` Secondary color

`float ratio` ratio between 0 to 1 to calc color with color1 and color2

```C#
AddText("Hello Word !", new Vector2(0.5f, 0.5f), 1.0f, TextAlignment.CENTER, "White", new Color(255, 0, 0), new Color(0, 255, 0), 0.5f);
```

</details>

### AddTexture

<details>

<summary>Show</summary>

`AddTexture(sprite, pos, size, align, orient, color1, color2, ratio, preserveTextureRatio, testSprite)`

`string sprite` texture name

`Vector2 pos` position on screen (ratio between 0 to 1 or pixel)

`Vector2 size` size on screen (ratio between 0 to 1 or pixel)

`float orient` orientation in degre

`TextAlignment align` alignment

`Color color1` Primary color

`Color color2` Secondary color

`float ratio` ratio between 0 to 1 to calc color with color1 and color2

`bool preserveTextureRatio` true if screen width is greater than height

`bool testSprite` true if you want to raise an exception if the sprite does not exist

```C#
AddTexture("", new Vector2(0.5f, 0.5f), new Vector2(0.5f, 0.5f);
```

</details>

### AddFrame

<details>

<summary>Show</summary>

`AddFrame(pos, size, align, color1, color2, ratio, background)`

`Vector2 pos` position on screen (ratio between 0 to 1 or pixel)

`Vector2 size` size on screen (ratio between 0 to 1 or pixel)

`TextAlignment align` alignment

`Color color1` Primary color

`Color color2` Secondary color

`float ratio` ratio between 0 to 1 to calc color with color1 and color2

`bool background` transparent background linked to the defined color

```C#
AddFrame(new Vector2(0.5f, 0.5f), new Vector2(0.5f, 0.5f), new Color(0, 100, 220), true);
```

</details>

### AddProgressBar

<details>

<summary>Show</summary>

`AddProgressBar(pos, size, align, gradient, tiles color1, color2, ratio, bordercol, backcol)`

`Vector2 pos` position on screen (ratio between 0 to 1 or pixel)

`Vector2 size` size on screen (ratio between 0 to 1 or pixel)

`TextAlignment align` alignment

`bool gradient` false = simple colored bar, true = gradient color bar

`int tiles` number of tiles for gradient

`Color color1` Primary color

`Color color2` Secondary color

`float ratio` ratio between 0 to 1 to calc color with color1 and color2

`Color bordercol` add colored frame

`Color backcol` add colored background

```C#
AddProgressBar(new Vector2(0.5f, 0.5f), new Vector2(0.8f, 0.05f), new Color(255, 0, 0), new Color(0, 255, 0), 1.0f, bordercol: new Color(0, 100, 220));
```

</details>

### AddGraph

<details>

<summary>Show</summary>

`AddGraphBar(pos, size, values, align, color1, bordercol)`

`Vector2 pos` position on screen (ratio between 0 to 1 or pixel)

`Vector2 size` size on screen (ratio between 0 to 1 or pixel)

`List<float> values` ratio list

`TextAlignment align` alignment

`Color color1` graph color

`Color bordercol` add colored frame

```C#
var RatioList = new List<float>() { 0.2f, 0.34f, 0.5f, 0.25f, 0.8f, 0.95f, 0.6f, 0.4f, 0.3f, 0.1f};
AddGraph(new Vector2(0.5f, 0.5f), new Vector2(0.6f, 0.3f), RatioList, Color.White, bordercol: new Color(0, 100, 220));
```

</details>
