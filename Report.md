# NL2SQL Old vs New 

**What this is:** A tiny comparison. We did **not** change the prompts.

## Big Picture
- **Old prompt:** SQL + extra text; sometimes uses '2025' (quotes).
- **New prompt:** SQL only; uses 2025 (number). Cleaner.
- **Tables:** same in both — `employees`, `salary`, `studies`.

## Results
1) **All employees:** both OK.  
2) **Salaries in 2024:** both OK (new uses number, old uses '2024').  
3) **Employees + studies:** both OK (column names differ by prompt style).  
4) **Top earner 2025:** both OK (may pick one if tie).  
5) **Latest salary per employee:** both OK (two valid methods).  
6) **>1 degree:** both OK (DISTINCT not needed but fine).

## Why they look different
- Output style: Old adds explanation; New is SQL-only.
- Year type: Old sometimes treats year like text; New uses numbers.
- Column casing: Old/new examples show different casing, but same fields.

## Tiny Tips
- Use numbers for `year` when it's an integer.
- If you use `LIMIT 1`, add a tie-breaker like `, name ASC`.
- Keep joins simple: `JOIN ... ON ...` with the matching keys.

## Bottom Line
- All shared outputs are OK. The new prompt is cleaner to run.