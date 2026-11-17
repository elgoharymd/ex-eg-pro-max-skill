# Engineering Examples

## 1. Replace duplicated status booleans with one state
**Before**
```ts
const [loading, setLoading] = useState(false);
const [error, setError] = useState<string | null>(null);
const [done, setDone] = useState(false);
```
Impossible states (loading and done together) are representable.

**After**
```ts
type Status =
  | { kind: 'idle' }
  | { kind: 'loading' }
  | { kind: 'error'; message: string }
  | { kind: 'success' };

const [status, setStatus] = useState<Status>({ kind: 'idle' });
```

## 2. Validate external input at the boundary
```ts
import { z } from 'zod';

const BookingInput = z.object({
  studioId: z.string().min(1),
  startsAt: z.coerce.date(),
  durationMinutes: z.number().int().min(15).max(480),
});

export function parseBooking(raw: unknown) {
  const result = BookingInput.safeParse(raw);
  if (!result.success) {
    throw new ValidationError(result.error.issues.map(i => i.message));
  }
  return result.data;
}
```
Use whichever schema library the project already has; the principle is the same.

## 3. Authorize by ownership, not by ID alone
```ts
async function getOrder(userId: string, orderId: string) {
  const order = await repo.findById(orderId);
  if (!order || order.userId !== userId) {
    throw new NotFoundError(); // do not reveal existence
  }
  return order;
}
```

## 4. Separate data access from presentation
- `features/bookings/bookingRepository.ts`: reads and writes bookings.
- `features/bookings/bookingRules.ts`: pure functions for availability and pricing.
- `features/bookings/BookingList.tsx`: renders the data it is given.
The component receives props; it does not call the database.

## 5. Responsive grid without media-query sprawl
```css
.cards {
  display: grid;
  gap: var(--space-4);
  grid-template-columns: repeat(auto-fit, minmax(min(100%, 260px), 1fr));
}
```
One rule adapts across widths and never overflows on phones.

## 6. Accessible icon-only button
```tsx
<button type="button" aria-label="Close dialog" onClick={onClose}>
  <CloseIcon aria-hidden="true" />
</button>
```

## 7. Reduced motion
```css
.card {
  transition: transform 200ms ease;
}
@media (prefers-reduced-motion: reduce) {
  .card {
    transition: none;
  }
}
```

## 8. Measured change, not a guess
Record before and after for the same page and device:
- Bundle size of the route, from the build output.
- Lighthouse performance score, same settings.
Report both numbers. If you cannot measure, say so.
