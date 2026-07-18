# Holy-Bible-2-Wicca-Holy-Bible-a-continuance-of-king-James-version-2nd-Revelations
Autobiography

// Smooth scrolling and navigation
document.querySelectorAll('a.nav-link').forEach(link => {
    link.addEventListener('click', function(e) {
        e.preventDefault();
        const targetId = this.getAttribute('href');
        const targetSection = document.querySelector(targetId);
        
        if (targetSection) {
            // Remove active class from all links
            document.querySelectorAll('a.nav-link').forEach(l => l.classList.remove('active'));
            // Add active class to clicked link
            this.classList.add('active');
            
            // Smooth scroll to section
            targetSection.scrollIntoView({
                behavior: 'smooth',
                block: 'start'
            });
        }
    });
});

// Update active nav link on scroll
window.addEventListener('scroll', () => {
    let current = '';
    const sections = document.querySelectorAll('section[id]');
    
    sections.forEach(section => {
        const sectionTop = section.offsetTop;
        const sectionHeight = section.clientHeight;
        
        if (scrollY >= sectionTop - 200) {
            current = section.getAttribute('id');
        }
    });
    
    document.querySelectorAll('a.nav-link').forEach(link => {
        link.classList.remove('active');
        if (link.getAttribute('href') === '#' + current) {
            link.classList.add('active');
        }
    });
});

// Episode card hover effects
document.querySelectorAll('.episode-card').forEach(card => {
    card.addEventListener('mouseenter', function() {
        this.style.transform = 'translateY(-10px)';
        this.style.boxShadow = '0 15px 40px rgba(212, 175, 55, 0.3)';
    });
    
    card.addEventListener('mouseleave', function() {
        this.style.transform = 'translateY(0)';
        this.style.boxShadow = 'none';
    });
});

// Course card interactive elements
document.querySelectorAll('.course-card').forEach(card => {
    const enrollBtn = card.querySelector('.enroll-btn');
    
    card.addEventListener('mouseenter', function() {
        this.style.transform = 'scale(1.05)';
        this.style.boxShadow = '0 15px 40px rgba(212, 175, 55, 0.2)';
    });
    
    card.addEventListener('mouseleave', function() {
        this.style.transform = 'scale(1)';
        this.style.boxShadow = 'none';
    });
    
    enrollBtn.addEventListener('click', function(e) {
        e.preventDefault();
        const courseName = card.querySelector('h3').textContent;
        showCourseModal(courseName);
    });
});

// Teaching card animation
document.querySelectorAll('.teaching-card').forEach((card, index) => {
    card.style.opacity = '0';
    card.style.animation = `fadeInUp 0.6s ease-out ${index * 0.1}s forwards`;
});

// Add fadeInUp animation to stylesheet dynamically
const style = document.createElement('style');
style.innerHTML = `
    @keyframes fadeInUp {
        from {
            opacity: 0;
            transform: translateY(30px);
        }
        to {
            opacity: 1;
            transform: translateY(0);
        }
    }
    
    @keyframes shimmer {
        0% {
            background-position: -1000px 0;
        }
        100% {
            background-position: 1000px 0;
        }
    }
    
    .loading {
        background: linear-gradient(90deg, #404040 25%, #505050 50%, #404040 75%);
        background-size: 1000px 100%;
        animation: shimmer 2s infinite;
    }
`;
document.head.appendChild(style);

