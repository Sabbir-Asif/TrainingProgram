# Static File Caching Strategies

## Overview
When serving static files (JS, CSS, images), we need two things:
1. Long-term caching for better performance
2. Immediate updates when files change

## Common Strategies

### 1. E-tag Strategy
- File URL remains unchanged
- Server generates a unique identifier (E-tag) for each file version
- Client sends `If-None-Match` header with cached E-tag
- Server compares E-tags to determine if file has changed

```http
Client: GET /styles.css
Server: 200 OK, ETag: "abc123"

Later...
Client: GET /styles.css, If-None-Match: "abc123"
Server: 304 Not Modified (if unchanged)
```

**Pros:**
- URL consistency
- Bandwidth efficient

**Cons:**
- Requires server validation
- Extra round-trip time

### 2. Cache Busting Strategy
- Append version/hash to file URL
- Example: `styles.css?v=123` or `styles.123.css`
- CDN treats each version as a different file

```html
<!-- Original -->
<link href="/styles.css" rel="stylesheet">

<!-- With cache busting -->
<link href="/styles.css?v=123" rel="stylesheet">
<!-- or -->
<link href="/styles.123.css" rel="stylesheet">
```

**Pros:**
- No server validation needed
- Works well with CDNs
- Immediate updates

**Cons:**
- Requires build process
- URL changes with each update

## Implementation Tips

1. **For Cache Busting:**
   - Use content hash in filename
   - Configure build tools (webpack, rollup) to generate hashed filenames
   - Update HTML templates to reference correct versions

2. **For E-tags:**
   - Configure server to generate E-tags
   - Set appropriate cache headers
   - Handle `If-None-Match` requests

## Best Practice Recommendations

1. Use cache busting for:
   - Static assets (JS, CSS, images)
   - Production environments
   - CDN deployment

2. Use E-tags for:
   - Dynamic content
   - API responses
   - Development environments
