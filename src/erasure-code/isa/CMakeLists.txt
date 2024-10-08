# ISA
set(isal_src_dir ${CMAKE_SOURCE_DIR}/src/isa-l)
include_directories(${isal_src_dir}/include)

if(HAVE_NASM_X64_AVX2)
  set(CMAKE_ASM_FLAGS "-i ${isal_src_dir}/include/ ${CMAKE_ASM_FLAGS}")
  set(isa_srcs
    ${isal_src_dir}/erasure_code/ec_base.c
    ${isal_src_dir}/erasure_code/gf_2vect_dot_prod_sse.asm
    ${isal_src_dir}/erasure_code/gf_3vect_dot_prod_sse.asm
    ${isal_src_dir}/erasure_code/gf_4vect_dot_prod_sse.asm
    ${isal_src_dir}/erasure_code/gf_5vect_dot_prod_sse.asm
    ${isal_src_dir}/erasure_code/gf_6vect_dot_prod_sse.asm
    ${isal_src_dir}/erasure_code/gf_vect_dot_prod_sse.asm
    ${isal_src_dir}/erasure_code/gf_2vect_mad_avx2.asm
    ${isal_src_dir}/erasure_code/gf_3vect_mad_avx2.asm
    ${isal_src_dir}/erasure_code/gf_4vect_mad_avx2.asm
    ${isal_src_dir}/erasure_code/gf_5vect_mad_avx2.asm
    ${isal_src_dir}/erasure_code/gf_6vect_mad_avx2.asm
    ${isal_src_dir}/erasure_code/gf_vect_mad_avx2.asm
    ${isal_src_dir}/erasure_code/ec_highlevel_func.c
    ${isal_src_dir}/erasure_code/gf_2vect_mad_avx.asm
    ${isal_src_dir}/erasure_code/gf_3vect_mad_avx.asm
    ${isal_src_dir}/erasure_code/gf_4vect_mad_avx.asm
    ${isal_src_dir}/erasure_code/gf_5vect_mad_avx.asm
    ${isal_src_dir}/erasure_code/gf_6vect_mad_avx.asm
    ${isal_src_dir}/erasure_code/gf_vect_mad_avx.asm
    ${isal_src_dir}/erasure_code/ec_multibinary.asm
    ${isal_src_dir}/erasure_code/gf_2vect_mad_sse.asm
    ${isal_src_dir}/erasure_code/gf_3vect_mad_sse.asm
    ${isal_src_dir}/erasure_code/gf_4vect_mad_sse.asm
    ${isal_src_dir}/erasure_code/gf_5vect_mad_sse.asm
    ${isal_src_dir}/erasure_code/gf_6vect_mad_sse.asm
    ${isal_src_dir}/erasure_code/gf_vect_mad_sse.asm
    ${isal_src_dir}/erasure_code/gf_2vect_dot_prod_avx2.asm
    ${isal_src_dir}/erasure_code/gf_3vect_dot_prod_avx2.asm
    ${isal_src_dir}/erasure_code/gf_4vect_dot_prod_avx2.asm
    ${isal_src_dir}/erasure_code/gf_5vect_dot_prod_avx2.asm
    ${isal_src_dir}/erasure_code/gf_6vect_dot_prod_avx2.asm
    ${isal_src_dir}/erasure_code/gf_vect_dot_prod_avx2.asm
    ${isal_src_dir}/erasure_code/gf_vect_mul_avx.asm
    ${isal_src_dir}/erasure_code/gf_2vect_dot_prod_avx.asm
    ${isal_src_dir}/erasure_code/gf_3vect_dot_prod_avx.asm
    ${isal_src_dir}/erasure_code/gf_4vect_dot_prod_avx.asm
    ${isal_src_dir}/erasure_code/gf_5vect_dot_prod_avx.asm
    ${isal_src_dir}/erasure_code/gf_6vect_dot_prod_avx.asm
    ${isal_src_dir}/erasure_code/gf_vect_dot_prod_avx.asm
    ${isal_src_dir}/erasure_code/gf_vect_mul_sse.asm
    ${isal_src_dir}/erasure_code/gf_2vect_dot_prod_avx512.asm
    ${isal_src_dir}/erasure_code/gf_2vect_mad_avx512.asm
    ${isal_src_dir}/erasure_code/gf_3vect_dot_prod_avx512.asm
    ${isal_src_dir}/erasure_code/gf_3vect_mad_avx512.asm
    ${isal_src_dir}/erasure_code/gf_4vect_dot_prod_avx512.asm
    ${isal_src_dir}/erasure_code/gf_4vect_mad_avx512.asm
    ${isal_src_dir}/erasure_code/gf_vect_dot_prod_avx512.asm
    ${isal_src_dir}/erasure_code/gf_vect_mad_avx512.asm
    ${isal_src_dir}/raid/raid_base.c
    ${isal_src_dir}/raid/raid_multibinary.asm
    ${isal_src_dir}/raid/xor_check_sse.asm
    ${isal_src_dir}/raid/xor_gen_sse.asm
    ${isal_src_dir}/raid/xor_gen_avx.asm
    ${isal_src_dir}/raid/xor_gen_avx512.asm
    ${isal_src_dir}/raid/pq_check_sse.asm
    ${isal_src_dir}/raid/pq_gen_sse.asm
    ${isal_src_dir}/raid/pq_gen_avx.asm
    ${isal_src_dir}/raid/pq_gen_avx2.asm
    ErasureCodeIsa.cc
    ErasureCodeIsaTableCache.cc
    ErasureCodePluginIsa.cc
  )
