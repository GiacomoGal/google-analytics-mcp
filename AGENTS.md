# Guida agente — fork GiacomoGal/google-analytics-mcp

Lettura umana e lettura agente di questo file descrivono lo stesso checkout. Il README umano resta la fonte delle affermazioni sul server. Questo file registra rango, destinatario, condizioni, trigger e host ref dei contratti già scritti, e aggiunge solo i limiti del fork. Non sostituisce README, `CONTRIBUTING.md`, `LICENSE`, `CODEOWNERS` né i template di issue.

Data della lettura: 2026-11-07. Base del checkout: `c3a6cad432881d911c26429a40dc9efd17a0ca5c` (`main` del fork al momento del branch).

## Stato che questa guida lascia sconosciuto

- Uso attuale di questo fork: unknown.
- Account Google collegato a questo fork: unknown.
- Installazione di questo fork: unknown.
- Campo descrizione del repository, letto dall'API pubblica GitHub il 2026-11-07: vuoto. L'inventario di incarico segna la descrizione come assente. Lo scopo non viene ricostruito oltre la frase del README citata sotto.
- Inventario di incarico, lotto 6 sezione 3, mandato documentale t127u: `identity_proven=false`, `unknowncurrentuse=true`, `nextdocscope=unresolved`, `identity_evidence` vuoto, proposte ed execution receipt vuoti, etichetta UNMAPPED. Quel ref inventario `main` non prova allineamento a un host.
- L'API pubblica, nello stesso giorno, mostra un fatto più stretto: il repository è un fork pubblico, default branch `main`, archived false, parent `googleanalytics/google-analytics-mcp`. L'origine git configurata in questo workspace punta a `github.com/GiacomoGal/google-analytics-mcp`. Questo prova l'identità configurata del checkout. Non prova canonicità operativa, sync, uso, installazione o un account.
- Conflitto di fonti, lasciato aperto: l'inventario dichiara nessuna associazione per nome a servizi o repository omonimi; l'API dichiara il parent upstream omonimo. Nessuna delle due fonti è una decisione di lifecycle. `executed` non risulta da questo lavoro.
- Questa guida non è un PASS documentale. Una review indipendente resta necessaria.

## Frase di scopo presente nel README

Il README di questo checkout, subito sotto la nota di fork, afferma che il repository contiene il sorgente per eseguire un server MCP locale che interagisce con le API di Google Analytics. Questa guida cita quella frase come testo del checkout. Non la estende a un deployment, a un account, a una property o a una versione PyPI verificata in esecuzione.

## Contratti già nel tree

Nessun file di istruzioni agente esisteva prima di questa guida: niente `AGENTS.md` precedente, niente `CLAUDE.md`, niente regole `.cursor`. Nessun file di memoria è nel tree. Questa guida non crea una memoria e non sincronizza memorie, store o backup.

Gli host ref sono nominati e, dove indicato, controllati solo come link statici. I path locali, la console Google Cloud, il canale Discord e ogni materiale di credenziali non sono stati aperti.

### README.md — rango root, destinatario umano

| Blocco | Ancora nel README preservato | Destinatario | Condizioni scritte | Trigger scritto | Host ref |
| --- | --- | --- | --- | --- | --- |
| Scopo e canale | paragrafo iniziale e Discord | lettori del repository | il titolo qualifica il server come experimental | lettura del README | `https://modelcontextprotocol.io`, `https://support.google.com/analytics`, URL Discord del README |
| Strumenti | sezione Tools | lettori e, in via indiretta, un LLM che usi il server | uso delle Admin API e Data API, secondo il testo | uso dei tool nominati | guide `developers.google.com` Admin v1 e Data v1; concetto MCP tools |
| Informazioni account e property | tre voci | lo stesso | il testo parla di account e property dell'utente, senza nominarne uno | chiamata dei nomi `get_account_summaries`, `get_property_details`, `list_google_ads_links` | nessuno oltre le guide API |
| Report core | due voci | lo stesso | Data API, property specifica per dimensioni e metriche custom | `run_report`, `get_custom_dimensions_and_metrics` | nessuno oltre le guide API |
| Report realtime | una voce | lo stesso | Data API | `run_realtime_report` | nessuno oltre le guide API |
| Setup | sezioni Python, API, credenziali, Gemini | chi segue il testo di setup | credenziali ADC di un utente con accesso agli account o alle property; scope read-only citato nel testo | passi numerati e comandi `gcloud` di esempio | pipx, pagine di abilitazione API, console Cloud, ADC, OAuth client, Gemini CLI, marketplace, `~/.gemini/settings.json`, segnaposto di path e project id |
| Prova | sezione Try it out | chi lancia Gemini e incolla i prompt | il testo assume `analytics-mcp` visibile in `/mcp` | `/mcp` e cinque prompt di esempio | nessuno nuovo |
| Contributi | sezione finale | contributori | rinvio a `CONTRIBUTING.md` | apertura della guida | `CONTRIBUTING.md` |

