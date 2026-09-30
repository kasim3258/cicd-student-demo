# CI/CD Implementation using GitHub Actions

## Project
Student Python CI/CD Demonstration

## Objective
This project demonstrates:
- A simple Python application
- Automated testing with pytest
- Continuous Integration using GitHub Actions
- Continuous Deployment using GitHub Actions
- Deployment to GitHub Pages

## Project Structure

```text
cicd-student-demo/
├── README.md
├── student_result.py
├── test_student_result.py
├── index.html
└── .github/
    └── workflows/
        ├── ci.yml
        └── cd.yml
```

## Application

The Python program checks whether a student's mark is a pass or fail.

- Mark >= 40 -> Pass
- Mark < 40 -> Fail

## CI Workflow

Every push to the `main` branch triggers:

1. Checkout source code
2. Set up Python 3.13
3. Install pytest
4. Run automated tests

Expected result:

```text
3 passed
```

## CD Workflow

Every push to `main` also triggers deployment:

1. Checkout source code
2. Configure GitHub Pages
3. Upload the website artifact
4. Deploy the website

## GitHub Pages Setup

After creating the repository:

1. Open **Settings**
2. Open **Pages**
3. Under **Build and deployment**
4. Set **Source** to **GitHub Actions**

The deployed website will normally be available at:

```text
https://USERNAME.github.io/cicd-student-demo/
```

Replace `USERNAME` with your GitHub username.

## Final Pipeline

```text
Code
  |
  v
GitHub
  |
  v
GitHub Actions
  |
  +----> CI: Python + pytest
  |          |
  |          +---- PASS / FAIL
  |
  +----> CD: GitHub Pages
             |
             v
        Live Website
```

## Local Test (Optional)

If Python is installed locally:

```bash
pip install pytest
pytest -v
```

## Important Demonstration

To demonstrate CI failure, temporarily change:

```python
if mark >= 40:
```

to:

```python
if mark >= 50:
```

Then commit and push. The boundary test should fail.

Restore the condition to:

```python
if mark >= 40:
```

and push again. The CI pipeline should pass.
