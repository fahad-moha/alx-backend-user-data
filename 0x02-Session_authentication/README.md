# Understanding Authentication, Sessions, and Cookies

## What is Authentication?
Authentication is the process of verifying the identity of a user, device, or system. It ensures that the person or entity accessing a system or resource is who they claim to be.

## What is Session Authentication?
Session authentication is a way of managing user authentication that involves a server-side session. When a user logs in, the server creates a session for that user and sends a session token (usually a cookie) to the client. The client then includes this token in subsequent requests, allowing the server to identify the user and maintain their session.

## What are Cookies?
Cookies are small pieces of data that a website stores in the user's web browser. They are used to store information about the user's preferences, browsing history, and session information.

## How to Send Cookies
Cookies are typically sent by the server to the client as part of the HTTP response headers. The `Set-Cookie` header is used to instruct the client to store the cookie.

Example:
```
HTTP/1.1 200 OK
Set-Cookie: session_id=abcd1234; HttpOnly; Secure
```

## How to Parse Cookies
On the client-side, cookies can be accessed and manipulated using JavaScript. The `document.cookie` property returns a string containing all the cookies, which can be parsed and used as needed.

Example:
```javascript
// Get the value of a specific cookie
function getCookie(name) {
  const cookies = document.cookie.split(';');
  for (let i = 0; i < cookies.length; i++) {
    const cookie = cookies[i].trim();
    if (cookie.startsWith(name + '=')) {
      return cookie.substring(name.length + 1);
    }
  }
  return '';
}

// Set a cookie
function setCookie(name, value, days) {
  const date = new Date();
  date.setTime(date.getTime() + (days * 24 * 60 * 60 * 1000));
  const expires = 'expires=' + date.toUTCString();
  document.cookie = name + '=' + value + ';' + expires + ';path=/';
}
```

By understanding authentication, session management, and cookies, you can build secure and user-friendly web applications that manage user sessions and maintain state effectively.