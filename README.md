<!DOCTYPE html>
<html lang="ar">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>سورة الفاتحة - تلاوة محمد صديق المنشاوي</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        body {
            font-family: 'Arial', sans-serif;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            background: linear-gradient(to right, #4a90e2, #6cb2f3);
            color: #ffffff;
        }
        .player-container {
            background: rgba(0, 0, 0, 0.7);
            padding: 30px;
            width: 400px;
            border-radius: 20px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.5);
            text-align: center;
            transition: transform 0.2s;
        }
        .player-container h1 {
            font-size: 1.5em;
            margin-bottom: 20px;
            color: #fff;
            text-shadow: 1px 1px 2px rgba(0, 0, 0, 0.5);
        }
        .progress-container {
            display: flex;
            align-items: center;
            margin-top: 20px;
            color: #f1f1f1;
        }
        .time {
            font-size: 0.9em;
            width: 50px;
        }
        .progress-bar {
            flex-grow: 1;
            height: 12px;
            background-color: rgba(255, 255, 255, 0.2);
            border-radius: 6px;
            margin: 0 10px;
            position: relative;
            cursor: pointer;
        }
        .progress {
            height: 100%;
            width: 0;
            background: linear-gradient(to right, #ff416c, #ff4b2b);
            border-radius: 6px;
            transition: width 0.1s ease-in-out;
        }
        .controls {
            display: flex;
            justify-content: center;
            gap: 20px;
            margin-top: 30px;
        }
        .control-button {
            background-color: rgba(255, 255, 255, 0.15);
            border: none;
            color: #ffffff;
            padding: 15px;
            font-size: 20px;
            border-radius: 50%;
            cursor: pointer;
            transition: all 0.3s ease;
            width: 60px;
            height: 60px;
            position: relative;
            overflow: hidden;
        }
        .control-button:hover {
            background-color: rgba(255, 255, 255, 0.3);
            transform: scale(1.05);
        }
        .control-button:disabled {
            background-color: rgba(255, 255, 255, 0.1);
            cursor: not-allowed;
        }
        .playlist {
            margin-top: 20px;
            text-align: left;
            max-height: 200px;
            overflow-y: auto;
            padding: 10px;
            border-radius: 10px;
            background: rgba(255, 255, 255, 0.1);
            color: #ffffff;
        }
        .playlist-item {
            cursor: pointer;
            padding: 5px;
            transition: background 0.3s;
        }
        .playlist-item:hover {
            background: rgba(255, 255, 255, 0.2);
        }
    </style>
</head>
<body>

    <div class="player-container">
        <h1>سورة الفاتحة</h1>
        <audio id="audioPlayer">
            <source id="audioSource" src="https://server10.mp3quran.net/minsh/Almusshaf-Al-Mojawwad/001.mp3" type="audio/mpeg">
            متصفحك لا يدعم تشغيل الصوت.
        </audio>

        <div class="progress-container">
            <span class="time" id="currentTime">0:00</span>
            <div class="progress-bar" id="progressBar">
                <div class="progress" id="progress"></div>
            </div>
            <span class="time" id="duration">0:00</span>
        </div>

        <div class="controls">
            <button class="control-button" onclick="playAudio()" id="playButton" title="تشغيل">▶️</button>
            <button class="control-button" onclick="pauseAudio()" id="pauseButton" title="إيقاف مؤقت" disabled>⏸️</button>
        </div>

        <div class="playlist">
    <h3>قائمة التشغيل</h3>
    <div class="playlist-item" onclick="loadSurah('001', 'سورة الفاتحة')">سورة الفاتحة</div>
    <div class="playlist-item" onclick="loadSurah('002', 'سورة البقرة')">سورة البقرة</div>
    <div class="playlist-item" onclick="loadSurah('003', 'سورة آل عمران')">سورة آل عمران</div>
    <div class="playlist-item" onclick="loadSurah('004', 'سورة النساء')">سورة النساء</div>
    <div class="playlist-item" onclick="loadSurah('005', 'سورة المائدة')">سورة المائدة</div>
    <div class="playlist-item" onclick="loadSurah('006', 'سورة الأنعام')">سورة الأنعام</div>
    <div class="playlist-item" onclick="loadSurah('007', 'سورة الأعراف')">سورة الأعراف</div>
    <div class="playlist-item" onclick="loadSurah('008', 'سورة الأنفال')">سورة الأنفال</div>
    <div class="playlist-item" onclick="loadSurah('009', 'سورة التوبة')">سورة التوبة</div>
    <div class="playlist-item" onclick="loadSurah('010', 'سورة يونس')">سورة يونس</div>
    <div class="playlist-item" onclick="loadSurah('011', 'سورة هود')">سورة هود</div>
    <div class="playlist-item" onclick="loadSurah('012', 'سورة يوسف')">سورة يوسف</div>
    <div class="playlist-item" onclick="loadSurah('013', 'سورة الرعد')">سورة الرعد</div>
    <div class="playlist-item" onclick="loadSurah('014', 'سورة إبراهيم')">سورة إبراهيم</div>
    <div class="playlist-item" onclick="loadSurah('015', 'سورة الحجر')">سورة الحجر</div>
    <div class="playlist-item" onclick="loadSurah('016', 'سورة النحل')">سورة النحل</div>
    <div class="playlist-item" onclick="loadSurah('017', 'سورة الإسراء')">سورة الإسراء</div>
    <div class="playlist-item" onclick="loadSurah('018', 'سورة الكهف')">سورة الكهف</div>
    <div class="playlist-item" onclick="loadSurah('019', 'سورة مريم')">سورة مريم</div>
    <div class="playlist-item" onclick="loadSurah('020', 'سورة طه')">سورة طه</div>
    <div class="playlist-item" onclick="loadSurah('021', 'سورة الأنبياء')">سورة الأنبياء</div>
    <div class="playlist-item" onclick="loadSurah('022', 'سورة الحج')">سورة الحج</div>
    <div class="playlist-item" onclick="loadSurah('023', 'سورة المؤمنون')">سورة المؤمنون</div>
    <div class="playlist-item" onclick="loadSurah('024', 'سورة النور')">سورة النور</div>
    <div class="playlist-item" onclick="loadSurah('025', 'سورة الفرقان')">سورة الفرقان</div>
    <div class="playlist-item" onclick="loadSurah('026', 'سورة الشعراء')">سورة الشعراء</div>
    <div class="playlist-item" onclick="loadSurah('027', 'سورة النمل')">سورة النمل</div>
    <div class="playlist-item" onclick="loadSurah('028', 'سورة القصص')">سورة القصص</div>
    <div class="playlist-item" onclick="loadSurah('029', 'سورة العنكبوت')">سورة العنكبوت</div>
    <div class="playlist-item" onclick="loadSurah('030', 'سورة الروم')">سورة الروم</div>
    <div class="playlist-item" onclick="loadSurah('031', 'سورة لقمان')">سورة لقمان</div>
    <div class="playlist-item" onclick="loadSurah('032', 'سورة السجدة')">سورة السجدة</div>
    <div class="playlist-item" onclick="loadSurah('033', 'سورة الأحزاب')">سورة الأحزاب</div>
    <div class="playlist-item" onclick="loadSurah('034', 'سورة سبأ')">سورة سبأ</div>
    <div class="playlist-item" onclick="loadSurah('035', 'سورة فاطر')">سورة فاطر</div>
    <div class="playlist-item" onclick="loadSurah('036', 'سورة يس')">سورة يس</div>
    <div class="playlist-item" onclick="loadSurah('037', 'سورة الصافات')">سورة الصافات</div>
    <div class="playlist-item" onclick="loadSurah('038', 'سورة ص')">سورة ص</div>
    <div class="playlist-item" onclick="loadSurah('039', 'سورة الزمر')">سورة الزمر</div>
    <div class="playlist-item" onclick="loadSurah('040', 'سورة غافر')">سورة غافر</div>
    <div class="playlist-item" onclick="loadSurah('041', 'سورة فصلت')">سورة فصلت</div>
    <div class="playlist-item" onclick="loadSurah('042', 'سورة الشورى')">سورة الشورى</div>
    <div class="playlist-item" onclick="loadSurah('043', 'سورة الزخرف')">سورة الزخرف</div>
    <div class="playlist-item" onclick="loadSurah('044', 'سورة الدخان')">سورة الدخان</div>
    <div class="playlist-item" onclick="loadSurah('045', 'سورة الجاثية')">سورة الجاثية</div>
    <div class="playlist-item" onclick="loadSurah('046', 'سورة الأحقاف')">سورة الأحقاف</div>
    <div class="playlist-item" onclick="loadSurah('047', 'سورة محمد')">سورة محمد</div>
    <div class="playlist-item" onclick="loadSurah('048', 'سورة الفتح')">سورة الفتح</div>
    <div class="playlist-item" onclick="loadSurah('049', 'سورة الحجرات')">سورة الحجرات</div>
    <div class="playlist-item" onclick="loadSurah('050', 'سورة ق')">سورة ق</div>
    <div class="playlist-item" onclick="loadSurah('051', 'سورة الذاريات')">سورة الذاريات</div>
    <div class="playlist-item" onclick="loadSurah('052', 'سورة الطور')">سورة الطور</div>
    <div class="playlist-item" onclick="loadSurah('053', 'سورة النجم')">سورة النجم</div>
    <div class="playlist-item" onclick="loadSurah('054', 'سورة القمر')">سورة القمر</div>
    <div class="playlist-item" onclick="loadSurah('055', 'سورة الرحمن')">سورة الرحمن</div>
    <div class="playlist-item" onclick="loadSurah('056', 'سورة الواقعة')">سورة الواقعة</div>
    <div class="playlist-item" onclick="loadSurah('057', 'سورة الحديد')">سورة الحديد</div>
    <div class="playlist-item" onclick="loadSurah('058', 'سورة المجادلة')">سورة المجادلة</div>
    <div class="playlist-item" onclick="loadSurah('059', 'سورة الحشر')">سورة الحشر</div>
    <div class="playlist-item" onclick="loadSurah('060', 'سورة الممتحنة')">سورة الممتحنة</div>
    <div class="playlist-item" onclick="loadSurah('061', 'سورة الصف')">سورة الصف</div>
    <div class="playlist-item" onclick="loadSurah('062', 'سورة الجمعة')">سورة الجمعة</div>
    <div class="playlist-item" onclick="loadSurah('063', 'سورة المنافقون')">سورة المنافقون</div>
    <div class="playlist-item" onclick="loadSurah('064', 'سورة التغابن')">سورة التغابن</div>
 <div class="playlist-item" onclick="loadSurah('065', 'سورة الطلاق')">سورة الطلاق</div>
    <div class="playlist-item" onclick="loadSurah('066', 'سورة التحريم')">سورة التحريم</div>
    <div class="playlist-item" onclick="loadSurah('067', 'سورة الملك')">سورة الملك</div>
    <div class="playlist-item" onclick="loadSurah('068', 'سورة القلم')">سورة القلم</div>
    <div class="playlist-item" onclick="loadSurah('069', 'سورة الحاقة')">سورة الحاقة</div>
    <div class="playlist-item" onclick="loadSurah('070', 'سورة المعارج')">سورة المعارج</div>
    <div class="playlist-item" onclick="loadSurah('071', 'سورة نوح')">سورة نوح</div>
    <div class="playlist-item" onclick="loadSurah('072', 'سورة الجن')">سورة الجن</div>
    <div class="playlist-item" onclick="loadSurah('073', 'سورة المزمل')">سورة المزمل</div>
    <div class="playlist-item" onclick="loadSurah('074', 'سورة المدثر')">سورة المدثر</div>
    <div class="playlist-item" onclick="loadSurah('075', 'سورة القيامة')">سورة القيامة</div>
    <div class="playlist-item" onclick="loadSurah('076', 'سورة الإنسان')">سورة الإنسان</div>
    <div class="playlist-item" onclick="loadSurah('077', 'سورة المرسلات')">سورة المرسلات</div>
    <div class="playlist-item" onclick="loadSurah('078', 'سورة النبأ')">سورة النبأ</div>
    <div class="playlist-item" onclick="loadSurah('079', 'سورة النازعات')">سورة النازعات</div>
    <div class="playlist-item" onclick="loadSurah('080', 'سورة عبس')">سورة عبس</div>
    <div class="playlist-item" onclick="loadSurah('081', 'سورة التكوير')">سورة التكوير</div>
    <div class="playlist-item" onclick="loadSurah('082', 'سورة الإنفطار')">سورة الإنفطار</div>
    <div class="playlist-item" onclick="loadSurah('083', 'سورة المطففين')">سورة المطففين</div>
    <div class="playlist-item" onclick="loadSurah('084', 'سورة الإنشقاق')">سورة الإنشقاق</div>
    <div class="playlist-item" onclick="loadSurah('085', 'سورة البروج')">سورة البروج</div>
    <div class="playlist-item" onclick="loadSurah('086', 'سورة الطارق')">سورة الطارق</div>
    <div class="playlist-item" onclick="loadSurah('087', 'سورة الأعلى')">سورة الأعلى</div>
    <div class="playlist-item" onclick="loadSurah('088', 'سورة الغاشية')">سورة الغاشية</div>
    <div class="playlist-item" onclick="loadSurah('089', 'سورة الفجر')">سورة الفجر</div>
    <div class="playlist-item" onclick="loadSurah('090', 'سورة البلد')">سورة البلد</div>
    <div class="playlist-item" onclick="loadSurah('091', 'سورة الشمس')">سورة الشمس</div>
    <div class="playlist-item" onclick="loadSurah('092', 'سورة الليل')">سورة الليل</div>
    <div class="playlist-item" onclick="loadSurah('093', 'سورة الضحى')">سورة الضحى</div>
    <div class="playlist-item" onclick="loadSurah('094', 'سورة الشرح')">سورة الشرح</div>
    <div class="playlist-item" onclick="loadSurah('095', 'سورة التين')">سورة التين</div>
    <div class="playlist-item" onclick="loadSurah('096', 'سورة العلق')">سورة العلق</div>
    <div class="playlist-item" onclick="loadSurah('097', 'سورة القدر')">سورة القدر</div>
    <div class="playlist-item" onclick="loadSurah('098', 'سورة البينة')">سورة البينة</div>
    <div class="playlist-item" onclick="loadSurah('099', 'سورة الزلزلة')">سورة الزلزلة</div>
    <div class="playlist-item" onclick="loadSurah('100', 'سورة العاديات')">سورة العاديات</div>
    <div class="playlist-item" onclick="loadSurah('101', 'سورة القارعة')">سورة القارعة</div>
    <div class="playlist-item" onclick="loadSurah('102', 'سورة التكاثر')">سورة التكاثر</div>
    <div class="playlist-item" onclick="loadSurah('103', 'سورة العصر')">سورة العصر</div>
    <div class="playlist-item" onclick="loadSurah('104', 'سورة الهمزة')">سورة الهمزة</div>
    <div class="playlist-item" onclick="loadSurah('105', 'سورة الفيل')">سورة الفيل</div>
    <div class="playlist-item" onclick="loadSurah('106', 'سورة قريش')">سورة قريش</div>
    <div class="playlist-item" onclick="loadSurah('107', 'سورة الماعون')">سورة الماعون</div>
    <div class="playlist-item" onclick="loadSurah('108', 'سورة الكوثر')">سورة الكوثر</div>
    <div class="playlist-item" onclick="loadSurah('109', 'سورة الكافرون')">سورة الكافرون</div>
    <div class="playlist-item" onclick="loadSurah('110', 'سورة النصر')">سورة النصر</div>
    <div class="playlist-item" onclick="loadSurah('111', 'سورة المسد')">سورة المسد</div>
    <div class="playlist-item" onclick="loadSurah('112', 'سورة الإخلاص')">سورة الإخلاص</div>
    <div class="playlist-item" onclick="loadSurah('113', 'سورة الفلق')">سورة الفلق</div>
    <div class="playlist-item" onclick="loadSurah('114', 'سورة الناس')">سورة الناس</div>
</div>
     </div>
    </div>

    <script>
        const audioPlayer = document.getElementById('audioPlayer');
        const playButton = document.getElementById('playButton');
        const pauseButton = document.getElementById('pauseButton');
        const progressBar = document.getElementById('progress');
        const progressBarContainer = document.getElementById('progressBar');
        const currentTimeDisplay = document.getElementById('currentTime');
        const durationDisplay = document.getElementById('duration');
        const audioSource = document.getElementById('audioSource');

        function playAudio() {
            audioPlayer.play();
            playButton.disabled = true;
            pauseButton.disabled = false;
        }

        function pauseAudio() {
            audioPlayer.pause();
            playButton.disabled = false;
            pauseButton.disabled = true;
        }

        audioPlayer.ontimeupdate = () => {
            const progressPercent = (audioPlayer.currentTime / audioPlayer.duration) * 100;
            progressBar.style.width = progressPercent + '%';
            currentTimeDisplay.textContent = formatTime(audioPlayer.currentTime);
        };

        audioPlayer.onloadedmetadata = () => {
            durationDisplay.textContent = formatTime(audioPlayer.duration);
        };

        audioPlayer.onended = () => {
            playButton.disabled = false;
            pauseButton.disabled = true;
            progressBar.style.width = '0%';
            currentTimeDisplay.textContent = "0:00";
        };

        function formatTime(seconds) {
            const minutes = Math.floor(seconds / 60);
            const remainingSeconds = Math.floor(seconds % 60);
            return `${minutes}:${remainingSeconds < 10 ? '0' : ''}${remainingSeconds}`;
        }

        progressBarContainer.addEventListener('click', (e) => {
            const rect = progressBarContainer.getBoundingClientRect();
            const clickX = e.clientX - rect.left;
            const newTime = (clickX / progressBarContainer.offsetWidth) * audioPlayer.duration;
            audioPlayer.currentTime = newTime;
        });

        function loadSurah(surahNumber, surahName) {
            audioSource.src = `https://server10.mp3quran.net/minsh/Almusshaf-Al-Mojawwad/${surahNumber}.mp3`;
            audioPlayer.load();
            document.querySelector('.player-container h1').textContent = surahName;
            playAudio();
        }
    </script>

</body>
</html>
