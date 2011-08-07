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
+   `ID:39` Vieno kodo failo ilgis negali būti ilgesnis nei 1000 eilučių.
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

Django
------

Pastabos, skirtos sistemoms, rašomoms naudojant
`Django karkasą <https://www.djangoproject.com/>`_.

+   `ID:30` Modelių laukai privalo turėti komentarus. (Kurie gali būti 
    tušti.) Komentarai rašomi po lauku. Pavyzdžiui:

    .. code-block:: python

        class Poll(models.Model):
            """ Class comment.
            """

            question = models.CharField(max_length=200)
            """ Attribute comment.
            """
            
            pub_date = models.DateTimeField('date published')
            """
            """

Kitos rekomendacijos
--------------------

+   `ID:32` Turėtų būti vengiama naudoti Java stiliaus „getter“ ir „setter“
    metodus. Pavyzdžiui, vietoj:

    .. code-block:: python

        class A(object):
            """ Example class.
            """
            
            def __init__(self):
                self._a = u'foo'
            
            def get_a(self):
                """ Returns a.
                """
                return self._a
            
            def set_a(self, a):
                """ Returns a.
                """
                self._a = a

    turėtų būti tiesiog viešas atributas ``a`` (kadangi nei „getter“, nei
    „setter“ neatlieka jokių papildomų veiksmų):

    .. code-block:: python

        class A(object):
            """ Example class.
            """
            
            def __init__(self):
                self.a = u'foo'

    Jei reikia pasiekti, kad atributo reikšmę galima būtų tik skaityti 
    (negalima būtų keisti), tai tą galima pasiekti naudojanti ``property``
    dekoratorių:

    .. code-block:: python

        class A(object):
            """ Example class.
            """
            
            def __init__(self):
                self._a = u'foo'
                
            @property
            def a(self):
                """ Read only attribute.
                """
                return self._a 

    >>> a = A()
    >>> print a.a
    foo
    >>> a.a = u'bar'
    Traceback (most recent call last):
    ...
    AttributeError: can't set attribute

    Jei reikia prieš keičiant atributo reikšmę atlikti kažkokius veiksmus,
    pavyzdžiui, konvertavimą, tai taip pat galima pasiekti pasinaudojant
    ``property``:

    .. code-block:: python

        import datetime


        class B(object):
            """ Example class.
            """
            
            def __init__(self):
                self._date = datetime.date.today()
                
            def _get_date_string(self):
                """ Returns date as string.
                """
                return self._date.strftime("%Y-%m-%d")
            
            def _set_date_string(self, date_string):
                """ Sets date from string.
                """
                self._date = datetime.datetime.strptime(
                    date_string, "%Y-%m-%d").date()
                
            date = property(
                fget=_get_date_string,
                fset=_set_date_string,
                doc="Date as string.")

    >>> b = B()
    >>> print b.date
    2011-08-07
    >>> b.date = "2012-01-01"
    >>> print b.date
    2012-01-01
    >>> b._date
    datetime.date(2012, 1, 1)

+   `ID:33` Simbolių eilučių sujungimui turėtų būti naudojamas ``join``
    metodas vietoj sudėties operatoriaus:

    >>> # Blogai:
    ... rez = ""
    ... for i in range(10):
    ...     if i % 2:
    ...         rez += str(i)
    ... print rez
    13579
    >>> # Gerai:
    ... rez_list = []
    ... for i in range(10):
    ...     if i % 2:
    ...         rez_list.append(str(i))
    ... print ''.join(rez_list)
    13579
    >>> # Dar geriau:
    ... print ''.join(str(i) for i in xrange(10) if i % 2)
    13579

+   `ID:34` Jei tarpiniai rezultatai nėra reikalingi, tai vietoj sąrašų
    generavimo turėtų būti naudojami generatoriai. Pavyzdžiui, vietoj:

    >>> print str(sum([3**i for i in range(10000)]))[100:120]
    83662602261161789771

    turėtų būti:

    >>> print str(sum(3**i for i in xrange(10000)))[100:120]
    83662602261161789771

+   `ID:35` Patikrinimui ar elementas priklauso konteineriui, turėtų būti 
    naudojamas operatorius ``in``:

    >>> print 1 in [1, 2, 3, 4]
    True
    >>> print 'a' in {'a': 1, 'b': 2}
    True
    >>> print 1 in {'a': 1, 'b': 2}
    False
    >>> print {'a': 1, 'b': 2}.has_key('b')
    ...                                 # Turėtų būti vengiama.
    True

+   `ID:36` Jei reikia tam tikro tipo objekto, tai gautasis objektas turėtų 
    būti konvertuojamas į norimą tipą, o ne tikrinama ar jis yra to tipo
    (žr. `neišreikštinis tipizavimas
    <http://žosmė.lt/python/glossary.html#term-neisreikstinis-tipizavimas>`_).
    Pavyzdžiui, vietoj:

    .. code-block:: python

        if isinstance(a, unicode):
            do_stuff(a)
        else:
            raise ...

    turėtų būti:

    .. code-block:: python

        do_stuff(unicode(a))

+   `ID:37` `Lengviau paprašyti gailestingumo nei leidimo.
    <http://žosmė.lt/python/glossary.html#term-eafp>`_ Pavyzdžiui, vietoj:

    .. code-block:: python

        if len(args) > 0:
            print args[0]
        else:
            print u'No arguments.'

    turėtų būti:

    .. code-block:: python

        try:
            print args[0]
        except IndexError:
            print 'No arguments'
            
    Taip pat verta atkreipti dėmesį, kad kartais egzistuoja funkcijos,
    kurios apskritai pašalina poreikį rankiniu būdu tikrinti:

    >>> a = {}
    ... for i in a.get(u'foo', []):
    ...     print i
    >>> for i in range(10):
    ...     a.setdefault(i % 3, []).append(i)
    >>> print a
    {0: [0, 3, 6, 9], 1: [1, 4, 7], 2: [2, 5, 8]}

+   `ID:38` Išimčių gaudymo rėžiai turėtų būti kuo siauresni (tai yra 
    niekada neturėtų būti naudojamas tuščias ``except`` sakinys).
    Pavyzdžiui:

    .. code-block:: python

        try:
            import foo
        except:
            foo = None
    
    neturėtų būti naudojamas, nes bus pagaunamos ir tokios išimtys, kaip
    ``KeyInterrupt`` (naudotojas nurodė programai išsijungti).

Reikalavimai lietuviškam kodui
==============================

+   `ID:19` Toje pačioje klasėje neturėtų būti maišomi lietuviški vardai
    su angliškais.
+   `ID:20` Jei yra galimybė (Python 3.*), tai vardai turi būti rašomi
    su lietuviškais rašmenimis.
+   `ID:24` Vardai rašomi vardininko linksnyje.

Reikalavimai internacionalizuotam kodui
=======================================

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
