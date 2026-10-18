# Dark Patterns: Skill Content (Draft for Review)

Purpose: source material for an AI skill that keeps the features we build free of dark
patterns. This document is the content. Once approved it becomes the body of the skill.

Written in plain language. No jargon where a plain word works.

---

## 1. What are dark patterns

A dark pattern (also called a deceptive pattern) is a user interface choice that gets a
person to do something they did not mean to do, because it serves the business and not the
person. The term was coined by UX designer Harry Brignull in 2010.

A good working definition from academic work (Mathur et al., Princeton, 2019): dark patterns
are "user interface design choices that benefit an online service by coercing, steering, or
deceiving users into making unintended and potentially harmful decisions."

The key test is the gap between what the user wanted and what the design pushed them into.
Normal good design helps a person reach their own goal. A dark pattern bends the interface so
the person reaches the company's goal instead, often without noticing.

Three traits separate a dark pattern from ordinary persuasion:

- It works against the user's own interest, not just for the company's.
- The user would likely object if they saw clearly what was happening.
- The design hides, rushes, shames, or tricks to close that gap.

Dark patterns are not only an ethics problem. They are increasingly illegal. Regulators in
the US (FTC), the EU (GDPR / EDPB), and California (CPRA) now treat many of them as unlawful.

---

## 2. How are they used

### 2.1 The common catalogue

This is the current catalogue maintained by Harry Brignull at deceptive.design. These are
the patterns to recognize and never ship.

| Pattern | What it does |
| --- | --- |
| Sneaking | Draws the user into a transaction under false pretenses by hiding or delaying relevant information. |
| Forced action | The user wants one thing but must first do something else they would rather avoid. |
| Hard to cancel | Signing up is easy, cancelling is made very hard. |
| Preselection | A default option is chosen for the user to steer the decision. |
| Obstruction | Barriers and hurdles make it hard to finish a task or reach information. |
| Hidden subscription | The user is enrolled in recurring payment without clear disclosure or explicit consent. |
| Hidden costs | A low price hides fees that only appear at checkout, after the user has invested effort. |
| Trick wording | Confusing or misleading language pushes an action (for example, double negatives). |
| Visual interference | Information the user expects to see is hidden, obscured, or disguised. |
| Fake social proof | Fake reviews, testimonials, or "X people are viewing this" messages inflate credibility. |
| Fake urgency | A false time limit pressures the user to act. |
| Nagging | Repeated interruptions push the user toward something that may not serve them. |
| Fake scarcity | A false sign of limited supply or high demand pressures the user. |
| Disguised ads | Advertising is dressed up as interface or native content so users click by mistake. |
| Confirmshaming | Emotional guilt pushes the user toward a choice they would not otherwise make. |
| Comparison prevention | Prices and features are combined or buried so products are hard to compare. |
| Addictive design | The design exploits psychological weakness to drive compulsive use. |
| Currency confusion | Real money is turned into virtual currency so real spend is hard to see. |

### 2.2 The mechanisms behind them

Most patterns lean on known human tendencies. The "pre-pick your preferred option" writeup
(Evil by Design, under the "Sloth" category) is a clear example of how one is engineered:

- Priming: earlier exposure to a word or image makes the related choice easier to pick later.
- Familiarity: an option that feels familiar feels like enough to decide on.
- Credibility: a choice looks safe when it carries the designer's apparent authority.
- Defaults: making the desired action the default steers people toward it.

The tells for that one specific pattern: a "recommended" or "preferred" label, a vague
"best value" claim attached to the option the company wants, social proof that others picked
it, and a pre-selected default. None of these informs the user. All of them steer.

### 2.3 How regulators group them

Three authoritative groupings. They overlap with the catalogue above and are useful because
they carry legal weight.

FTC, "Bringing Dark Patterns to Light" (2022). The report groups practices into categories
and warns that false or misleading versions may break the law:

- Endorsements / false social proof (fake testimonials, "39 people are viewing this").
- Scarcity (false "only 2 left").
- Urgency (false countdown timers, false "limited time").
- Obstruction (hard to cancel, accounts that cannot be deleted).
- Sneaking / information hiding (surprise cart items, fees hidden to checkout, virtual currency).
- Interface interference (false button hierarchy, disguised ads, bait and switch).
- Coerced action (nagging, forced enrollment, grinding).
- Asymmetric choice (confusing questions, confirmshaming).

Note: the FTC says accurate statements (genuine low stock, a real deadline) are not deceptive.
The harm is in the false or hidden version.

EDPB Guidelines 03/2022 (deceptive design in social media, GDPR focus). Six categories:

- Overloading (continuous prompting, privacy maze, too many options).
- Skipping (deceptive snugness, "look over there").
- Stirring (emotional steering, hidden in plain sight).
- Obstructing (dead end, longer than necessary, misleading information).
- Fickle (lacking hierarchy, decontextualising, inconsistent interface, language discontinuity).
- Left in the dark (conflicting information, ambiguous wording).

Mathur et al. (Princeton, 2019) group patterns into seven high-level types: Sneaking,
Urgency, Misdirection, Social proof, Scarcity, Obstruction, and Forced action.

---

## 3. How should we avoid them as UX people

The goal is simple to state: the interface should help the user reach the user's goal, and
be honest about the cost to them. Concrete rules:

- Make the easy path the honest path. The default, the biggest button, and the clearest
  wording should all point at what is best for the user, or at a neutral choice, never at a
  trap.
- Symmetry of effort. If signing up takes one click, cancelling should take about one click.
  If opting in is one tap, opting out should be one tap. Unequal effort is the tell.
- Show the full price and the full commitment before the user commits, not after. No fee,
  subscription, or auto-renewal should first appear at or after checkout.
- Say what the choice means in plain words. No double negatives. No guilt wording on the
  decline option ("No thanks, I like paying too much" is a dark pattern).
- Only state scarcity, urgency, or social proof when it is true and verifiable. A countdown
  that resets, a stock count that never moves, a review you cannot trace: remove it.
- Defaults should reflect the privacy-protective and lower-spend option, not the one that
  extracts the most. Pre-ticked consent is not consent.
- Make comparison easy. Do not bundle or bury prices to stop people shopping around.
- Respect attention. No endless nagging, no interruptions designed to wear the user down.

A fast self-check (adapted from the Mathur et al. lens). Ask of any design:

1. Is the choice asymmetric? Does it make one option far easier than the other for no reason
   that helps the user?
2. Is it covert? Would the user be surprised to learn what the design is doing?
3. Is it deceptive? Does it create or rely on a false belief?
4. Does it hide information the user needs to decide well?
5. Is it restrictive? Does it remove or block a choice the user should have?

If the answer to any of these is yes and it serves the business over the user, it is a dark
pattern. Redesign it.

---

## 4. When should we use them

Never, if "them" means dark patterns. There is no legitimate use of a deceptive pattern. If
it only works because the user does not understand it, it is out.

What we can use, and should, is honest persuasion and good defaults. The line:

- Allowed: a default that protects the user (privacy on, spend off, safest choice first).
- Allowed: true urgency and true scarcity, stated plainly ("sale ends Friday" when it does).
- Allowed: real social proof (real, attributable reviews and ratings).
- Allowed: a genuine recommendation, clearly labelled as ours and easy to ignore.
- Allowed: friction that protects the user (a confirm step before a destructive or costly
  action). Friction to protect is good. Friction to trap is a dark pattern.

The test for any "nudge": would we be comfortable showing the user exactly how and why it
works? If explaining it to the user would make them feel tricked, it is a dark pattern. If
explaining it would make them feel helped or respected, it is fine.

One more rule: when in doubt, ask the user (the person we are building for), do not guess.
If the intended behavior is unclear, stop and confirm rather than ship a steering default.

---

## 5. What coders should decide when building features

Dark patterns are not only a designer's problem. They are often introduced in code: the
default value of a checkbox, the order of buttons, what the cancel endpoint actually does,
whether a timer is real. Developers are the last line of defense. Before building a feature
that touches a user choice, a payment, a consent, a subscription, or attention, decide:

