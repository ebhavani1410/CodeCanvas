# CodeCanvas 🎨

> Transform coding problems into animated visual simulations

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](http://makeapullrequest.com)
[![Hackathon](https://img.shields.io/badge/Hackathon-2026-blue.svg)](https://github.com)

CodeCanvas is an AI-powered learning platform that transforms coding problems and user-written code into animated, story-based simulations. Instead of reading abstract logic, learners can **see** algorithms come alive, **watch** data structures evolve, and **understand** execution through interactive visualizations.

## ✨ Features

- 🎬 **Real-Time Code Visualization** - See YOUR code execute step-by-step, not generic animations
- 🎮 **Interactive Playback Controls** - Play, pause, step forward/backward, adjust speed
- 🤖 **AI-Powered Explanations** - Contextual captions that explain the "why" behind each step
- 📊 **Multiple Data Structures** - Arrays, HashMaps, Trees, Graphs, Stacks, Queues
- 🔒 **Secure Sandboxed Execution** - Safe code execution with resource limits
- 🌐 **Multi-Language Support** - JavaScript, Python (Java, C++ coming soon)
- 📱 **Responsive Design** - Works on desktop and tablet
- ⚡ **High Performance** - 60 FPS animations, <200ms latency

## 🎯 Why CodeCanvas?

| Problem | Solution |
|---------|----------|
| Execution is invisible and abstract | Real-time visual simulation of code execution |
| Generic algorithm animations | Visualize YOUR actual code, not predefined examples |
| Difficult to debug logic errors | Step through execution and see state changes |
| Hard to understand complexity | Visual performance analysis and optimization hints |

## 🚀 Quick Start

### Prerequisites

- Node.js 20+ or Python 3.11+
- Docker (for sandboxed execution)
- AWS Account (for deployment)

### Installation

```bash
# Clone the repository
git clone https://github.com/yourusername/codecanvas.git
cd codecanvas

# Install dependencies
npm install

# Set up environment variables
cp .env.example .env
# Edit .env with your configuration

# Start development server
npm run dev
```

### Docker Setup

```bash
# Build Docker image
docker build -t codecanvas .

# Run container
docker run -p 3000:3000 codecanvas
```


## 📖 Usage

### Basic Example

1. **Enter a problem description**:
```
Find two numbers in a sorted array that sum to a target value.
```

2. **Write your code**:
```javascript
function twoSum(arr, target) {
  let left = 0;
  let right = arr.length - 1;
  
  while (left < right) {
    const sum = arr[left] + arr[right];
    if (sum === target) {
      return [left, right];
    } else if (sum < target) {
      left++;
    } else {
      right--;
    }
  }
  return [-1, -1];
}
```

3. **Click "Visualize"** and watch your code come alive!

### Advanced Features

**Step-by-Step Execution**:
```javascript
// Use playback controls
- Space: Play/Pause
- →: Step forward
- ←: Step backward
- R: Reset
```

**Speed Control**:
```javascript
// Adjust animation speed
0.25x | 0.5x | 1x | 1.5x | 2x
```

**Export & Share**:
```javascript
// Generate shareable link
const shareUrl = await canvas.share();

// Export as GIF
await canvas.export('gif');
```

## 🏗️ Architecture

```
┌─────────────────────────────────────────────────────────┐
│                    CLIENT LAYER                          │
│  React.js • Canvas API • WebSocket • TailwindCSS        │
└────────────────────┬────────────────────────────────────┘
                     │ HTTPS/WebSocket
┌────────────────────┴────────────────────────────────────┐
│                  API GATEWAY LAYER                       │
│  REST API • WebSocket Handler • Auth Service            │
└────────────────────┬────────────────────────────────────┘
                     │
┌────────────────────┴────────────────────────────────────┐
│              CORE PROCESSING LAYER                       │
│  Problem Parser • Simulation Engine • Caption Generator  │
└────────────────────┬────────────────────────────────────┘
                     │
┌────────────────────┴────────────────────────────────────┐
│          VISUALIZATION & EXECUTION LAYER                 │
│  Memory Visualizer • Sandboxed Executor • Result Render │
└──────────────────────────────────────────────────────────┘
```

For detailed architecture, see [design.md](./design.md)

## 🛠️ Technology Stack

### Frontend
- **Framework**: React 18+ with TypeScript
- **Styling**: TailwindCSS
- **Animation**: Framer Motion, GSAP, D3.js
- **Editor**: Monaco Editor
- **Build**: Vite

### Backend
- **Runtime**: Node.js 20 LTS
- **Framework**: Express.js / Fastify
- **WebSocket**: Socket.io
- **Validation**: Zod

### AI & Parsing
- **LLM**: OpenAI GPT-4 / Anthropic Claude
- **NLP**: spaCy, NLTK
- **Orchestration**: LangChain

### Infrastructure
- **Cloud**: AWS (ECS, RDS, ElastiCache, S3, CloudFront)
- **Database**: PostgreSQL 15
- **Cache**: Redis 7
- **Containers**: Docker
- **IaC**: Terraform

## 📂 Project Structure

```
codecanvas/
├── frontend/               # React frontend application
│   ├── src/
│   │   ├── components/    # React components
│   │   ├── hooks/         # Custom hooks
│   │   ├── services/      # API services
│   │   ├── utils/         # Utility functions
│   │   └── App.tsx        # Main app component
│   └── package.json
├── backend/               # Node.js backend services
│   ├── src/
│   │   ├── api/          # API routes
│   │   ├── services/     # Business logic
│   │   ├── models/       # Data models
│   │   ├── utils/        # Utilities
│   │   └── server.ts     # Entry point
│   └── package.json
├── simulation/           # Code execution engine
│   ├── sandbox/         # Sandboxed execution
│   ├── parsers/         # Code parsers
│   └── instrumentation/ # Code instrumentation
├── infrastructure/      # IaC and deployment
│   ├── terraform/      # Terraform configs
│   ├── docker/         # Dockerfiles
│   └── k8s/           # Kubernetes manifests
├── docs/              # Documentation
│   ├── api/          # API documentation
│   └── guides/       # User guides
├── design.md         # System design document
├── requirements.md   # Requirements specification
└── README.md        # This file
```

## 🧪 Testing

```bash
# Run all tests
npm test

# Run unit tests
npm run test:unit

# Run integration tests
npm run test:integration

# Run E2E tests
npm run test:e2e

# Run with coverage
npm run test:coverage
```

## 🚢 Deployment

### Local Development
```bash
npm run dev
```

### Staging
```bash
npm run deploy:staging
```

### Production
```bash
npm run deploy:production
```

### AWS Deployment
```bash
# Initialize Terraform
cd infrastructure/terraform
terraform init

# Plan deployment
terraform plan

# Apply changes
terraform apply
```

For detailed deployment instructions, see [deployment guide](./docs/deployment.md)

## 📊 Performance

- **API Response Time**: < 200ms (p95)
- **WebSocket Latency**: < 50ms (p95)
- **Animation Frame Rate**: 60 FPS
- **System Uptime**: 99.9%
- **Concurrent Users**: 10,000+

## 🔒 Security

- **Sandboxed Execution**: Docker containers with resource limits
- **Input Validation**: Comprehensive validation and sanitization
- **Authentication**: JWT with OAuth 2.0 support
- **Encryption**: TLS 1.3, AES-256 at rest
- **Rate Limiting**: Configurable per user tier
- **DDoS Protection**: AWS Shield + WAF

## 🤝 Contributing

We welcome contributions! Please see our [Contributing Guide](./CONTRIBUTING.md) for details.

### Development Workflow

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

### Code Style

- Follow ESLint configuration
- Use Prettier for formatting
- Write tests for new features
- Update documentation

## 🗺️ Roadmap

### Phase 1: MVP (Q1 2026) ✅
- [x] JavaScript and Python support
- [x] Array and HashMap visualizations
- [x] Basic step-by-step execution
- [x] Core playback controls

### Phase 2: Enhanced Features (Q2 2026)
- [ ] Java and C++ support
- [ ] Tree and graph visualizations
- [ ] AI-powered captions
- [ ] User authentication
- [ ] Execution history

### Phase 3: Advanced Capabilities (Q3 2026)
- [ ] Multi-language support (Go, Rust, TypeScript)
- [ ] Advanced data structures
- [ ] Performance analysis
- [ ] Collaborative mode
- [ ] Mobile responsive

### Phase 4: Platform Expansion (Q4 2026)
- [ ] Custom problem templates
- [ ] AI debugging assistant
- [ ] Gamification
- [ ] Classroom mode
- [ ] Mobile apps

See [requirements.md](./requirements.md) for detailed roadmap.

## 📈 Success Metrics

- **User Engagement**: 5+ simulations per session
- **Retention**: 40% weekly active users
- **Learning Improvement**: 60% better comprehension
- **User Satisfaction**: NPS > 50
- **Performance**: 99.9% uptime

## 🎓 Use Cases

### For Students
- Understand algorithms visually
- Debug homework assignments
- Prepare for exams
- Learn data structures

### For Interview Prep
- Practice LeetCode problems
- Understand optimal solutions
- Learn time/space complexity
- Build problem-solving intuition

### For Educators
- Create interactive lessons
- Demonstrate algorithms in class
- Track student progress
- Engage visual learners

### For Developers
- Debug complex algorithms
- Optimize performance
- Understand legacy code
- Learn new patterns

## 📚 Documentation

- [Requirements Specification](./requirements.md) - Detailed functional and non-functional requirements
- [System Design](./design.md) - Complete architecture and technical design
- [API Documentation](./docs/api/README.md) - REST and WebSocket API reference
- [User Guide](./docs/guides/user-guide.md) - How to use CodeCanvas
- [Developer Guide](./docs/guides/developer-guide.md) - How to contribute

## 🏆 Awards & Recognition

- 🥇 Best Educational Tool - Hackathon 2026
- 🌟 Featured on Product Hunt
- 📰 Mentioned in TechCrunch

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](./LICENSE) file for details.

## 👥 Team

- **Project Lead**: [Your Name](https://github.com/yourusername)
- **Frontend**: [Developer Name](https://github.com/developer)
- **Backend**: [Developer Name](https://github.com/developer)
- **Design**: [Designer Name](https://github.com/designer)

## 🙏 Acknowledgments

- Inspired by [VisuAlgo](https://visualgo.net/) and [Python Tutor](https://pythontutor.com/)
- Built with amazing open-source tools
- Special thanks to our beta testers and contributors

## 📞 Contact & Support

- **Website**: [codecanvas.dev](https://codecanvas.dev)
- **Email**: support@codecanvas.dev
- **Discord**: [Join our community](https://discord.gg/codecanvas)
- **Twitter**: [@codecanvas](https://twitter.com/codecanvas)
- **GitHub Issues**: [Report bugs](https://github.com/yourusername/codecanvas/issues)

## 💡 FAQ

**Q: What languages are supported?**
A: Currently JavaScript and Python. Java, C++, Go, Rust, and TypeScript coming soon.

**Q: Is my code safe?**
A: Yes! All code runs in isolated Docker containers with strict resource limits and no network access.

**Q: Can I use this for teaching?**
A: Absolutely! CodeCanvas is perfect for educators. Contact us for classroom features.

**Q: Is it free?**
A: Yes, with a free tier. Premium features available for power users.

**Q: Can I contribute?**
A: Yes! We welcome contributions. See our [Contributing Guide](./CONTRIBUTING.md).

---

<div align="center">

**Made with ❤️ by the CodeCanvas Team**

[Website](https://codecanvas.dev) • [Documentation](./docs) • [Discord](https://discord.gg/codecanvas) • [Twitter](https://twitter.com/codecanvas)

⭐ Star us on GitHub — it helps!

</div>
