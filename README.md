# fullscreen
An explainer to define additional full screen options.

## Abstract
The ability to customize the UI when in fullscreen mode. On some Android devices
there are physical buttons so that the back, home buttons are not hidden. However on devices that use overlays for the navigation buttons fullscreen mode can
remove these depending on browser vendor. Samsung Internet browser keeps these
buttons however Chrome does not. Some pages may prefer to have the navigation
buttons so that the user can easily navigate out of the page. On the other
hand other pages may not wish to have the navigation bar. This adds the
ability for the page to provide a hint at what the UA should do.

## Proposed API change:

Current API is 
```WebIDL
partial interface Element {
  Promise<void> requestFullscreen();
  // ...
};
```

Proposed API is
```WebIDL
partial interface Element {
  Promise<void> requestFullscreen(optional FullscreenOptions options);
  // ...
};
```

## FullscreenOptions IDL

```WebIDL
enum FullscreenNavigationUI {
  "auto",
  "show",
  "hide"
};

dictionary FullscreenOptions {
  FullscreenNavigationUI navigationUI = "auto";
};
```
