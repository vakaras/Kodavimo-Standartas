===================
Kodavimo standartas
===================

.. role:: identifier(literal)

.. default-role:: identifier

.. toctree:: 
  :maxdepth: 1

Pratarmė
========

Šiame dokumente pateiktas stiliaus, kurio turėtų būti laikomasi 
programuojant aprašymas. Kol kas jis apibrėžia tik programavimą
**Python** programavimo kalba. Dokumentą sudaro trys dalys:

+   bendrieji reikalavimai – reikalavimai, kurie nepriklauso nuo to kam
    yra skirtas kuriamasis projektas;
+   lietuviško kodo reikalavimai – reikalavimai, apibrėžiantys kaip turėtų
    būti rašomas kodas, kuris dėl kokių nors priežasčių negali būti
    internacionalizuotas;
+   internacionalizuoto kodo reikalavimai – reikalavimai, apibrėžiantys
    kaip turėtų būti rašomas kodas, kurį galima internacionalizuoti.

Bendrieji reikalavimai
======================

------
Python
------

Visais šiame dokumente neaprašytais atvejais turėtų būti laikomasi
`PEP 8 <http://www.python.org/dev/peps/pep-0008/>`_.

Kodo išdėstymas
---------------

+   `ID:1` Tam pačiam blokui priklausantis kodas nuo krašto atitraukiamas
    vienodai.
+   `ID:2` Atitraukimo žingsnis lygus dviem tarpo simboliams.
+   `ID:3` Kodo eilutės negali būti ilgesnės nei 76 simboliai.
+   `ID:7` Teksto eilutės (dokumentacija ir komentarai) negali būti
    ilgesnės nei 72 simboliai.
+   `ID:6` Jei funkcijos kvietimas, masyvo aprašymas ir panašiai netelpa
    toje pačioje eilutėje, pirmas narys turi būti naujoje eilutėje ir
    visi nariai turi būti atitraukti taip pažymint, kad yra pratęsiama
    ankstesnė eilutė.

    .. code-block:: python

        some_set = set([
            first_element, second_element, third_element,])
        book = Book.objects.filter(
            author=author, title=title)[0]
        
+   `ID:4` Kodo eilutė laužiama po operatoriaus. Pavyzdžiui:

    .. code-block:: python

        if ((very_long_function() and other_very_long_function()) or
            some_variable):

            do_stuff()

+   `ID:8` Ilgos eilutės pratęsimui turėtų būti naudojami skliausteliai, o
    ne įžambusis brūkšnys („\“). Pavyzdžiui:

    .. code-block:: python

        long_string = (
                u'This is very long string. '
                u'Very long.')

+   `ID:9` Aukščiausio lygio funkcijų ir klasių aprašymai turėtų būti
    atskirti pora tuščių eilučių.
+   `ID:10` Negalima naudoti sudėtinių (keletas sakinių toje pačioje
    eilutėje) sakinių. Pavyzdžiui:

    .. code-block:: python
        
        if foo == 'blah': do_blah_thing()
        do_one(); do_two(); do_three()

    Turėtų būti:

    .. code-block:: python

        if foo == 'blah':
            do_blah_thing()
        do_one()
        do_two()
        do_three()

+   `ID:15` Teksto eilutės privalo būti tipo ``unicode`` **Python 2.***
    ir tipo ``str`` **Python 3.***. Python 2.* pavyzdys:

    .. code-block:: python

        some_text = u'Some text.'

+   `ID:16` Baitų eilutės privalo būti tipo ``str`` **Python 2.*** ir
    tipo ``bytes`` **Python 3.***. Python 3.* pavyzdys:

    .. code-block:: python

        some_bytes = b'<html>'

+   `ID:27` Į nekeičiamų (immutable) konteinerių vidų galima dėti tik
    nekeičiamo tipo objektus. Pavyzdžiui, taip negalima:

    .. code-block:: python

        book = (title, [author1, author2])

+   `ID:31` Numatytieji funkcijų argumentų reikšmės gali būti tik
    nekintami objektai. Pavyzdžiui, taip negalima:

    .. code-block:: python

        def foo(bar=[]):
            ...

    Turėtų būti:

    .. code-block:: python

        def foo(bar=()):
            ...

