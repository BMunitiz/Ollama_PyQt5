# Ollama Chat GUI

A modern desktop chat application built with PyQt5 that provides a user-friendly interface for interacting with Ollama's local language models.

## Overview

This project creates a sleek desktop chat interface that connects to your local Ollama server, allowing you to easily switch between different language models and have conversations in a clean, dark-themed environment.

## Features

### 🖥️ Desktop Interface
- **Framework**: PyQt5 for native desktop experience
- **Theme**: Dark mode with custom styling
- **Layout**: Two-column design for optimal space usage
- **Responsive**: Clean and intuitive user interface

### 🤖 Model Management
- **Auto-Detection**: Automatically loads available Ollama models
- **Dynamic Selection**: Dropdown menu to switch between models
- **Real-time**: Instant model switching without restart

### 💬 Chat Experience
- **Dual Windows**: Separate conversation display and input areas
- **Message Formatting**: Color-coded messages (User vs Assistant)
- **Scroll Management**: Automatic scrolling to latest messages
- **Session Management**: Reset button to clear conversation history

## Installation & Setup

### Prerequisites
```bash
pip install PyQt5 ollama
```

### Running Ollama
Ensure Ollama is installed and running on your system:
```bash
# Start Ollama service
ollama serve

# Pull desired models (optional - will auto-detect existing models)
ollama pull llama2
ollama pull codellama
```

### Launching the Application
```bash
python Ollama_GUI.ipynb
# Or run the code directly if extracted from notebook
```

## Code Structure

### Core Components

```python
class Chat(QWidget):
    def __init__(self):
        super().__init__()
        self.initUI()          # Initialize interface
        self.settings()        # Window configuration  
        self.button_clicks()   # Event handlers
```

### Key Methods
- `initUI()`: Creates and arranges all UI elements
- `button_clicks()`: Handles button interactions
- `query_submission()`: Processes user input and displays messages
- `chat()`: Communicates with Ollama API

### UI Layout
```
MASTER LAYOUT (Horizontal)
├── COLUMN 1 (30%)
│   ├── Title
│   ├── Model Selector
│   ├── Submit Button
│   └── Reset Button
└── COLUMN 2 (70%)
    ├── Conversation Window
    └── Query Input Box
```

## Configuration

### Model Detection
The application automatically detects available models:
```python
models = ollama.list()
model_lists = []
for model in models['models']:
    model_lists.append(model['model'])
```

### Custom Styling
Dark theme CSS implementation:
```css
QWidget {
    background-color: #333;
    color: #fff;
}
QPushButton {
    background-color: #66a3ff;
    border-radius: 5px;
}
```

## Usage

1. **Select Model**: Choose from available Ollama models in dropdown
2. **Type Message**: Enter your query in the input box
3. **Submit**: Click "Submit Query" or press Enter
4. **View Response**: Watch as the AI response appears in the chat window
5. **Reset**: Use "Reset" button to clear conversation history

## Dependencies

- **PyQt5**: Desktop application framework
- **ollama**: Python client for Ollama API
- **Standard Library**: No additional external dependencies required

## System Requirements

- Python 3.7+
- Ollama installed and running locally
- PyQt5 compatible system (Windows, macOS, Linux)

## Features in Detail

### Message Formatting
- User messages: Ivory colored, right-aligned
- Assistant messages: Dark sea green colored, left-aligned
- HTML formatting support for rich text

### Error Handling
- Graceful model selection
- Robust Ollama API communication
- Clear user feedback through UI elements

## Customization

The application can be easily customized by modifying:
- Color scheme in CSS stylesheet
- Window dimensions in `settings()` method
- Layout proportions in master layout
- Font sizes and styling

---

*Perfect for developers and AI enthusiasts who want a local, private chat interface with their Ollama models.*
