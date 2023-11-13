const puppeteer = require("puppeteer")

let browser, page
let nameOutputText,
  emailOutputText,
  currentAddressOutputText,
  permanentAddressOutputText

beforeAll(async () => {
  browser = await puppeteer.launch({
    executablePath:
      "C:/Program Files (x86)/Google/Chrome/Application/chrome.exe",
    headless: "false",
  })
  page = await browser.newPage()

  await page.goto("https://demoqa.com/text-box")

  await page.type("#userName", "John Doe")
  await page.type("#userEmail", "john.doe@example.com")
  await page.type("#currentAddress", "Street Main 123")
  await page.type("#permanentAddress", "123 Main Street")

  await page.click("#submit")

  await page.waitForTimeout(1000)

  nameOutputText = await page.$eval("#name", (output) => output.textContent)

  emailOutputText = await page.$eval("#email", (output) => output.textContent)

  currentAddressOutputText = await page.$eval(
    "p#currentAddress",
    (output) => output.textContent
  )

  permanentAddressOutputText = await page.$eval(
    "p#permanentAddress",
    (output) => output.textContent
  )
}, 10000)

test("Check Full Name", () => {
  expect(nameOutputText).toBe("Name:John Doe")
})
test("Check Email", () => {
  expect(emailOutputText).toBe("Email:john.doe@example.com")
})
test("Check Current Address", () => {
  expect(currentAddressOutputText).toBe("Current Address :Street Main 123 ")
})
test("Check Permanent Address", () => {
  expect(permanentAddressOutputText).toBe("Permananet Address :123 Main Street")
})

afterAll(async () => {
  await browser.close()
})