elseif(HAVE_ARMV8_SIMD)
  set(isa_srcs
    ${isal_src_dir}/erasure_code/ec_base.c
    ${isal_src_dir}/erasure_code/aarch64/ec_aarch64_highlevel_func.c
    ${isal_src_dir}/erasure_code/aarch64/ec_aarch64_dispatcher.c
    ${isal_src_dir}/erasure_code/aarch64/gf_2vect_dot_prod_neon.S
    ${isal_src_dir}/erasure_code/aarch64/gf_2vect_mad_neon.S
    ${isal_src_dir}/erasure_code/aarch64/gf_3vect_dot_prod_neon.S
    ${isal_src_dir}/erasure_code/aarch64/gf_3vect_mad_neon.S
    ${isal_src_dir}/erasure_code/aarch64/gf_4vect_dot_prod_neon.S
    ${isal_src_dir}/erasure_code/aarch64/gf_4vect_mad_neon.S
    ${isal_src_dir}/erasure_code/aarch64/gf_5vect_dot_prod_neon.S
    ${isal_src_dir}/erasure_code/aarch64/gf_5vect_mad_neon.S
    ${isal_src_dir}/erasure_code/aarch64/gf_6vect_mad_neon.S
    ${isal_src_dir}/erasure_code/aarch64/gf_vect_dot_prod_neon.S
    ${isal_src_dir}/erasure_code/aarch64/gf_vect_mad_neon.S
    ${isal_src_dir}/erasure_code/aarch64/gf_vect_mul_neon.S
    ${isal_src_dir}/erasure_code/aarch64/ec_multibinary_arm.S
    ${isal_src_dir}/raid/raid_base.c
    ${isal_src_dir}/raid/aarch64/raid_aarch64_dispatcher.c
    ${isal_src_dir}/raid/aarch64/raid_multibinary_arm.S
    ${isal_src_dir}/raid/aarch64/xor_check_neon.S
    ${isal_src_dir}/raid/aarch64/xor_gen_neon.S
    ${isal_src_dir}/raid/aarch64/pq_check_neon.S
    ${isal_src_dir}/raid/aarch64/pq_gen_neon.S
    ErasureCodeIsa.cc
    ErasureCodeIsaTableCache.cc
    ErasureCodePluginIsa.cc
  )
  set_source_files_properties(
    ${isal_src_dir}/erasure_code/aarch64/ec_multibinary_arm.S
    ${isal_src_dir}/raid/aarch64/raid_multibinary_arm.S
    PROPERTIES COMPILE_FLAGS "-D__ASSEMBLY__"
  )
endif()

add_library(ec_isa SHARED
  ${isa_srcs}
  $<TARGET_OBJECTS:erasure_code_objs>)
target_link_libraries(ec_isa ${EXTRALIBS})
set_target_properties(ec_isa PROPERTIES
  INSTALL_RPATH "")
install(TARGETS ec_isa DESTINATION ${erasure_plugin_dir})
