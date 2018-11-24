# Custom kernel for Xiaomi Redmi Note 2 (Hermes)
# Kernel version 3.10.108 (upstreamed from me)
# Rebased Kernel (Credits: @Dinolek)

* Works:
	* LCM (nt35596_tianma , nt35596_auo , nt35532_boe)
	* Touch (ATMEL , FT)
	* Sdcard
	* WI-FI
	* BT
	* GPS
	* Button-Backlight
	* Brightness
	* Leds Indication
	* RIL (SIM1 and SIM2)
	* Alsps (LTR559)
	* Accelerometer (BMI160_ACC)
	* Gyroscope (BMI160_GYRO)
	* OTG
	* GPU
	* Sound (Speaker,Headphones)
	* Vibrator
	* Battery 3000mah (stock table)
	* Flashlight
	* Camera (s5k3m2_mipi_raw, s5k3m2_2nd_mipi_raw, ov5670_mipi_raw, ov5670_2nd_mipi_raw, ov5670_2nd_flt_mipi_raw)
	* Lens (DF9761BAF)
    * MAGNETOMETER (AKM09911)

* Don't work:
  * IR Blaster (not tested/not sure if works)
  * cw2015 (missing/not working driver, need reversion)
  * Magnetometer (YAS537)(missing/not working driver, need reversion)
  * Alsps (STK3X1X)(missing/not working driver, need reversion)
  * ?
  
# BUILD (WARNING! PLEASE READ CAREFULLY!)
export TOP=$(pwd) <br>
export CROSS_COMPILE=/home/(your username)/(toolchain folder name)/bin/aarch64-linux-android- <br>
mkdir -p $TOP/KERNEL_OBJ <br>
make -C kernel-3.10 O=$TOP/KERNEL_OBJ ARCH=arm64 MTK_TARGET_PROJECT=hermes TARGET_BUILD_VARIANT=user CROSS_COMPILE=$TOOLCHAIN ROOTDIR=$TOP hermes_defconfig <br>
make -C kernel-3.10 O=$TOP/KERNEL_OBJ ROOTDIR=$TOP <br>

# I2C

* I2C0
	* TPS65132              (003e)
	* KD_CAMERA_HW          (007f)
	* DF9761BAF             (0018) - LENS
	* CAM_CAL_DRV           (0036)

* I2C1
	* DA9210                (0068)
	* TPS6128x              (0075)

* I2C2
	* ATMEL                 (004a)
	* KD_CAMERA_HW_BUS_2    (007f)
	* FT			(0038)

* I2C3
	* AKM0991               (000c)
	* YAS537                (002e)
	* LSM6DS3_ACCEL         (006a)
	* LTR_559ALS		(0023)
	* LSM6DS3_GYRO		(0034)
	* STK3X1X               (0048)
	* BMI160_GYRO		(0066)
	* BMI160_ACC		(0068)
	* Step_couneter(BMI160_STC)		(007a)

* I2C4
	* CW2015 		(0062)

# AUTORS
* nofearnohappy
* LazyC0DEr
* Anomalchik
* Dinolek
