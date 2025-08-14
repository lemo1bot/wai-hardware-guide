# w.ai Worker Setup Guide - My Experience

Hey everyone! 👋 

So I was trying to set up a w.ai worker node to earn some W points, and man, it was a bit confusing at first. After going through the process and testing different methods, I figured I'd share the easiest way to get it running.

## What is w.ai Worker?

Basically, you run a worker node that contributes your GPU power to w.ai's distributed AI system. You earn W points for your contributions, which might convert to rewards later. Pretty cool way to monetize your GPU!

## Hardware Requirements (What I Tested)

### What Works:
- **Apple Silicon Macs**: M1, M2, M3, M4 (my MacBook M2 worked great)
- **NVIDIA GPUs**: GTX 1050+, RTX 2060, RTX 3070, RTX 4080, etc.
- **Compute Capability**: 5.0+ (most modern cards)

### What You Need:
- Good internet connection
- CUDA Toolkit 12.4 (for NVIDIA users)
- At least 8GB RAM (16GB+ recommended)

## Step-by-Step Setup (The Easy Way)

### Step 1: Sign Up for w.ai Dashboard
1. Go to w.ai dashboard
2. Sign up with your email
3. Create a new API key in the "API Keys" section
4. Save that API key - you'll need it!

### Step 2: Choose Your Setup Method

I tried three different ways:

#### Option A: Desktop App (Easiest)
- Download the GUI app from w.ai dashboard
- Install it on your local PC
- Enter your API key
- Click run - that's it!

#### Option B: CLI on Your Own Machine
If you want more control, use the command line:

```bash
# Install w.ai CLI
curl -fsSL https://app.w.ai/install.sh | bash

# Set your API key
export W_AI_API_KEY=your_api_key_here

# Run the worker
wai run
```

#### Option C: Rent a GPU (What I Did)
I rented a GPU from QuickPod because my local machine wasn't powerful enough:

1. Sign up on QuickPod
2. Fund your account (I used crypto)
3. Choose "CUDA 12.4" template
4. Pick a cheap GPU ($0.05/hr)
5. Create the pod with 100GB disk
6. Connect via SSH

### Step 3: Install Dependencies (For CLI/Rental)

If you're using CLI or rented GPU, you'll need to install some stuff:

```bash
# Update system
apt update && apt upgrade -y

# Install basic tools
apt install nano screen curl git wget jq make gcc tmux htop -y

# Install Python
apt install python3 python3-pip python3-venv python3-dev -y

# Install Node.js
curl -fsSL https://deb.nodesource.com/setup_22.x | bash -
apt install -y nodejs
npm install -g yarn
```

### Step 4: Install CUDA 12.4 (NVIDIA Users Only)

This is the tricky part - w.ai only works with CUDA 12.4:

```bash
# For WSL/Windows users
wget https://developer.download.nvidia.com/compute/cuda/repos/wsl-ubuntu/x86_64/cuda-wsl-ubuntu.pin
sudo mv cuda-wsl-ubuntu.pin /etc/apt/preferences.d/cuda-repository-pin-600
wget https://developer.download.nvidia.com/compute/cuda/12.4.0/local_installers/cuda-repo-wsl-ubuntu-12-4-local_12.4.0-1_amd64.deb
sudo dpkg -i cuda-repo-wsl-ubuntu-12-4-local_12.4.0-1_amd64.deb
sudo cp /var/cuda-repo-wsl-ubuntu-12-4-local/cuda-*-keyring.gpg /usr/share/keyrings/
sudo apt-get update
sudo apt-get -y install cuda-toolkit-12-4

# Add to PATH
echo 'export PATH=/usr/local/cuda-12.4/bin:$PATH' >> ~/.bashrc
echo 'export LD_LIBRARY_PATH=/usr/local/cuda-12.4/lib64:$LD_LIBRARY_PATH' >> ~/.bashrc
source ~/.bashrc
```

### Step 5: Run Your Worker

```bash
# Set your API key
export W_AI_API_KEY=your_api_key_here

# Start the worker
wai run
```

You should see it start mining! Takes a few minutes to get going.

## Running Multiple Workers (Advanced)

Once you get one worker running, you can run multiple to earn more:

### Install PM2 (Process Manager)
```bash
npm install -g pm2
```

### Create Config File
Create `wai.config.js`:
```javascript
module.exports = {
  apps : [{
    name: 'wai-node',
    script: 'wai',
    args: 'run',
    instances: 4,  // Number of workers
    autorestart: true,
    watch: false,
    max_memory_restart: '1G',
    env: {
      NODE_ENV: 'production',
      W_AI_API_KEY: 'your-api-key-here'
    }
  }]
};
```

### Start Multiple Workers
```bash
pm2 start wai.config.js
pm2 logs wai-node  # Check logs
```

## Monitoring Your Workers

### Check Status
```bash
# GPU usage
nvidia-smi

# Worker status
pm2 list

# Worker logs
pm2 logs wai-node

# Disk usage
du -sh /root/.wombo
```

### Useful Commands
```bash
# Stop workers
pm2 stop wai.config.js

# Restart workers
pm2 restart wai.config.js

# Kill all workers
pm2 kill
```

## My Experience & Tips

### What Worked for Me:
- **Rented GPU**: Much easier than setting up local CUDA
- **Multiple workers**: I run 9 instances on one GPU
- **PM2**: Keeps everything running smoothly

### Common Issues I Ran Into:
1. **CUDA version wrong**: Had to uninstall and reinstall CUDA 12.4
2. **API key issues**: Make sure you copy the full key
3. **Permission errors**: Sometimes need to run with sudo
4. **Memory issues**: Reduce number of workers if you get memory errors

### Performance Tips:
- Start with 1 worker, then increase gradually
- Monitor GPU memory usage
- Keep your system updated
- Use wired internet connection

## Earnings & Rewards

- You earn W points for your contributions
- Points are tracked in your dashboard
- Future rewards likely based on points earned
- More GPU power = more points

## Where to Get Help

- **Official w.ai Worker Guide**: https://github.com/0xmoei/wai-worker
- **w.ai Dashboard**: https://app.w.ai
- **QuickPod**: For GPU rentals
- **Vast**: Alternative GPU rental service

---

**Written by**: [@bank_of_btc](https://x.com/bank_of_btc)

**Based on**: My actual experience setting up w.ai workers

**When I tested**: August 2025

---

*This is my experience setting up w.ai workers. Your setup might be different, but this should get you started!*

#wai #Worker #GPU #Mining #AI
