---
title: Optimizing TV series quality in Sonarr using TRaSH guides custom formats
description: A ELI5 guide to using TRaSH guides to optimize your HD (1080P) TV series in ElfHosted
---

The following guide was contributed by @LayeZee, [Elf-venger](/team/#elf-vengers) and Arr-Ninja!

Below you'll find an ELI5 guide to importing the 1080p version of the [TRaSH Guides](https://trash-guides.info/) into your [Sonarr][sonarr] for better compatibility with your devices.

(*This isn't a 1 size fits all but it's close*)

!!! tip "Too complicated? Do it with ElfBot!"
    There's a simpler way, if you don't care to run through the process yourself. See [Sonarr's docs](/app/sonarr/#add-trash-guides) for details!

## Process

Below I'm going to explain like you're 5 and show you how to import custom formats, I have [another guide for Radarr](/guides/media/optimize-movie-quality-with-trash-custom-formats/) showing these steps already, so if you've joined me here from that guide please skip to step 2 where you'll find the JSON codes you came here for, if you've just joined me for Sonarr please read on how to import a custom format JSON code into Sonarr!

First off, load [Sonarr][sonarr] from your Elfhosted dashboard and navigate to your settings page. Once there, click on `Custom Formats` and in the middle of the page you should see a `+` button, click this, you'll then be presented with a page asking you for a JSON code, (don't worry I'll provide the codes) you then paste the code into the box and once done, at the lower right of the screen you press `import` and then `Save`. Then the process begins again, rinse and repeat. `+` > `Import` > `Paste Code` > `Import` > `Save`.

Here are screenshots illustrating the steps:

![](/images/trash-guide-sonarr-1.png)

![](/images/trash-guide-sonarr-2.png)

![](/images/trash-guide-sonarr-3.png)

![](/images/trash-guide-sonarr-4.png)

Now you know how to import a JSON code let's begin!

## Custom Formats

Firstly we're going to create the whole list of custom formats needed for this to work following step 1 import these codes one by one untill you've completed the list.

### Unwanted

#### BR-DISK

??? example "JSON [show/hide]"
    ```json
    {
    "trash_id": "85c61753df5da1fb2aab6f2a47426b09",
    "trash_scores": {
        "default": -10000
    },
    "trash_regex": "https://regex101.com/r/UpA3I7/2",
    "name": "BR-DISK",
    "includeCustomFormatWhenRenaming": false,
    "specifications": [
        {
        "name": "BR-DISK",
        "implementation": "ReleaseTitleSpecification",
        "negate": false,
        "required": true,
        "fields": {
            "value": "^(?!.*\\b((?<!HD[._ -]|HD)DVD|BDRip|720p|MKV|XviD|WMV|d3g|(BD)?REMUX|^(?=.*1080p)(?=.*HEVC)|[xh][-_. ]?26[45]|German.*[DM]L|((?<=\\d{4}).*German.*([DM]L)?)(?=.*\\b(AVC|HEVC|VC[-_. ]?1|MVC|MPEG[-_. ]?2)\\b))\\b)(((?=.*\\b(Blu[-_. ]?ray|BD|HD[-_. ]?DVD)\\b)(?=.*\\b(AVC|HEVC|VC[-_. ]?1|MVC|MPEG[-_. ]?2|BDMV|ISO)\\b))|^((?=.*\\b(((?=.*\\b((.*_)?COMPLETE.*|Dis[ck])\\b)(?=.*(Blu[-_. ]?ray|HD[-_. ]?DVD)))|3D[-_. ]?BD|BR[-_. ]?DISK|Full[-_. ]?Blu[-_. ]?ray|^((?=.*((BD|UHD)[-_. ]?(25|50|66|100|ISO)))))))).*"
        }
        }
    ]
    }
    ```

### LQ

??? example "JSON [show/hide]"
    ```json
    {
    "trash_id": "9c11cd3f07101cdba90a2d81cf0e56b4",
    "trash_scores": {
        "default": -10000
    },
    "name": "LQ",
    "includeCustomFormatWhenRenaming": false,
    "specifications": [
        {
        "name": "BRiNK",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(BRiNK)$"
        }
        },
        {
        "name": "CHX",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(CHX)$"
        }
        },
        {
        "name": "CTFOH",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(CTFOH)$"
        }
        },
        {
        "name": "d3g",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(d3g)$"
        }
        },
        {
        "name": "EVO",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(EVO)$"
        }
        },
        {
        "name": "FGT",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(FGT)$"
        }
        },
        {
        "name": "GHOSTS",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(GHOSTS)$"
        }
        },
        {
        "name": "HiQVE",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(HiQVE)$"
        }
        },
        {
        "name": "iNTENSO",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(iNTENSO)$"
        }
        },
        {
        "name": "iVy",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(iVy)$"
        }
        },
        {
        "name": "JFF",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(JFF)$"
        }
        },
        {
        "name": "MeGusta",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(MeGusta)$"
        }
        },
        {
        "name": "NERO",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(NERO)$"
        }
        },
        {
        "name": "nhanc3",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(nhanc3)$"
        }
        },
        {
        "name": "Pahe",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "Pahe(\\.(ph|in))?\\b"
        }
        },
        {
        "name": "PSA",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(PSA)$"
        }
        },
        {
        "name": "SasukeducK",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(SasukeducK)$"
        }
        },
        {
        "name": "TBS",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(TBS)$"
        }
        },
        {
        "name": "TG",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(TG)$"
        }
        },
        {
        "name": "VIDEOHOLE",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(VIDEOHOLE)$"
        }
        },
        {
        "name": "worldmkv",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(worldmkv)$"
        }
        },
        {
        "name": "XLF",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(XLF)$"
        }
        },
        {
        "name": "Zero00",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(Zero00)$"
        }
        }
    ]
    }
    ```

#### LQ (Release Title)

??? example "JSON [show/hide]"
    ```json
    {
    "trash_id": "e2315f990da2e2cbfc9fa5b7a6fcfe48",
    "trash_scores": {
        "default": -10000
    },
    "name": "LQ (Release Title)",
    "includeCustomFormatWhenRenaming": false,
    "specifications": [
        {
        "name": "TeeWee",
        "implementation": "ReleaseTitleSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "\\b(TeeWee)\\b"
        }
        },
        {
        "name": "BiTOR (2160p)",
        "implementation": "ReleaseTitleSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "(?=.*?(\\b2160p\\b))(?=.*?(\\bBiTOR\\b))"
        }
        },
        {
        "name": "BEN THE MEN",
        "implementation": "ReleaseTitleSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "\\b(BEN[ ._-]THE[ ._-]MEN)\\b"
        }
        }
    ]
    }
    ```

#### x265 (HD)

??? example "JSON [show/hide]"
    ```json
    {
    "trash_id": "47435ece6b99a0b477caf360e79ba0bb",
    "trash_scores": {
        "default": -10000
    },
    "name": "x265 (HD)",
    "includeCustomFormatWhenRenaming": false,
    "specifications": [
        {
        "name": "x265/HEVC",
        "implementation": "ReleaseTitleSpecification",
        "negate": false,
        "required": true,
        "fields": {
            "value": "[xh][ ._-]?265|\\bHEVC(\\b|\\d)"
        }
        },
        {
        "name": "Not 2160p",
        "implementation": "ResolutionSpecification",
        "negate": true,
        "required": true,
        "fields": {
            "value": 2160
        }
        }
    ]
    }
    ```

#### Extras

??? example "JSON [show/hide]"
    ```json
    {
    "trash_id": "fbcb31d8dabd2a319072b84fc0b7249c",
    "trash_scores": {
        "default": -10000
    },
    "trash_regex": "https://regex101.com/r/lZ9iTm/1",
    "name": "Extras",
    "includeCustomFormatWhenRenaming": false,
    "specifications": [
        {
        "name": "Extras",
        "implementation": "ReleaseTitleSpecification",
        "negate": false,
        "required": true,
        "fields": {
            "value": "(?<=\\bS\\d+\\b).*\\b(Extras|Bonus|Extended[ ._-]Clip)\\b"
        }
        }
    ]
    }
    ```

#### Bad Duel Groups

??? example "JSON [show/hide]"
    ```json
    {
    "trash_id": "32b367365729d530ca1c124a0b180c64",
    "trash_scores": {
        "default": -10000,
        "french-multi": 0
    },
    "name": "Bad Dual Groups",
    "includeCustomFormatWhenRenaming": false,
    "specifications": [
        {
        "name": "alfaHD",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(alfaHD.*)$"
        }
        },
        {
        "name": "BAT",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(BAT)$"
        }
        },
        {
        "name": "BlackBit",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(BlackBit)$"
        }
        },
        {
        "name": "BNd",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(BNd)$"
        }
        },
        {
        "name": "C.A.A",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(C\\.A\\.A)$"
        }
        },
        {
        "name": "Cory",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(Cory)$"
        }
        },
        {
        "name": "EXTREME",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(EXTREME)$"
        }
        },
        {
        "name": "FF",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(FF)$"
        }
        },
        {
        "name": "FOXX",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(FOXX)$"
        }
        },
        {
        "name": "G4RiS",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(G4RiS)$"
        }
        },
        {
        "name": "GUEIRA",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(GUEIRA)$"
        }
        },
        {
        "name": "LCD",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(LCD)$"
        }
        },
        {
        "name": "N3G4N",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(N3G4N)$"
        }
        },
        {
        "name": "PD",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(PD)$"
        }
        },
        {
        "name": "PTHome",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(PTHome)$"
        }
        },
        {
        "name": "RiPER",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(RiPER)$"
        }
        },
        {
        "name": "RK",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(RK)$"
        }
        },
        {
        "name": "SiGLA",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(SiGLA)$"
        }
        },
        {
        "name": "Tars",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(Tars)$"
        }
        },
        {
        "name": "vnlls",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(vnlls)$"
        }
        },
        {
        "name": "WTV",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(WTV)$"
        }
        },
        {
        "name": "Yatogam1",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(Yatogam1)$"
        }
        },
        {
        "name": "YusukeFLA",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(YusukeFLA)$"
        }
        },
        {
        "name": "ZigZag",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(ZigZag)$"
        }
        },
        {
        "name": "ZNM",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(ZNM)$"
        }
        }
    ]
    }
    ```

#### No-RisGroup

??? example "JSON [show/hide]"
    ```json
    {
    "trash_id": "82d40da2bc6923f41e14394075dd4b03",
    "trash_scores": {
        "default": -10000
    },
    "name": "No-RlsGroup",
    "includeCustomFormatWhenRenaming": false,
    "specifications": [
        {
        "name": "No Parsed Group",
        "implementation": "ReleaseGroupSpecification",
        "negate": true,
        "required": false,
        "fields": {
            "value": "."
        }
        }
    ]
    }
    ```

#### Obfuscated

??? example "JSON [show/hide]"
    ```json
    {
    "trash_id": "e1a997ddb54e3ecbfe06341ad323c458",
    "trash_scores": {
        "default": -10000
    },
    "name": "Obfuscated",
    "includeCustomFormatWhenRenaming": false,
    "specifications": [
        {
        "name": "4P",
        "implementation": "ReleaseTitleSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "-4P\\b"
        }
        },
        {
        "name": "4Planet",
        "implementation": "ReleaseTitleSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "-4Planet\\b"
        }
        },
        {
        "name": "AsRequested",
        "implementation": "ReleaseTitleSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "-AsRequested\\b"
        }
        },
        {
        "name": "BUYMORE",
        "implementation": "ReleaseTitleSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "-BUYMORE\\b"
        }
        },
        {
        "name": "Chamele0n",
        "implementation": "ReleaseTitleSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "-Chamele0n\\b"
        }
        },
        {
        "name": "GEROV",
        "implementation": "ReleaseTitleSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "-GEROV\\b"
        }
        },
        {
        "name": "iNC0GNiTO",
        "implementation": "ReleaseTitleSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "-iNC0GNiTO\\b"
        }
        },
        {
        "name": "NZBGeek",
        "implementation": "ReleaseTitleSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "-NZBGeek\\b"
        }
        },
        {
        "name": "Obfuscated",
        "implementation": "ReleaseTitleSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "-Obfuscated\\b"
        }
        },
        {
        "name": "postbot",
        "implementation": "ReleaseTitleSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "-postbot\\b"
        }
        },
        {
        "name": "Rakuv",
        "implementation": "ReleaseTitleSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "-Rakuv\\b"
        }
        },
        {
        "name": "Scrambled",
        "implementation": "ReleaseTitleSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "(?<=\\bS\\d+\\b).*(Scrambled)\\b"
        }
        },
        {
        "name": "WhiteRev",
        "implementation": "ReleaseTitleSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "-WhiteRev\\b"
        }
        },
        {
        "name": "xpost",
        "implementation": "ReleaseTitleSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "-xpost\\b"
        }
        },
        {
        "name": "WRTEAM",
        "implementation": "ReleaseTitleSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "-WRTEAM\\b"
        }
        },
        {
        "name": "CAPTCHA",
        "implementation": "ReleaseTitleSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "-CAPTCHA\\b"
        }
        },
        {
        "name": "_nzb",
        "implementation": "ReleaseTitleSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "_nzb\\b"
        }
        }
    ]
    }
    ```

#### Retags

??? example "JSON [show/hide]"
    ```json
    {
    "trash_id": "06d66ab109d4d2eddb2794d21526d140",
    "trash_scores": {
        "default": -10000
    },
    "name": "Retags",
    "includeCustomFormatWhenRenaming": false,
    "specifications": [
        {
        "name": ".heb",
        "implementation": "ReleaseTitleSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "[.]heb\\b"
        }
        },
        {
        "name": "[eztv]",
        "implementation": "ReleaseTitleSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "\\[eztv([ ._-]re)?\\]"
        }
        },
        {
        "name": "[rarbg]",
        "implementation": "ReleaseTitleSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "\\[rarbg\\]"
        }
        },
        {
        "name": "[rartv]",
        "implementation": "ReleaseTitleSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "\\[rartv\\]"
        }
        },
        {
        "name": "[TGx]",
        "implementation": "ReleaseTitleSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "\\[TGx\\]"
        }
        }
    ]
    }
    ```

#### Scene

??? example "JSON [show/hide]"
    ```json
    {
    "trash_id": "1b3994c551cbb92a2c781af061f4ab44",
    "trash_scores": {
        "default": -10000
    },
    "trash_regex": "https://regex101.com/r/BoIGFA/1",
    "name": "Scene",
    "includeCustomFormatWhenRenaming": false,
    "specifications": [
        {
        "name": "Scene Groups + Naming",
        "implementation": "ReleaseTitleSpecification",
        "negate": false,
        "required": true,
        "fields": {
            "value": "^(?=.*(\\b\\d{3,4}p\\b).*([_. ]WEB[_. ])(?!DL)\\b)|\\b(-CAKES|-GGEZ|-GGWP|-GLHF|-GOSSIP|-NAISU|-KOGI|-PECULATE|-SLOT|-EDITH|-ETHEL|-ELEANOR|-B2B|-SPAMnEGGS|-FTP|-DiRT|-SYNCOPY|-BAE|-SuccessfulCrab|-NHTFS|-SURCODE|-B0MBARDIERS)"
        }
        },
        {
        "name": "Not INFLATE/DEFLATE",
        "implementation": "ReleaseTitleSpecification",
        "negate": true,
        "required": true,
        "fields": {
            "value": "\\b(INFLATE|DEFLATE[)\\]]?)$"
        }
        }
    ]
    }
    ```

#### Repack/Proper

??? example "JSON [show/hide]"
    ```json
    {
    "trash_id": "ec8fa7296b64e8cd390a1600981f3923",
    "trash_scores": {
        "default": 5
    },
    "trash_regex": "https://regex101.com/r/S91wR8/2",
    "name": "Repack/Proper",
    "includeCustomFormatWhenRenaming": false,
    "specifications": [{
            "name": "Repack",
            "implementation": "ReleaseTitleSpecification",
            "negate": false,
            "required": false,
            "fields": {
                "value": "\\b(Repack)\\b"
            }
        },
        {
            "name": "Proper",
            "implementation": "ReleaseTitleSpecification",
            "negate": false,
            "required": false,
            "fields": {
                "value": "\\b(Proper)\\b"
            }
        },
        {
            "name": "Rerip",
            "implementation": "ReleaseTitleSpecification",
            "negate": false,
            "required": false,
            "fields": {
                "value": "\\b(Rerip)\\b"
            }
        }
    ]
    }
    ```

#### Repack V2

??? example "JSON [show/hide]"
    ```json
    {
    "trash_id": "eb3d5cc0a2be0db205fb823640db6a3c",
    "trash_scores": {
        "default": 6
    },
    "name": "Repack v2",
    "includeCustomFormatWhenRenaming": false,
    "specifications": [
        {
        "name": "Repack v2",
        "implementation": "ReleaseTitleSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "\\b(repack2)\\b"
        }
        },
        {
        "name": "Proper v2",
        "implementation": "ReleaseTitleSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "\\b(proper2)\\b"
        }
        }
    ]
    }
    ```

#### Repack V3

??? example "JSON [show/hide]"
    ```json
    {
    "trash_id": "44e7c4de10ae50265753082e5dc76047",
    "trash_scores": {
        "default": 7
    },
    "name": "Repack v3",
    "includeCustomFormatWhenRenaming": false,
    "specifications": [
        {
        "name": "Repack v3",
        "implementation": "ReleaseTitleSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "\\b(repack3)\\b"
        }
        }
    ]
    }
    ```

#### AMZN

??? example "JSON [show/hide]"
    ```json
    {
    "trash_id": "d660701077794679fd59e8bdf4ce3a29",
    "trash_scores": {
        "default": 70,
        "anime-sonarr": 3
    },
    "name": "AMZN",
    "includeCustomFormatWhenRenaming": true,
    "specifications": [
        {
        "name": "Amazon",
        "implementation": "ReleaseTitleSpecification",
        "negate": false,
        "required": true,
        "fields": {
            "value": "\\b(amzn|amazon(hd)?)\\b"
        }
        },
        {
        "name": "WEBDL",
        "implementation": "SourceSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": 3
        }
        },
        {
        "name": "WEBRIP",
        "implementation": "SourceSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": 4
        }
        }
    ]
    }
    ```

#### ATVP

??? example "JSON [show/hide]"
    ```json
    {
    "trash_id": "f67c9ca88f463a48346062e8ad07713f",
    "trash_scores": {
        "default": 100
    },
    "name": "ATVP",
    "includeCustomFormatWhenRenaming": true,
    "specifications": [
        {
        "name": "Apple TV+",
        "implementation": "ReleaseTitleSpecification",
        "negate": false,
        "required": true,
        "fields": {
            "value": "\\b(atvp|aptv|Apple TV\\+)\\b"
        }
        },
        {
        "name": "WEBDL",
        "implementation": "SourceSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": 3
        }
        },
        {
        "name": "WEBRIP",
        "implementation": "SourceSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": 4
        }
        }
    ]
    }
    ```

#### Comedy Central

??? example "JSON [show/hide]"
    ```json
    {
    "trash_id": "77a7b25585c18af08f60b1547bb9b4fb",
    "trash_scores": {
        "default": 50
    },
    "trash_regex": "https://regex101.com/r/A3TRwE/1",
    "name": "CC",
    "includeCustomFormatWhenRenaming": true,
    "specifications": [
        {
        "name": "Comedy Central",
        "implementation": "ReleaseTitleSpecification",
        "negate": false,
        "required": true,
        "fields": {
            "value": "\\b(CC)\\b[ ._-]web[ ._-]?(dl|rip)?\\b"
        }
        },
        {
        "name": "WEBDL",
        "implementation": "SourceSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": 3
        }
        },
        {
        "name": "WEBRIP",
        "implementation": "SourceSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": 4
        }
        }
    ]
    }
    ```

#### DC Universe (Streaming Services)

??? example "JSON [show/hide]"
    ```json
    {
    "trash_id": "36b72f59f4ea20aad9316f475f2d9fbb",
    "trash_scores": {
        "default": 50
    },
    "name": "DCU",
    "includeCustomFormatWhenRenaming": true,
    "specifications": [
        {
        "name": "DC Universe",
        "implementation": "ReleaseTitleSpecification",
        "negate": false,
        "required": true,
        "fields": {
            "value": "\\b(dcu|DC Universe)\\b"
        }
        },
        {
        "name": "WEBDL",
        "implementation": "SourceSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": 3
        }
        },
        {
        "name": "WEBRIP",
        "implementation": "SourceSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": 4
        }
        }
    ]
    }
    ```

#### DSNP+

??? example "JSON [show/hide]"
    ```json
    {
    "trash_id": "89358767a60cc28783cdc3d0be9388a4",
    "trash_scores": {
        "default": 100,
        "anime-sonarr": 5
    },
    "name": "DSNP",
    "includeCustomFormatWhenRenaming": true,
    "specifications": [
        {
        "name": "Disney+",
        "implementation": "ReleaseTitleSpecification",
        "negate": false,
        "required": true,
        "fields": {
            "value": "\\b(dsnp|dsny|disney|Disney\\+)\\b"
        }
        },
        {
        "name": "WEBDL",
        "implementation": "SourceSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": 3
        }
        },
        {
        "name": "WEBRIP",
        "implementation": "SourceSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": 4
        }
        }
    ]
    }
    ```

#### HMAX (HBO Max)

??? example "JSON [show/hide]"
    ```json
    {
    "trash_id": "a880d6abc21e7c16884f3ae393f84179",
    "trash_scores": {
        "default": 80
    },
    "name": "HMAX",
    "includeCustomFormatWhenRenaming": true,
    "specifications": [
        {
        "name": "HBO Max",
        "implementation": "ReleaseTitleSpecification",
        "negate": false,
        "required": true,
        "fields": {
            "value": "\\b(hmax|hbom|hbo[ ._-]max)\\b(?=[ ._-]web[ ._-]?(dl|rip)\\b)"
        }
        },
        {
        "name": "WEBDL",
        "implementation": "SourceSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": 3
        }
        },
        {
        "name": "WEBRIP",
        "implementation": "SourceSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": 4
        }
        }
    ]
    }
    ```

#### HBO (HBO)

??? example "JSON [show/hide]"
    ```json
    {
    "trash_id": "7a235133c87f7da4c8cccceca7e3c7a6",
    "trash_scores": {
        "default": 50
    },
    "name": "HBO",
    "includeCustomFormatWhenRenaming": true,
    "specifications": [
        {
        "name": "HBO",
        "implementation": "ReleaseTitleSpecification",
        "negate": false,
        "required": true,
        "fields": {
            "value": "\\b(hbo)(?![ ._-]max)\\b(?=[ ._-]web[ ._-]?(dl|rip)\\b)"
        }
        },
        {
        "name": "WEBDL",
        "implementation": "SourceSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": 3
        }
        },
        {
        "name": "WEBRIP",
        "implementation": "SourceSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": 4
        }
        }
    ]
    }
    ```

#### Hulu

??? example "JSON [show/hide]"
    ```json
    {
    "trash_id": "f6cce30f1733d5c8194222a7507909bb",
    "trash_scores": {
        "default": 50
    },
    "name": "HULU",
    "includeCustomFormatWhenRenaming": true,
    "specifications": [
        {
        "name": "Hulu",
        "implementation": "ReleaseTitleSpecification",
        "negate": false,
        "required": true,
        "fields": {
            "value": "\\b(hulu)\\b"
        }
        },
        {
        "name": "WEBDL",
        "implementation": "SourceSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": 3
        }
        },
        {
        "name": "WEBRIP",
        "implementation": "SourceSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": 4
        }
        }
    ]
    }
    ```

#### IT (iTunes)

??? example "JSON [show/hide]"
    ```json
    {
    "trash_id": "0ac24a2a68a9700bcb7eeca8e5cd644c",
    "trash_scores": {
        "default": 50
    },
    "name": "iT",
    "includeCustomFormatWhenRenaming": true,
    "specifications": [
        {
        "name": "iTunes",
        "implementation": "ReleaseTitleSpecification",
        "negate": false,
        "required": true,
        "fields": {
            "value": "\\b(it|itunes)\\b(?=[ ._-]web[ ._-]?(dl|rip)\\b)"
        }
        }
    ]
    }
    ```

#### Max (Streaming Service)

??? example "JSON [show/hide]"
    ```json
    {
    "trash_id": "81d1fbf600e2540cee87f3a23f9d3c1c",
    "trash_scores": {
        "default": 90
    },
    "trash_regex": "https://regex101.com/r/fa649l/1",
    "name": "MAX",
    "includeCustomFormatWhenRenaming": true,
    "specifications": [
        {
        "name": "Max",
        "implementation": "ReleaseTitleSpecification",
        "negate": false,
        "required": true,
        "fields": {
            "value": "\\b((?<!hbo[ ._-])max)\\b(?=[ ._-]web[ ._-]?(dl|rip)\\b)"
        }
        },
        {
        "name": "WEBDL",
        "implementation": "SourceSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": 3
        }
        },
        {
        "name": "WEBRIP",
        "implementation": "SourceSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": 4
        }
        }
    ]
    }
    ```

#### NF (Netflix)

??? example "JSON [show/hide]"
    ```json
    {
    "trash_id": "d34870697c9db575f17700212167be23",
    "trash_scores": {
        "default": 60,
        "anime-sonarr": 4
    },
    "name": "NF",
    "includeCustomFormatWhenRenaming": true,
    "specifications": [
        {
        "name": "Netflix",
        "implementation": "ReleaseTitleSpecification",
        "negate": false,
        "required": true,
        "fields": {
            "value": "\\b(nf|netflix(u?hd)?)\\b"
        }
        },
        {
        "name": "WEBDL",
        "implementation": "SourceSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": 3
        }
        },
        {
        "name": "WEBRIP",
        "implementation": "SourceSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": 4
        }
        }
    ]
    }
    ```

#### PMTP (Paramount+)

??? example "JSON [show/hide]"
    ```json
    {
    "trash_id": "c67a75ae4a1715f2bb4d492755ba4195",
    "trash_scores": {
        "default": 60
    },
    "name": "PMTP",
    "includeCustomFormatWhenRenaming": true,
    "specifications": [
        {
        "name": "Paramount+",
        "implementation": "ReleaseTitleSpecification",
        "negate": false,
        "required": true,
        "fields": {
            "value": "\\b(pmtp|Paramount\\+)\\b"
        }
        },
        {
        "name": "WEBDL",
        "implementation": "SourceSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": 3
        }
        },
        {
        "name": "WEBRIP",
        "implementation": "SourceSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": 4
        }
        }
    ]
    }
    ```

#### PCOK (Peacock TV)

??? example "JSON [show/hide]"
    ```json
    {
    "trash_id": "1656adc6d7bb2c8cca6acfb6592db421",
    "trash_scores": {
        "default": 60
    },
    "name": "PCOK",
    "includeCustomFormatWhenRenaming": true,
    "specifications": [
        {
        "name": "Peacock TV",
        "implementation": "ReleaseTitleSpecification",
        "negate": false,
        "required": true,
        "fields": {
            "value": "\\b(pcok|Peacock TV)\\b"
        }
        },
        {
        "name": "WEBDL",
        "implementation": "SourceSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": 3
        }
        },
        {
        "name": "WEBRIP",
        "implementation": "SourceSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": 4
        }
        }
    ]
    }
    ```

#### SHO (Showtime)

??? example "JSON [show/hide]"
    ```json
    {
    "trash_id": "ae58039e1319178e6be73caab5c42166",
    "trash_scores": {
        "default": 50
    },
    "trash_regex": "https://regex101.com/r/kjPPbG/1",
    "name": "SHO",
    "includeCustomFormatWhenRenaming": true,
    "specifications": [
        {
        "name": "SHOWTIME",
        "implementation": "ReleaseTitleSpecification",
        "negate": false,
        "required": true,
        "fields": {
            "value": "\\b(sho|showtime)\\b[ ._-]web[ ._-]?(dl|rip)?\\b"
        }
        },
        {
        "name": "WEBDL",
        "implementation": "SourceSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": 3
        }
        },
        {
        "name": "WEBRIP",
        "implementation": "SourceSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": 4
        }
        }
    ]
    }
    ```

#### STAN

??? example "JSON [show/hide]"
    ```json
    {
    "trash_id": "1efe8da11bfd74fbbcd4d8117ddb9213",
    "trash_scores": {
        "default": 60
    },
    "trash_regex": "https://regex101.com/r/IMS7Or/1",
    "name": "STAN",
    "includeCustomFormatWhenRenaming": true,
    "specifications": [
        {
        "name": "Stan",
        "implementation": "ReleaseTitleSpecification",
        "negate": false,
        "required": true,
        "fields": {
            "value": "\\b(stan)\\b[ ._-]web[ ._-]?(dl|rip)?\\b"
        }
        },
        {
        "name": "WEBDL",
        "implementation": "SourceSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": 3
        }
        },
        {
        "name": "WEBRIP",
        "implementation": "SourceSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": 4
        }
        }
    ]
    }
    ```

#### WEB Tier 1

??? example "JSON [show/hide]"
    ```json
    {
    "trash_id": "e6258996055b9fbab7e9cb2f75819294",
    "trash_scores": {
        "default": 1700,
        "anime-sonarr": 350
    },
    "name": "WEB Tier 01",
    "includeCustomFormatWhenRenaming": false,
    "specifications": [
        {
        "name": "ABBiE",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(ABBiE)$"
        }
        },
        {
        "name": "AJP69",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(AJP69)$"
        }
        },
        {
        "name": "APEX",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(APEX|PAXA|PEXA|XEPA)$"
        }
        },
        {
        "name": "CasStudio",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(CasStudio)$"
        }
        },
        {
        "name": "CRFW",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(CRFW)$"
        }
        },
        {
        "name": "CtrlHD",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(CtrlHD)$"
        }
        },
        {
        "name": "FLUX",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(FLUX)$"
        }
        },
        {
        "name": "HONE",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(HONE)$"
        }
        },
        {
        "name": "KiNGS",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(KiNGS)$"
        }
        },
        {
        "name": "monkee",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(monkee)$"
        }
        },
        {
        "name": "NOSiViD",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(NOSiViD)$"
        }
        },
        {
        "name": "NTb",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(NTb)$"
        }
        },
        {
        "name": "NTG",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(NTG)$"
        }
        },
        {
        "name": "QOQ",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(QOQ)$"
        }
        },
        {
        "name": "RTN",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(RTN)$"
        }
        },
        {
        "name": "SiC",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(SiC)$"
        }
        },
        {
        "name": "T6D",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(T6D)$"
        }
        },
        {
        "name": "TOMMY",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(TOMMY)$"
        }
        },
        {
        "name": "ViSUM",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(ViSUM)$"
        }
        },
        {
        "name": "WEBDL",
        "implementation": "SourceSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": 3
        }
        },
        {
        "name": "WEBRIP",
        "implementation": "SourceSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": 4
        }
        }
    ]
    }
    ```

#### WEB Tier 2

??? example "JSON [show/hide]"
    ```json
    {
    "trash_id": "58790d4e2fdcd9733aa7ae68ba2bb503",
    "trash_scores": {
        "default": 1650,
        "anime-sonarr": 150
    },
    "name": "WEB Tier 02",
    "includeCustomFormatWhenRenaming": false,
    "specifications": [
        {
        "name": "3cTWeB",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(3cTWeB)$"
        }
        },
        {
        "name": "BLUTONiUM",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(BLUTONiUM)$"
        }
        },
        {
        "name": "BTW",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(BTW)$"
        }
        },
        {
        "name": "Chotab",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(Chotab)$"
        }
        },
        {
        "name": "Cinefeel",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(Cinefeel)$"
        }
        },
        {
        "name": "CiT",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(CiT)$"
        }
        },
        {
        "name": "CMRG",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(CMRG)$"
        }
        },
        {
        "name": "Coo7",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(Coo7)$"
        }
        },
        {
        "name": "dB",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(dB)$"
        }
        },
        {
        "name": "DEEP",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(DEEP)$"
        }
        },
        {
        "name": "END",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(END)$"
        }
        },
        {
        "name": "ETHiCS",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(ETHiCS)$"
        }
        },
        {
        "name": "FC",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(FC)$"
        }
        },
        {
        "name": "Flights",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(Flights)$"
        }
        },
        {
        "name": "GNOME",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(GNOME)$"
        }
        },
        {
        "name": "iJP",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(iJP)$"
        }
        },
        {
        "name": "iKA",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(iKA)$"
        }
        },
        {
        "name": "iT00NZ",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(iT00NZ)$"
        }
        },
        {
        "name": "JETIX",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(JETIX)$"
        }
        },
        {
        "name": "KHN",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(KHN)$"
        }
        },
        {
        "name": "KiMCHI",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(KiMCHI)$"
        }
        },
        {
        "name": "Kitsune",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(Kitsune)$"
        }
        },
        {
        "name": "LAZY",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(LAZY)$"
        }
        },
        {
        "name": "MiU",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(MiU)$"
        }
        },
        {
        "name": "MZABI",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(MZABI)$"
        }
        },
        {
        "name": "NPMS",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(NPMS)$"
        }
        },
        {
        "name": "NYH",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(NYH)$"
        }
        },
        {
        "name": "orbitron",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(orbitron)$"
        }
        },
        {
        "name": "PHOENiX",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(PHOENiX)$"
        }
        },
        {
        "name": "playWEB",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(playWEB)$"
        }
        },
        {
        "name": "PSiG",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(PSiG)$"
        }
        },
        {
        "name": "ROCCaT",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(ROCCaT)$"
        }
        },
        {
        "name": "RTFM",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(RTFM)$"
        }
        },
        {
        "name": "SA89",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(SA89)$"
        }
        },
        {
        "name": "SbR",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(SbR)$"
        }
        },
        {
        "name": "SDCC",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(SDCC)$"
        }
        },
        {
        "name": "SIGMA",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(SIGMA)$"
        }
        },
        {
        "name": "SMURF",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(SMURF)$"
        }
        },
        {
        "name": "SPiRiT",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(SPiRiT)$"
        }
        },
        {
        "name": "TEPES",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(TEPES)$"
        }
        },
        {
        "name": "TVSmash",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(TVSmash)$"
        }
        },
        {
        "name": "WELP",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(WELP)$"
        }
        },
        {
        "name": "XEBEC",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(XEBEC|4KBEC|CEBEX)$"
        }
        },
        {
        "name": "WEBDL",
        "implementation": "SourceSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": 3
        }
        },
        {
        "name": "WEBRIP",
        "implementation": "SourceSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": 4
        }
        }
    ]
    }
    ```

#### WEB Tier 3

??? example "JSON [show/hide]"
    ```json
    {
    "trash_id": "d84935abd3f8556dcd51d4f27e22d0a6",
    "trash_scores": {
        "default": 1600,
        "anime-sonarr": 150
    },
    "name": "WEB Tier 03",
    "includeCustomFormatWhenRenaming": false,
    "specifications": [
        {
        "name": "DRACULA",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(DRACULA)$"
        }
        },
        {
        "name": "NINJACENTRAL",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(NINJACENTRAL)$"
        }
        },
        {
        "name": "SLiGNOME",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(SLiGNOME)$"
        }
        },
        {
        "name": "SwAgLaNdEr",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(SwAgLaNdEr)$"
        }
        },
        {
        "name": "T4H",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(T4H)$"
        }
        },
        {
        "name": "ViSiON",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(ViSiON)$"
        }
        },
        {
        "name": "WEBDL",
        "implementation": "SourceSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": 3
        }
        },
        {
        "name": "WEBRIP",
        "implementation": "SourceSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": 4
        }
        }
    ]
    }
    ```

#### WEB Scene

??? example "JSON [show/hide]"
    ```json
    {
    "trash_id": "d0c516558625b04b363fa6c5c2c7cfd4",
    "trash_scores": {
        "default": 1600
    },
    "name": "WEB Scene",
    "includeCustomFormatWhenRenaming": false,
    "specifications": [
        {
        "name": "DEFLATE",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(DEFLATE)$"
        }
        },
        {
        "name": "INFLATE",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(INFLATE)$"
        }
        }
    ]
    }
    ```

## Quality Profiles

Now you've added all the custom formats to Sonarr and now we need to build the "Quality Profile" that we're going to add these newly added Custom Formats to do that when Sonarr searches it uses these formats to narrow down the search.

So to start go to Sonarrs settings page again, this time you want to click "Profiles" we want to create a new Profile so click the "+" button and you'll be faced with a page wanting a bunch of information, you'll find that below.

### WEB-DL (1080p)

* Name: WEB-DL (1080p)
* Upgrade Allowed: True
* Upgrade Until: WEB 1080p
* Minimum Custom Format Score: 0
* Upgrade Until Custom Format Score: 10000

Under the qualities section we need to add and build the qualities exactly as I've described them below otherwise the upgrades and pulling of files won't be correct. 

First you need to find and select the quality in the list called "WEB 1080p" this should include 2 other qualities shown in the bar at the right hand side of the title.

Now you need to find and select the quality called "WEB 720p" and lastly find and select "HDTV 1080p" 

This is the order in which they should be in the list - drag and drop them in this order at the top of the list. (*Note: quality does matter even if not selected in the list so make sure you select them and move them to the top in the order shown.*)

1. WEB 1080p
2. WEB 720p
3. HDTV 1080p

### Scoring 

Now we've added our custom formats and we've built the profile to add them to now we have to score them within the profile we just made to do this scroll down a little further past the qualities and you'll see our custom formats we created, next to each custom format on the right hand side there's an empty box called "Score" in this box you're going to add the scores listed below for each custom format.

(Scores)

* BR-DISK - (-10000)
* LQ - (-10000)
* LQ (Release Title) - (-10000)
* x265 (HD) - (-10000)
* Extras - (-10000)
* Bad Duel Groups - (-10000)
* No-RlsGroup - (-10000)
* Obfuscated - (-10000)
* Retags - (-10000)
* Scene - (-10000)
* Repack/Proper - (5)
* Repack V2 - (6)
* Repack V3 - (7)
* AMZN - (70)
* ATVP - (100)
* CC - (50)
* DCU - (50)
* DSNP - (100)
* HMAX - (80)
* HBO - (50)
* HULU - (50)
* iT - (50)
* MAX - (90)
* NF - (60)
* PMTP - (60)
* PCOK - (60)
* SHO - (50)
* STAN - (60)

Once you've added these scores, you're done! Just set your default quality as the new Profile we created and all of your shows (if available to download) will be downloaded at optimal quality and are highly likely not to transcode or be incompatible with your streaming device be it a phone or firestick a Roku or Xbox.

However if 1080p isn't your thing and you'd like the quality upgrade please look out for my 2160p (4K) guides also.

--8<-- "common-links.md"