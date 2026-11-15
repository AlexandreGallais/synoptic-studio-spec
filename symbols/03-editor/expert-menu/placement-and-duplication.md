# Placement and duplication

> [Home](../../../README.md) › [Symbols](../../README.md) › [Editor](../README.md) › [Advanced tools](README.md) › Placement and duplication

Status: draft, from the Product Owner's description of 2026-11-11. Not validated.

## Rules

- The user picks a reference, then a shape to duplicate, then the rule of the duplication.
- Example 1: pick a point and a radius, then ask for 30 copies of a shape, equally spaced on the circle.
- Example 2: pick an existing line or shape, then ask for copies that follow its edge, equally spaced along it.

## What the research found

Source: the second research report (`research/t4-…/rapport.md`, section 3.19).

- AutoCAD: **polar** array (centre, count, angle between items, total angle, items rotated or not); array **along a path** (line, polyline, spline, arc, circle, ellipse; by count or by interval; items tangent or parallel); an array is "associative" (one linked object) or made of independent objects.
- Opinion of the report: three rules, **polar**, **along a path**, **grid**; options: count or spacing, start and end angle, copies rotated or not; independent copies, gathered in a group. Confidence: medium.
- Name: the report proposes **Advanced tools** instead of "expert menu" (see the [editor](../README.md)); the Product Owner used this name on 2026-11-15.

## Open questions

- The three rules and their options: to confirm. See [Open questions](../../10-open-questions.md).
