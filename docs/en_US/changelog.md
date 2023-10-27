# TaHomaLocal plugin
# Changelog

>**IMPORTANT**
>
>As a reminder, if there is no information on an update, it means that it only concerns the updating of documentation, translation or text.

# 26/10/2023 - v1.0.7 stable
- Add equipment in database
- Add field in Configuration page to enter box IPv4 address (optional) in case of box access issue (DNS issue)

# 11/10/2023 - v1.0.0 stable
- Initiale version

# 02/10/2023 - v1.0.0 beta
- v1.0.0 beta


# List of equipments recognized during plugin SMART mode import
> Alarm
>- internal:TSKAlarmComponent

> Awning
>- io:HorizontalAwningIOComponent
>- rts:HorizontalAwningRTSComponent

> ContactSensor
>- io:SomfyContactIOSystemSensor
>- zigbee:DoorSensorComponent

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

> HumiditySensor
>- zigbee:RelativeHumidityComponent

> GarageDoor
>- io:DiscreteGarageOpenerIOComponent

> Gate
>- io:SlidingDiscreteFullyPedestriableGateOpenerIOComponent

> HeatingSystem
>- io:AtlanticElectricalHeaterIOComponent
>- zigbee:DanfossIconValveComponent

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
>- zigbee:MotionSensorComponent

> OnOff
>- io:OnOffIOComponent

> Pod
>- internal:PodV2Component
>- internal:PodV3Component

> ProtocolGateway
>- io:StackComponent
>- zigbee:StackV3Component
>- zigbee:TransceiverV3_0Component

> RemoteController
>- io:KeygoController
>- zigbee:ZigbeeRemoteComponent

> RollerShutter
>- io:MicroModuleRollerShutterSomfyIOComponent
>- io:RollerShutterGenericIOComponent
>- io:RollerShutterVeluxIOComponent
>- io:RollerShutterWithBatterySomfyIOComponent
>- io:RollerShutterWithLowSpeedManagementIOComponent

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
