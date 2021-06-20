Security Checklist
Kube Security
  - [ ] 1. อย่า Run Docker โดย root user
  - [ ] 2. ควรจะใช้ package docker file ที่เราจะใช้เท่านั้น
  - [ ] 3. Node ควรจะ allow port สำหรับที่จะใช้เท่านั้น
  - [ ] 4. ควรกำหนด Network policy ให้ Pod สามารถคุยกันได้เฉพาะ ที่จะใช้เท่านั้น
  - [ ]5. set policy agent pod ให้ Deployment deploy only namespace ที่ pod สามารถ deploy ได้เท่านั้น
  - [ ] 6. service account pod ควร สิทธิ์ เฉพาะที่ pod นั้นใช้เท่านั้น
  - [ ]7. Image ควรใช้ Private Registry
  - [ ] 8. Pod ตัวไหน ที่ไม่ได้ใช้ API ของ Cloud ไม่ควร access API ของ Cloud ได้ (Metadata consealing)
  - [ ] 9. ห้ามเก็บ Password ที่อยู่ใน App ควรอยู่ใน Secret manager
  - [ ] 10. Scan image ที่เรา Build เป็นประจำ
  - [ ] 11. แบ่งสิทธิ์ ในการใช้ Kubectl ให้ access only namespace
  - [ ] 12. worker node ไม่ควรเปิด SSH ให้ผ่าน Kubectl เท่านั้น
  - [ ] 13. Kube cluster ควรอยู่ใน Private network เท่านั้น ให้ set ผ่าน LB เท่านั้น

Api Security

- [ ] 1. ทุก Api ควรมี AccessKeys
- [ ] 2. Api ควร enable oauth2
- [ ] 3. ไม่ควรนำข้อมูล เกี่ยวกับ User Profile ส่วนตัวไว้ใน JWT
- [ ] 4. Api ทุกตัว ควร Enable HSTS
- [ ] 5. Api ใช้ port ไหน allow port นั้น
- [ ] 6. ให้ทุก API ผ่าน LB เท่านั้น เพราะ LB ใส่ firewall ได้ แล้ว ไม่ควรใช้ Port เดี่ยวกับ port API
- [ ] 7. Api แยก ENV ชัดเจน ไม่ควร test บน Production เช่น Dev, SIT, UAT, PROD, PROD Support, Perf Test, Perf Test on cloud
- [ ] 8. User ที่เข้ามาใช้งาน API ควรมี สิทธิ์ไม่เท่ากัน กำหนด By Route
- [ ] 9. เช็คสิทธิ์ Api ทุกเส้น ว่า user นั้นมี สิทธิ์เข้าถึงไหม
- [ ] 10. JWT ควร Encode ด้วย RSA(Asymmetric key) ทำ Secret
- [ ] 11. Refresh token ควรเก็บไว้ใน DB หรือใน Redis ด้วย เพื่อที่จะสามารถ Revoke ได้
- [ ] 12. Logout ออกจากระบบ ควรลบ Refresh token และ Token ออกจาก DB ด้วย
- [ ] 13. Set X-Forwarded-for ที่ LB เพื่อเก็บ Log User IP ไว้ด้วย เมื่อ login
- [ ] 14. ปิด Debug mode
- [ ] 15. ไม่ควรใช้ Phpmyadmin
- [ ] 16. ทุก API ที่ต่อ Database ควร close session ด้วย

