# Copyright 2018 Google Inc.
#
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
#
#      http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.
#
################################################################################

FROM gcr.io/oss-fuzz-base/base-builder
RUN apt-get update && apt-get install -y make libtool pkg-config
RUN git clone --recursive --depth 1 git://git.ghostscript.com/mupdf.git mupdf
RUN git clone --depth 1 https://github.com/derdus/resvg-test-suite.git resvg-test-suite && \
    zip -q $SRC/svg_fuzzer_seed_corpus.zip resvg-test-suite/svg_files/*.svg && \
    rm -rf resvg-test-suite
ADD https://raw.githubusercontent.com/AFLplusplus/AFLplusplus/refs/heads/stable/dictionaries/svg.dict $SRC/svg_fuzzer.dict
WORKDIR mupdf
COPY *.cc $SRC/
COPY build.sh *.options $SRC/