// Modal functionality for courses
function showCourseModal(courseName) {
    // Check if modal already exists
    let modal = document.getElementById('course-modal');
    if (!modal) {
        modal = document.createElement('div');
        modal.id = 'course-modal';
        modal.className = 'modal';
        modal.innerHTML = `
            <div class="modal-content">
                <span class="modal-close">&times;</span>
                <h2 id="modal-course-name"></h2>
                <p>Coming Soon: Full course curriculum, lessons, and interactive practices will be available.</p>
                <p>This course integrates teachings from Holy Bible 2 with active witchcraft instruction.</p>
                <button class="modal-btn" onclick="subscribeToUpdates()">Notify Me When Available</button>
            </div>
        </modal>
    }
    
    document.getElementById('modal-course-name').textContent = courseName;
    modal.style.display = 'block';
    
    // Add modal styles if not already present
    if (!document.getElementById('modal-styles')) {
        const modalStyles = document.createElement('style');
        modalStyles.id = 'modal-styles';
        modalStyles.innerHTML = `
            .modal {
                display: none;
                position: fixed;
                z-index: 1000;
                left: 0;
                top: 0;
                width: 100%;
                height: 100%;
                background-color: rgba(0, 0, 0, 0.8);
                animation: fadeIn 0.3s ease-in;
            }
            
            @keyframes fadeIn {
                from { opacity: 0; }
                to { opacity: 1; }
            }
            
            .modal-content {
                background-color: #16213e;
                margin: 10% auto;
                padding: 40px;
                border: 2px solid #d4af37;
                width: 80%;
                max-width: 600px;
                border-radius: 10px;
                box-shadow: 0 10px 50px rgba(0, 0, 0, 0.5);
                animation: slideDown 0.4s ease-out;
            }
            
            @keyframes slideDown {
                from {
                    transform: translateY(-50px);
                    opacity: 0;
                }
                to {
                    transform: translateY(0);
                    opacity: 1;
                }
            }
            
            .modal-close {
                color: #d4af37;
                float: right;
                font-size: 28px;
                font-weight: bold;
                cursor: pointer;
                transition: color 0.3s;
            }
            
            .modal-close:hover {
                color: #e5c158;
            }
            
            .modal-btn {
                background-color: #d4af37;
                color: #1a1a2e;
                padding: 12px 30px;
                border: none;
                border-radius: 5px;
                cursor: pointer;
                font-weight: bold;
                font-size: 1em;
                margin-top: 20px;
                transition: all 0.3s ease;
            }
            
            .modal-btn:hover {
                background-color: #e5c158;
                transform: scale(1.05);
            }
        `;
        document.head.appendChild(modalStyles);
    }
    
    // Close modal on X click
    const closeBtn = modal.querySelector('.modal-close');
    closeBtn.addEventListener('click', function() {
        modal.style.display = 'none';
    });
    
    // Close modal on outside click
    window.addEventListener('click', function(event) {
        if (event.target === modal) {
            modal.style.display = 'none';
        }
    });
}

// Subscribe to updates
function subscribeToUpdates() {
    const email = prompt('Enter your email to be notified of course launches:');
    if (email) {
        console.log('Subscription requested for:', email);
        alert('Thank you for your interest! We will notify you when this course becomes available.');
        document.getElementById('course-modal').style.display = 'none';
    }
}

// Parallax effect for header
window.addEventListener('scroll', function() {
    const header = document.querySelector('header');
    const scrollPosition = window.scrollY;
    header.style.backgroundPosition = '0 ' + (scrollPosition * 0.5) + 'px';
});

// Intersection Observer for fade-in animations
const observerOptions = {
    threshold: 0.1,
    rootMargin: '0px 0px -100px 0px'
};

const observer = new IntersectionObserver(function(entries) {
    entries.forEach(entry => {
        if (entry.isIntersecting) {
            entry.target.style.opacity = '1';
            entry.target.style.transform = 'translateY(0)';
            observer.unobserve(entry.target);
        }
    });
}, observerOptions);

// Observe episode and course cards
document.querySelectorAll('.episode-card, .course-card, .teaching-card').forEach(card => {
    card.style.opacity = '0';
    card.style.transform = 'translateY(20px)';
    card.style.transition = 'opacity 0.6s ease-out, transform 0.6s ease-out';
    observer.observe(card);
});

// Interactive timeline for episodes
function createEpisodeTimeline() {
    const episodes = document.querySelectorAll('.episode-card');
    let currentEpisode = 0;
    
    // Add keyboard navigation
    document.addEventListener('keydown', function(event) {
        if (event.key === 'ArrowRight' && currentEpisode < episodes.length - 1) {
            currentEpisode++;
            episodes[currentEpisode].scrollIntoView({ behavior: 'smooth', block: 'nearest' });
        } else if (event.key === 'ArrowLeft' && currentEpisode > 0) {
            currentEpisode--;
            episodes[currentEpisode].scrollIntoView({ behavior: 'smooth', block: 'nearest' });
        }
    });
}

// Initialize on page load
document.addEventListener('DOMContentLoaded', function() {
    createEpisodeTimeline();
    
    // Add loading effect to images if present
    const images = document.querySelectorAll('img');
    images.forEach(img => {
        img.addEventListener('load', function() {
            this.style.animation = 'fadeIn 0.5s ease-in';
        });
    });
    
    console.log('Holy Bible 2 Platform - Interactive features loaded');
});

// Scroll progress indicator
const progressBar = document.createElement('div');
progressBar.id = 'scroll-progress';
progressBar.style.cssText = `
    position: fixed;
    top: 0;
    left: 0;
    height: 3px;
    background: linear-gradient(90deg, #d4af37, #e5c158);
    width: 0%;
    z-index: 999;
`;
document.body.appendChild(progressBar);

window.addEventListener('scroll', function() {
    const scrollHeight = document.documentElement.scrollHeight - document.documentElement.clientHeight;
    const scrolled = (window.scrollY / scrollHeight) * 100;
    progressBar.style.width = scrolled + '%';
});

// Add accessibility: keyboard shortcuts information
console.log('Keyboard Shortcuts:');
console.log('← → Arrow keys: Navigate between episodes');
console.log('# + Section ID: Jump to section (e.g., #episodes)');

// Easter egg: reveal hidden content on specific key combination
let keySequence = [];
const secretKey = ['h', 'o', 'l', 'y'];

document.addEventListener('keydown', function(event) {
    keySequence.push(event.key.toLowerCase());
    
    if (keySequence.length > secretKey.length) {
        keySequence.shift();
    }
    
    if (keySequence.join('') === secretKey.join('')) {
        revealSecretMessage();
        keySequence = [];
    }
});

function revealSecretMessage() {
    const secret = document.createElement('div');
    secret.style.cssText = `
        position: fixed;
        top: 50%;
        left: 50%;
        transform: translate(-50%, -50%);
        background: linear-gradient(135deg, #1a1a2e, #16213e);
        color: #d4af37;
        padding: 40px;
        border: 2px solid #d4af37;
        border-radius: 10px;
        text-align: center;
        z-index: 2000;
        font-size: 1.2em;
        max-width: 500px;
        box-shadow: 0 0 40px rgba(212, 175, 55, 0.5);
        animation: fadeIn 0.5s ease-in;
    `;
    secret.innerHTML = `
        <p><strong>✨ You have found the hidden message ✨</strong></p>
        <p>"The unknown father on her birth certificate felt less like an absence and more like a connection, a thread leading to a realm beyond human understanding."</p>
        <p style="font-size: 0.9em; margin-top: 20px; color: #888;">- Holy Bible 2: The Unseen Tapestry</p>
        <button onclick="this.parentElement.remove()" style="
            margin-top: 20px;
            background-color: #d4af37;
            color: #1a1a2e;
            padding: 10px 20px;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            font-weight: bold;
        ">Close</button>
    `;
    document.body.appendChild(secret);
    
    setTimeout(() => {
        if (secret.parentElement) {
            secret.remove();
        }
    }, 10000);
}
