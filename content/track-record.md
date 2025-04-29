## What Have I Built and Shipped?

"Tell me about something you've built."
It’s one of the first questions I get from early-stage founders—and one I’d ask myself as a future founder.

So I decided to dig through my own backlog and highlight a few projects I'm proud of. Things that shipped. Things that made a difference. Things that still make me smile.

## Rewriting the Scheduling Engine at Quad Graphics

At Quad Graphics, I overhauled the task arrangement logic in a legacy C++ scheduling tool—a Gantt chart-based application used to schedule printing jobs. The original system had serious performance issues. Nested loops—sometimes triple—created time complexities tipping into O(n3)O(n3) territory, and memory leaks were common.

After profiling the system and brainstorming with a senior engineer, I explored tree-based approaches to reduce the algorithmic overhead. We decided to implement the new logic in C# using interop, trading raw speed for garbage-collected stability. Pointers were replaced by handles to prevent leaks, and the codebase became vastly more maintainable.

I committed to writing clean, forward-looking code. The rewrite took two weeks of deep focus and late nights, followed by a full suite of unit and integration tests.

The result? An 800% performance improvement.
Users noticed. They stopped waiting minutes for job rearrangement and started getting results in seconds. Several even reached out to personally thank me.

That feedback—that impact—is why I love building.
