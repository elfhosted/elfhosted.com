---
title: Optimizing Movie quality in Radarr using TRaSH guides custom formats
description: A ELI5 guide to using TRaSH guides to optimize your HD (1080P) movies in ElfHosted
---

The following guide was contributed by @LayeZee, [Elf-venger](/team/#elf-vengers) and Arr-Ninja!

Below you'll find an ELI5 guide to importing the 1080p version of the [TRaSH Guides](https://trash-guides.info/) into your [Radarr][radarr] for better compatibility with your devices.

(*This isn't a 1 size fits all but it's close*)

!!! tip "Too complicated? Do it with ElfBot!"
    There's a simpler way, if you don't care to run through the process yourself. See [Radarr](/app/radarr/#add-trash-guides) for details!

## Process

Okay so let's begin.

You'll need to first go to radarr and open your Settings page then click on `Custom Formats`, after doing this press the `+` button and on the page that is displayed and at the bottom left click `import`, now the page displayed will be asking for a JSON code, once you've pasted the JSON code you'll save, confirm the custom formats are added, and then press `Save` at the bottom right of the screen and then the process begins again.

I'll provide the codes below but essentially this step 1 is what we'll be following until stated otherwise so please familiarize yourselves with the process of adding a custom format and copy and pasting the JSON code.

Here are screenshots illustrating the steps:

![](/images/trash-guide-radarr-1.png)

![](/images/trash-guide-radarr-2.png)

![](/images/trash-guide-radarr-2a.png)

![](/images/trash-guide-radarr-3.png)

## Custom Formats

Here we're are going to be copying the JSON codes for the required Custom Formats, I'm going to skip the explanation as to why we're adding 4K profiles etc in a 1080p list as this is an ELI5 instructional, if you wish to understand more please refer to the original trash guides for an in-depth explanation of events.

So starting the codes these are going to be for "movie types"

#### Remaster

??? example "JSON [show/hide]"
    ```json
    {
    "trash_id": "570bc9ebecd92723d2d21500f4be314c",
    "trash_scores": {
        "default": 25
    },
    "name": "Remaster",
    "includeCustomFormatWhenRenaming": false,
    "specifications": [{
            "name": "Remaster",
            "implementation": "ReleaseTitleSpecification",
            "negate": false,
            "required": true,
            "fields": {
                "value": "Remaster"
            }
        },
        {
            "name": "Not 4K Remaster",
            "implementation": "ReleaseTitleSpecification",
            "negate": true,
            "required": true,
            "fields": {
                "value": "4K"
            }
        }
    ]
    }
    ```

#### 4K Remaster 

??? example "JSON [show/hide]"
    ```json
    {
    "trash_id": "eca37840c13c6ef2dd0262b141a5482f",
    "trash_scores": {
        "default": 25
    },
    "name": "4K Remaster",
    "includeCustomFormatWhenRenaming": true,
    "specifications": [
        {
        "name": "Remaster",
        "implementation": "ReleaseTitleSpecification",
        "negate": false,
        "required": true,
        "fields": {
            "value": "Remaster"
        }
        },
        {
        "name": "4K",
        "implementation": "ReleaseTitleSpecification",
        "negate": false,
        "required": true,
        "fields": {
            "value": "4k"
        }
        },
        {
        "name": "Not 4K Resolution",
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

#### Criterion Collection

??? example "JSON [show/hide]"
    ```json
    {
    "trash_id": "e0c07d59beb37348e975a930d5e50319",
    "trash_scores": {
        "default": 25
    },
    "name": "Criterion Collection",
    "includeCustomFormatWhenRenaming": true,
    "specifications": [
        {
        "name": "Bluray",
        "implementation": "SourceSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": 9
        }
        },
        {
        "name": "DVD",
        "implementation": "SourceSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": 5
        }
        },
        {
        "name": "Criterion",
        "implementation": "ReleaseTitleSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "\\b(Criterion)\\b"
        }
        },
        {
        "name": "CC",
        "implementation": "ReleaseTitleSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "\\b(CC)\\b"
        }
        },
        {
        "name": "Not Criterion RlsGrp",
        "implementation": "ReleaseGroupSpecification",
        "negate": true,
        "required": true,
        "fields": {
            "value": "^(Criterion)$"
        }
        }
    ]
    }
    ```

#### Master of Cinema

??? example "JSON [show/hide]"
    ```json
    {
    "trash_id": "9d27d9d2181838f76dee150882bdc58c",
    "trash_scores": {
        "default": 25
    },
    "name": "Masters of Cinema",
    "includeCustomFormatWhenRenaming": true,
    "specifications": [
        {
        "name": "Masters of Cinema",
        "implementation": "ReleaseTitleSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "\\b(Masters[ .-]?Of[ .-]?Cinema)(\\b|\\d)"
        }
        },
        {
        "name": "MoC",
        "implementation": "ReleaseTitleSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "\\b(MoC)\\b"
        }
        }
    ]
    }
    ```

#### Vinegar Syndrome

??? example "JSON [show/hide]"
    ```json
    {
    "trash_id": "db9b4c4b53d312a3ca5f1378f6440fc9",
    "trash_scores": {
        "default": 25
    },
    "name": "Vinegar Syndrome",
    "includeCustomFormatWhenRenaming": true,
    "specifications": [
        {
        "name": "Vinegar Syndrome",
        "implementation": "ReleaseTitleSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "\\b(Vinegar[ ._-]Syndrome)\\b"
        }
        },
        {
        "name": "VS",
        "implementation": "ReleaseTitleSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "\\b(V-S)\\b"
        }
        },
        {
        "name": "VinSyn",
        "implementation": "ReleaseTitleSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "\\b(VinSyn)\\b"
        }
        }
    ]
    }
    ```


#### Special Edition

??? example "JSON [show/hide]"
    ```json
    {
    "trash_id": "957d0f44b592285f26449575e8b1167e",
    "trash_scores": {
        "default": 125
    },
    "trash_regex": "https://regex101.com/r/44pLFg/1",
    "name": "Special Edition",
    "includeCustomFormatWhenRenaming": false,
    "specifications": [
        {
        "name": "Special Edition",
        "implementation": "ReleaseTitleSpecification",
        "negate": false,
        "required": true,
        "fields": {
            "value": "(?<!^|{)\\b(extended|uncut|directors|special|unrated|uncensored|cut|version|edition)(\\b|\\d)"
        }
        },
        {
        "name": "Not IMAX Edition",
        "implementation": "ReleaseTitleSpecification",
        "negate": true,
        "required": true,
        "fields": {
            "value": "\\b(IMAX[ ._-]Edition)\\b"
        }
        },
        {
        "name": "Not Open Matte",
        "implementation": "ReleaseTitleSpecification",
        "negate": true,
        "required": true,
        "fields": {
            "value": "\\b(Open[ ._-]?Matte)\\b"
        }
        },
        {
        "name": "Not Theatrical",
        "implementation": "ReleaseTitleSpecification",
        "negate": true,
        "required": true,
        "fields": {
            "value": "Theatrical"
        }
        },
        {
        "name": "Not Extended Clip",
        "implementation": "ReleaseTitleSpecification",
        "negate": true,
        "required": true,
        "fields": {
            "value": "\\b(Extended[ ._-]Clip)\\b"
        }
        }
    ]
    }
    ```

#### IMAX

??? example "JSON [show/hide]"
    ```json
    {
    "trash_id": "eecf3a857724171f968a66cb5719e152",
    "trash_scores": {
        "default": 800
    },
    "trash_regex": "https://regex101.com/r/e7ugxU/1",
    "name": "IMAX",
    "includeCustomFormatWhenRenaming": false,
    "specifications": [
        {
        "name": "IMAX",
        "implementation": "ReleaseTitleSpecification",
        "negate": false,
        "required": true,
        "fields": {
            "value": "\\b((?<!NON[ ._-])IMAX)\\b"
        }
        },
        {
        "name": "NOT: IMAX Enhanced",
        "implementation": "ReleaseTitleSpecification",
        "negate": true,
        "required": true,
        "fields": {
            "value": "^(?=.*\\b((DSNP|Disney\\+|BC|B?CORE)(?=[ ._-]web[ ._-]?(dl|rip)\\b)))(?=.*\\b((?<!NON[ ._-])IMAX)\\b)|^(?=.*\\b(IMAX[ ._-]Enhanced)\\b)"
        }
        }
    ]
    }
    ```

#### IMAX Enhanced

??? example "JSON [show/hide]"
    ```json
    {
    "trash_id": "9f6cbff8cfe4ebbc1bde14c7b7bec0de",
    "trash_scores": {
        "default": 800
    },
    "trash_regex": "https://regex101.com/r/e7ugxU/1",
    "name": "IMAX Enhanced",
    "includeCustomFormatWhenRenaming": true,
    "specifications": [
        {
        "name": "IMAX Enhanced",
        "implementation": "ReleaseTitleSpecification",
        "negate": false,
        "required": true,
        "fields": {
            "value": "^(?=.*\\b((DSNP|Disney\\+|BC|B?CORE)(?=[ ._-]web[ ._-]?(dl|rip)\\b)))(?=.*\\b((?<!NON[ ._-])IMAX)\\b)|^(?=.*\\b(IMAX[ ._-]Enhanced)\\b)"
        }
        }
    ]
    }
    ```

### HQ Release Groups

Now we'll move onto adding the custom formats for High Quality release groups (so we don't get bad copies)

#### HD Bluray Tier 1

??? example "JSON [show/hide]"
    ```json
    {
    "trash_id": "ed27ebfef2f323e964fb1f61391bcb35",
    "trash_scores": {
        "default": 1800,
        "sqp-1-1080p": 1100,
        "sqp-1-2160p": 1100
    },
    "name": "HD Bluray Tier 01",
    "includeCustomFormatWhenRenaming": false,
    "specifications": [
        {
        "name": "BLURAY",
        "implementation": "SourceSpecification",
        "negate": false,
        "required": true,
        "fields": {
            "value": 9
        }
        },
        {
        "name": "Not REMUX",
        "implementation": "QualityModifierSpecification",
        "negate": true,
        "required": true,
        "fields": {
            "value": 5
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
        },
        {
        "name": "BBQ",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(BBQ)$"
        }
        },
        {
        "name": "BMF",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(BMF)$"
        }
        },
        {
        "name": "c0kE",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(c0kE)$"
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
        "name": "CRiSC",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(CRiSC)$"
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
        "name": "D-Z0N3",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(D-Z0N3)$"
        }
        },
        {
        "name": "Dariush",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(Dariush)$"
        }
        },
        {
        "name": "decibeL",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(decibeL)$"
        }
        },
        {
        "name": "DON",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(DON)$"
        }
        },
        {
        "name": "EbP",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(EbP)$"
        }
        },
        {
        "name": "EDPH",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(EDPH)$"
        }
        },
        {
        "name": "Geek",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(Geek)$"
        }
        },
        {
        "name": "LolHD",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(LolHD)$"
        }
        },
        {
        "name": "NCmt",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(NCmt)$"
        }
        },
        {
        "name": "PTer",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(PTer)$"
        }
        },
        {
        "name": "TayTO",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(TayTO)$"
        }
        },
        {
        "name": "TDD",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(TDD)$"
        }
        },
        {
        "name": "TnP",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(TnP)$"
        }
        },
        {
        "name": "VietHD",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(VietHD)$"
        }
        },
        {
        "name": "ZQ",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(ZQ)$"
        }
        }
    ]
    }
    ```

#### HD Bluray Tier 2

??? example "JSON [show/hide]"
    ```json
    {
    "trash_id": "c20c8647f2746a1f4c4262b0fbbeeeae",
    "trash_scores": {
        "default": 1750,
        "sqp-1-1080p": 1050,
        "sqp-1-2160p": 1050
    },
    "name": "HD Bluray Tier 02",
    "includeCustomFormatWhenRenaming": false,
    "specifications": [
        {
        "name": "BLURAY",
        "implementation": "SourceSpecification",
        "negate": false,
        "required": true,
        "fields": {
            "value": 9
        }
        },
        {
        "name": "Not REMUX",
        "implementation": "QualityModifierSpecification",
        "negate": true,
        "required": true,
        "fields": {
            "value": 5
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
        },
        {
        "name": "EA",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(EA)$"
        }
        },
        {
        "name": "HiDt",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(HiDt)$"
        }
        },
        {
        "name": "HiSD",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(HiSD)$"
        }
        },
        {
        "name": "iFT",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(iFT)$"
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
        "name": "QOQ",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(QOQ)$"
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
        "name": "sbR",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(sbR)$"
        }
        }
    ]
    }
    ```

#### HD Bluray Tier 3

??? example "JSON [show/hide]"
    ```json
    {
    "trash_id": "5608c71bcebba0a5e666223bae8c9227",
    "trash_scores": {
        "default": 1700,
        "sqp-1-1080p": 1000,
        "sqp-1-2160p": 1000
    },
    "name": "HD Bluray Tier 03",
    "includeCustomFormatWhenRenaming": false,
    "specifications": [
        {
        "name": "BLURAY",
        "implementation": "SourceSpecification",
        "negate": false,
        "required": true,
        "fields": {
            "value": 9
        }
        },
        {
        "name": "Not REMUX",
        "implementation": "QualityModifierSpecification",
        "negate": true,
        "required": true,
        "fields": {
            "value": 5
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
        },
        {
        "name": "BHDStudio",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(BHDStudio)$"
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
        "name": "LoRD",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(LoRD)$"
        }
        },
        {
        "name": "playHD",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(playHD)$"
        }
        },
        {
        "name": "SPHD",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(SPHD)$"
        }
        }
    ]
    }
    ```

#### Web Tier 1

??? example "JSON [show/hide]"
    ```json
    {
    "trash_id": "c20f169ef63c5f40c2def54abaf4438e",
    "trash_scores": {
        "default": 1700,
        "anime-radarr": 350
    },
    "name": "WEB Tier 01",
    "includeCustomFormatWhenRenaming": false,
    "specifications": [
        {
        "name": "WEBDL",
        "implementation": "SourceSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": 7
        }
        },
        {
        "name": "WEBRIP",
        "implementation": "SourceSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": 8
        }
        },
        {
        "name": "ABBIE",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(ABBIE)$"
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
        "name": "BLUTONiUM",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(BLUTONiUM)$"
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
        "name": "CRFW",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(CRFW)$"
        }
        },
        {
        "name": "CRUD",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(CRUD)$"
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
        "name": "GNOME",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(GNOME)$"
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
        "name": "SiC",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(SiC)$"
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
        }
    ]
    }
    ```

#### Web Tier 2

??? example "JSON [show/hide]"
    ```json
    {
    "trash_id": "403816d65392c79236dcb6dd591aeda4",
    "trash_scores": {
        "default": 1650,
        "anime-radarr": 250
    },
    "name": "WEB Tier 02",
    "includeCustomFormatWhenRenaming": false,
    "specifications": [
        {
        "name": "WEBDL",
        "implementation": "SourceSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": 7
        }
        },
        {
        "name": "WEBRIP",
        "implementation": "SourceSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": 8
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
        "name": "Flights",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(Flights)$"
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
        "name": "MiU",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(MiU)$"
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
        "name": "MZABI",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(MZABI)$"
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
        "name": "SbR",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(SbR)$"
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
        "name": "TOMMY",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(TOMMY)$"
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
        }
    ]
    }
    ```

#### Web Tier 3

??? example "JSON [show/hide]"
    ```json
    {
    "trash_id": "af94e0fe497124d1f9ce732069ec8c3b",
    "trash_scores": {
        "default": 1600,
        "anime-radarr": 150
    },
    "name": "WEB Tier 03",
    "includeCustomFormatWhenRenaming": false,
    "specifications": [
        {
        "name": "WEBDL",
        "implementation": "SourceSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": 7
        }
        },
        {
        "name": "WEBRIP",
        "implementation": "SourceSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": 8
        }
        },
        {
        "name": "GNOMiSSiON",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(GNOMiSSiON)$"
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
        "name": "ROCCaT",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(ROCCaT)$"
        }
        },
        {
        "name": "SiGMA",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(SiGMA)$"
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
        }
    ]
    }
    ```

### Misc

Now we'll move onto adding 2 miscellaneous Custom Formats to allow for proper repacks.

#### Repack/Proper

??? example "JSON [show/hide]"
    ```json
    {
    "trash_id": "e7718d7a3ce595f289bfee26adc178f5",
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

#### Repack 2

??? example "JSON [show/hide]"
    ```json
    {
    "trash_id": "ae43b294509409a6a13919dedd4764c4",
    "trash_scores": {
        "default": 6
    },
    "trash_regex": "https://regex101.com/r/kQ4oeP/1",
    "name": "Repack2",
    "includeCustomFormatWhenRenaming": false,
    "specifications": [
        {
        "name": "Repack2",
        "implementation": "ReleaseTitleSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "\\b(Repack2)\\b"
        }
        },
        {
        "name": "Proper2",
        "implementation": "ReleaseTitleSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "\\b(Proper2)\\b"
        }
        }
    ]
    }
    ```

### Unwanted

5Now we'll add the unwanted items in this next list, remember we're still following step 1 in the way we're adding these custom formats.

#### BR-DISK

??? example "JSON [show/hide]"
    ```json
    {
    "trash_id": "ed38b889b31be83fda192888e2286d83",
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

#### LQ

??? example "JSON [show/hide]"
    ```json
    {
    "trash_id": "90a6f9a284dff5103f6346090e6280c8",
    "trash_scores": {
        "default": -10000
    },
    "name": "LQ",
    "includeCustomFormatWhenRenaming": false,
    "specifications": [
        {
        "name": "24xHD",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "\\b(24xHD)\\b"
        }
        },
        {
        "name": "41RGB",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(41RGB)$"
        }
        },
        {
        "name": "4K4U",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(4K4U)$"
        }
        },
        {
        "name": "AROMA",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(AROMA)$"
        }
        },
        {
        "name": "aXXo",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(aXXo)$"
        }
        },
        {
        "name": "AZAZE",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(AZAZE)$"
        }
        },
        {
        "name": "BARC0DE",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(BARC0DE)$"
        }
        },
        {
        "name": "BdC",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(BdC)$"
        }
        },
        {
        "name": "beAst",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(beAst)$"
        }
        },
        {
        "name": "C4K",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(C4K)$"
        }
        },
        {
        "name": "CDDHD",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(CDDHD)$"
        }
        },
        {
        "name": "CHAOS",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(CHAOS)$"
        }
        },
        {
        "name": "CHD",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(CHD)$"
        }
        },
        {
        "name": "CiNE",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(CiNE)$"
        }
        },
        {
        "name": "CREATiVE24",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(CREATiVE24)$"
        }
        },
        {
        "name": "CrEwSaDe",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(CrEwSaDe)$"
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
        "name": "DDR",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(DDR)$"
        }
        },
        {
        "name": "DepraveD",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(DepraveD)$"
        }
        },
        {
        "name": "DNL",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(DNL)$"
        }
        },
        {
        "name": "EPiC",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(EPiC)$"
        }
        },
        {
        "name": "EuReKA",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(EuReKA)$"
        }
        },
        {
        "name": "FaNGDiNG0",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(FaNGDiNG0)$"
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
        "name": "FRDS",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(FRDS)$"
        }
        },
        {
        "name": "FZHD",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(FZHD)$"
        }
        },
        {
        "name": "GalaxyRG",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(GalaxyRG)$"
        }
        },
        {
        "name": "GHD",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(GHD)$"
        }
        },
        {
        "name": "GPTHD",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(GPTHD)$"
        }
        },
        {
        "name": "HDS",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(HDS)$"
        }
        },
        {
        "name": "HDT",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(HDT)$"
        }
        },
        {
        "name": "HDTime",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(HDTime)$"
        }
        },
        {
        "name": "HDWinG",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(HDWinG)$"
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
        "name": "iPlanet",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(iPlanet)$"
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
        "name": "jennaortega",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(jennaortega(UHD)?)$"
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
        "name": "KiNGDOM",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(KiNGDOM)$"
        }
        },
        {
        "name": "KIRA",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(KIRA)$"
        }
        },
        {
        "name": "L0SERNIGHT",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(L0SERNIGHT)$"
        }
        },
        {
        "name": "LAMA",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(LAMA)$"
        }
        },
        {
        "name": "Leffe",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(Leffe)$"
        }
        },
        {
        "name": "Liber8",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(Liber8)$"
        }
        },
        {
        "name": "LiGaS",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(LiGaS)$"
        }
        },
        {
        "name": "MarkII",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(MarkII)$"
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
        "name": "mHD",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(mHD)$"
        }
        },
        {
        "name": "mSD",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(mSD)$"
        }
        },
        {
        "name": "MTeam",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(MTeam|MT)$"
        }
        },
        {
        "name": "MySiLU",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(MySiLU)$"
        }
        },
        {
        "name": "NhaNc3",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(NhaNc3)$"
        }
        },
        {
        "name": "nHD",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(nHD)$"
        }
        },
        {
        "name": "nikt0",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(nikt0)$"
        }
        },
        {
        "name": "NoGroup",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "NoGr(ou)?p"
        }
        },
        {
        "name": "nSD",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(nSD)$"
        }
        },
        {
        "name": "OFT",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(OFT)$"
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
        "name": "PATOMiEL",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(PATOMiEL)$"
        }
        },
        {
        "name": "PiRaTeS",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(PiRaTeS)$"
        }
        },
        {
        "name": "PRODJi",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(PRODJi)$"
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
        "name": "PTNK",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(PTNK)$"
        }
        },
        {
        "name": "RARBG",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(RARBG)$"
        }
        },
        {
        "name": "RDN",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(RDN)$"
        }
        },
        {
        "name": "RiffTrax",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(Rifftrax)$"
        }
        },
        {
        "name": "RU4HD",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(RU4HD)$"
        }
        },
        {
        "name": "SANTi",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(SANTi)$"
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
        "name": "Scene",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(Scene)$"
        }
        },
        {
        "name": "STUTTERSHIT",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(STUTTERSHIT)$"
        }
        },
        {
        "name": "SWTYBLZ",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(SWTYBLZ)$"
        }
        },
        {
        "name": "tarunk9c",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(tarunk9c)$"
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
        "name": "TEKNO3D",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(TEKNO3D)$"
        }
        },
        {
        "name": "Tigole",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(Tigole)$"
        }
        },
        {
        "name": "TIKO",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(TIKO)$"
        }
        },
        {
        "name": "VISIONPLUSHDR",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(VISIONPLUSHDR(-X|1000)?)$"
        }
        },
        {
        "name": "WAF",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(WAF)$"
        }
        },
        {
        "name": "WiKi",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(WiKi)$"
        }
        },
        {
        "name": "x0r",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(x0r)$"
        }
        },
        {
        "name": "YIFY",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(YIFY)$"
        }
        },
        {
        "name": "YTS",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(YTS(.(MX|LT|AG))?)$"
        }
        },
        {
        "name": "Zeus",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(Zeus)$"
        }
        }
    ]
    }
    ```

#### LQ (Release Title)

??? example "JSON [show/hide]"
    ```json
    {
    "trash_id": "e204b80c87be9497a8a6eaff48f72905",
    "trash_scores": {
        "default": -10000
    },
    "name": "LQ (Release Title)",
    "includeCustomFormatWhenRenaming": false,
    "specifications": [
        {
        "name": "1XBET",
        "implementation": "ReleaseTitleSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "\\b(1XBET)\\b"
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
        "name": "jennaortega",
        "implementation": "ReleaseTitleSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "(?<!-)\\b(jennaortega(UHD)?)\\b"
        }
        },
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
        "name": "Will1869",
        "implementation": "ReleaseTitleSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "\\b(Will1869)\\b"
        }
        }
    ]
    }
    ```

#### 3D

??? example "JSON [show/hide]"
    ```json
    {
    "trash_id": "b8cd450cbfa689c0259a01d9e29ba3d6",
    "trash_scores": {
        "default": -10000
    },
    "trash_regex": "https://regex101.com/r/c6Dobc/1",
    "name": "3D",
    "includeCustomFormatWhenRenaming": false,
    "specifications": [
        {
        "name": "3D",
        "implementation": "ReleaseTitleSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "(?<=\\b[12]\\d{3}\\b).*\\b(3d|sbs|half[ .-]ou|half[ .-]sbs)\\b"
        }
        },
        {
        "name": "BluRay3D",
        "implementation": "ReleaseTitleSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "\\b(BluRay3D)\\b"
        }
        },
        {
        "name": "BD3D",
        "implementation": "ReleaseTitleSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "\\b(BD3D)\\b"
        }
        }
    ]
    }
    ```

#### x265 (HD)

??? example "JSON [show/hide]"
    ```json
    {
    "trash_id": "dc98083864ea246d05a42df0d05f81cc",
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

You don't have to add this especially if you want the extra files)

??? example "JSON [show/hide]"
    ```json
    {
    "trash_id": "0a3f082873eb454bde444150b70253cc",
    "trash_scores": {
        "default": -10000
    },
    "trash_regex": "https://regex101.com/r/nzK5TQ/1",
    "name": "Extras",
    "includeCustomFormatWhenRenaming": false,
    "specifications": [
        {
        "name": "Extras",
        "implementation": "ReleaseTitleSpecification",
        "negate": false,
        "required": true,
        "fields": {
            "value": "(?<=\\b[12]\\d{3}\\b).*\\b(Extras|Bonus|Extended[ ._-]Clip)\\b"
        }
        }
    ]
    }
    ```

Like the Extras above these next Custom Formats are optional, but are recommended for our 1080p profile we're creating. (We're still adding via the step 1 method)

