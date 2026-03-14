# Scripting

This is a basic script to assign incrementing cable numbers. It is written in JavaScript but you can use any programming language you want to interact with the API.

More demo scripts are available [here](https://github.com/jan-ldwg/site_manager_demo_scripts)

```js title="generateCableNumbers.js"
import "dotenv/config";

const API_URL = process.env.API_URL ?? "http://localhost:5056/api";

//before we can do anything with the API we need to login
export const login = async () => {
  const res = await fetch(`${process.env.API_URL}/auth/sign-in/email`, {
    method: "POST",
    headers: {
      "Content-Type": "application/json",
    },
    body: JSON.stringify({
      email: process.env.EMAIL,
      password: process.env.PASSWORD,
    }),
  });

  if (!res.ok) {
    throw new Error("Failed to login");
  }

  // We need to save the cookie for all subsequent requests
  const cookie = res.headers.get("set-cookie");
  if (!cookie) {
    throw new Error("No cookie returned from login");
  }

  return cookie;
};

//see the API documentation for all available endpoints, methods and expected responses
async function getCables() {
  const res = await fetch(`${API_URL}/cables`, {
    headers: {
      Cookie: cookie,
    },
  });

  if (!res.ok) {
    throw new Error(`Failed to fetch cables: ${res.status}`);
  }

  const cables = await res.json();
  return cables;
}

//small util to get numbers to fixed length
function padNumber(number, length) {
  let r = "" + number;
  while (r.length < length) {
    r = "0" + r;
  }
  return r;
}

async function setCableNumber(id, number) {
  const res = await fetch(`${API_URL}/cables/${id}`, {
    //dont forget the Content-Type or else the server will ignore the body!
    headers: { Cookie: cookie, "Content-Type": "application/json" },
    method: "PATCH",
    body: JSON.stringify({
      number: number,
    }),
  });

  if (!res.ok) {
    throw new Error(`Failed to update cable '${id}'`);
  }
}

let cookie = "";

async function main() {
  let index = 1;
  try {
    cookie = await login();
    const cables = await getCables();

    for (const cable of cables) {
      if (!cable.number) {
        await setCableNumber(cable.id, `x${padNumber(index, 5)}`);
        index += 1;
      }
    }
  } catch (err) {
    console.error(err);
    process.exit(1);
  }
}

main();
```
