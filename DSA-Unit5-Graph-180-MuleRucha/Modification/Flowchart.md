## Flowchart

                 ( START )
                     |
                     v
        / Input locations and roads /
                     |
                     v
             +---------------------+
             | Create weighted     |
             | graph               |
             +---------------------+
                     |
                     v
       / Input source and destination /
                     |
                     v
               /-------------\
              < Are inputs    >
              < valid?        >
               \-------------/
                 /         \
              No             Yes
              |               |
              v               v
    /-------------------\  +--------------------------+
   / Display invalid     \ | Run Dijkstra before      |
   \ input message       / | update                   |
    \-------------------/  +--------------------------+
              |                       |
              |                       v
              |            /---------------------------\
              |           / Display shortest route and \
              |           \ distance or no-path message/
              |            \---------------------------/
              |                       |
              |                       v
              |            / Input and validate new road /
              |                       |
              |                       v
              |            +----------------------------+
              |            | Add road and display       |
              |            | updated graph               |
              |            +----------------------------+
              |                       |
              |                       v
              |            +----------------------------+
              |            | Run Dijkstra after update  |
              |            +----------------------------+
              |                       |
              |                       v
              |            /---------------------------\
              |           / Display updated route and   \
              |           \ distance or no-path message /
              |            \---------------------------/
              |                       |
              |                       v
              |            +----------------------------+
              |            | Compare before and after   |
              |            | results                    |
              |            +----------------------------+
              |                       |
              +-----------------------+
                                      |
                                      v
                                  ( STOP )
