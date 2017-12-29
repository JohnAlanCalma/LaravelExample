# LaravelExample
## Setup
- download/clone the git repository from
  - `git clone https://github.com/paslandau/laravelexample.git`
- navigate into the project folder
  - `cd laravelexample`
- make sure not to work directly on the master branch  
  - `git checkout -b my_local_branch`
- to prepare the vagrant configuration, run
  - `vendor/bin/homestead make` or `vendor/bin/homestead.bat make` on Windows
- adjust the `hosts` file and the newly created `Homestead.yaml` in the root of the repo according to your needs. Usually that includes:
  - adjust `ip`
    - make sure the `ip` is not already used in your local network
  - add an entry to your host file
    - `[IP] laravelexample.app` (e.g. `192.168.33.111 laravelexample.app`)
    - location on Unix: `/etc/hosts`
    - location on Windows: `C:\Windows\System32\drivers\etc`
- adjust `folders` and `sites` mapping (optional; it should be set up correctly by default if you followed the steps above).
  Watch out for the following:
  - the `folders: - map: "[PATH]"` should point to the absolute path to the `cube` repository on your **local** machine
  - the `folders: to: "[PATH]"` denotes the path on your **vagrant** machine that is mapped to the above mentioned path on your local machine,
    so that you can access your local files within the vagrant box.
  - the `sites: - map: "[HOSTNAME]"` denotes the hostname that the nginx is looking for to serve content on
    - you _should_ adjust that to the hostname chosen for your hostfile (e.g. `laravelexample.app`) although it not necessary since nginx will even respond to another hostname
  - the `sites: - to: "[PATH]"` denotes the absolute path withing the vagrant box that the above mentioned hostname uses as `root` path for content.
    This should be the path to the `public` folder of this repository
- start the vagrant box with `vagrant up`, ssh into it with `vagrant ssh`, switch to the project folder (by default, this should be `cd /home/vagrant/laravelexample/`) and install the 
  project's dependencies
  - `composer install`
- setup laravel by generating an application key and setting up the .env file:
  - php artisan key:generate
  - `cp .env.example .env`
- generate the meta data files for better code completion
  - `php artisan ide-helper:meta`
  - `php artisan ide-helper:generate`
  - `php artisan ide-helper:model`

You should now be able to open http://laravelexample.app/ in your browser and see the Laravel welcome page :)




<p align="center"><img src="https://laravel.com/assets/img/components/logo-laravel.svg"></p>

<p align="center">
<a href="https://travis-ci.org/laravel/framework"><img src="https://travis-ci.org/laravel/framework.svg" alt="Build Status"></a>
<a href="https://packagist.org/packages/laravel/framework"><img src="https://poser.pugx.org/laravel/framework/d/total.svg" alt="Total Downloads"></a>
<a href="https://packagist.org/packages/laravel/framework"><img src="https://poser.pugx.org/laravel/framework/v/stable.svg" alt="Latest Stable Version"></a>
<a href="https://packagist.org/packages/laravel/framework"><img src="https://poser.pugx.org/laravel/framework/license.svg" alt="License"></a>
</p>

## About Laravel

Laravel is a web application framework with expressive, elegant syntax. We believe development must be an enjoyable and creative experience to be truly fulfilling. Laravel attempts to take the pain out of development by easing common tasks used in the majority of web projects, such as:

- [Simple, fast routing engine](https://laravel.com/docs/routing).
- [Powerful dependency injection container](https://laravel.com/docs/container).
- Multiple back-ends for [session](https://laravel.com/docs/session) and [cache](https://laravel.com/docs/cache) storage.
- Expressive, intuitive [database ORM](https://laravel.com/docs/eloquent).
- Database agnostic [schema migrations](https://laravel.com/docs/migrations).
- [Robust background job processing](https://laravel.com/docs/queues).
- [Real-time event broadcasting](https://laravel.com/docs/broadcasting).

Laravel is accessible, yet powerful, providing tools needed for large, robust applications.

## Learning Laravel

Laravel has the most extensive and thorough [documentation](https://laravel.com/docs) and video tutorial library of any modern web application framework, making it a breeze to get started learning the framework.

If you're not in the mood to read, [Laracasts](https://laracasts.com) contains over 1100 video tutorials on a range of topics including Laravel, modern PHP, unit testing, JavaScript, and more. Boost the skill level of yourself and your entire team by digging into our comprehensive video library.

## Laravel Sponsors

We would like to extend our thanks to the following sponsors for helping fund on-going Laravel development. If you are interested in becoming a sponsor, please visit the Laravel [Patreon page](http://patreon.com/taylorotwell):

- **[Vehikl](https://vehikl.com/)**
- **[Tighten Co.](https://tighten.co)**
- **[British Software Development](https://www.britishsoftware.co)**
- [Fragrantica](https://www.fragrantica.com)
- [SOFTonSOFA](https://softonsofa.com/)
- [User10](https://user10.com)
- [Soumettre.fr](https://soumettre.fr/)
- [CodeBrisk](https://codebrisk.com)
- [1Forge](https://1forge.com)
- [TECPRESSO](https://tecpresso.co.jp/)
- [Pulse Storm](http://www.pulsestorm.net/)
- [Runtime Converter](http://runtimeconverter.com/)
- [WebL'Agence](https://weblagence.com/)

## Contributing

Thank you for considering contributing to the Laravel framework! The contribution guide can be found in the [Laravel documentation](http://laravel.com/docs/contributions).

## Security Vulnerabilities

If you discover a security vulnerability within Laravel, please send an e-mail to Taylor Otwell via [taylor@laravel.com](mailto:taylor@laravel.com). All security vulnerabilities will be promptly addressed.

## License

The Laravel framework is open-sourced software licensed under the [MIT license](http://opensource.org/licenses/MIT).
