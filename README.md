Laravel Kendo UI DataSource
===========================

ESSENTIALLY ALL WORK ON THIS PROJECT WAS ORIGINALLY DONE BY USER meowcakes.  I HAVE FORKED THIS FROM websolutionmw MERELY TO GIVE MYSELF CONTROL OVER THE DEPENDENCY VERSIONS.  I TAKE NO CREDIT OR RESPONSIBILITY FOR THE ORIGINAL SCRIPTS, OTHER THAN THE TRIVIAL ADJUSTMENTS I HAVE MADE.

Server side Kendo UI DataSource implementation for Laravel

### Installation

- [Laravel Kendo UI DataSource on Packagist](https://packagist.org/packages/chemprof/laravel-kendo-ui-datasource)
- [Laravel Kendo UI DataSource on GitHub](https://github.com/chemprof/laravel-kendo-ui-datasource)

To get the latest version simply require it in your `composer.json` file.

~~~
"ChemProf/laravel-kendo-ui-datasource": "master"
~~~

You can register the facade in the `aliases` key of your `app/config/app.php` file.

~~~
'aliases' => array(

    'KendoDataSource' => 'ChemProf\LaravelKendoUiDatasource\Facade'

)
~~~

### Example

```php
$kd = KendoDataSource::make(
	Input::all(),
	[
		'address' => 'string',
		'suburb' => 'string',
		'phone' => 'string',
		'created_at' => 'date',
		'fully_registered' => 'boolean',
	]
);

$query = User::newQuery();
$count = $kd->execute($query);
return Response::json(['data' => $query->get()->toArray(), 'total' => $count]);
```
