# Instructions

- Following Playwright test failed.
- Explain why, be concise, respect Playwright best practices.
- Provide a snippet of code with the fix, if possible.

# Test info

- Name: HMS_04.3.spec.js >> DOCTOR AUTHENTICATED SCRIPTS >> HMS_TS_15 Verify patient's details are visible when entered in Search
- Location: tests\HMS_04.3.spec.js:430:9

# Error details

```
Error: expect(locator).toBeVisible() failed

Locator: getByRole('row').filter({ hasText: 'Dr. Dortha Davis' }).first()
Expected: visible
Timeout: 5000ms
Error: element(s) not found

Call log:
  - Expect "toBeVisible" getByRole('row').filter({ hasText: 'Dr. Dortha Davis' }).first() with timeout 5000ms
  - waiting for getByRole('row').filter({ hasText: 'Dr. Dortha Davis' }).first()

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
- heading "Result against \"Dr. Dortha Davis\" keyword" [level=4]
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
  409 |         await mng_patient.mng_eye_icon.click()
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
> 435 |         await expect(page.getByRole("row").filter({hasText:`${pdname}`}).first()).toBeVisible()
      |                                                                                   ^ Error: expect(locator).toBeVisible() failed
  436 | 
  437 |     })
  438 | })
```