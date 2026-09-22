# JSON-LD Template — Splendido apartmani

Koristiti za splendido.hr stranice apartmana. Zamijeniti sve `{{PLACEHOLDER}}` vrijednosti.

## Apartment schema

```json
{
  "@context": "https://schema.org",
  "@type": "Apartment",
  "name": "{{IME_APARTMANA}}",
  "description": "{{KRATKI_OPIS_EN}}",
  "url": "https://splendido.hr/en/baska/apartment/{{SLUG}}",
  "image": [
    "https://splendido.hr/images/{{SLUG}}/main.jpg"
  ],
  "numberOfRooms": {{BROJ_SOBA}},
  "floorSize": {
    "@type": "QuantitativeValue",
    "value": {{POVRSINA_M2}},
    "unitCode": "MTK"
  },
  "occupancy": {
    "@type": "QuantitativeValue",
    "minValue": 1,
    "maxValue": {{MAX_GOSTI}}
  },
  "amenityFeature": [
    {"@type": "LocationFeatureSpecification", "name": "WiFi", "value": true},
    {"@type": "LocationFeatureSpecification", "name": "Air conditioning", "value": {{AC_TRUE_FALSE}}},
    {"@type": "LocationFeatureSpecification", "name": "Parking", "value": {{PARKING_TRUE_FALSE}}}
  ],
  "address": {
    "@type": "PostalAddress",
    "streetAddress": "{{ADRESA}}",
    "addressLocality": "Baška",
    "postalCode": "51523",
    "addressCountry": "HR"
  },
  "geo": {
    "@type": "GeoCoordinates",
    "latitude": 44.9697,
    "longitude": 14.7572
  },
  "containedInPlace": {
    "@type": "LodgingBusiness",
    "name": "Splendido d.o.o.",
    "url": "https://splendido.hr",
    "telephone": "{{TELEFON}}",
    "email": "info@splendido.hr"
  }
}
```

## FAQ schema (dodati ispod Apartment bloka)

```json
{
  "@context": "https://schema.org",
  "@type": "FAQPage",
  "mainEntity": [
    {
      "@type": "Question",
      "name": "Where is {{IME_APARTMANA}} located?",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "{{IME_APARTMANA}} is located in Baška, on the island of Krk, Croatia. {{UDALJENOST_PLAZA_CENTAR}}"
      }
    },
    {
      "@type": "Question",
      "name": "How many guests can stay in {{IME_APARTMANA}}?",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "{{IME_APARTMANA}} accommodates up to {{MAX_GOSTI}} guests."
      }
    },
    {
      "@type": "Question",
      "name": "Is parking available at {{IME_APARTMANA}}?",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "{{PARKING_ODGOVOR_EN}}"
      }
    }
  ]
}
```

## Napomene

- Oba JSON-LD bloka idu u `<script type="application/ld+json">` tag u `<head>` ili na dno stranice
- `latitude` i `longitude` su za centar Baške — zamijeniti preciznijim ako poznato
- `{{SLUG}}` = URL-friendly ime apartmana (mala slova, crtice, bez dijakritika)
- Amenity lista: dodavati/uklanjati prema stvarnim podacima apartmana
