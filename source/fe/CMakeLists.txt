## ---------------------------------------------------------------------
##
## Copyright (C) 2012 - 2021 by the deal.II authors
##
## This file is part of the deal.II library.
##
## The deal.II library is free software; you can use it, redistribute
## it, and/or modify it under the terms of the GNU Lesser General
## Public License as published by the Free Software Foundation; either
## version 2.1 of the License, or (at your option) any later version.
## The full text of the license can be found in the file LICENSE.md at
## the top level directory of deal.II.
##
## ---------------------------------------------------------------------

INCLUDE_DIRECTORIES(BEFORE ${CMAKE_CURRENT_BINARY_DIR})

SET(_unity_include_src
  block_mask.cc
  component_mask.cc
  fe_abf.cc
  fe_bernardi_raugel.cc
  fe_bdm.cc
  fe.cc
  fe_bernstein.cc
  fe_data.cc
  fe_dgp.cc
  fe_dgp_monomial.cc
  fe_dgp_nonparametric.cc
  fe_dgq.cc
  fe_dg_vector.cc
  fe_enriched.cc
  fe_face.cc
  fe_nedelec.cc
  fe_nedelec_sz.cc
  fe_nothing.cc
  fe_poly.cc
  fe_poly_tensor.cc
  fe_pyramid_p.cc
  fe_p1nc.cc
  fe_q_base.cc
  fe_q.cc
  fe_q_bubbles.cc
  fe_q_dg0.cc
  fe_q_hierarchical.cc
  fe_q_iso_q1.cc
  fe_rannacher_turek.cc
  fe_raviart_thomas.cc
  fe_raviart_thomas_nodal.cc
  fe_rt_bubbles.cc
  fe_series.cc
  fe_series_fourier.cc
  fe_series_legendre.cc
  fe_system.cc
  fe_simplex_p.cc
  fe_simplex_p_bubbles.cc
  fe_trace.cc
  fe_values_extractors.cc
  fe_wedge_p.cc
  mapping_c1.cc
  mapping_cartesian.cc
  mapping.cc
  mapping_fe.cc
  mapping_q1.cc
  mapping_q.cc
  mapping_q_cache.cc
  mapping_manifold.cc
  )

SET(_separate_src
  fe_values.cc
  fe_values_inst2.cc
  fe_values_inst3.cc
  fe_values_inst4.cc
  fe_values_inst5.cc
  fe_values_inst6.cc
  mapping_fe_field.cc
  mapping_fe_field_inst2.cc
  fe_tools.cc
  fe_tools_interpolate.cc
  fe_tools_extrapolate.cc
  mapping_q1_eulerian.cc
  mapping_q_eulerian.cc
  )

# determined by profiling
SET(_n_includes_per_unity_file 10)

SETUP_SOURCE_LIST("${_unity_include_src}"
  "${_separate_src}"
  ${_n_includes_per_unity_file}
  _src
  )

SET(_inst
  fe_abf.inst.in
  fe_bdm.inst.in
  fe_bernstein.inst.in
  fe_dgp.inst.in
  fe_dgp_monomial.inst.in
  fe_dgp_nonparametric.inst.in
  fe_dgq.inst.in
  fe_dg_vector.inst.in
  fe_face.inst.in
  fe.inst.in
  fe_nedelec.inst.in
  fe_nedelec_sz.inst.in
  fe_nothing.inst.in
  fe_poly.inst.in
  fe_poly_tensor.inst.in
  fe_pyramid_p.inst.in
  fe_q_base.inst.in
  fe_q_bubbles.inst.in
  fe_q_dg0.inst.in
  fe_q_hierarchical.inst.in
  fe_q.inst.in
  fe_q_iso_q1.inst.in
  fe_rannacher_turek.inst.in
  fe_raviart_thomas.inst.in
  fe_raviart_thomas_nodal.inst.in
  fe_rt_bubbles.inst.in
  fe_series_fourier.inst.in
  fe_series_legendre.inst.in
  fe_simplex_p.inst.in
  fe_simplex_p_bubbles.inst.in
  fe_system.inst.in
  fe_enriched.inst.in
  fe_tools.inst.in
  fe_tools_interpolate.inst.in
  fe_tools_extrapolate.inst.in
  fe_trace.inst.in
  fe_values.decl.1.inst.in
  fe_values.decl.2.inst.in
  fe_values.impl.1.inst.in
  fe_values.impl.2.inst.in
  fe_values.inst.in
  fe_wedge_p.inst.in
  mapping_c1.inst.in
  mapping_cartesian.inst.in
  mapping.inst.in
  mapping_fe.inst.in
  mapping_fe_field.inst.in
  mapping_q1_eulerian.inst.in
  mapping_q1.inst.in
  mapping_q_cache.inst.in
  mapping_q_eulerian.inst.in
  mapping_q.inst.in
  mapping_manifold.inst.in
  )

FILE(GLOB _header
  ${CMAKE_SOURCE_DIR}/include/deal.II/fe/*.h
  )

DEAL_II_ADD_LIBRARY(obj_fe OBJECT ${_src} ${_header} ${_inst})
EXPAND_INSTANTIATIONS(obj_fe "${_inst}")
