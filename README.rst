==================
corona_chan_gob_mx
==================


.. image:: https://img.shields.io/pypi/v/corona_chan_gob_mx.svg
        :target: https://pypi.python.org/pypi/corona_chan_gob_mx

.. image:: https://img.shields.io/travis/dem4ply/corona_chan_gob_mx.svg
        :target: https://travis-ci.org/dem4ply/corona_chan_gob_mx

.. image:: https://readthedocs.org/projects/corona-chan-gob-mx/badge/?version=latest
        :target: https://corona-chan-gob-mx.readthedocs.io/en/latest/?badge=latest
        :alt: Documentation Status


corona chan scraper for gob mx


* Free software: WTFPL
* Documentation: https://corona-chan-gob-mx.readthedocs.io.


Features
--------

* le los pdf publicados en `casos de covid-19 en mexico <https://www.gob.mx/
  salud/documentos/coronavirus-covid-19-comunicado-tecnico-diario-238449>`_
* transforma las tablas de los pdf en listas de dicionarios para poder 
  ser procesadas en python de manera mas facil


==========
How to use
==========

el uso basico seria con

.. code-block:: python

	import corona_chan_gob_mx import get_today_cases()
	table = get_today_cases()
	for row in table:
		assert isinstance( row, dict )

se puede adquirir la lista de pdfs con

.. code-block:: python

	import corona_chan_gob_mx.scraper import list_of_pdfs
	links = list_of_pdfs.get()
	print( links.native )
	# [
	#	'https://www.gob.mx/cms/uploads/attachment/file/544087/'
	#	'Tabla_casos_sospechosos_COVID-19_2020.03.29.pdf',
	#	'https://www.gob.mx/cms/uploads/attachment/file/544086/'
	#	'Tabla_casos_positivos_COVID-19_resultado_InDRE_2020.03.29.pdf' ]
	for link in links.native:
		table = link.get()
		for row in table.native:
			assert isinstance( row, dict )

para leer pdf sin descargarlos

.. code-block:: python

	import corona_chan_gob_mx.scraper import pdf_to_dicts
	tabla = pdf_to_dict( "/path/to/pdf/tabla.pdf" )
	for row in table:
		assert isinstance( row, dict )
