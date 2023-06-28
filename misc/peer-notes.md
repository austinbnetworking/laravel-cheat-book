# Laravel Notes from Pairing

Things to learn/do: (In order of priority)  
1. VueJS - Javascript framework. 
   1. Ziggy - VueJs additional functionality.
2. Tailwind CSS - CSS framework.
3. Laravel Valet - Environment. 
4. Yarn for NPM - Package management. 
5. Vite - Package management
6. Mailhog - Local mail service.
7. Nova - Laravel admin dashboard.
9. Update [database/forms-authentication.md](database/forms-authentication.md)
10. Update [blade/yield-sections.md](blade/yield-sections.md)
11. Update [blade/blade.md](blade/blade.md)
12. Update [routing/routing.md](routing/routing.md)
13. Watch [What's new in Laravel 9](https://laracasts.com/series/whats-new-in-laravel-9)
14. Watch [What's new in Laravel 10](https://laracasts.com/series/whats-new-in-laravel-10)
15. [Vue Use](https://vueuse.org/core/useStepper/#usestepper)
16. [Precognition](https://laravel.com/docs/10.x/precognition#using-vue-and-inertia)

Good things to know:  
1.  Hero Icons is a good icon source.  

Access Systems Support local setup with valet:  
1. Clone repository
2. Install dependencies - `composer install` && `npm install`
3. Create database
4. Setup ENV and add DB info - `cp .env.example .env`
5. Generate keys - `php artisan key:generate`
6. Run initial migrations - `php artisan migrate`
7. Start the development server - `npm run dev`