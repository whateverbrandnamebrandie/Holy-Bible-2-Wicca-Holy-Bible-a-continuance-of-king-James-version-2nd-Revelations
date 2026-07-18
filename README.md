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
                from { or          }
            
            .momomomomomomomomodaoddaall--ccllo         
            .momomomomomomomomomomomomomomomomomoommoommoommoomoommoommoommoommoomomoommoommooddaall--bnbububububububububububububububububububububububububububububububububububububbubububububububububububububububububububububububububububububububububububububububububububbuubbuubbuubbuubbuubbuubbuubbuubbuubuubbuubbuubbuubbuubbuubbuubbuubbuubbuubbuubbuubbuubbuubbuubbuubbuubbuubbuubbuubbuubbuubbuubbuubbuubbuubbuubbuubbuubbuubbuubbuubbuubbuubbuubbuuttt