Il README nomina questi tool e non ne documenta i parametri: `get_account_summaries`, `get_property_details`, `list_google_ads_links`, `run_report`, `get_custom_dimensions_and_metrics`, `run_realtime_report`. Il subject del commit `9cb51d5` in questa history dice `feat: add list_property_annotations tool (#75)`. Quel subject non è una firma di tool: l'implementazione non è stata aperta e il nome non compare nell'elenco del README. Non entra nel contratto strumenti.

Nel testo preservato convivono due nomi di attributo: la prosa indica `GOOGLE_CLOUD_PROJECT` e l'esempio JSON usa la chiave `GOOGLE_PROJECT_ID`. Sono entrambi segnaposto (`YOUR_PROJECT_ID`). Questa guida non sceglie quale chiave sia operativa, perché env e codice non sono stati letti, e non modifica l'esempio upstream.

### CONTRIBUTING.md — rango root, destinatario contributori

| Blocco | Righe | Destinatario | Condizioni scritte | Trigger scritto | Host ref |
| --- | --- | --- | --- | --- | --- |
| CLA | 6–16 | chi invia patch, o il datore | accordo CLA; il contributore conserva il copyright e dà permesso d'uso e redistribuzione | invio di un contributo | `https://cla.developers.google.com/` |
| Review | 18–23 | chi invia patch, inclusi i membri del progetto | ogni submission richiede review | pull request GitHub | `https://help.github.com/articles/about-pull-requests/` |
| Comunità | 25–28 | partecipanti | linee guida comunitarie Google | partecipazione | `https://opensource.google.com/conduct/` |
| Stile | 30–45 | contributori di codice | PEP 8 e larghezza 80; `black` raccomandato | `nox -s format` dopo l'installazione descritta | PEP 8, repository Black |
| Test | 47–56 | contributori | test in `tests/` | `nox -s tests*` | nessuno esterno |
| Prova Gemini locale | 58–72 | chi prova i prompt in locale | `command` in `~/.gemini/settings.json` puntato a `PATH_TO_REPO/.venv/bin/analytics-mcp` | comando `gemini` con `--debug`, secondo il testo | path locale del repo e file settings |
| Prova da GitHub | 74–103 | chi prova un branch via pipx | `--no-cache` e uno spec git | esempio di branch `awesome-feature-42` | `git+https://github.com/googleanalytics/google-analytics-mcp.git@awesome-feature-42` |

L'URL git di esempio punta all'upstream `googleanalytics/google-analytics-mcp`, non a questo fork. Resta com'è. Questa guida non lo reindirizza.

I comandi `pip`, `nox`, `gemini` e `pipx` in quel file sono istruzioni upstream per i contributori. Questa guida non li esegue e non li converte in un permesso di esecuzione dentro il mandato documentale.

### LICENSE — rango root, destinatario "You"

L'intestazione del file `LICENSE` identifica Apache License, Version 2.0, January 2004, con URL `http://www.apache.org/licenses/`. Il testo integrale non è stato ricopiato qui. Il contratto di licenza resta quello del file. La pagina `https://www.apache.org/licenses/LICENSE-2.0` risponde 200 a un HEAD ed è solo un controllo di raggiungibilità.

### CODEOWNERS — rango root, destinatario citato nel file

L'intero file è la riga `@googleanalytics/google-analytics`. Nel testo non c'è un pattern di path. Questa guida non interpreta quella riga come assegnazione provata di ownership su un percorso e non ha interrogato l'API code owners.

### Template di issue — rango nested, `.github/ISSUE_TEMPLATE/`

