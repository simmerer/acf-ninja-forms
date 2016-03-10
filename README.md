# ACF Ninja Forms Field

This is an Advanced Custom Field custom field to select one or many [Ninja Forms](http://www.ninjaforms.com/).

## Compatibility

* ACF version 4 and up. Prior versions had an incompatibility with ACF v4, which has been fixed here.

## Installation

This add-on can be treated as both a WP plugin or a theme include.

*Plugin*
1. Copy the 'acf-ninja-forms' folder into your plugins folder
2. Activate the Advanced Custom Fields: Ninja Forms Field plugin through the 'Plugins' menu in WordPress

*Include*
1. Copy the 'acf-ninja-forms' folder into your theme folder (can use sub folders). You can place the folder anywhere inside the 'wp-content' directory
2. Edit your functions.php file and add the code below (Make sure the path is correct to include the acf-ninja-forms.php file)

```
function my_register_fields() {
    include_once('acf-ninja-forms.php');
}
add_action('acf/register_fields', 'my_register_fields');
```

## Using the field

The field lets you pick one or many fields.

The data returned is either a Form object or an array of Form objects.

If you have selected a single form and you want to display the form on the page, you can use:

```
<?php
    $form = get_field('your_form_field');
    if ( function_exists( 'ninja_forms_display_form' ) ) {
        ninja_forms_display_form( $form[ 'id' ] );
    }
?>
```

You can find out more about the Ninja Forms methods to embed a form on a page in their [documentation](http://docs.ninjaforms.com/)

If you are using the field to select multiple forms, you will have to iterate over the array.  You can then use the form object as you like:

```
<?php
    $forms = get_field('your_forms');
    foreach( $forms as $form ){
        echo $form[ 'id' ];
    }
?>
```

## About

Plugin modified by [David Simmer](http://simmerdesigns.com) to fill a need for a functional ACF 4.x-compatible add-on.

## Credits

Thanks to to [Chuck Mac](https://chuckmacdev.com/) for coming up with this Ninja Forms + ACF plugin, [Boston Dell-Vandenberg](http://www.pomelodesign.com) for a few additions, and Adam Pope for the [ACF Gravity Forms](https://github.com/stormuk/Gravity-Forms-ACF-Field) and Lewis Mcarey for the [Users Field ACF](https://github.com/lewismcarey/User-Field-ACF-Add-on) add-ons upon which this is all based.
