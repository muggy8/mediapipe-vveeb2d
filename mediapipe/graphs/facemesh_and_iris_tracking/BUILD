# Copyright 2019 The MediaPipe Authors.
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

load(
    "//mediapipe/framework/tool:mediapipe_graph.bzl",
    "mediapipe_binary_graph",
)

licenses(["notice"])

package(default_visibility = ["//visibility:public"])

cc_library(
    name = "gpu_tracking_calculator",
    deps = [
        "//mediapipe/calculators/core:constant_side_packet_calculator",
        "//mediapipe/calculators/core:flow_limiter_calculator",
        "//mediapipe/calculators/core:split_vector_calculator",
        "//mediapipe/graphs/iris_tracking/calculators:update_face_landmarks_calculator",
        "//mediapipe/graphs/iris_tracking/subgraphs:iris_and_depth_renderer_gpu",
        "//mediapipe/modules/face_landmark:face_landmark_front_gpu",
        "//mediapipe/modules/iris_landmark:iris_landmark_left_and_right_gpu",

        "//mediapipe/calculators/core:gate_calculator",
        "//mediapipe/calculators/core:immediate_mux_calculator",
        "//mediapipe/calculators/image:image_properties_calculator",
        "//mediapipe/framework/tool:switch_container",
        "//mediapipe/graphs/face_effect/subgraphs:single_face_geometry_from_landmarks_gpu",
        "//mediapipe/modules/face_geometry:env_generator_calculator",
    ],
)

mediapipe_binary_graph(
    name = "custom_tracking_gpu_binary_graph",
    graph = "face_mesh_and_iris_mobile.pbtxt",
    output_name = "face_mesh_and_iris_mobile.binarypb",
    deps = [":gpu_tracking_calculator"],
)
