# Authorization Testing Results

| Page / Feature             | Guest | Reserver | Administrator |
|---------------------------|--------|----------|----------------|
| / (index)                 | ✅     | ✅       | ✅              |
| └─ View resource form     | ❌     | ✅       | ✅              |
| └─ Create new resource    | ❌     | ❌       | ✅              |
| /login                    | ⚠️     | ⚠️       | ✅              |
| /register                 | ✅     | ❌       | ❌              |
| /profile                  | ❌     | ✅       | ✅              |
| /admin/users              | ❌     | ❌       | ✅              |
| /reservation              | ❌     | ✅       | ✅              |
| /resources                | ❌     | ✅       | ✅              |
| /api/reservations/1       | ❌     | ✅       | ✅              |

**Symbols:**
- ✅ = Pass
- ❌ = Fail
- ⚠️ = Attention (e.g., sensitive info leaked)

**Notes:**
- "⚠️ Reserver has unintended access to `/profile` (or another resource)."
- "⚠️ Unusual HTTP status codes observed (e.g., 500 or 403) when trying to access protected resources."
- "⚠️ Possible authentication bypass observed on `/login` or `/register`."
