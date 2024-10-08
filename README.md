# Image Resizer & Compressor

A simple Python application for resizing and compressing images. This application provides a clean, intuitive GUI to handle image manipulation tasks efficiently.

## Features

- **Browse Images**: Select an image file from your system.
- **Image Preview**: View a preview of the selected image (currently under review, see troubleshooting section).
- **Resize Images**: Resize images by specifying width and height.
- **Compress Images**: Compress images with adjustable quality settings.
- **Save in Multiple Formats**: Save images in JPEG or PNG formats.

## Requirements

- Python 3.x
- Pillow library (PIL)
- Tkinter (usually included with Python)

## Installation

1. **Clone the Repository**

   ```sh
   git clone https://github.com/prakhardoneria/image-resizer-compressor.git
   cd image-resizer-compressor
   ```

2. **Set Up a Virtual Environment (Optional)**

   ```sh
   python -m venv .venv
   source .venv/bin/activate  # On Windows use: .venv\Scripts\activate
   ```

3. **Install Dependencies**

   ```sh
   pip install -r requirements.txt
   ```

   The `requirements.txt` file should include:
   ```
   pillow
   ```

## Usage

1. **Run the Application**

   ```sh
   python main.py
   ```

2. **Browse for an Image**

   Click the "Browse Image" button to select an image file from your system.

3. **Preview the Image**

   The selected image should appear in the preview area (currently being reviewed for fixes).

4. **Resize the Image**

   - Enter the desired width and height.
   - Select the format (JPEG or PNG).
   - Click the "Resize Image" button to resize the image and save it to a chosen location.

5. **Compress the Image**

   - Enter the desired quality (1-100).
   - Select the format (JPEG or PNG).
   - Click the "Compress Image" button to compress the image and save it to a chosen location.

## Code Structure

- **`main.py`**: The main script for running the GUI application.
- **`resizer.py`**: Contains functions for resizing and compressing images.
- **`utils.py`**: Contains utility functions like `get_save_path` to handle file saving dialogs.

## Troubleshooting

### Image Preview Not Showing
If the image preview isn't appearing in the GUI:

1. Make sure the image is being loaded correctly. You can verify this in `main.py` by checking if the `PIL.Image` object is created successfully.
   
   ```python
   from PIL import Image, ImageTk
   
   # Load image for preview
   img = Image.open(file_path)
   img.thumbnail((300, 300))  # Adjust size for preview
   img_preview = ImageTk.PhotoImage(img)
   
   # Set to label for preview
   preview_label.config(image=img_preview)
   preview_label.image = img_preview  # Keep a reference to avoid garbage collection
   ```

2. If the preview window is not refreshing, ensure that the Tkinter `label` for the preview is updated after browsing.

3. Ensure the Tkinter event loop is properly handling the update of the preview label. You might need to call `preview_label.update()` after setting the new image.

## Contributing

Feel free to submit issues, fork the repository, or open pull requests. Contributions are welcome!
