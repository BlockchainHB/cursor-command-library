# Gen Image

## Task
Generate product images using Replicate's image generation models based on prompts stored in markdown files. No reference images needed - works purely from text prompts.

## Variables
- **{prompt_file}**: `/Users/neat/New/demo_prompts.md`
- **{output_dir}**: `/Users/neat/New/Generated_Images`
- **{timestamp}**: Current timestamp in format `YYYY-MM-DD_HH-MM-SS`
- **{model}**: `google/nano-banana` (or search for alternatives)

## Product Details (for prompt enhancement)
- **{base_prompt}**: "A premium smart coffee maker, matte black finish with brushed aluminum accents, 'AeroBrew' logo visible on front display, minimalist design"
- **{product_details}**: "sleek cylindrical body, approximately 12 inches tall, touchscreen interface on front, glass carafe with wooden handle, built-in grinder visible on top, modern kitchen appliance aesthetic"

## Workflow

### 1. Setup workspace
- Read `{prompt_file}` to get all prompts (one per line)
- Create output directory: `{output_dir}/{timestamp}/`
- Create subdirectories: `images/`, `prompts/`, `logs/`
- Success: Workspace ready

### 2. Search for image generation model
- Use `mcp_replicate_search` to find suitable models
- Look for: `google/nano-banana`, `black-forest-labs/flux`, or similar
- Verify model accepts text prompts
- Success: Model selected

### 3. Generate images
- For each prompt in `{prompt_file}`:
  - Enhance prompt with product details:
    ```
    {base_prompt}, {product_details}. 
    Setting: {prompt_from_file}
    Style: Professional product photography, clean lighting
    ```
  - Call `mcp_replicate_create_models_predictions`:
    ```json
    {
      "model_owner": "google",
      "model_name": "nano-banana",
      "input": {
        "prompt": "[enhanced prompt]",
        "output_format": "jpg"
      }
    }
    ```
  - Wait for completion (use `Prefer: wait` header)
  - Extract image URL from response
  - Save prompt to `prompts/prompt_{index:03d}.txt`
  - Log generation details
- Success: All images generated

### 4. Download images
- For each generated image URL:
  - Download using `curl` or similar
  - Save as `images/image_{index:03d}.jpg`
  - Handle errors gracefully
- Success: All images downloaded

### 5. Create summary report
- Generate `{output_dir}/{timestamp}/generation_summary.md`:
  ```markdown
  # Image Generation Report - {timestamp}
  
  ## Summary
  - Model: {model}
  - Total Prompts: {count}
  - Successfully Generated: {success_count}
  - Failed: {fail_count}
  
  ## Generated Images
  | Index | Prompt | Status | File |
  |-------|--------|--------|------|
  | 001   | {prompt} | ✓ | image_001.jpg |
  ```
- Open output directory: `open {output_dir}/{timestamp}/`
- Success: Report generated

## Notes
- Prompts should be one per line in the markdown file
- Model parameters vary by model - check Replicate docs
- Some models support `aspect_ratio`, `negative_prompt` - add if available
- For batch processing, consider rate limits