- Defaults. What is the default value, and who does it favor? Set consent and marketing
  flags to off by default. Never pre-check an opt-in.
- Symmetry. Does a cancel / delete / opt-out path exist and is it as easy as the opt-in?
  If you built the sign-up flow, you own building an equally simple exit.
- Honesty of dynamic UI. If the code renders a countdown, a stock count, a "N people viewing"
  badge, or a "recommended" tag, is the value real and sourced from true data? If you cannot
  back it with a real source, do not render it.
- Disclosure timing. Does the code surface full price, fees, and recurring charges before the
  commit action, not after? Put the disclosure on the same screen as the button.
- Consent integrity. Is consent freely given, specific, informed, and recorded? A bundled or
  assumed consent is not valid. Store what was consented to and when.
- Cancellation and deletion that actually work. "Hard to cancel" and "immortal accounts" are
  named dark patterns and are enforcement targets. Build the delete and the unsubscribe for
  real, and test them.
- Accessibility is not optional here. Visual interference and false hierarchy often hurt
  assistive-technology users most. A choice that a screen reader cannot present fairly is a
  dark pattern by effect.

If a product or design request asks you to build one of these against the user, that is the
moment to raise it, not to implement it quietly. Name the pattern and propose the honest
version.

---

## 6. What the skill will enforce

The skill runs on any change that adds or changes a user-facing choice, a consent, a payment
or subscription, a default value, or any urgency / scarcity / social-proof element. It does
three things:

1. Detect. Scan the change for the catalogue in section 2.1 and the five-question lens in
   section 3. Flag any match as a finding with the pattern name, where it lives, and the
   honest alternative.

2. Block. Treat these as hard failures that stop "done" until fixed or explicitly waived by a
   human:
   - Pre-checked or defaulted opt-in for consent, marketing, or data sharing.
   - A sign-up / opt-in path with no equally easy cancel / opt-out / delete path.
   - Urgency, scarcity, or social-proof UI not backed by a real data source.
   - Fees, recurring charges, or auto-renewal first disclosed at or after the commit action.
   - Confirmshaming or trick wording (guilt language, double negatives) on a decline option.
   - A "recommended" / "preferred" / pre-selected default that serves the business over the
     user with no honest basis.

3. Require evidence. For each flagged element the change must show the honest basis: the real
   data source behind a scarcity or social-proof claim, the location of the matching opt-out,
   the pre-commit disclosure, the default set to the user-protective value. No evidence means
   the finding stands.

The only bypass is an explicit human waiver, in words, with a reason, recorded in the change.
The skill never self-waives by calling something "trivial."

---

## Sources and evidence notes

Each source was read this session unless noted. Where a count or claim came from a secondary
summary rather than the primary document, that is flagged.

- Deceptive pattern catalogue (section 2.1): read directly from deceptive.design/types
  (Harry Brignull). Evidence: observed.
- "Pre-pick your preferred option" mechanics (section 2.2): read directly from
  evilbydesign.info/sloth/pre-pick-your-preferred-option/. Evidence: observed.
- FTC categories (section 2.3): the FTC PDF did not parse this session; categories were taken
  from a law-firm summary (agg.com) of "Bringing Dark Patterns to Light" (2022). Evidence:
  reported. Limitation: verify the exact category list against the FTC PDF before publishing.
- EDPB six categories (section 2.3): from a securiti.ai summary of EDPB Guidelines 03/2022.
  Evidence: reported. Limitation: confirm subtypes against the official EDPB PDF.
- Mathur et al. seven categories and the definition in section 1: read from
  deceptive.design/book/contents/chapter-13 and the Princeton project page
  (webtransparency.cs.princeton.edu/dark-patterns). Evidence: observed.
- The five-question lens in section 3 (asymmetric, covert, deceptive, hides information,
  restrictive): attributed to the Mathur et al. 2019 paper. Evidence: documented. Limitation:
  the five dimensions were not confirmed against the raw paper (arXiv 1907.07032) this
  session; confirm the exact wording before publishing.
