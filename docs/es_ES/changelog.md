
# TaHomaLocal plugin
# Changelog

>**IMPORTANT**
>
>As a reminder, if there is no information on an update, it means that it only concerns the updating of documentation, translation or text.

07/24/2024 - v1.1.1 beta & stable
- Add IP Mode IP (for particular network configuration)

# 12/20/2023 - v1.0.14 stable
- Improve Daemon processing during plugin configuration phase

# 12/17/2023 - v1.0.13 stable
- Add equipments in database

# 12/16/2023 - v1.0.13 stable
- Improve processing "Gateway(s) Discovery" (part 2)

# 12/13/2023 - v1.0.12 stable
- Improve processing "Gateway(s) Discovery" (part 1)
- Add equipments in database

# 12/07/2023 - v1.0.11 stable
- Add equipments in database

# 10/26/2023 - v1.0.7 stable
- Add equipments in database
- Add field in Configuration page to enter box IPv4 address (optional) in case of box access issue (DNS issue)

# 10/11/2023 - v1.0.0 stable
- Initiale version

# 10/02/2023 - v1.0.0 beta
- v1.0.0 beta


# List of equipments recognized during plugin SMART mode import
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
