if (DEFINED ESP_PLATFORM)
  idf_component_register(SRCS "miniz.c"
    INCLUDE_DIRS "." # ignore original miniz.h
    REQUIRES esp_rom)
  target_compile_options(${COMPONENT_LIB} PRIVATE 
    -DMINIZ_EXPORT= 
    -DMZ_FREE=free
    -DMZ_MALLOC=malloc
    -DMZ_REALLOC=realloc)
else ()
  include("project.cmake")
endif ()