Laravel's events provide a simple observer pattern implementation, allowing you to subscribe and listen for various events that occur within your application.

Event classes are typically stored in the app/Events directory, while their listeners are stored in app/Listeners. 

Don't worry if you don't see these directories in your application as they will be created for you as you generate events and listeners using Artisan console commands.

Events serve as a great way to decouple various aspects of your application, since a single event can have multiple listeners that do not depend on each other. For example, you may wish to send a Slack notification to your user each time an order has shipped. Instead of coupling your order processing code to your Slack notification code, you can raise an App\Events\OrderShipped event which a listener can receive and use to dispatch a Slack notification.

# Observer pattern

![image](https://user-images.githubusercontent.com/4015406/148737764-006aae07-87cb-4c64-9c93-a49bcdbc48cd.png)


# Conceptes

- Observer Pattern: The observer pattern is a software design pattern in which an object, named the subject, maintains a list of its dependents, called observers, and notifies them automatically of any state changes, usually by calling one of their methods. | https://en.wikipedia.org/wiki/Observer_pattern
- Event classes: **app/Events**
- Listeners:  **app/Listeners**


# Coneixements previs

- Service Providers: App\Providers\EventServiceProvider

# Procediment

1. Registrar els events i els listeners
2. 


# Comandes artisan

- php artisan event:generate
- php artisan event:list
- php artisan make:event
- php artisan make:listener

# RECURSOS

- https://laravel.com/docs/8.x/events
