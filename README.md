# utl-sas-format-that-right-justify-sas-character-variable-values
SAS format that right justifiles sas character variable values
    %let pgm=utl-sas-format-that-right-justifies-sas-character-variable-values;

    %stop_submission;

    SAS format that right justifies sas character variable values

    INPUT
    =====

    data have;
      input
        name$
        sex$ age;
    cards4;
    Alfred  M 14
    Al      M 13
    Barbara F 13
    Joe     F 14
    Henry   M 14
    James   M 12
    ;;;;
    run;quit;

    OUTPUT
    ======

    proc print data=have;
    format name $charRight.;
    run;quit;

     NAME    SEX AGE

     Alfred   M   14
         Al   M   13
    Barbara   F   13
        Joe   F   14
      Henry   M   14
      James   M   12


    github
    https://tinyurl.com/mvdyxvck
    https://github.com/rogerjdeangelis/utl-sas-format-that-right-justify-sas-character-variable-values

    communities.sas
    https://tinyurl.com/ytftef77
    https://communities.sas.com/t5/SAS-IML-Software-and-Matrix/how-to-right-justify-a-character-matrix-in-sas-iml/m-p/748148#M5487

    /**************************************************************************************************************************/
    /* INPUT                 | PROCESS                                      | OUTPUT                                          */
    /* =====                 | =======                                      | ======                                          */
    /*                       |                                              |                                                 */
    /* data have;            | proc fcmp outlib=work.functions.charRight;   |  NAME      SEX    AGE                           */
    /*   input               |   function charRight(txt $) $32;             |                                                 */
    /*     name$             |     ryght=right(txt);                        |  Alfred     M      14                           */
    /*     sex$ age;         |   return(ryght);                             |      Al     M      13                           */
    /* cards4;               | endsub;                                      | Barbara     F      13                           */
    /* Alfred  M 14          | run;quit;                                    |     Joe     F      14                           */
    /* Al      M 13          |                                              |   Henry     M      14                           */
    /* Barbara F 13          | options cmplib=work.functions;               |   James     M      12                           */
    /* Joe     F 14          |                                              |                                                 */
    /* Henry   M 14          | * put the function in a format;              |                                                 */
    /* James   M 12          | proc format;                                 |                                                 */
    /* ;;;;                  |   value $charRight other=[charRight()];      |                                                 */
    /* run;quit;             | run;quit;                                    |                                                 */
    /*                       |                                              |                                                 */
    /*                       | proc print data=have;                        |                                                 */
    /*                       | format name $charRight.;                     |                                                 */
    /*                       | run;quit;                                    |                                                 */
    /**************************************************************************************************************************/

    /*                   _
    (_)_ __  _ __  _   _| |_
    | | `_ \| `_ \| | | | __|
    | | | | | |_) | |_| | |_
    |_|_| |_| .__/ \__,_|\__|
            |_|
    */

    data have;
      input
        name$
        sex$ age;
    cards4;
    Alfred  M 14
    Al      M 13
    Barbara F 13
    Joe     F 14
    Henry   M 14
    James   M 12
    ;;;;
    run;quit;

    /**************************************************************************************************************************/
    /* NAME       SEX    AGE                                                                                                  */
    /*                                                                                                                        */
    /* Alfred      M      14                                                                                                  */
    /* Al          M      13                                                                                                  */
    /* Barbara     F      13                                                                                                  */
    /* Joe         F      14                                                                                                  */
    /* Henry       M      14                                                                                                  */
    /* James       M      12                                                                                                  */
    /**************************************************************************************************************************/

    /*
     _ __  _ __ ___   ___ ___  ___ ___
    | `_ \| `__/ _ \ / __/ _ \/ __/ __|
    | |_) | | | (_) | (_|  __/\__ \__ \
    | .__/|_|  \___/ \___\___||___/___/
    |_|
    */

    proc fcmp outlib=work.functions.charRight;
      function charRight(txt $) $32;
        ryght=right(txt);
      return(ryght);
    endsub;
    run;quit;

    options cmplib=work.functions;

    * put the function in a format;
    proc format;
      value $charRight other=[charRight()];
    run;quit;

    proc print data=have;
    format name $charRight.;
    run;quit;

    /**************************************************************************************************************************/
    /*  NAME      SEX    AGE                                                                                                  */
    /*                                                                                                                        */
    /*  Alfred     M      14                                                                                                  */
    /*      Al     M      13                                                                                                  */
    /* Barbara     F      13                                                                                                  */
    /*     Joe     F      14                                                                                                  */
    /*   Henry     M      14                                                                                                  */
    /*   James     M      12                                                                                                  */
    /**************************************************************************************************************************/

    /*              _
      ___ _ __   __| |
     / _ \ `_ \ / _` |
    |  __/ | | | (_| |
     \___|_| |_|\__,_|

    */
