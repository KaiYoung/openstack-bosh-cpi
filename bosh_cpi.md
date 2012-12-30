#OpenStack CPI Implementation #
OpenStack CPI is an implementation of BOSH CPI. It allows BOSH to interface with various services in OpenStack like glance, controller and registry. In the sections below we outline the implementation details for each of the method in CPI interface.

##Initialize ##

Implementation of `def initialize(options)` method. 

1. Validate the `options` passed to this method
2. In the second step the parameters are extracted from `options` object to populate the following properties 
	+ `@agent_properties`	
	+ `@openstack_properties`
	+ `@registry_propertiess`
3. Populate the `openstack_params` and Instantiate `Fog::Compute` instance
4. Populate the `glance_params`and instantiate `Fog::Image` instance
5. Instantiate `Registry_Client`.

Figure below shows the flow of control.

![openstack_cpi_initialize](https://raw.github.com/rajdeepd/openstack-bosh-cpi/master/images/openstack_cpi_initialize.png)

##Create Stemcell ##

Implementation of method `create_stemcell(image_path, cloud_properties)`
Steps outlined below are the flow control implemented to extract and upload kernel image, ramdisk and stem cell image.

1. Extract parameters from the `cloud_properties`. Check if `kernel_file` parameter exists, instantiate `kernel_image` object
2. Construct `kernel_params`
3. Upload `kernel_image` to glance service by calling the method `upload_image(kernel_params)`
4. If params contain `ramdisk_file` 
5. Instantiate ramdisk_image object and populate `ramdisk_parama`
6. Upload the `ramdisk_image` to glance service by calling `upload(ramdisk_params)`
7. Populate `image_params` for the stem cell to be uploaded to glance service
8. Call the method `upload_image(image_params)` 

Figure below shows the flow control for the method `create_stemcell(image_path, cloud_properties)`

![openstack_cpi_createstemcell](https://raw.github.com/rajdeepd/openstack-bosh-cpi/master/images/openstack_cpi_createstemcell.png)

##Delete Stemcell

![openstack_cpi_deletestemcell](https://raw.github.com/rajdeepd/openstack-bosh-cpi/master/images/openstack_cpi_deletestemcell.png)

##Create VM ##

![openstack_cpi_create_vm](https://raw.github.com/rajdeepd/openstack-bosh-cpi/master/images/openstack_cpi_create_vm.png)
##Delete VM ##

##Create Volume ##

##Delete Volume##
