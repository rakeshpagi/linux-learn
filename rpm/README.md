
1. Rebuild rpm 
- rpm --rebuilddb

2. Query rpm
- rpmquery tmux 

3. Backup rpmdb 
- rpmdb --verifydb
- rpmdb --exportdb > rpmbackup.db

4. Reindex 
- rpm --rebuilddb  
- rpmddb --rebuilddb

5. Query Tags : 
- rpm --querytags 

6. Sqlite DB 
 # sqlite3 /var/lib/rpm/rpmdb.sqlite ".schema"
 # .tables 
 # ^D to exit or .exit

 7. Check Database Corruption : 

 sqlite3 ${RPMFILE} "PRAGMA quick_check" 
 sqlite3 ${RPMFILE} "PRAGMA integrity_check"
 sqlite3 ${RPMFILE} "PRAGMA page_count"
 sqlite3 ${RPMFILE} "PRAGMA freelist_count"
 sqlite3 ${RPMFILE} "PRAGMA wal_checkpoint";
 sqlite3 ${RPMFILE} "PRAGMA optimize";


 // recover export 
 sqlite3 ${FILENAME} ".recover" > tmp_db_recover.sql


-- dnf history 
get actual dnf link version : readlink $( command -v dnf ) ; 

-- Installed packages
- dnf list installed 

; history location in dnf3 : /var/lib/dnf/history.sqlite

- dnf history list 
- dnf history info <id> 
- dnf history undo <id> 

-- Unsatisfied repo packages
dnf repoquery --unsatisfied 


--- sync packages with actual distro version 
- dnf distro-sync

--- Check Log files 
/var/log/dnf*.logs


--- Duplicates 
- dnf repoquery --duplicates


--- Find Who Requires Package 
- rpm -q --whatrequires ${PACKAGENAME}

-- Missing Dependencies
- dnf repoquery --unsatisfied 

--- Re-Install or Install again 
- dnf reinstall -y missing-deps 
