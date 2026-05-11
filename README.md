# CI_MLops
this project is to learnings of end to end implemetation of continous Integration

#############Learnings#######################################
1. Continuous Integration Benefits
Automation: Tests run automatically on every push/PR without manual intervention
Early Detection: Bugs caught before code reaches main branch
Consistency: Same testing environment across all developers

1. Application Layer (app.py)
Framework: Built with Streamlit (Python web framework for data apps)
Functionality: A "Power Calculator" that takes user input and computes:
Square (n²)
Cube (n³)
Fifth Power (n⁵)
Key Learning: Streamlit simplifies interactive web app creation without complex backend setup
2. Testing Layer (_test.py)
Framework: Uses pytest for unit testing
Test Coverage: 4 test functions covering:
✅ test_square() - validates square calculations
✅ test_cube() - validates cube calculations
✅ test_fifth_power() - validates fifth power calculations
✅ test_invalid_input() - exception handling (TypeError for invalid types)
Key Learning: Tests are modular, specific, and include both positive and negative cases
3. CI/CD Pipeline (ci.yaml)
Automated workflow triggered on push and pull requests to the main branch:

Workflow Steps:

Code Checkout - Retrieves repository code
Python Setup - Configures Python 3.9 environment
Dependency Installation - Installs pytest and streamlit
Automated Tests - Runs pytest on _test.py


graph LR
    A["Developer Push/PR"] --> B["GitHub Detects Event"]
    B --> C["Workflow Triggered"]
    C --> D["Ubuntu Runner Starts"]
    D --> E["Python 3.9 Setup"]
    E --> F["Install Dependencies"]
    F --> G["Run pytest"]
    G --> H{Tests Pass?}
    H -->|Yes| I["✅ Build Success"]
    H -->|No| J["❌ Build Fails - Notify Developer"]
