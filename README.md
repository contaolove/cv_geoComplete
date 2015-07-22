# Geo auto-completer field
Provides the geo auto-complete widget (http://ubilabs.github.io/geocomplete/) for frontend and backend, which allows you to fill out a text field with geo data from google and autofill predefined address fields.

The widget isn't uploaded yet, because the development structure to use git for all extensions isn't done yet and there are much extensions to publish. If you are interested to use the widget, please send me an e-mail.

# Dependencies
In frontend jQuery has to be enabled.
If you are not using Composer to install this widget, you will also need:
https://github.com/terminal42/contao-NamespaceClassLoader

# Languages
The widget is translated in
 * Englisch
 * German

# Installation and usage
Install it via Composer or just copy all files into system/modules/cv_geofield

DCA-Field example for use
```
'street1' => array
(
	'label'						=> &$GLOBALS['TL_LANG']['tl_table']['street1'],
	'exclude'					=> true,
	'inputType'					=> 'cvGeoComplete',
	'eval'						=> array
	(
		'maxlength'=>255, 'tl_class'=>'long',
		'ownValue'				=> 'route',
		'autofill'				=> array
		(
			'country'						=> '#ctrl_country',
			'administrative_area_level_1'	=> '#ctrl_state',
			'locality'						=> '#ctrl_city',
			'postal_code'					=> '#ctrl_postal',
			'street_number'					=> '#ctrl_street2'
		),
		'street_number_seperator'			=> ' '
	),
	'sql'						=> "varchar(255) NOT NULL default ''"
),
```
DCA-Field with all options
```
'geotestfield' => array
(
	'label'						=> &$GLOBALS['TL_LANG']['tl_cv_config']['geotestfield'],
	'exclude'					=> true,
	'inputType'					=> 'cvGeoComplete',
	'eval'						=> array
	(
		'mandatory'				=>true,

		'map'					=> false, 	// or '.map'
		'location'				=> false, 	// or 'Musterstrasse 123, 1234 Musterstadt, Land' or array(12.12345678, 13.12345678)
		'details'				=> false, 	// or '.details'
		'detailsAttribute'		=> '',	  	// or 'data-geo'
		'ownValue'				=> '',	  	// or 'route' or 'locality' or ..
		'autofill'				=> array
		(
			'route'							=> '#ctrl_street1',
			'intersection'					=> '',
			'political'						=> '',
			'country'						=> '#ctrl_country',
			'administrative_area_level_1'	=> '#ctrl_state',
			'administrative_area_level_2'	=> '',
			'administrative_area_level_3'	=> '',
			'colloquial_area'				=> '',
			'locality'						=> '#ctrl_city',
			'sublocality'					=> '',
			'neighborhood'					=> '',
			'premise'						=> '',
			'subpremise'					=> '',
			'postal_code'					=> '#ctrl_postal',
			'natural_feature'				=> '',
			'airport'						=> '',
			'park'							=> '',
			'point_of_interest'				=> '',
			'post_box'						=> '',
			'street_number'					=> '#ctrl_street1',
			'lat'							=> '',
			'lng'							=> '',
			'viewport'						=> '',
			'location'						=> '',
			'formatted_address'				=> '',
			'location_type'					=> '',
			'bounds'						=> ''
		),
		'street_number_seperator'			=> ' '
	),
	'sql'						=> "varchar(255) NOT NULL default ''"
),
```

Supported parameters for eval array

| Parameter | Default | Description |
| ------------- | ------------- | ------------- | ------------- |
| mandatory  | false | Contao default parameter |
| map  | false | Can be any CSS selector which holds the map |
| location  | false | Either a string which contains the address (Musterstrasse 123, 12345 Musterstadt, Land) or a array with latitude and longitude data (array(12.12345678, 13.12345678) |
| details  | false | Can be any CSS selector which holds the details for address |
| detailsAttribute  | 'name' | The attribute's name to use as an indicator (e.g. data-geo) |
| ownValue  | false | Can be a string with the name of the result parameter (e.g. route or locality). So you must not add an extra field for autofill addresses  |
| autofill  | false | An array with result parameter => CSS selector pairs which should be used to fill out other address data fields |
| street_number_seperator  | '' | The seperator used to add the street number to the street if both are using the same CSS selector |

# Credits
 * The widget uses the Geocomplete plugin from Ubilabs (http://ubilabs.github.io/geocomplete/)
