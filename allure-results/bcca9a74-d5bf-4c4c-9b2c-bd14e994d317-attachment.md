# Instructions

- Following Playwright test failed.
- Explain why, be concise, respect Playwright best practices.
- Provide a snippet of code with the fix, if possible.

# Test info

- Name: HMS_04.3.spec.js >> DOCTOR AUTHENTICATED SCRIPTS >> HMS_TS_14 - Verify that medical history can be added for a patient
- Location: tests\HMS_04.3.spec.js:404:9

# Error details

```
Test timeout of 120000ms exceeded.
```

```
Error: locator.click: Test timeout of 120000ms exceeded.
Call log:
  - waiting for getByRole('row').filter({ hasText: 'Icie Senger' }).first().getByRole('link', { name: /View|/ })

```

# Page snapshot

```yaml
- generic [active] [ref=f1e1]:
  - generic [ref=f1e2]:
    - navigation [ref=f1e5]:
      - generic [ref=f1e6]: Main Navigation
      - list [ref=f1e7]:
        - listitem [ref=f1e8]:
          - link " Dashboard" [ref=f1e9] [cursor=pointer]:
            - /url: dashboard.php
            - generic [ref=f1e10]:
              - generic [ref=f1e11]: 
              - generic [ref=f1e13]: Dashboard
        - listitem [ref=f1e14]:
          - link " Appointment History" [ref=f1e15] [cursor=pointer]:
            - /url: appointment-history.php
            - generic [ref=f1e16]:
              - generic [ref=f1e17]: 
              - generic [ref=f1e19]: Appointment History
        - listitem [ref=f1e20]:
          - link " Patients " [ref=f1e21] [cursor=pointer]:
            - /url: javascript:void(0)
            - generic [ref=f1e22]:
              - generic [ref=f1e23]: 
              - generic [ref=f1e25]:
                - text: Patients
                - generic [ref=f1e26]: 
        - listitem [ref=f1e27]:
          - link " Search" [ref=f1e28] [cursor=pointer]:
            - /url: search.php
            - generic [ref=f1e29]:
              - generic [ref=f1e30]: 
              - generic [ref=f1e32]: Search
    - generic [ref=f1e33]:
      - banner [ref=f1e34]:
        - generic [ref=f1e35]:
          - text: 
          - link [ref=f1e36] [cursor=pointer]:
            - /url: "#"
            - heading "HMS" [level=2] [ref=f1e37]
          - link "" [ref=f1e38] [cursor=pointer]:
            - /url: "#"
          - text: 
        - list [ref=f1e41]:
          - listitem [ref=f1e42]:
            - heading "Hospital Management System" [level=2] [ref=f1e43]
          - listitem [ref=f1e44]:
            - link "Rahul Ramachandran " [ref=f1e45] [cursor=pointer]:
              - /url: ""
              - generic [ref=f1e47]:
                - text: Rahul Ramachandran
                - generic [ref=f1e48]: 
      - generic [ref=f1e50]:
        - generic [ref=f1e52]:
          - heading "Doctor | Manage Patients" [level=1] [ref=f1e54]
          - list [ref=f1e55]:
            - listitem [ref=f1e56]: Doctor
            - listitem [ref=f1e57]: / Manage Patients
        - generic [ref=f1e60]:
          - heading "Manage Patients" [level=5] [ref=f1e61]
          - table [ref=f1e62]:
            - rowgroup [ref=f1e63]:
              - row [ref=f1e64]:
                - columnheader "#" [ref=f1e65]
                - columnheader "Patient Name" [ref=f1e66]
                - columnheader "Patient Contact Number" [ref=f1e67]
                - columnheader "Patient Gender" [ref=f1e68]
                - columnheader "Creation Date" [ref=f1e69]
                - columnheader "Updation Date" [ref=f1e70]
                - columnheader "Action" [ref=f1e71]
            - rowgroup [ref=f1e72]:
              - row [ref=f1e73]:
                - cell "1." [ref=f1e74]
                - cell "Dulqur Salman" [ref=f1e75]
                - cell "8775599884" [ref=f1e76]
                - cell "male" [ref=f1e77]
                - cell "2026-10-26 12:38:21" [ref=f1e78]
                - cell [ref=f1e79]
                - cell [ref=f1e80]:
                  - link "" [ref=f1e81] [cursor=pointer]:
                    - /url: edit-patient.php?editid=7
                  - text: "||"
                  - link "" [ref=f1e83] [cursor=pointer]:
                    - /url: view-patient.php?viewid=7
              - row [ref=f1e85]:
                - cell "2." [ref=f1e86]
                - cell "Mohanlal" [ref=f1e87]
                - cell "8775599884" [ref=f1e88]
                - cell "male" [ref=f1e89]
                - cell "2026-10-26 13:00:11" [ref=f1e90]
                - cell [ref=f1e91]
                - cell [ref=f1e92]:
                  - link "" [ref=f1e93] [cursor=pointer]:
                    - /url: edit-patient.php?editid=8
                  - text: "||"
                  - link "" [ref=f1e95] [cursor=pointer]:
                    - /url: view-patient.php?viewid=8
              - row [ref=f1e97]:
                - cell "3." [ref=f1e98]
                - cell "Unnimukundan" [ref=f1e99]
                - cell "8775599884" [ref=f1e100]
                - cell "male" [ref=f1e101]
                - cell "2026-10-28 16:02:05" [ref=f1e102]
                - cell [ref=f1e103]
                - cell [ref=f1e104]:
                  - link "" [ref=f1e105] [cursor=pointer]:
                    - /url: edit-patient.php?editid=9
                  - text: "||"
                  - link "" [ref=f1e107] [cursor=pointer]:
                    - /url: view-patient.php?viewid=9
              - row [ref=f1e109]:
                - cell "4." [ref=f1e110]
                - cell "Unnimukundan" [ref=f1e111]
                - cell "8775599884" [ref=f1e112]
                - cell "male" [ref=f1e113]
                - cell "2026-10-29 11:00:55" [ref=f1e114]
                - cell [ref=f1e115]
                - cell [ref=f1e116]:
                  - link "" [ref=f1e117] [cursor=pointer]:
                    - /url: edit-patient.php?editid=10
                  - text: "||"
                  - link "" [ref=f1e119] [cursor=pointer]:
                    - /url: view-patient.php?viewid=10
              - row [ref=f1e121]:
                - cell "5." [ref=f1e122]
                - cell "Unnimukundan" [ref=f1e123]
                - cell "8775599884" [ref=f1e124]
                - cell "male" [ref=f1e125]
                - cell "2026-10-29 11:10:19" [ref=f1e126]
                - cell [ref=f1e127]
                - cell [ref=f1e128]:
                  - link "" [ref=f1e129] [cursor=pointer]:
                    - /url: edit-patient.php?editid=11
                  - text: "||"
                  - link "" [ref=f1e131] [cursor=pointer]:
                    - /url: view-patient.php?viewid=11
              - row [ref=f1e133]:
                - cell "6." [ref=f1e134]
                - cell "Unnimukundan" [ref=f1e135]
                - cell "8775599884" [ref=f1e136]
                - cell "male" [ref=f1e137]
                - cell "2026-10-29 11:12:17" [ref=f1e138]
                - cell [ref=f1e139]
                - cell [ref=f1e140]:
                  - link "" [ref=f1e141] [cursor=pointer]:
                    - /url: edit-patient.php?editid=12
                  - text: "||"
                  - link "" [ref=f1e143] [cursor=pointer]:
                    - /url: view-patient.php?viewid=12
              - row [ref=f1e145]:
                - cell "7." [ref=f1e146]
                - cell "Unnimukundan" [ref=f1e147]
                - cell "8775599884" [ref=f1e148]
                - cell "male" [ref=f1e149]
                - cell "2026-10-29 11:38:20" [ref=f1e150]
                - cell [ref=f1e151]
                - cell [ref=f1e152]:
                  - link "" [ref=f1e153] [cursor=pointer]:
                    - /url: edit-patient.php?editid=13
                  - text: "||"
                  - link "" [ref=f1e155] [cursor=pointer]:
                    - /url: view-patient.php?viewid=13
              - row [ref=f1e157]:
                - cell "8." [ref=f1e158]
                - cell "Unnimukundan" [ref=f1e159]
                - cell "8775599884" [ref=f1e160]
                - cell "male" [ref=f1e161]
                - cell "2026-10-29 12:00:51" [ref=f1e162]
                - cell [ref=f1e163]
                - cell [ref=f1e164]:
                  - link "" [ref=f1e165] [cursor=pointer]:
                    - /url: edit-patient.php?editid=14
                  - text: "||"
                  - link "" [ref=f1e167] [cursor=pointer]:
                    - /url: view-patient.php?viewid=14
              - row [ref=f1e169]:
                - cell "9." [ref=f1e170]
                - cell "Steven Nader" [ref=f1e171]
                - cell "8775599884" [ref=f1e172]
                - cell "male" [ref=f1e173]
                - cell "2026-10-29 12:15:21" [ref=f1e174]
                - cell [ref=f1e175]
                - cell [ref=f1e176]:
                  - link "" [ref=f1e177] [cursor=pointer]:
                    - /url: edit-patient.php?editid=15
                  - text: "||"
                  - link "" [ref=f1e179] [cursor=pointer]:
                    - /url: view-patient.php?viewid=15
              - row [ref=f1e181]:
                - cell "10." [ref=f1e182]
                - cell "Reagan Hayes" [ref=f1e183]
                - cell "8775599884" [ref=f1e184]
                - cell "male" [ref=f1e185]
                - cell "2026-10-29 12:54:43" [ref=f1e186]
                - cell [ref=f1e187]
                - cell [ref=f1e188]:
                  - link "" [ref=f1e189] [cursor=pointer]:
                    - /url: edit-patient.php?editid=16
                  - text: "||"
                  - link "" [ref=f1e191] [cursor=pointer]:
                    - /url: view-patient.php?viewid=16
              - row [ref=f1e193]:
                - cell "11." [ref=f1e194]
                - cell "Rebeka Abbott" [ref=f1e195]
                - cell "8775599884" [ref=f1e196]
                - cell "male" [ref=f1e197]
                - cell "2026-10-29 13:11:34" [ref=f1e198]
                - cell [ref=f1e199]
                - cell [ref=f1e200]:
                  - link "" [ref=f1e201] [cursor=pointer]:
                    - /url: edit-patient.php?editid=17
                  - text: "||"
                  - link "" [ref=f1e203] [cursor=pointer]:
                    - /url: view-patient.php?viewid=17
              - row [ref=f1e205]:
                - cell "12." [ref=f1e206]
                - cell "Danyka Nader V" [ref=f1e207]
                - cell "8775599884" [ref=f1e208]
                - cell "male" [ref=f1e209]
                - cell "2026-10-29 13:24:09" [ref=f1e210]
                - cell [ref=f1e211]
                - cell [ref=f1e212]:
                  - link "" [ref=f1e213] [cursor=pointer]:
                    - /url: edit-patient.php?editid=18
                  - text: "||"
                  - link "" [ref=f1e215] [cursor=pointer]:
                    - /url: view-patient.php?viewid=18
              - row [ref=f1e217]:
                - cell "13." [ref=f1e218]
                - cell "Furman Kuphal" [ref=f1e219]
                - cell "8775599884" [ref=f1e220]
                - cell "male" [ref=f1e221]
                - cell "2026-10-30 14:56:50" [ref=f1e222]
                - cell [ref=f1e223]
                - cell [ref=f1e224]:
                  - link "" [ref=f1e225] [cursor=pointer]:
                    - /url: edit-patient.php?editid=19
                  - text: "||"
                  - link "" [ref=f1e227] [cursor=pointer]:
                    - /url: view-patient.php?viewid=19
              - row [ref=f1e229]:
                - cell "14." [ref=f1e230]
                - cell "Lurline Mayert DVM" [ref=f1e231]
                - cell "8775599884" [ref=f1e232]
                - cell "male" [ref=f1e233]
                - cell "2026-10-30 16:12:23" [ref=f1e234]
                - cell [ref=f1e235]
                - cell [ref=f1e236]:
                  - link "" [ref=f1e237] [cursor=pointer]:
                    - /url: edit-patient.php?editid=20
                  - text: "||"
                  - link "" [ref=f1e239] [cursor=pointer]:
                    - /url: view-patient.php?viewid=20
              - row [ref=f1e241]:
                - cell "15." [ref=f1e242]
                - cell "Mr. Holden Mosciski-Hahn III" [ref=f1e243]
                - cell "8775599884" [ref=f1e244]
                - cell "male" [ref=f1e245]
                - cell "2026-10-30 16:33:09" [ref=f1e246]
                - cell [ref=f1e247]
                - cell [ref=f1e248]:
                  - link "" [ref=f1e249] [cursor=pointer]:
                    - /url: edit-patient.php?editid=21
                  - text: "||"
                  - link "" [ref=f1e251] [cursor=pointer]:
                    - /url: view-patient.php?viewid=21
              - row [ref=f1e253]:
                - cell "16." [ref=f1e254]
                - cell "Mr. Ephraim Krajcik" [ref=f1e255]
                - cell "8775599884" [ref=f1e256]
                - cell "male" [ref=f1e257]
                - cell "2026-10-30 16:52:37" [ref=f1e258]
                - cell [ref=f1e259]
                - cell [ref=f1e260]:
                  - link "" [ref=f1e261] [cursor=pointer]:
                    - /url: edit-patient.php?editid=22
                  - text: "||"
                  - link "" [ref=f1e263] [cursor=pointer]:
                    - /url: view-patient.php?viewid=22
              - row [ref=f1e265]:
                - cell "17." [ref=f1e266]
                - cell "Penny Feest DDS" [ref=f1e267]
                - cell "8775599884" [ref=f1e268]
                - cell "male" [ref=f1e269]
                - cell "2026-10-30 17:12:58" [ref=f1e270]
                - cell [ref=f1e271]
                - cell [ref=f1e272]:
                  - link "" [ref=f1e273] [cursor=pointer]:
                    - /url: edit-patient.php?editid=23
                  - text: "||"
                  - link "" [ref=f1e275] [cursor=pointer]:
                    - /url: view-patient.php?viewid=23
              - row [ref=f1e277]:
                - cell "18." [ref=f1e278]
                - cell "Junius Hagenes" [ref=f1e279]
                - cell "8775599884" [ref=f1e280]
                - cell "male" [ref=f1e281]
                - cell "2026-10-30 17:45:24" [ref=f1e282]
                - cell [ref=f1e283]
                - cell [ref=f1e284]:
                  - link "" [ref=f1e285] [cursor=pointer]:
                    - /url: edit-patient.php?editid=24
                  - text: "||"
                  - link "" [ref=f1e287] [cursor=pointer]:
                    - /url: view-patient.php?viewid=24
              - row [ref=f1e289]:
                - cell "19." [ref=f1e290]
                - cell "Humberto Klocko" [ref=f1e291]
                - cell "8775599884" [ref=f1e292]
                - cell "male" [ref=f1e293]
                - cell "2026-11-05 10:49:07" [ref=f1e294]
                - cell [ref=f1e295]
                - cell [ref=f1e296]:
                  - link "" [ref=f1e297] [cursor=pointer]:
                    - /url: edit-patient.php?editid=25
                  - text: "||"
                  - link "" [ref=f1e299] [cursor=pointer]:
                    - /url: view-patient.php?viewid=25
  - contentinfo:
    - generic:
      - generic [ref=f1e301]: Hospital Management System
      - generic [ref=f1e302]: 
  - generic [ref=f1e305]:
    - button "" [ref=f1e306] [cursor=pointer]
    - generic [ref=f1e308]: Style Selector
    - generic [ref=f1e309]:
      - generic [ref=f1e310]:
        - generic [ref=f1e311]: Fixed header
        - generic [ref=f1e313] [cursor=pointer]
      - generic [ref=f1e315]:
        - generic [ref=f1e316]: Fixed sidebar
        - generic [ref=f1e318] [cursor=pointer]
      - generic [ref=f1e320]:
        - generic [ref=f1e321]: Closed sidebar
        - generic [ref=f1e323] [cursor=pointer]
      - generic [ref=f1e325]:
        - generic [ref=f1e326]: Fixed footer
        - generic [ref=f1e328] [cursor=pointer]
      - generic [ref=f1e330]:
        - generic [ref=f1e331]: 
        - generic [ref=f1e342]: 
      - generic [ref=f1e353]:
        - generic [ref=f1e354]: 
        - generic [ref=f1e365]: 
      - generic [ref=f1e376]:
        - generic [ref=f1e377]: 
        - generic [ref=f1e388]: 
```

