---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

layout: home
---


<button id="toggle-theme" class="toggle-theme" title="Theme">Toggle Theme</button>


<style>
.toggle-theme {
    width: 74px;
    height: 41px;
    margin-top: 20px;
    margin-bottom: 20px;
    cursor: pointer;
}

body.light-mode {
    background-color: white;
    color: black;
}

body.dark-mode {
    background-color: black;
    color: white;
}

body.light-mode h1 {
    color: black;
}

body.dark-mode h1 {
    color: white;
}
</style>


<script>
document.addEventListener("DOMContentLoaded", function() {
    const body = document.body;
    const toggleButton = document.getElementById('toggle-theme');

   
    const savedTheme = localStorage.getItem('theme');
    if (savedTheme) {
        body.classList.add(savedTheme);
    } else {
        body.classList.add('light-mode'); 
    }

  

    toggleButton.addEventListener('click', function() {
        if (body.classList.contains('dark-mode')) {
            body.classList.remove('dark-mode');
            body.classList.add('light-mode');
            localStorage.setItem('theme', 'light-mode');
            console.log("Switched to light mode");
        } else {
            body.classList.remove('light-mode');
            body.classList.add('dark-mode');
            localStorage.setItem('theme', 'dark-mode');
            console.log("Switched to dark mode");
        }
      
    });

   
});
</script>
