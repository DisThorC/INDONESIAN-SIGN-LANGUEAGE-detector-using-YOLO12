## Copilot Workspace Instructions

This repository provides a lean realtime Indonesian Sign Language (ISL) detector using a fine‑tuned YOLO12s model (50 epochs). Only essential runtime code plus final weights are tracked.

### Included
- Realtime scripts and runtime (`realtime.py`, `src/yolo12/*`)
- Final weights: `runs/train/exp_y12s_50e_640/weights/{best.pt,last.pt}`
- Configs and lightweight utilities

### Excluded
- Raw/full datasets and large artifact images
- Bulk run outputs beyond the two weight files

### Key Runtime Features
- Threaded webcam capture for lower latency
- Optional tracker + temporal smoothing
- Semantic prior + optional Markov decoding
- Dynamic `imgsz` and frame stride to maintain >20 FPS

### Workflow Rules
1. If you add/change runtime flags, update the Quick Start section in `README.md`.
2. Do not commit large media/datasets; `.gitignore` already blocks them.
3. Keep `requirements.txt` and `pyproject.toml` in sync for new deps.
4. Add small tests only when logic changes (tracker, smoothing, decoding).
5. Keep commits focused and descriptive.

### Common Commands
- Setup venv and install requirements, then:
- Run realtime: `python run_realtime.py` or `python .\realtime.py --duration 15`
- Quick CPU sanity train (optional): 1 epoch with reduced `imgsz`

### Optional Future Enhancements
- Simple latency benchmark across image sizes
- ONNX/TensorRT export & quantization scripts in a separate branch to keep the footprint small

### Ownership
Author: DISTHORC. Maintain attribution in README and license headers if files are significantly refactored.

### Principle
Favor clarity and performance knobs over heavy abstractions; keep it easy to reproduce.

---
Revise this file if the project scope evolves; keep it concise.
<!-- Use this file to provide workspace-specific custom instructions to Copilot. For more details, visit https://code.visualstudio.com/docs/copilot/copilot-customization#_use-a-githubcopilotinstructionsmd-file -->

	<!-- Ask for project type, language, and frameworks if not specified. Skip if already provided. -->

	<!--
	Ensure that the previous step has been marked as completed.
	Call project setup tool with projectType parameter.
	Run scaffolding command to create project files and folders.
	Use '.' as the working directory.
	If no appropriate projectType is available, search documentation using available tools.
	Otherwise, create the project structure manually using available file creation tools.
	-->

	<!--
	Verify that all previous steps have been completed successfully and you have marked the step as completed.
	Develop a plan to modify codebase according to user requirements.
	Apply modifications using appropriate tools and user-provided references.
	Skip this step for "Hello World" projects.
	-->

	<!-- ONLY install extensions provided mentioned in the get_project_setup_info. Skip this step otherwise and mark as completed. -->

	<!--
	Verify that all previous steps have been completed.
	Install any missing dependencies.
	Run diagnostics and resolve any issues.
	Check for markdown files in project folder for relevant instructions on how to do this.
	-->

	<!--
	Verify that all previous steps have been completed.
	Check https://code.visualstudio.com/docs/debugtest/tasks to determine if the project needs a task. If so, use the create_and_run_task to create and launch a task based on package.json, README.md, and project structure.
	Skip this step otherwise.
	 -->

	<!--
	Verify that all previous steps have been completed.
	Prompt user for debug mode, launch only if confirmed.
	 -->

	<!--
	Verify that all previous steps have been completed.
	Verify that README.md and the copilot-instructions.md file in the .github directory exists and contains current project information.
	Clean up the copilot-instructions.md file in the .github directory by removing all HTML comments.
	 -->

<!--
## Execution Guidelines
PROGRESS TRACKING:

COMMUNICATION RULES:

DEVELOPMENT RULES:

FOLDER CREATION RULES:

EXTENSION INSTALLATION RULES:

PROJECT CONTENT RULES:

TASK COMPLETION RULES:
  - Project is successfully scaffolded and compiled without errors
  - copilot-instructions.md file in the .github directory exists in the project
  - README.md file exists and is up to date
  - User is provided with clear instructions to debug/launch the project

Before starting a new task in the above plan, update progress in the plan.
## Copilot workspace checklist
