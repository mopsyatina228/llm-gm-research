# Архитектурные паттерны

## Pattern A — State outside the model

Модель не является источником истины.

LLM -> proposed actions/state delta -> validator -> state store

Полезно для инвентаря, здоровья, ресурсов, положения объектов и таймеров.

## Pattern B — Director + Actor

Одна подсистема держит мир и формирует контекст, другая модель играет конкретного агента.

Можно расширить до Director -> GM -> NPC tools / rules -> State.

## Pattern C — Layered memory

recent transcript -> summaries -> retrievable archive

Старые данные не исчезают, но не попадают в каждый prompt.

## Pattern D — Private knowledge

Общий мир не равен знаниям персонажа.

У каждого NPC есть свой knowledge state. GM получает полный truth state, NPC получает только разрешённое подмножество.

## Pattern E — Phase compaction

Компрессия происходит на устойчивых границах: конец боя, смена сцены, завершение крупного действия, временной скачок, закрытие квестовой линии.

## Pattern F — Fine-tuning for behavior, RAG for truth

Fine-tuning: стиль, GM-поведение, структура ответа, устойчивые привычки.

RAG/state store: динамический канон, конкретные факты, правила кампании.

## Pattern G — Explicit state delta

Вместо того чтобы принимать текст модели как факт, модель отдельно предлагает изменения:

state_delta = [{entity, field, old?, new?, reason}]

Система валидирует и только потом применяет их.

## Pattern H — Consequence clocks

События могут продвигаться независимо от игрока.

Пример: clock = raiders-preparing, current = 3/6, advance_when = players spend two days / ignore warning / fail intervention.

Это полезно для мира, который не должен стоять на паузе, пока игроки выбирают, в какую дверь стучать.

## Pattern I — Provenance

Важный факт хранится вместе с источником: fact, source, observed_by, confidence, canonical=true|false.

Это позволяет отличать истину мира от слуха, ошибочного воспоминания и вывода NPC.

## Pattern J — Evaluation by state, not prose alone

Для GMing недостаточно оценивать только красоту текста.

Минимальные независимые метрики: continuity, rule/state consistency, knowledge isolation, player agency, consequence tracking, resource accounting, long-horizon recall, stylistic fit.