# Beispieldeployment auf PCO 

mit diesem Playbook kann eine dreischichtige Infrastruktur auf Basis von der PlusCloudOpen bereitgestellt werden. 

## Need

Man braucht das clouds.yaml + secure.yaml file, in dem dann die Cloud "pluscloudopen" am Anfang entprechend der Playbooks benannt wird:

    clouds:
      pluscloudopen:
        auth:


Benutzt wird aktuell ansible 2.9


## variablen

in variables.yaml kann man beliebige Netze, Router, Instancen, Loadbalancermember etc setzen. Die einzelnen Variablen sind in dervariable.yaml erklärt. In der Regel muss das Playbook nicht mehr editiert werden. 
in jumphostconfig.yaml stehen alle infos zu dem Jumphost, der eine Verbindung via ssh auf die Umgebung ermöglicht. 


## Aufruf


    ansible-playbook create_instanceos_lb_loop.yaml

Installiert das gesamte Setup und gibt am Ende die IP des Jumphosts aus, auf die man sich dann einloggen kann. (Hint: "ssh -A für key-forwarding") 


## Löschen

Hier ist die Reihenfolge wichtig, um alle Teile komplett zu entfernen:

Zuerst:

    ansible-playbook delete_jump_host.yaml

Dann:

    ansible-playbook: delete_instanceos_lb_loop.yaml
