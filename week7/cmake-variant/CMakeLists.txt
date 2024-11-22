cmake_minimum_required(VERSION 3.21)
project(FibonacciPlot)



include_directories(include)

# Пути к заголовочным файлам
include_directories(${CMAKE_SOURCE_DIR}/../libs/gnuplot/gnuplot-iostream)

# Указываем путь к Boost
set(BOOST_ROOT "/usr")
set(BOOST_LIBRARYDIR "/usr/lib")

# Находим Boost
find_package(Boost REQUIRED COMPONENTS iostreams)

# Подключаем заголовочные файлы Boost
include_directories(${Boost_INCLUDE_DIRS})

# Добавляем исходные файлы
set(SOURCE_FILES
    src/main/main.cpp
    src/main/fibonacci.cpp
)

# Создаем исполнимый файл
add_executable(FibonacciPlot ${SOURCE_FILES})

# Линкуем с Boost
target_link_libraries(FibonacciPlot Boost::iostreams)
