---

layout: post

author: softwareshinobi

title:  "Shinobi Tech Jutsu / Automating Image Magick"

categories: [Developer Tools, Bash]

tags: [ Markdown, Automation, MkDocs, Bash Scripting, Images ]

image: assets/imagery/covers/jhbtzied.jpg

description: "Sick of manually wrangling image references in your MkDocs project? This Bash script is your automation hero –  it'll auto-magically generate a markdown file bursting with all your JPG and PNG images. No sweat, all win!"

hidden: false

---

Sick of manually wrangling image references in your MkDocs project? This Bash script is your automation hero –  it'll auto-magically generate a markdown file bursting with all your JPG and PNG images. No sweat, all win!


** What We're Doing**

Today, we're diving into the world of markdown automation, specifically how to whip up a markdown file bursting with all the images in your current directory. This little trick is perfect for anyone using a markdown server like MkDocs and wants to serve up those sweet visuals in a snap. 

**Why Automate Image Inclusion?**

* **Speed Demon:** Manually adding image references can be a tedious task, especially with a directory full of pictures. This script automates the process, saving you precious time and repetitive keystrokes.
* **Accuracy Ace:**  Let's face it, manual entries are prone to typos. This script ensures all your images are referenced correctly, keeping your markdown file clean and error-free.
* **Future-Proofing:**  Adding new images? No problem! Just drop them in the directory, and the script will automatically include them in the next run. Easy peasy.

**The Script Sorcery:**

Here's the magic code that will weave its spell and generate your markdown file:

```sh
# Filename for the markdown file (change if needed)
markdown_file="index.md"

# Start the markdown file with a title
echo "# Images" > "$markdown_file"

# Loop through all image files (JPG and PNG)
for image in *.jpg *.png; do
  # Check if file exists before referencing
  if [[ -f "$image" ]]; then
    # Add an image reference to the markdown file with proper alt text (add your own!)
    echo "![](./$image "Your descriptive alt text here")" >> "$markdown_file"
  fi
done

echo "Markdown file '$markdown_file' created with image references."
```

**Breaking Down the Brilliance:**

* **File Setup:** The script defines the filename for your markdown file (change "index.md" if needed).
* **Title Time:** It starts the file with a clear and concise title – "# Images".
* **Image Inclusion Loop:** The `for` loop iterates through all files ending in `.jpg` or `.png`, ensuring both image types are included.
* **File Existence Check:** A check is added (`[[ -f "$image" ]]`) to verify if the file exists before referencing it. This eliminates errors if there are no images or non-image files present.
* **Organized Paths:** The image reference uses `./$image` to create a relative path within the markdown file. This ensures the reference works correctly when the file is included in other documents.
* **Descriptive Alt Text (Optional):**  While not required by the script, consider adding alt text within the square brackets for each image. This improves accessibility by providing a textual description for screen readers and users who can't see the image.

**Putting it All Together:**

Save this script as a `.sh` file (e.g., `automate_images.sh`) and run it from your terminal.  It will generate a markdown file (`index.md` by default) containing references to all your JPG and PNG images in the current directory. 

Now, when you fire up your MkDocs server, all those images will be displayed in all their glory! 

**Bonus Tip:**  Feel free to modify the script to fit your specific needs. You can change the filename, add different image formats, or even customize the alt text placeholder. 

So, coders, go forth and automate your image inclusion! This script is a handy tool to streamline your workflow and keep your markdown files looking sharp.  In the next article, we'll delve deeper into the world of MkDocs and explore some cool tricks to make your documentation truly shine! 
