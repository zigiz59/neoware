Общее
Используя скрипты, вы можете сделать почти что угодно, все ограничивается лишь вашей фантазией.

Структура кода
Весь код пишется на JS (Rhino). Начало кода должно состоять из getName() и getAuthor(). Там содержится базовая информация о скрипте


function getName() {
    return "Example";
}

function getAuthor() {
    return "KrytickYT";
}
В коде так-же может частично поддерживаться Java код, но с указанием полных Package. Не рекомендуется использовать из-за возможных багов.

О скриптах
При выполнении скрипта, он идет 1 для всех активных ботов. Есть множество ивентов для работы с ними.

Файл с вашим кодом должен выглядеть как filename.js Расширение обязательно!

Таймеры
Чтоб не городить ужас с таймерами как в BetterCaptcha-bypass, можно использовать 3 встроенных таймера.

pBot.stimer1

pBot.stimer2

pBot.stimer3

Они ничем не заняты, поэтому их можно использовать как угодно.


//Пример использования таймеров бота
function getName() {
    return "Example";
}

function getAuthor() {
    return "KrytickYT";
}

function onUpdate(pBot) {
    //Выполняется, при обновлении бота (20 тиков в сек.)
    //Переменные от пакета:
    //
    //pBot (PBot)
  
    if(pBot.stimer1.hasReached(1000)) {     //Проверяем, прошла ли 1 секунда (1сек = 1000мс)
        pBot.stimer1.reset();     //Сбрасываем таймер когда прошло время

        //Тут будет ваш код
    }
    //Таймер для каждого бота идет свой, и они не будут мешать друг другу.
}
ScriptAPI
ScriptAPI - встроенный набор инструментов для написания скриптов.


function tutorial() {
    ScriptAPI.sendMessage("Hello World");     //Отправит в чат сообщение, можно использовать для дебага
    var placeholder = ScriptAPI.parsePlaceholders("%n");     //Использование тех-же плейсхолдеров, что и в командах ботов
    var randomPlayer = ScriptAPI.getRandomTabPlayer();     //Получает ник рандомного игрока из таба
    var clean = ScriptAPI.stripColor("§c§lExample Text");     //Чистит строку от цветовых знаков
    var translateKey = ScriptAPI.translateItemKey("tile.thinStainedGlass.lime");     //Вернет реальное название предмета по ItemStack.item.getTranslationKey();
  
}

Боты
JavaScript

pBot - Возращается любым ивентом. Это сам бот.

String  | pBot.getNickname() - Никнейм бота.
Void    | pBot.jump() - Заставляет подпрыгнуть бота.
Void    | pBot.stopBot() - Отключить и остановить бота.
Boolean | pBot.hasMap() - Вернет true если у бота имеется карта в инвенторе.
Integer | pBot.currentWindowID() - Вернет ID текущего меню.
Void    | pBot.isOnline() - Вернет true, если бот онлайн.
Void    | pBot.dropItem(slot) - Выкинет предмет из инвентаря.
Void    | pBot.sendMessage(msg) - Отправить сообщение от бота.
Void    | pBot.sendPacket(packet) - Отправит пакет на сервер.
Void    | pBot.useItem() - Нажмет пкм по текущему предмету в хотбаре.
Void    | pBot.windowClick(slot, mouseButton) - Нажмет на предмет в текущем инвентаре.
String  | pBot.windowTitle - Вернет название текущего меню.
Void    | pBot.changeSlot(slot) - Сменить активный слот в хотбаре.
Void    | pBot.swapHands() - Положить предмет из правой руки в левую.
Void    | pBot.reconnect() - Переподключить бота к серверу.

------------------------------------------------------------

PBotWorld     | pBot.getWorld() - Мир, в котором находится бот.
List<.Entity> | pBot.getWorld().loadedEntityList - Список всех сущностей в мире.
IBlockState   | pBot.getWorld().getBlockState(blockPos) - Получить блок по координатам.
IBlockState   | pBot.getWorld().getBlockState(blockPos) - Получить блок по координатам.

------------------------------------------------------------

