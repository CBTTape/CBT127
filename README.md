# CBT127
Converted to GitHub via [cbt2git](https://github.com/wizardofzos/cbt2git)

This is still a work in progress. 
Due to amazing work by Alison Zhang and Jake Choi repos are no longer deleted.

```
//***FILE 127 IS IN IEBUPDTE FORMAT FROM                            *   FILE 127
//*      **FILE 127 REPLACEMENT FROM: CLARK HUNTER                  *   FILE 127
//*      **                           COMPUWARE CORPORATION         *   FILE 127
//*      **                           SOUTHFIELD, MICHIGAN          *   FILE 127
//*      **                           313-540-0900                  *   FILE 127
//*      **                                                         *   FILE 127
//*      **COMMENTS FROM V232 VERSION OF CBT TAPE WITH MY UPDATES:  *   FILE 127
//*                                                                 *   FILE 127
//*      **FILE 127 IS IN IEBUPDTE FORMAT FROM CHRYSLER AND         *   FILE 127
//*                 CONTAINS :                                      *   FILE 127
//*                                                                 *   FILE 127
//*                   1. DASD SEEK ANALYSIS PROGRAM.  THIS          *   FILE 127
//*                   PROGRAM READS IN GTF DATA AND SUMMARIZED      *   FILE 127
//*                   DASD SIO/IO RECORDS.   THIS PROGRAM IS IN     *   FILE 127
//*                   IEBUPDTE SYSIN FORMAT AND REQUIRES THE        *   FILE 127
//*                   VTOC MACROS THAT ARE CONTAINED IN FILE 112    *   FILE 127
//*                                                                 *   FILE 127
//*                        BY DEVICE CALCULATE NUMBER SIO CC = 0-3  *   FILE 127
//*                         TOTAL CYLINDERS SEEKED                  *   FILE 127
//*                         AVERAGE CYLINDERS SEEKED                *   FILE 127
//*                         AVERAGE IO TIME                         *   FILE 127
//*                         MAXIMUM IO TIME OVER RUN                *   FILE 127
//*                   **10JAN85 FIXED FOR XA, MISC PROGRAM BUGS     *   FILE 127
//*                   FIXED                                         *   FILE 127
//*                   2. A SAMPLE IEECVXIT PROGRAM                  *   FILE 127
//*                      **10JAN85 REMOVED DUE TO LACK OF           *   FILE 127
//*                      INTEREST                                   *   FILE 127
//*                   3. SUBROUTINE TO PRODUCE A NICE PRINTABLE     *   FILE 127
//*                      HEADER DATE                                *   FILE 127
//*                   4  TSO CP FOR STANDALONE DIDOCS (DCMS)        *   FILE 127
//*                      AUTO UPDATE                                *   FILE 127
//*                      **10JAN85 REMOVED DUE TO LACK OF           *   FILE 127
//*                      INTEREST                                   *   FILE 127
//*                   5  PROGRAM TO LOCATE, ALLOC, DUMP THE         *   FILE 127
//*                      MVS/SE2 SMF D.S.                           *   FILE 127
//*                      **10JAN85 REMOVED DUE TO LACK OF           *   FILE 127
//*                      INTEREST                                   *   FILE 127
//*                   6  COMPANY USER MODS IN SMP4 FORMAT           *   FILE 127
//*                      **10JAN85 REMOVED DUE TO LACK OF           *   FILE 127
//*                      INTEREST                                   *   FILE 127
//*                   7  SEE NEW STUFF BELOW:                       *   FILE 127
//*                                                                 *   FILE 127
//*      PDS CONTAINS:                                              *   FILE 127
//*                                                                 *   FILE 127
//*       MACROS:  - @ENT @RET @STCK CLEAR CONV ENTER ENTERX        *   FILE 127
//*                  LEAVE MSG PDEDSNAM REGS SYSGET SYSPUT          *   FILE 127
//*                  TSCVDATE VTCALL VTEXCP VTFMT VTOC VTOCMSG      *   FILE 127
//*                  VTOCOM VTOCPARS                                *   FILE 127
//*                                                                 *   FILE 127
//*      $DOC      - DOCUMENTATION FILE                             *   FILE 127
//*                                                                 *   FILE 127
//*      JCL       - SAMPLE JCL USED TO DUMP PDS.                   *   FILE 127
//*                  AND TRY TO CHECK THAT I DIDN'T FORGET ANY      *   FILE 127
//*                  MACROS                                         *   FILE 127
//*                                                                 *   FILE 127
//*      TSGTFMAP  - PGM TO REDUCE GTF SIO/IO TRACE RECORDS.        *   FILE 127
//*                  SEE COMMENTS AT BEGINNING OF PROGRAM FOR       *   FILE 127
//*                  HOW TO RUN.  USES SUBR: TSCVDATE, VTOCEXCP     *   FILE 127
//*                  NOW SUPPORTS XA FORMAT OF GTF RECORDS          *   FILE 127
//*                                                                 *   FILE 127
//*      TSCALL    - TSOCP TO CALL PROGRAMS FROM                    *   FILE 127
//*                  "TASKLIB"/STEPLIB/ LNKLST/LPALIB. IDEA IS      *   FILE 127
//*                  TO NOT USE TSO "CALL" WITH HARDCODED           *   FILE 127
//*                  LOADLIBS THAT HAVE TO BE OPENED.               *   FILE 127
//*                  (FIXED BY "UPDATER")                           *   FILE 127
//*                                                                 *   FILE 127
//*      TSCVDAT   - SUBROUTINE TO MAKE NICE PRINTABLE DATE FOR     *   FILE 127
//*                  HEADINGS.                                      *   FILE 127
//*                                                                 *   FILE 127
//*      TSDYNLXA  - PGM XA DYNALIST TO LIST ESOTERIC UNIT NAMES    *   FILE 127
//*                  (NOTE: USES ESTAES TO EXECUTE                  *   FILE 127
//*                  UNAUTHORIZED!!)                                *   FILE 127
//*                                                                 *   FILE 127
//*      TSENQSP3  - TSOCP (AKA $DENQ) SCAN FOR GENERIC SYSDSN      *   FILE 127
//*                  ENQS, LOOK FOR ENQ LOCKOUTS, LOOK FOR          *   FILE 127
//*                  RESERVE ENQS.  (NOTE USES GQSCAN)              *   FILE 127
//*                                                                 *   FILE 127
//*      TSSPACE   - TSO CP TO LIST SPACE, IXVTOC STATUS,           *   FILE 127
//*                  PATH(CHAN/CHPID), LSPACE(FREE) SPACE,          *   FILE 127
//*                  #USERS, DEVTYPE, AND ADDRESS FOR DASD. CAN     *   FILE 127
//*                  ASK FOR ALL DASD WITH LESS THAN N PATHS TO     *   FILE 127
//*                  SEE IF ANY DASD PATHS ARE MISSING.             *   FILE 127
//*                                                                 *   FILE 127
//*      TSSYSTEM  - TSO CP TO SHOW RELEASE, CPUTYPE, CPUSERIAL#,   *   FILE 127
//*                  SYSRES, REAL STORAGE, HOW LONG SINCE           *   FILE 127
//*                  (IPL/SET IPS).                                 *   FILE 127
//*                                                                 *   FILE 127
//*      VTOC      - TSO CP VTOC - FIXED FOR SP3/XA UCBSCAN,        *   FILE 127
//*                  HANDLES 123 EXTENTS WITH DF/EF.  (NOTE I       *   FILE 127
//*                  USE ENTRY VTOCEXCP FOR VTOC READING IN         *   FILE 127
//*                  TSGTFMAP)                                      *   FILE 127
//*                                                                 *   FILE 127
//*      ** EVERYTHING HAS BEEN USED ON SP3 AND XA2.1.1.            *   FILE 127
//*                                                                 *   FILE 127
```