| File | Destinatario | Condizioni scritte | Trigger | Host ref |
| --- | --- | --- | --- | --- |
| `bug_report.md` | chi segnala un bug del server MCP | i temi delle API Google Analytics, se non specifici di questa libreria, vanno alle risorse di supporto; controllare le issue esistenti | apertura issue; label scritte `bug`, `triage`; assignees vuoti | `https://developers.google.com/analytics/support` |
| `feature_request.md` | chi propone un'idea per questo progetto | stesso rinvio per richieste che riguardano le API e non questa libreria | apertura issue; label `enhancement`, `triage` | lo stesso URL |
| `usage_question.md` | chi fa una domanda d'uso specifica di questo progetto | stesso rinvio per domande sulle API non specifiche di questa libreria | apertura issue; label `question`, `triage` | lo stesso URL |

I tre template chiamano il progetto anche "library". Questa guida non corregge quella parola.

### Istruzioni nested assenti

Sotto `analytics_mcp/`, `tests/` e `.github/` non ci sono altre guide Markdown di agente. `.github/workflows/presubmit.yaml`, `.github/renovate.json5`, `pyproject.toml`, `noxfile.py` e `.gitignore` sono config o script: non sono stati letti e non sono stati modificati. Non entrano come contratti di comportamento.

## Host ref

| Ref | Dove compare | Azione su questo incarico |
| --- | --- | --- |
| `https://modelcontextprotocol.io` | README | HEAD 308 verso `/docs/2026-07-28/getting-started/intro`, poi HEAD 200. Corpo non archiviato. |
| `https://modelcontextprotocol.io/docs/concepts/tools` | README | HEAD 308 verso `/specification/2026-07-28/server/tools`, poi HEAD 200. Il path citato non è la URL finale. Il link nel README non è stato riscritto. |
| `https://pypi.org/project/analytics-mcp/` | badge README | HEAD 200. Non prova che il checkout coincida con l'artefatto pubblicato. |
| `https://www.python.org/downloads/` | badge README | HEAD 200. |
| `https://github.com/googleanalytics/google-analytics-mcp` | badge e URL di esempio in CONTRIBUTING | HEAD 200 sulla home del repository upstream. |
| `https://pipx.pypa.io/stable/#install-pipx` | README | HEAD 200 su `https://pipx.pypa.io/stable/`. Il frammento `#install-pipx` non è stato verificato nel corpo. |
| Guide Admin API e Data API su `developers.google.com` | README | HEAD 200 per entrambe le URL scritte nel README. |
| `https://developers.google.com/analytics/support` | template di issue | HEAD 200. |
| `https://support.google.com/analytics` | README | HEAD 404, GET 200. Il corpo non è stato letto. |
| `https://support.google.com/googleapi/answer/6158841` | README | HEAD 404, GET 200. Corpo non letto. |
| `https://support.google.com/googleapi/answer/7014113` | README | HEAD 404, GET 200. Corpo non letto. |
| `https://cloud.google.com/docs/authentication/provide-credentials-adc` | README | HEAD 301 verso `https://docs.cloud.google.com/docs/authentication/provide-credentials-adc`, poi HEAD 200. |
| `https://support.google.com/cloud/answer/15549257` | README | HEAD 404, GET 200. Corpo non letto. |
| `https://console.cloud.google.com/apis/library/analyticsadmin.googleapis.com` | README | Non aperto. È una console e può legare la richiesta a un progetto o a un account. |
| `https://console.cloud.google.com/apis/library/analyticsdata.googleapis.com` | README | Non aperto, per lo stesso motivo. |
| `https://discord.com/channels/971845904002871346/1398002598665257060` | README | Non aperto. È un canale, non una pagina documentale statica. |
| `https://www.youtube.com/watch?v=PT4wGPxWiRQ` | badge README | GET 200 sulla pagina. Il video non è stato trascritto e non è una fonte di policy. |
| `https://youtu.be/nS8HLdwmVlY` e la watch URL del tutorial | README | GET 303 da `youtu.be` verso la watch URL con `feature=youtu.be`. Il secondo hop non è stato seguito. Il video non è stato trascritto. |
| `https://cla.developers.google.com/` | CONTRIBUTING | HEAD 307 verso `/about`, poi HEAD 200. |
| `https://opensource.google.com/conduct/` | CONTRIBUTING | HEAD 301 verso `https://opensource.google/conduct/`, poi HEAD 200. |
| `https://help.github.com/articles/about-pull-requests/` | CONTRIBUTING | HEAD 301 verso `https://docs.github.com/articles/about-pull-requests`, poi HEAD 302 verso `/en/pull-requests/reference/pull-requests`. Il secondo hop non è stato aperto. |
| `https://www.python.org/dev/peps/pep-0008/` | CONTRIBUTING | HEAD 302 verso `https://peps.python.org/pep-0008/`, poi HEAD 200. |
| `https://github.com/psf/black` | CONTRIBUTING | HEAD 200. |
| `https://github.com/google-gemini/gemini-cli/blob/main/docs/cli/index.md` | README | GET 404. Nessuna URL sostitutiva è stata cercata. Il link upstream non è stato riscritto. |
| Marketplace `Google.geminicodeassist` | README | HEAD 404, GET 200. Corpo non letto. |
| `https://www.apache.org/licenses/` e `LICENSE-2.0` | intestazione LICENSE e controllo | HEAD 200. |
| Badge `img.shields.io` | README | Non richiesti. Un fetch del badge può interrogare servizi terzi. |
| `~/.gemini/settings.json` | README e CONTRIBUTING | Non aperto. |
| `YOUR_CLIENT_JSON_FILE`, `PATH_TO_CREDENTIALS_JSON`, `SERVICE_ACCOUNT_EMAIL`, `YOUR_PROJECT_ID`, `PATH_TO_REPO` | README e CONTRIBUTING | Segnaposto del testo. Nessun file, env, token, client OAuth o project id reale è stato letto. |
| Scope `https://www.googleapis.com/auth/analytics.readonly` | README | Citato come stringa del README. Non è stato usato come autorizzazione. |
| Comandi `gcloud auth application-default login` di esempio | README | Restano esempi del README. Questa guida non li esegue e non autorizzano un login. |

