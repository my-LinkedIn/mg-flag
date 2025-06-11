# mg-flag
Madagascar National Flag

```D
import std.stdio;
import std.file;

void main()
{
    // Flag of Madagascar: vertical white (left), and right half split horizontally (top red, bottom green)
    enum width = 1920;
    enum height = 1080;

    auto file = File("pic.ppm", "wb");
    file.write("P6\n", width, " ", height, "\n255\n");

    foreach (i; 0 .. height) {
        foreach (j; 0 .. width) {
            ubyte[3] pixel;
            if (j < width / 3) {
                // Left 1/3: white
                pixel = [255, 255, 255];
            } else if (i < height / 2) {
                // Right 2/3, top half: red
                pixel = [206, 17, 38];
            } else {
                // Right 2/3, bottom half: green
                pixel = [0, 122, 61];
            }
            file.rawWrite(pixel);
        }
    }
    file.close();
}
```
