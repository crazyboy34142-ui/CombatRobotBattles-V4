# Combat Robot Battles V4.2 (3D Combat POV)

195 country robots, ek arena, ek last robot standing. 2D engine + Three.js 3D robot POV, sab `www/index.html` mein.

## V4.2 mein kya naya hai
- **Head-mounted POV**: camera robot ke sir se, head body se alag ghoomta hai (target ki taraf, warna idhar-udhar scan), walking bob + turn roll.
- **Apne haath + weapon first-person mein dikhte hain** (left = pulse cannon, right = country ka melee weapon), alag render pass, recoil/swing animation ke saath.
- **Humanoid robots**: joints (shoulder/elbow/knee), armour plates, 8 weapon models. Paas ke ~10 robots detailed, baaki cheap LOD (195 robots ke liye).
- **Combat**: robots projectile fire karte hain, HP + armour, hit flash, knockback, body-slam/melee damage, explosion on destroy, death-cam.
- **HP bars**: 3D mein sar ke upar, 2D arena mein (<=60 robots), POV HUD mein HP/armour/weapon.
- **Bug fix**: 3D mein koi exception aaye to game freeze hota tha (`requestAnimationFrame` render ke baad lagta tha). Ab 3D fail ho to automatic 2D chase-cam, game chalta rehta hai. WebGL context loss bhi handle.
- Settings: **Lethal HP combat** (EXPERIMENTAL). Off = HP sirf show-combat hai, elimination purane mode (Auto KO etc.) se hi hoti hai. On = 0 HP par robot destroy.

## Run (browser)
```bash
npm install        # three.module.js ko www/lib me copy karta hai (offline 3D)
npm run serve      # http://localhost:8080
```
Seedha `www/index.html` kholne par Three.js CDN se load hota hai (internet chahiye); file:// par module import browser block kar sakta hai, server se chalao.

## Android APK
```bash
npm install
npx cap add android
npm run sync
npx cap open android
```
`capacitor.config.json` mein `androidScheme: https` hai taaki module import + localStorage theek chale.

## Known limits
- Poora battle engine abhi bhi 2D physics hai; 3D uska POV view hai (overlay canvas).
- Lethal HP mode untuned hai (195 robots mein round bahut tez khatam hoga).
- API keys repo mein mat daalo; Settings mein app ke andar daalo.

## API keys (private)
`www/keys.js` mein YouTube Data API key, ElevenLabs key aur Channel ID bhar do; app start par apne aap Settings mein aa jati hain.
Ye file `.gitignore` mein hai, GitHub par nahi jayegi. Dhyan: `npx cap sync` se ye file APK ke andar bhi chali jati hai, isliye APK public share mat karo.