# Test source

```ts
  309 |         const patientLogin = new patientLog(loggedInPatient)
  310 |         const BASE_URL ="http://49.249.29.4:8081/TestServer/Build/Hospital_Doctor_Patient_Management_System/";
  311 | 
  312 |         await expect(patientLogin.heading).toHaveText("User | Dashboard");
  313 | 
  314 |         // Open the account dropdown
  315 |         await patientLogin.profile_dropdown.click();
  316 | 
  317 |         // Uses a valid CSS selector instead of the broken POM locator
  318 |         await loggedInPatient.locator('a[href="logout.php"]').click();
  319 |         await expect(loggedInPatient).toHaveURL(`${BASE_URL}index.php`);
  320 | 
  321 |         // Attempt to access the dashboard after logout
  322 |         await loggedInPatient.goto(`${BASE_URL}hms/dashboard.php`);
  323 | 
  324 |         // A protected page should not remain accessible
  325 |         await expect(loggedInPatient).not.toHaveURL(/dashboard\.php/);
  326 |     })
  327 | 
  328 |     test("HMS_TS_11 - Login as Doctor with valid credentials and verify dashboard", async({browser})=>{
  329 |         const {context,page} = await openDoctorLogin(browser)
  330 |         const drLoginPage = new doctorLogin(page)
  331 | 
  332 |         await drLoginPage.DoctorLoginProcess(process.env.DOCTOR_1_EMAIL?.trim(),process.env.DOCTOR_1_PWD?.trim())
  333 |         await expect(drLoginPage.heading).toHaveText("Doctor | Dashboard")
  334 |         await expect(page.getByRole('heading', { name: 'My Profile' })).toBeVisible();
  335 |         await expect(page.getByText("My Appointments", { exact: true })).toBeVisible();
  336 |         await context.close();
  337 |     })
  338 | 
  339 | 
  340 |     test("HMS_TS_12 - Verify a new Patient's Doctor appointment in Doctor's Appointment history",{tag:'@failed1'}, async ({ browser }) => {
  341 |         test.setTimeout(240000);
  342 | 
  343 |         const { context, page } = await openPatientLogin(browser);
  344 |         const result = await registerNewPatient(page);
  345 | 
  346 |         expect(result.message).toBe("Successfully Registered. You can login now");
  347 |         
  348 |         await result.patientRegister.re_login.click();
  349 |         const patientLogin = await loginPatient(page, result.email, result.password);
  350 |         await expect(patientLogin.heading).toHaveText("User | Dashboard");
  351 | 
  352 |         const patientAppointment = new appointment(page);
  353 |         const message = await patientAppointment.appointment_booking(
  354 |             "Radiology",
  355 |             "Rahul Ramachandran",
  356 |             "2026-12-15",
  357 |             "10:00 AM"
  358 |         );
  359 |         expect(message).toBe("Your appointment successfully booked");
  360 | 
  361 |         const { context: context2, page: page2 } = await openDoctorLogin(browser);
  362 | 
  363 |         const drLoginPage = new doctorLogin(page2);
  364 |         await drLoginPage.DoctorLoginProcess(
  365 |             process.env.DOCTOR_2_EMAIL,
  366 |             process.env.DOCTOR_2_PWD
  367 |         );
  368 | 
  369 |         await drLoginPage.aptHistory.click();
  370 |         await expect(page2.locator(`//td[@class="hidden-xs" and normalize-space()="${result.name}"]`)).toBeVisible();
  371 | 
  372 |         await context.close();
  373 |         await context2.close();
  374 |     });
  375 | 
  376 | })
  377 | 
  378 | 
  379 | test.describe("DOCTOR AUTHENTICATED SCRIPTS",()=>{
  380 |     test.use({ storageState:'.auth/user.json'});
  381 |     test.setTimeout(120000);
  382 |     test("HMS_TS_13 - Add a Patient and Verify patient is added in Manage Patients",{tag:'@failed2'},async({page})=>{
  383 | 
  384 |         await page.goto(
  385 |             'http://49.249.29.4:8081/TestServer/Build/Hospital_Doctor_Patient_Management_System/hms/doctor/dashboard.php'
  386 |         );
  387 |         await expect(page.getByText("Doctor | Dashboard")).toBeVisible();
  388 | 
  389 |         const doctor_patient = new Doctor_Patient(page)
  390 |         const email = uniqueEmail2()
  391 | 
  392 |         await doctor_patient.add_patient(
  393 |             pdname_actual,
  394 |             patient_data.age,
  395 |             patient_data.phno,
  396 |             patient_data.address,
  397 |             patient_data.med_hist,
  398 |             email
  399 |         )
  400 |         await doctor_patient.manage_patient()
  401 |         await expect(page.locator(`//td[@class="hidden-xs" and normalize-space()="${pdname}"]`).first()).toBeVisible()
  402 |     })
  403 | 
  404 |     test("HMS_TS_14 - Verify that medical history can be added for a patient",{tag:'@failed2'},async({page})=>{
  405 |         await page.goto('http://49.249.29.4:8081/TestServer/Build/Hospital_Doctor_Patient_Management_System/hms/doctor/dashboard.php');
  406 |         let mng_patient = new Doctor_Patient(page,pdname_actual)
  407 |         await mng_patient.patient_link.click()
  408 |         await mng_patient.manage_patient_link.click()
> 409 |         await mng_patient.mng_eye_icon.click()
      |                                        ^ Error: locator.click: Test timeout of 120000ms exceeded.
  410 |         await expect(mng_patient.table_heading).toBeVisible()
  411 |         await expect(mng_patient.med_hist_heading).toBeVisible()
  412 | 
  413 |         await mng_patient.add_med_hist_btn.click()
  414 |         const mdialog = page.locator('#myModal').first()
  415 |         await mdialog.getByPlaceholder("Blood Pressure").fill(medhistory.patient_bp)
  416 |         await mdialog.getByPlaceholder("Blood Sugar").first().fill(medhistory.patient_sugar)
  417 |         await mdialog.getByPlaceholder("Weight").fill(medhistory.patient_weight)
  418 |         await mdialog.locator('input[name="temp"]').fill(medhistory.patient_temp)
  419 |         await mdialog.getByPlaceholder("Medical Prescription").fill(medhistory.prescription)
  420 | 
  421 |         const message = await withAcceptedDialog(
  422 |             page,
  423 |             () => mdialog.locator('button[name="submit"]').click()
  424 |         );
  425 |         
  426 |         expect(message).toBe("Medicle history has been added.");
  427 |         
  428 |     })
  429 | 
  430 |     test("HMS_TS_15 Verify patient's details are visible when entered in Search",{tag:'@failed2'},async({page})=>{
  431 |         await page.goto('http://49.249.29.4:8081/TestServer/Build/Hospital_Doctor_Patient_Management_System/hms/doctor/dashboard.php');
  432 |         let dr_dashboard = new doctorLogin(page)
  433 |         await dr_dashboard.SearchPatient(pdname_actual)
  434 |         await page.waitForTimeout(2000)
  435 |         await expect(page.getByRole("row").filter({hasText:`${pdname}`}).first()).toBeVisible()
  436 | 
  437 |     })
  438 | })
```