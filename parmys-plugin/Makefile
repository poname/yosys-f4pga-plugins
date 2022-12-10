# Copyright 2020-2022 F4PGA Authors
#
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
#
#     http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.
#
# SPDX-License-Identifier: Apache-2.0

PLUGIN_DIR := $(abspath $(dir $(lastword $(MAKEFILE_LIST))))

NAME = parmys
SOURCES = parmys.cc \
		  parmys_arch.cc \
		  parmys_update.cc \
		  parmys_utils.cc \
		  parmys_resolve.cc \
		  adders.cc \
		  enum_str.cc \
		  MixingOptimization.cc \
		  read_xml_config_file.cc \
		  odin_error.cc \
		  odin_util.cc \
		  netlist_statistic.cc \
		  netlist_utils.cc \
		  netlist_check.cc \
		  netlist_cleanup.cc \
		  node_creation_library.cc \
		  multipliers.cc \
		  subtractions.cc \
		  HardSoftLogicMixer.cc \
		  odin_ii.cc \
		  string_cache.cc \
		  partial_map.cc \
		  hard_blocks.cc \
		  BlockMemories.cc \
		  memories.cc \
		  netlist_visualizer.cc \
		  Hashtable.cc \
		  ast_util.cc \
		  ../third_party/vtr-libs/vtrutil/src/vtr_util.cc \
		  ../third_party/vtr-libs/vtrutil/src/vtr_token.cc \
		  ../third_party/vtr-libs/vtrutil/src/vtr_memory.cc \
		  ../third_party/vtr-libs/vtrutil/src/vtr_list.cc \
		  ../third_party/vtr-libs/vtrutil/src/vtr_log.cc \
		  ../third_party/vtr-libs/vtrutil/src/vtr_expr_eval.cc \
		  ../third_party/vtr-libs/vtrutil/src/vtr_digest.cc \
		  ../third_party/vtr-libs/vtrutil/src/vtr_math.cc \
		  ../third_party/vtr-libs/vtrutil/src/vtr_path.cc \
		  ../third_party/vtr-libs/vtrutil/src/vtr_assert.cc \
		  ../third_party/vtr-libs/log/src/log.cc \
		  ../third_party/pugixml/src/pugixml.cpp \
		  ../third_party/vtr-libs/argparse/src/argparse.cc \
		  ../third_party/vtr-libs/argparse/src/argparse_formatter.cc \
		  ../third_party/vtr-libs/argparse/src/argparse_util.cc \
		  ../third_party/vtr-libs/rtlnumber/src/rtl_int.cc \
		  ../third_party/vtr-libs/rtlnumber/src/rtl_utils.cc \
		  ../third_party/vtr-libs/pugiutil/src/pugixml_loc.cc \
		  ../third_party/vtr-libs/pugiutil/src/pugixml_util.cc \
		  ../third_party/vtr-libs/archfpga/src/physical_types.cc \
		  ../third_party/vtr-libs/archfpga/src/read_xml_util.cc \
		  ../third_party/vtr-libs/archfpga/src/arch_error.cc \
		  ../third_party/vtr-libs/archfpga/src/physical_types_util.cc \
		  ../third_party/vtr-libs/archfpga/src/arch_check.cc \
		  ../third_party/vtr-libs/archfpga/src/arch_util.cc \
		  ../third_party/vtr-libs/archfpga/src/read_xml_arch_file.cc \
		  ../third_party/vtr-libs/archfpga/src/parse_switchblocks.cc \
		  ../third_party/vtr-libs/archfpga/src/echo_arch.cc

include ../Makefile_plugin.common

CXXFLAGS += -I../third_party/pugixml/src
CXXFLAGS += -I../third_party/vtr-libs/archfpga/src
CXXFLAGS += -I../third_party/vtr-libs/log/src
CXXFLAGS += -I../third_party/vtr-libs/pugiutil/src
CXXFLAGS += -I../third_party/vtr-libs/rtlnumber/src/include
CXXFLAGS += -I../third_party/vtr-libs/rtlnumber/src
CXXFLAGS += -I../third_party/vtr-libs/vtrutil/src
CXXFLAGS += -I../third_party/vtr-libs/argparse/src
CXXFLAGS += -I../third_party/vtr-libs/vpr/src/draw

CXXSTD := c++14
CXXFLAGS += -std=$(CXXSTD) -Os

LDLIBS += -lpthread

VERILOG_MODULES = adff2dff.v \
				  adffe2dff.v \
				  aldff2dff.v \
				  aldffe2dff.v \
				  vtr_primitives.v

# install_modules: $(VERILOG_MODULES)
# install -D $< $(YOSYS_PLUGINS_DIR)/parmys/$<
install_modules: $(VERILOG_MODULES)
	$(foreach f,$^,install -D $(f) $(YOSYS_DATA_DIR)/parmys/$(f);)

install: install_modules

clean_modules:
	rm -rf ./third_party

clean: clean_modules