# Plugin TaHomaLocal
# Changelog


>**IMPORTANT**
>
> S'il n'y a pas d'information sur la mise à jour, c'est que celle-ci concerne uniquement de la mise à jour de documentation, de traduction ou de texte.

# 22/01/2024 - v1.0.22 beta & stable
- Ajout équipements en BDD
- Evolutions code Daemon

# 18/01/2024 - v1.0.21 beta & stable
- Changement du Logo
- Evolutions formats paramètres des commandes

# 16/01/2024 - v1.0.20 beta & stable
- Améliorations générales

# 13/01/2024 - v1.0.19 beta & stable

Cette version est une version définitive de l'implémentation COMPLETE de l'API locale SOMFY.
Tous les équipements (remontés par l'API locale) sont pris en charge et l'ensemble de leurs commandes est rendu accessible.
Cela comprend les commandes à 0, 1 et 2 paramètres (param2 qu'il soit optionnel ou non).

- Ajout équipements en BDD
- Mise a jour banque d'icones
- Suppression accès champ Token Scope (edition non autorisée par Somfy - Valeur fixe : devmode)
- Correction afin de supprimer l'erreur [Errno 98] Address already in use

# 06/01/2024 - v1.0.18 stable
- Amélioration création des commandes info en tenant compte du subtype
- Amélioration et créations des commandes action à 1 paramètre avec liste des valeurs lorsqu’elles sont définies (connues)
- Amélioration création et gestion des commandes actions avec création d’une commande info supplémentaire pour les actions nécéssitant 2 paramètres

# 30/12/2023 - v1.0.16 stable
- Ajout équipements en BDD
- Mise a jour banque d'icones
- Correction d'un bug qui entrainait un mauvais fonctionnement de l'import en mode SMART

# 20/12/2023 - v1.0.14 stable
- Amelioration gestion du Daemon lors de la phase de configuration du plugin

# 17/12/2023 - v1.0.13 stable
- Ajout équipements en BDD
- Mise a jour banque d'icones

# 16/12/2023 - v1.0.13 stable
- Amelioration processing "Découverte passerelles" (part 2)

# 13/12/2023 - v1.0.12 stable
- Amelioration processing "Découverte passerelles" (part 1)
- Mise a jour banque d'icones
- Ajout équipements en BDD

# 07/12/2023 - v1.0.11 stable
- Ajout équipements en BDD

# 01/11/2023 - v1.0.10 stable
- Corrections : extension manquante pour certains fichiers de la BDD
- Ajout équipements en BDD

# 30/10/2023 - v1.0.9 stable
- Corrections
- Ajout icones Devices
- Ajout équipements en BDD

# 28/10/2023 - v1.0.8 stable
- Ajout une dépendance
- Ajout icone Gateway

# 26/10/2023 - v1.0.7 stable
- Ajout équipements en BDD

# 24/10/2023 - v1.0.7 stable
- Ajout possibilité (optionnelle) d'entrer l'adresse IPv4 de la box (en cas de pb de DNS)

# 23/10/2023 - v1.0.6 stable
- Corrections
- Ajout équipements en BDD
- Ajout rubriques
- Ajout modèle de box dans panneau de configuration

# 19/10/2023 - v1.0.5 stable
- Corrections

# 18/10/2023 - v1.0.4 stable
- Ajout équipements en BDD

# 17/10/2023 - v1.0.4 stable
- Ajout équipements en BDD

# 16/10/2023 - v1.0.3 stable
- Corrections
- Ajout équipements en BDD

# 13/10/2023 - v1.0.2 stable
- Evolutions mineures
- Ajout équipements en BDD

# 12/10/2023 - v1.0.1 stable
- Corrections et évolutions mineures

# 11/10/2023 - v1.0.0 stable
- Edition initiale

# 02/10/2023
- Edition v1.0.0 beta


# Equipements en BDD utilisés pour le Mode Smart
> Alarm
>- internal:TSKAlarmComponent
>- io:AlarmIOComponent

> Awning
>- io:HorizontalAwningIOComponent
>- rts:HorizontalAwningRTSComponent

> ContactSensor
>- io:SomfyContactIOSystemSensor
>- zigbee:DoorSensorComponent

> Dock
>- internal:TSKDockComponent

> ElectricitySensor
>- io:AirConditioningElectricalEnergyConsumptionSensor
>- io:DHWCumulatedElectricalEnergyConsumptionIOSystemDeviceSensor
>- io:DHWElectricalEnergyConsumptionSensor
>- io:ElectricityMeterComponent
>- io:EnergyConsumptionSensorsConfigurationComponent
>- io:EnergyConsumptionSensorsHeatPumpComponent
>- io:HeatingElectricalEnergyConsumptionSensor
>- io:OtherElectricalEnergyConsumptionSensor
>- io:PlugsElectricalEnergyConsumptionSensor
>- io:TotalElectricalEnergyConsumptionIOSystemSensor

> ExteriorScreen
>- io:VerticalExteriorAwningIOComponent

> ExteriorVenetianBlind
>- io:ExteriorVenetianBlindIOComponent

> GarageDoor
>- io:DiscreteGarageOpenerIOComponent
>- io:DiscreteGarageOpenerWithPartialPositionIOComponent
>- io:GarageOpenerIOComponent
>- rts:GarageDoorRTSComponent
>- rts:GarageDoor4TRTSComponent

> Gate
>- io:SlidingDiscreteFullyPedestriableGateOpenerIOComponent
>- io:SlidingDiscreteGateOpenerIOComponent
>- rts:GateOpenerRTS4TComponent

> Generic
>- rts:Generic4TRTSComponent

> HeatingSystem
>- io:AtlanticElectricalHeaterIOComponent
>- zigbee:DanfossIconValveComponent

> HumiditySensor
>- zigbee:RelativeHumidityComponent

> Light
>- io:DimmableLightIOComponent
>- io:OnOffLightIOComponent
>- rts:LightRTSComponent

> LightSensor
>- io:LightIOSystemSensor

> NetworkComponent
>- io:BeaconIOComponent
>- zigbee:ZigbeeNetworkNode

> OccupancySensor
>- io:SomfyOccupancyIOSystemSensor
>- zigbee:MotionSensorComponent

> OnOff
>- io:OnOffIOComponent
>- rts:OnOffRTSComponent

> Pergola
>- io:SimpleBioclimaticPergolaIOComponent

> Pod
>- internal:PodMiniComponent
>- internal:PodV2Component
>- internal:PodV3Component

> ProtocolGateway
>- enocean:TransceiverEnoceanComponent
>- io:StackComponent
>- zigbee:StackV3Component
>- zigbee:TransceiverV3_0Component

> RemoteController
>- io:IORemoteController
>- io:KeygoController
>- io:V500Controller
>- zigbee:ZigbeeRemoteComponent

> RollerShutter
>- io:MicroModuleRollerShutterSomfyIOComponent
>- io:RollerShutterGenericIOComponent
>- io:RollerShutterVeluxIOComponent
>- io:RollerShutterWithBatterySomfyIOComponent
>- io:RollerShutterWithLowSpeedManagementIOComponent
>- rts:RollerShutterRTSComponent

> Siren
>- io:SomfyIndoorSimpleSirenIOComponent

> SmokeSensor
>- io:SomfySmokeIOSystemSensor

> SwingingShutter
>- io:SwingingShutterSomfyIOComponent
>- rts:SwingingShutterRTSComponent

> TemperatureSensor
>- io:TemperatureIOSystemSensor
>- zigbee:TemperatureSensorComponent

> WaterHeatingSystem
>- io:AtlanticDomesticHotWaterProductionV2_CETHI_V4_IOComponent
>- io:DomesticHotWaterTankComponent

> WaterSensor
>- zigbee:WaterLeakageSensorComponent

> Wifi
>- internal:WifiComponent

> Window
>- io:WindowOpenerVeluxIOComponent

> WindowHandle
>- enocean:EnOceanWindowHandle
