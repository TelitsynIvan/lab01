## Homework in laboratory work I

Данная лабораторная работа посвещена изучению утилит для разработки проектов

## Tasks

- [x] 1. Ознакомиться со ссылками учебного материала
- [x] 2. Выполнить инструкцию учебного материала
- [x] 3. Скачайте библиотеку *boost* с помощью утилиты **wget**. Адрес для скачивания `https://sourcefor$
- [x] 4. Разархивируйте скаченный файл в директорию `~/boost_1_69_0`
- [x] 5. Подсчитайте количество файлов в директории `~/boost_1_69_0` **не включая** вложенные директории.
- [x] 6. Подсчитайте количество файлов в директории `~/boost_1_69_0` **включая** вложенные директории.
- [x] 7. Подсчитайте количество заголовочных файлов, файлов с расширением `.cpp`, сколько остальных файл$
- [x] 8. Найдите полный пусть до файла `any.hpp` внутри библиотеки *boost*.
- [x] 9. Выведите в консоль все файлы, где упоминается последовательность `boost::asio`.
- [x] 10. Скомпилирутйе *boost*. Можно воспользоваться [инструкцией](https://www.boost.org/doc/libs/1_61$
- [x] 11. Перенесите все скомпилированные на предыдущем шаге статические библиотеки в директорию `~/boos$
- [x] 12. Подсчитайте сколько занимает дискового пространства каждый файл в этой директории.
- [x] 13. Найдите *топ10* самых "тяжёлых".

## Report and tutorial
```bash
```
1)Скачаем библиотеку boost с помощью утилиты wget. Адрес для скачивания https://sourceforge.net/projects/boost/files/boost/1.69.0/boost1690.tar.gz.
```sh
$ wget https://sourceforge.net/projects/boost/files/boost/1.69.0/boost_1_69_0.tar.gz
```
Распознаётся excellmedia.dl.sourceforge.net (excellmedia.dl.sourceforge.net)… 202.153.32.19<br>
Подключение к excellmedia.dl.sourceforge.net (excellmedia.dl.sourceforge.net)|202.153.32.19|:443... соед<br>
HTTP-запрос отправлен. Ожидание ответа… 200 OK<br>
Длина: 111710205 (107M) [application/x-gzip]<br>
Сохранение в: «boost_1_69_0.tar.gz»

2) Разархивируем скаченный файл в директорию ~/boost_1_69_0.
```sh
$ tar -xvf boost_1_69_0.tar.gz
```

3) Подсчитаем количество файлов в директории ~/boost_1_69_0, не включая вложенные.
```sh
$ find . -maxdepth 1 -type f | wc -l
```
12

4) Подсчитаем количество файлов в директории ~/boost_1_69_0, включая вложенные.
```sh
$ find . -type f|wc -l
```
61 193

5) Подсчитаем количество заголовочных файлов, файлов с расширением .cpp и
количество остальных файлов
```sh
$ find . -name “*.hpp” -o -name “*.h” | wc -l
```
15 208
```sh
$ find . -name “*.cpp” | wc -l
```
13 774
```sh
$ find . -and -type -f -and -not -name “*.cpp” -and -not -name “*.h” -and -not - name “*.hpp” | wc -l
```
32 211

6) Найдем пути до различных файлов **any.hpp** внутри библиотеки
```sh
$ find . -name “any.hpp”
```
./boost/fusion/include/any.hpp<br>
./boost/fusion/algorithm/query/any.hpp<br>
./boost/fusion/algorithm/query/detail/any.hpp<br>
./boost/spirit/home/support/algorithm/any.hpp<br>
./boost/proto/detail/any.hpp<br>
./boost/type_erasure/any.hpp<br>
./boost/hana/fwd/any.hpp<br>
./boost/hana/any.hpp<br>
./boost/any.hpp<br>
./boost/xpressive/detail/utility/any.hpp<br>

7) Выведем в консоль все файлы, где упоминается последовательность **boost::asio**.
```sh
$ grep -Ril “boost::asio” .
```
./boost/beast/experimental/core/impl/timeout_socket.hpp<br>
./boost/beast/experimental/core/impl/flat_stream.ipp<br>
./boost/beast/experimental/core/impl/timeout_service.ipp<br>
./boost/beast/experimental/core/flat_stream.hpp<br>
./boost/beast/experimental/core/ssl_stream.hpp<br>
./boost/beast/experimental/core/timeout_service.hpp<br>
./boost/beast/experimental/core/timeout_socket.hpp<br>

8) Скомпилируем boost.
```sh
./bootstrap.sh –prefix=boost_output
./b2 install
```

9) Перенесем все скомпилированные на предыдущем шаге статические библиотеки в директорию ~/boost-libs
```sh
mv boost_1_69_0/=boost_output/lib/ boost-libs/
```

10) Подсчитаем сколько занимает дискового пространства каждый файл в этой директории
```sh
$ find . type -f -exec du -h {} +;
```

100K ./libboost_stacktrace_basic.a<br>
2,4M ./libboost_wave.dylib<br>
7,8M ./libboost_math_tr1.a<br>
5,4M ./libboost_python27.a 164K ./libboost_thread.dylib 100K ./libboost_math_c99f.dylib<br>
480K ./libboost_$<br>
1,9M ./libboost_math_c99f.a<br>
1,8M ./libboost_math_c99l.a<br>
1,3M ./libboost_iostreams.a<br>
1,1M ./libboost_thread.a<br>
7,3M ./libboost_program_options.a <br>
188K ./libboost_iostreams.dylib<br>
300K ./libboost_coroutine.a<br>
276K ./libboost_timer.a <br>
412K ./libboost_wserialization.dylib 940K ./libboost_contract.a <br>
172K ./libboost_contract.dylib 892K ./libboost_numpy27.a <br>
740K ./libboost_type_erasure.a<br>
21M ./libboost_log_setup.a<br>
16K ./libboost_atomic.a<br>
208K ./libboost_random.a<br>
104K ./libboost_prg_exec_monitor.dylib 528K ./libboost_date_time.a<br>
648K ./libboost_graph.dylib<br>
828K ./libboost_locale.dylib<br>

11) Найдем топ-10 самых тяжелых
```sh
$ find . type -f -exec du -h {} +|sort -rh | head -n 10
```

28M ./libboost_wave.a<br>
21M ./libboost_log_setup.a<br>
20M ./libboost_log.a<br>
16M ./libboost_test_exec_monitor.a<br>
15M ./libboost_unit_test_framework.a<br>
9,1M ./libboost_locale.a<br>
8,9M ./libboost_regex.a<br>
8,1M ./libboost_math_tr1f.a<br>
7,8M ./libboost_math_tr1.a<br>
7,7M ./libboost_math_tr1l.a<br>
