---
layout: default
title: "Bad 90s Blog"
header_title: "All That And A Bag Of Chips"
header_subtitle: "*** NEW POSTS UPDATED WEEKLY! ***"
---

<div style="text-align: center; margin: 20px 0;">
    <div class="simple-player" style="margin: 0 auto;">
        <div class="player-title">
            🎵 RANDOM JUKEBOX 🎵
        </div>
        
        <div class="track-display" id="trackDisplay">
            CLICK RANDOM TO SELECT TRACK
        </div>
        
        <audio id="audioPlayer" style="display: none;"></audio>
        
        <div class="controls">
            <button class="play-button" onclick="togglePlay()" id="playButton">▶️ PLAY</button>
            <br>
            <div class="volume-control">
                🔇 <input type="range" class="volume-slider" id="volumeSlider" min="0" max="100" value="70" onchange="setVolume()"> 🔊
            </div>
            <button class="random-button" onclick="selectRandomTrack()">🎲 RANDOM TRACK</button>
        </div>
    </div>
</div>

<style>
    .simple-player {
        background-color: #000000;
        border: 3px outset #c0c0c0;
        padding: 12px;
        margin: 20px 0;
        color: #00ff00;
        font-family: "Courier New", monospace;
        max-width: 350px;
        text-align: center;
    }
    
    .player-title {
        background-color: #000080;
        color: #ffff00;
        padding: 5px;
        font-size: 11px;
        font-weight: bold;
        border: 1px inset #c0c0c0;
        margin-bottom: 8px;
    }
    
    .track-display {
        background-color: #000000;
        border: 1px inset #808080;
        padding: 8px;
        margin: 8px 0;
        min-height: 30px;
        color: #00ff00;
        font-size: 11px;
        display: flex;
        align-items: center;
        justify-content: center;
    }
    
    .controls {
        margin: 10px 0;
    }
    
    .play-button {
        background-color: #c0c0c0;
        border: 2px outset #c0c0c0;
        padding: 6px 12px;
        font-family: "Times New Roman", serif;
        font-weight: bold;
        font-size: 11px;
        cursor: pointer;
        color: #000000;
        margin: 0 5px;
    }
    
    .play-button:active {
        border: 2px inset #c0c0c0;
    }
    
    .play-button:hover {
        background-color: #e0e0e0;
    }
    
    .random-button {
        background-color: #008080;
        border: 2px outset #008080;
        padding: 4px 8px;
        font-family: "Times New Roman", serif;
        font-size: 10px;
        cursor: pointer;
        color: #ffffff;
        margin-top: 5px;
    }
    
    .random-button:active {
        border: 2px inset #008080;
    }
    
    .volume-control {
        margin: 8px 0;
        font-size: 10px;
        color: #00ff00;
    }
    
    .volume-slider {
        width: 120px;
        margin: 0 8px;
        accent-color: #00ff00;
    }
    
    .blink {
        animation: blink 1s linear infinite;
    }
    
    @keyframes blink {
        0% { opacity: 1; }
        50% { opacity: 0; }
        100% { opacity: 1; }
    }
</style>

