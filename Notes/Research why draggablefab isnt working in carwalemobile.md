
Issues identified in story:
1. draggable fab when overlapped with scrollspy is laggy
2. app team have to manually disable scrolling when draggablefab is in drag state (told by suryansh)
3. perfomance of draggablefab needs to be improved (current fps was 2~25)

---

What was the issue?  
1. current draggable fab button is using Animated internally which is imported from react-native and which runs on JS thread,
2. carwale mobile's homepage contains scroll-spy and other components which use Animated imported from react-native-reanimated
3. this is creating conflict when user drags button above scroll-spy it glitches (reason is unknown).

Proposed solution:
Migration of draggableFabButton using react-native-reanimated which will fix all 3 issues, since migration will use same Animated import

---
#react-native