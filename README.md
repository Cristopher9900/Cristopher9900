## Olá! 👋

- 🔭 Atualmente atuo com desenvolvimento Front-end e Back-end, utilizando tecnologias como HTML, CSS, JavaScript, Python e MySQL.
- 🌱 Atualmente estou aprendendo mais sobre integração com banco de dados, ferramentas em nuvem e aprimorando meus conhecimentos em Java, Node.js e SQL Server para desenvolvimento full stack.
- 👯 Estou em busca de colaborar em projetos de desenvolvimento web, especialmente com foco em front-end, back-end e integração com banco de dados.
- 💬 Pode me perguntar sobre desenvolvimento web, Java, Node.js, integração com banco de dados, rotinas administrativas e Excel avançado.
- ⚡ Curiosidade: adoro aprender coisas novas por conta própria e sempre busco formas de automatizar tarefas para facilitar o dia a dia!
<div>
  <a href="https://beacons.ai/Cristopher9900">
   <img height ="180em" src ="https://github-readme-stats.vercel.app/api?username=Cristopher9900&show_icons=true&theme=dracula&include_all_comits=true&count_private=true">   <img height ="180em" src ="https://github-readme-stats.vercel.app/api/top-langs/?username=Cristopher9900&layout=compact&langs_count=16&theme=dracula"/>
</div>
 <div style="display: inline-block; text-align: center">
  <div>
    <img style="margin: 5px;" alt="Java" height="30" width="40" src="https://raw.githubusercontent.com/devicons/devicon/master/icons/java/java-original.svg">
    <img style="margin: 5px;" alt="Python" height="30" width="40" src="https://raw.githubusercontent.com/devicons/devicon/master/icons/python/python-original.svg">
    <img style="margin: 5px;" alt="HTML" height="30" width="40" src="https://raw.githubusercontent.com/devicons/devicon/master/icons/html5/html5-original.svg">
    <img style="margin: 5px;" alt="CSS" height="30" width="40" src="https://raw.githubusercontent.com/devicons/devicon/master/icons/css3/css3-original.svg">
    <img style="margin: 5px;" alt="JavaScript" height="30" width="40" src="https://raw.githubusercontent.com/devicons/devicon/master/icons/javascript/javascript-plain.svg">
    <img style="margin: 5px;" alt="C#" height="30" width="40" src="https://raw.githubusercontent.com/devicons/devicon/master/icons/csharp/csharp-original.svg">
    <img style="margin: 5px;" alt="MySQL" height="30" width="40" src="https://raw.githubusercontent.com/devicons/devicon/master/icons/mysql/mysql-original.svg">
    <img style="margin: 5px;" alt="Node.js" height="30" width="40" src="https://raw.githubusercontent.com/devicons/devicon/master/icons/nodejs/nodejs-original.svg">
    <img style="margin: 5px;" alt="Git" height="30" width="40" src="https://raw.githubusercontent.com/devicons/devicon/master/icons/git/git-original.svg">
    <img style="margin: 5px;" alt="VSCode" height="30" width="40" src="https://raw.githubusercontent.com/devicons/devicon/master/icons/vscode/vscode-original.svg">
    <img style="margin: 5px;" alt="Windows" height="30" width="40" src="https://raw.githubusercontent.com/devicons/devicon/master/icons/windows8/windows8-original.svg">
    <br><br/>
  </div>
  <div style="margin-top: 15px;">
    <img alt="Baby-Yoda" height="60" src="https://media.giphy.com/media/RbDKaczqWovIugyJmW/giphy.gif">
  </div>
</div>

   
<div>
  <a href="mailto:cris.pichelli123@gmail.com" target="_blank">
    <img src="https://img.shields.io/badge/-Gmail-%23333?style=for-the-badge&logo=gmail&logoColor=white">
  </a>
  <a href="https://www.linkedin.com/in/cristopher-pichelli-27663a294" target="_blank">
    <img src="https://img.shields.io/badge/-LinkedIn-%230077B5?style=for-the-badge&logo=linkedin&logoColor=white">
  </a>
</div>
name: generate animation

on:
  # run automatically every 24 hours
  schedule:
    - cron: "0 */24 * * *" 
  
  # allows to manually run the job at any time
  workflow_dispatch:
  
  # run on every push on the master branch
  push:
    branches:
    - master
    



jobs:
  generate:
    permissions: 
      contents: write
    runs-on: ubuntu-latest
    timeout-minutes: 5
    
    steps:
      # generates a snake game from a github user (<github_user_name>) contributions graph, output a svg animation at <svg_out_path>
      - name: generate github-contribution-grid-snake.svg
        uses: Platane/snk/svg-only@v3
        with:
          github_user_name: ${{ github.repository_owner }}
          outputs: |
            dist/github-contribution-grid-snake.svg
            dist/github-contribution-grid-snake-dark.svg?palette=github-dark
          
          
      # push the content of <build_dir> to a branch
      # the content will be available at https://raw.githubusercontent.com/<github_user>/<repository>/<target_branch>/<file> , or as github page
      - name: push github-contribution-grid-snake.svg to the output branch
        uses: crazy-max/ghaction-github-pages@v3.1.0
        with:
          target_branch: output
          build_dir: dist
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}




