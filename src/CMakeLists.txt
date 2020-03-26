set(openfec_sources
	lib_stable/ldpc_staircase/of_ldpc_staircase_api.c
	lib_stable/ldpc_staircase/of_ldpc_staircase.h
	lib_stable/ldpc_staircase/of_codec_profile.h
	lib_stable/ldpc_staircase/of_ldpc_includes.h
	lib_stable/ldpc_staircase/of_ldpc_staircase_api.h
	lib_stable/ldpc_staircase/of_ldpc_staircase_pchk.c
	lib_stable/reed-solomon_gf_2_8/of_reed-solomon_gf_2_8_api.h
	lib_stable/reed-solomon_gf_2_8/of_reed-solomon_gf_2_8.h
	lib_stable/reed-solomon_gf_2_8/of_reed-solomon_gf_2_8_includes.h
	lib_stable/reed-solomon_gf_2_8/of_reed-solomon_gf_2_8_api.c
	lib_stable/reed-solomon_gf_2_8/of_codec_profile.h
	lib_stable/reed-solomon_gf_2_8/of_reed-solomon_gf_2_8.c
	lib_stable/reed-solomon_gf_2_m/of_reed-solomon_gf_2_m_includes.h
	lib_stable/reed-solomon_gf_2_m/of_codec_profile.h
	lib_stable/reed-solomon_gf_2_m/of_reed-solomon_gf_2_m_api.h
	lib_stable/reed-solomon_gf_2_m/of_reed-solomon_gf_2_m.h
	lib_stable/reed-solomon_gf_2_m/of_reed-solomon_gf_2_m_api.c
	lib_stable/reed-solomon_gf_2_m/galois_field_codes_utils/of_galois_field_code.c
	lib_stable/reed-solomon_gf_2_m/galois_field_codes_utils/algebra_2_4.h
	lib_stable/reed-solomon_gf_2_m/galois_field_codes_utils/algebra_2_8.c
	lib_stable/reed-solomon_gf_2_m/galois_field_codes_utils/of_galois_field_code.h
	lib_stable/reed-solomon_gf_2_m/galois_field_codes_utils/algebra_2_8.h
	lib_stable/reed-solomon_gf_2_m/galois_field_codes_utils/algebra_2_4.c
	lib_stable/2d_parity_matrix/of_2d_parity_api.h
	lib_stable/2d_parity_matrix/of_2d_parity_api.c
	lib_stable/2d_parity_matrix/of_2d_parity_includes.h
	lib_stable/2d_parity_matrix/of_codec_profile.h
	lib_stable/2d_parity_matrix/of_2d_parity.h
	lib_common/statistics/of_statistics.h
	lib_common/statistics/of_statistics.c
	lib_common/of_rand.c
	lib_common/of_cb.h
	lib_common/of_rand.h
	lib_common/of_debug.h
	lib_common/of_mem.c
	lib_common/linear_binary_codes_utils/binary_matrix/of_matrix_sparse.c
	lib_common/linear_binary_codes_utils/binary_matrix/of_hamming_weight.c
	lib_common/linear_binary_codes_utils/binary_matrix/of_matrix_dense.h
	lib_common/linear_binary_codes_utils/binary_matrix/of_matrix_convert.h
	lib_common/linear_binary_codes_utils/binary_matrix/of_matrix_sparse.h
	lib_common/linear_binary_codes_utils/binary_matrix/of_hamming_weight.h
	lib_common/linear_binary_codes_utils/binary_matrix/of_matrix_dense.c
	lib_common/linear_binary_codes_utils/binary_matrix/of_tools.c
	lib_common/linear_binary_codes_utils/binary_matrix/of_tools.h
	lib_common/linear_binary_codes_utils/binary_matrix/of_matrix_convert.c
	lib_common/linear_binary_codes_utils/ml_decoding/of_ml_decoding.h
	lib_common/linear_binary_codes_utils/ml_decoding/of_ml_decoding.c
	lib_common/linear_binary_codes_utils/ml_decoding/of_ml_tool.c
	lib_common/linear_binary_codes_utils/ml_decoding/of_ml_tool.h
	lib_common/linear_binary_codes_utils/of_symbol.h
	lib_common/linear_binary_codes_utils/of_symbol.c
	lib_common/linear_binary_codes_utils/of_create_pchk.c
	lib_common/linear_binary_codes_utils/of_linear_binary_code.h
	lib_common/linear_binary_codes_utils/it_decoding/of_it_decoding.c
	lib_common/linear_binary_codes_utils/it_decoding/of_it_decoding.h
	lib_common/linear_binary_codes_utils/of_create_pchk.h
	lib_common/of_mem.h
	lib_common/of_openfec_profile.h
	lib_common/of_openfec_api.h
	lib_common/of_openfec_api.c
	lib_common/of_types.h
	lib_advanced/ldpc_from_file/of_ldpc_ff_api.h
	lib_advanced/ldpc_from_file/of_ldpc_ff_includes.h
	lib_advanced/ldpc_from_file/of_codec_profile.h
	lib_advanced/ldpc_from_file/of_ldpc_includes.h
	lib_advanced/ldpc_from_file/of_ldpc_ff_api.c
	lib_advanced/ldpc_from_file/of_ldpc_ff.h
)

add_library(openfec  SHARED  ${openfec_sources})

# From: $cmake --help-property SOVERSION
#		For shared libraries VERSION and SOVERSION can be used to specify
#		the build version and api version respectively.
#
# Edit it as appropriate to be in line with the src/lib_common/of_openfec_api.c::more_about() version
#
set_target_properties(openfec PROPERTIES
			VERSION 1.4.2
			SOVERSION 1) 

# Feel free to edit as appropriate the "target_link_libraries".
#
# Add the IL (DevIL) library if you want to have the possibility to
# produce H/G matrix images with LDPC codes.
# More precisely, we are relying on the DevIL library
# (http://openil.sourceforge.net/).
# Please install it on your machine before compiling the OpenFEC
# library if needed.
# Otherwise remove the IL library.

target_link_libraries(openfec m)
#target_link_libraries(openfec m IL)

#target_link_libraries(openfec pthread IL)
#target_link_libraries(openfec pthread)
