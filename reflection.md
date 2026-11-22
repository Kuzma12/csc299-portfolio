# CSC 299 Final Reflection

## 1. Fresh Claude Code Sessions

One thing that happened in Round 5 was that Claude asked me what to do with the older requirements and tests that used the six-move winning route. We already had the original escape rules written down from the earlier rounds, but now we were changing how the player wins.

I decided to keep the old requirements and add notes explaining what changed instead of deleting everything. I think having clearer instructions in CLAUDE.md about what to do when changing an old requirement would have helped the new session.

We ended up adding that rule to CLAUDE.md so future sessions would know what to do. I learned that even if something was already decided, it helps to write down clear instructions so the next session doesn't get confused.

## 2. Changing an Earlier Requirement

In Round 5, I changed R3 because I wanted the keycard to actually have a purpose. Before, the player only needed to reach the Escape Pod with oxygen left. After the change, the player also needed to find the keycard on the Bridge and unlock the door before escaping.

This caused some of the older tests to fail because they were still using the original winning route. The shortest winning route changed from 6 moves to 8 moves, and 28 tests had to be updated.

The tests helped us see what needed to change. We also made decision record docs/decisions/0005.md to explain why we changed the escape rule and how it works now. I think the decision record explains the change well because it talks about the other options and why we didn't choose them.

I learned that changing one requirement can affect a lot of other parts of a program, even if the change seems small at first.

## 3. A Test That Caught a Problem

One test that was useful was test_R5_R10_clues_no_longer_steer_players_away_from_the_bridge in tests/test_world.py.

Part of the test was:

    for phrase in ("cold and still", "Nothing forward of here leads off the ship"):
        with self.subTest(phrase=phrase):
            self.assertNotIn(phrase, self.corridor)
            self.assertNotIn(phrase, self.bridge)

This test checked that the old scanner clues were no longer telling the player that going to the Bridge wasn't useful.

The problem was that in Round 5, the player needed to visit the Bridge to get the keycard. But some of the old scanner clues made it seem like going there was a waste of time.

We fixed the clues so they would help players find the keycard without telling them exactly how to finish the game. The fix was made in commit 5c4913c.

I think this was a useful test because the game could still run without errors, but it was giving the player confusing information. It showed me that tests aren't just for checking if the program crashes. They can also help check if the game makes sense.

## 4. A Commit I Would Change

One commit I would do differently is ea9a1ef from Round 6.

The commit message said there were 38 new game tests when there were actually 34. It also said there were 44 damaged-save cases when there were actually 45.

The code was working, but the commit message had the wrong numbers.

If I could do it again, I would check the test results more carefully before making the commit. We didn't change the original commit because we were supposed to keep our Git history. Instead, the correction was explained in commit f83da0c.

This taught me that I should pay more attention to the commit messages and not just whether the code works. I also learned that it's okay to make mistakes as long as I explain them and correct them properly.

## 5. Understanding Code Without an Assistant

The function I chose was read() from signal_lost/savefile.py.

When I first looked at the function without asking an assistant, I thought it was basically a way for the JSON file to give information to the program. I also thought that if the file didn't exist or something was wrong with it, the function would display some kind of file error.

After asking an assistant, I learned that the function opens the saved JSON file, reads the information, and returns it to the program. If the file is missing, it raises a NoSaveFile error. If the file is damaged or can't be read, it raises a DamagedSave error.

I was right about the function reading information from the JSON file and checking for errors. What I got wrong was thinking that it actually displays the error message to the player. The function only raises the error, and another part of the program handles what the player sees.

This helped me understand that different functions can have different jobs. One function can read the file and check for problems, while another part of the program decides what message to show.
