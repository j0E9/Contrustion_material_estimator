Floor Plan Material Estimator & Cost Calculator


An automated Python tool that processes structural floor plan images to estimate required construction materials (cement, sand, aggregates, bricks, steel, paint) and calculate total material costs based on user-selected brands.

The project integrates deep learning via YOLO for structural layout analysis, OpenCV and scikit-image for mathematical morphology (skeletonization) to measure centerline length, and EasyOCR to extract dimensional text from drawings.

🚀 Features
Automated Scaling: Computes physical dimensions from pixel space using a known structural reference object.

Structural Point Detection: Uses a custom-trained YOLO model to identify structural elements (e.g., T-Junctions).

Centerline Extraction: Uses Canny Edge detection and skeletonization algorithms to accurately capture the total linear wall lengths.

OCR Dimension Processing: Extracts room dimensions text (e.g., 3000 x 4000) directly from the image using EasyOCR.

Detailed Material Takeoff: Computes volumetric quantities for:

Foundations (Footings, Plinth, and PCC)

Brickwork masonry (with automated deduction factors)

Reinforced Concrete (RC) works & steel reinforcement weight

Internal/External plastering surface area

Surface painting area requirements

Interactive Dynamic Costing: Allows real-time console selection of material types and brands (e.g., UltraTech, TATA Steel, Asian Paints) to generate a complete localized pricing breakdown.

🛠️ Tech Stack & Dependencies
Make sure you have Python installed, then install the required core libraries:

Bash
pip install numpy opencv-python ultralytics scikit-image easyocr
Note: tkinter is used for native file dialog popups and comes pre-installed with standard Python distributions on Windows/macOS.

📋 Project Structure & Data Requirements
Before running the script, ensure your environment handles the following paths referenced in the code:

YOLO Weights: A trained model file located at your specified local directory (default in code points to E:\datset\...). Update this path to your localized best.pt file.

💻 How To Use
Run the Script:

python estimator.py



**File Selection:**
    *   A GUI window will pop up prompting you to select your **Floor Plan Image**.
    *   A second window will ask for a **Section Image** (optional/can be canceled to skip).
3.  **Automatic Processing:**
    *   The script reads the image, runs object detection, finds text markings, and processes wall centerlines.
4.  **Interactive Cost Estimation:**
    *   The console will prompt you to dynamically select your preferred brands and grade qualities for Cement, Sand, Coarse Aggregate, Steel, Bricks, and Paint.
5.  **Output:** 
    *   A fully compiled breakdown of physical volumes, individual material weight allocations, and an itemized financial cost summary is printed straight to the terminal.

---

## 📊 Sample CLI Output Demonstration


Image: C:/Users/Project/floor_plan.png
T-Junctions Detected: 14
Total Centerline Length: 45210.12 mm
Total Area: 112.45 m²

=== Foundation Details ===
Total Foundation Quantity: 50.603 m³

=== Total Materials Used ===
Total Cement Used: 412 bags
Total Sand Used: 12450.32 kg
Total Coarse Aggregate Used: 24110.8 kg
Total Steel Used: 1235.41 kg
Total Bricks Used: 8437 units

Select Cement Brand:
1. Ultratech - Rs350
2. Ramco - Rs340
3. Chettinad - Rs320
Enter your choice (1/2/3): 1

... [Other Material Selections] ...

=== Total Cost ===
Grand Total: Rs 432,650.00


⚖️ Custom Estimation Assumptions
The internal engineering constants applied within calculations are:

Wall Thickness: $300\mm
Plaster Thickness: $12\mm
Density of Steel: $7850\kg/m^3
Standard Paint Coverage: $1\Liter
per $5\m^2
