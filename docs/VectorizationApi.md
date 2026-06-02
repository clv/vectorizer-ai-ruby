# VectorizerAI::VectorizationApi

All URIs are relative to *https://api.vectorizer.ai/api/v1*

| Method | HTTP request | Description |
| ------ | ------------ | ----------- |
| [**post_delete**](VectorizationApi.md#post_delete) | **POST** /delete | Delete a retained image |
| [**post_download**](VectorizationApi.md#post_download) | **POST** /download | Download a retained result |
| [**post_vectorize**](VectorizationApi.md#post_vectorize) | **POST** /vectorize | Vectorize an image |


## post_delete

> <DeleteImageResponse> post_delete(opts)

Delete a retained image

Delete a retained image and result before its retention period expires.

### Examples

```ruby
require 'time'
require 'vectorizer_ai'
# setup authorization
VectorizerAI.configure do |config|
  # Configure HTTP basic authorization: basicAuth
  config.username = 'YOUR USERNAME'
  config.password = 'YOUR PASSWORD'
end

api_instance = VectorizerAI::VectorizationApi.new
opts = {
    image_token: 'image_token_example', # String | Image Token to delete before its retention period expires. (required)
}

begin
  # Delete a retained image
  result = api_instance.post_delete(opts)
  p result
rescue VectorizerAI::ApiError => e
  puts "Error when calling VectorizationApi->post_delete: #{e}"
end
```

#### Using the post_delete_with_http_info variant

This returns an Array which contains the response data, status code and headers.

> <Array(<DeleteImageResponse>, Integer, Hash)> post_delete_with_http_info(opts)

```ruby
begin
  # Delete a retained image
  data, status_code, headers = api_instance.post_delete_with_http_info(opts)
  p status_code # => 2xx
  p headers # => { ... }
  p data # => <DeleteImageResponse>
rescue VectorizerAI::ApiError => e
  puts "Error when calling VectorizationApi->post_delete_with_http_info: #{e}"
end
```

### Parameters

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **image_token** | **String** | Image Token to delete before its retention period expires. |  |

### Return type

[**DeleteImageResponse**](DeleteImageResponse.md)

### Authorization

[basicAuth](../README.md#basicAuth)

### HTTP request headers

- **Content-Type**: multipart/form-data
- **Accept**: application/json


## post_download

> File post_download(opts)

Download a retained result

Download a production result from a retained Image Token, optionally changing output.file_format and other output options. Include receipt when downloading additional formats after upgrading a preview result.

### Examples

```ruby
require 'time'
require 'vectorizer_ai'
# setup authorization
VectorizerAI.configure do |config|
  # Configure HTTP basic authorization: basicAuth
  config.username = 'YOUR USERNAME'
  config.password = 'YOUR PASSWORD'
end

api_instance = VectorizerAI::VectorizationApi.new
opts = {
    image_token: 'image_token_example', # String | Image Token returned from a vectorize request with policy.retention_days > 0. (required)
    receipt: 'receipt_example', # String | Receipt returned in the X-Receipt response header when upgrading a preview result to production. Include it when downloading additional formats from that upgraded preview.
    output_file_format: 'svg', # String | Output file format to generate.
    output_shape_stacking: 'cutouts', # String | Whether shapes are cut out of each other or stacked atop each other.
    output_group_by: 'none', # String | Grouping of shapes in output.
    output_draw_style: 'fill_shapes', # String | How shapes are rendered.
    output_strokes_stroke_width: 3.4, # Float | Width of stroke for shape outlines (when enabled).
    output_strokes_non_scaling_stroke: true, # Boolean | Use non-scaling strokes when drawing shape outlines.
    output_strokes_use_override_color: true, # Boolean | Override shape color with a specific color.
    output_strokes_override_color: 'output_strokes_override_color_example', # String | Color value to override shape stroke color if enabled. Must be in '#RRGGBB' or 'rgba(r,g,b,a)' format.
    output_gap_filler_enabled: true, # Boolean | Enable filling small visual gaps caused by vector rendering artifacts.
    output_gap_filler_non_scaling_stroke: true, # Boolean | Use non-scaling strokes for gap filling.
    output_gap_filler_clip: true, # Boolean | Clip gap filler strokes to shape bounds when stacking shapes.
    output_gap_filler_stroke_width: 3.4, # Float | Width of the gap filler strokes (in output units).
    output_parameterized_shapes_flatten: true, # Boolean | Whether to flatten detected circles, rectangles, and stars to curves.
    output_curves_line_fit_tolerance: 3.4, # Float | Maximum allowed error when approximating curves with line segments.
    output_curves_allowed_quadratic_bezier: true, # Boolean | Allow quadratic Bézier curves in the output.
    output_curves_allowed_cubic_bezier: true, # Boolean | Allow cubic Bézier curves in the output.
    output_curves_allowed_circular_arc: true, # Boolean | Allow circular arcs in the output.
    output_curves_allowed_elliptical_arc: true, # Boolean | Allow elliptical arcs in the output.
    output_svg_version: 'svg_1_0', # String | SVG version to declare in the SVG output.
    output_svg_fixed_size: true, # Boolean | Whether to fix the SVG dimensions in the output file.
    output_svg_adobe_compatibility_mode: true, # Boolean | Enable Illustrator compatibility by disabling unsupported SVG features.
    output_pdf_version: 'PDF_1_4', # String | PDF version to generate for PDF output.
    output_pdf_compression_mode: 'None', # String | Compression method to apply to PDF output streams.
    output_eps_version: 'PS_3_0_EPSF_3_0', # String | EPS format version for EPS output.
    output_dxf_compatibility_level: 'lines_only', # String | Level of primitive support for DXF output.
    output_bitmap_anti_aliasing_mode: 'anti_aliased', # String | Anti-aliasing mode for bitmap (PNG) output.
    output_size_scale: 3.4, # Float | Overall uniform scaling factor for the output image.
    output_size_width: 3.4, # Float | Output width, in the selected unit (see output.size.unit).
    output_size_height: 3.4, # Float | Output height, in the selected unit (see output.size.unit).
    output_size_unit: 'none', # String | Measurement unit for output dimensions.
    output_size_aspect_ratio: 'preserve_inset', # String | How to preserve or stretch aspect ratio.
    output_size_align_x: 3.4, # Float | Horizontal alignment (0.0 = left, 0.5 = center, 1.0 = right) when aspect ratio is preserved.
    output_size_align_y: 3.4, # Float | Vertical alignment (0.0 = top, 0.5 = center, 1.0 = bottom) when aspect ratio is preserved.
    output_size_input_dpi: 3.4, # Float | Override the detected DPI of the input image for size computations.
    output_size_output_dpi: 3.4, # Float | DPI setting for the output image.
}

begin
  # Download a retained result
  result = api_instance.post_download(opts)
  p result
rescue VectorizerAI::ApiError => e
  puts "Error when calling VectorizationApi->post_download: #{e}"
end
```

#### Using the post_download_with_http_info variant

This returns an Array which contains the response data, status code and headers.

> <Array(File, Integer, Hash)> post_download_with_http_info(opts)

```ruby
begin
  # Download a retained result
  data, status_code, headers = api_instance.post_download_with_http_info(opts)
  p status_code # => 2xx
  p headers # => { ... }
  p data # => File
rescue VectorizerAI::ApiError => e
  puts "Error when calling VectorizationApi->post_download_with_http_info: #{e}"
end
```

### Parameters

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **image_token** | **String** | Image Token returned from a vectorize request with policy.retention_days &gt; 0. |  |
| **receipt** | **String** | Receipt returned in the X-Receipt response header when upgrading a preview result to production. Include it when downloading additional formats from that upgraded preview. | [optional] |
| **output_file_format** | **String** | Output file format to generate. | [optional][default to &#39;svg&#39;] |
| **output_shape_stacking** | **String** | Whether shapes are cut out of each other or stacked atop each other. | [optional][default to &#39;cutouts&#39;] |
| **output_group_by** | **String** | Grouping of shapes in output. | [optional][default to &#39;none&#39;] |
| **output_draw_style** | **String** | How shapes are rendered. | [optional][default to &#39;fill_shapes&#39;] |
| **output_strokes_stroke_width** | **Float** | Width of stroke for shape outlines (when enabled). | [optional][default to 1] |
| **output_strokes_non_scaling_stroke** | **Boolean** | Use non-scaling strokes when drawing shape outlines. | [optional][default to true] |
| **output_strokes_use_override_color** | **Boolean** | Override shape color with a specific color. | [optional][default to false] |
| **output_strokes_override_color** | **String** | Color value to override shape stroke color if enabled. Must be in &#39;#RRGGBB&#39; or &#39;rgba(r,g,b,a)&#39; format. | [optional][default to &#39;#000000&#39;] |
| **output_gap_filler_enabled** | **Boolean** | Enable filling small visual gaps caused by vector rendering artifacts. | [optional][default to true] |
| **output_gap_filler_non_scaling_stroke** | **Boolean** | Use non-scaling strokes for gap filling. | [optional][default to true] |
| **output_gap_filler_clip** | **Boolean** | Clip gap filler strokes to shape bounds when stacking shapes. | [optional][default to false] |
| **output_gap_filler_stroke_width** | **Float** | Width of the gap filler strokes (in output units). | [optional][default to 2] |
| **output_parameterized_shapes_flatten** | **Boolean** | Whether to flatten detected circles, rectangles, and stars to curves. | [optional][default to false] |
| **output_curves_line_fit_tolerance** | **Float** | Maximum allowed error when approximating curves with line segments. | [optional][default to 0.1] |
| **output_curves_allowed_quadratic_bezier** | **Boolean** | Allow quadratic Bézier curves in the output. | [optional][default to true] |
| **output_curves_allowed_cubic_bezier** | **Boolean** | Allow cubic Bézier curves in the output. | [optional][default to true] |
| **output_curves_allowed_circular_arc** | **Boolean** | Allow circular arcs in the output. | [optional][default to true] |
| **output_curves_allowed_elliptical_arc** | **Boolean** | Allow elliptical arcs in the output. | [optional][default to true] |
| **output_svg_version** | **String** | SVG version to declare in the SVG output. | [optional][default to &#39;svg_1_1&#39;] |
| **output_svg_fixed_size** | **Boolean** | Whether to fix the SVG dimensions in the output file. | [optional][default to false] |
| **output_svg_adobe_compatibility_mode** | **Boolean** | Enable Illustrator compatibility by disabling unsupported SVG features. | [optional][default to false] |
| **output_pdf_version** | **String** | PDF version to generate for PDF output. | [optional][default to &#39;PDF_1_4&#39;] |
| **output_pdf_compression_mode** | **String** | Compression method to apply to PDF output streams. | [optional][default to &#39;Deflate&#39;] |
| **output_eps_version** | **String** | EPS format version for EPS output. | [optional][default to &#39;PS_3_0_EPSF_3_0&#39;] |
| **output_dxf_compatibility_level** | **String** | Level of primitive support for DXF output. | [optional][default to &#39;lines_and_arcs&#39;] |
| **output_bitmap_anti_aliasing_mode** | **String** | Anti-aliasing mode for bitmap (PNG) output. | [optional][default to &#39;anti_aliased&#39;] |
| **output_size_scale** | **Float** | Overall uniform scaling factor for the output image. | [optional] |
| **output_size_width** | **Float** | Output width, in the selected unit (see output.size.unit). | [optional] |
| **output_size_height** | **Float** | Output height, in the selected unit (see output.size.unit). | [optional] |
| **output_size_unit** | **String** | Measurement unit for output dimensions. | [optional][default to &#39;none&#39;] |
| **output_size_aspect_ratio** | **String** | How to preserve or stretch aspect ratio. | [optional][default to &#39;preserve_inset&#39;] |
| **output_size_align_x** | **Float** | Horizontal alignment (0.0 &#x3D; left, 0.5 &#x3D; center, 1.0 &#x3D; right) when aspect ratio is preserved. | [optional][default to 0.5] |
| **output_size_align_y** | **Float** | Vertical alignment (0.0 &#x3D; top, 0.5 &#x3D; center, 1.0 &#x3D; bottom) when aspect ratio is preserved. | [optional][default to 0.5] |
| **output_size_input_dpi** | **Float** | Override the detected DPI of the input image for size computations. | [optional] |
| **output_size_output_dpi** | **Float** | DPI setting for the output image. | [optional] |

### Return type

**File**

### Authorization

[basicAuth](../README.md#basicAuth)

### HTTP request headers

- **Content-Type**: multipart/form-data
- **Accept**: image/svg+xml, application/postscript, application/pdf, application/dxf, image/png, application/json


## post_vectorize

> File post_vectorize(opts)

Vectorize an image

Submit exactly one image source as multipart form data: image, image.url, image.base64, or image.token. The response body is the generated SVG, EPS, PDF, DXF, or PNG file selected by output.file_format. Clients should allow an idle timeout of at least 180 seconds.

### Examples

```ruby
require 'time'
require 'vectorizer_ai'
# setup authorization
VectorizerAI.configure do |config|
  # Configure HTTP basic authorization: basicAuth
  config.username = 'YOUR USERNAME'
  config.password = 'YOUR PASSWORD'
end

api_instance = VectorizerAI::VectorizationApi.new
opts = {
    image: File.new('/path/to/some/file'), # File | Binary file upload of the image to vectorize. Accepts .bmp, .gif, .jpeg, .png, or .tiff files.
    image_url: 'image_url_example', # String | URL to fetch the input image from for vectorization.
    image_base64: 'BYTE_ARRAY_DATA_HERE', # String | Base64-encoded string of the input image. Maximum size 1 megabyte.
    image_token: 'image_token_example', # String | An Image Token returned from an earlier vectorization call with policy.retention_days > 0.
    mode: 'production', # String | Mode of operation, useful during integration work.
    input_max_pixels: 56, # Integer | Maximum input image size (width × height in pixels) before resizing.
    policy_retention_days: 56, # Integer | Number of days to retain the uploaded image and its results for re-use.
    processing_max_colors: 56, # Integer | Maximum number of colors allowed in the vectorization result. 0 means unlimited.
    processing_shapes_min_area_px: 3.4, # Float | Minimum shape area (in pixels) to keep in the result; smaller shapes are discarded.
    processing_palette: 'processing_palette_example', # String | Palette remapping and color control, using '[color][-> remapped][~ tolerance];' format.
    processing_color_profile_input: 'ignore', # String | How to handle ICC profiles embedded in input images.
    processing_color_profile_output: 'processing_color_profile_output_example', # String | ICC profile behavior for output files: preserve, ignore.
    processing_parameterized_shapes_ellipse_general_enabled: true, # Boolean | Enable detection and parameterization of this parameterized shape type.
    processing_parameterized_shapes_ellipse_circle_enabled: true, # Boolean | Enable detection and parameterization of this parameterized shape type.
    processing_parameterized_shapes_triangle_general_enabled: true, # Boolean | Enable detection and parameterization of this parameterized shape type.
    processing_parameterized_shapes_triangle_isosceles_enabled: true, # Boolean | Enable detection and parameterization of this parameterized shape type.
    processing_parameterized_shapes_quadrilateral_general_enabled: true, # Boolean | Enable detection and parameterization of this parameterized shape type.
    processing_parameterized_shapes_quadrilateral_rectangle_enabled: true, # Boolean | Enable detection and parameterization of this parameterized shape type.
    processing_parameterized_shapes_quadrilateral_bullet_enabled: true, # Boolean | Enable detection and parameterization of this parameterized shape type.
    processing_parameterized_shapes_star_n3_enabled: true, # Boolean | Enable detection and parameterization of this parameterized shape type.
    processing_parameterized_shapes_star_n4_enabled: true, # Boolean | Enable detection and parameterization of this parameterized shape type.
    processing_parameterized_shapes_star_n5_enabled: true, # Boolean | Enable detection and parameterization of this parameterized shape type.
    processing_parameterized_shapes_star_n6_enabled: true, # Boolean | Enable detection and parameterization of this parameterized shape type.
    output_file_format: 'svg', # String | Output file format to generate.
    output_shape_stacking: 'cutouts', # String | Whether shapes are cut out of each other or stacked atop each other.
    output_group_by: 'none', # String | Grouping of shapes in output.
    output_draw_style: 'fill_shapes', # String | How shapes are rendered.
    output_strokes_stroke_width: 3.4, # Float | Width of stroke for shape outlines (when enabled).
    output_strokes_non_scaling_stroke: true, # Boolean | Use non-scaling strokes when drawing shape outlines.
    output_strokes_use_override_color: true, # Boolean | Override shape color with a specific color.
    output_strokes_override_color: 'output_strokes_override_color_example', # String | Color value to override shape stroke color if enabled. Must be in '#RRGGBB' or 'rgba(r,g,b,a)' format.
    output_gap_filler_enabled: true, # Boolean | Enable filling small visual gaps caused by vector rendering artifacts.
    output_gap_filler_non_scaling_stroke: true, # Boolean | Use non-scaling strokes for gap filling.
    output_gap_filler_clip: true, # Boolean | Clip gap filler strokes to shape bounds when stacking shapes.
    output_gap_filler_stroke_width: 3.4, # Float | Width of the gap filler strokes (in output units).
    output_parameterized_shapes_flatten: true, # Boolean | Whether to flatten detected circles, rectangles, and stars to curves.
    output_curves_line_fit_tolerance: 3.4, # Float | Maximum allowed error when approximating curves with line segments.
    output_curves_allowed_quadratic_bezier: true, # Boolean | Allow quadratic Bézier curves in the output.
    output_curves_allowed_cubic_bezier: true, # Boolean | Allow cubic Bézier curves in the output.
    output_curves_allowed_circular_arc: true, # Boolean | Allow circular arcs in the output.
    output_curves_allowed_elliptical_arc: true, # Boolean | Allow elliptical arcs in the output.
    output_svg_version: 'svg_1_0', # String | SVG version to declare in the SVG output.
    output_svg_fixed_size: true, # Boolean | Whether to fix the SVG dimensions in the output file.
    output_svg_adobe_compatibility_mode: true, # Boolean | Enable Illustrator compatibility by disabling unsupported SVG features.
    output_pdf_version: 'PDF_1_4', # String | PDF version to generate for PDF output.
    output_pdf_compression_mode: 'None', # String | Compression method to apply to PDF output streams.
    output_eps_version: 'PS_3_0_EPSF_3_0', # String | EPS format version for EPS output.
    output_dxf_compatibility_level: 'lines_only', # String | Level of primitive support for DXF output.
    output_bitmap_anti_aliasing_mode: 'anti_aliased', # String | Anti-aliasing mode for bitmap (PNG) output.
    output_size_scale: 3.4, # Float | Overall uniform scaling factor for the output image.
    output_size_width: 3.4, # Float | Output width, in the selected unit (see output.size.unit).
    output_size_height: 3.4, # Float | Output height, in the selected unit (see output.size.unit).
    output_size_unit: 'none', # String | Measurement unit for output dimensions.
    output_size_aspect_ratio: 'preserve_inset', # String | How to preserve or stretch aspect ratio.
    output_size_align_x: 3.4, # Float | Horizontal alignment (0.0 = left, 0.5 = center, 1.0 = right) when aspect ratio is preserved.
    output_size_align_y: 3.4, # Float | Vertical alignment (0.0 = top, 0.5 = center, 1.0 = bottom) when aspect ratio is preserved.
    output_size_input_dpi: 3.4, # Float | Override the detected DPI of the input image for size computations.
    output_size_output_dpi: 3.4, # Float | DPI setting for the output image.
}

begin
  # Vectorize an image
  result = api_instance.post_vectorize(opts)
  p result
rescue VectorizerAI::ApiError => e
  puts "Error when calling VectorizationApi->post_vectorize: #{e}"
end
```

#### Using the post_vectorize_with_http_info variant

This returns an Array which contains the response data, status code and headers.

> <Array(File, Integer, Hash)> post_vectorize_with_http_info(opts)

```ruby
begin
  # Vectorize an image
  data, status_code, headers = api_instance.post_vectorize_with_http_info(opts)
  p status_code # => 2xx
  p headers # => { ... }
  p data # => File
rescue VectorizerAI::ApiError => e
  puts "Error when calling VectorizationApi->post_vectorize_with_http_info: #{e}"
end
```

### Parameters

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **image** | **File** | Binary file upload of the image to vectorize. Accepts .bmp, .gif, .jpeg, .png, or .tiff files. | [optional] |
| **image_url** | **String** | URL to fetch the input image from for vectorization. | [optional] |
| **image_base64** | **String** | Base64-encoded string of the input image. Maximum size 1 megabyte. | [optional] |
| **image_token** | **String** | An Image Token returned from an earlier vectorization call with policy.retention_days &gt; 0. | [optional] |
| **mode** | **String** | Mode of operation, useful during integration work. | [optional][default to &#39;production&#39;] |
| **input_max_pixels** | **Integer** | Maximum input image size (width × height in pixels) before resizing. | [optional][default to 2097252] |
| **policy_retention_days** | **Integer** | Number of days to retain the uploaded image and its results for re-use. | [optional][default to 0] |
| **processing_max_colors** | **Integer** | Maximum number of colors allowed in the vectorization result. 0 means unlimited. | [optional][default to 0] |
| **processing_shapes_min_area_px** | **Float** | Minimum shape area (in pixels) to keep in the result; smaller shapes are discarded. | [optional][default to 0.125] |
| **processing_palette** | **String** | Palette remapping and color control, using &#39;[color][-&gt; remapped][~ tolerance];&#39; format. | [optional] |
| **processing_color_profile_input** | **String** | How to handle ICC profiles embedded in input images. | [optional][default to &#39;ignore&#39;] |
| **processing_color_profile_output** | **String** | ICC profile behavior for output files: preserve, ignore. | [optional][default to &#39;ignore&#39;] |
| **processing_parameterized_shapes_ellipse_general_enabled** | **Boolean** | Enable detection and parameterization of this parameterized shape type. | [optional][default to true] |
| **processing_parameterized_shapes_ellipse_circle_enabled** | **Boolean** | Enable detection and parameterization of this parameterized shape type. | [optional][default to true] |
| **processing_parameterized_shapes_triangle_general_enabled** | **Boolean** | Enable detection and parameterization of this parameterized shape type. | [optional][default to true] |
| **processing_parameterized_shapes_triangle_isosceles_enabled** | **Boolean** | Enable detection and parameterization of this parameterized shape type. | [optional][default to true] |
| **processing_parameterized_shapes_quadrilateral_general_enabled** | **Boolean** | Enable detection and parameterization of this parameterized shape type. | [optional][default to true] |
| **processing_parameterized_shapes_quadrilateral_rectangle_enabled** | **Boolean** | Enable detection and parameterization of this parameterized shape type. | [optional][default to true] |
| **processing_parameterized_shapes_quadrilateral_bullet_enabled** | **Boolean** | Enable detection and parameterization of this parameterized shape type. | [optional][default to true] |
| **processing_parameterized_shapes_star_n3_enabled** | **Boolean** | Enable detection and parameterization of this parameterized shape type. | [optional][default to true] |
| **processing_parameterized_shapes_star_n4_enabled** | **Boolean** | Enable detection and parameterization of this parameterized shape type. | [optional][default to true] |
| **processing_parameterized_shapes_star_n5_enabled** | **Boolean** | Enable detection and parameterization of this parameterized shape type. | [optional][default to true] |
| **processing_parameterized_shapes_star_n6_enabled** | **Boolean** | Enable detection and parameterization of this parameterized shape type. | [optional][default to true] |
| **output_file_format** | **String** | Output file format to generate. | [optional][default to &#39;svg&#39;] |
| **output_shape_stacking** | **String** | Whether shapes are cut out of each other or stacked atop each other. | [optional][default to &#39;cutouts&#39;] |
| **output_group_by** | **String** | Grouping of shapes in output. | [optional][default to &#39;none&#39;] |
| **output_draw_style** | **String** | How shapes are rendered. | [optional][default to &#39;fill_shapes&#39;] |
| **output_strokes_stroke_width** | **Float** | Width of stroke for shape outlines (when enabled). | [optional][default to 1] |
| **output_strokes_non_scaling_stroke** | **Boolean** | Use non-scaling strokes when drawing shape outlines. | [optional][default to true] |
| **output_strokes_use_override_color** | **Boolean** | Override shape color with a specific color. | [optional][default to false] |
| **output_strokes_override_color** | **String** | Color value to override shape stroke color if enabled. Must be in &#39;#RRGGBB&#39; or &#39;rgba(r,g,b,a)&#39; format. | [optional][default to &#39;#000000&#39;] |
| **output_gap_filler_enabled** | **Boolean** | Enable filling small visual gaps caused by vector rendering artifacts. | [optional][default to true] |
| **output_gap_filler_non_scaling_stroke** | **Boolean** | Use non-scaling strokes for gap filling. | [optional][default to true] |
| **output_gap_filler_clip** | **Boolean** | Clip gap filler strokes to shape bounds when stacking shapes. | [optional][default to false] |
| **output_gap_filler_stroke_width** | **Float** | Width of the gap filler strokes (in output units). | [optional][default to 2] |
| **output_parameterized_shapes_flatten** | **Boolean** | Whether to flatten detected circles, rectangles, and stars to curves. | [optional][default to false] |
| **output_curves_line_fit_tolerance** | **Float** | Maximum allowed error when approximating curves with line segments. | [optional][default to 0.1] |
| **output_curves_allowed_quadratic_bezier** | **Boolean** | Allow quadratic Bézier curves in the output. | [optional][default to true] |
| **output_curves_allowed_cubic_bezier** | **Boolean** | Allow cubic Bézier curves in the output. | [optional][default to true] |
| **output_curves_allowed_circular_arc** | **Boolean** | Allow circular arcs in the output. | [optional][default to true] |
| **output_curves_allowed_elliptical_arc** | **Boolean** | Allow elliptical arcs in the output. | [optional][default to true] |
| **output_svg_version** | **String** | SVG version to declare in the SVG output. | [optional][default to &#39;svg_1_1&#39;] |
| **output_svg_fixed_size** | **Boolean** | Whether to fix the SVG dimensions in the output file. | [optional][default to false] |
| **output_svg_adobe_compatibility_mode** | **Boolean** | Enable Illustrator compatibility by disabling unsupported SVG features. | [optional][default to false] |
| **output_pdf_version** | **String** | PDF version to generate for PDF output. | [optional][default to &#39;PDF_1_4&#39;] |
| **output_pdf_compression_mode** | **String** | Compression method to apply to PDF output streams. | [optional][default to &#39;Deflate&#39;] |
| **output_eps_version** | **String** | EPS format version for EPS output. | [optional][default to &#39;PS_3_0_EPSF_3_0&#39;] |
| **output_dxf_compatibility_level** | **String** | Level of primitive support for DXF output. | [optional][default to &#39;lines_and_arcs&#39;] |
| **output_bitmap_anti_aliasing_mode** | **String** | Anti-aliasing mode for bitmap (PNG) output. | [optional][default to &#39;anti_aliased&#39;] |
| **output_size_scale** | **Float** | Overall uniform scaling factor for the output image. | [optional] |
| **output_size_width** | **Float** | Output width, in the selected unit (see output.size.unit). | [optional] |
| **output_size_height** | **Float** | Output height, in the selected unit (see output.size.unit). | [optional] |
| **output_size_unit** | **String** | Measurement unit for output dimensions. | [optional][default to &#39;none&#39;] |
| **output_size_aspect_ratio** | **String** | How to preserve or stretch aspect ratio. | [optional][default to &#39;preserve_inset&#39;] |
| **output_size_align_x** | **Float** | Horizontal alignment (0.0 &#x3D; left, 0.5 &#x3D; center, 1.0 &#x3D; right) when aspect ratio is preserved. | [optional][default to 0.5] |
| **output_size_align_y** | **Float** | Vertical alignment (0.0 &#x3D; top, 0.5 &#x3D; center, 1.0 &#x3D; bottom) when aspect ratio is preserved. | [optional][default to 0.5] |
| **output_size_input_dpi** | **Float** | Override the detected DPI of the input image for size computations. | [optional] |
| **output_size_output_dpi** | **Float** | DPI setting for the output image. | [optional] |

### Return type

**File**

### Authorization

[basicAuth](../README.md#basicAuth)

### HTTP request headers

- **Content-Type**: multipart/form-data
- **Accept**: image/svg+xml, application/postscript, application/pdf, application/dxf, image/png, application/json

