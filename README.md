# Livewire-wire-navigate-issues-with-flowbite-and-other-libraries
Fix dropdown menus in livewire 3 after wire:navigate


Ok great, I was equally faced with similar challenge but then I keep asking myself how can i drop Livewire just because of this little issues? and how can I not use wire:navigate because of this same issues till i was able to figure out a way.

According to the docs: 
[https://livewire.laravel.com/docs/navigate#dont-rely-on-domcontentloaded](https://livewire.laravel.com/docs/navigate#dont-rely-on-domcontentloaded)

this event listener was suggested

```php
    document.addEventListener('livewire:navigated', () => { 
        // any code you place here will be fired after livewire has successfully swapped the initial page with the on you navigated to
    })
```
## Solution 1


Great, so in my case i was Using Flowbite so i had to copy a function from their Docs page and that was all.


```php
    document.addEventListener('livewire:navigated', () => { 
         // console.log('navigated to a new page');
          initFlowbite();
      })
```


## Solution 2 

Another solution that works for most frames works like Bootstrap and others is to add *data-navigate-track* or *data-navigate-once* to all your scripts like so:

      ```htm
      <script data-navigate-once src="https://cdn.jsdelivr.net/npm/flowbite@2.5.2/dist/flowbite.min.js"></script>
      ```

      ```htm
      <script data-navigate-track src="{{ url('/') }}/buttons.github.io/buttons.js"></script>
      ```
