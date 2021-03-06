# RelateIQ Client - Beta

[![Latest Stable Version](https://poser.pugx.org/torann/relateiq/v/stable.png)](https://packagist.org/packages/torann/relateiq) [![Total Downloads](https://poser.pugx.org/torann/relateiq/downloads.png)](https://packagist.org/packages/torann/relateiq)

----------

## Installation

- [RelateIQ Client on Packagist](https://packagist.org/packages/torann/relateiq)
- [RelateIQ Client on GitHub](https://github.com/torann/relateiq)

To get the latest version of RelateIQ Client simply require it in your `composer.json` file.

~~~
"torann/relateiq": "dev-master"
~~~

You'll then need to run `composer install` to download it and have the autoloader updated.


## Laravel Setup

Once RelateIQ Client is installed you need to register the service provider with the application. Open up `app/config/app.php` and find the `providers` key.


```php
'Torann\RelateIQ\ServiceProvider'
```

> There is no need to add the Facade, the package will add it for you.


### Add RelateIQ to the Services Config 

Open up `app/config/services.php` and add `relateiq`.


```php
'relateiq' => array(
	'key'    => '66cfba7f741d645a488c0b21ebFAKE',
	'secret' => 'effd5216acac6314219ALSOFAKE',
),
```

## RelateIQ Client Instance


```php
$riq = new RelateIQ('66cfba7f741d645a488c0b21ebFAKE', 'effd5216acac6314219ALSOFAKE');
$contact = $riq->getContact('741d645a488c0b21eb');
```

For Laravel simple use the facade `RelateIQ`. 

```php
$contact = new RelateIQ::getContact('741d645a488c0b21eb');
```

## Methods

### Create a Contact `newContact(:properties)`
A POST request which creates a new Contact object and returns the created Contact with its new unique ID.

**Parameters:**

- `:properties` Attributes that are comprised of a contact object in RelateIQ. The following attributes are supported through the API:
  - name
  - email **(Required)**
  - phone
  - address
  - company
  - title
  - twitter

**Example**

```php
$contact = RelateIQ::newContact(array(
    'name'    => 'John Doe',
    'email'   => 'john.doe@mail.box',
    'phone'   => '555-4454',
    'address' => '22 Hill Ave',
    'company' => 'Box Maker, Inc.',
    'title'   => 'Lead Taper',
    'twitter' => '@John4Boxes'
));
```

### Get a Single Contact `getContact(:id)`
A GET request which pulls a specific Contact by ID, Email or Phone Number

**Parameters:**

- `:id` The identifier for the Contact to be fetched.

**Example**

```php
$contact = new RelateIQ::getContact('741d645a488c0b21eb');
```


### Get All Contacts `getContacts()`
A GET request which fetches a paginated collection of all Contacts in your Organization.

**Example**

```php
$contacts = new RelateIQ::getContacts();
```

### Update a Contact
A PUT request which updates the details of a specific Contact.

**Example**

```php
$contact = new RelateIQ::getContact('741d645a488c0b21eb');
$contact->name = 'Sally Doe';
$contact->save();
```

## Change Log

#### v0.1.0

- First release
