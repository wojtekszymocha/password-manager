project(PasswordManager)

add_library(sqlite3 STATIC ../lib/sqlite3.c)
find_package(OpenSSL REQUIRED)
include_directories(${OPENSSL_INCLUDE_DIR})

add_executable(passwordManager main.cpp PasswordManager.cpp)

target_include_directories(sqlite3 PUBLIC ../lib)
target_link_libraries(passwordManager PRIVATE sqlite3 ${OPENSSL_LIBRARIES})

add_subdirectory(test)
add_subdirectory(DataBase)
