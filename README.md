# Web Paroki Content Repository

This repository stores all content for the Web Paroki CMS. Content is primarily stored in JSON format, with images stored in the `images` directory.

## Structure

```
web-paroki-content/
├── posts/                  # Blog posts in JSON format
├── images/
│   ├── banners/            # Banner images (1920x1080 max, converted to WebP)
│   └── inline/             # Inline images (1200x1200 max, converted to WebP)
├── jadwal-kegiatan.json    # Event schedule data
├── statistik.json          # Parish statistics
├── umkm.json               # UMKM directory data
├── wilayah-lingkungan.json # Ward and Neighborhood hierarchy
├── pastor-tim-kerja.json   # Pastor and Team directory
└── README.md
```

## How Content is Managed

Content is managed through the Web Paroki CMS admin panel at `/admin` (in the main web application).
All changes made in the CMS are automatically committed to this repository.

## Content Schemas

### Posts (`posts/*.json`)

Posts are stored as individual JSON files in the `posts/` directory.

```json
{
  "frontmatter": {
    "title": "String",
    "slug": "String (unique-identifier)",
    "description": "String",
    "publishedAt": "ISO Date String",
    "author": "String",
    "categories": ["String"],
    "banner": "String (path to image)",
    "published": "Boolean"
  },
  "content": {
    "ops": [ ... ] // Quill Delta format
  }
}
```

### Jadwal Kegiatan (`jadwal-kegiatan.json`)

Stores the schedule of upcoming and past events.

```json
[
  {
    "id": "UUID",
    "title": "String",
    "date": "YYYY-MM-DD",
    "time": "HH:mm",
    "location": "String",
    "description": "String",
    "category": "String"
  }
]
```

### Statistik (`statistik.json`)

General statistics about the parish.

```json
{
  "churches": "Number",
  "wards": "Number",
  "families": "Number",
  "parishioners": "Number",
  "lastUpdated": "ISO Date String"
}
```

### UMKM (`umkm.json`)

Directory of local businesses (UMKM).

```json
[
  {
    "id": "UUID",
    "businessName": "String",
    "owner": "String",
    "address": "String",
    "phone": "String",
    "type": "String",
    "description": "String"
  }
]
```

### Wilayah & Lingkungan (`wilayah-lingkungan.json`)

Hierarchical data of Wards (Wilayah) and Neighborhoods (Lingkungan).

```json
[
  {
    "id": "UUID",
    "name": "String (Wilayah Name)",
    "coordinator": "String (Wilayah Coordinator)",
    "address": "String",
    "email": "String",
    "phone": "String",
    "lingkungan": [
      {
        "id": "UUID",
        "name": "String (Lingkungan Name)",
        "chief": "String (Lingkungan Chief)",
        "address": "String",
        "email": "String",
        "phone": "String"
      }
    ]
  }
]
```

### Pastor & Tim Kerja (`pastor-tim-kerja.json`)

Directory for Pastors and Work Teams.

```json
{
  "pastor": [
    {
      "id": "UUID",
      "name": "String",
      "role": "String",
      "imageUrl": "String",
      "description": "String",
      "quote": "String (Optional)",
      "email": "String (Optional)",
      "phone": "String (Optional)"
    }
  ],
  "timKerja": [
    {
      "id": "UUID",
      "name": "String",
      "role": "String",
      "division": "String",
      "quote": "String (Optional)",
      "email": "String (Optional)",
      "phone": "String (Optional)"
    }
  ]
}
```
