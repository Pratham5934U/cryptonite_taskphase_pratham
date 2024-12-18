## Solution 

1. I used `zsteg` I got some text `ZIT HQZI OL GWLEXKTR, WXZ ZIT ZKXZI SOTL OF ZIT LIQRGVL. LTTA ZIT HQZZTKFL...` 
2. Then I used base64 decoder i got `dA,erEed)vHH8VHLDeK-4dAS(R` 
3. Then I also tried URL Analysis on the hidden string  `izzhl://woz.sn/yktqatlztof0` in the metadata because it looked like a url it did not result in 
   anything
4. Then I used `binwalk` and found that image had a `Zlib compressed data`, I extracted it and decompressed it after that I oped it in bless but after that I had no clue to what to do
