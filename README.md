# ngx-facebook

This is a wrapper for the official Facebook JavaScript SDK. It makes it easier to use Facebook SDK with Angular 8+ by providing components, providers and types. 

<br><br>

[![npm](https://img.shields.io/npm/l/express.svg)](https://www.npmjs.com/package/@finosofica/ngx-facebook)
[![npm](https://img.shields.io/npm/dt/@finosofica/ngx-facebook.svg)](https://www.npmjs.com/package/@finosofica/ngx-facebook)
[![npm](https://img.shields.io/npm/dm/@finosofica/ngx-facebook.svg)](https://www.npmjs.com/package/@finosofica/ngx-facebook)

<br><br>

## Installation

#### 1. Install via NPM:

```shell
npm i --save @finosofica/ngx-facebook
```

#### 2. Add the Facebook JavaScript SDK to your index.html
```html
<script type="text/javascript" src="https://connect.facebook.net/en_US/sdk.js"></script>
```

#### 3. Import `FacebookModule` into your app's root module
```typescript

import { FacebookModule } from '@finosofica/ngx-facebook';

@NgModule({
  ...
  imports: [
    FacebookModule.forRoot()
  ],
  ...
})
export class AppModule { }

```

If you only want to use only, without using the other components, then you can import it in your app's module instead of `FacebookModule`.


```typescript
import { FacebookService, InitParams } from '@finosofica/ngx-facebook';

...

export class MyComponentOrService {

  constructor(private fb: FacebookService) {

    let initParams: InitParams = {
      appId: '1234566778',
      xfbml: true,
      version: 'v2.8'
    };

    fb.init(initParams);

  }

}
```

<br><br>

### Example of login with Facebook

```typescript
import { FacebookService, LoginResponse } from '@finosofica/ngx-facebook';

@Component(...)
export class MyComponent {

  constructor(private fb: FacebookService) { }

  loginWithFacebook(): void {

    this.fb.login()
      .then((response: LoginResponse) => console.log(response))
      .catch((error: any) => console.error(error));

  }

}
```

<br><br>

### Example of sharing on Facebook
```typescript
import { FacebookService, UIParams, UIResponse } from '@finosofica/ngx-facebook';

...

share(url: string) {

  let params: UIParams = {
    href: 'https://github.com/finosofica/ngx-facebook',
    method: 'share'
  };

  this.fb.ui(params)
    .then((res: UIResponse) => console.log(res))
    .catch((e: any) => console.error(e));

}
```

<br><br>

### Example of adding a Facebook like button
```html
<fb-like href="https://github.com/finosofica/ngx-facebook"></fb-like>
```

<br><br>

### Example of playing a Facebook video

#### Basic video component usage:
```html
<fb-video href="https://www.facebook.com/facebook/videos/10153231379946729/"></fb-video>
```

#### Advanced video component usage:
```html
<fb-video href="https://www.facebook.com/facebook/videos/10153231379946729/" (paused)="onVideoPaused($event)"></fb-video>
```
```typescript
import { Component, ViewChild } from '@angular/core';
import { FBVideoComponent } from '@finosofica/ngx-facebook';

@Component(...)
export class MyComponent {

  @ViewChild(FBVideoComponent) video: FBVideoComponent;

  ngAfterViewInit() {
    this.video.play();
    this.video.pause();
    this.video.getVolume();
  }

  onVideoPaused(ev: any) {
    console.log('User paused the video');
  }

}
```

<br><br>
## Contribution
- **Having an issue**? or looking for support? [Open an issue](https://github.com/finosofica/ngx-facebook/issues/new) and we will get you the help you need.
- Got a **new feature or a bug fix**? Fork the repo, make your changes, and submit a pull request.

## Support this project
If you find this project useful, please star the repo to let people know that it's reliable. Also, share it with friends and colleagues that might find this useful as well. Thank you :smile:
