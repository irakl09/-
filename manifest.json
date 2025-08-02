self.addEventListener('install', event => {
  event.waitUntil(
    caches.open('volvo-schedule-v1').then(cache => {
      return cache.addAll([
        '/',
        '/index.html',
        '/1.jpg',
        '/1-512.jpg',
        '/manifest.json'
      ]);
    })
  );
});

self.addEventListener('fetch', event => {
  event.respondWith(
    caches.match(event.request).then(response => {
      return response || fetch(event.request);
    })
  );
});

self.addEventListener('message', event => {
  if (event.data && event.data.type === 'SKIP_WAITING') {
    self.skipWaiting();
  }
});
