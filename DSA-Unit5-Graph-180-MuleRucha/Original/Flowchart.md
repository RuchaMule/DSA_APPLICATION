                 ( START )
                     |
                     v
      / Input number of locations \
     /          and roads           \
                     |
                     v
      +-----------------------------+
      | Create weighted graph and   |
      | enter road distances        |
      +-----------------------------+
                     |
                     v
       / Input source and destination /
                     |
                     v
      +-----------------------------+
      | Initialize distances; set   |
      | source distance = 0         |
      +-----------------------------+
                     |
                     v
                /-----------\
               < Priority    >
               < queue       >
               < empty?      >
                \-----------/
                 /         \
              Yes           No
               |             |
               v             v
       /----------------\  +------------------------+
      < Destination      > | Remove minimum-distance|
      < reachable?       > | location from queue    |
       \----------------/  +------------------------+
          /       \                    |
        Yes        No                  v
         |          |       +------------------------+
         v          v       | Relax adjacent edges   |
  /-------------------\     | and update distances   |
 / Display route and   \    | and parents            |
 \ total distance      /    +------------------------+
  \-------------------/                |
         |                              |
         |                    Repeat queue loop
         |                              |
         |______________________________|
         |
         |          /-------------------\
         |         / Display "No path    \
         |         \ exists"             /
         |          \-------------------/
         |                   |
         v                   v
                  ( STOP )
