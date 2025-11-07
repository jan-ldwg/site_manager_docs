```typescript
type PortType = {
  portTypeId: string; //UUIDv4
  portTypeName: string;
  portTypeDirection:
    | "IN"
    | "OUT"
    | "BIDI"
    | "SWITCHABLE"
    | "UPLINK"
    | "DOWNLINK"
    | "UPSTREAM"
    | "DOWNSTREAM";
  connectorId: string;
  connectorName: string;
  connectorGender: string;
  connectorIcon: string;
  compatibleSignalTypes: string[];
};
type Module = {
  moduleTypeId: string;
  moduleTypeName: string;
  manufacturer: string;
  manufacturerName: string;
  manufactuerNameShort: string;
  orderNumber?: string;
  orderName?: string;
  ports: PortType[];
};

type ModuleSlotType = {
  moduleSlotTypeId: string; //UUIDv4
  moduleSlotTypeName: string;
};

type DeviceType = {
  deviceTypeId: string; //UUIDv4
  deviceTypeName: string;
  manufacturerId: string;
  manufacturerName: string;
  manufactuerNameShort: string;
  orderCode?: string;
  orderName?: string;
  climateLoad: number; //in watts
  weight?: number; //in grams
  width?: number; //in millimeters
  height?: number; //in millimeters
  depth?: number; //in millimeters
  heightRackUnits?: number; //in RU
  portTypes?: PortType[];
  moduleSlotTypes?: ModuleSlotType[];
};
```
