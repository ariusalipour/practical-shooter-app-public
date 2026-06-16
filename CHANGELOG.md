# Changelog

## 2026-05-19
- Started Phase 1 design-system rollout by consolidating shared design tokens (light/dark palettes, typography, spacing, radii, sizing, shadows) and applying them across shared UI components, improving visual consistency and making future UX updates easier to ship safely.
- Added a new design-token reference document so contributors can use the same token source when building or updating screens.

## 2026-05-13
- Reorganised the components folder into feature-based sub-folders (`shared`, `home`, `rules`, `diff`, `calendar`, `learn`, `account`) to improve code discoverability and reduce coupling; all existing imports continue to work via the updated barrel export.

## 2026-05-12
- Fixed match totals (maximum points, match name) not updating in scoring sessions when a match's stages were edited; totals are now always recalculated and persisted when a match is saved.
- Added an offline banner to the top of the Home tab; a clearly visible warning now appears automatically when the device has no internet connection and disappears once connectivity is restored.
- Improved time entry in the Hit Factor Calculator and Stage Calculator; typing more than two digits now automatically inserts a decimal point to keep two decimal places, and adding a fifth digit slides the decimal to maintain the same format (e.g. typing 1, 2, 3, 4, 5 displays as 12.34 → 123.45).
- Stage and match editors now save automatically when you navigate back or swipe to close; there is no longer a separate Save button — your changes are kept if valid, or you are shown inline errors to fix before leaving. Blank new stages and matches with nothing entered are silently discarded.
- Added non-penalty paper and steel target types to stage configuration; these targets score normally but misses do not incur penalties, and they are included in the minimum shots and maximum points calculations.
- Added the ability to edit stage configuration directly from the scoring session; each stage now shows an edit icon in the verifier, and saving changes automatically adjusts any existing scores that exceed the new limits.
- Fixed the HF, points, and time summary not appearing below the last scored stage in the verifier.

## 2025-02-10
- Fixed swipe gestures not working on rules in Android; favourite and share swipe actions now work correctly on Android devices in both the rulebook viewer and favourites modal.

## 2025-01-18
- Fixed Match Verifier not showing existing scores when returning to a completed match; tapping a match now shows your previous scores instead of starting a new session.
- Moved power factor selector from stage calculator to match summary page; changing power factor now recalculates all scored stages instantly.
- Improved Match Verifier to auto-complete matches when all stages are scored; removed the manual "Complete Match" button since scores are saved automatically as you go.
- Fixed Match Verifier summary not updating after scoring a stage; the match totals and stage list now refresh correctly when returning from the calculator.
- Fixed Match Verifier scores exceeding stage limits when editing stages; if you reduce target counts on a stage with existing scores, those scores are automatically adjusted to fit the new limits (hits removed in order: alphas, charlies, deltas, misses).
- Fixed Match Verifier stage scores not showing when tapping a scored stage; the calculator now opens with the existing score pre-populated, allowing you to review or edit your previous entry.
- Added "Prefill Alphas" setting in Account settings; when enabled, the Match Verifier stage calculator starts with all alphas pre-filled based on target count, allowing you to substitute C/D/M hits by tapping (automatically swaps an alpha) and restore alphas by long-pressing.
- Added scoring validation to Match Verifier; scoring buttons (A, C, D, M) are now disabled when you reach the maximum number of hits allowed based on the stage's target configuration, preventing over-scoring.
- Added Match Verifier to the Learn tab; create matches with multiple stages, define target configurations for each stage, and score them using the hit factor calculator interface with automatic hit factor and points tracking.
- Fixed Hit Factor Calculator allowing negative scores; total points and hit factor are now clamped to a minimum of 0.

## 2025-01-08
- Updated app version to 3.0 with build number 30 to maintain iOS version continuity after the previous release used version 27.
- Capitalised all menu titles in the Account screen for consistent styling.
- Removed arrow icon from the App Info row in Account settings since it is non-interactive.
- Added share button to articles; tap the share icon in the article header to share the article title, summary, and a link with others.
- Added share button to quiz results; after completing a quiz, tap "Share Results" to share your score and challenge others to try the quiz.
- Added "Share Quiz" option on the quiz intro screen; share any quiz with others before starting it.
- Added restart button to quiz header; tap the refresh icon in the top-right corner while taking a quiz to start over from the beginning.
- Added deep link support for articles and quizzes; tapping a shared article or quiz link now opens the app directly to that content.

## 2025-01-07
- Added "Understanding Comstock Scoring and Hit Factor" article to the Learn tab; covers hit factor calculations, scoring zones, Major vs Minor power factor, and strategies for balancing speed and accuracy in IPSC competition.
- Added linked quiz for the Comstock scoring article; 8 questions testing your understanding of hit factor calculations, scoring zones, and competitive strategies.

## 2025-01-05
- Fixed app crashing when quiz questions are modified or deleted after users have started or completed attempts; stale answers for removed questions are now filtered out and historical attempts show a "Modified" badge for questions that no longer exist in the current quiz version.
- Fixed quiz completion failing on native apps with "LoadBundleFromServer" error; quizzes now complete and save scores correctly on iOS and Android.
- Added custom numpad to Hit Factor Calculator; enter time using the built-in numpad instead of the native keyboard, with tap to delete and long-press to clear.
- Added Hit Factor Calculator to the Learn tab; quickly calculate your stage hit factor by entering time and tapping scoring buttons for A, C, D, misses, no-shoots, and procedurals with real-time results and max potential display.
- Improved linked quiz selector in article editor; replaced horizontal chip selector with a searchable list that shows the selected quiz prominently and allows filtering through many quizzes easily.
- Added article-quiz linking; admins can now link a published quiz to an article and readers see a "Test Your Knowledge" tile at the end of the article that launches the quiz directly.
- Linked quiz tile in articles now shows your best score, in-progress status, attempt count, and last attempt details; tap the last attempt row to view your full results.

