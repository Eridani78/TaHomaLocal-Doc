# TaHomaLocal Plugin
# SMART Mode supported devices


Alarm
- internal:TSKAlarmComponent
- io:AlarmIOComponent

Awning
- io:HorizontalAwningIOComponent
- rts:HorizontalAwningRTSComponent

ContactSensor
- io:SomfyContactIOSystemSensor
- zigbee:DoorSensorComponent

Dock
- internal:TSKDockComponent

ElectricitySensor
- io:AirConditioningElectricalEnergyConsumptionSensor
- io:DHWCumulatedElectricalEnergyConsumptionIOSystemDeviceSensor
- io:DHWElectricalEnergyConsumptionSensor
- io:ElectricityMeterComponent
- io:EnergyConsumptionSensorsConfigurationComponent
- io:EnergyConsumptionSensorsHeatPumpComponent
- io:HeatingElectricalEnergyConsumptionSensor
- io:OtherElectricalEnergyConsumptionSensor
- io:PlugsElectricalEnergyConsumptionSensor
- io:TotalElectricalEnergyConsumptionIOSystemSensor

ExteriorScreen
- io:VerticalExteriorAwningIOComponent

ExteriorVenetianBlind
- io:ExteriorVenetianBlindIOComponent

GarageDoor
- io:DiscreteGarageOpenerIOComponent
- io:DiscreteGarageOpenerWithPartialPositionIOComponent
- io:GarageOpenerIOComponent
- rts:GarageDoorRTSComponent
- rts:GarageDoor4TRTSComponent

Gate
- io:GateOpenerIOComponent
- io:SlidingDiscreteFullyPedestriableGateOpenerIOComponent
- io:SlidingDiscreteGateOpenerIOComponent
- rts:GateOpenerRTSComponent
- rts:GateOpenerRTS4TComponent

Generic
- rts:Generic4TRTSComponent

HeatingSystem
- io:AtlanticElectricalHeaterIOComponent
- zigbee:DanfossIconValveComponent

HumiditySensor
- zigbee:RelativeHumidityComponent

Light
- io:DimmableLightIOComponent
- io:OnOffLightIOComponent
- rts:LightRTSComponent

LightSensor
- io:LightIOSystemSensor

NetworkComponent
- io:BeaconIOComponent
- zigbee:ZigbeeNetworkNode

OccupancySensor
- io:SomfyOccupancyIOSystemSensor
- zigbee:MotionSensorComponent

OnOff
- io:OnOffIOComponent
- rts:OnOffRTSComponent

Pergola
- io:SimpleBioclimaticPergolaIOComponent

Pod
- internal:PodMiniComponent
- internal:PodV2Component
- internal:PodV3Component

ProtocolGateway
- enocean:TransceiverEnoceanComponent
- io:StackComponent
- zigbee:StackV3Component
- zigbee:TransceiverV3_0Component

RemoteController
- io:IORemoteController
- io:KeygoController
- io:V500Controller
- zigbee:ZigbeeRemoteComponent

RollerShutter
- io:MicroModuleRollerShutterSomfyIOComponent
- io:RollerShutterGenericIOComponent
- io:RollerShutterVeluxIOComponent
- io:RollerShutterWithBatterySomfyIOComponent
- io:RollerShutterWithLowSpeedManagementIOComponent
- rts:RollerShutterRTSComponent

Siren
- io:SomfyIndoorSimpleSirenIOComponent

SmokeSensor
- io:SomfySmokeIOSystemSensor

SwingingShutter
- io:SwingingShutterSomfyIOComponent
- rts:SwingingShutterRTSComponent

TemperatureSensor
- io:TemperatureIOSystemSensor
- zigbee:TemperatureSensorComponent

WaterHeatingSystem
- io:AtlanticDomesticHotWaterProductionV2_CETHI_V4_IOComponent
- io:DomesticHotWaterTankComponent

WaterSensor
- zigbee:WaterLeakageSensorComponent

Wifi
- internal:WifiComponent

Window
- io:WindowOpenerVeluxIOComponent

WindowHandle
- enocean:EnOceanWindowHandle
