# BitBuffer
Typings for [rstk](https://github.com/rstk)'s [BitBuffer](https://github.com/rstk/BitBuffer) module.

## Installation
```bash
npm i @rbxts/bitbuffer-rstk
```

## Usage
```ts
import { ReplicatedStorage } from "@rbxts/services";
import BitBuffer from "@rbxts/bitbuffer-rstk";

class PlayerData {
        public Money: number;

        public Experience: number;

        public AverageFps: number;

        public CustomName: string;

        public constructor(serialized?: string) {
                const buffer = BitBuffer.FromBase91(serialized);

                this.Money = buffer.ReadUInt(32);
                this.Experience = buffer.ReadUInt(16);
                this.AverageFps = buffer.ReadFloat32();
		this.CustomName = buffer.ReadString();
        }

        public Serialize() {
                const buffer = new BitBuffer();

                buffer.WriteUInt(32, this.Money);
                buffer.WriteUInt(16, this.Experience);
                buffer.WriteFloat32(this.AverageFps);
                buffer.WriteString(this.CustomName);

                return buffer.ToBase91();
        }
}

export = PlayerData;
```
