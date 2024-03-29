---
{"dg-publish":true,"permalink":"/anteckningar/git/"}
---


# Git är ett versionshanteringsprogram

Ett versionshanteringssystem är program som håller koll på förändringar i koden (eller filer, och eller foldrar). De sparar också en del metadata för att hålla koll på vem som gjort en viss förändring och när förändringen gjordes.

## Config
För att sätta användarnamn och email samt deafult branch för dina commits
```bash
git config --global user.name "John Doe"
git config --global user.email John.Doe@unknown.cc
git config --global init.defaultbranch main
```
## Kommandon
**git init** Skapar en ny git-repository. 
**git add** Lägger till de filer som ska tas med i nästa commit (nästa ögonblicksbild av koden)
**git commit** Skapar en ögonblicksbild (en commit) av alla de filer som lagts till med *git add* tidigare.
**git log --all --graph --decorate** Visar alla commits i en "fin" graf.
**git log --all --graph --decorate --oneline** Visar dem mer kompakt

För att lägga till alias så kör man 
**git config --global alias.graph "log --all --graph --decorate --oneline"** För att till exempel lägga till *git graph* som kör git log --all --graph --decorate --oneline*.

**git push origin master:master** pushar lokala branchen master till origin(remote) branch master
För att slippa ange vilken lokal branch som hör ihop med vilken remote branch kan man skriva:
**git branch --set-upstream-to=origin/master**

Skillnaden mellan att använda **git fetch branchName** och **git pull** är att fetch hämtar branchen, men gör inte en merge. **git pull** == **git fetch; git merge**

**git add -p** Interaktiv staging (man kan till exempel välja att inte lägga till alla console.logs) sen när man gjort commit så kan man köra **git checkout branchNamn** för att få bort alla console.logs. 

**git stash** Sparar undan ändringar och återgår till senaste
**git stash pop** Tar tillbaka ändringar som stashats.

För att uppdatera den lokala listan med remot-branches så kan man skriva:
**git remote update origin --prune**


För att undvika merge commits kan man skriva `git pull --rebase` istället för `git pull`. Man kan även använda `pull.rebase`-inställningen i Git, så att `git pull`-kommandot alltid motsvarar `git pull --rebase`.

## tagg
Man kan lägga till taggar till commits
Man börjar med att commit'a som vanligt och sen gör man ytterligare en commit med:
```
git tag -a v1.0.0 -m "meddelande"
git push origin --tags
```

## Checkout remote branch locally
>The syntax for making git checkout "remote-ready" is rather easy: simply add the "--track" flag and the remote branch's ref.
```
git checkout --track origin/newsletter
```

Kolla upp mer om *git bisect*




```mermaid

gitGraph
   commit
   commit
   branch develop
   checkout develop
   commit
   commit
   checkout main
   merge develop
   commit
   commit
```


















