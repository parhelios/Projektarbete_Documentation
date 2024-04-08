## Tasks:

### Innan arbetet:

Innan något arbete påbörjas, gå in i Terminal och öppna gitbash.

Ställ dig i projektmappen med: **cd "[sökväg]"** (viktigt med citattecken).

Säkerställ att du står i din egen branch, t.ex. **"Tobias-branch"**

Om du inte står i rätt branch, flytta till den med: **git switch [branchnamn]**

Synkronisera datan från development till din egen branch med: **git merge origin/development**

Sen kan arbetet påbörjas.

### Under arbetet:

Kolla Sprint Taskboard så att ingen annan utvecklare håller på med Tasken du tänkt jobba med.

Assigna dig själv till Tasken i fråga **(!)**.

När en Task påbörjas, flytta den från New till Active.

Utför arbetet.

Namnge Committen till samma nummer och namn som Task:en, t.ex: **"120: Add repositories to UOW"**.

### Efter arbetet:

Gå till Repos > Pull requests i Azure.

Se till att merge ska ske till **development** (överst på skärmen).

Lägg till den/de Tasks som commiten berör.

Skapa ny pull request och tagga två utvecklare.

Skriv sedan i Discordkanalen **"code-review"** och tagga relevanta utvecklare.

Dessa granskar committen och meddelar sedan när code reviewn är avklarad.

Utvecklaren som satte upp pull requesten färdigställer den och kan samtidigt avsluta de Tasks som taggats.

Därefter går det att börja om från början.
