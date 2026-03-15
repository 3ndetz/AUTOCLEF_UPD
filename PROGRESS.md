# Progress

## Текущий статус

**MC версия:** 1.21
**Дата:** 2026-03-15

Предыдущие логи: `old/PROGRESS_2026-03-15.md`, `old/PROGRESS_2026-03-12.md`

---

## 1. Investigation

## 2. Plan

## 3. Implementation

### altoclef known issues fixes (2026-03-15)

- **SW in-chest stuck**: `LootContainerTask` — added 10s timeout (200 ticks), always close screen in onStop
- **projectile dodging**: `ProjectileHelper.getClosestPointOnFlatLine()` — division by zero guard when projectile has no horizontal velocity
- **EpicCamera tp ~100000 blocks**: `GestureTask` — clamp camera distance to 20 blocks max, reset modifiers in onStop; EpicCamera sanity check 50 blocks

### PvP combat movement rewrite (2026-03-15)

- **KillAuraHelper.GoJump**: полный переписан — tick-based (без Thread, без sleep, без 900ms задержки)
- Бот теперь ВСЕГДА спринтит+прыгает к цели без рывков и пауз
- **onPlayerInteract**: всегда aim + sprint, убрана проверка `isPathing()` которая блокировала движение
- **stopCombatMovement()**: чистый release всех клавиш при выходе из PvP
