# mediainfo-nighly-nightly.yazi (DEPRECATED)

## DEPRECATED using mediainfo instead:

> [!IMPORTANT]
> I won't update this repo anymore, so switch back to the stable version.
> From now on, I will make it compatible with both the stable and nightly versions.
> Use this repo: https://github.com/boydaihungst/mediainfo.yazi

<!--toc:start-->

- [mediainfo-nighly.yazi](#mediainfo-yazi)
  - [Installation](#installation)
  <!--toc:end-->

This is a Yazi plugin for previewing media files. The preview shows thumbnail
using `ffmpeg` if available and media metadata using `mediainfo`.

> [!IMPORTANT]
> Minimum version: yazi v25.2.7.

## Preview

- Video

![video](assets/2025-02-15-09-15-39.png)

- Audio file with cover
  ![audio_with_cover_picture](assets/2025-02-15-09-14-23.png)

- Images

![image](assets/2025-02-15-16-52-39.png)

- Subtitle

![subrip](assets/2025-02-15-16-51-11.png)

- There are more extensions which are supported by mediainfo.

## Installation

Install the plugin:

> [!IMPORTANT] Replace magick, image, video with mediainfo-nighly:
> `mediainfo-nighly` use video, image, magick plugins behind the scene to render preview image, song cover.
> So you can remove those 3 plugins from `preloaders` and `previewers` sections in `yazi.coml`.

If you have cache problem, run this cmd, and follow the tips: `yazi --clear-cache`

```bash
ya pack -a boydaihungst/mediainfo-nighly
```

Config folder for each OS: https://yazi-rs.github.io/docs/configuration/overview
Create `.../yazi/yazi.toml` and add:

```toml
[plugin]
  prepend_preloaders = [
    # Replace magick, image, video with mediainfo-nighly
    { mime = "{audio,video,image}/*", run = "mediainfo-nighly" },
    { mime = "application/subrip", run = "mediainfo-nighly" },
  ]
  prepend_previewers = [
    # Replace magick, image, video with mediainfo-nighly
    { mime = "{audio,video,image}/*", run = "mediainfo-nighly"},
  ]
```