PBotEntity       | pBot.player - Бот в виде PlayerEntity, координаты, инвентарь и т.д.
Container        | pBot.player.openContainer - Инвентарь бота.
List<.ItemStack> | pBot.player.openContainer.getInventory() - Список предметов в инвентаре.
Integer          | pBot.player.openContainer.windowId - Вернет ID текущего меню.
Double           | pBot.player.posX - Координата X бота.
Double           | pBot.player.posY - Координата Y бота.
Double           | pBot.player.posZ - Координата Z бота.
Float            | pBot.player.rotationYaw - Yaw позиция камеры бота.
Float            | pBot.player.rotationPitch - Pitch позиция камеры бота.
Boolean          | pBot.player.onGround - Касание бота с землей.
Boolean          | pBot.mc.gameSettings.keyBindForward.pressed - Управление движением вперед.
Boolean          | pBot.mc.gameSettings.keyBindBack.pressed - Управление движением назад.
Boolean          | pBot.mc.gameSettings.keyBindLeft.pressed - Управление движением влево.
Boolean          | pBot.mc.gameSettings.keyBindRight.pressed - Управление движением вправо.
Boolean          | pBot.mc.gameSettings.keyBindJump.pressed - Управление прыжком.
Boolean          | pBot.mc.gameSettings.keyBindSneak.pressed - Управление приседанием.
Boolean          | pBot.mc.gameSettings.keyBindSprint.pressed - Управление спиртом/бегом.
Некоторые из выше перечисленных переменных можно изменять, например:
pBot.mc.gameSettings.keyBindJump.pressed = true;
pBot.player.rotationYaw = 180;

Boolean          | pBot.player.isInWater() - Вернет true, если бот находится в воде.
Boolean          | pBot.player.isCreative() - Вернет true, если бот находится в Creative.
Boolean          | pBot.player.isSneaking() - Вернет true, если бот находится на шифте.
Boolean          | pBot.player.isInLava() - Вернет true, если бот находится в лаве.
Boolean          | pBot.player.isBurning() - Вернет true, если бот горит.
Boolean          | pBot.player.isSprinting() - Вернет true, если бот бежит.
Boolean          | pBot.player.isOnLadder() - Вернет true, если находится на лестнице.
Float            | pBot.player.getHealth() - Вернет кол-во здоровья у бота.
Integer          | pBot.player.experienceLevel - Вернет уровень опыта у бота.

Ивенты
Для полноценной работы существуют ивенты ботов

Пример использования

function SPacketJoinGame(pBot, packetIn) {
    //Выполняется, когда бот заходит на сервер
    //Переменные от пакета:
    //
    //pBot (PBot)
    //packetIn.playerId (Integer)
    //packetIn.hardcoreMode (Boolean)
    //packetIn.gameType (GameType)
    //packetIn.dimension (Integer)
    //packetIn.difficulty (EnumDifficulty)
    //packetIn.maxPlayers (Integer)
    //packetIn.worldType (WorldType)
}

function SPacketChat(pBot, packetIn) {
    //Выполняется, когда приходит сообщение в чате у бота
    //Переменные от пакета:
    //
    //pBot (PBot)
    //packetIn.chatComponent (ITextComponent)
    //packetIn.type (ChatType)
    //packetIn.getChatComponent().getFormattedText() (String)
}

function SPacketDisconnect(pBot, packetIn) {
    //Выполняется, когда бот отключается
    //Переменные от пакета:
    //
    //pBot (PBot)
    //packetIn.reason (ITextComponent)
    //packetIn.getReason().getFormattedText() (String)
}

function SPacketTitle(pBot, packetIn) {
    //Выполняется, когда приходит Title сообщение
    //Переменные от пакета:
    //
    //pBot (PBot)
    //packetIn.type (Type)
    //packetIn.message (ITextComponent)
    //packetIn.fadeInTime (Integer)
    //packetIn.displayTime (Integer)
    //packetIn.fadeOutTime (Integer)
}

function SPacketResourcePackSend(pBot, packetIn) {
    //Выполняется, когда приходит запрос на скачку ресурспака
    //Переменные от пакета:
    //
    //pBot (PBot)
    //packetIn.url (String)
    //packetIn.hash (String)
}

