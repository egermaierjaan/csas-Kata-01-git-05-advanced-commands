# csas-Kata-01-git-05-advanced-commands

## Zadání:
- Forkněte si repozitář na této [adrese](https://github.com/1-PF/csas-Kata-01-git-05-advanced-commands).
- Vyklonujte si repozitář ze svého forku.
- V repozitáři je 10 commitů (C0-C9) a 4 větve (master, bugfix, feature, featurev2). Cílem je dostat počáteční stav historie projektu do výsledného stavu pomocí Git operací: cherry-pick, squash, rebase, revert.
- Vytvořte si lokální větve z remote větví.
- Squashněte `C8` a `C9` z `bugfix` do masteru.
- Smažte `origin/bugfix` a `bugfix`.
- Proveďte cherry-pick `C4` z `featurev2` do `feature`.
- Smažte `origin/featurev2` a `featurev2`.
- Proveďte rebase `feature` na master.
- Mergněte `feature` do masteru.
- Smažte `origin/feature` a `feature`.
- Revertněte `C1` v masteru.
- Pushněte změny do remote repozitáře.

### Počáteční stav repozitáře:
![obrazek](https://user-images.githubusercontent.com/100168224/166677479-7e493e02-6ccc-4400-9c96-c4a6a2e34579.png)

### Výsledný stav repozitáře:
![obrazek](https://user-images.githubusercontent.com/100168224/166683564-f779d5ea-dad9-4997-a4cc-0711bce8e3ad.png)


## Postup:
- Forkneme si daný repozitář a vyklonujeme pomocí zkopírované URL ve forku:
```
    git clone <URL>
```
- Podíváme se, jaké máme remote větve a vytvoříme si z nich lokální větve:
```
    git branch -r
    git branch bugfix origin/bugfix
    git branch feature origin/feature
    git branch featurev2 origin/featurev2
```
- Zkontrolujeme, že jsme přepnuti na větev master a uděláme squash commitů ve větvi `bugfix` do masteru:
```
    git merge --squash bugfix
    git commit -m "Merge bugfix"
```
- Smažeme remote větev `origin/bugfix` a lokální větev `bugfix`:
```
    git push origin --delete bugfix
    git branch -D bugfix
```
- Přepneme se na větev `feature` a provedeme cherry-pick commitu `C4` z větve `featurev2` do větve `feature`:
```
    git cherry-pick <ID C4>
```
- Smažeme remote větev `origin/featurev2` a lokální větev `featurev2`:
```
    git push origin --delete featurev2
    git branch -D featurev2
```
- Zůstaneme na větvi `feature` a rebasneme ji na master:
```
    git rebase master
```
- Přepneme se na master a mergneme větev `feature` do masteru (použijeme fast forward):
```
    git merge feature
```
- Smažeme remote větev `origin/feature` a lokální větev `feature`:
```
    git push origin --delete feature
    git branch -d feature
```
- Revertneme commit `C1`:
```
    git revert <ID C1>
```
- Pushneme změny do remote repozitáře (našeho forku):
```
    git push
```