Un controllo HTTP registra solo lo status e, se presente, il primo `Location`. Non certifica il contenuto della pagina, non aggiorna i link e non autorizza l'uso dell'API, di un account o di un video.

## Esempi del README: query, prompt e claim

Queste stringhe sono citazioni del README. Sono esempi. Non costituiscono una policy di questo fork e non costituiscono un'autorizzazione su un account Google.

- `what can the analytics-mcp server do?`
- `Give me details about my Google Analytics property with 'xyz' in the name`
- `what are the most popular events in my Google Analytics property in the last 180 days?`
- `were most of my users in the last 6 months logged in?`
- `what are the custom dimensions and custom metrics in my property?`

`xyz` è il segnaposto scritto nel README. Non è un property id letto da un account. I claim dentro questi prompt ("my property", "my users") sono parole dell'esempio. Non attestano dati Analytics.

Anche i comandi `gcloud`, il JSON `mcpServers` e lo spec `pipx` sono esempi o istruzioni upstream citate. Descriverli in questa guida non autorizza esecuzione, login, credenziali o dati reali.

## Upstream presente e non importato

Il confronto pubblico three-dot `googleanalytics:main...main` del fork, letto il 2026-11-07, riporta `status=behind`, `ahead_by=0`, `behind_by=57`. Lo SHA upstream osservato è `8ce1c8fd0d23375ca02787b3c31b21fccc4238f3`. Il tree pubblico di quello SHA elenca path assenti da questo checkout, tra cui `TROUBLESHOOTING.md`, `Dockerfile`, `.kokoro/`, `skills-lock.json`, `analytics_mcp/oauth.py`, altri moduli sotto `analytics_mcp/tools/`, `examples/multi_tenant_adk_agent/` e test aggiuntivi. Il contenuto di quei path non è stato aperto. Non entra in questa guida e non è stato copiato nel fork.

Questo incarico non sincronizza il fork con upstream, non apre una pull request upstream, non fa merge, rebase, force push, deploy o archive.

## Matrice fonte → testo nuovo

