[vvv.html](https://github.com/user-attachments/files/27087590/vvv.html)
# servantsofthemistressss
we are a wholesome community of normal ish people that find joy in serving mistress Valkyr
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Divine Realm - Character Bios</title>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Playfair+Display:wght@700&family=Cinzel:wght@400;700&display=swap');

        :root {
            --bg: #0a0a0a;
            --accent: #9b1c9e;
            --gold: #d4af37;
        }

        * { margin: 0; padding: 0; box-sizing: border-box; }

        body {
            background: linear-gradient(135deg, #0a0a0a 0%, #1a0033 100%);
            color: #eee;
            font-family: 'Cinzel', serif;
            min-height: 100vh;
            padding: 20px;
        }

        header {
            text-align: center;
            margin-bottom: 40px;
            padding: 20px;
            background: rgba(0,0,0,0.7);
            border-bottom: 3px solid var(--gold);
        }

        h1 {
            font-family: 'Playfair Display', serif;
            font-size: 3.5rem;
            color: var(--gold);
            text-shadow: 0 0 20px var(--accent);
            letter-spacing: 4px;
        }

        .subtitle {
            color: #bbb;
            font-size: 1.3rem;
            margin-top: 10px;
        }

        .grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(320px, 1fr));
            gap: 25px;
            max-width: 1400px;
            margin: 0 auto;
        }

        .card {
            background: rgba(20, 20, 40, 0.95);
            border-radius: 16px;
            overflow: hidden;
            box-shadow: 0 10px 30px rgba(155, 28, 158, 0.3);
            transition: transform 0.4s, box-shadow 0.4s;
            border: 2px solid rgba(212, 175, 55, 0.2);
        }

        .card:hover {
            transform: translateY(-12px);
            box-shadow: 0 20px 50px rgba(155, 28, 158, 0.5);
        }

        .pfp {
            width: 100%;
            height: 320px;
            object-fit: cover;
            border-bottom: 4px solid var(--accent);
        }

        .card-content {
            padding: 22px;
        }

        .name {
            font-size: 1.9rem;
            color: var(--gold);
            margin-bottom: 12px;
            text-align: center;
        }

        .bio {
            line-height: 1.7;
            color: #ddd;
            min-height: 200px;
            margin-bottom: 20px;
        }

        .edit-btn {
            display: block;
            width: 100%;
            padding: 12px;
            background: linear-gradient(45deg, var(--accent), #c026d3);
            color: white;
            border: none;
            border-radius: 8px;
            cursor: pointer;
            font-family: inherit;
            font-size: 1.1rem;
            transition: all 0.3s;
        }

        .edit-btn:hover {
            background: linear-gradient(45deg, #c026d3, var(--accent));
            transform: scale(1.03);
        }

        /* Modal */
        .modal {
            display: none;
            position: fixed;
            top: 0; left: 0;
            width: 100%; height: 100%;
            background: rgba(0,0,0,0.9);
            z-index: 1000;
            align-items: center;
            justify-content: center;
        }

        .modal-content {
            background: #1a0033;
            padding: 30px;
            border-radius: 16px;
            width: 90%;
            max-width: 500px;
            border: 3px solid var(--gold);
        }

        .modal h2 {
            color: var(--gold);
            margin-bottom: 20px;
            text-align: center;
        }

        .modal input, .modal textarea {
            width: 100%;
            padding: 12px;
            margin: 12px 0;
            background: #220044;
            border: 2px solid var(--accent);
            color: white;
            border-radius: 8px;
            font-family: inherit;
        }

        .modal textarea {
            min-height: 220px;
            resize: vertical;
        }

        .modal-buttons {
            display: flex;
            gap: 15px;
            margin-top: 25px;
        }

        .save-btn {
            background: #22c55e;
            color: white;
            flex: 1;
            padding: 14px;
            font-size: 1.1rem;
            border: none;
            border-radius: 8px;
            cursor: pointer;
        }

        .cancel-btn {
            background: #ef4444;
            color: white;
            flex: 1;
            padding: 14px;
            font-size: 1.1rem;
            border: none;
            border-radius: 8px;
            cursor: pointer;
        }

        .reset-btn {
            margin-top: 40px;
            background: #444;
            color: #ccc;
            padding: 12px 24px;
            border: none;
            border-radius: 8px;
            cursor: pointer;
            display: block;
            margin: 0 auto;
            font-size: 1rem;
        }

        footer {
            text-align: center;
            margin-top: 60px;
            color: #666;
            font-size: 0.9rem;
        }
    </style>
</head>
<body>
    <header>
        <h1>THE DIVINE REALM</h1>
        <p class="subtitle">Meet the Eternal Beings • Edit Their Legends</p>
    </header>

    <div class="grid" id="bios-grid"></div>

    <button class="reset-btn" onclick="resetAllBios()">Reset All Bios to Default</button>

    <!-- Edit Modal -->
    <div class="modal" id="edit-modal">
        <div class="modal-content">
            <h2 id="modal-title">Edit Legend</h2>
            <input type="text" id="edit-name" placeholder="Name">
            <textarea id="edit-bio" placeholder="Write their bio / legend here..."></textarea>
            
            <div class="modal-buttons">
                <button class="cancel-btn" onclick="closeModal()">Cancel</button>
                <button class="save-btn" onclick="saveEdit()">Save Changes</button>
            </div>
        </div>
    </div>

    <footer>
        Changes are saved automatically in your browser.<br>
        Only you can see your custom edits on this device.
    </footer>

    <script>
        let characters = [
            {
                id: 1,
                name: "Valkyr",
                title: "Mistress and Goddess",
                pfp: "https://www.tiktok.com/@angxart111", // TikTok profile (may not load directly)
                bio: "I am Valkyr, the supreme Mistress and Goddess who commands desire, power, and absolute submission. Those who kneel before me find both ecstasy and ruin. My will is law. My gaze breaks souls.",
                isValkyr: true
            },
            {
                id: 2,
                name: "Enter Name",
                pfp: "https://picsum.photos/id/1015/800/600",
                bio: "Write the bio here...",
                isValkyr: false
            },
            {
                id: 3,
                name: "Enter Name",
                pfp: "https://picsum.photos/id/201/800/600",
                bio: "Write the bio here...",
                isValkyr: false
            },
            {
                id: 4,
                name: "Enter Name",
                pfp: "https://picsum.photos/id/251/800/600",
                bio: "Write the bio here...",
                isValkyr: false
            },
            {
                id: 5,
                name: "Enter Name",
                pfp: "https://picsum.photos/id/669/800/600",
                bio: "Write the bio here...",
                isValkyr: false
            }
        ];

        function loadBios() {
            const saved = localStorage.getItem('divineBios');
            if (saved) {
                const parsed = JSON.parse(saved);
                characters = characters.map(char => {
                    const savedChar = parsed.find(s => s.id === char.id);
                    if (savedChar) {
                        char.name = savedChar.name;
                        char.bio = savedChar.bio;
                    }
                    return char;
                });
            }
        }

        function saveBios() {
            localStorage.setItem('divineBios', JSON.stringify(characters));
        }

        function renderBios() {
            const grid = document.getElementById('bios-grid');
            grid.innerHTML = '';

            characters.forEach(char => {
                const card = document.createElement('div');
                card.className = 'card';
                card.innerHTML = `
                    <img src="${char.pfp}" alt="${char.name}" class="pfp" 
                         onerror="this.src='https://picsum.photos/id/1005/800/600'">
                    <div class="card-content">
                        <div class="name">${char.name}</div>
                        ${char.isValkyr ? `<div style="color:#c026d3; text-align:center; margin-bottom:15px; font-size:1.1rem;">${char.title}</div>` : ''}
                        <div class="bio">${char.bio}</div>
                        <button class="edit-btn" onclick="openEditModal(${char.id})">✎ Edit Name & Bio</button>
                    </div>
                `;
                grid.appendChild(card);
            });
        }

        let currentEditingId = null;

        function openEditModal(id) {
            currentEditingId = id;
            const char = characters.find(c => c.id === id);
            if (!char) return;

            document.getElementById('edit-name').value = char.name;
            document.getElementById('edit-bio').value = char.bio;
            document.getElementById('modal-title').textContent = `Edit ${char.isValkyr ? 'Valkyr' : 'Character'}`;
            document.getElementById('edit-modal').style.display = 'flex';
        }

        function closeModal() {
            document.getElementById('edit-modal').style.display = 'none';
            currentEditingId = null;
        }

        function saveEdit() {
            if (!currentEditingId) return;

            const newName = document.getElementById('edit-name').value.trim();
            const newBio = document.getElementById('edit-bio').value.trim();

            if (newName === '') {
                alert("Name cannot be empty.");
                return;
            }

            const char = characters.find(c => c.id === currentEditingId);
            if (char) {
                char.name = newName;
                char.bio = newBio || "No bio written yet...";
            }

            saveBios();
            renderBios();
            closeModal();
        }

        function resetAllBios() {
            if (confirm("Reset ALL bios back to default? This cannot be undone.")) {
                localStorage.removeItem('divineBios');
                location.reload();
            }
        }

        window.onclick = function(event) {
            const modal = document.getElementById('edit-modal');
            if (event.target === modal) closeModal();
        };

        document.addEventListener('keydown', function(e) {
            if (e.key === "Escape") {
                const modal = document.getElementById('edit-modal');
                if (modal.style.display === 'flex') closeModal();
            }
        });

        // Initialize
        window.onload = function() {
            loadBios();
            renderBios();
        };
    </script>
</body>
</html>
