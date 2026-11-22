# CSC 299 Final Project Portfolio

## About This Portfolio

This portfolio contains three projects I developed
for my CSC 299 final assignment.

My projects explore different areas of programming:
a terminal adventure game, a student dashboard,
and a command-line log analysis tool.

## Projects

| Project | Kind | Repository | What it does |
|---------|------|------------|--------------|
| StudyFlow | Web app | https://github.com/Kuzma12/studyflow | Organizes assignments, deadlines, and completed tasks. |
| Signal Lost | Game | https://github.com/Kuzma12/signal-lost | A spaceship adventure with survival mechanics and saved games. |
| LogLens | CLI | https://github.com/Kuzma12/loglens | Analyzes log files and filters errors and warnings. |

**Project developed further:** Signal Lost.

## Main Project: Signal Lost

Signal Lost is my extended project.

I developed it across six rounds, adding new
requirements and improving the game over time.

The game includes navigation, oxygen management,
a ship map, scanning, inventory, health, hazards,
a locked escape pod, and save/load functionality.

In Round 5, I revised an earlier escape requirement
so players must find and use a keycard before winning.

The project has 390 passing automated tests,
six architectural decision records, and six
development handoffs.

## Testing

### Signal Lost

cd signal-lost
python3 -m unittest discover -s tests -v

### StudyFlow

cd studyflow
node --test

### LogLens

cd loglens
python3 -m unittest discover -s tests -v

## Reflection

See [reflection.md](reflection.md) for my reflection
on the development process and use of Claude Code.
