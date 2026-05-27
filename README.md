lib/
│
├── main.dart
├── app.dart
├── app_startup.dart
│
├── core/
│   ├── constants/
│   │   ├── app_constants.dart
│   │   ├── canvas_constants.dart
│   │   ├── performance_constants.dart
│   │   ├── gesture_constants.dart
│   │   └── storage_constants.dart
│   ├── extensions/
│   │   ├── offset_extensions.dart
│   │   ├── rect_extensions.dart
│   │   ├── size_extensions.dart
│   │   ├── matrix4_extensions.dart
│   │   ├── path_extensions.dart
│   │   ├── color_extensions.dart
│   │   ├── string_extensions.dart
│   │   ├── build_context_extensions.dart
│   │   ├── iterable_extensions.dart
│   │   ├── num_extensions.dart
│   │   └── duration_extensions.dart
│   ├── utils/
│   │   ├── id_generator.dart
│   │   ├── logger.dart
│   │   ├── debounce.dart
│   │   ├── throttle.dart
│   │   ├── timer_utils.dart
│   │   ├── math_utils.dart
│   │   ├── geometry_utils.dart
│   │   ├── bezier_utils.dart
│   │   ├── color_utils.dart
│   │   ├── text_utils.dart
│   │   ├── file_utils.dart
│   │   ├── date_utils.dart
│   │   ├── compression_utils.dart
│   │   └── platform_utils.dart
│   ├── errors/
│   │   ├── app_exception.dart
│   │   ├── storage_exception.dart
│   │   ├── rendering_exception.dart
│   │   ├── gesture_exception.dart
│   │   ├── serialization_exception.dart
│   │   └── error_handler.dart
│   ├── memory/
│   │   ├── memory_monitor.dart
│   │   ├── memory_pressure_handler.dart
│   │   ├── object_pool.dart
│   │   ├── cache_manager.dart
│   │   ├── image_cache_manager.dart
│   │   ├── disposable.dart
│   │   └── weak_reference_map.dart
│   ├── performance/
│   │   ├── frame_monitor.dart
│   │   ├── performance_budget.dart
│   │   ├── performance_overlay.dart
│   │   ├── render_profiler.dart
│   │   └── performance_mode.dart
│   ├── platform/
│   │   ├── platform_info.dart
│   │   ├── platform_channel.dart
│   │   ├── haptic_feedback.dart
│   │   └── device_memory_info.dart
│   ├── di/
│   │   ├── app_providers.dart
│   │   ├── storage_providers.dart
│   │   ├── canvas_providers.dart
│   │   └── service_providers.dart
│   └── network/
│       ├── connectivity_monitor.dart
│       └── sync_status.dart
│
├── features/
│   │
│   ├── canvas/                          # محرك إطار العرض (Viewport)
│   │   ├── domain/models/              # viewport_state, canvas_bounds, camera, grid_config
│   │   ├── domain/repositories/         # canvas_repository interface
│   │   ├── domain/usecases/             # get/set viewport, fit_to_content, focus_node
│   │   ├── data/repositories/           # canvas_repository_impl
│   │   ├── data/datasources/            # local datasource, cache
│   │   ├── data/models/                 # viewport_dto, canvas_config_dto
│   │   ├── presentation/providers/      # viewport_provider, grid_provider
│   │   ├── presentation/widgets/        # canvas_widget, canvas_painter, minimap, grid
│   │   └── presentation/screens/        # canvas_screen
│   │
│   ├── rendering/                       # محرك الرسم (Rendering Engine)
│   │   ├── domain/models/              # render_layer, render_command, paint_style, lod_level
│   │   ├── domain/contracts/            # renderable, spatial_index, render_pipeline
│   │   ├── data/spatial/                # quad_tree, r_tree, spatial_query, bounding_box
│   │   ├── data/culling/                # viewport_culler, occlusion_culler
│   │   ├── data/caching/                # render_cache, geometry_cache, picture_recorder_cache
│   │   ├── data/batching/               # paint_batcher, draw_call, batch_strategy
│   │   ├── presentation/engine/         # render_engine, render_pipeline_impl, render_pass
│   │   ├── presentation/painters/       # background, selection, snap_guide, debug
│   │   └── presentation/providers/      # render_engine_provider, spatial_index_provider
│   │
│   ├── nodes/                           # نظام العقد (Node System)
│   │   ├── domain/models/              # base_node, node_id, node_style + 13 نوع عقدة
│   │   ├── domain/repositories/         # node_repository interface
│   │   ├── domain/usecases/             # create, update, delete, move, resize, group
│   │   ├── data/repositories/           # node_repository_impl
│   │   ├── data/datasources/            # local datasource, node_cache, media_cache
│   │   ├── data/models/                 # 12 DTO + type_converter
│   │   ├── data/tables/                 # node_table (Drift)
│   │   ├── presentation/providers/      # node_list, selected_nodes, node_registry
│   │   ├── presentation/widgets/        # 15 نوع widget + context_menu, edit_overlay
│   │   ├── presentation/painters/       # shadow, border, shape painters
│   │   └── presentation/registry/       # node_registry, node_factory, widget_factory
│   │
│   ├── edges/                           # نظام الحواف (Edge Engine)
│   │   ├── domain/models/              # edge, edge_style, edge_type, edge_route, anchor
│   │   ├── domain/repositories/         # edge_repository interface
│   │   ├── domain/usecases/             # create, delete, update_style, reroute
│   │   ├── data/repositories/           # edge_repository_impl
│   │   ├── data/datasources/            # local datasource, edge_cache
│   │   ├── data/routing/                # straight, curved, step, smart, ortho routers
│   │   ├── data/tables/                 # edge_table (Drift)
│   │   ├── presentation/providers/      # edge_list, edge_routing providers
│   │   ├── presentation/widgets/        # edge_widget, label, anchor, creation_preview
│   │   └── presentation/painters/       # edge, arrow, curve, dashed_line painters
│   │
│   ├── gestures/                        # نظام اللمس (Gesture Engine)
│   │   ├── domain/models/              # gesture_event, gesture_type, touch_point, velocity
│   │   ├── domain/contracts/            # gesture_handler, gesture_arbiter
│   │   ├── data/recognizers/            # pan, pinch_zoom, double_tap, long_press, lasso
│   │   ├── data/arbitration/            # gesture_arbiter_impl, arena, priority_tree
│   │   ├── data/tracking/               # pointer_tracker, velocity_estimator, inertial_scroller
│   │   ├── presentation/providers/      # gesture_provider, pointer_provider
│   │   ├── presentation/widgets/        # gesture_handler, node_drag, edge_drag, pan
│   │   └── presentation/handlers/       # tap, long_press, pinch_zoom, double_tap, lasso
│   │
│   ├── selection/                       # نظام التحديد (Selection)
│   │   ├── domain/models/              # selection_state, mode, lasso_path, bounds
│   │   ├── domain/usecases/             # select, deselect, lasso, marquee, invert
│   │   ├── presentation/providers/      # selection_provider
│   │   └── presentation/widgets/        # marquee, lasso, handles, toolbar
│   │
│   ├── mindmap/                         # محرك الخريطة الذهنية
│   │   ├── domain/models/              # mindmap_tree, layout_config, fold_state
│   │   ├── domain/usecases/             # add_child, fold, unfold, auto_arrange, convert
│   │   ├── data/layouts/                # tree, radial, fishbone, organic, compact
│   │   ├── data/algorithms/             # tree_positioner, radial, subtree_metrics
│   │   ├── data/animation/              # layout_animator, fold_animation
│   │   ├── presentation/providers/      # mindmap, layout, fold providers
│   │   ├── presentation/widgets/        # mindmap_widget, node, edge, fold_button
│   │   └── presentation/painters/       # mindmap_edge, fold_indicator painters
│   │
│   ├── alignment/                       # المحاذاة والجذب (Snap/Align)
│   │   ├── domain/models/              # snap_config, snap_result, alignment_guide
│   │   ├── domain/usecases/             # snap_to_grid, snap_to_node, align, distribute
│   │   └── presentation/               # smart_guides_overlay, snap_feedback
│   │
│   ├── state_management/                # نظام التراجع/الإعادة (Undo/Redo)
│   │   ├── domain/models/              # command, command_history, command_group
│   │   ├── data/commands/               # 11 نوع أمر (create, delete, move, resize, etc.)
│   │   ├── data/history/                # undo_redo_manager, history_compressor, limit
│   │   ├── data/snapshot/               # state_snapshot, snapshot_compressor
│   │   └── presentation/providers/      # undo_redo_provider, command_provider
│   │
│   ├── storage/                         # التخزين والاستمرارية
│   │   ├── domain/models/              # project, save_state, backup_info, migration
│   │   ├── domain/usecases/             # save, load, export, import, backup, migrate
│   │   ├── data/database/               # Drift DB + 9 tables + 8 DAOs + migrations
│   │   ├── data/services/               # auto_save, crash_recovery, backup, compression
│   │   ├── data/preferences/            # Hive-based preferences
│   │   └── presentation/providers/      # database, project, save_state providers
│   │
│   ├── search/                          # البحث والفهرسة
│   │   ├── domain/models/              # search_query, result, filter, index
│   │   ├── data/indexing/               # text, tag, property indexers + fuzzy_matcher
│   │   └── presentation/               # search_bar, results, filter_chips
│   │
│   ├── tags/                            # نظام الوسوم
│   │   ├── domain/                      # tag, tag_group models + usecases
│   │   └── presentation/               # tag_chip, tag_input, filter_panel
│   │
│   ├── export/                          # نظام التصدير
│   │   ├── domain/                      # export_config, format, region, quality
│   │   ├── data/services/               # image, pdf, svg, json export + privacy mode
│   │   ├── data/renderers/              # offscreen_canvas, tiled_renderer
│   │   └── presentation/               # export_dialog, preview, share_button
│   │
│   ├── templates/                       # نظام القوالب
│   │   ├── domain/                      # template, category, data models
│   │   └── presentation/               # gallery, card, preview widgets
│   │
│   ├── journal/                         # نظام اليوميات
│   │   ├── domain/                      # journal_entry, date (Hijri/Gregorian), link
│   │   └── presentation/               # daily_journal, calendar, timeline
│   │
│   ├── rtl/                             # دعم العربية و RTL
│   │   ├── domain/services/             # bidi_detector, arabic_typography, numerals, dates
│   │   ├── presentation/               # rtl_wrapper, bidi_text, mirrored_icon
│   │   └── presentation/theme/         # arabic_text_theme, rtl_aware_theme
│   │
│   └── ui/                              # واجهة المستخدم
│       ├── theme/                       # app_theme, colors, typography, spacing
│       ├── components/                  # app_bar, buttons, inputs, sheets, dialogs
│       ├── menus/                       # radial_menu, context_menu, toolbar, quick_actions
│       ├── navigation/                  # router, route_guards
│       └── screens/                     # canvas, project_list, settings screens
│
├── l10n/                                # الترجمة
│   ├── app_ar.dart
│   └── app_en.dart
│
└── gen/                                 # ملفات مُولّدة
    ├── l10n/
    └── assets.gen.dart