+   `ID:28` Visos klasės turi būti naujo tipo Python klasės. (Tai yra
    Python 2.* klasės būtinai turi paveldėti iš ``object``.)

Tarpai
------

+   `ID:5` Simbolis esantis kairėje naujos eilutės simbolio, negali būti
    tarpo simbolis.

Komentarai
----------

Komentarai gali būti dviejų tipų:

+   `ID:11` blokiniai – aprašo kodą, kuris yra po jais, ir yra išlygiuoti
    kartu su juo. Kiekviena komentaro eilutė prasideda simboliu ``#`` ir
    bent vienu tarpu. Pastraipos bloke yra atskiriamos eilutėmis su 
    simboliu ``#``;
+   `ID:12` įterptiniai – paaiškina toje pačioje eilutė esantį sakinį.
    Pradedami simboliu ``#`` ir tarpu.

+   `ID:13` Įterptiniai komentarai turi būti išlygiuoti ties 41-uoju
    simboliu. Jei netelpa, jie keliami į kitą eilutę arba laužiami.
    Pavyzdžiui:

    .. code-block:: python
        
        
        x = x + 1                               # Compensate the border.
        very_long_function_name(argument=some_argument)
                                                # This function name is so
                                                # long that comment have
                                                # to start on the other 
                                                # line.

+   `ID:14` Komentarai rašomi pilnais sakiniais – pradedami didžiąją raide
    (nebent pirmas žodis yra reikšminis) ir baigiami tašku.

Pavadinimai
-----------

+   `ID:17` Klasių vardai turi būti ``CamelCase``.
+   `ID:18` Išimčių vardai turėtų būti ``CamelCase`` su galūne ``Error``.
    Pavyzdžiui:

    .. code-block:: python
        
        raise BlogasVardoFormatasError(vardas)

+   `ID:21` funkcijų, metodų, kintamųjų ir funkcijų argumentų vardai turi
    būti ``lower_case_with_underscores``.
+   `ID:22` konstantos turėtų būti ``UPPER_CASE_WITH_UNDERSCORES``.
+   Vienaskaita rašomi:

    +   `ID:26` klasių vardai;
    +   `ID:25` paprastų objektų (ne konteinerių) vardai.

+   Konteinerių objektų vardai rašomi arba daugiskaita arba vienaskaita
    su galūne nurodančia objekto tipą:

    .. code-block:: python

        books = [book1, book2, book3]
        book_set = set(books)

Lietuviško kodo reikalavimai
============================

+   `ID:19` Toje pačioje klasėje neturėtų būti maišomi lietuviški vardai
    su angliškais.
+   `ID:20` Jei yra galimybė (Python 3.*), tai vardai turi būti rašomi
    su lietuviškais rašmenimis.
+   `ID:24` Vardai rašomi vardininko linksnyje.
+   `ID:23` „getter“ metodas turėtų vadintis ``get_`` + atributo, kurio
    reikšmę jis turi grąžinti pavadinimas vardininko linksnyje. Pavyzdžiui:

    .. code-block:: python

        class Autorius(object):

            get_vardas(self):
                return self._vardas

+   `ID:29` „setter“ metodas turėtų vadintis ``set_`` + atributo, kurio
    reikšmę jis keičia pavadinimas vardininko linksnyje.

Internacionalizuoto kodo reikalavimai
=====================================

Priedas: Pavadinimų rašymo būdai
================================

Galima išskirti tokius pavadinimų rašymo būdus (naudojama angliška 
terminija):

+   ``b`` – viena mažoji raidė;
+   ``B`` – viena didžioji raidė;
+   ``lowercase``;
+   ``lower_case_with_underscores``;
+   ``UPPERCASE``;
+   ``UPPER_CASE_WITH_UNDERSCORES``;
+   ``CamelCase`` / ``CapitalizeWords`` / ``CapWords`` – visi žodžiai
    iš didžiosios raidės, trumpiniai rašomi didžiosiomis raidėmis 
    (``HTTPServerError``);
+   ``mixedCase`` – nuo ``CamelCase`` skiriasi tuo, kad pirmoji raidė – 
    mažoji;
+   ``Capitalized_Words_With_Underscores``.
