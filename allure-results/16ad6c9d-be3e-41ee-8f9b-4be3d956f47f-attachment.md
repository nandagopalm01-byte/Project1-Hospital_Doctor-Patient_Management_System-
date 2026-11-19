# Instructions

- Following Playwright test failed.
- Explain why, be concise, respect Playwright best practices.
- Provide a snippet of code with the fix, if possible.

# Test info

- Name: HMS_04.3.spec.js >> DOCTOR AUTHENTICATED SCRIPTS >> HMS_TS_15 Verify patient's details are visible when entered in Search
- Location: tests\HMS_04.3.spec.js:428:9

# Error details

```
Error: expect(locator).toBeVisible() failed

Locator: getByRole('row').filter({ hasText: 'Sam Kuphal-Kulas' }).first()
Expected: visible
Timeout: 5000ms
Error: element(s) not found

Call log:
  - Expect "toBeVisible" getByRole('row').filter({ hasText: 'Sam Kuphal-Kulas' }).first() with timeout 5000ms
  - waiting for getByRole('row').filter({ hasText: 'Sam Kuphal-Kulas' }).first()

```

```yaml
- navigation:
  - text: Main Navigation
  - list:
    - listitem:
      - link " Dashboard":
        - /url: dashboard.php
    - listitem:
      - link " Appointment History":
        - /url: appointment-history.php
    - listitem:
      - link " Patients ":
        - /url: javascript:void(0)
    - listitem:
      - link " Search":
        - /url: search.php
- banner:
  - link "HMS":
    - /url: "#"
    - heading "HMS" [level=2]
  - link "":
    - /url: "#"
  - list:
    - listitem:
      - heading "Hospital Management System" [level=2]
    - listitem:
      - link "Rahul Ramachandran ":
        - /url: ""
        - img
        - text: Rahul Ramachandran 
- heading "Doctor | Manage Patients" [level=1]
- list:
  - listitem: Doctor
  - listitem: / Manage Patients
- form:
  - text: Search by Name/Mobile No.
  - textbox
  - button "Search"
- heading "Result against \"Sam Kuphal-Kulas\" keyword" [level=4]
- table:
  - rowgroup:
    - row "# Patient Name Patient Contact Number Patient Gender Creation Date Updation Date Action":
      - columnheader "#"
      - columnheader "Patient Name"
      - columnheader "Patient Contact Number"
      - columnheader "Patient Gender"
      - columnheader "Creation Date"
      - columnheader "Updation Date"
      - columnheader "Action"
  - rowgroup:
    - row "No record found against this search":
      - cell "No record found against this search"
- contentinfo: Hospital Management System 
- button ""
- text: Style Selector Fixed header Fixed sidebar Closed sidebar Fixed footer      
```

# Test source

