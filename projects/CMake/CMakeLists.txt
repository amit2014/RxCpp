cmake_minimum_required(VERSION 3.2 FATAL_ERROR)

project(rxcpp VERSION 2.2.4 LANGUAGES C CXX)

set_property(GLOBAL PROPERTY USE_FOLDERS ON)

# define some folders

get_filename_component(RXCPP_DIR "${CMAKE_CURRENT_SOURCE_DIR}" PATH)
get_filename_component(RXCPP_DIR "${RXCPP_DIR}" PATH)

MESSAGE( STATUS "RXCPP_DIR: " ${RXCPP_DIR} )

add_subdirectory(${RXCPP_DIR}/Rx/v2/test ${CMAKE_CURRENT_BINARY_DIR}/test)

add_subdirectory(${RXCPP_DIR}/projects/doxygen ${CMAKE_CURRENT_BINARY_DIR}/projects/doxygen)

set(EXAMPLES_DIR ${RXCPP_DIR}/Rx/v2/examples)

add_subdirectory(${EXAMPLES_DIR}/cep ${CMAKE_CURRENT_BINARY_DIR}/examples/cep)
add_subdirectory(${EXAMPLES_DIR}/stop ${CMAKE_CURRENT_BINARY_DIR}/examples/stop)
add_subdirectory(${EXAMPLES_DIR}/linesfrombytes ${CMAKE_CURRENT_BINARY_DIR}/examples/linesfrombytes)
add_subdirectory(${EXAMPLES_DIR}/println ${CMAKE_CURRENT_BINARY_DIR}/examples/println)
add_subdirectory(${EXAMPLES_DIR}/pythagorian ${CMAKE_CURRENT_BINARY_DIR}/examples/pythagorian)
add_subdirectory(${EXAMPLES_DIR}/tests ${CMAKE_CURRENT_BINARY_DIR}/examples/tests)

