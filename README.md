\# Autonomous Indoor Guide Robot — EMINES Campus



> Project Lead: Mohamed Mohssine | Team of 14 | EMINES – UM6P | Sept 2025 – June 2026



An autonomous mobile robot designed to guide visitors inside the EMINES building. Built from scratch — mechanical, electrical, and software — by a 14-person interdisciplinary team.



\## Demo



\[Insert photo of robot here]

\[Insert photo of SolidWorks render here]

\[Insert LiDAR scan RViz screenshot here]



\## What it does



\- Autonomous navigation in a semi-structured indoor environment (no floor markers, no beacons)

\- Real-time mapping and localisation using SLAM Toolbox + LiDAR LD06

\- Semantic obstacle detection: people, scooters, cleaning machines — via fine-tuned YOLOv8n

\- LiDAR–camera fusion for obstacle distance estimation (pixel-to-angle projection + sector isolation)

\- Multilingual voice chatbot (FR/EN/AR) with RAG pipeline (Gemini 2.5 Flash, ChromaDB, Whisper STT/Edge TTS)

\- React/TypeScript touch interface with destination selection and real-time robot status

\- Automatic docking and recharging via spring-loaded conductive plates + visual alignment



\## Tech Stack



| Layer | Technology |

|---|---|

| Robotics framework | ROS2 (Humble) |

| SLAM | SLAM Toolbox (pose-graph, loop closure) |

| Navigation | Navigation2 (Nav2), DWA/TEB planners |

| Perception | LiDAR LD06 (360°, 12m range), Logitech C920 |

| Object detection | YOLOv8n fine-tuned on custom dataset (Roboflow, \~20k images) |

| Motor control | Arduino Mega, Pololu 37Dx68L DC motors, PID (Kp=57.56, Ki=772.5) |

| Compute | NIPOGI Mini PC (8GB RAM), Ubuntu 24 |

| UI | React + TypeScript + Tailwind CSS |

| Chatbot backend | Next.js API + GROQ LLM |

| CAD | SolidWorks (octagonal differential-drive chassis) |



\## Architecture



\### Software (ROS2 node graph)

```

LiDAR (/scan) ──┐

Encoders (/odom)──┤── SLAM Toolbox ──> /map

Camera ──────────┘        │

&#x20;                         ▼

&#x20;                   Navigation2 (Nav2)

&#x20;                         │

&#x20;              ┌──────────┴──────────┐

&#x20;         Path Planner         Costmap (YOLO fusion)

&#x20;                         │

&#x20;                   /cmd\_vel

&#x20;                         │

&#x20;                   Arduino Bridge

&#x20;                         │

&#x20;                Left/Right DC Motors

```



\### Mechanical

\- Differential drive, octagonal chassis (steel square tube 20×20×2, welded)

\- Wheel radius: 100mm, wheelbase: 488mm

\- Two Pololu DC motors with encoders, one castor wheel

\- All structural parts CNC-machined or 3D-printed in-house



\## Current Status (March 2026)



\- \[x] Full mechanical chassis fabricated and assembled

\- \[x] SLAM working in simulation (Gazebo) and real corridor tests

\- \[x] PID motor control validated experimentally (zero static error)

\- \[x] YOLO object detection + LiDAR fusion working in real-time

\- \[x] React UI deployed with LLM chatbot

\- \[ ] Nav2 full autonomous navigation (in progress)

\- \[ ] Physical integration of all subsystems (in progress)

\- \[ ] Auto-docking final tests (planned May 2026)



\## Key Results



\- SLAM map generated of EMINES Block E ground floor corridor

\- PID controller: rise time < 0.2s, zero static error, validated under load

\- YOLO detection: person + distance estimation confirmed at \~2.25m and \~4.12m

\- Battery autonomy: 113.2 Wh calculated for 3h operation



\## Team



Project managed by Mohamed Mohssine (also responsible for software architecture, 

ROS2, SLAM, YOLO integration, and LLM chatbot).

14-person team across mechanical, electrical, and software disciplines.



\## Institution



EMINES – School of Industrial Management  

Mohammed VI Polytechnic University (UM6P), Benguerir, Morocco

