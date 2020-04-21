# nodered
Git repository for Node-RED project

DatabaseFiles-kansiossa pohja valostatuksille. Tämä syötetään MongoDB:seen. MongoDB nodet konffaattava oman DB:n mukaan.
Flowssa on pätkä, jolla pystyy filun lataamaan DB:seen.
Simusta valo-nappia klikattaessa lähettää msg:n MQTT:n avulla, missä payloadissa napin nimi ja huoneen numero.
Ohjelma haistelee MongoDB:stä, oliko valo päällä ennen valonappia klikattaessa vai ei. Jos ei ollut, asettaa ilmanvaihdon 30% teholle. Jos oli, ottaa sen pois päältä.
Voi myös syöttää manuaalisesti arvoja, nämäkin päivittyy DB:seen. Arvo 0 on sama asia kuin ilmastointi pois päältä.

Mitään historia-lokia ei ole tähän (ainakaan vielä) toteutettu.

21.4: Uusi formaatti MongoDB:seen tehonsäädön vuoksi. Jos MongoDB on jo alustettu, niin uuden fieldin saa lisättyä mongon komentorivioperaatiolla: 
    > db.lights.update({"_id":1},{$set:{"defaultPower" : 30}}). Pitää vain toistaa joka _id:lle.

