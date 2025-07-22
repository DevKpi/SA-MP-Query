Samp_Query Class by DevKpi

A PHP class for querying SA-MP (San Andreas Multiplayer) servers using the SA-MP Query Protocol.
This class allows retrieving various information from SA-MP servers including server status, player information, server rules, and basic server details.

* @package    SAMP
* @author     DevKpi
* @version    1.0
 
Properties:
@property resource|null $socket          Socket connection to the server
@property array        $server_info      Array containing server information
@property int         $retry_limit      Number of connection retry attempts
@property array       $timeouts         Array containing timeout values for connections

Methods:
@method __construct($server_address, $port = 7777)  Initializes connection to the SA-MP server
@method bool     Is_Online()            Checks if the server is online
@method int|null Get_Ping()             Returns the server ping in milliseconds
@method array    Get_Information()      Returns basic server information (hostname, gamemode, etc.)
@method array    Get_Players_0()        Returns basic player information (nickname and score)
@method array    Get_Players_1()        Returns detailed player information (ID, nickname, score, ping)
@method array    Get_Rules()            Returns server rules

Private Methods:
@method mixed    attempt($operation)    Handles retry mechanism for server operations
@method int      To_Int($data)         Converts byte data to integer
@method string   Build_Packet($command) Builds query packet for server communication
   

* Usage Example:

$query = new Samp_Query('server_ip', 7777);
if($query->Is_Online()) {
  $info = $query->Get_Information();
  $players = $query->Get_Players_1();
}
