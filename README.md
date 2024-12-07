import React, { useState } from 'react';
import { 
  Moon, 
  Sun, 
  Menu, 
  X, 
  GitHub, 
  Linkedin, 
  Mail, 
  ArrowRight 
} from 'lucide-react';

// Sample project data - replace with your own
const projects = [
  {
    id: 1,
    title: 'Project Alpha',
    description: 'A cutting-edge web application that revolutionizes user interaction.',
    technologies: ['React', 'Tailwind CSS', 'TypeScript'],
    imageUrl: '/api/placeholder/600/400',
    githubLink: '#',
    liveLink: '#'
  },
  {
    id: 2,
    title: 'Data Visualization Platform',
    description: 'Interactive dashboard for complex data analysis and reporting.',
    technologies: ['D3.js', 'Node.js', 'MongoDB'],
    imageUrl: '/api/placeholder/600/400',
    githubLink: '#',
    liveLink: '#'
  },
  {
    id: 3,
    title: 'E-Commerce Solution',
    description: 'Full-stack e-commerce platform with advanced features.',
    technologies: ['React', 'GraphQL', 'Stripe'],
    imageUrl: '/api/placeholder/600/400',
    githubLink: '#',
    liveLink: '#'
  }
];

const Portfolio = () => {
  const [isDarkMode, setIsDarkMode] = useState(false);
  const [isMobileMenuOpen, setIsMobileMenuOpen] = useState(false);

  const toggleDarkMode = () => {
    setIsDarkMode(!isDarkMode);
  };

  const toggleMobileMenu = () => {
    setIsMobileMenuOpen(!isMobileMenuOpen);
  };

  return (
    <div className={`${isDarkMode ? 'dark bg-gray-900 text-white' : 'bg-white text-gray-900'} min-h-screen transition-colors duration-300`}>
      {/* Navigation */}
      <nav className="fixed top-0 left-0 right-0 z-50 bg-white/80 dark:bg-gray-900/80 backdrop-blur-md shadow-sm">
        <div className="container mx-auto px-4 py-4 flex justify-between items-center">
          <h1 className="text-2xl font-bold tracking-tight">
            Your Name
          </h1>
          
          {/* Desktop Navigation */}
          <div className="hidden md:flex items-center space-x-6">
            <a href="#about" className="hover:text-blue-600 transition">About</a>
            <a href="#projects" className="hover:text-blue-600 transition">Projects</a>
            <a href="#contact" className="hover:text-blue-600 transition">Contact</a>
            
            {/* Social Icons */}
            <div className="flex space-x-4">
              <a href="#" target="_blank" rel="noopener noreferrer" className="hover:text-blue-600">
                <GitHub size={20} />
              </a>
              <a href="#" target="_blank" rel="noopener noreferrer" className="hover:text-blue-600">
                <Linkedin size={20} />
              </a>
            </div>
            
            {/* Dark Mode Toggle */}
            <button 
              onClick={toggleDarkMode} 
              className="hover:text-blue-600 transition"
            >
              {isDarkMode ? <Sun size={20} /> : <Moon size={20} />}
            </button>
          </div>
          
          {/* Mobile Menu Toggle */}
          <div className="md:hidden">
            <button 
              onClick={toggleMobileMenu} 
              className="focus:outline-none"
            >
              {isMobileMenuOpen ? <X size={24} /> : <Menu size={24} />}
            </button>
          </div>
        </div>
        
        {/* Mobile Menu Dropdown */}
        {isMobileMenuOpen && (
          <div className="md:hidden absolute top-full left-0 right-0 bg-white dark:bg-gray-900 shadow-lg">
            <div className="flex flex-col items-center py-4 space-y-4">
              <a href="#about" className="hover:text-blue-600" onClick={toggleMobileMenu}>About</a>
              <a href="#projects" className="hover:text-blue-600" onClick={toggleMobileMenu}>Projects</a>
              <a href="#contact" className="hover:text-blue-600" onClick={toggleMobileMenu}>Contact</a>
              
              {/* Mobile Social Icons */}
              <div className="flex space-x-6 pt-2">
                <a href="#" target="_blank" rel="noopener noreferrer" className="hover:text-blue-600">
                  <GitHub size={24} />
                </a>
                <a href="#" target="_blank" rel="noopener noreferrer" className="hover:text-blue-600">
                  <Linkedin size={24} />
                </a>
              </div>
              
              {/* Mobile Dark Mode Toggle */}
              <button 
                onClick={toggleDarkMode} 
                className="hover:text-blue-600 transition"
              >
                {isDarkMode ? 'Light Mode' : 'Dark Mode'}
              </button>
            </div>
          </div>
        )}
      </nav>

      {/* Hero Section */}
      <header id="about" className="container mx-auto px-4 pt-24 pb-16 md:pt-36 md:pb-24">
        <div className="max-w-3xl mx-auto text-center">
          <h2 className="text-4xl md:text-6xl font-bold mb-6 tracking-tight">
            Hi, I'm [Your Name] <br />
            <span className="text-blue-600">Creative Developer</span>
          </h2>
          <p className="text-lg md:text-xl text-gray-600 dark:text-gray-300 mb-8 max-w-2xl mx-auto">
            I craft digital experiences that blend innovative design with robust functionality. 
            Passionate about creating solutions that make a difference.
          </p>
          <div className="flex justify-center space-x-4">
            <a 
              href="#projects" 
              className="bg-blue-600 text-white px-6 py-3 rounded-full hover:bg-blue-700 transition flex items-center"
            >
              View My Work <ArrowRight className="ml-2" size={20} />
            </a>
            <a 
              href="#contact" 
              className="border border-gray-300 dark:border-gray-600 px-6 py-3 rounded-full hover:bg-gray-100 dark:hover:bg-gray-800 transition"
            >
              Contact Me
            </a>
          </div>
        </div>
      </header>

      {/* Projects Section */}
      <section id="projects" className="container mx-auto px-4 py-16 md:py-24">
        <div className="text-center mb-12">
          <h3 className="text-3xl md:text-4xl font-bold mb-4">My Projects</h3>
          <p className="text-gray-600 dark:text-gray-300 max-w-xl mx-auto">
            A collection of projects that showcase my skills and creativity.
          </p>
        </div>
        
        <div className="grid md:grid-cols-3 gap-8">
          {projects.map((project) => (
            <div 
              key={project.id} 
              className="bg-white dark:bg-gray-800 rounded-lg shadow-lg overflow-hidden transform transition hover:scale-105"
            >
              <img 
                src={project.imageUrl} 
                alt={project.title} 
                className="w-full h-48 object-cover"
              />
              <div className="p-6">
                <h4 className="text-xl font-semibold mb-3">{project.title}</h4>
                <p className="text-gray-600 dark:text-gray-300 mb-4">
                  {project.description}
                </p>
                <div className="flex flex-wrap gap-2 mb-4">
                  {project.technologies.map((tech) => (
                    <span 
                      key={tech} 
                      className="bg-gray-100 dark:bg-gray-700 px-2 py-1 rounded-full text-xs"
                    >
                      {tech}
                    </span>
                  ))}
                </div>
                <div className="flex space-x-4">
                  <a 
                    href={project.githubLink} 
                    target="_blank" 
                    rel="noopener noreferrer"
                    className="bg-gray-100 dark:bg-gray-700 px-4 py-2 rounded-full flex items-center hover:bg-gray-200 dark:hover:bg-gray-600 transition"
                  >
                    <GitHub size={16} className="mr-2" /> GitHub
                  </a>
                  <a 
                    href={project.liveLink} 
                    target="_blank" 
                    rel="noopener noreferrer"
                    className="bg-blue-600 text-white px-4 py-2 rounded-full flex items-center hover:bg-blue-700 transition"
                  >
                    Live Site <ArrowRight size={16} className="ml-2" />
                  </a>
                </div>
              </div>
            </div>
          ))}
        </div>
      </section>

      {/* Contact Section */}
      <section 
        id="contact" 
        className="container mx-auto px-4 py-16 md:py-24 bg-gray-50 dark:bg-gray-800"
      >
        <div className="max-w-xl mx-auto text-center">
          <h3 className="text-3xl md:text-4xl font-bold mb-6">Let's Connect</h3>
          <p className="text-gray-600 dark:text-gray-300 mb-8">
            I'm always open to discussing new projects, opportunities, or just having a chat.
          </p>
          
          <div className="flex flex-col md:flex-row justify-center space-y-4 md:space-y-0 md:space-x-4">
            <a 
              href="mailto:your.email@example.com" 
              className="bg-blue-600 text-white px-6 py-3 rounded-full hover:bg-blue-700 transition flex items-center justify-center"
            >
              <Mail className="mr-2" size={20} /> Email Me
            </a>
            <a 
              href="#" 
              target="_blank" 
              rel="noopener noreferrer"
              className="border border-gray-300 dark:border-gray-600 px-6 py-3 rounded-full hover:bg-gray-100 dark:hover:bg-gray-700 transition flex items-center justify-center"
            >
              <Linkedin className="mr-2" size={20} /> LinkedIn
            </a>
          </div>
        </div>
      </section>

      {/* Footer */}
      <footer className="bg-white dark:bg-gray-900 py-8 border-t dark:border-gray-700">
        <div className="container mx-auto px-4 text-center">
          <p className="text-gray-600 dark:text-gray-400">
            © 2024 Your Name. All rights reserved.
          </p>
        </div>
      </footer>
    </div>
  );
};

export default Portfolio;

