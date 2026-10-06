# 🤖 AI CAD Assistant: Drawing & Image-to-3D Engine

AI-assisted application for reconstructing 3D mechanical geometry from either:

- **Engineering drawings / blueprints**
- **Reference images / product images**

The app uses a multimodal Gemini model to interpret the input image, identify geometric features and dimensions, generate CAD geometry programmatically, validate the resulting mesh, and display it in an interactive 3D viewer.

---

## ✨ Capabilities

### 🔍 Automatic Input Detection
The application can automatically determine whether the uploaded image is:

- **Engineering Drawing / Blueprint**
- **Reference Image / Product Image**

The user can also override the detected mode manually.

---

### 📐 Engineering Drawing Reconstruction
For technical drawings, the system prioritizes:

- Explicit dimensions
- Engineering annotations
- Holes and slots
- Radii and chamfers
- Orthographic views
- Geometric constraints

Explicit measurements take priority over visual proportions.

---

### 📷 Reference Image to 3D
The application can also reconstruct a plausible 3D representation from:

- Product images
- Photographs
- CAD renders
- Screenshots
- Isometric illustrations

When exact dimensions are unavailable, the system preserves visible proportions and infers missing geometry.

A known real-world dimension can optionally be provided as a **scale anchor**.

---

### 🧠 AI Geometry Interpretation
Before generating the 3D model, the system analyzes the image and extracts information such as:

- Part identification
- Dimensions
- Geometric features
- Repeated structures
- Symmetry
- Assumptions
- Uncertainties
- Confidence scores

This allows the user to review what the AI understood before generating the model.

---

### ✏️ Human-in-the-Loop Review
Users can provide corrections or additional information before CAD generation.

Examples:

```text
There are 8 wires, not 7.
Overall width is 32 mm.
The hidden side is symmetrical.
```

---

### 🧱 CAD Geometry Generation
The application generates geometry using:

- **Trimesh** for 3D primitives
- **Manifold3D** for Constructive Solid Geometry (CSG)

Typical operations include:

```text
Base
+ Rib
+ Boss
- Hole
- Slot
```

---

### 🔄 Automatic CAD Repair
If the generated CAD code fails, the application can automatically send the error back to Gemini and attempt to repair the geometry before returning an error to the user.

---

### 🌐 Interactive 3D Viewer
Generated models can be inspected directly in the browser using **Three.js**.

The viewer supports:

- Rotation
- Zoom
- Pan
- Full 360° inspection
- Bottom-side inspection

---

### ✅ Geometry Validation
The generated mesh is checked for:

- Watertight topology
- Face winding consistency
- Finite vertex coordinates
- Volume
- Surface area
- Bounding dimensions
- Vertex count
- Face count

---

### 📥 STL Export
Generated models can be downloaded as `.stl` files for further use in:

- 3D printing workflows
- CAD tools
- Visualization
- Simulation pipelines

---

## 🏗️ Architecture

```text
                   Input Image
                       │
                       ▼
                Gemini Vision
                       │
                 Auto Detection
                       │
          ┌────────────┴────────────┐
          │                         │
          ▼                         ▼
 Engineering Drawing        Reference Image
      Analysis                  Analysis
          │                         │
          └────────────┬────────────┘
                       ▼
             Geometry Interpretation
                       │
                Human Review
                       │
                       ▼
              CAD Code Generation
                       │
                  Auto Repair
                       │
                       ▼
          Trimesh + Manifold3D
                       │
                Mesh Validation
                       │
          ┌────────────┴────────────┐
          ▼                         ▼
    Three.js Viewer                STL
```

---

## 🛠️ Tech Stack

- Python
- Google Gemini
- Streamlit
- Trimesh
- Manifold3D
- NumPy
- Pillow
- Three.js
- WebGL

---

## 📦 Installation

Clone the repository:

```bash
git clone https://github.com/YOUR_USERNAME/YOUR_REPOSITORY.git
cd YOUR_REPOSITORY
```

Create a virtual environment:

```bash
python -m venv .venv
```

Activate it.

### Windows

```bash
.venv\Scripts\activate
```

### Linux / macOS

```bash
source .venv/bin/activate
```

Install dependencies:

```bash
pip install streamlit google-genai trimesh manifold3d numpy pillow python-dotenv
```

---

## 🔑 Configuration

Create a `.env` file in the project root:

```env
GEMINI_API_KEY=YOUR_GEMINI_API_KEY
```

Optional:

```env
GEMINI_MODEL=gemini-3.8-flash
```

Add `.env` to `.gitignore`:

```text
.env
.venv/
__pycache__/
*.pyc
```

---

## ▶️ Run the App

```bash
streamlit run app.py
```

Then open the Streamlit URL shown in the terminal.

---

## 📂 Suggested Repository Structure

```text
ai-cad-assistant/
│
├── app.py
├── README.md
├── requirements.txt
├── .gitignore
│
└── assets/
    ├── demo.gif
    ├── input_example.png
    └── generated_model.png
```

---

## 🎯 Project Motivation

This project explores the use of multimodal AI as a reasoning layer between visual information and deterministic engineering tools.

Instead of directly generating a 3D mesh, the workflow is:

```text
Image
  ↓
AI Understanding
  ↓
Geometry Reasoning
  ↓
CAD Operations
  ↓
Deterministic Geometry Engine
  ↓
3D Model
```

The project is an experiment toward more intelligent and accessible **AI-assisted CAD and engineering workflows**.

---

## 📸 Demo

Add your GIF or screenshot here:
#### Test 1
<img width="1911" height="912" alt="Image" src="https://github.com/user-attachments/assets/5bcf5aaf-5618-4a69-bdcd-3abcc4b15647" />

#### Test 2
<img width="1907" height="902" alt="Image" src="https://github.com/user-attachments/assets/c64dcc8c-8540-49ae-8714-0a4225079209" />

#### Test 3
<img width="1898" height="957" alt="Image" src="https://github.com/user-attachments/assets/cb594f1b-8db1-4cad-8577-5b7b1780a888" />

#### Test 4
<img width="1903" height="962" alt="Image" src="https://github.com/user-attachments/assets/30a1acf3-a644-4656-980d-b1f42338ee44" />

#### Test 4
<img width="1898" height="903" alt="Image" src="https://github.com/user-attachments/assets/b56fa1c3-5078-44c4-b086-c034299bee6d" />

---

## 👤 Author

**Savadogo Abdoul**

AI · Industrial AI · Smart Manufacturing · Digital Transformation
