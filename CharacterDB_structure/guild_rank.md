Back to the [characters database](charactersdb_struct) list of tables.

The \`guild\_rank\` table
-------------------------

This table holds the information on all of the ranks available in a guild along with their names and what rights a person with that rank has.

### Structure

| **Field**                                     | **Type**         | **Null** | **Key** | **Default** | **Extra** |
|-----------------------------------------------|------------------|----------|---------|-------------|-----------|
| [guildid](Guild_rank#guildid)                 | int(6) unsigned  | NO       | PRI     | 0           |           |
| [rid](Guild_rank#rid)                         | int(11) unsigned | NO       | PRI     |             |           |
| [rname](Guild_rank#rname)                     | varchar(255)     | NO       |         |             |           |
| [rights](Guild_rank#rights)                   | int(3) unsigned  | NO       |         | 0           |           |
| [BankMoneyPerDay](Guild_rank#bankmoneyperday) | int(11) unsigned | NO       |         | 0           |           |

### Description of the fields

#### guildid

The guild ID that the rank is part of. See [guild.guildid](guild#guildid)

#### rid

The particular rank ID. This number must be unique to each rank in a guild.

#### rname

The name of the rank that is displayed in-game.

#### rights

The rights a player with this rank has in the guild. The calculation of multiple rights is a bit different in this case as the rights do not all have 2^n values. To combine ranks, you must do the OR operation (|) on the two flags.


| Flag  | Name                   | Comments                                                                  |
| ----- | ---------------------- | ------------------------------------------------------------------------- |
| 64    | GR_RIGHT_EMPTY         | Having just this flag by itself is equivalent to having no rights at all. |
| 65    | GR_RIGHT_GCHATLISTEN   | Player can read messages in the guild general chat channel.               |
| 66    | GR_RIGHT_GCHATSPEAK    | Player can type messages in the guild general chat channel.               |
| 68    | GR_RIGHT_OFFCHATLISTEN | Player can read messages in the guild officers channel.                   |
| 72    | GR_RIGHT_OFFCHATSPEAK  | Player can type messages in the guild officers channel.                   |
| 80    | GR_RIGHT_INVITE        | Can invite other players to guild.                                        |
| 96    | GR_RIGHT_REMOVE        | Can kick other players out of guild.                                      |
| 192   | GR_RIGHT_PROMOTE       | Can promote other players.                                                |
| 320   | GR_RIGHT_DEMOTE        | Can demote other players.                                                 |
| 4160  | GR_RIGHT_SETMOTD       | Can change the guild message of the day.                                  |
| 8256  | GR_RIGHT_EPNOTE        | Can edit other players' personal notes.                                   |
| 16448 | GR_RIGHT_VIEWOFFNOTE   | Can view the officer notes of other players.                              |
| 32832 | GR_RIGHT_EOFFNOTE      | Can edit officer notes of other players.                                  |
| 61951 | GR_RIGHT_ALL           | Has all of the rights.                                                    |

#### BankMoneyPerDay

The total money per day, in copper, that a person with this rank can take out. Use the maximum value of an unsigned int (4294967295) to specify unlimited amount.
