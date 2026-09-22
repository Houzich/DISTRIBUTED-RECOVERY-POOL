# 🚀 DISTRIBUTED RECOVERY POOL

A distributed computing platform for recovering your own crypto wallets, keys and other data.

Do you have an old wallet, some missing data, or a large search space that a single computer cannot efficiently check?
Distributed Recovery Pool lets you combine computing resources from many participants and split the task between them.
Each participant receives a unique range, so the same work is not performed multiple times.

---

## 🎯 Why this project?

- Some recovery tasks require checking a very large number of possibilities.
- A single computer may take a very long time. A distributed approach allows splitting the search space across multiple independent participants.

**The principle is simple:**

```
Big task
      ↓
Split into ranges
      ↓
┌─────────┬─────────┬─────────┬─────────┐
│ Worker 1│ Worker 2│ Worker 3│ Worker 4│
└─────────┴─────────┴─────────┴─────────┘
      ↓
Parallel processing
      ↓
Overall progress
```

Each participant works on its own portion of the task.

---

## 🏠 Rooms

The main concept of the project is Rooms.
A Room groups participants working on one category of tasks.

Examples:

- 🔐 recovering crypto wallets using different RNGs;
- 🧩 recovering known parts of mnemonics using different RNGs;
- 🔑 recovering keys with known constraints using different RNGs;
- #️⃣ hashing-related computational tasks;
- ⚙️ custom computational tasks.

Each room can have its own:

- task parameters;
- ranges;
- distribution rules;
- computation settings;
- constraints;
- statistics.

---

## 🛠 Private Rooms

- You do not have to join an existing room.
- A user can create a private room for a specific task.
- This is useful if you need to combine several machines to recover your own data or run specialized computations.
- The room creator defines its parameters and rules.

---

## 📦 Task distribution

One of the platform's main features is automatic distribution of the computation space.
Each participant is assigned a unique range:

```
Room
 │
 ├── Worker #001 → Range A
 ├── Worker #002 → Range B
 ├── Worker #003 → Range C
 ├── Worker #004 → Range D
 └── Worker #005 → Range E
```

- Ranges must not overlap.

This allows:

- avoiding duplicate work;
- using computing resources as efficiently as possible;
- tracking each participant's contribution;
- resuming work after a client restart.

---

## 📊 Monitoring via Telegram

A Telegram bot is used for management and monitoring.
A participant can view:

- Room status

```
🏠 Room: Recovery-01
👥 Workers: 27
📊 Progress: 38.42%
⚡ Total speed: 18.7 GH/s
⏱ Runtime: 14h 32m
```

- Own Worker status

```
🖥 Worker #1842
Status: 🟢 Online
Speed: 742 MH/s
Progress: 64.17%
Assigned range: A91F...B204
```

A website or Telegram bot becomes the single interface for controlling distributed computations.

---

## ⚡ Architecture

The project consists of several main components:

```
			Telegram Bot
			     │
			     ▼
		  ┌─────────────┐
		  │    Server   │
		  │             │
		  │ Rooms       │
		  │ Workers     │
		  │ Tasks       │
		  │ Statistics  │
		  └──────┬──────┘
			     │
	  ┌──────────┼──────────┐
	  ▼          ▼          ▼
	Worker 1   Worker 2   Worker 3
	  │          │          │
	  ▼          ▼          ▼
	Compute    Compute    Compute
```

- The Server manages tasks and distributes ranges.
- Workers perform the computations.
- The Telegram bot provides the user interface for management and monitoring.

---

## 💻 Worker

- After connecting, a Worker receives a task from the server.
- Then it:
  - receives the assigned range;
  - starts computations;
  - periodically sends statistics;
  - reports completion of a range;
  - receives the next range.

Thus, the user does not need to distribute work between machines manually.

---

## 📈 Statistics

The system provides both individual and aggregated statistics.

For a room:

- number of participants;
- number of active Workers;
- total volume of work performed;
- current progress;
- aggregate speed;
- runtime.

For a participant:

- own speed;
- processed ranges;
- current progress;
- number of completed tasks;
- runtime;
- Worker status.

---

## 🔐 Security

- The project is intended for the legal recovery of your own data and wallets, and for distributed computations you are authorized to perform.
- Do not use the platform to access other people's wallets, keys, accounts, or data.
- Do not send the server:
  - seed phrases;
  - private keys;
  - passwords;
  - wallet files;
  - other confidential information.
- Instead, the Worker should handle sensitive task parameters locally.

---

## 🚀 Quick start

1. Install the Worker
   - Download the latest client release from Releases.
   - Unpack the archive and run the Worker.
2. Authenticate
   - Get a participant ID via the Telegram bot and enter it in the client.
3. Choose a room
   - After connecting, a list of rooms is available:

```
Available rooms:
[01] Recovery
[02] Hash Research
[03] Custom Tasks
```

4. Start the Worker
   - After connecting, the server assigns a free range.
   - Computation starts automatically.
5. Monitor progress
   - Open the Telegram bot to see:
     - the current task;
     - speed;
     - progress;
     - Worker status;
     - room statistics.

---

## 💳 Access to the pool

- Access to the infrastructure may be provided via subscription.
- Subscription allows connecting to available rooms and using the distributed computing infrastructure according to each room's rules.
- Subscription terms and available plans are published separately.

---

## 🧩 For developers

🧩 For developers
The project is designed for further expansion.
Possible development directions:
- new types of computational tasks;
- additional algorithms;
- custom Worker clients;
- APIs;
- extended statistics;
- automatic scaling;
- Docker deployment;
- additional management interfaces.