## 2025-01-04
- Quiz cards in the Learn tab now display taxonomy badges; category, difficulty, and disciplines are shown on each quiz for quick reference.
- Quiz list in admin panel now displays taxonomy badges; category, difficulty, and disciplines are shown on each quiz card for easy identification.
- Added taxonomy selection to the quiz editor; admins can now assign category, difficulty, disciplines, and tags when creating or editing quizzes.
- Added full quiz taxonomy management to the admin panel; admins can now add, edit, and delete quiz categories, difficulties, and disciplines with a dedicated management modal, matching the article taxonomy admin experience.
- Added "Seed Default Taxonomy" buttons to the admin Quizzes panel; admins can now quickly populate default categories, difficulties, and disciplines for quiz filtering with a single tap for each type.
- Added search and filtering to the Quizzes screen; you can now search quizzes by title or description, and filter by category, difficulty, discipline, or tags.
- Added "Hide completed quizzes" toggle in the filter modal; easily hide quizzes you've already attempted to focus on new challenges.
- Added quiz taxonomy system supporting categories (rules, safety, scoring, etc.), difficulty levels (beginner, intermediate, advanced), disciplines (handgun, rifle, shotgun, etc.), and custom tags for better quiz organisation.
- Added appendix comparison to the revision comparison feature; when comparing rulebook revisions, you can now see which appendices were added, removed, or modified, with word-level diffs for meta description changes.
- Quiz review now shows your answers from the last attempt; when reviewing quiz results, you can see which questions you got wrong with your incorrect answer displayed alongside the correct answer.
- Fixed quiz scoring bug where the last answer wasn't counted in the final score; all answers are now correctly included when calculating results.
- Quiz answer choices are now randomised each time you take a quiz; the order of options is shuffled when starting, resuming, or retaking a quiz for added variety and to prevent memorising answer positions.
- Quiz cards now show your last attempt at the bottom; tap to view the full results including your score, answers, and explanations from that attempt.
- Quizzes tile now shows "Sign In" badge for guest users; signing in is required to access quizzes and track your progress.

## 2025-01-03
- Fixed quiz icons and coloured backgrounds not displaying when using a custom accent colour; transparent colour overlays now work correctly with both hex and HSL colour formats.

## 2025-12-22
- Reduced spacing between paragraphs, bullet points, and headers in Learn tab chat responses; messages now have tighter, more natural formatting that's easier to read.
- Improved chat scrolling behaviour when AI responds; the message list now automatically scrolls to show the top of the new AI response, making it easier to read answers from the beginning without manual scrolling.
- Enabled Enter key to send messages in Learn tab chat input on mobile; pressing Enter on the mobile keyboard now sends your message for faster interaction.
- Fixed bullet points in rule descriptions not displaying correctly; Wingdings bullet characters from the API are now converted to standard bullet points (•) with proper line breaks, so rules like 3.2.1 display their lists correctly.
- Fixed appendix links in Learn tab chat responses not appearing; "Appendix A1", "Appendixes B2" and similar references are now properly detected and clickable.
- Fixed subrule links being truncated in Learn tab; citations like "Rule 10.5.3.1" now link correctly instead of being cut off to "Rule 10.5.3".
- Fixed appendix links with letter suffixes being cut off; references like "Appendix D4a" now link correctly instead of being truncated to "D4".
- Fixed excessive paragraph spacing in Learn tab chat responses; paragraphs now have natural line breaks without extra spacing between them.
- Improved Enter key behaviour in Learn tab chat input on web/desktop; Enter now reliably sends messages while Shift+Enter adds a new line.
- Added clickable appendix references (e.g., "Appendix A1") throughout the app; tapping an appendix citation in AI chat responses or rule text navigates directly to the appendix image for easy reference.
- Added AI-powered Rules Assistant chatbot to the Learn tab; ask natural language questions about IPSC rules and receive answers with cited rule sources that you can tap to view in the Rules tab.
- Added discipline selector dropdown to the chatbot; choose a specific discipline (Handgun, Rifle, Shotgun, etc.) before asking questions to get focused answers from that rulebook only.
- Chat conversation history and selected discipline are now preserved when switching between tabs or closing the app, so you can return to the Learn tab without losing your place.
- The Rules Assistant now requires a signed-in account; guest users see a prompt to sign in.

## 2025-12-18
- Calendar now automatically scrolls to the current month when first loaded, making it easier to see today's events without needing to scroll or tap the "Today" button.
- Deployed the app to EAS Hosting at https://practicalshooter.expo.app for easy web access.
- Added responsive sidebar navigation on desktop web browsers (1024px+), converting bottom tabs into a vertical sidebar on the left for a more desktop-friendly experience while keeping bottom tabs on mobile and native platforms.

## 2025-12-12
- Added a typed Practical Shooter Events API client so the app can fetch live event listings and reference data from the events service.
- Cached events locally across the previous and next year, refreshing in the background on launch so searches stay instant and resilient offline.
- Added a synced avatar colour picker on the Account tab so shooters can choose a hue for their profile tile, have it persist across devices, and automatically tint the app highlights.

## 2025-12-06
- Added Firestore-backed feature flags (via the `featureFlags/{category}` collection) so toggles like guest access can be controlled without shipping an app update.

## 2025-12-05
- Guest mode now lets you skip sign-in, explore the app, and sign out back to the auth screen with clear guest messaging.
- Added bottom tab navigation on the signed-in home screen with Home, Calendar, Rules, Learn, and Account icons.
