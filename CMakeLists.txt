cmake_minimum_required(VERSION 3.16.3)

project(Nuklear VERSION 0.0.1 LANGUAGES C)

if(NOT CMAKE_BUILD_TYPE)
  set(CMAKE_BUILD_TYPE Debug)
endif()

add_library(Nuklear
  STATIC
    src/nuklear_9slice.c
    src/nuklear_buffer.c
    src/nuklear_button.c
    src/nuklear_chart.c
    src/nuklear_color_picker.c
    src/nuklear_color.c
    src/nuklear_combo.c
    src/nuklear_context.c
    src/nuklear_contextual.c
    src/nuklear_draw.c
    src/nuklear_edit.c
    src/nuklear_font.c
    src/nuklear_group.c
    src/nuklear_image.c
    src/nuklear_input.c
    src/nuklear_layout.c
    src/nuklear_list_view.c
    src/nuklear_math.c
    src/nuklear_menu.c
    src/nuklear_page_element.c
    src/nuklear_panel.c
    src/nuklear_pool.c
    src/nuklear_popup.c
    src/nuklear_progress.c
    src/nuklear_property.c
    src/nuklear_scrollbar.c
    src/nuklear_selectable.c
    src/nuklear_slider.c
    src/nuklear_string.c
    src/nuklear_style.c
    src/nuklear_table.c
    src/nuklear_text_editor.c
    src/nuklear_text.c
    src/nuklear_toggle.c
    src/nuklear_tooltip.c
    src/nuklear_tree.c
    src/nuklear_utf8.c
    src/nuklear_util.c
    src/nuklear_vertex.c
    src/nuklear_widget.c
    src/nuklear_window.c
)

# Some flags needs to be defined in every header instantiation, while others affect
# only the internal implementation. See the 'Usage/Flags' section of the docs to
# check which is which.
target_compile_definitions(Nuklear
  PUBLIC
    $<$<BOOL:${NK_INCLUDE_FIXED_TYPES}>:NK_INCLUDE_FIXED_TYPES>
    $<$<BOOL:${NK_INCLUDE_DEFAULT_ALLOCATOR}>:NK_INCLUDE_DEFAULT_ALLOCATOR>
    $<$<BOOL:${NK_INCLUDE_STANDARD_VARARGS}>:NK_INCLUDE_STANDARD_VARARGS>
    $<$<BOOL:${NK_INCLUDE_STANDARD_BOOL}>:NK_INCLUDE_STANDARD_BOOL>
    $<$<BOOL:${NK_INCLUDE_VERTEX_BUFFER_OUTPUT}>:NK_INCLUDE_VERTEX_BUFFER_OUTPUT>
    $<$<BOOL:${NK_INCLUDE_FONT_BAKING}>:NK_INCLUDE_FONT_BAKING>
    $<$<BOOL:${NK_INCLUDE_DEFAULT_FONT}>:NK_INCLUDE_DEFAULT_FONT>
    $<$<BOOL:${NK_INCLUDE_COMMAND_USERDATA}>:NK_INCLUDE_COMMAND_USERDATA>
    $<$<BOOL:${NK_UINT_DRAW_INDEX}>:NK_UINT_DRAW_INDEX>
)
target_compile_definitions(Nuklear
  PRIVATE
    $<$<BOOL:${NK_INCLUDE_STANDARD_IO}>:NK_INCLUDE_STANDARD_IO>
    $<$<BOOL:${NK_BUTTON_TRIGGER_ON_RELEASE}>:NK_BUTTON_TRIGGER_ON_RELEASE>
    $<$<BOOL:${NK_ZERO_COMMAND_MEMORY}>:NK_ZERO_COMMAND_MEMORY>
    $<$<BOOL:${NK_KEYSTATE_BASED_INPUT}>:NK_KEYSTATE_BASED_INPUT>
)

target_include_directories(Nuklear
  PUBLIC
    src
)

target_compile_features(Nuklear PRIVATE c_std_90)
set_target_properties(Nuklear
  PROPERTIES
    C_STANDARD_REQUIRED ON
    C_EXTENSIONS OFF
)
