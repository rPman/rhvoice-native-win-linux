Данный репозиторий содержит инфорамцию по сборке библиотеки jni голосового движка RHVoice на основе его исходных текстов android.

чтобы собрать нужно:
установленный python и scons (в 99% случаев оно уже стоит)
для windows: как минимум нужна visual studio (возможно заработает с mingw)

клонируем https://github.com/Olga-Yakovleva/RHVoice
в каталоге гита RHVoice src нужно создать символическую ссылку:
cd RHVoice/src
ln -s java/android/services/jni jni

клонируем этот гит https://github.com/rPman/rhvoice-native-win-linux
там файлы, которые необходимо положить поверх склонированного репозитария из каталогов windows и linux соответственно с заменой

для linux: необходимо поправить путь до java в файле rhvoice-native-win-linux/linux/src/jni/SConscript
local_env["CPPPATH"].append("/usr/lib/jvm/jdk1.8.0_60/include")
local_env["CPPPATH"].append("/usr/lib/jvm/jdk1.8.0_60/include/linux")

переходим в каталог RHVoice и запускаем scons

результат будет в каталоге
для linux: RHVoice/build/linux/jni/ файл libjni.so
для windows: RHVoice/build\windows\x64\jni\jni.dll и RHVoice/build\windows\x86\jni\jni.dll (scons автоматически собирает для обоих архитектур)
