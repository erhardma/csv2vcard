#asv to vcard
This script produces vcard-files in the export directory. The Input-File is generated by the ASV, the "Amtliche Schulverwaltung" of Bavaria.
You can create an "Exportformat" with the fields
Familienname
Rufname
Telefonnummer
Handynummer
Skript 6

where Skript 6 is a script to generate the birthdate in the necessary format:
´´´
if (obj?.lehrerStamm.geburtsdatum != null) {
   // Feldwert zurückgeben
    def bday = obj?.lehrerStamm?.geburtsdatum.format("yyyy-MM-dd")
} else {
   // Entwertungszeichen oder Text zurückgeben
   def bday = ""
}

´´
![image](https://user-images.githubusercontent.com/54348970/216435367-7b57d34b-316d-4e88-9a60-000f614cf39c.png)



This script is based on the following script:

[![Downloads](http://pepy.tech/badge/csv2vcard)](http://pepy.tech/count/csv2vcard)

csv2vcard
=========
A Python script that parses a .csv file of contacts and automatically creates vCards. The vCards are super useful for sending your contact details or those of your team. You can also upload them to e.g. Dropbox and use them with QR codes! You can also use them for transferring new contacts to Outlook, a new CRM etc. The specific use case in mind was to programmatically create vCards from a list of contacts in a spreadsheet, to be incorporated into business cards.

Usage
-----

1. Install package with `pip3 install csv2vcard`

2. Create csv file with contacts

*CSV file format (delimeter can be changed in csv_delimeter param, see below)*

`last_name, first_name, org, title, phone, email, website, street, city, p_code, country`

**Important: you should name the columns exactly the same way because they are used as keys to generate the vCards**

3. `cd yourcsvfoldername` go to the folder where you have your csv file

4. Open python `python3` (gotcha: using Python 3.6 features)

5. Import module `from csv2vcard import csv2vcard`

6. Now you have 2 options for running (both will create an /export/ dir for your vCard):

- Test the app with `csv2vcard.test_csv2vcard()`. This will create a Forrest Gump test vCard.
- Use your real data `csv2vcard.csv2vcard("yourcsvfilename", ",")` where ","  is your csv delimeter. This will create all your vCards.