function SPacketMaps(pBot, imageInBase64, mapID) {
    //Выполняется, когда приходит 1 фрейм карты
    //Переменные от пакета:
    //
    //pBot (PBot)
    //imageInBase64 (String) Картинка, в формате Base64 (PNG)
    //mapID (Integer) MapID карты
}

function onPuzzleCaptcha(pBot, imageInBase64) {
    //Выполняется, когда приходит капча
    //Переменные от пакета:
    //
    //pBot (PBot)
    //imageInBase64 (String) Картинка, в формате Base64 (PNG)
}

function onUpdate(pBot) {
    //Выполняется, при обновлении бота (20 тиков в сек.)
    //Переменные от пакета:
    //
    //pBot (PBot)
}

Примеры кода
AutoRegister

function getName() {
    return "Example";
}

function getAuthor() {
    return "KrytickYT";
}

function SPacketChat(pBot, packetIn) {
    if(packetIn.getChatComponent().getFormattedText().contains("/reg")) {
        pBot.sendMessage('/reg 123123 123123');
    }
}
BetterCaptcha-Bypass

var TimerUtil = function() {
    this.lastMS = new Date().getTime();
};

TimerUtil.prototype.hasReached = function(delay) {
    return (new Date().getTime() - this.lastMS) >= delay;
};

TimerUtil.prototype.hasReached = function(active, delay) {
    return active || this.hasReached(delay);
};

TimerUtil.prototype.getLastMS = function() {
    return this.lastMS;
};

TimerUtil.prototype.reset = function() {
    this.lastMS = new Date().getTime();
};

TimerUtil.prototype.getTimePassed = function() {
    return new Date().getTime() - this.lastMS;
};

TimerUtil.prototype.getCurrentTime = function() {
    return new Date().getTime();
};

TimerUtil.prototype.setTime = function(time) {
    this.lastMS = time;
};

var timer = new TimerUtil();

function onUpdate(pBot) {
    if(pBot.windowTitle != null) {
        if (timer.hasReached(800)) {
            for(var slot = 0; slot < pBot.player.openContainer.getInventory().size(); slot++) {
            	if (ScriptAPI.stripColor(pBot.windowTitle.toLowerCase()).contains(ScriptAPI.stripColor(pBot.player.openContainer.getInventory().get(slot).getDisplayName()).toLowerCase())) {
            		pBot.windowClick(slot, 0);
            	}
            }
            timer.reset();
        }
    }
}
Вводит команду через 1 секунду после авторизации
В обнове будет нормальный ивент авторизации


function getName() {
    return "Example";
}

function getAuthor() {
    return "KrytickYT";
}

var list = new java.util.HashMap();

function onUpdate(pBot) {
  if(pBot.isRegistered()) {
        if(list.get(pBot.getNickname()) == false) {
            java.lang.Thread.sleep(1000); //Оч опасное решение, лучше так не делать
            list.put(pBot.getNickname(), true);
            pBot.sendMessage("/shhhhhh");
        }
  }
}
function SPacketJoinGame(pBot, packetIn) {
    list.put(pBot.getNickname(), false);
}
Авторешение примера из чата
Подходят примеры по типу таких: 2+6, 10-5, 3*4, 12/3


function getName() {
    return "Example";
}

function getAuthor() {
    return "KrytickYT";
}

function SPacketChat(pBot, packetIn) {
    var message = ScriptAPI.stripColor(packetIn.getChatComponent().getFormattedText());
    var cleanedString = message.replace(/[^0-9\+\-\*\/]/g, '');
    if(cleanedString.length >= 3) {
        var result = eval(cleanedString);
        pBot.sendMessage(result);
    }
}

Discord server https://discord.com/invite/2rxyndXyUB
Дискорд сервер https://discord.com/invite/2rxyndXyUB
Дс https://discord.com/invite/2rxyndXyUB
Дс серв https://discord.com/invite/2rxyndXyUB
Дс сервер https://discord.com/invite/2rxyndXyUB
ds server https://discord.com/invite/2rxyndXyUB
ds serv
ds https://discord.com/invite/2rxyndXyUB

ЭТО JAVASCRIPT 
И он для игры в майнкрафт
Это клиент neoware
