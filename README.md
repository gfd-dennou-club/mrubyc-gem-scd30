# mrubyc-gem-scd30
mruby/c sources for scd30 (CO2 sensor)

## デバイス

データシート
https://media.digikey.com/pdf/Data%20Sheets/Sensirion%20PDFs/CD_AN_SCD30_Interface_Description_D1.pdf

## 参考
Arduino/libraries/Adafruit_SCD30/Adafruit_SCD30.cpp

## sample 
```
#I2C 初期化
i2c = I2C.new(22, 21)

sleep(1)

# CO2センサ初期化
scd30 = SCD30.new(i2c)
sleep(1)

# 観測
loop do
  if scd30.dataReady
    var = scd30.read
    if var
      puts "CO2         : #{var[0]} ppm"
      puts "Temperature : #{var[1]} C"
      puts "Humidity    : #{var[2]} %"
    end
  end

  sleep( 0.5 )
end
```