####  Bad Duel Groups

??? example "JSON [show/hide]"
    ```json
    {
    "trash_id": "b6832f586342ef70d9c128d40c07b872",
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
        "name": "ONLYMOViE",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(ONLYMOViE)$"
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
        "name": "TvR",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "^(TvR)$"
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

#### EVO (no WEBDL)

??? example "JSON [show/hide]"
    ```json
    {
    "trash_id": "90cedc1fea7ea5d11298bebd3d1d3223",
    "trash_scores": {
        "default": -10000
    },
    "name": "EVO (no WEBDL)",
    "includeCustomFormatWhenRenaming": false,
    "specifications": [
        {
        "name": "EVO",
        "implementation": "ReleaseGroupSpecification",
        "negate": false,
        "required": true,
        "fields": {
            "value": "^(EVO(TGX)?)$"
        }
        },
        {
        "name": "WEBDL",
        "implementation": "SourceSpecification",
        "negate": true,
        "required": true,
        "fields": {
            "value": 7
        }
        },
        {
        "name": "WEBRIP",
        "implementation": "SourceSpecification",
        "negate": true,
        "required": true,
        "fields": {
            "value": 8
        }
        }
    ]
    }
    ```

#### No-RisGroup

??? example "JSON [show/hide]"
    ```json
    {
    "trash_id": "ae9b7c9ebde1f3bd336a8cbd1ec4c5e5",
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
    "trash_id": "7357cf5161efbf8c4d5d0c30b4815ee2",
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
            "value": "(?<=\\b[12]\\d{3}\\b).*(Scrambled)\\b"
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
    "trash_id": "5c44f52a8714fdd79bb4d98e2673be1f",
    "trash_scores": {
        "default": -10000
    },
    "name": "Retags",
    "includeCustomFormatWhenRenaming": false,
    "specifications": [
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
        "name": "[rarbg]",
        "implementation": "ReleaseTitleSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "\\[rarbg\\]"
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
        "name": "[TGx]",
        "implementation": "ReleaseTitleSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "\\[TGx\\]"
        }
        },
        {
        "name": ".VAV",
        "implementation": "ReleaseTitleSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "[.]VAV\\b"
        }
        },
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
        "name": "ORARBG",
        "implementation": "ReleaseTitleSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": "\\b(ORARBG)\\b"
        }
        }
    ]
    }
    ```

#### Scene

??? example "JSON [show/hide]"
    ```json
    {
    "trash_id": "f537cf427b64c38c8e36298f657e4828",
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
            "value": "\\b(INFLATE|DEFLATE)\\b"
        }
        }
    ]
    }
    ```
### Streaming Providers

The following custom formats are for streaming providers, they are optional but are recommended to be added. (Still using step 1 method)

#### AMZN (Amazon Prime Video)

??? example "JSON [show/hide]"
    ```json
    {
    "trash_id": "b3b3a6ac74ecbd56bcdbefa4799fb9df",
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
            "value": 7
        }
        },
        {
        "name": "WEBRIP",
        "implementation": "SourceSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": 8
        }
        }
    ]
    }
    ```

#### ATVP (Apple TV+)

??? example "JSON [show/hide]"
    ```json
    {
    "trash_id": "40e9380490e748672c2522eaaeb692f7",
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
            "value": 7
        }
        },
        {
        "name": "WEBRIP",
        "implementation": "SourceSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": 8
        }
        }
    ]
    }
    ```


#### BCORE (Bravia Core)

??? example "JSON [show/hide]"
    ```json
    {
    "trash_id": "cc5e51a9e85a6296ceefe097a77f12f4",
    "trash_scores": {
        "default": 15,
        "sqp-1-1080p": -10000,
        "sqp-1-2160p": -10000
    },
    "name": "BCORE",
    "includeCustomFormatWhenRenaming": true,
    "specifications": [
        {
        "name": "Bravia Core",
        "implementation": "ReleaseTitleSpecification",
        "negate": false,
        "required": true,
        "fields": {
            "value": "\\b(BCORE)\\b"
        }
        },
        {
        "name": "WEBDL",
        "implementation": "SourceSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": 7
        }
        },
        {
        "name": "WEBRIP",
        "implementation": "SourceSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": 8
        }
        }
    ]
    }
    ```

#### CRIT (Criterion Channel)

??? example "JSON [show/hide]"
    ```json
    {
    "trash_id": "16622a6911d1ab5d5b8b713d5b0036d4",
    "trash_scores": {
        "default": 20
    },
    "name": "CRiT",
    "includeCustomFormatWhenRenaming": true,
    "specifications": [
        {
        "name": "CRiT",
        "implementation": "ReleaseTitleSpecification",
        "negate": false,
        "required": true,
        "fields": {
            "value": "\\b(CRiT)\\b"
        }
        },
        {
        "name": "WEBDL",
        "implementation": "SourceSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": 7
        }
        },
        {
        "name": "WEBRIP",
        "implementation": "SourceSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": 8
        }
        },
        {
        "name": "Not Criterion RlsGrp",
        "implementation": "ReleaseGroupSpecification",
        "negate": true,
        "required": true,
        "fields": {
            "value": "^(Criterion)$"
        }
        }
    ]
    }
    ```


#### DSNP (Disney+)

??? example "JSON [show/hide]"
    ```json
    {
    "trash_id": "84272245b2988854bfb76a16e60baea5",
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
            "value": 7
        }
        },
        {
        "name": "WEBRIP",
        "implementation": "SourceSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": 8
        }
        }
    ]
    }
    ```

#### HBO (HBO)

??? example "JSON [show/hide]"
    ```json
    {
    "trash_id": "509e5f41146e278f9eab1ddaceb34515",
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
            "value": 7
        }
        },
        {
        "name": "WEBRIP",
        "implementation": "SourceSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": 8
        }
        }
    ]
    }
    ```

#### HMAX (HBO Max)

??? example "JSON [show/hide]"
    ```json
    {
    "trash_id": "5763d1b0ce84aff3b21038eea8e9b8ad",
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
            "value": 7
        }
        },
        {
        "name": "WEBRIP",
        "implementation": "SourceSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": 8
        }
        }
    ]
    }
    ```

#### Hulu (Hulu)

??? example "JSON [show/hide]"
    ```json
    {
    "trash_id": "526d445d4c16214309f0fd2b3be18a89",
    "name": "Hulu",
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
            "value": 7
        }
        },
        {
        "name": "WEBRIP",
        "implementation": "SourceSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": 8
        }
        }
    ]
    }
    ```


#### Max (Max Streaming Service)

??? example "JSON [show/hide]"
    ```json
    {
    "trash_id": "6a061313d22e51e0f25b7cd4dc065233",
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
            "value": 7
        }
        },
        {
        "name": "WEBRIP",
        "implementation": "SourceSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": 8
        }
        }
    ]
    }
    ```

#### MA (Movies Anywhere)

??? example "JSON [show/hide]"
    ```json
    {
    "trash_id": "2a6039655313bf5dab1e43523b62c374",
    "trash_scores": {
        "default": 20
    },
    "name": "MA",
    "includeCustomFormatWhenRenaming": true,
    "specifications": [
        {
        "name": "Movies Anywhere",
        "implementation": "ReleaseTitleSpecification",
        "negate": false,
        "required": true,
        "fields": {
            "value": "(?<!dts[ .-]?hd[ .-]?)ma\\b(?=.*\\bweb[ ._-]?(dl|rip)\\b)"
        }
        }
    ]
    }
    ```

#### NF (Netflix)

??? example "JSON [show/hide]"
    ```json
    {
    "trash_id": "170b1d363bd8516fbf3a3eb05d4faff6",
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
            "value": 7
        }
        },
        {
        "name": "WEBRIP",
        "implementation": "SourceSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": 8
        }
        }
    ]
    }
    ```

#### PCOK (Peacock TV)

??? example "JSON [show/hide]"
    ```json
    {
    "trash_id": "c9fd353f8f5f1baf56dc601c4cb29920",
    "name": "PCOK",
    "includeCustomFormatWhenRenaming": true,
    "specifications": [
        {
        "name": "Peacock TV",
        "implementation": "ReleaseTitleSpecification",
        "negate": false,
        "required": true,
        "fields": {
            "value": "\\b(pcok|peacock)\\b"
        }
        },
        {
        "name": "WEBDL",
        "implementation": "SourceSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": 7
        }
        },
        {
        "name": "WEBRIP",
        "implementation": "SourceSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": 8
        }
        }
    ]
    }
    ```


#### PMTP (Paramount+)

??? example "JSON [show/hide]"
    ```json
    {
    "trash_id": "e36a0ba1bc902b26ee40818a1d59b8bd",
    "name": "PMTP",
    "includeCustomFormatWhenRenaming": true,
    "specifications": [
        {
        "name": "Paramount+",
        "implementation": "ReleaseTitleSpecification",
        "negate": false,
        "required": true,
        "fields": {
            "value": "\\b(pmtp|Paramount Plus)\\b"
        }
        },
        {
        "name": "WEBDL",
        "implementation": "SourceSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": 7
        }
        },
        {
        "name": "WEBRIP",
        "implementation": "SourceSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": 8
        }
        }
    ]
    }
    ```

#### STAN (Stan)

??? example "JSON [show/hide]"
    ```json
    {
    "trash_id": "c2863d2a50c9acad1fb50e53ece60817",
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
            "value": 7
        }
        },
        {
        "name": "WEBRIP",
        "implementation": "SourceSpecification",
        "negate": false,
        "required": false,
        "fields": {
            "value": 8
        }
        }
    ]
    }
    ```

## Quality Profiles

Okay that's all the custom formats we will need for the 1080p Radarr setup, in the next section we will be adding a quality profile so we can match our custom formats to a profile to search for movies using our custom formats we've just added.

### Quality Profile (1080p)

Okay, so now we need to navigate to radarrs settings page once again, but this time we're going to click on Profiles.

You should see a plus button similar to the page where we added custom formats, go ahead and click the plus button and you'll be presented with a page called "Add Quality Profile"

The information needed to fill the form is below.

* Name: HD Bluray + WEB
* Upgrade allowed: Check the upgrades allowed box ✅
* Upgrade until quality: Set this to Bluray-1080p
* Minimum custom format score: 0
* Upgrade until custom format score: 10000
* Language: Original

On the right hand side of the screen (Below on mobile) you should see a bunch of qualities, we're going to mark and put them in a certain order, this order must be followed exactly if it is not the profile won't grab and upgrade as expected.

1. Bluray-1080p ✅
2. WEB 1080p ✅
3. Bluray-720p ✅

Once those qualities are checked we need to move them to the top of the list (drag and drop) in the order I've displayed them here.

Once they are in the correct order we can move onto scoring the custom formats for the quality profile we've just created.

### Scoring

In this section we're going to add the scores to the custom formats so that radarr can sort through the qualities it pulls correctly, according to our rules we've set, ready? Let's begin.

To add the scores look below the qualities and you'll see a section full of the custom formats we added with box's titled "Score" on the right hand side of them, you input the below scores in this box next to the same custom format.

(Movie Versions)

1. Remaster - 25
2. 4K Remaster - 25
3. Criterion Collection - 25
4. Masters of Cinema - 25
5. Vinegar Syndrome - 25
6. Special Edition - 125
7. IMAX - 800
8. IMAX Enhanced - 800

(HQ Release Groups)

1. HD Bluray Tier 1 - 1800
2. HD Bluray Tier 2 - 1750
3. HD Bluray Tier 3 - 1700
4. WEB Tier 1 - 1700
5. WEB Tier 2 - 1650
6. WEB Tier 3 - 1600

(Misc)


1. Repack/Proper - 5
2. Repack2 - 6

(Unwanted)

1. BR-DISK - (-10000)
2. LQ - (-10000)
3. LQ (Release Title) - (-10000)
4. x264 (HD) - (-10000)
5. 3D - (-10000)
6. Extras - (-10000)

(Optional)

1. Bad Duel Groups - (-10000)
2. EVO (no WEBDL) - (-10000)
3. No-RlsGroup - (-10000)
4. Obfuscated - (-10000)
5. Retags - (-10000)
6. Scene - (-10000)

(General Streaming Services)

1. AMZN - 0
2. ATVP - 0
3. BCORE - 15
4. CRiT - 20
5. DSNP - 0
6. HBO - 0
7. HMAX - 0
8. Hulu - 0
9. MAX - 0
10. MA - 20
11. NF - 0
12. PMTP - 0
13. PCOK - 0
14. STAN - 0

### Breakdown and Why (General Streaming Services)

The reason why these Custom Formats have a score of 0 is because they are mainly used for the naming scheme and other variables should decide for movies if a certain release if preferred.

BCore, CRiT and MA are the only ones with a score because of their better source material, or higher bitrate and quality compared to other streaming services. However you can score these as you wish.

That's it for radarr 1080p Custom Formats there are some "Special Quality Profiles" regarding this 1080p profile but for those you'll have to dive into the trash guides discord and search for them as per the rules of trash guides. I cannot share these publicly however the same steps apply to inputting those custom formats as we've seen here.

I hope this guide helped, if it did please show ElfHosted some love! 💟

--8<-- "common-links.md"