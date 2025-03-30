＃单词匹配游戏回声
<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <title>单词配对游戏</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background: #87CEEB;
            display: flex;
            flex-direction: column;
            align-items: center;
        }
        .container {
            display: flex;
            justify-content: space-around;
            width: 90%;
            margin: 20px;
        }
        .column {
            display: flex;
            flex-direction: column;
            gap: 15px;
        }
        .item {
            width: 120px;
            height: 120px;
            border-radius: 50%;
            display: flex;
            justify-content: center;
            align-items: center;
            cursor: pointer;
            transition: transform 0.3s;
            padding: 10px;
            text-align: center;
            border: 3px solid #000;
        }
        .lotus {
            background: #7CFC00;
            box-shadow: 0 0 10px rgba(0,100,0,0.5);
        }
        .frog {
            background: #00FF00;
            box-shadow: 0 0 10px rgba(0,200,0,0.5);
            position: relative;
        }
        .score-board {
            font-size: 24px;
            margin: 20px;
        }
        button {
            padding: 10px 20px;
            font-size: 18px;
            cursor: pointer;
            background: #4CAF50;
            border: none;
            color: white;
            border-radius: 5px;
        }
        .matched {
            opacity: 0.5;
            pointer-events: none;
        }
    </style>
</head>
<body>
    <div class="score-board">得分：<span id="score">0</span></div>
    <div class="container">
        <div class="column" id="lotusColumn"></div>
        <div class="column" id="frogColumn"></div>
    </div>
    <button onclick="resetGame()">重新开始</button>

    <script>
        const wordPairs = [
            { en: "decorous", zh: "列队" },
            { en: "mauve", zh: "淡紫色" },
            { en: "tambourine", zh: "鼓" },
            { en: "magnanimous", zh: "高尚的" },
            { en: "imperious", zh: "傲慢的" },
            { en: "genitals", zh: "生殖器" },
            { en: "uncouth", zh: "粗鲁的" },
            { en: "poignancy", zh: "抽泣" }
        ];

        let selectedLotus = null;
        let selectedFrog = null;
        let score = 0;

        function createGame() {
            // 创建独立随机顺序的英文和中文选项
            const shuffledEnglish = shuffleArray([...wordPairs]);
            const shuffledChinese = shuffleArray([...wordPairs]);

            // 创建英文列
            shuffledEnglish.forEach(pair => {
                const lotus = createItem('lotus', pair.en, pair.en);
                document.getElementById('lotusColumn').appendChild(lotus);
            });

            // 创建中文列（独立随机顺序）
            shuffledChinese.forEach(pair => {
                const frog = createItem('frog', pair.en, pair.zh);
                document.getElementById('frogColumn').appendChild(frog);
            });
        }

        function createItem(className, dataValue, text) {
            const item = document.createElement('div');
            item.className = `item ${className}`;
            item.dataset.en = dataValue;
            item.textContent = text;
            item.onclick = className === 'lotus' ? handleLotusClick : handleFrogClick;
            return item;
        }

        功能shufflearray（array）{
            返回array.sort.sort（sort）=> MATH.RANDOM（） -  0.5）;
        }

        函数（handletusclick）（e）{
            如果SelectionLotus）selectionLotus.style.transform ='';
            selectedlotus = e.target;
            e.target.Style.transform ='比例（1.1）';
            检查（检查）（（）；
        }

        功能（Hander HanderFogClick）（E）{
            如果选择frog）选择frog.style.transform ='';
            选定的青蛙= e.target;
            e.target.Style.transform ='比例（1.1）';
            检查（检查）（（）；
        }

        功能检查（检查））{
            如果选择lotus ||！selectionFrog）返回;

            const lotusrect = selectLotus.getBoundingClientRect（）;
            const frogrect = selectedfrog.getBoundingClientRect（）;

            if（selectedlotus.dataset.en === selectedfrog.dataset.en）{
                得分 += 10;
                selected frog.style.transform =`翻译（
                    $ {lutusrect.left -frogrect.left} px，
                    $ {lotusrect.top -frogrect.top} px
                ）
                selectedfrog.classlist.add（'匹配'）;
            } 别的 {
                得分= math.max（0，得分-5）;
                settimeout（（）=> {
                    selected frog.style.transform ='';
                }，500）;
            }

            document.getElementById（'score'）。textContent =得分;
            selectedlotus.style.transform ='';
            selectedlotus = null;
            selected frog = null;
        }

        函数resetGame（）{
            document.getElementById（'lotuscolumn'）。innerhtml ='';
            document.getElementById（'Frogcolumn'）。innerhtml ='';
            得分= 0;
            document.getElementById（'score'）。textContent =得分;
            CreateGame（）；
        }

        //初始化游戏
        CreateGame（）；
    </script>
</ body >
