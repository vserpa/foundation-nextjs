# foundation-nextjs
PoC using NextJS

https://github.com/vserpa/foundation-nextjs

## Technologies
- [React](https://reactjs.org)
- [NextJS](http://nextjs.org)
- [TypeScript](https://www.typescriptlang.org/)
- [TailwindCSS](http://tailwindcss.com)
- [Tabler Icons](https://tabler-icons.io/)
- [Mantine](https://mantine.dev/)
- [Firebase](https://firebase.google.com/)
- UUID
- [Google Fonts](https://fonts.google.com)

## Create a new project from scratch

```shell
npx create-next-app@latest <project_name>
cd <project_name>
npm install @tabler/icons-react
npm i uuid
npm i -D @types/uuid
npm i firebase
npm install @mantine/core @mantine/hooks @mantine/dates dayjs @emotion/react
```

## Running the project

1. Create a Firebase project and active Firestore and Google Auth.

- Firestore permitions:

```
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /{document=**} {
    	allow read, write: if false;
    }

    match /financas/{email}/transacoes/{id} {
  		allow read: if (request.auth != null && request.auth.token.email == email);
      allow write: if (request.auth != null && request.auth.token.email == email);
    }
    
    match /usuarios/{email} {
  		allow read: if (request.auth != null && request.auth.token.email == email);
      allow write: if (request.auth != null && request.auth.token.email == email);
    }
  }
}
```

3. Create `.env.local` file on the project root folder:

```bash
NEXT_PUBLIC_FIREBASE_PROJECT_ID=
NEXT_PUBLIC_FIREBASE_AUTH_DOMAIN=
NEXT_PUBLIC_FIREBASE_API_KEY=
```
Use your Firebase credentials.

4. Running the project:

```bash
$ npm install

$ npm run dev
```
Access http://localhost:3000.

## License

[MIT License](LICENSE.md).
