# Data Dictionary – NordTech Solutions

## Identifierare
| Kolumn | Beskrivning |
|------|-------------|
| order_id | Unikt ID för varje order. En order kan innehålla flera orderrader. |
| orderrad_id | Unikt ID för varje orderrad. |
| kund_id | Unikt ID för kund. |

## Datum & tid
| Kolumn | Beskrivning |
|------|-------------|
| orderdatum | Rå orderdatum i inkonsekventa textformat. |
| leveransdatum | Rå leveransdatum i inkonsekventa textformat. |
| orderdatum_dt | Rensat orderdatum i datetime-format. |
| leveransdatum_dt | Rensat leveransdatum i datetime-format. |
| leveranstid_dagar | Antal dagar mellan orderdatum och leveransdatum. Skapad kolumn. |
| vecka | Kalendervecka för orderdatum. Skapad för tidsanalys. |
| månad | Månad för orderdatum. Skapad för säsongsanalys. |

## Produkt & order
| Kolumn | Beskrivning |
|------|-------------|
| produkt_sku | Produktens SKU (artikelnummer). |
| produktnamn | Produktens namn. |
| kategori | Produktkategori (rensad och standardiserad). |
| antal | Antal beställda enheter per orderrad. Konverterad till numeriskt värde. |
| pris_per_enhet | Rå prisinformation i textformat. |
| pris_enhet_sek | Rensat pris per enhet i SEK (float). |
| rad_total | Totalt värde per orderrad (antal × pris_enhet_sek). |

## Kund & betalning
| Kolumn | Beskrivning |
|------|-----------|
| kundtyp | Typ av kund (Privat / Företag). |
| region | Kundens region. Rensad och standardiserad. |
| betalmetod | Betalningsmetod. Normaliserad (Kort, Swish, Faktura). |
| leveransstatus | Leveransstatus. Saknade värden ersatta med “Okänd”. |

## Recension & sentiment
| Kolumn | Beskrivning |
|------|-------------|
| recension_text | Kundens fritextrecension. |
| recensionsdatum | Datum då recensionen skrevs. |
| betyg | Numeriskt betyg (1–5). |
| sentiment | Klassificerat sentiment (Positiv, Neutral, Negativ, Ingen recension) baserat på BERT-modell. |

## Datatvätt – sammanfattning
- Datum standardiserades från flera format
- Priser rensades från text och konverterades till numeriska värden
- Kategoriska fält normaliserades
- Rader utan giltigt pris exkluderades
- Ordrar med 0 kr exkluderades vid AOV-beräkning
- Sentimentanalys genomfördes med förtränad BERT-modell
