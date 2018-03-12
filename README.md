# cradle-csrf
CSRF helpers

## Install

```
composer require cradlephp/cradle-csrf
```

Then in `/bootstrap.php`, add

```
->register('cradlephp/cradle-csrf')
```

## Usage

In any of your routes add the following code.

```
cradle()->trigger('csrf-load', $request, $response);
```

The CSRF token will be found in `$request->getStage('csrf')`. In your form
template, be sure to add this key in a hidden field like the following.

```
<input name="csrf" value="{{csrf}}" />
```

When validating this form in a route you can use the following

```
cradle()->trigger('csrf-validate', $request, $response);
```

If there is an error, it will be found in the response error object message.
You can check this using the following.

```
if($response->isError()) {
    $message = $response->getMessage();
    //report the error
}
```
