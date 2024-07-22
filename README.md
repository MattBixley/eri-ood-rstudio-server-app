# eri-ood-rstudio-server
OOD RStudio-server for app for eRI ( beta)

![icon.png](RStudio)

## Notes on `template/script.sh.erb` 

* `--server-data-dir "${TMPDIR}"` redirects output of PIDs from `/var/run/rstudio-rsession` to `${TMPDIR}`.
 
* `--secure-cookie-key-file "${TMPDIR}/rstudio-server/secure-cookie-key"` redirects output of secure-cookie-key from `/tmp/rstudio-server` to `$TMPDIR`. Necessary to avoid conflict where multiple RStudio Server instances are running and generate same hard-coded file.
 
* `--database-config-file "${DBCONF}"` sets the path for a new database config requirement in 1.4.1717.

* Your `$TMPDIR` location needs to be unique for this to work. We use our queueing system to set a unique `$TMPDIR` per job. You can also use export `TMPDIR="$(mktemp -d)"` within ***template/script.sh.erb***.