| ID | Fonte | Elemento | Destinazione nuova | Motivazione |
| --- | --- | --- | --- | --- |
| M1 | README, frase di scopo | scopo del sorgente come server MCP locale verso le API Analytics | citazione nella sezione scopo; corpo README invariato | è l'unica frase di scopo nel checkout; l'inventario non ha una descrizione da cui derivarne un'altra |
| M2 | README, elenco Tools | sei nomi di tool, senza parametri | tabella contratti README | il README li nomina; i parametri non sono in quella sezione e il codice non è stato letto |
| M3 | git log del checkout, subject `9cb51d5` | nome `list_property_annotations` | frase di esclusione dal contratto tool | un subject non è una firma; promuoverlo inventerebbe un contratto |
| M4 | README, prosa `GOOGLE_CLOUD_PROJECT` e JSON `GOOGLE_PROJECT_ID` | tensione testuale | nota nella sezione README, esempio non corretto | correggere il README upstream supererebbe l'adattamento minimo e richiederebbe env o codice |
| M5 | README, prompt e comandi di esempio | cinque prompt, `gcloud`, JSON Gemini | sezione esempi, con etichetta di non-policy | il mandato chiede di separare esempi e claim da autorizzazioni e da risultati certificati |
| M6 | README, link | host ref | tabella host ref | i ref vanno ricostruiti; console, Discord e path locali restano non aperti |
| M7 | CONTRIBUTING.md | CLA, review, condotta, stile, test, prove Gemini e pipx | tabella contratti contributi | sono obblighi upstream verso i contributori; restringerli sarebbe una restrizione arbitraria |
| M8 | CONTRIBUTING.md, spec git | URL `googleanalytics/google-analytics-mcp` | lasciato nel file; richiamato qui | l'adattamento minimo non reindirizza l'esempio upstream verso il fork |
| M9 | `LICENSE`, intestazione | Apache 2.0 | rinvio al file, senza copia | il contratto legale resta il file; copiarlo non aggiunge un obbligo |
| M10 | `CODEOWNERS` | una riga senza pattern | descrizione letterale | inventare un pattern di ownership andrebbe oltre il file |
| M11 | `.github/ISSUE_TEMPLATE/*.md` | tre moduli, label, rinvio al supporto API | tabella nested | sono le uniche istruzioni nested applicabili e lette |
| M12 | albero del checkout | assenza di guida agente e di file di memoria | questo `AGENTS.md`; divieto di memory sync | il mandato chiede una guida agente coerente col README e vieta il sync di memoria |
| M13 | brief locale lotto 6 sezione 3, non presente nel tree | unknown, UNMAPPED, unresolved, evidenze vuote | sezione stato | è la fonte dell'incarico; non viene promossa a policy del progetto upstream |
| M14 | API GitHub fork e parent, 2026-11-07 | fork, parent, descrizione vuota, behind 57 | sezione stato e sezione upstream | distingue identità configurata e parent pubblico da uso, account e sync |
| M15 | tree upstream elencato e non letto | path assenti nel checkout | elenco di non-import | aprire quei file, in particolare oauth, lock e kokoro, uscirebbe dal mandato |
| M16 | controlli HTTP della tabella host ref | status e `Location` | stessa tabella | verifica documentale richiesta; il corpo delle pagine non diventa fonte di nuove regole |
| M17 | nota aggiunta in cima al README | rinvio a questo file e limiti unknown | README, solo il blockquote | il lettore umano del README deve vedere gli stessi limiti dell'agente senza riscrivere il corpo upstream |

## Coerenza tra README umano e questa guida

- Il README continua a dire che cosa il testo upstream afferma del server, dei tool, del setup e dei prompt.
- Questa guida dice come trattare quelle frasi nel fork: citazione, non prova di uso, non autorizzazione, non risultato certificato.
- I contratti di CLA, review, condotta, licenza e template restano rivolti ai destinatari scritti nei file originali.
- Il limite "non eseguire i comandi durante questo incarico documentale" vincola l'agente che lavora su questo mandato. Non cancella le istruzioni di contributo scritte per i contributori upstream.
- Nessuna roadmap, nessun commento e nessun prompt di esempio è stato promosso a policy.

## Ricevuta delle fonti e dei limiti

File letti per intero o per intestazione: `README.md`, `CONTRIBUTING.md`, `CODEOWNERS`, i tre template in `.github/ISSUE_TEMPLATE/`, le prime righe di `LICENSE` fino all'identificazione Apache 2.0. Il brief di incarico, lotto 6 sezione 3, è stato letto come allegato esterno.

Non letti, e non modificati: codice Python, test, `pyproject.toml`, `noxfile.py`, workflow, Renovate, `.gitignore`, Dockerfile assente in questo checkout, file env, token, OAuth, client Analytics, property id, export, backup, memorie, store privati, `skills-lock.json` upstream, path sotto `.kokoro/`, `analytics_mcp/oauth.py`.

Nessun install, import, build, test applicativo, server MCP, login, Discovery, provider, SSH, sync, invio, merge, deploy o archive è stato eseguito. I controlli di link sono quelli della tabella host ref.

La ricevuta di commit, con SHA base, SHA head e diff, sta nel messaggio della pull request del fork. Questa guida, da sola, non chiude la review.
