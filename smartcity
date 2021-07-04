pragma solidity ^0.8.4;


contract SmartCity {
    
    
  
    uint public transactions; // pour compter toutes les transactions
    
    struct Informateur {
        
        string Message ;  // message de l'informateur
        string emitter_type; // le status de l'informateur, dans la function c'est string memory _informateur
        string Position ; // le lieu ou s'est passé les evenements
        bool initialized; // pour comprendre si le vehicule avait été enregistré avant
       
        uint  date; // le jour que le vehicule avait eu le probleme
        
    }
    // le mapping dans un autre mapping, j'ai utilié deux clés qui sont uniques pour etre logique. 
    mapping(string=>mapping(address=>Informateur))public informations;
    
    event Informer (address indexed informateur, string  _plaque,string message ,uint _date); // les evenement pour connaitre celui qui a fait le mouvement
    
    
    //cette fonction verifie les informations données par les informateurs
    
     function verifierLevehicule(string memory _plaque, address _add)view public returns(Informateur memory) {
        
       return  informations[_plaque][_add];
     }
    
    // cette focntion ajoute les informations et ça prend l'address de l'utilisateur comme informateur, c'est pourquoi j'ai utilisé msg.sender
    
    function informerMouvement(string memory _plaque,string memory _message,string memory _informateur,string memory _position )public {
        require(informations[_plaque][msg.sender].initialized==false,"this vehicule is already here");
        transactions+=1;
        informations[_plaque][msg.sender]=Informateur(_message,_informateur,_position,true,block.timestamp);
        emit Informer(msg.sender,_plaque,_message,block.timestamp);
    }
    
    
