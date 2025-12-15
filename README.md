local Serviços = {
    Jogadores = jogo¡::GetService((S)"Jogadores"(S)‚,
    Espaço de trabalho = jogo¡::GetService((S)"Espaço de trabalho"(S)‚,
    Serviço de entrada do usuário = jogo¡::GetService((S)"UserInputService"(S)‚,
    RunService = jogo¡::GetService((S)"RunService"(S)‚,
    TweenService = jogo¡::GetService((S)"TweenService"(S)‚,
    CoreGui = jogo¡::GetService((S)"Core Gui"(S)‚,
    Serviço HTTP = jogo¡::GetService((S)"HttpService"(S)
O}

local Jogador = Serviços.O.Jogadores.O.Jogador local
local Personagem = Jogador.O.Personagem ou ou Jogador.O.PersonagemAdicionado¡::Aguardem((S)(S)
local Parte Raiz = Personagem¡::Espere pela criança((S)"Parte Raiz Humanóide"(S)
local Câmera = Serviços.O.Espaço de trabalho.O.Câmera atual
local Rato = Jogador¡::GetMouse((S)(S)

- TABELA DE CONFIGURAÇÃO E ESTADO
local Configurações de script = {
    Aimbot = {
        Habilitado = falso‚,
        Chave = Enum.O.Tipo de entrada do usuário.O.Botão Mouse2‚,
        EquipeVerificar = falso‚,
        VisibleCheck = verdade verdadeira
    O}‚,
    ESP = {
        Habilitado = falso‚,
        MostrarJogadores = verdade verdadeira‚,
        MostrarFrutas = verdade verdadeira‚,
        MostrarBaús = verdade verdadeira‚,
        Conexões = {O}
    O}‚,
    Teleporte = {
        Habilitado = falso‚,
        Alvo = nulo‚,
        TweenSpeed = 150 -- Velocidade do teleporte (quanto maior, mais rápido)
    O}‚,
    Voa = {
        Habilitado = falso‚,
        Velocidade = 50‚,
        Velocidade = nulo‚,
        Giro = nulo
    O}‚,
    Noclip = {
        Habilitado = falso‚,
        Conexão = nulo
    O}
O}

-- FUNÇÕES PRINCIPAIS (OTIMIZADAS)

-- Função para criar a GUI (Responsiva para Celular)
local function (função) criarGUI((S)(S)
    local ScreenGui = Instância.O.novo novo((S)"Screen Gui"(S)
    ScreenGui.O.Nome Nome = "Hub Otimizado"
    ScreenGui.O.Parente = Serviços.O.CoreGui
    ScreenGui.O.ZIndexComportamento = Enum.O.ZIndexComportamento.O.Irmão
    ScreenGui.O.IgnorarGuiInset = verdade verdadeira -- Ignorar uma barra superior do Roblox para melhor uso em celular

    local Quadro principal = Instância.O.novo novo((S)"Moldura"(S)
    Quadro principal.O.Nome Nome = "Matriz"
    Quadro principal.O.Parente = ScreenGui
    Quadro principal.O.FundoCor3 = Cor3.O.doRGB((S)25‚, 25‚, 25(S)
    Quadro principal.O.BorderSizePixel = 0
    Quadro principal.O.Posição = UDim2.O.novo novo((S)0,5‚, ¿ ¿ -150‚, 0,5‚, ¿ ¿ -100(S)
    Quadro principal.O.Tamanho (Size) = UDim2.O.novo novo((S)0‚, 300‚, 0‚, 200(S) -- Menor para ser mais discreto
    Quadro principal.O.Arrastável = verdade verdadeira

    local Titulo = Instância.O.novo novo((S)"RótuloTexto"(S)
    Titulo.O.Nome Nome = "Título"
    Titulo.O.Parente = Quadro principal
    Titulo.O.FundoCor3 = Cor3.O.doRGB((S)255‚, 85‚, 0(S)
    Titulo.O.BorderSizePixel = 0
    Titulo.O.Tamanho (Size) = UDim2.O.novo novo((S)1 1‚, 0‚, 0‚, 25(S)
    Titulo.O.Fonte = Enum.O.Fonte.O.FonteSansBold
    Titulo.O.Texto = "Blox Fruits Hub v3.0"
    Titulo.O.TextoCor3 = Cor3.O.novo novo((S)1 1‚, 1 1‚, 1 1(S)

    -- Layout de Botões em Grid para facilitar toque no celular
    local BotãoLayout = Instância.O.novo novo((S)"Layout UIList"(S)
    BotãoLayout.O.Parente = Quadro principal
    BotãoLayout.O.Remando = UDim.O.novo novo((S)0‚, 5(S)
    BotãoLayout.O.Order de classificação = Enum.O.Order de classificação.O.Ordem de layout

    local function (função) criarToggle((S)texto‚, layoutOrdem‚, retorno telefônico(S)
        local Botão = Instância.O.novo novo((S)"ButãoTexto"(S)
        Botão.O.Nome Nome = texto
        Botão.O.Parente = Quadro principal
        Botão.O.FundoCor3 = Cor3.O.doRGB((S)60‚, 60‚, 60(S)
        Botão.O.BorderSizePixel = 0
        Botão.O.Tamanho (Size) = UDim2.O.novo novo((S)1 1‚, ¿ ¿ -10‚, 0‚, 30(S)
        Botão.O.Posição = UDim2.O.novo novo((S)0‚, 5‚, 0‚, 30 + + ((S)layoutOrdem * * 35(S)(S)
        Botão.O.Fonte = Enum.O.Fonte.O.FonteSans
        Botão.O.Texto = texto .. ": DESLIGADO"
        Botão.O.TextoCor3 = Cor3.O.novo novo((S)1 1‚, 1 1‚, 1 1(S)
        Botão.O.Ordem de layout = layoutOrdem

        Botão.O.Botão Mouse1Click¡::Conectar((S)function (função)((S)(S)
            local novo Estado = não não retorno telefônico.O.estadual
            retorno telefônico.O.estadual = novo Estado
            Botão.O.Texto = texto .. ": " .. ((S)novo Estado e, e "LIGADO" ou ou "DESLIGADA"(S)
            Botão.O.FundoCor3 = novo Estado e, e Cor3.O.doRGB((S)0‚, 150‚, 0(S) ou ou Cor3.O.doRGB((S)60‚, 60‚, 60(S)
            retorno telefônico.O.func((S)novo Estado(S)
        fim fim(S)
    fim fim

    -- Criando os botões com suas respeitos funções
    criarToggle((S)O "Aimbot"‚, 1 1‚, { estadual = Configurações de script.O.Aimbot.O.Habilitado‚, func = alternarAimbot O}(S)
    criarToggle((S)O "ESP"‚, 2 (2)‚, { estadual = Configurações de script.O.ESP.O.Habilitado‚, func = alternarESP O}(S)
    criarToggle((S)O "Noclip"‚, 3 (s)‚, { estadual = Configurações de script.O.Noclip.O.Habilitado‚, func = alternarnódulo O}(S)
    criarToggle((S)O "Voar"‚, 4 4‚, { estadual = Configurações de script.O.Voa.O.Habilitado‚, func = alternarvoar O}(S)

    -- Botão de Teleporte (não é um alternar)
    local Botão Tp = Instância.O.novo novo((S)"ButãoTexto"(S)
    Botão Tp.O.Nome Nome = "Button Teleporto"
    Botão Tp.O.Parente = Quadro principal
    Botão Tp.O.FundoCor3 = Cor3.O.doRGB((S)85‚, 0‚, 255(S)
    Botão Tp.O.BorderSizePixel = 0
    Botão Tp.O.Tamanho (Size) = UDim2.O.novo novo((S)1 1‚, ¿ ¿ -10‚, 0‚, 30(S)
    Botão Tp.O.Posição = UDim2.O.novo novo((S)0‚, 5‚, 0‚, 30 + + ((S)4 4 * * 35(S)(S)
    Botão Tp.O.Fonte = Enum.O.Fonte.O.FonteSans
    Botão Tp.O.Texto = "TP para Baú Próximo"
    Botão Tp.O.TextoCor3 = Cor3.O.novo novo((S)1 1‚, 1 1‚, 1 1(S)
    Botão Tp.O.Ordem de layout = 5
    Botão Tp.O.Botão Mouse1Click¡::Conectar((S)teletransportePara o Peito Mais Próximo(S)
fim fim

-- Função Aimbot (Otimizada)
function (função) alternarAimbot((S)estadual(S)
    Configurações de script.O.Aimbot.O.Habilitado = estadual
    - A lógica do aimbot será executada no loop principal para melhorar a performance
fim fim

-- Função ESP (Otimizada com pooling de objetos)
function (função) alternarESP((S)estadual(S)
    Configurações de script.O.ESP.O.Habilitado = estadual
    -- Limpa ESPs antigos
    para por _‚, cone em (em) pares((S)Configurações de script.O.ESP.O.Conexões(S) fazer do
        se se cone então então cone¡::Desconectar((S)(S) fim fim
    fim fim
    para por _‚, obj em (em) pares((S)Serviços.O.CoreGui¡::GetChildren((S)(S)(S) fazer do
        se se obj.O.Nome Nome¡::encontrar((S)"ESP_"(S) então então
            obj¡::Destruir((S)(S)
        fim fim
    fim fim
    Configurações de script.O.ESP.O.Conexões = {O}

    se se estadual então então
        -- ESP para Jogadores
        para por _‚, p. p em (em) pares((S)Serviços.O.Jogadores¡::GetPlayers((S)(S)(S) fazer do
            se se p. p ~= Jogador e, e p. p.O.Personagem e, e p. p.O.Personagem¡::FindFirstChild((S)"Parte Raiz Humanóide"(S) então então
                local espGui = Instância.O.novo novo((S)"Billboard Gui"(S)
                espGui.O.Nome Nome = "ESP_Player_" .. p. p.O.Nome Nome
                espGui.O.Adornee = p. p.O.Personagem.O.HumanóideRootPart
                espGui.O.Tamanho (Size) = UDim2.O.novo novo((S)0‚, 100‚, 0‚, 50(S)
                espGui.O.Sempre no topo = verdade verdadeira
                espGui.O.Parente = Serviços.O.CoreGui

                local quadro = Instância.O.novo novo((S)"Moldura"‚, espGui(S)
                quadro.O.Tamanho (Size) = UDim2.O.novo novo((S)1 1‚, 0‚, 1 1‚, 0(S)
                quadro.O.FundoCor3 = Cor3.O.novo novo((S)1 1‚, 0‚, 0(S)
                quadro.O.AntecedentesTransparência = 0,5

                local rotulo = Instância.O.novo novo((S)"RótuloTexto"‚, quadro(S)
                rotulo.O.Tamanho (Size) = UDim2.O.novo novo((S)1 1‚, 0‚, 1 1‚, 0(S)
                rotulo.O.AntecedentesTransparência = 1 1
                rotulo.O.Texto = p. p.O.Nome Nome
                rotulo.O.TextoCor3 = Cor3.O.novo novo((S)1 1‚, 1 1‚, 1 1(S)
                rotulo.O.TextoScaled = verdade verdadeira
                rotulo.O.Fonte = Enum.O.Fonte.O.FonteSansBold
                
                local
