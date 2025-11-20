# Seminaarityo_Tekoalymalli
Virallinen raportti työhön löytyy erillisenä pdf palautuksena teamsissa, sekä myös video työn esittelystä 

Ohessa lähdekoodi ja viimeinen mallin koulutukseen käytetty csv tiedosto. 

Tämä skripti kouluttaa LSTM-neuroverkon ennustamaan kirjaston/palvelun päivittäisiä total check-in -määriä historiallisten tietojen perusteella.
Koodi:

Lataa ja esikäsittelee datan (model_training.csv)

Kouluttaa LSTM-mallin

Arvioi mallin suorituskykyä testidatalla

Ennustaa seuraavat 50 päivää

Piirtää sekä oppimiskäyrät että historialliset vs. ennustetut check-init

1. Vaatimukset

Skripti on suunniteltu ajettavaksi Google Colabissa, mutta sen voi ajaa myös paikallisesti.

Python-kirjastot

Tarvitset vähintään seuraavat paketit:

numpy

pandas

matplotlib

scikit-learn (sklearn)

tensorflow (sis. keras)

google.colab (vain jos ajat Colabissa – tämä on valmiina Colab-ympäristössä)

Jos ajat paikallisesti, voit asentaa paketit esimerkiksi:

pip install numpy pandas matplotlib scikit-learn tensorflow


Huom: google.colab-moduuli ei ole käytettävissä paikallisesti. Tällöin sinun pitää poistaa tai korvata from google.colab import files ja files.upload() -kohdat ja lukea CSV suoraan levyhaku-polusta.

2. Data: model_training.csv

Skriptin odottama CSV-tiedosto:

Tiedoston nimi: model_training.csv

Sarakkeita mm.:

date_only (päivämäärä)

Weekday

Season

day_type

total_checkins_per_day

Lisäksi sarakkeet Hanze, RUG, Staff, daily_men_checkins, daily_women_checkins, jotka skripti pudottaa pois.

Tiedoston tulee olla:

Colabissa: ladattavissa käyttöliittymän kautta (files.upload()).

Paikallisesti: samassa hakemistossa kuin Python-skripti (tai polku päivitetty path-muuttujaan).

3. Ajaminen Google Colabissa

Avaa Google Colab
.

Luo uusi Notebook tai lataa tämä skripti notebook-muotoon.

Varmista, että käytät Python 3 -ympäristöä ja GPU-tukea jos haluat nopeuttaa koulutusta (Valinnainen: Runtime → Change runtime type → Hardware accelerator: GPU).

Suorita solut, kunnes saavut riviin:

from google.colab import files
uploaded = files.upload()


Valitse model_training.csv omalta koneeltasi, kun Colab pyytää tiedostoa.

Jatka kaikkien solujen suorittamista ylhäältä alas.

Skriptin suorituksen aikana:

Malli tallennetaan tiedostoon daily_checkins.keras (paras validointitulos).

Konsoliin tulostuu:

Lopullinen validointihäviö (MSE)

Validointimae (MAE)

Testijoukon R², MAE, MSE

Näytölle piirretään:

Koulutuksen ja validoinnin häviökäyrä

Historialliset ja ennustetut check-init (2021-01-01 alkaen)

4. Ajaminen paikallisesti (ilman Colabia)

Tallenna skripti esimerkiksi nimellä train_lstm.py.

Varmista, että model_training.csv on samassa hakemistossa tai päivitä:

path = 'model_training.csv'


vastaamaan oikeaa sijaintia.

Poista tai kommentoi Colab-riippuvaiset rivit:

from google.colab import files
uploaded = files.upload()
