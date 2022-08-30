NextGen Inventory CLI

### 1. bigip-onboard create
usage: Create BIG-IP to device group

required params:
- icontrol_hostname: BIG-IP icontrol API hostname
- icontrol_username: BIG-IP icontrol API username
- icontrol_password: BIG-IP icontrol API password

positional params:
- id: ID of BIG-IP device group, it should be specified when add new BIG-IP to an existing group.
- availability_zone: availability zone of BIG-IP group, default null.
- icontrol_port: BIP-IP icontrol API port, default 443.

command example:
1. Create a new BIG-IP to a new device group

    `bigip-onboard create 10.145.76.72 admin admin@f5.com --availability_zone nova`
2. Create a new BIG-IP to an existing device group

    `bigip-onboard create 10.145.75.174 admin admin@f5.com --id 8842dbbb-8041-4318-9517-f09cd29a3f55`

### 2. bigip-onboard delete
usage: Remove an existing BIG-IP or an existing device group

required params:
- id: ID of BIG-IP device group

positional params:
- icontrol_hostname: hostname of BIG-IP to be removed

command example:
1. Remove an existing BIG-IP from an existing group, icontrol_hostname should be specified.

`bigip-onboard delete 8842dbbb-8041-4318-9517-f09cd29a3f55 --icontrol_hostname 10.145.75.174`

2. Remove an existing group.

`bigip-onboard delete 8842dbbb-8041-4318-9517-f09cd29a3f55`



### 3. bigip-onboard update
usage: Modify the admin properties of an existing BIG-IP in an existing device group

required params:
- id: ID of BIG-IP group

positional params:
- admin-state-down: when this param exist in the command, `admin_state_up` property will be set `false`. 
(The updating logic is same as `neutron agent-update`)
- availability_zone: availability zone of BIG-IP group

command example:
1. update admin_state_up to `false`.

    `bigip-onboard update 8842dbbb-8041-4318-9517-f09cd29a3f55 --admin-state-down`

2. update availability_zone to `test`

    `bigip-onboard update 8842dbbb-8041-4318-9517-f09cd29a3f55 --availability_zone test`

### 4. bigip-onboard refresh
usage: Refresh the device properties of an existing BIG-IP in an existing device group

required params:
- id: ID of BIG-IP group
- icontrol_hostname: hostname of BIG-IP to be refreshed

command example:

`bigip-onboard refresh 8842dbbb-8041-4318-9517-f09cd29a3f55 10.145.75.174`

### 5. bigip-onboard list
usage: List all BIG-IP in the inventory

no required params and positional params.

### 6. bigip-onboard show
usage: Show the specific group of BIG-IP inventory

required params:
- id: ID of BIG-IP group

command example:

`bigip-onboard show 8842dbbb-8041-4318-9517-f09cd29a3f55`

