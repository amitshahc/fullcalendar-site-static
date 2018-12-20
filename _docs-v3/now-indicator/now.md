---
title: now
---

Explicitly sets the "today" date of the calendar. This is the day that is normally highlighted in yellow.

<div class='spec' markdown='1'>
Moment, function
</div>

Normally, the local browser's current date is used.

You can override the current date by providing a Moment-like value, such as an ISO8601 date string like `"2013-12-01T00:00:00"`.

You can also provide a function that returns a Moment-like value.

Overriding the current date is particularly useful when your calendar is using a custom [timezone](timezone) parameter. The current year/month/date in the custom timezone might be different than the local computer's current date.

You'll most likely want to calculate this with a server-side script and inject it into the settings of the calendar. Here is an example in PHP:

```php
<?php
  $datetime = new DateTime('now', 'America/Chicago');
  /*** PHP 7  ***/
  // $datetime = new DateTime('now', new DateTimeZone('America/Chicago'));
  $datetime_string = $datetime->format('c');
?>

$('#calendar').fullCalendar({
  now: <?php echo json_encode($datetime_string) ?>
});
```
