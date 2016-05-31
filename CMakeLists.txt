cmake_minimum_required(VERSION 2.8.12.2)
project(fjorge)
SET(CMAKE_C_FLAGS "-g -pg -Iinclude -O3 -Wall -ansi -pedantic -std=c11 -DDEBUG -D_FORTIFY_SOURCE=2 -D__STDC_VERSION__=201112L -D__GNUC__")
SET(CFLAGS CMAKE_C_FLAGS)
add_definitions(-DDBNG_PREFIX=\"${CMAKE_INSTALL_PREFIX}\")

add_executable(
	fjorge
  src/add_header.c
  src/array_length.c
  src/basic_auth.c
  src/base64_encode.c
  src/main_function.c
  src/make_hostnames.c
  src/pack_protover.c
  src/parse_cmdline.c
  src/permute_strings.c
  src/print_hostnames.c
  src/print_options.c
  src/print_trace.c
  src/recv_response.c
  src/send_request.c
  src/signal_handler.c
  src/tcp_close.c
  src/tcp_connect.c
  src/tls_connect.c
  src/tls_error.c
  src/tls_recv_response.c
  src/tls_send_request.c
  src/unpack_protover.c
  src/url_decode.c
  src/url_encode.c
  src/usage_desc.c
  include/fjorge.h)

find_library(SSL ssl)
find_library(CRYPTO crypto)
target_link_libraries(fjorge ssl crypto)
install(TARGETS fjorge DESTINATION bin)