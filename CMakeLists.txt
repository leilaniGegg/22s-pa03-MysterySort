cmake_minimum_required(VERSION 3.15)
project(PA03_template)
set(CMAKE_CXX_STANDARD 14)

# Create the executable for sorting
add_executable(PA03_sorting_mystery main.cpp DataSets.cpp DataSets.h Mystery01Analysis.cpp Mystery01Analysis.h Mystery02Analysis.cpp Mystery02Analysis.h Mystery03Analysis.cpp Mystery03Analysis.h Mystery04Analysis.cpp Mystery04Analysis.h Mystery05Analysis.cpp Mystery05Analysis.h)

message("Platform: " $ENV{PLATFORM})
if($ENV{PLATFORM} STREQUAL "wsl2")
    message("  Identified wsl2 platform.  Linking to mystery_sorting lib")
    find_library(MYSTERY_LIBRARY mystery_sorting_wsl2 lib)
    target_link_libraries(PA03_sorting_mystery LINK_PUBLIC ${MYSTERY_LIBRARY})
elseif($ENV{PLATFORM} STREQUAL "mac")
    message("  Identified mac platform.  Linking to mystery_sorting_mac lib")
    find_library(MYSTERY_LIBRARY mystery_sorting_mac lib)
    target_link_libraries(PA03_sorting_mystery LINK_PUBLIC ${MYSTERY_LIBRARY})
elseif($ENV{PLATFORM} STREQUAL "mac-intel")
    message("  Identified Intel-mac platform.  Linking to mystery_sorting_mac_intel lib")
    find_library(MYSTERY_LIBRARY mystery_sorting_mac_intel lib)
    target_link_libraries(PA03_sorting_mystery LINK_PUBLIC ${MYSTERY_LIBRARY})
else()
    error("Platform Not Supported")
endif()







