if(APPLE)
  set(CMAKE_C_FLAGS "-O2 -Wall -mmacosx-version-min=10.5  -arch i386 -Dunix")
else()
  if(MINGW)
    set(CMAKE_C_FLAGS "-O2 -Wall -DWIN32")
  else()
    set(CMAKE_C_FLAGS "-O2 -Wall -Dlinux -Dunix")
  endif()
endif()

link_directories(../cdp2k ../sfsys)

include_directories(../../include)

add_executable(houskeep main.c ap_house.c channels.c clean.c dump.c dupl.c respec.c sort.c)

target_link_libraries(houskeep cdp2k sfsys ${EXTRA_LIBRARIES})

my_install(houskeep)

