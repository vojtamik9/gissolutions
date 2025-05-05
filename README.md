from PIL import Image
import requests
import streamlit as st
from streamlit import container
from streamlit_lottie import st_lottie
st.set_page_config(page_title="GISSOLUTIONS", page_icon=":herb:", layout= "wide")

def load_lottieurl(url):
    r = requests.get(url)
    if r.status_code != 200:
        return None
    return r.json()

def local_css(file_name):
    with open(file_name)as f:
        st.markdown(f"<style>{f.read()}</style>", unsafe_allow_html=True)

local_css("style/style.css")

lottie_coding = load_lottieurl("https://lottie.host/6c88b0ca-c91f-4d3a-8038-4e53800c7848/UuyjSawI1l.json")
img_contact_form = Image.open("obrazky/rychory.png")
img_lottie_animation = Image.open("obrazky/horizont_1.jpg")
lottie_social_media = load_lottieurl("https://lottie.host/0fa62cd9-f87a-4701-a007-d3eb24db9b94/QXGBbwipEk.json")

with st.container():
    st.title("GISSOLUTIONS")
    st.subheader("Firma z Olomouce specializující se na dronové zpracování dat a jejich analýzu")
    st.write("Snímáme drony, provádíme analýzy dat, nabízíme poradenství v GIS, všechny naše úkony pomohou vám a vaší firmě efektivněji hospodařit")
    st.write(
        """ 
             V GISSOLUTIONS se za pomoci dronů, satelitních dat a GIS softwarů, snažíme digitalizovat plochy zájmových území a chystat tyto plochy 
             pro chytré a autonomní hospodaření. Pomocí nasbíraných dat, Vám pomůžeme vytěžit co největší množství informací o zájmových plochách 
             a poskytneme Vám data, která zefektivní Vaše další hospodaření.     
        """
    )
    st.write("Pokud máte zájem o naše služby vyplňte tento zakázkový formulář, který nám odešlete rovnou do e-mailu > formulář")

    with st.container():
        st.write("---")
        left_column, right_column = st.columns(2)
        with left_column:
            st.header("Co děláme?")
            st.write(
               """ 
                Naše služby pokrývají široké spektrum aktivit:
                - dronové snímání 
                - analýza dat
                - práce se satelitními daty
                - poradenství v GIS 
                """
        )
    with right_column:
        st.lottie(lottie_coding, height=300, key="coding")

with st.container():
    st.write("---")
    st.header("Naše práce")
    st.write("##")
    image_column, text_column = st.columns((1, 2))
    with image_column:
        st.image(img_lottie_animation)


    with text_column:
        st.subheader("Vývoj využití a struktury krajiny v lokalitách zaniklého osídlení - případová studie Malé Moravy")
        st.write(
             """
             Diplomová práce Mgr. Vojtěcha Mikulenky, která se zabývá historickým vývojem krajiny v lokalitě Malé Moravy. "
             Práce na základě vytvoření rozsáhlého souboru dat umožňuje pozorovat vývoj krajiny do dnešních dnů a pomáhá chápat souvislosti, které utváří charakter současné krajiny")
             """
        )
        st.markdown("Odkaz na celý text zde (https://theses.cz/id/0wh1zn/Vyvoj_vyuziti_a_struktury_krajiny_v_lokalitach_zanikleho_.pdf)")

with st.container():
    image_column, text_column = st.columns((1, 2))
    with image_column:
        st.image(img_contact_form)
    with text_column:
        st.subheader("Vývoj ekologické stability v oblasti Rýchor")
        st.write(
            """
            Diplomová práce Mgr. Milana Viktoříka, která se zabývá problematikou ekologické stability na území Krkonošského národního parku, konkrétně na území Rýchor.
            """
            )
        st.markdown("Odkaz na celý text práce zde:(https://theses.cz/id/57ea72/Vyvoj_ekologicke_stability_v_oblasti_Rychor.pdf?lang=cs)")

# --- KONTAKTY ---
with st.container():
    st.write("---")
    st.header("Zaujala Vás naše práce? Napište nám o zakázku na míru")
    st.write("##")

    contact_form = """
    <form action="https://formsubmit.co/gissolutions.cr@gmail.com" method="POST">
         <input type="hidden" name="_captcha" value="false">  
         <input type="text" name="name" placeholder="Vaše jméno" required>
         <input type="email" name="email" placeholder="Váš e-mail" required>
         <textarea name="message" placeholder="Popište nám Vaši zakázku" required></textarea>
         <button type="submit">Odeslat</button>
    </form>
    """
    left_column, right_column = st.columns(2)
    with left_column:
        st.markdown(contact_form, unsafe_allow_html=True)
    with right_column:
        st.empty()

# --- ZÁHLAVÍ ---
with st.container():
    st.write("---")
    st.markdown("<h2 style='text-align: center;'>Kde nás najdete?</h2>", unsafe_allow_html=True)
    left_column, right_column = st.columns(2)
    with left_column:
        st.subheader("Kontaktní údaje")
        st.write(
            """
            e-mail: 
            - gissolutions.cr@gmail.com
            """
            )
        st.write(
            """
            kontaktní osoby:
            - Mgr. Vojtěch Mikulenka - tel. 607 143 028
            - Mgr. Milan Viktořík - tel. 604 615 037
            """
            )
        st.markdown(
            """
            sociální sítě:
            - Facebook: https://www.facebook.com/
            - Instagram: GISSOLUTIONS
            """
            )
    with right_column:
        st.lottie(lottie_social_media, height=400, key="coding1")