# The list of RxCpp source files. Please add every new file to this list
set(RX_SOURCES
   ${RXCPP_DIR}/Rx/v2/src/rxcpp/operators/rx-all.hpp
   ${RXCPP_DIR}/Rx/v2/src/rxcpp/operators/rx-amb.hpp
   ${RXCPP_DIR}/Rx/v2/src/rxcpp/operators/rx-any.hpp
   ${RXCPP_DIR}/Rx/v2/src/rxcpp/operators/rx-buffer_count.hpp
   ${RXCPP_DIR}/Rx/v2/src/rxcpp/operators/rx-buffer_time.hpp
   ${RXCPP_DIR}/Rx/v2/src/rxcpp/operators/rx-buffer_time_count.hpp
   ${RXCPP_DIR}/Rx/v2/src/rxcpp/operators/rx-combine_latest.hpp
   ${RXCPP_DIR}/Rx/v2/src/rxcpp/operators/rx-concat.hpp
   ${RXCPP_DIR}/Rx/v2/src/rxcpp/operators/rx-concat_map.hpp
   ${RXCPP_DIR}/Rx/v2/src/rxcpp/operators/rx-connect_forever.hpp
   ${RXCPP_DIR}/Rx/v2/src/rxcpp/operators/rx-debounce.hpp
   ${RXCPP_DIR}/Rx/v2/src/rxcpp/operators/rx-delay.hpp
   ${RXCPP_DIR}/Rx/v2/src/rxcpp/operators/rx-distinct.hpp
   ${RXCPP_DIR}/Rx/v2/src/rxcpp/operators/rx-distinct_until_changed.hpp
   ${RXCPP_DIR}/Rx/v2/src/rxcpp/operators/rx-element_at.hpp
   ${RXCPP_DIR}/Rx/v2/src/rxcpp/operators/rx-filter.hpp
   ${RXCPP_DIR}/Rx/v2/src/rxcpp/operators/rx-finally.hpp
   ${RXCPP_DIR}/Rx/v2/src/rxcpp/operators/rx-flat_map.hpp
   ${RXCPP_DIR}/Rx/v2/src/rxcpp/operators/rx-group_by.hpp
   ${RXCPP_DIR}/Rx/v2/src/rxcpp/operators/rx-ignore_elements.hpp
   ${RXCPP_DIR}/Rx/v2/src/rxcpp/operators/rx-lift.hpp
   ${RXCPP_DIR}/Rx/v2/src/rxcpp/operators/rx-map.hpp
   ${RXCPP_DIR}/Rx/v2/src/rxcpp/operators/rx-merge.hpp
   ${RXCPP_DIR}/Rx/v2/src/rxcpp/operators/rx-multicast.hpp
   ${RXCPP_DIR}/Rx/v2/src/rxcpp/operators/rx-observe_on.hpp
   ${RXCPP_DIR}/Rx/v2/src/rxcpp/operators/rx-on_error_resume_next.hpp
   ${RXCPP_DIR}/Rx/v2/src/rxcpp/operators/rx-pairwise.hpp
   ${RXCPP_DIR}/Rx/v2/src/rxcpp/operators/rx-publish.hpp
   ${RXCPP_DIR}/Rx/v2/src/rxcpp/operators/rx-reduce.hpp
   ${RXCPP_DIR}/Rx/v2/src/rxcpp/operators/rx-ref_count.hpp
   ${RXCPP_DIR}/Rx/v2/src/rxcpp/operators/rx-repeat.hpp
   ${RXCPP_DIR}/Rx/v2/src/rxcpp/operators/rx-replay.hpp
   ${RXCPP_DIR}/Rx/v2/src/rxcpp/operators/rx-retry.hpp
   ${RXCPP_DIR}/Rx/v2/src/rxcpp/operators/rx-sample_time.hpp
   ${RXCPP_DIR}/Rx/v2/src/rxcpp/operators/rx-scan.hpp
   ${RXCPP_DIR}/Rx/v2/src/rxcpp/operators/rx-skip.hpp
   ${RXCPP_DIR}/Rx/v2/src/rxcpp/operators/rx-skip_last.hpp
   ${RXCPP_DIR}/Rx/v2/src/rxcpp/operators/rx-skip_until.hpp
   ${RXCPP_DIR}/Rx/v2/src/rxcpp/operators/rx-start_with.hpp
   ${RXCPP_DIR}/Rx/v2/src/rxcpp/operators/rx-subscribe.hpp
   ${RXCPP_DIR}/Rx/v2/src/rxcpp/operators/rx-subscribe_on.hpp
   ${RXCPP_DIR}/Rx/v2/src/rxcpp/operators/rx-switch_if_empty.hpp
   ${RXCPP_DIR}/Rx/v2/src/rxcpp/operators/rx-switch_on_next.hpp
   ${RXCPP_DIR}/Rx/v2/src/rxcpp/operators/rx-take.hpp
   ${RXCPP_DIR}/Rx/v2/src/rxcpp/operators/rx-take_last.hpp
   ${RXCPP_DIR}/Rx/v2/src/rxcpp/operators/rx-take_until.hpp
   ${RXCPP_DIR}/Rx/v2/src/rxcpp/operators/rx-tap.hpp
   ${RXCPP_DIR}/Rx/v2/src/rxcpp/operators/rx-time_interval.hpp
   ${RXCPP_DIR}/Rx/v2/src/rxcpp/operators/rx-timeout.hpp
   ${RXCPP_DIR}/Rx/v2/src/rxcpp/operators/rx-timestamp.hpp
   ${RXCPP_DIR}/Rx/v2/src/rxcpp/operators/rx-with_latest_from.hpp
   ${RXCPP_DIR}/Rx/v2/src/rxcpp/operators/rx-window.hpp
   ${RXCPP_DIR}/Rx/v2/src/rxcpp/operators/rx-window_time.hpp
   ${RXCPP_DIR}/Rx/v2/src/rxcpp/operators/rx-window_time_count.hpp
   ${RXCPP_DIR}/Rx/v2/src/rxcpp/operators/rx-zip.hpp
   ${RXCPP_DIR}/Rx/v2/src/rxcpp/rx-connectable_observable.hpp
   ${RXCPP_DIR}/Rx/v2/src/rxcpp/rx-coordination.hpp
   ${RXCPP_DIR}/Rx/v2/src/rxcpp/rx-grouped_observable.hpp
   ${RXCPP_DIR}/Rx/v2/src/rxcpp/rx-includes.hpp
   ${RXCPP_DIR}/Rx/v2/src/rxcpp/rx-notification.hpp
   ${RXCPP_DIR}/Rx/v2/src/rxcpp/rx-observable.hpp
   ${RXCPP_DIR}/Rx/v2/src/rxcpp/rx-observer.hpp
   ${RXCPP_DIR}/Rx/v2/src/rxcpp/rx-operators.hpp
   ${RXCPP_DIR}/Rx/v2/src/rxcpp/rx-predef.hpp
   ${RXCPP_DIR}/Rx/v2/src/rxcpp/rx-scheduler.hpp
   ${RXCPP_DIR}/Rx/v2/src/rxcpp/rx-sources.hpp
   ${RXCPP_DIR}/Rx/v2/src/rxcpp/rx-subjects.hpp
   ${RXCPP_DIR}/Rx/v2/src/rxcpp/rx-subscriber.hpp
   ${RXCPP_DIR}/Rx/v2/src/rxcpp/rx-subscription.hpp
   ${RXCPP_DIR}/Rx/v2/src/rxcpp/rx-test.hpp
   ${RXCPP_DIR}/Rx/v2/src/rxcpp/rx-trace.hpp
   ${RXCPP_DIR}/Rx/v2/src/rxcpp/rx-util.hpp
   ${RXCPP_DIR}/Rx/v2/src/rxcpp/rx.hpp
   ${RXCPP_DIR}/Rx/v2/src/rxcpp/schedulers/rx-currentthread.hpp
   ${RXCPP_DIR}/Rx/v2/src/rxcpp/schedulers/rx-eventloop.hpp
   ${RXCPP_DIR}/Rx/v2/src/rxcpp/schedulers/rx-immediate.hpp
   ${RXCPP_DIR}/Rx/v2/src/rxcpp/schedulers/rx-newthread.hpp
   ${RXCPP_DIR}/Rx/v2/src/rxcpp/schedulers/rx-runloop.hpp
   ${RXCPP_DIR}/Rx/v2/src/rxcpp/schedulers/rx-sameworker.hpp
   ${RXCPP_DIR}/Rx/v2/src/rxcpp/schedulers/rx-test.hpp
   ${RXCPP_DIR}/Rx/v2/src/rxcpp/schedulers/rx-virtualtime.hpp
   ${RXCPP_DIR}/Rx/v2/src/rxcpp/sources/rx-create.hpp
   ${RXCPP_DIR}/Rx/v2/src/rxcpp/sources/rx-defer.hpp
   ${RXCPP_DIR}/Rx/v2/src/rxcpp/sources/rx-error.hpp
   ${RXCPP_DIR}/Rx/v2/src/rxcpp/sources/rx-interval.hpp
   ${RXCPP_DIR}/Rx/v2/src/rxcpp/sources/rx-iterate.hpp
   ${RXCPP_DIR}/Rx/v2/src/rxcpp/sources/rx-never.hpp
   ${RXCPP_DIR}/Rx/v2/src/rxcpp/sources/rx-range.hpp
   ${RXCPP_DIR}/Rx/v2/src/rxcpp/sources/rx-scope.hpp
   ${RXCPP_DIR}/Rx/v2/src/rxcpp/sources/rx-timer.hpp
   ${RXCPP_DIR}/Rx/v2/src/rxcpp/subjects/rx-behavior.hpp
   ${RXCPP_DIR}/Rx/v2/src/rxcpp/subjects/rx-replaysubject.hpp
   ${RXCPP_DIR}/Rx/v2/src/rxcpp/subjects/rx-subject.hpp
   ${RXCPP_DIR}/Rx/v2/src/rxcpp/subjects/rx-synchronize.hpp
)

# Grouping all the source files puts them into a virtual folder in Visual Studio
source_group("src" FILES ${RX_SOURCES})

add_library(RxCpp SHARED ${RX_SOURCES})
SET_TARGET_PROPERTIES(RxCpp PROPERTIES LINKER_LANGUAGE CXX)
