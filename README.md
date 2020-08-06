# php7.4fpm + php-memprof + php-meminfo

## Расширение php-memprof
* https://github.com/arnaud-lb/php-memory-profiler
* `pecl install memprof`
* `memprof_dump_callgrind(fopen($projectDir.'callgrind.dump', 'wb'));`
* `MEMPROF_PROFILE=1 bin/console leak --env=prod`
* `kcachegrind callgrind.dump`

## Расширение php-meminfo
* https://github.com/BitOne/php-meminfo
* `git clone git@github.com:vudaltsov/php-meminfo.git` + `git checkout php74_support`
* устанавливаем по инструкции в `README.md`
* [подробная инструкция по анализу](https://github.com/BitOne/php-meminfo/blob/master/doc/hunting_down_memory_leaks.md)
