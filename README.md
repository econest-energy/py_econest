# Project description
## py_econest

A Python Library for reading data from the econest Household Energy Management System.

You can directly call the library for UUID registration, connectivity detection, and some configuration before receiving data, but you need to provide the serial number and host.


### Usage


```sh
from py_econest import EconestEnergy
import asyncio


async def test():
	# initialization
	econest_energy = EconestEnergy(serial_number="Your serial number", host="device host")

	# Register a UUID.
	device_uuid = await econest_energy.register_uuid()

	# Sampling data synchronization settings
	sync_data_is_success = await econest_energy.sync_data(device_uuid) -> bool

	# Data transmission control
	data_ctrl_is_success = await econest_energy.data_ctrl(device_uuid) -> bool

	# Test connection.
	check_connection_is_success = await econest_energy.check_connection() -> bool


if __name__ == "__main__":
	asyncio.run(test())
```