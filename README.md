# MiData Sanity Checks
This Streamlit Python script can be used to check and standardize all the users in [MiData](https://db.scout.ch/de/).

The App is deployed in the Streamlit Community Cloud under https://midata-checks.streamlit.app

## MiData
MiData is the member database of PBS (Pfadi Bewegung Schweiz)\
It is based on hitobito, the Github Repo can be found [here](https://github.com/hitobito/hitobito_pbs)

## How to use it
- Login in to MiData and Make sure it is in German
- Navigate to the layer you want to check
- Select the Tab "Personen"
- Export "Alle Angaben" (Export → Excel → Alle Angaben)
- Upload to this App and run the desired checks.


## Available Checks:
### Duplikate

### Doppelte Rollen
Checks if there are duplicated entries, based on "Vorname" and "Nachname"
### Ungültige Adresse
Verifies if all Address Fields are filled in and hold valid Data.\
**Regex used to check:**\
Strasse: ^[/ ()'A-Za-záàâäéèêëíìîïóòôöúùûüÁÀÂÄÉÈÊËÍÌÎÏÓÒÔÖÚÙÛÜ.-]+$\
Hausnummer: ^[0-9]{1,3}[a-z]{0,1}$\
PLZ: ^[0-9]{4}$\
Ort: ^[A-Z][ /()'A-Za-zäöüÄÖÜéèêëáàâô.-]+$\
Land: Schweiz

### Ungültige AHV-Nr.
Checks if an AHV-Nr was added and if it is valid.\
**Regex:** 756\.[0-9]{4}+\.[0-9]{4}+\.[0-9]{2}
### Ungültige E-Mail
Checks if at least one E-Mail field is filled in and if all of them are valid.\
**Regex:** ^[A-Za-z0-9._%+-]+@[A-Za-z0-9.-]+\.[A-Za-z]{2,}$
### Ungültige Tel Nr.
Allows you to select a specific column (containing "Telefonnummer") you want to check.\

You can then select if you want to check for a specific type. (Mobile or Landline Number) This is checked based on the beginning of the Number.\

After that you can select the desired format. (All that don't match this will be listed)

### Leere Felder
This allows you to select one or more columns.
The App then checks if they are empty.\
You can select if all of the selected columns need to be empty to be listed or just one is enough.

### Custom Regex
This check allows you to select a column and enter you own Regex.
You can the decided if all of the matching or not matching columns are shown.
