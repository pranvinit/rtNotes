### WordPress CRON API

#### Limitations of WordPress Cron

- WordPress Cron is not a real cron job. It is a pseudo-cron job that depends on user visits to trigger scheduled tasks.
- WordPress Cron is not reliable for low-traffic websites because it depends on user visits.

**Note**: To ensure that CRON jobs are executed on time on low-traffic websites, you can use:
1. Third party services like EasyCron or Cronless.
2. Server-side CRON jobs.
3. Plugins like WP-Crontrol or Advanced Cron Manager.

#### Commonly used functions

1. `wp_schedule_event()`: Schedules a recurring event. Takes:
    - `$timestamp`: The time the event should first run (time()).
    - `$recurrence`: The frequency of the event (hourly, daily, etc.).
    - `$hook`: The action to execute.

2. `wp_schedule_single_event()`: Schedules a single event. Takes:
    - `$timestamp`: The time the event should run (time()).
    - `$hook`: The action to execute.

3. `wp_next_scheduled()`: Checks if an event is scheduled. Takes:
    - `$hook`: The action to check.

4. `wp_clear_scheduled_hook()`: Clears all scheduled events for the given hook. Takes:
    - `$hook`: The action to clear.

**Note**: The corn jobs are stored in the `wp_options` table with the option name `cron`.