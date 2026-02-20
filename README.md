# TaskFlow - Mobile-Friendly Docker Application

A modern, responsive task management web application built with HTML, CSS, JavaScript, and Docker. Perfect for managing your daily tasks with a beautiful UI that works seamlessly on all devices.

## 📱 Features

- ✅ **Responsive Design** - Works perfectly on desktop, tablet, and mobile devices
- 🎯 **Task Management** - Add, complete, and delete tasks with ease
- 🔴 **Priority Levels** - Set priority (High, Medium, Low) for each task
- 📊 **Statistics Dashboard** - Track total, completed, and pending tasks
- 🎨 **Modern UI** - Beautiful gradient design with smooth animations
- 💾 **Local Storage** - Tasks persist in browser's local storage
- 🐳 **Docker Ready** - Fully containerized for easy deployment
- ⚡ **Fast & Lightweight** - Minimal dependencies, optimized performance
- 🔒 **Secure** - Built with security best practices (XSS prevention)
- ♿ **Accessible** - Semantic HTML and ARIA labels for accessibility

## 🚀 Quick Start

### Prerequisites

- Docker and Docker Compose installed on your system
- Or: Node.js 18+ and npm (for local development)

### Option 1: Using Docker Compose (Recommended)

```bash
# Navigate to project directory
cd Docker

# Build and run the application
docker-compose up --build

# The app will be available at http://localhost:3000
```

To stop the application:
```bash
docker-compose down
```

### Option 2: Using Docker Build

```bash
# Build the Docker image
docker build -t taskflow-app .

# Run the container
docker run -p 3000:3000 --name taskflow taskflow-app

# Access the app at http://localhost:3000

# To stop the container
docker stop taskflow
docker rm taskflow
```

### Option 3: Local Development (Without Docker)

```bash
# Install dependencies
npm install

# Start the development server
npm start

# The app will be available at http://localhost:3000
```

For development with auto-reload:
```bash
npm install -g nodemon
npm run dev
```

## 📁 Project Structure

```
Docker/
├── app.js                    # Express server
├── package.json             # Project dependencies
├── Dockerfile               # Docker configuration
├── docker-compose.yml       # Docker Compose configuration
├── .dockerignore            # Files to exclude from Docker build
├── .gitignore              # Git ignore rules
├── README.md               # This file
└── public/
    ├── index.html          # Main HTML file
    ├── css/
    │   └── style.css       # Responsive CSS styles
    └── js/
        └── script.js       # JavaScript functionality
```

## 🛠️ Technology Stack

- **Backend:** Node.js with Express.js
- **Frontend:** HTML5, CSS3, Vanilla JavaScript
- **Containerization:** Docker & Docker Compose
- **Storage:** LocalStorage API (client-side)

## 📖 How to Use

1. **Add a Task**
   - Enter task text in the input field
   - Select priority level (Low, Medium, High)
   - Click the "+" button or press Enter
   - Task is automatically saved

2. **Complete a Task**
   - Click the checkbox next to a task
   - Task will be marked as completed (strikethrough + opacity)

3. **Delete a Task**
   - Click the delete (🗑️) button
   - Confirm deletion when prompted

4. **Filter Tasks**
   - Click "All" to see all tasks
   - Click "Active" to see incomplete tasks
   - Click "Completed" to see finished tasks

5. **View Statistics**
   - Dashboard shows total, completed, and pending tasks
   - Updates in real-time as you manage tasks

## 🎨 Responsive Breakpoints

- **Desktop** (1200px+): Full layout with side-by-side components
- **Tablet** (768px - 1199px): Optimized for medium screens
- **Mobile** (480px - 767px): Compact layout for phones
- **Small Mobile** (<480px): Fully optimized single-column layout

## 🐳 Docker Commands

### Build the image
```bash
docker build -t taskflow-app .
```

### Run container with custom port
```bash
docker run -p 8080:3000 taskflow-app
```

### View running containers
```bash
docker ps
```

### View container logs
```bash
docker logs taskflow-app
```

### Stop and remove containers
```bash
docker-compose down -v
```

### Build without cache
```bash
docker-compose build --no-cache
```

## 🔧 Environment Variables

- `NODE_ENV`: Set to `production` by default
- `PORT`: Application port (default: 3000)

To modify, edit `docker-compose.yml` or create a `.env` file:
```
NODE_ENV=production
PORT=3000
```

## 📱 Mobile Optimization

- Viewport meta tag for proper scaling
- Touch-friendly button sizes (minimum 44x44px)
- Flexible layouts using CSS Grid and Flexbox
- Optimized font sizes for readability
- Reduced motion support
- Fast touch response times

## ♿ Accessibility Features

- Semantic HTML structure
- ARIA labels for interactive elements
- Color contrast ratios meet WCAG guidelines
- Keyboard navigation support
- Focus indicators for interactive elements
- Form labels properly associated with inputs

## 🚀 Deployment

### Deploy to AWS EC2
```bash
# SSH into your EC2 instance
ssh -i your-key.pem ec2-user@your-instance-ip

# Clone your repository
git clone <repo-url>
cd Docker

# Install Docker
sudo yum update -y
sudo yum install docker -y
sudo systemctl start docker

# Build and run with Docker Compose
sudo docker-compose up -d
```

### Deploy to DigitalOcean
```bash
# Set up droplet with Docker pre-installed
# Then:
git clone <repo-url>
cd Docker
docker-compose up -d
```

### Deploy to Heroku
```bash
heroku create your-app-name
heroku container:push web
heroku container:release web
heroku open
```

## 🔒 Security Considerations

- XSS Prevention: HTML escaping implemented
- No external script dependencies (reduces attack surface)
- Security headers recommended for production
- User input validation on client-side
- HTTPS recommended for production deployment

## 📊 Health Check

The Docker container includes a health check endpoint that verifies the application is running:

```bash
docker inspect --format='{{.State.Health.Status}}' taskflow-app
```

## 🐛 Troubleshooting

### Port already in use
```bash
# Find process using port 3000
lsof -i :3000

# Change port in docker-compose.yml
# Change "3000:3000" to "8080:3000" or desired port
```

### Container exits immediately
```bash
# Check logs for errors
docker-compose logs app

# Verify package.json has correct main entry
```

### Tasks not persisting
- Tasks are stored in browser's LocalStorage
- Clear browser cache will delete tasks
- Try incognito/private window to test a fresh instance

### CSS/JS not loading
- Clear browser cache (Ctrl+Shift+Delete)
- Check browser console for errors (F12)
- Verify static files are in public/ directory

## 📈 Performance Optimization

- Minified CSS and JS in production
- Lazy loading for images
- Efficient DOM manipulation
- Debounced input handling
- Optimized animations with transform/opacity

## 🤝 Contributing

Feel free to fork this project and submit pull requests. All contributions are welcome!

## 📄 License

This project is licensed under the MIT License - see the LICENSE file for details.

## 💡 Future Enhancements

- User authentication
- Cloud synchronization
- Task categories/tags
- Recurring tasks
- Task reminders
- Dark mode
- Multi-language support
- Task analytics
- Export to PDF/CSV
- Collaborative features

## 📞 Support

If you encounter any issues, please:
1. Check the Troubleshooting section
2. Review Docker logs: `docker-compose logs`
3. Check browser console (F12) for JavaScript errors
4. Verify all files are properly created in the project structure

## 🎉 Acknowledgments

- Modern CSS techniques and responsive design principles
- Docker best practices for containerization
- Accessibility standards from WCAG

---

**Made with ❤️ using Docker and modern web technologies**

Last Updated: February 2026
#   d o c k e r  
 