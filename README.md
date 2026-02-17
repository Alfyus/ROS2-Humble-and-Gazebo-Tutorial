[TUTORIAL ITALIANO](#ros2-humble-e-gazebo-in-italiano)

[ENGLISH TUTORIAL](#ros2-humble-and-gazebo-in-english)
# ROS2 Humble e Gazebo in Italiano
## Pre-requisiti
> [!IMPORTANT]
> ASSICURATEVI DI AVERE UBUNTU 22.04 (Jammy Jellyfish). [LINK UBUNTU](https://releases.ubuntu.com/jammy/)

Aprite il terminale (Ctrl+Alt+T) e scrivete:

```
locale
```

Se la shell non vi restituisce nulla, per settare tutto in Italiano:

```
sudo apt update && sudo apt-get install locales
```

```
sudo locale-gen it_IT it_IT.UTF-8
```

```
sudo update-locale LC_ALL=it_IT.UTF-8 LANG=it_IT.UTF-8
```

```
export LANG=it_IT.UTF-8
```

Per installare ROS2 dobbiamo abilitare Ubuntu Universe repository:
```
sudo apt install software-properties-common
```
```
sudo add-apt-repository universe
```
Ora possiamo aggiungere la repository nel sistema. Autorizziamo la GPG pubblica (data da ROS2) e aggiungiamo ROS2 Alla source list:

```
sudo apt update && sudo apt install curl gnupg lsb-release
```
```
sudo curl -sSL https://raw.githubusercontent.com/ros/rosdistro/master/ros.key -o /usr/share/keyrings/ros-archive-keyring.gpg
```
```
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/ros-archive-keyring.gpg] http://packages.ros.org/ros2/ubuntu $(source /etc/os-release && echo $UBUNTU_CODENAME) main" | sudo tee /etc/apt/sources.list.d/ros2.list > /dev/null
```
## Installazione ROS2 Humble
```
sudo apt update
```
```
sudo apt install ros-humble-desktop
```

Ora facciamo il setup automatico da terminale per usare ROS2:

```
echo "source /opt/ros/humble/setup.bash" >> ~/.bashrc
```
```
source ~/.bashrc
```

Ricordatevi che, se avete personalizzato la shell, dovete sostituire .bashrc con il file corrispondente alla vostra shell (ad esempio, .zshrc). Se non avete apportato modifiche, i due comandi di terminale precedenti andranno bene.

>[!TIP]
>Per confermare che l’installazione sia avvenuta con successo:
>```
>ros2 run demo_nodes_cpp talker
>```
>
>Vi dovrebbe mostrare un output del genere:
>> [INFO] [1652382860.246687611] [talker]: Publishing: 'Hello World: 1'
>
>> [INFO] [1652382861.250208871] [talker]: Publishing: 'Hello World: 2'
>
>> [INFO] [1652382862.246508551] [talker]: Publishing: 'Hello World: 3'
>
>
>Aprite un altro terminale lasciando quello di prima aperto mentre continua a generare testo. Ora digitate:
>```
>ros2 run demo_nodes_py listener
>```
>L’output dovrebbe essere:
>
>> [INFO] [1652382936.495044030] [listener]: I heard: [Hello World: 1]
>
>> [INFO] [1652382937.478216343] [listener]: I heard: [Hello World: 2]
>
>> [INFO] [1652382938.487370309] [listener]: I heard: [Hello World: 3]
>
>Se i due output sono quelli descritti prima, ROS2 funziona correttamente!

## Installare Gazebo

Per installare gazebo:
```
sudo apt install gazebo
```
Confermate con “S”

Per avviarlo:
```
gazebo
```


Per interfacciare ROS2 con Gazebo:
```
sudo apt install ros-humble-gazebo-ros-pkgs
```
Confermate con “S”

>[!TIP]
>Per confermare che Gazebo si interfacci correttamente con ROS2:
>```
>ros2 run turtlesim turtlesim_node
>```
>Questo comando dovrebbe aprire una finestra che mostra una tartaruga. Cerchiamo ora di far muovere questa tartaruga con la tastiera, aprite un nuovo terminale lasciando la finstra con la tartaruga attiva e scrivete:
>```
>ros2 run turtlesim turtle_teleop_key
>```
>Se tutto è installato correttamente, mettete le due finestre accanto, usando le frecce della tastiera dovreste riuscire a muovere la tartaruga.


# ROS2 Humble and Gazebo in English
## Prerequisite
> [!IMPORTANT]
> ENSURE YOUR ENVIRONMENT IS RUNNING UNUNTU 22.04 (Jammy Jellyfish).[LINK UBUNTU](https://releases.ubuntu.com/jammy/)

Open the terminal (Ctrl+Alt+T) and type:

```
locale
```

If the shell doesn't return anything, to set everything to English:

```
sudo apt update && sudo apt-get install locales
```

```
sudo locale-gen en_US en_US.UTF-8
```

```
sudo update-locale LC_ALL=en_US.UTF-8 LANG=en_US.UTF-8
```

```
export LANG=en_US.UTF-8
```

To install ROS2 we need to enable Ubuntu Universe repository:
```
sudo apt install software-properties-common
```
```
sudo add-apt-repository universe
```
Now we can add the repository to the system. We authorize the public GPG (provided by ROS2) and add ROS2 to the source list:

```
sudo apt update && sudo apt install curl gnupg lsb-release
```
```
sudo curl -sSL https://raw.githubusercontent.com/ros/rosdistro/master/ros.key -o /usr/share/keyrings/ros-archive-keyring.gpg
```
```
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/ros-archive-keyring.gpg] http://packages.ros.org/ros2/ubuntu $(source /etc/os-release && echo $UBUNTU_CODENAME) main" | sudo tee /etc/apt/sources.list.d/ros2.list > /dev/null
```
## ROS2 Humble Installation
```
sudo apt update
```
```
sudo apt install ros-humble-desktop
```

Now let's do the automatic setup from terminal to use ROS2:

```
echo "source /opt/ros/humble/setup.bash" >> ~/.bashrc
```
```
source ~/.bashrc
```

Remember that if you've customized the shell, replace bashrc with your shell (e.g., zshrc). If you haven't changed anything, the two terminal commands above are fine.

>[!TIP]
>To confirm that the installation was successful:
>```
>ros2 run demo_nodes_cpp talker
>```
>
>It should show you an output like this:
>> [INFO] [1652382860.246687611] [talker]: Publishing: 'Hello World: 1'
>
>> [INFO] [1652382861.250208871] [talker]: Publishing: 'Hello World: 2'
>
>> [INFO] [1652382862.246508551] [talker]: Publishing: 'Hello World: 3'
>
>
>Open another terminal leaving the first one open while it continues to generate text. Now type:
>```
>ros2 run demo_nodes_py listener
>```
>The output should be:
>
>> [INFO] [1652382936.495044030] [listener]: I heard: [Hello World: 1]
>
>> [INFO] [1652382937.478216343] [listener]: I heard: [Hello World: 2]
>
>> [INFO] [1652382938.487370309] [listener]: I heard: [Hello World: 3]
>
>If the two outputs are as described above, ROS2 is working correctly!

## Installing Gazebo

To install gazebo:
```
sudo apt install gazebo
```
Confirm with “Y”

To start it:
```
gazebo
```


To interface ROS2 with Gazebo:
```
sudo apt install ros-humble-gazebo-ros-pkgs
```
Confirm with “Y”

>[!TIP]
>To confirm that Gazebo is correctly interfacing with ROS2:
>```
>ros2 run turtlesim turtlesim_node
>```
>This command should open a window showing a turtle. Now let's try to move this turtle with the keyboard. Open a new terminal, leaving the window with the turtle active, and type:
>```
>ros2 run turtlesim turtle_teleop_key
>```
>If everything is installed correctly, place the two windows next to each other, using the arrow keys on your keyboard you should be able to move the turtle.
>