📌 Roadmap

**Phase 1**
- Core Worker architecture
- Room system
- Range distribution
- Telegram monitoring

**Phase 2**
- Extended statistics
- Custom room creation
- API
- Automatic task recovery

**Phase 3**
- Infrastructure scaling
- Additional types of Workers
- Extended monitoring
- Load distribution optimization

---
## 🌐 Join us

One computer is one computing resource.
A pool is many resources working on a common task.
Choose a room, connect your Worker and use spare computing power to recover your own data and perform distributed computational tasks.

- ⚡ Distributed computing
- 🏠 Rooms
- 🖥 Workers
- 📊 Real-time monitoring
- 🔐 Privacy-focused architecture

---
## 💰 COMPENSATION

Participants are rewarded for their computational contribution to a room's tasks.
The reward amount depends on the volume of the range actually processed by the participant's Worker on their machine.
The larger the processed range, the greater the participant's computational contribution.

### 📊 How it works?

After joining a room, a Worker receives an individual range:

```
Room
 │
 ├── Worker #01 → Range A
 ├── Worker #02 → Range B
 ├── Worker #03 → Range C
 └── Worker #04 → Range D
```

Once the assigned range is completed, the system records the result and calculates the participant's contribution.
For example:

```
🖥 Worker #1842
Processed: 12,500,000,000 candidates
Status: ✅ Completed
Contribution: 12,500,000,000
```

Rewards are calculated based on the verified volume of completed work according to the rules of each room.
***🏆 Each participant's contribution is tracked separately***


A participant can see:

- 📦 assigned range;
- ✅ processed range;
- 📊 percent complete;
- ⚡ Worker speed;
- 🏆 accumulated computational contribution;
- 💰 available reward.

Thus, participants are rewarded not just for being connected, but for the real volume of computation their machines perform.
**⚡ Connect your Worker → get a range → compute → increase your contribution.**


## Welcome to Distributed Recovery Pool.
 - **https://t.me/brute_force_gpu**
 - **https://t.me/Hash_Pool**

---
# 🔒 OFFLINE MODE

Run your tasks without an internet connection
A pool participant does not need to keep their machine online constantly.
A Worker can operate fully offline.
This allows you to use your PC's compute power without sending the server sensitive task parameters or intermediate results during computation.

### 📴 Offline operation

After receiving necessary task parameters, the participant can disconnect from the network.
The Worker continues to operate locally:

```
┌───────────────────────────────┐
│         YOUR PC               │
│                               │
│  Worker                       │
│     ↓                         │
│  Local computation            │
│     ↓                         │
│  Range processing             │
│     ↓                         │
│  Local result file            │
│                               │
└───────────────┬───────────────┘
                │
          NO INTERNET
```

All computations are performed directly on the participant's machine.
### 🔐 Privacy

While operating offline, the Worker does not send computation results to the pool.
This lets the participant retain control over:
- original task parameters;
- processed ranges;
- search results;
- discovered values;
- history of work performed.
No results are required to be sent to the server automatically.


##### 📄 LOCAL RESULT FILE

The Worker automatically saves information about performed work to a text file.
The file contains an encrypted representation of:
- the processed range;
- the task state;
- found results;
- necessary metadata.

Example:

```
Worker ID: 1842
Task: Recovery-01
Range: ENC: A7F2...91C4
Processed: ENC: 73D1...F082
Status: COMPLETED
Result: FOUND
Result ID: ENC: 91AF...72B1
```

The file can be kept locally and used later to synchronize with the pool.


##### 🔎 HOW TO KNOW A RESULT WAS FOUND?

The Worker displays the result in the program interface.
For example:

```
╔══════════════════════════════╗
║        TASK COMPLETED        ║
╠══════════════════════════════╣
║                              ║
║  Range:       COMPLETED      ║
║                              ║
║  Result:      ✓ FOUND        ║
║                              ║
║  Results:     1              ║
║                              ║
╚══════════════════════════════╝
```

The same information is saved to a local text file.
Thus, a participant does not need to stay connected to the server to determine the outcome of their work.

##### 📤 SYNC VIA TELEGRAM

After finishing offline work, the participant can reconnect to the internet and upload the saved file to the Telegram bot.
The bot reads the file and updates the participant's data.
For example:

```
Worker #1842
Previous progress: 42.17%
Uploaded result: +12.4B processed
New progress: 54.61%
Status: ✓ Synchronized
```

##### 🔄 RANGE UPDATES

Completed range information can be updated in two ways:

**📄 Via file**

The participant sends the saved text file to the Telegram bot.
The bot processes it and updates the recorded work.

**💬 Via message**

If needed, the participant can provide required data directly in a message to the Telegram bot.
After synchronization, the pool receives information about ranges that were already processed.


🛡 WHY OFFLINE MODE?

It is especially useful for participants who:
- work on machines without constant internet access;
- want to minimize network interaction;
- do not want to transmit results in real time;
- perform long-running computations;
- want to store results locally;
- use a dedicated machine for computing.

Internet is only needed for synchronization — computations themselves can be performed locally.
### ⚡ YOUR PC. YOUR DATA. YOUR COMPUTATION.
**Connect to the pool → get a task → disconnect from the internet → compute locally → save the result → reconnect later → synchronize via Telegram.**
Maximum autonomy. Minimum network interaction.

## Welcome to Distributed Recovery Pool.
 - **https://t.me/brute_force_gpu**
 - **https://t.me/Hash_Pool**

---