```ts
  332 |         await expect(page.getByRole('heading', { name: 'My Profile' })).toBeVisible();
  333 |         await expect(page.getByText("My Appointments", { exact: true })).toBeVisible();
  334 |         await context.close();
  335 |     })
  336 | 
  337 | 
  338 |     test("HMS_TS_12 - Verify a new Patient's Doctor appointment in Doctor's Appointment history",{tag:'@failed1'}, async ({ browser }) => {
  339 |         test.setTimeout(240000);
  340 | 
  341 |         const { context, page } = await openPatientLogin(browser);
  342 |         const result = await registerNewPatient(page);
  343 | 
  344 |         expect(result.message).toBe("Successfully Registered. You can login now");
  345 |         
  346 |         await result.patientRegister.re_login.click();
  347 |         const patientLogin = await loginPatient(page, result.email, result.password);
  348 |         await expect(patientLogin.heading).toHaveText("User | Dashboard");
  349 | 
  350 |         const patientAppointment = new appointment(page);
  351 |         const message = await patientAppointment.appointment_booking(
  352 |             "Radiology",
  353 |             "Rahul Ramachandran",
  354 |             "2026-12-15",
  355 |             "10:00 AM"
  356 |         );
  357 |         expect(message).toBe("Your appointment successfully booked");
  358 | 
  359 |         const { context: context2, page: page2 } = await openDoctorLogin(browser);
  360 | 
  361 |         const drLoginPage = new doctorLogin(page2);
  362 |         await drLoginPage.DoctorLoginProcess(
  363 |             process.env.DOCTOR_2_EMAIL,
  364 |             process.env.DOCTOR_2_PWD
  365 |         );
  366 | 
  367 |         await drLoginPage.aptHistory.click();
  368 |         await expect(page2.locator(`//td[@class="hidden-xs" and normalize-space()="${result.name}"]`)).toBeVisible();
  369 | 
  370 |         await context.close();
  371 |         await context2.close();
  372 |     });
  373 | 
  374 | })
  375 | 
  376 | 
  377 | test.describe("DOCTOR AUTHENTICATED SCRIPTS",()=>{
  378 |     test.use({ storageState:'.auth/user.json'});
  379 |     test.setTimeout(120000);
  380 |     test("HMS_TS_13 - Add a Patient and Verify patient is added in Manage Patients",{tag:'@failed2'},async({page})=>{
  381 | 
  382 |         await page.goto(
  383 |             'http://49.249.29.4:8081/TestServer/Build/Hospital_Doctor_Patient_Management_System/hms/doctor/dashboard.php'
  384 |         );
  385 |         await expect(page.getByText("Doctor | Dashboard")).toBeVisible();
  386 | 
  387 |         const doctor_patient = new Doctor_Patient(page)
  388 |         const email = uniqueEmail2()
  389 | 
  390 |         await doctor_patient.add_patient(
  391 |             pdname,
  392 |             patient_data.age,
  393 |             patient_data.phno,
  394 |             patient_data.address,
  395 |             patient_data.med_hist,
  396 |             email
  397 |         )
  398 |         await doctor_patient.manage_patient()
  399 |         await expect(page.locator(`//td[@class="hidden-xs" and normalize-space()="${pdname}"]`).first()).toBeVisible()
  400 |     })
  401 | 
  402 |     test("HMS_TS_14 - Verify that medical history can be added for a patient",{tag:'@failed2'},async({page})=>{
  403 |         await page.goto('http://49.249.29.4:8081/TestServer/Build/Hospital_Doctor_Patient_Management_System/hms/doctor/dashboard.php');
  404 |         let mng_patient = new Doctor_Patient(page,"Mohanlal")
  405 |         await mng_patient.patient_link.click()
  406 |         await mng_patient.manage_patient_link.click()
  407 |         await mng_patient.mng_eye_icon.click()
  408 |         await expect(mng_patient.table_heading).toBeVisible()
  409 |         await expect(mng_patient.med_hist_heading).toBeVisible()
  410 | 
  411 |         await mng_patient.add_med_hist_btn.click()
  412 |         const mdialog = page.locator('#myModal').first()
  413 |         await mdialog.getByPlaceholder("Blood Pressure").fill(medhistory.patient_bp)
  414 |         await mdialog.getByPlaceholder("Blood Sugar").first().fill(medhistory.patient_sugar)
  415 |         await mdialog.getByPlaceholder("Weight").fill(medhistory.patient_weight)
  416 |         await mdialog.locator('input[name="temp"]').fill(medhistory.patient_temp)
  417 |         await mdialog.getByPlaceholder("Medical Prescription").fill(medhistory.prescription)
  418 | 
  419 |         const message = await withAcceptedDialog(
  420 |             page,
  421 |             () => mdialog.locator('button[name="submit"]').click()
  422 |         );
  423 |         
  424 |         expect(message).toBe("Medicle history has been added.");
  425 |         
  426 |     })
  427 | 
  428 |     test("HMS_TS_15 Verify patient's details are visible when entered in Search",{tag:'@auth_test3'},async({page})=>{
  429 |         await page.goto('http://49.249.29.4:8081/TestServer/Build/Hospital_Doctor_Patient_Management_System/hms/doctor/dashboard.php');
  430 |         let dr_dashboard = new doctorLogin(page)
  431 |         await dr_dashboard.SearchPatient(pdname)
> 432 |         await expect(page.getByRole("row").filter({hasText:`${pdname}`}).first()).toBeVisible()
      |                                                                                   ^ Error: expect(locator).toBeVisible() failed
  433 | 
  434 |     })
  435 | })
```