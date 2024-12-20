# Create a zip file containing the basic portfolio website structure
import zipfile
import os

# Define the file structure for the portfolio website
website_structure = {
    "index.html": """
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Samia Islam Portfolio</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <header>
        <h1>Samia Islam</h1>
        <p>Rockville Centre, NY | <a href="mailto:islam.samia305@gmail.com">islam.samia305@gmail.com</a> | <a href="http://www.linkedin.com/in/samia-islam-29mar05/">LinkedIn</a></p>
    </header>
    <main>
        <section id="about">
            <h2>About Me</h2>
            <p>Bachelor of Business Administration in Computer Information Systems at Baruch College, Zicklin School of Business. Expected May 2026.</p>
        </section>
        <section id="projects">
            <h2>Projects</h2>
            <ul>
                <li><strong>RXR Realty Digital Lab Intern</strong> - Assisted in migrating enterprise knowledge repository content.</li>
                <li><strong>Project Destined</strong> - Participated in a $1.2 Million real estate deal.</li>
                <li><strong>Goldman Sachs & TechNYC Intern</strong> - Improved vaccine awareness in NYC communities.</li>
            </ul>
        </section>
        <section id="resume">
            <h2>Resume</h2>
            <p><a href="resume.pdf" target="_blank">Download My Resume</a></p>
        </section>
    </main>
    <footer>
        <p>&copy; 2024 Samia Islam. All rights reserved.</p>
    </footer>
</body>
</html>
""",
    "style.css": """
body {
    font-family: Arial, sans-serif;
    margin: 0;
    padding: 0;
    background-color: #f4f4f9;
    color: #333;
}

header {
    background: #007acc;
    color: #fff;
    padding: 1rem 0;
    text-align: center;
}

header h1 {
    margin: 0;
}

header p {
    margin: 0.5rem 0;
}

main {
    padding: 1rem;
}

section {
    margin-bottom: 2rem;
}

h2 {
    color: #007acc;
}

footer {
    text-align: center;
    padding: 1rem 0;
    background: #333;
    color: #fff;
}
""",
    "resume.pdf": None  # Placeholder for the resume file
}

# Create the zip file
zip_file_path = "/mnt/data/portfolio_website.zip"
with zipfile.ZipFile(zip_file_path, 'w') as zipf:
    for file_name, content in website_structure.items():
        if content is not None:
            zipf.writestr(file_name, content)
        else:
            # Embed the uploaded resume PDF into the zip file
            with open("/mnt/data/Islam, Samia, Resume.pdf", "rb") as resume_file:
                zipf.writestr("resume.pdf", resume_file.read())

zip_file_path