<script>
    // Your FLAC music collection - UPDATE WITH YOUR ACTUAL TRACK NAMES!
    const musicLibrary = [
        { title: "Downtown Dance", file: "music/track01.flac" },
        { title: "Harbor Hymn", file: "music/track02.flac" },
        { title: "Traffic Trouble", file: "music/track03.flac" },
        { title: "Disaster Decision", file: "music/track04.flac" },
        { title: "Serious Sims", file: "music/track05.flac" },
        { title: "SimCity Segue", file: "music/track06.flac" },
        { title: "Subway Song", file: "music/track07.flac" },
        { title: "Virtual Village", file: "music/track08.flac" },
        { title: "Railroad Rap", file: "music/track09.flac" },
        { title: "City Shimmy", file: "music/track10.flac" },
        { title: "Chinatown Concerto", file: "music/track11.flac" },
        { title: "Repetition Rendition", file: "music/track12.flac" },
        { title: "Newspaper Segue", file: "music/track13.flac" },
        { title: "Mayor Mambo", file: "music/track14.flac" },
        { title: "Bluesy Berg", file: "music/track15.flac" },
        { title: "Traffic Trouble (Section A)", file: "music/track16.flac" },
        { title: "City Shimmy (Section B)", file: "music/track17.flac" },
        { title: "Unused", file: "music/track18.flac" },
        { title: "Classic Theme", file: "music/track19.flac" }
    ];

    let currentTrack = null;
    let isPlaying = false;
    
    const audio = document.getElementById('audioPlayer');
    const trackDisplay = document.getElementById('trackDisplay');
    const playButton = document.getElementById('playButton');
    
    // Select a random track
    function selectRandomTrack() {
        const randomIndex = Math.floor(Math.random() * musicLibrary.length);
        currentTrack = musicLibrary[randomIndex];
        
        // Update display
        trackDisplay.innerHTML = `<span class="blink">♪</span> ${currentTrack.title.toUpperCase()} <span class="blink">♪</span>`;
        
        // Load the track
        audio.innerHTML = `
            <source src="${currentTrack.file}" type="audio/flac">
            <source src="${currentTrack.file.replace('.flac', '.mp3')}" type="audio/mpeg">
            <source src="${currentTrack.file.replace('.flac', '.ogg')}" type="audio/ogg">
            Browser doesn't support FLAC!
        `;
        audio.load();
        
        // Reset play button
        isPlaying = false;
        playButton.textContent = '▶️ PLAY';
    }
    
    // Toggle play/pause
    function togglePlay() {
        if (!currentTrack) {
            trackDisplay.textContent = 'SELECT A TRACK FIRST!';
            setTimeout(() => {
                trackDisplay.textContent = 'CLICK RANDOM TO SELECT TRACK';
            }, 2000);
            return;
        }
        
        if (isPlaying) {
            audio.pause();
            isPlaying = false;
            playButton.textContent = '▶️ PLAY';
            trackDisplay.innerHTML = `⏸️ PAUSED: ${currentTrack.title.toUpperCase()}`;
        } else {
            audio.play().then(() => {
                isPlaying = true;
                playButton.textContent = '⏸️ PAUSE';
                trackDisplay.innerHTML = `<span class="blink">♪</span> NOW PLAYING: ${currentTrack.title.toUpperCase()} <span class="blink">♪</span>`;
            }).catch(e => {
                console.error('Playback failed:', e);
                trackDisplay.textContent = '⚠️ PLAYBACK ERROR!';
                isPlaying = false;
                playButton.textContent = '▶️ PLAY';
            });
        }
    }
    
    // When song ends
    audio.addEventListener('ended', () => {
        isPlaying = false;
        playButton.textContent = '▶️ PLAY';
        trackDisplay.innerHTML = `✅ FINISHED: ${currentTrack.title.toUpperCase()}`;
    });
    
    // Set volume
    function setVolume() {
        const volume = document.getElementById('volumeSlider').value / 100;
        audio.volume = volume;
    }
    
    // Auto-select random track on load
    window.onload = () => {
        selectRandomTrack();
        setVolume(); // Set initial volume
    };
</script>

## Latest Blog Entries

{% for post in site.posts limit:5 %}
<div class="post">
    <div class="post-title"><a href="{{ post.url | relative_url }}">{{ post.title }}</a></div>
    <div class="post-date">Posted: {{ post.date | date: "%B %d, %Y" }}</div>
    {% if post.tags and post.tags.size > 0 %}
    <div class="post-tags">
        <b>Tags:</b> 
        {% for tag in post.tags %}
        <a href="{{ '/tag/' | append: tag | append: '/' | relative_url }}" class="tag">{{ tag }}</a>{% unless forloop.last %}, {% endunless %}
        {% endfor %}
    </div>
    {% endif %}
    {{ post.excerpt }}
    {% if post.mood %}<p><b>Current mood:</b> {{ post.mood }}</p>{% endif %}
</div>
{% endfor %}

{% if site.posts.size == 0 %}
<div class="post">
    <div class="post-title">Welcome to My Blog!</div>
    <div class="post-date">Posted: {{ site.time | date: "%B %d, %Y" }}</div>
    <p>Welcome to my totally awesome homepage! I just learned HTML and I'm super excited to share my thoughts with the entire Internet. This is like having my own TV channel but better!</p>
    <p>I spent all weekend learning how to make this page. My friend Dave showed me how to use Netscape Composer and it's pretty rad. Can't wait to add more cool stuff like animated GIFs and maybe even a Java applet!</p>
    <p><b>Current mood:</b> 😎 Excited about the Information Superhighway!</p>
</div>
{% endif %}