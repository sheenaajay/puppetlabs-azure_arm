Document: "loadBalancer"


Path: "https://github.com/Azure/azure-rest-api-specs/blob/2fbb5118cd34f412a51d9bc8a274224b216763cf/specification/network/resource-manager/Microsoft.Network/stable/2019-06-01/loadBalancer.json")

## LoadBalancer

LoadBalancer resource.

```puppet
azure_load_balancer {
  api_version => "api_version",
  etag => "etag (optional)",
  id => "id (optional)",
  location => "location (optional)",
  parameters => "parameters",
  properties => $azure_load_balancer_properties_format
  resource_group_name => "resource_group_name",
  sku => $azure_load_balancer_sku
  subscription_id => "subscription_id",
  tags => "tags (optional)",
}
```

| Name        | Type           | Required       | Description       |
| ------------- | ------------- | ------------- | ------------- |
|api_version | String | true | Client API version. |
|etag | String | false | A unique read-only string that changes whenever the resource is updated. |
|id | String | false | Resource ID. |
|location | String | false | Resource location. |
|parameters | Hash | true | Parameters supplied to the create or update load balancer operation. |
|properties | [LoadBalancerPropertiesFormat](#loadbalancerpropertiesformat) | false | Properties of load balancer. |
|resource_group_name | String | true | The name of the resource group. |
|sku | [LoadBalancerSku](#loadbalancersku) | false | The load balancer SKU. |
|subscription_id | String | true | The subscription credentials which uniquely identify the Microsoft Azure subscription. The subscription ID forms part of the URI for every service call. |
|tags | Hash | false | Resource tags. |
        
## LoadBalancerPropertiesFormat

Properties of the load balancer.

```puppet
$azure_load_balancer_properties_format = {
  backendAddressPools => $azure_backend_address_pool
  frontendIPConfigurations => $azure_frontend_ip_configuration
  inboundNatPools => $azure_inbound_nat_pool
  inboundNatRules => $azure_inbound_nat_rule
  loadBalancingRules => $azure_load_balancing_rule
  outboundRules => $azure_outbound_rule
  probes => $azure_probe
  provisioningState => "provisioningState (optional)",
  resourceGuid => "resourceGuid (optional)",
}
```

| Name        | Type           | Required       | Description       |
| ------------- | ------------- | ------------- | ------------- |
|backendAddressPools | [BackendAddressPool](#backendaddresspool) | false | Collection of backend address pools used by a load balancer. |
|frontendIPConfigurations | [FrontendIPConfiguration](#frontendipconfiguration) | false | Object representing the frontend IPs to be used for the load balancer. |
|inboundNatPools | [InboundNatPool](#inboundnatpool) | false | Defines an external port range for inbound NAT to a single backend port on NICs associated with a load balancer. Inbound NAT rules are created automatically for each NIC associated with the Load Balancer using an external port from this range. Defining an Inbound NAT pool on your Load Balancer is mutually exclusive with defining inbound Nat rules. Inbound NAT pools are referenced from virtual machine scale sets. NICs that are associated with individual virtual machines cannot reference an inbound NAT pool. They have to reference individual inbound NAT rules. |
|inboundNatRules | [InboundNatRule](#inboundnatrule) | false | Collection of inbound NAT Rules used by a load balancer. Defining inbound NAT rules on your load balancer is mutually exclusive with defining an inbound NAT pool. Inbound NAT pools are referenced from virtual machine scale sets. NICs that are associated with individual virtual machines cannot reference an Inbound NAT pool. They have to reference individual inbound NAT rules. |
|loadBalancingRules | [LoadBalancingRule](#loadbalancingrule) | false | Object collection representing the load balancing rules Gets the provisioning. |
|outboundRules | [OutboundRule](#outboundrule) | false | The outbound rules. |
|probes | [Probe](#probe) | false | Collection of probe objects used in the load balancer. |
|provisioningState | String | false | Gets the provisioning state of the PublicIP resource. Possible values are: 'Updating', 'Deleting', and 'Failed'. |
|resourceGuid | String | false | The resource GUID property of the load balancer resource. |
        
## BackendAddressPool

Pool of backend IP addresses.

```puppet
$azure_backend_address_pool = {
  etag => "etag (optional)",
  id => "id (optional)",
  name => "name (optional)",
  properties => $azure_backend_address_pool_properties_format
}
```

| Name        | Type           | Required       | Description       |
| ------------- | ------------- | ------------- | ------------- |
|etag | String | false | A unique read-only string that changes whenever the resource is updated. |
|id | String | false | Resource ID. |
|name | String | false | Gets name of the resource that is unique within the set of backend address pools used by the load balancer. This name can be used to access the resource. |
|properties | [BackendAddressPoolPropertiesFormat](#backendaddresspoolpropertiesformat) | false | Properties of load balancer backend address pool. |
        
## BackendAddressPoolPropertiesFormat

Properties of the backend address pool.

```puppet
$azure_backend_address_pool_properties_format = {
  backendIPConfigurations => $azure_network_interface_ip_configuration
  loadBalancingRules => $azure_sub_resource
  outboundRule => $azure_sub_resource
  outboundRules => $azure_sub_resource
  provisioningState => "provisioningState (optional)",
}
```

| Name        | Type           | Required       | Description       |
| ------------- | ------------- | ------------- | ------------- |
|backendIPConfigurations | [NetworkInterfaceIPConfiguration](#networkinterfaceipconfiguration) | false | Gets collection of references to IP addresses defined in network interfaces. |
|loadBalancingRules | [SubResource](#subresource) | false | Gets load balancing rules that use this backend address pool. |
|outboundRule | [SubResource](#subresource) | false | Gets outbound rules that use this backend address pool. |
|outboundRules | [SubResource](#subresource) | false | Gets outbound rules that use this backend address pool. |
|provisioningState | String | false | Get provisioning state of the public IP resource. Possible values are: 'Updating', 'Deleting', and 'Failed'. |
        
## NetworkInterfaceIPConfiguration

IPConfiguration in a network interface.

```puppet
$azure_network_interface_ip_configuration = {
  etag => "etag (optional)",
  id => "id (optional)",
  name => "name (optional)",
  properties => $azure_network_interface_ip_configuration_properties_format
}
```

| Name        | Type           | Required       | Description       |
| ------------- | ------------- | ------------- | ------------- |
|etag | String | false | A unique read-only string that changes whenever the resource is updated. |
|id | String | false | Resource ID. |
|name | String | false | The name of the resource that is unique within a resource group. This name can be used to access the resource. |
|properties | [NetworkInterfaceIPConfigurationPropertiesFormat](#networkinterfaceipconfigurationpropertiesformat) | false | Network interface IP configuration properties. |
        
## NetworkInterfaceIPConfigurationPropertiesFormat

Properties of IP configuration.

```puppet
$azure_network_interface_ip_configuration_properties_format = {
  applicationGatewayBackendAddressPools => $azure_application_gateway_backend_address_pool
  applicationSecurityGroups => $azure_application_security_group
  loadBalancerBackendAddressPools => $azure_backend_address_pool
  loadBalancerInboundNatRules => $azure_inbound_nat_rule
  primary => "primary (optional)",
  privateIPAddress => "privateIPAddress (optional)",
  privateIPAddressVersion => $azure_ip_version
  privateIPAllocationMethod => $azure_ip_allocation_method
  provisioningState => "provisioningState (optional)",
  publicIPAddress => $azure_public_ip_address
  subnet => $azure_subnet
  virtualNetworkTaps => $azure_virtual_network_tap
}
```

| Name        | Type           | Required       | Description       |
| ------------- | ------------- | ------------- | ------------- |
|applicationGatewayBackendAddressPools | [ApplicationGatewayBackendAddressPool](#applicationgatewaybackendaddresspool) | false | The reference of ApplicationGatewayBackendAddressPool resource. |
|applicationSecurityGroups | [ApplicationSecurityGroup](#applicationsecuritygroup) | false | Application security groups in which the IP configuration is included. |
|loadBalancerBackendAddressPools | [BackendAddressPool](#backendaddresspool) | false | The reference of LoadBalancerBackendAddressPool resource. |
|loadBalancerInboundNatRules | [InboundNatRule](#inboundnatrule) | false | A list of references of LoadBalancerInboundNatRules. |
|primary | Boolean | false | Gets whether this is a primary customer address on the network interface. |
|privateIPAddress | String | false | Private IP address of the IP configuration. |
|privateIPAddressVersion | [IPVersion](#ipversion) | false | Available from Api-Version 2016-03-30 onwards, it represents whether the specific ipconfiguration is IPv4 or IPv6. Default is taken as IPv4. |
|privateIPAllocationMethod | [IPAllocationMethod](#ipallocationmethod) | false | The private IP address allocation method. |
|provisioningState | String | false | The provisioning state of the network interface IP configuration. Possible values are: 'Updating', 'Deleting', and 'Failed'. |
|publicIPAddress | [PublicIPAddress](#publicipaddress) | false | Public IP address bound to the IP configuration. |
|subnet | [Subnet](#subnet) | false | Subnet bound to the IP configuration. |
|virtualNetworkTaps | [VirtualNetworkTap](#virtualnetworktap) | false | The reference to Virtual Network Taps. |
        
## ApplicationGatewayBackendAddressPool

Backend Address Pool of an application gateway.

```puppet
$azure_application_gateway_backend_address_pool = {
  etag => "etag (optional)",
  id => "id (optional)",
  name => "name (optional)",
  properties => $azure_application_gateway_backend_address_pool_properties_format
  type => "type (optional)",
}
```

| Name        | Type           | Required       | Description       |
| ------------- | ------------- | ------------- | ------------- |
|etag | String | false | A unique read-only string that changes whenever the resource is updated. |
|id | String | false | Resource ID. |
|name | String | false | Name of the backend address pool that is unique within an Application Gateway. |
|properties | [ApplicationGatewayBackendAddressPoolPropertiesFormat](#applicationgatewaybackendaddresspoolpropertiesformat) | false | Properties of the application gateway backend address pool. |
|type | String | false | Type of the resource. |
        
## ApplicationGatewayBackendAddressPoolPropertiesFormat

Properties of Backend Address Pool of an application gateway.

```puppet
$azure_application_gateway_backend_address_pool_properties_format = {
  backendAddresses => $azure_application_gateway_backend_address
  backendIPConfigurations => $azure_network_interface_ip_configuration
  provisioningState => "provisioningState (optional)",
}
```

| Name        | Type           | Required       | Description       |
| ------------- | ------------- | ------------- | ------------- |
|backendAddresses | [ApplicationGatewayBackendAddress](#applicationgatewaybackendaddress) | false | Backend addresses. |
|backendIPConfigurations | [NetworkInterfaceIPConfiguration](#networkinterfaceipconfiguration) | false | Collection of references to IPs defined in network interfaces. |
|provisioningState | String | false | Provisioning state of the backend address pool resource. Possible values are: 'Updating', 'Deleting', and 'Failed'. |
        
## ApplicationGatewayBackendAddress

Backend address of an application gateway.

```puppet
$azure_application_gateway_backend_address = {
  fqdn => "fqdn (optional)",
  ipAddress => "ipAddress (optional)",
}
```

| Name        | Type           | Required       | Description       |
| ------------- | ------------- | ------------- | ------------- |
|fqdn | String | false | Fully qualified domain name (FQDN). |
|ipAddress | String | false | IP address. |
        
        
## ApplicationSecurityGroup

An application security group in a resource group.

```puppet
$azure_application_security_group = {
  id => "id (optional)",
  location => "location (optional)",
  properties => $azure_application_security_group_properties_format
  tags => "tags (optional)",
}
```

| Name        | Type           | Required       | Description       |
| ------------- | ------------- | ------------- | ------------- |
|id | String | false | Resource ID. |
|location | String | false | Resource location. |
|properties | [ApplicationSecurityGroupPropertiesFormat](#applicationsecuritygrouppropertiesformat) | false | Properties of the application security group. |
|tags | Hash | false | Resource tags. |
        
## ApplicationSecurityGroupPropertiesFormat

Application security group properties.

```puppet
$azure_application_security_group_properties_format = {
}
```

| Name        | Type           | Required       | Description       |
| ------------- | ------------- | ------------- | ------------- |
        
        
## InboundNatRule

Inbound NAT rule of the load balancer.

```puppet
$azure_inbound_nat_rule = {
  etag => "etag (optional)",
  id => "id (optional)",
  name => "name (optional)",
  properties => $azure_inbound_nat_rule_properties_format
}
```

| Name        | Type           | Required       | Description       |
| ------------- | ------------- | ------------- | ------------- |
|etag | String | false | A unique read-only string that changes whenever the resource is updated. |
|id | String | false | Resource ID. |
|name | String | false | Gets name of the resource that is unique within the set of inbound NAT rules used by the load balancer. This name can be used to access the resource. |
|properties | [InboundNatRulePropertiesFormat](#inboundnatrulepropertiesformat) | false | Properties of load balancer inbound nat rule. |
        
## InboundNatRulePropertiesFormat

Properties of the inbound NAT rule.

```puppet
$azure_inbound_nat_rule_properties_format = {
  backendIPConfiguration => $azure_network_interface_ip_configuration
  backendPort => "1234 (optional)",
  enableFloatingIP => "enableFloatingIP (optional)",
  enableTcpReset => "enableTcpReset (optional)",
  frontendIPConfiguration => $azure_sub_resource
  frontendPort => "1234 (optional)",
  idleTimeoutInMinutes => "1234 (optional)",
  protocol => $azure_transport_protocol
  provisioningState => "provisioningState (optional)",
}
```

| Name        | Type           | Required       | Description       |
| ------------- | ------------- | ------------- | ------------- |
|backendIPConfiguration | [NetworkInterfaceIPConfiguration](#networkinterfaceipconfiguration) | false | A reference to a private IP address defined on a network interface of a VM. Traffic sent to the frontend port of each of the frontend IP configurations is forwarded to the backend IP. |
|backendPort | Integer | false | The port used for the internal endpoint. Acceptable values range from 1 to 65535. |
|enableFloatingIP | Boolean | false | Configures a virtual machine's endpoint for the floating IP capability required to configure a SQL AlwaysOn Availability Group. This setting is required when using the SQL AlwaysOn Availability Groups in SQL server. This setting can't be changed after you create the endpoint. |
|enableTcpReset | Boolean | false | Receive bidirectional TCP Reset on TCP flow idle timeout or unexpected connection termination. This element is only used when the protocol is set to TCP. |
|frontendIPConfiguration | [SubResource](#subresource) | false | A reference to frontend IP addresses. |
|frontendPort | Integer | false | The port for the external endpoint. Port numbers for each rule must be unique within the Load Balancer. Acceptable values range from 1 to 65534. |
|idleTimeoutInMinutes | Integer | false | The timeout for the TCP idle connection. The value can be set between 4 and 30 minutes. The default value is 4 minutes. This element is only used when the protocol is set to TCP. |
|protocol | [TransportProtocol](#transportprotocol) | false | The reference to the transport protocol used by the load balancing rule. |
|provisioningState | String | false | Gets the provisioning state of the public IP resource. Possible values are: 'Updating', 'Deleting', and 'Failed'. |
        
        
## SubResource

Reference to another subresource.

```puppet
$azure_sub_resource = {
  id => "id (optional)",
}
```

| Name        | Type           | Required       | Description       |
| ------------- | ------------- | ------------- | ------------- |
|id | String | false | Resource ID. |
        
## TransportProtocol

The transport protocol for the endpoint.

```puppet
$azure_transport_protocol = {
}
```

| Name        | Type           | Required       | Description       |
| ------------- | ------------- | ------------- | ------------- |
        
## IPVersion

IP address version.

```puppet
$azure_ip_version = {
}
```

| Name        | Type           | Required       | Description       |
| ------------- | ------------- | ------------- | ------------- |
        
## IPAllocationMethod

IP address allocation method.

```puppet
$azure_ip_allocation_method = {
}
```

| Name        | Type           | Required       | Description       |
| ------------- | ------------- | ------------- | ------------- |
        
## PublicIPAddress

Public IP address resource.

```puppet
$azure_public_ip_address = {
  etag => "etag (optional)",
  id => "id (optional)",
  location => "location (optional)",
  properties => $azure_public_ip_address_properties_format
  sku => $azure_public_ip_address_sku
  tags => "tags (optional)",
  zones => "zones (optional)",
}
```

| Name        | Type           | Required       | Description       |
| ------------- | ------------- | ------------- | ------------- |
|etag | String | false | A unique read-only string that changes whenever the resource is updated. |
|id | String | false | Resource ID. |
|location | String | false | Resource location. |
|properties | [PublicIPAddressPropertiesFormat](#publicipaddresspropertiesformat) | false | Public IP address properties. |
|sku | [PublicIPAddressSku](#publicipaddresssku) | false | The public IP address SKU. |
|tags | Hash | false | Resource tags. |
|zones | Array | false | A list of availability zones denoting the IP allocated for the resource needs to come from. |
        
## PublicIPAddressPropertiesFormat

Public IP address properties.

```puppet
$azure_public_ip_address_properties_format = {
  ddosSettings => $azure_ddos_settings
  dnsSettings => $azure_public_ip_address_dns_settings
  idleTimeoutInMinutes => "1234 (optional)",
  ipAddress => "ipAddress (optional)",
  ipConfiguration => $azure_ip_configuration
  ipTags => $azure_ip_tag
  provisioningState => "provisioningState (optional)",
  publicIPAddressVersion => $azure_ip_version
  publicIPAllocationMethod => $azure_ip_allocation_method
  publicIPPrefix => $azure_sub_resource
  resourceGuid => "resourceGuid (optional)",
}
```

| Name        | Type           | Required       | Description       |
| ------------- | ------------- | ------------- | ------------- |
|ddosSettings | [DdosSettings](#ddossettings) | false | The DDoS protection custom policy associated with the public IP address. |
|dnsSettings | [PublicIPAddressDnsSettings](#publicipaddressdnssettings) | false | The FQDN of the DNS record associated with the public IP address. |
|idleTimeoutInMinutes | Integer | false | The idle timeout of the public IP address. |
|ipAddress | String | false | The IP address associated with the public IP address resource. |
|ipConfiguration | [IPConfiguration](#ipconfiguration) | false | The IP configuration associated with the public IP address. |
|ipTags | [IpTag](#iptag) | false | The list of tags associated with the public IP address. |
|provisioningState | String | false | The provisioning state of the PublicIP resource. Possible values are: 'Updating', 'Deleting', and 'Failed'. |
|publicIPAddressVersion | [IPVersion](#ipversion) | false | The public IP address version. |
|publicIPAllocationMethod | [IPAllocationMethod](#ipallocationmethod) | false | The public IP address allocation method. |
|publicIPPrefix | [SubResource](#subresource) | false | The Public IP Prefix this Public IP Address should be allocated from. |
|resourceGuid | String | false | The resource GUID property of the public IP resource. |
        
## DdosSettings

Contains the DDoS protection settings of the public IP.

```puppet
$azure_ddos_settings = {
  ddosCustomPolicy => $azure_sub_resource
  protectionCoverage => "protectionCoverage (optional)",
}
```

| Name        | Type           | Required       | Description       |
| ------------- | ------------- | ------------- | ------------- |
|ddosCustomPolicy | [SubResource](#subresource) | false | The DDoS custom policy associated with the public IP. |
|protectionCoverage | String | false | The DDoS protection policy customizability of the public IP. Only standard coverage will have the ability to be customized. |
        
        
## PublicIPAddressDnsSettings

Contains FQDN of the DNS record associated with the public IP address.

```puppet
$azure_public_ip_address_dns_settings = {
  domainNameLabel => "domainNameLabel (optional)",
  fqdn => "fqdn (optional)",
  reverseFqdn => "reverseFqdn (optional)",
}
```

| Name        | Type           | Required       | Description       |
| ------------- | ------------- | ------------- | ------------- |
|domainNameLabel | String | false | Gets or sets the Domain name label.The concatenation of the domain name label and the regionalized DNS zone make up the fully qualified domain name associated with the public IP address. If a domain name label is specified, an A DNS record is created for the public IP in the Microsoft Azure DNS system. |
|fqdn | String | false | Gets the FQDN, Fully qualified domain name of the A DNS record associated with the public IP. This is the concatenation of the domainNameLabel and the regionalized DNS zone. |
|reverseFqdn | String | false | Gets or Sets the Reverse FQDN. A user-visible, fully qualified domain name that resolves to this public IP address. If the reverseFqdn is specified, then a PTR DNS record is created pointing from the IP address in the in-addr.arpa domain to the reverse FQDN. |
        
## IPConfiguration

IP configuration.

```puppet
$azure_ip_configuration = {
  etag => "etag (optional)",
  id => "id (optional)",
  name => "name (optional)",
  properties => $azure_ip_configuration_properties_format
}
```

| Name        | Type           | Required       | Description       |
| ------------- | ------------- | ------------- | ------------- |
|etag | String | false | A unique read-only string that changes whenever the resource is updated. |
|id | String | false | Resource ID. |
|name | String | false | The name of the resource that is unique within a resource group. This name can be used to access the resource. |
|properties | [IPConfigurationPropertiesFormat](#ipconfigurationpropertiesformat) | false | Properties of the IP configuration. |
        
## IPConfigurationPropertiesFormat

Properties of IP configuration.

```puppet
$azure_ip_configuration_properties_format = {
  privateIPAddress => "privateIPAddress (optional)",
  privateIPAllocationMethod => $azure_ip_allocation_method
  provisioningState => "provisioningState (optional)",
  publicIPAddress => $azure_public_ip_address
  subnet => $azure_subnet
}
```

| Name        | Type           | Required       | Description       |
| ------------- | ------------- | ------------- | ------------- |
|privateIPAddress | String | false | The private IP address of the IP configuration. |
|privateIPAllocationMethod | [IPAllocationMethod](#ipallocationmethod) | false | The private IP address allocation method. |
|provisioningState | String | false | Gets the provisioning state of the public IP resource. Possible values are: 'Updating', 'Deleting', and 'Failed'. |
|publicIPAddress | [PublicIPAddress](#publicipaddress) | false | The reference of the public IP resource. |
|subnet | [Subnet](#subnet) | false | The reference of the subnet resource. |
        
        
        
## Subnet

Subnet in a virtual network resource.

```puppet
$azure_subnet = {
  etag => "etag (optional)",
  id => "id (optional)",
  name => "name (optional)",
  properties => $azure_subnet_properties_format
}
```

| Name        | Type           | Required       | Description       |
| ------------- | ------------- | ------------- | ------------- |
|etag | String | false | A unique read-only string that changes whenever the resource is updated. |
|id | String | false | Resource ID. |
|name | String | false | The name of the resource that is unique within a resource group. This name can be used to access the resource. |
|properties | [SubnetPropertiesFormat](#subnetpropertiesformat) | false | Properties of the subnet. |
        
## SubnetPropertiesFormat

Properties of the subnet.

```puppet
$azure_subnet_properties_format = {
  addressPrefix => "addressPrefix (optional)",
  addressPrefixes => "addressPrefixes (optional)",
  delegations => $azure_delegation
  ipConfigurationProfiles => $azure_ip_configuration_profile
  ipConfigurations => $azure_ip_configuration
  natGateway => $azure_sub_resource
  networkSecurityGroup => $azure_network_security_group
  privateEndpointNetworkPolicies => "privateEndpointNetworkPolicies (optional)",
  privateEndpoints => $azure_private_endpoint
  privateLinkServiceNetworkPolicies => "privateLinkServiceNetworkPolicies (optional)",
  provisioningState => "provisioningState (optional)",
  resourceNavigationLinks => $azure_resource_navigation_link
  routeTable => $azure_route_table
  serviceAssociationLinks => $azure_service_association_link
  serviceEndpointPolicies => $azure_service_endpoint_policy
  serviceEndpoints => $azure_service_endpoint_properties_format
}
```

| Name        | Type           | Required       | Description       |
| ------------- | ------------- | ------------- | ------------- |
|addressPrefix | String | false | The address prefix for the subnet. |
|addressPrefixes | Array | false | List of address prefixes for the subnet. |
|delegations | [Delegation](#delegation) | false | Gets an array of references to the delegations on the subnet. |
|ipConfigurationProfiles | [IPConfigurationProfile](#ipconfigurationprofile) | false | Array of IP configuration profiles which reference this subnet. |
|ipConfigurations | [IPConfiguration](#ipconfiguration) | false | Gets an array of references to the network interface IP configurations using subnet. |
|natGateway | [SubResource](#subresource) | false | Nat gateway associated with this subnet. |
|networkSecurityGroup | [NetworkSecurityGroup](#networksecuritygroup) | false | The reference of the NetworkSecurityGroup resource. |
|privateEndpointNetworkPolicies | String | false | Enable or Disable apply network policies on private end point in the subnet. |
|privateEndpoints | [PrivateEndpoint](#privateendpoint) | false | An array of references to private endpoints. |
|privateLinkServiceNetworkPolicies | String | false | Enable or Disable apply network policies on private link service in the subnet. |
|provisioningState | String | false | The provisioning state of the resource. |
|resourceNavigationLinks | [ResourceNavigationLink](#resourcenavigationlink) | false | Gets an array of references to the external resources using subnet. |
|routeTable | [RouteTable](#routetable) | false | The reference of the RouteTable resource. |
|serviceAssociationLinks | [ServiceAssociationLink](#serviceassociationlink) | false | Gets an array of references to services injecting into this subnet. |
|serviceEndpointPolicies | [ServiceEndpointPolicy](#serviceendpointpolicy) | false | An array of service endpoint policies. |
|serviceEndpoints | [ServiceEndpointPropertiesFormat](#serviceendpointpropertiesformat) | false | An array of service endpoints. |
        
## Delegation

Details the service to which the subnet is delegated.

```puppet
$azure_delegation = {
  etag => "etag (optional)",
  id => "id (optional)",
  name => "name (optional)",
  properties => $azure_service_delegation_properties_format
}
```

| Name        | Type           | Required       | Description       |
| ------------- | ------------- | ------------- | ------------- |
|etag | String | false | A unique read-only string that changes whenever the resource is updated. |
|id | String | false | Resource ID. |
|name | String | false | The name of the resource that is unique within a subnet. This name can be used to access the resource. |
|properties | [ServiceDelegationPropertiesFormat](#servicedelegationpropertiesformat) | false | Properties of the subnet. |
        
## ServiceDelegationPropertiesFormat

Properties of a service delegation.

```puppet
$azure_service_delegation_properties_format = {
  actions => "actions (optional)",
  serviceName => "serviceName (optional)",
}
```

| Name        | Type           | Required       | Description       |
| ------------- | ------------- | ------------- | ------------- |
|actions | Array | false | Describes the actions permitted to the service upon delegation. |
|serviceName | String | false | The name of the service to whom the subnet should be delegated (e.g. Microsoft.Sql/servers). |
        
## IPConfigurationProfile

IP configuration profile child resource.

```puppet
$azure_ip_configuration_profile = {
  etag => "etag (optional)",
  id => "id (optional)",
  name => "name (optional)",
  properties => $azure_ip_configuration_profile_properties_format
}
```

| Name        | Type           | Required       | Description       |
| ------------- | ------------- | ------------- | ------------- |
|etag | String | false | A unique read-only string that changes whenever the resource is updated. |
|id | String | false | Resource ID. |
|name | String | false | The name of the resource. This name can be used to access the resource. |
|properties | [IPConfigurationProfilePropertiesFormat](#ipconfigurationprofilepropertiesformat) | false | Properties of the IP configuration profile. |
        
## IPConfigurationProfilePropertiesFormat

IP configuration profile properties.

```puppet
$azure_ip_configuration_profile_properties_format = {
  subnet => $azure_subnet
}
```

| Name        | Type           | Required       | Description       |
| ------------- | ------------- | ------------- | ------------- |
|subnet | [Subnet](#subnet) | false | The reference of the subnet resource to create a container network interface ip configuration. |
        
        
        
        
## NetworkSecurityGroup

NetworkSecurityGroup resource.

```puppet
$azure_network_security_group = {
  etag => "etag (optional)",
  id => "id (optional)",
  location => "location (optional)",
  properties => $azure_network_security_group_properties_format
  tags => "tags (optional)",
}
```

| Name        | Type           | Required       | Description       |
| ------------- | ------------- | ------------- | ------------- |
|etag | String | false | A unique read-only string that changes whenever the resource is updated. |
|id | String | false | Resource ID. |
|location | String | false | Resource location. |
|properties | [NetworkSecurityGroupPropertiesFormat](#networksecuritygrouppropertiesformat) | false | Properties of the network security group. |
|tags | Hash | false | Resource tags. |
        
## NetworkSecurityGroupPropertiesFormat

Network Security Group resource.

```puppet
$azure_network_security_group_properties_format = {
  defaultSecurityRules => $azure_security_rule
  networkInterfaces => $azure_network_interface
  provisioningState => "provisioningState (optional)",
  resourceGuid => "resourceGuid (optional)",
  securityRules => $azure_security_rule
  subnets => $azure_subnet
}
```

| Name        | Type           | Required       | Description       |
| ------------- | ------------- | ------------- | ------------- |
|defaultSecurityRules | [SecurityRule](#securityrule) | false | The default security rules of network security group. |
|networkInterfaces | [NetworkInterface](#networkinterface) | false | A collection of references to network interfaces. |
|provisioningState | String | false | The provisioning state of the public IP resource. Possible values are: 'Updating', 'Deleting', and 'Failed'. |
|resourceGuid | String | false | The resource GUID property of the network security group resource. |
|securityRules | [SecurityRule](#securityrule) | false | A collection of security rules of the network security group. |
|subnets | [Subnet](#subnet) | false | A collection of references to subnets. |
        
## SecurityRule

Network security rule.

```puppet
$azure_security_rule = {
  etag => "etag (optional)",
  id => "id (optional)",
  name => "name (optional)",
  properties => $azure_security_rule_properties_format
}
```

| Name        | Type           | Required       | Description       |
| ------------- | ------------- | ------------- | ------------- |
|etag | String | false | A unique read-only string that changes whenever the resource is updated. |
|id | String | false | Resource ID. |
|name | String | false | The name of the resource that is unique within a resource group. This name can be used to access the resource. |
|properties | [SecurityRulePropertiesFormat](#securityrulepropertiesformat) | false | Properties of the security rule. |
        
## SecurityRulePropertiesFormat

Security rule resource.

```puppet
$azure_security_rule_properties_format = {
  access => $azure_security_rule_access
  description => "description (optional)",
  destinationAddressPrefix => "destinationAddressPrefix (optional)",
  destinationAddressPrefixes => "destinationAddressPrefixes (optional)",
  destinationApplicationSecurityGroups => $azure_application_security_group
  destinationPortRange => "destinationPortRange (optional)",
  destinationPortRanges => "destinationPortRanges (optional)",
  direction => $azure_security_rule_direction
  priority => "1234 (optional)",
  protocol => "protocol",
  provisioningState => "provisioningState (optional)",
  sourceAddressPrefix => "sourceAddressPrefix (optional)",
  sourceAddressPrefixes => "sourceAddressPrefixes (optional)",
  sourceApplicationSecurityGroups => $azure_application_security_group
  sourcePortRange => "sourcePortRange (optional)",
  sourcePortRanges => "sourcePortRanges (optional)",
}
```

| Name        | Type           | Required       | Description       |
| ------------- | ------------- | ------------- | ------------- |
|access | [SecurityRuleAccess](#securityruleaccess) | true | The network traffic is allowed or denied. |
|description | String | false | A description for this rule. Restricted to 140 chars. |
|destinationAddressPrefix | String | false | The destination address prefix. CIDR or destination IP range. Asterisk '*' can also be used to match all source IPs. Default tags such as 'VirtualNetwork', 'AzureLoadBalancer' and 'Internet' can also be used. |
|destinationAddressPrefixes | Array | false | The destination address prefixes. CIDR or destination IP ranges. |
|destinationApplicationSecurityGroups | [ApplicationSecurityGroup](#applicationsecuritygroup) | false | The application security group specified as destination. |
|destinationPortRange | String | false | The destination port or range. Integer or range between 0 and 65535. Asterisk '*' can also be used to match all ports. |
|destinationPortRanges | Array | false | The destination port ranges. |
|direction | [SecurityRuleDirection](#securityruledirection) | true | The direction of the rule. The direction specifies if rule will be evaluated on incoming or outgoing traffic. |
|priority | Integer | false | The priority of the rule. The value can be between 100 and 4096. The priority number must be unique for each rule in the collection. The lower the priority number, the higher the priority of the rule. |
|protocol | String | true | Network protocol this rule applies to. |
|provisioningState | String | false | The provisioning state of the public IP resource. Possible values are: 'Updating', 'Deleting', and 'Failed'. |
|sourceAddressPrefix | String | false | The CIDR or source IP range. Asterisk '*' can also be used to match all source IPs. Default tags such as 'VirtualNetwork', 'AzureLoadBalancer' and 'Internet' can also be used. If this is an ingress rule, specifies where network traffic originates from. |
|sourceAddressPrefixes | Array | false | The CIDR or source IP ranges. |
|sourceApplicationSecurityGroups | [ApplicationSecurityGroup](#applicationsecuritygroup) | false | The application security group specified as source. |
|sourcePortRange | String | false | The source port or range. Integer or range between 0 and 65535. Asterisk '*' can also be used to match all ports. |
|sourcePortRanges | Array | false | The source port ranges. |
        
## SecurityRuleAccess

Whether network traffic is allowed or denied.

```puppet
$azure_security_rule_access = {
}
```

| Name        | Type           | Required       | Description       |
| ------------- | ------------- | ------------- | ------------- |
        
        
## SecurityRuleDirection

The direction of the rule. The direction specifies if rule will be evaluated on incoming or outgoing traffic.

```puppet
$azure_security_rule_direction = {
}
```

| Name        | Type           | Required       | Description       |
| ------------- | ------------- | ------------- | ------------- |
        
        
## NetworkInterface

A network interface in a resource group.

```puppet
$azure_network_interface = {
  etag => "etag (optional)",
  id => "id (optional)",
  location => "location (optional)",
  properties => $azure_network_interface_properties_format
  tags => "tags (optional)",
}
```

| Name        | Type           | Required       | Description       |
| ------------- | ------------- | ------------- | ------------- |
|etag | String | false | A unique read-only string that changes whenever the resource is updated. |
|id | String | false | Resource ID. |
|location | String | false | Resource location. |
|properties | [NetworkInterfacePropertiesFormat](#networkinterfacepropertiesformat) | false | Properties of the network interface. |
|tags | Hash | false | Resource tags. |
        
## NetworkInterfacePropertiesFormat

NetworkInterface properties.

```puppet
$azure_network_interface_properties_format = {
  dnsSettings => $azure_network_interface_dns_settings
  enableAcceleratedNetworking => "enableAcceleratedNetworking (optional)",
  enableIPForwarding => "enableIPForwarding (optional)",
  ipConfigurations => $azure_network_interface_ip_configuration
  macAddress => "macAddress (optional)",
  networkSecurityGroup => $azure_network_security_group
  primary => "primary (optional)",
  privateEndpoint => $azure_private_endpoint
  provisioningState => "provisioningState (optional)",
  resourceGuid => "resourceGuid (optional)",
  tapConfigurations => $azure_network_interface_tap_configuration
  virtualMachine => $azure_sub_resource
}
```

| Name        | Type           | Required       | Description       |
| ------------- | ------------- | ------------- | ------------- |
|dnsSettings | [NetworkInterfaceDnsSettings](#networkinterfacednssettings) | false | The DNS settings in network interface. |
|enableAcceleratedNetworking | Boolean | false | If the network interface is accelerated networking enabled. |
|enableIPForwarding | Boolean | false | Indicates whether IP forwarding is enabled on this network interface. |
|ipConfigurations | [NetworkInterfaceIPConfiguration](#networkinterfaceipconfiguration) | false | A list of IPConfigurations of the network interface. |
|macAddress | String | false | The MAC address of the network interface. |
|networkSecurityGroup | [NetworkSecurityGroup](#networksecuritygroup) | false | The reference of the NetworkSecurityGroup resource. |
|primary | Boolean | false | Gets whether this is a primary network interface on a virtual machine. |
|privateEndpoint | [PrivateEndpoint](#privateendpoint) | false | A reference to the private endpoint to which the network interface is linked. |
|provisioningState | String | false | The provisioning state of the public IP resource. Possible values are: 'Updating', 'Deleting', and 'Failed'. |
|resourceGuid | String | false | The resource GUID property of the network interface resource. |
|tapConfigurations | [NetworkInterfaceTapConfiguration](#networkinterfacetapconfiguration) | false | A list of TapConfigurations of the network interface. |
|virtualMachine | [SubResource](#subresource) | false | The reference of a virtual machine. |
        
## NetworkInterfaceDnsSettings

DNS settings of a network interface.

```puppet
$azure_network_interface_dns_settings = {
  appliedDnsServers => "appliedDnsServers (optional)",
  dnsServers => "dnsServers (optional)",
  internalDnsNameLabel => "internalDnsNameLabel (optional)",
  internalDomainNameSuffix => "internalDomainNameSuffix (optional)",
  internalFqdn => "internalFqdn (optional)",
}
```

| Name        | Type           | Required       | Description       |
| ------------- | ------------- | ------------- | ------------- |
|appliedDnsServers | Array | false | If the VM that uses this NIC is part of an Availability Set, then this list will have the union of all DNS servers from all NICs that are part of the Availability Set. This property is what is configured on each of those VMs. |
|dnsServers | Array | false | List of DNS servers IP addresses. Use 'AzureProvidedDNS' to switch to azure provided DNS resolution. 'AzureProvidedDNS' value cannot be combined with other IPs, it must be the only value in dnsServers collection. |
|internalDnsNameLabel | String | false | Relative DNS name for this NIC used for internal communications between VMs in the same virtual network. |
|internalDomainNameSuffix | String | false | Even if internalDnsNameLabel is not specified, a DNS entry is created for the primary NIC of the VM. This DNS name can be constructed by concatenating the VM name with the value of internalDomainNameSuffix. |
|internalFqdn | String | false | Fully qualified DNS name supporting internal communications between VMs in the same virtual network. |
        
        
        
## PrivateEndpoint

Private endpoint resource.

```puppet
$azure_private_endpoint = {
  etag => "etag (optional)",
  id => "id (optional)",
  location => "location (optional)",
  properties => $azure_private_endpoint_properties
  tags => "tags (optional)",
}
```

| Name        | Type           | Required       | Description       |
| ------------- | ------------- | ------------- | ------------- |
|etag | String | false | A unique read-only string that changes whenever the resource is updated. |
|id | String | false | Resource ID. |
|location | String | false | Resource location. |
|properties | [PrivateEndpointProperties](#privateendpointproperties) | false | Properties of the private endpoint. |
|tags | Hash | false | Resource tags. |
        
## PrivateEndpointProperties

Properties of the private endpoint.

```puppet
$azure_private_endpoint_properties = {
  manualPrivateLinkServiceConnections => $azure_private_link_service_connection
  networkInterfaces => $azure_network_interface
  privateLinkServiceConnections => $azure_private_link_service_connection
  provisioningState => $azure_provisioning_state
  subnet => $azure_subnet
}
```

| Name        | Type           | Required       | Description       |
| ------------- | ------------- | ------------- | ------------- |
|manualPrivateLinkServiceConnections | [PrivateLinkServiceConnection](#privatelinkserviceconnection) | false | A grouping of information about the connection to the remote resource. Used when the network admin does not have access to approve connections to the remote resource. |
|networkInterfaces | [NetworkInterface](#networkinterface) | false | Gets an array of references to the network interfaces created for this private endpoint. |
|privateLinkServiceConnections | [PrivateLinkServiceConnection](#privatelinkserviceconnection) | false | A grouping of information about the connection to the remote resource. |
|provisioningState | [ProvisioningState](#provisioningstate) | false | The provisioning state of the private endpoint. |
|subnet | [Subnet](#subnet) | false | The ID of the subnet from which the private IP will be allocated. |
        
## PrivateLinkServiceConnection

PrivateLinkServiceConnection resource.

```puppet
$azure_private_link_service_connection = {
  id => "id (optional)",
  name => "name (optional)",
  properties => $azure_private_link_service_connection_properties
}
```

| Name        | Type           | Required       | Description       |
| ------------- | ------------- | ------------- | ------------- |
|id | String | false | Resource ID. |
|name | String | false | The name of the resource that is unique within a resource group. This name can be used to access the resource. |
|properties | [PrivateLinkServiceConnectionProperties](#privatelinkserviceconnectionproperties) | false | Properties of the private link service connection. |
        
## PrivateLinkServiceConnectionProperties

Properties of the PrivateLinkServiceConnection.

```puppet
$azure_private_link_service_connection_properties = {
  groupIds => "groupIds (optional)",
  privateLinkServiceConnectionState => $azure_private_link_service_connection_state
  privateLinkServiceId => "privateLinkServiceId (optional)",
  provisioningState => $azure_provisioning_state
  requestMessage => "requestMessage (optional)",
}
```

| Name        | Type           | Required       | Description       |
| ------------- | ------------- | ------------- | ------------- |
|groupIds | Array | false | The ID(s) of the group(s) obtained from the remote resource that this private endpoint should connect to. |
|privateLinkServiceConnectionState | [PrivateLinkServiceConnectionState](#privatelinkserviceconnectionstate) | false | A collection of read-only information about the state of the connection to the remote resource. |
|privateLinkServiceId | String | false | The resource id of private link service. |
|provisioningState | [ProvisioningState](#provisioningstate) | false | The provisioning state of the private link service connection. |
|requestMessage | String | false | A message passed to the owner of the remote resource with this connection request. Restricted to 140 chars. |
        
## PrivateLinkServiceConnectionState

A collection of information about the state of the connection between service consumer and provider.

```puppet
$azure_private_link_service_connection_state = {
  actionRequired => "actionRequired (optional)",
  description => "description (optional)",
  status => "status (optional)",
}
```

| Name        | Type           | Required       | Description       |
| ------------- | ------------- | ------------- | ------------- |
|actionRequired | String | false | A message indicating if changes on the service provider require any updates on the consumer. |
|description | String | false | The reason for approval/rejection of the connection. |
|status | String | false | Indicates whether the connection has been Approved/Rejected/Removed by the owner of the service. |
        
## ProvisioningState

The current provisioning state.

```puppet
$azure_provisioning_state = {
}
```

| Name        | Type           | Required       | Description       |
| ------------- | ------------- | ------------- | ------------- |
        
        
        
        
        
## NetworkInterfaceTapConfiguration

Tap configuration in a Network Interface.

```puppet
$azure_network_interface_tap_configuration = {
  etag => "etag (optional)",
  id => "id (optional)",
  name => "name (optional)",
  properties => $azure_network_interface_tap_configuration_properties_format
}
```

| Name        | Type           | Required       | Description       |
| ------------- | ------------- | ------------- | ------------- |
|etag | String | false | A unique read-only string that changes whenever the resource is updated. |
|id | String | false | Resource ID. |
|name | String | false | The name of the resource that is unique within a resource group. This name can be used to access the resource. |
|properties | [NetworkInterfaceTapConfigurationPropertiesFormat](#networkinterfacetapconfigurationpropertiesformat) | false | Properties of the Virtual Network Tap configuration. |
        
## NetworkInterfaceTapConfigurationPropertiesFormat

Properties of Virtual Network Tap configuration.

```puppet
$azure_network_interface_tap_configuration_properties_format = {
  virtualNetworkTap => $azure_virtual_network_tap
}
```

| Name        | Type           | Required       | Description       |
| ------------- | ------------- | ------------- | ------------- |
|virtualNetworkTap | [VirtualNetworkTap](#virtualnetworktap) | false | The reference of the Virtual Network Tap resource. |
        
## VirtualNetworkTap

Virtual Network Tap resource.

```puppet
$azure_virtual_network_tap = {
  etag => "etag (optional)",
  id => "id (optional)",
  location => "location (optional)",
  properties => $azure_virtual_network_tap_properties_format
  tags => "tags (optional)",
}
```

| Name        | Type           | Required       | Description       |
| ------------- | ------------- | ------------- | ------------- |
|etag | String | false | Gets a unique read-only string that changes whenever the resource is updated. |
|id | String | false | Resource ID. |
|location | String | false | Resource location. |
|properties | [VirtualNetworkTapPropertiesFormat](#virtualnetworktappropertiesformat) | false | Virtual Network Tap Properties. |
|tags | Hash | false | Resource tags. |
        
## VirtualNetworkTapPropertiesFormat

Virtual Network Tap properties.

```puppet
$azure_virtual_network_tap_properties_format = {
  destinationLoadBalancerFrontEndIPConfiguration => $azure_frontend_ip_configuration
  destinationNetworkInterfaceIPConfiguration => $azure_network_interface_ip_configuration
  destinationPort => "1234 (optional)",
  networkInterfaceTapConfigurations => $azure_network_interface_tap_configuration
}
```

| Name        | Type           | Required       | Description       |
| ------------- | ------------- | ------------- | ------------- |
|destinationLoadBalancerFrontEndIPConfiguration | [FrontendIPConfiguration](#frontendipconfiguration) | false | The reference to the private IP address on the internal Load Balancer that will receive the tap. |
|destinationNetworkInterfaceIPConfiguration | [NetworkInterfaceIPConfiguration](#networkinterfaceipconfiguration) | false | The reference to the private IP Address of the collector nic that will receive the tap. |
|destinationPort | Integer | false | The VXLAN destination port that will receive the tapped traffic. |
|networkInterfaceTapConfigurations | [NetworkInterfaceTapConfiguration](#networkinterfacetapconfiguration) | false | Specifies the list of resource IDs for the network interface IP configuration that needs to be tapped. |
        
## FrontendIPConfiguration

Frontend IP address of the load balancer.

```puppet
$azure_frontend_ip_configuration = {
  etag => "etag (optional)",
  id => "id (optional)",
  name => "name (optional)",
  properties => $azure_frontend_ip_configuration_properties_format
  zones => "zones (optional)",
}
```

| Name        | Type           | Required       | Description       |
| ------------- | ------------- | ------------- | ------------- |
|etag | String | false | A unique read-only string that changes whenever the resource is updated. |
|id | String | false | Resource ID. |
|name | String | false | The name of the resource that is unique within the set of frontend IP configurations used by the load balancer. This name can be used to access the resource. |
|properties | [FrontendIPConfigurationPropertiesFormat](#frontendipconfigurationpropertiesformat) | false | Properties of the load balancer probe. |
|zones | Array | false | A list of availability zones denoting the IP allocated for the resource needs to come from. |
        
## FrontendIPConfigurationPropertiesFormat

Properties of Frontend IP Configuration of the load balancer.

```puppet
$azure_frontend_ip_configuration_properties_format = {
  inboundNatPools => $azure_sub_resource
  inboundNatRules => $azure_sub_resource
  loadBalancingRules => $azure_sub_resource
  outboundRules => $azure_sub_resource
  privateIPAddress => "privateIPAddress (optional)",
  privateIPAddressVersion => $azure_ip_version
  privateIPAllocationMethod => $azure_ip_allocation_method
  provisioningState => "provisioningState (optional)",
  publicIPAddress => $azure_public_ip_address
  publicIPPrefix => $azure_sub_resource
  subnet => $azure_subnet
}
```

| Name        | Type           | Required       | Description       |
| ------------- | ------------- | ------------- | ------------- |
|inboundNatPools | [SubResource](#subresource) | false | Read only. Inbound pools URIs that use this frontend IP. |
|inboundNatRules | [SubResource](#subresource) | false | Read only. Inbound rules URIs that use this frontend IP. |
|loadBalancingRules | [SubResource](#subresource) | false | Gets load balancing rules URIs that use this frontend IP. |
|outboundRules | [SubResource](#subresource) | false | Read only. Outbound rules URIs that use this frontend IP. |
|privateIPAddress | String | false | The private IP address of the IP configuration. |
|privateIPAddressVersion | [IPVersion](#ipversion) | false | It represents whether the specific ipconfiguration is IPv4 or IPv6. Default is taken as IPv4. |
|privateIPAllocationMethod | [IPAllocationMethod](#ipallocationmethod) | false | The Private IP allocation method. |
|provisioningState | String | false | Gets the provisioning state of the public IP resource. Possible values are: 'Updating', 'Deleting', and 'Failed'. |
|publicIPAddress | [PublicIPAddress](#publicipaddress) | false | The reference of the Public IP resource. |
|publicIPPrefix | [SubResource](#subresource) | false | The reference of the Public IP Prefix resource. |
|subnet | [Subnet](#subnet) | false | The reference of the subnet resource. |
        
        
        
        
        
        
        
        
        
        
        
        
        
        
        
        
## ResourceNavigationLink

ResourceNavigationLink resource.

```puppet
$azure_resource_navigation_link = {
  name => "name (optional)",
  properties => $azure_resource_navigation_link_format
}
```

| Name        | Type           | Required       | Description       |
| ------------- | ------------- | ------------- | ------------- |
|name | String | false | Name of the resource that is unique within a resource group. This name can be used to access the resource. |
|properties | [ResourceNavigationLinkFormat](#resourcenavigationlinkformat) | false | Resource navigation link properties format. |
        
## ResourceNavigationLinkFormat

Properties of ResourceNavigationLink.

```puppet
$azure_resource_navigation_link_format = {
  link => "link (optional)",
  linkedResourceType => "linkedResourceType (optional)",
}
```

| Name        | Type           | Required       | Description       |
| ------------- | ------------- | ------------- | ------------- |
|link | String | false | Link to the external resource. |
|linkedResourceType | String | false | Resource type of the linked resource. |
        
## RouteTable

Route table resource.

```puppet
$azure_route_table = {
  etag => "etag (optional)",
  id => "id (optional)",
  location => "location (optional)",
  properties => $azure_route_table_properties_format
  tags => "tags (optional)",
}
```

| Name        | Type           | Required       | Description       |
| ------------- | ------------- | ------------- | ------------- |
|etag | String | false | Gets a unique read-only string that changes whenever the resource is updated. |
|id | String | false | Resource ID. |
|location | String | false | Resource location. |
|properties | [RouteTablePropertiesFormat](#routetablepropertiesformat) | false | Properties of the route table. |
|tags | Hash | false | Resource tags. |
        
## RouteTablePropertiesFormat

Route Table resource.

```puppet
$azure_route_table_properties_format = {
  disableBgpRoutePropagation => "disableBgpRoutePropagation (optional)",
  provisioningState => "provisioningState (optional)",
  routes => $azure_route
  subnets => $azure_subnet
}
```

| Name        | Type           | Required       | Description       |
| ------------- | ------------- | ------------- | ------------- |
|disableBgpRoutePropagation | Boolean | false | Gets or sets whether to disable the routes learned by BGP on that route table. True means disable. |
|provisioningState | String | false | The provisioning state of the resource. Possible values are: 'Updating', 'Deleting', and 'Failed'. |
|routes | [Route](#route) | false | Collection of routes contained within a route table. |
|subnets | [Subnet](#subnet) | false | A collection of references to subnets. |
        
## Route

Route resource.

```puppet
$azure_route = {
  etag => "etag (optional)",
  id => "id (optional)",
  name => "name (optional)",
  properties => $azure_route_properties_format
}
```

| Name        | Type           | Required       | Description       |
| ------------- | ------------- | ------------- | ------------- |
|etag | String | false | A unique read-only string that changes whenever the resource is updated. |
|id | String | false | Resource ID. |
|name | String | false | The name of the resource that is unique within a resource group. This name can be used to access the resource. |
|properties | [RoutePropertiesFormat](#routepropertiesformat) | false | Properties of the route. |
        
## RoutePropertiesFormat

Route resource.

```puppet
$azure_route_properties_format = {
  addressPrefix => "addressPrefix (optional)",
  nextHopIpAddress => "nextHopIpAddress (optional)",
  nextHopType => $azure_route_next_hop_type
  provisioningState => "provisioningState (optional)",
}
```

| Name        | Type           | Required       | Description       |
| ------------- | ------------- | ------------- | ------------- |
|addressPrefix | String | false | The destination CIDR to which the route applies. |
|nextHopIpAddress | String | false | The IP address packets should be forwarded to. Next hop values are only allowed in routes where the next hop type is VirtualAppliance. |
|nextHopType | [RouteNextHopType](#routenexthoptype) | true | The type of Azure hop the packet should be sent to. |
|provisioningState | String | false | The provisioning state of the resource. Possible values are: 'Updating', 'Deleting', and 'Failed'. |
        
## RouteNextHopType

The type of Azure hop the packet should be sent to.

```puppet
$azure_route_next_hop_type = {
}
```

| Name        | Type           | Required       | Description       |
| ------------- | ------------- | ------------- | ------------- |
        
        
## ServiceAssociationLink

ServiceAssociationLink resource.

```puppet
$azure_service_association_link = {
  id => "id (optional)",
  name => "name (optional)",
  properties => $azure_service_association_link_properties_format
  type => "type (optional)",
}
```

| Name        | Type           | Required       | Description       |
| ------------- | ------------- | ------------- | ------------- |
|id | String | false | Resource ID. |
|name | String | false | Name of the resource that is unique within a resource group. This name can be used to access the resource. |
|properties | [ServiceAssociationLinkPropertiesFormat](#serviceassociationlinkpropertiesformat) | false | Resource navigation link properties format. |
|type | String | false | Resource type. |
        
## ServiceAssociationLinkPropertiesFormat

Properties of ServiceAssociationLink.

```puppet
$azure_service_association_link_properties_format = {
  allowDelete => "allowDelete (optional)",
  link => "link (optional)",
  linkedResourceType => "linkedResourceType (optional)",
  locations => "locations (optional)",
}
```

| Name        | Type           | Required       | Description       |
| ------------- | ------------- | ------------- | ------------- |
|allowDelete | Boolean | false | If true, the resource can be deleted. |
|link | String | false | Link to the external resource. |
|linkedResourceType | String | false | Resource type of the linked resource. |
|locations | Array | false | A list of locations. |
        
## ServiceEndpointPolicy

Service End point policy resource.

```puppet
$azure_service_endpoint_policy = {
  etag => "etag (optional)",
  id => "id (optional)",
  location => "location (optional)",
  properties => $azure_service_endpoint_policy_properties_format
  tags => "tags (optional)",
}
```

| Name        | Type           | Required       | Description       |
| ------------- | ------------- | ------------- | ------------- |
|etag | String | false | A unique read-only string that changes whenever the resource is updated. |
|id | String | false | Resource ID. |
|location | String | false | Resource location. |
|properties | [ServiceEndpointPolicyPropertiesFormat](#serviceendpointpolicypropertiesformat) | false | Properties of the service end point policy. |
|tags | Hash | false | Resource tags. |
        
## ServiceEndpointPolicyPropertiesFormat

Service Endpoint Policy resource.

```puppet
$azure_service_endpoint_policy_properties_format = {
  serviceEndpointPolicyDefinitions => $azure_service_endpoint_policy_definition
  subnets => $azure_subnet
}
```

| Name        | Type           | Required       | Description       |
| ------------- | ------------- | ------------- | ------------- |
|serviceEndpointPolicyDefinitions | [ServiceEndpointPolicyDefinition](#serviceendpointpolicydefinition) | false | A collection of service endpoint policy definitions of the service endpoint policy. |
|subnets | [Subnet](#subnet) | false | A collection of references to subnets. |
        
## ServiceEndpointPolicyDefinition

Service Endpoint policy definitions.

```puppet
$azure_service_endpoint_policy_definition = {
  etag => "etag (optional)",
  id => "id (optional)",
  name => "name (optional)",
  properties => $azure_service_endpoint_policy_definition_properties_format
}
```

| Name        | Type           | Required       | Description       |
| ------------- | ------------- | ------------- | ------------- |
|etag | String | false | A unique read-only string that changes whenever the resource is updated. |
|id | String | false | Resource ID. |
|name | String | false | The name of the resource that is unique within a resource group. This name can be used to access the resource. |
|properties | [ServiceEndpointPolicyDefinitionPropertiesFormat](#serviceendpointpolicydefinitionpropertiesformat) | false | Properties of the service endpoint policy definition. |
        
## ServiceEndpointPolicyDefinitionPropertiesFormat

Service Endpoint policy definition resource.

```puppet
$azure_service_endpoint_policy_definition_properties_format = {
  description => "description (optional)",
  service => "service (optional)",
  serviceResources => "serviceResources (optional)",
}
```

| Name        | Type           | Required       | Description       |
| ------------- | ------------- | ------------- | ------------- |
|description | String | false | A description for this rule. Restricted to 140 chars. |
|service | String | false | Service endpoint name. |
|serviceResources | Array | false | A list of service resources. |
        
        
## ServiceEndpointPropertiesFormat

The service endpoint properties.

```puppet
$azure_service_endpoint_properties_format = {
  locations => "locations (optional)",
  provisioningState => "provisioningState (optional)",
  service => "service (optional)",
}
```

| Name        | Type           | Required       | Description       |
| ------------- | ------------- | ------------- | ------------- |
|locations | Array | false | A list of locations. |
|provisioningState | String | false | The provisioning state of the resource. |
|service | String | false | The type of the endpoint service. |
        
## IpTag

Contains the IpTag associated with the object.

```puppet
$azure_ip_tag = {
  ipTagType => "ipTagType (optional)",
  tag => "tag (optional)",
}
```

| Name        | Type           | Required       | Description       |
| ------------- | ------------- | ------------- | ------------- |
|ipTagType | String | false | Gets or sets the ipTag type: Example FirstPartyUsage. |
|tag | String | false | Gets or sets value of the IpTag associated with the public IP. Example SQL, Storage etc. |
        
        
        
        
## PublicIPAddressSku

SKU of a public IP address.

```puppet
$azure_public_ip_address_sku = {
  name => "name (optional)",
}
```

| Name        | Type           | Required       | Description       |
| ------------- | ------------- | ------------- | ------------- |
|name | String | false | Name of a public IP address SKU. |
        
        
        
        
        
        
        
## InboundNatPool

Inbound NAT pool of the load balancer.

```puppet
$azure_inbound_nat_pool = {
  etag => "etag (optional)",
  id => "id (optional)",
  name => "name (optional)",
  properties => $azure_inbound_nat_pool_properties_format
}
```

| Name        | Type           | Required       | Description       |
| ------------- | ------------- | ------------- | ------------- |
|etag | String | false | A unique read-only string that changes whenever the resource is updated. |
|id | String | false | Resource ID. |
|name | String | false | The name of the resource that is unique within the set of inbound NAT pools used by the load balancer. This name can be used to access the resource. |
|properties | [InboundNatPoolPropertiesFormat](#inboundnatpoolpropertiesformat) | false | Properties of load balancer inbound nat pool. |
        
## InboundNatPoolPropertiesFormat

Properties of Inbound NAT pool.

```puppet
$azure_inbound_nat_pool_properties_format = {
  backendPort => "1234",
  enableFloatingIP => "enableFloatingIP (optional)",
  enableTcpReset => "enableTcpReset (optional)",
  frontendIPConfiguration => $azure_sub_resource
  frontendPortRangeEnd => "1234",
  frontendPortRangeStart => "1234",
  idleTimeoutInMinutes => "1234 (optional)",
  protocol => $azure_transport_protocol
  provisioningState => "provisioningState (optional)",
}
```

| Name        | Type           | Required       | Description       |
| ------------- | ------------- | ------------- | ------------- |
|backendPort | Integer | true | The port used for internal connections on the endpoint. Acceptable values are between 1 and 65535. |
|enableFloatingIP | Boolean | false | Configures a virtual machine's endpoint for the floating IP capability required to configure a SQL AlwaysOn Availability Group. This setting is required when using the SQL AlwaysOn Availability Groups in SQL server. This setting can't be changed after you create the endpoint. |
|enableTcpReset | Boolean | false | Receive bidirectional TCP Reset on TCP flow idle timeout or unexpected connection termination. This element is only used when the protocol is set to TCP. |
|frontendIPConfiguration | [SubResource](#subresource) | false | A reference to frontend IP addresses. |
|frontendPortRangeEnd | Integer | true | The last port number in the range of external ports that will be used to provide Inbound Nat to NICs associated with a load balancer. Acceptable values range between 1 and 65535. |
|frontendPortRangeStart | Integer | true | The first port number in the range of external ports that will be used to provide Inbound Nat to NICs associated with a load balancer. Acceptable values range between 1 and 65534. |
|idleTimeoutInMinutes | Integer | false | The timeout for the TCP idle connection. The value can be set between 4 and 30 minutes. The default value is 4 minutes. This element is only used when the protocol is set to TCP. |
|protocol | [TransportProtocol](#transportprotocol) | true | The reference to the transport protocol used by the inbound NAT pool. |
|provisioningState | String | false | Gets the provisioning state of the PublicIP resource. Possible values are: 'Updating', 'Deleting', and 'Failed'. |
        
        
        
        
## LoadBalancingRule

A load balancing rule for a load balancer.

```puppet
$azure_load_balancing_rule = {
  etag => "etag (optional)",
  id => "id (optional)",
  name => "name (optional)",
  properties => $azure_load_balancing_rule_properties_format
}
```

| Name        | Type           | Required       | Description       |
| ------------- | ------------- | ------------- | ------------- |
|etag | String | false | A unique read-only string that changes whenever the resource is updated. |
|id | String | false | Resource ID. |
|name | String | false | The name of the resource that is unique within the set of load balancing rules used by the load balancer. This name can be used to access the resource. |
|properties | [LoadBalancingRulePropertiesFormat](#loadbalancingrulepropertiesformat) | false | Properties of load balancer load balancing rule. |
        
## LoadBalancingRulePropertiesFormat

Properties of the load balancer.

```puppet
$azure_load_balancing_rule_properties_format = {
  backendAddressPool => $azure_sub_resource
  backendPort => "1234 (optional)",
  disableOutboundSnat => "disableOutboundSnat (optional)",
  enableFloatingIP => "enableFloatingIP (optional)",
  enableTcpReset => "enableTcpReset (optional)",
  frontendIPConfiguration => $azure_sub_resource
  frontendPort => "1234",
  idleTimeoutInMinutes => "1234 (optional)",
  loadDistribution => "loadDistribution (optional)",
  probe => $azure_sub_resource
  protocol => $azure_transport_protocol
  provisioningState => "provisioningState (optional)",
}
```

| Name        | Type           | Required       | Description       |
| ------------- | ------------- | ------------- | ------------- |
|backendAddressPool | [SubResource](#subresource) | false | A reference to a pool of DIPs. Inbound traffic is randomly load balanced across IPs in the backend IPs. |
|backendPort | Integer | false | The port used for internal connections on the endpoint. Acceptable values are between 0 and 65535. Note that value 0 enables 'Any Port'. |
|disableOutboundSnat | Boolean | false | Configures SNAT for the VMs in the backend pool to use the publicIP address specified in the frontend of the load balancing rule. |
|enableFloatingIP | Boolean | false | Configures a virtual machine's endpoint for the floating IP capability required to configure a SQL AlwaysOn Availability Group. This setting is required when using the SQL AlwaysOn Availability Groups in SQL server. This setting can't be changed after you create the endpoint. |
|enableTcpReset | Boolean | false | Receive bidirectional TCP Reset on TCP flow idle timeout or unexpected connection termination. This element is only used when the protocol is set to TCP. |
|frontendIPConfiguration | [SubResource](#subresource) | false | A reference to frontend IP addresses. |
|frontendPort | Integer | true | The port for the external endpoint. Port numbers for each rule must be unique within the Load Balancer. Acceptable values are between 0 and 65534. Note that value 0 enables 'Any Port'. |
|idleTimeoutInMinutes | Integer | false | The timeout for the TCP idle connection. The value can be set between 4 and 30 minutes. The default value is 4 minutes. This element is only used when the protocol is set to TCP. |
|loadDistribution | String | false | The load distribution policy for this rule. |
|probe | [SubResource](#subresource) | false | The reference of the load balancer probe used by the load balancing rule. |
|protocol | [TransportProtocol](#transportprotocol) | true | The reference to the transport protocol used by the load balancing rule. |
|provisioningState | String | false | Gets the provisioning state of the PublicIP resource. Possible values are: 'Updating', 'Deleting', and 'Failed'. |
        
        
        
        
        
## OutboundRule

Outbound rule of the load balancer.

```puppet
$azure_outbound_rule = {
  etag => "etag (optional)",
  id => "id (optional)",
  name => "name (optional)",
  properties => $azure_outbound_rule_properties_format
}
```

| Name        | Type           | Required       | Description       |
| ------------- | ------------- | ------------- | ------------- |
|etag | String | false | A unique read-only string that changes whenever the resource is updated. |
|id | String | false | Resource ID. |
|name | String | false | The name of the resource that is unique within the set of outbound rules used by the load balancer. This name can be used to access the resource. |
|properties | [OutboundRulePropertiesFormat](#outboundrulepropertiesformat) | false | Properties of load balancer outbound rule. |
        
## OutboundRulePropertiesFormat

Outbound rule of the load balancer.

```puppet
$azure_outbound_rule_properties_format = {
  allocatedOutboundPorts => "1234 (optional)",
  backendAddressPool => $azure_sub_resource
  enableTcpReset => "enableTcpReset (optional)",
  frontendIPConfigurations => $azure_sub_resource
  idleTimeoutInMinutes => "1234 (optional)",
  protocol => "protocol",
  provisioningState => "provisioningState (optional)",
}
```

| Name        | Type           | Required       | Description       |
| ------------- | ------------- | ------------- | ------------- |
|allocatedOutboundPorts | Integer | false | The number of outbound ports to be used for NAT. |
|backendAddressPool | [SubResource](#subresource) | true | A reference to a pool of DIPs. Outbound traffic is randomly load balanced across IPs in the backend IPs. |
|enableTcpReset | Boolean | false | Receive bidirectional TCP Reset on TCP flow idle timeout or unexpected connection termination. This element is only used when the protocol is set to TCP. |
|frontendIPConfigurations | [SubResource](#subresource) | true | The Frontend IP addresses of the load balancer. |
|idleTimeoutInMinutes | Integer | false | The timeout for the TCP idle connection. |
|protocol | String | true | The protocol for the outbound rule in load balancer. |
|provisioningState | String | false | Gets the provisioning state of the PublicIP resource. Possible values are: 'Updating', 'Deleting', and 'Failed'. |
        
        
        
## Probe

A load balancer probe.

```puppet
$azure_probe = {
  etag => "etag (optional)",
  id => "id (optional)",
  name => "name (optional)",
  properties => $azure_probe_properties_format
}
```

| Name        | Type           | Required       | Description       |
| ------------- | ------------- | ------------- | ------------- |
|etag | String | false | A unique read-only string that changes whenever the resource is updated. |
|id | String | false | Resource ID. |
|name | String | false | Gets name of the resource that is unique within the set of probes used by the load balancer. This name can be used to access the resource. |
|properties | [ProbePropertiesFormat](#probepropertiesformat) | false | Properties of load balancer probe. |
        
## ProbePropertiesFormat

Load balancer probe resource.

```puppet
$azure_probe_properties_format = {
  intervalInSeconds => "1234 (optional)",
  loadBalancingRules => $azure_sub_resource
  numberOfProbes => "1234 (optional)",
  port => "1234",
  protocol => "protocol",
  provisioningState => "provisioningState (optional)",
  requestPath => "requestPath (optional)",
}
```

| Name        | Type           | Required       | Description       |
| ------------- | ------------- | ------------- | ------------- |
|intervalInSeconds | Integer | false | The interval, in seconds, for how frequently to probe the endpoint for health status. Typically, the interval is slightly less than half the allocated timeout period (in seconds) which allows two full probes before taking the instance out of rotation. The default value is 15, the minimum value is 5. |
|loadBalancingRules | [SubResource](#subresource) | false | The load balancer rules that use this probe. |
|numberOfProbes | Integer | false | The number of probes where if no response, will result in stopping further traffic from being delivered to the endpoint. This values allows endpoints to be taken out of rotation faster or slower than the typical times used in Azure. |
|port | Integer | true | The port for communicating the probe. Possible values range from 1 to 65535, inclusive. |
|protocol | String | true | The protocol of the end point. If 'Tcp' is specified, a received ACK is required for the probe to be successful. If 'Http' or 'Https' is specified, a 200 OK response from the specifies URI is required for the probe to be successful. |
|provisioningState | String | false | Gets the provisioning state of the public IP resource. Possible values are: 'Updating', 'Deleting', and 'Failed'. |
|requestPath | String | false | The URI used for requesting health status from the VM. Path is required if a protocol is set to http. Otherwise, it is not allowed. There is no default value. |
        
        
## LoadBalancerSku

SKU of a load balancer.

```puppet
$azure_load_balancer_sku = {
  name => "name (optional)",
}
```

| Name        | Type           | Required       | Description       |
| ------------- | ------------- | ------------- | ------------- |
|name | String | false | Name of a load balancer SKU. |



## CRUD operations

Here is a list of endpoints that we use to create, read, update and delete the LoadBalancer

| Operation | Path | Verb | Description | OperationID |
| ------------- | ------------- | ------------- | ------------- | ------------- |
|Create|`/subscriptions/%{subscription_id}/resourceGroups/%{resource_group_name}/providers/Microsoft.Network/loadBalancers/%{load_balancer_name}`|Put|Creates or updates a load balancer.|LoadBalancers_CreateOrUpdate|
|List - list all|`/subscriptions/%{subscription_id}/providers/Microsoft.Network/loadBalancers`|Get|Gets all the load balancers in a subscription.|LoadBalancers_ListAll|
|List - get one|`/subscriptions/%{subscription_id}/resourceGroups/%{resource_group_name}/providers/Microsoft.Network/loadBalancers/%{load_balancer_name}`|Get|Gets the specified load balancer.|LoadBalancers_Get|
|List - get list using params|`/subscriptions/%{subscription_id}/resourceGroups/%{resource_group_name}/providers/Microsoft.Network/loadBalancers`|Get|Gets all the load balancers in a resource group.|LoadBalancers_List|
|Update|`/subscriptions/%{subscription_id}/resourceGroups/%{resource_group_name}/providers/Microsoft.Network/loadBalancers/%{load_balancer_name}`|Put|Creates or updates a load balancer.|LoadBalancers_CreateOrUpdate|
|Delete|`/subscriptions/%{subscription_id}/resourceGroups/%{resource_group_name}/providers/Microsoft.Network/loadBalancers/%{load_balancer_name}`|Delete|Deletes the specified load balancer.|LoadBalancers_Delete|
