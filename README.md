# Server Only Context

Tiny wrapper around `cache` to have request-scoped context
for server components. No more prop drilling!

```javascript
import serverContext from 'server-only-context';

export const [getLocale, setLocale] = serverContext('en')
export const [getUserId, setUserId] = serverContext('')
```

```javascript
import { setLocale, setUserId } from '@/context'

export default function UserPage({ params: { locale, userId } }) {
  setLocale(locale)
  setUserId(userId)
  return <MyComponent/>
}
```

```javascript
import { getLocale, getUserId } from '@/context'

export default function MyComponent() {
  const locale = getLocale()
  const userId = getUserId()

  return (
    <div>
      Hello {userId}! Locale is {locale}.
    </div>
  )
}
```
