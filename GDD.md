# 🎂 Cake Run
Versão: 0.1
Engine: Unity (URP)
Autor: Marcos Levi Borges de Souza

---

## SOBRE ESTE DOCUMENTO

Esta é a Bíblia do Jogo (Game Design Document). Cada bloco abaixo é uma missão fechada:
tem um objetivo, um checklist de tarefas, uma seção "O que vou aprender" e um checkpoint
de conhecimento no final. **Não avance de bloco se não conseguir responder o checkpoint.**

Formato de trabalho:
1. Ler o objetivo do bloco.
2. Executar o checklist, marcando `[x]` conforme avança.
3. Ao terminar, responder mentalmente (ou por escrito no DevLog.md) o checkpoint.
4. Só então seguir para o próximo bloco.

---

# STATUS DO PROJETO

- [ ] Bloco 0 - Planejamento
- [ ] Bloco 1 - Configuração do Projeto
- [ ] Bloco 2 - Movimentação
- [ ] Bloco 3 - Câmera
- [ ] Bloco 4 - Interação
- [ ] Bloco 5 - Bolo
- [ ] Bloco 6 - Física
- [ ] Bloco 7 - HUD
- [ ] Bloco 8 - Pedidos
- [ ] Bloco 9 - NPCs
- [ ] Bloco 10 - Cidade
- [ ] Bloco 11 - Sons
- [ ] Bloco 12 - Polimento
- [ ] Bloco 13 - Demo Steam

---

# BLOCO 0 — Planejamento

### Objetivo
Definir todo o jogo antes de escrever qualquer linha de código.

### Checklist
- [ ] Nome provisório
- [ ] Objetivo do jogo (o que o jogador faz e por quê)
- [ ] Gameplay (loop principal em 2-3 frases)
- [ ] Público-alvo
- [ ] Plataforma (PC via Steam, mobile, ambos?)
- [ ] Mecânicas principais (lista curta, 3 a 5)
- [ ] Obstáculos/desafios do jogador
- [ ] Fluxo do jogo (menu → gameplay → fim de partida/dia)

### O que vou aprender
- Game Design Document (o que é e por que toda produtora usa)
- Diferença entre "ideia de jogo" e "escopo de jogo" (o que é viável sozinho)
- Conceito de Game Loop (núcleo repetido de jogabilidade)
- Definição de MVP (Minimum Viable Product) aplicada a jogos

### Critério de conclusão
Documento com todas as respostas acima escritas neste próprio arquivo, na seção
"Decisões do Bloco 0" (adicionar abaixo quando preenchido).

### ✅ O que eu devo saber agora?
- O que é um GDD e para que serve?
- Qual é o game loop do Cake Run em uma frase?
- Por que definir escopo antes de programar evita retrabalho?

---

# BLOCO 1 — Configuração do Projeto

### Objetivo
Configurar o projeto Unity do zero, do jeito certo, para não precisar reestruturar depois.

### Checklist
- [ ] Criar projeto novo em Unity com template URP (Universal Render Pipeline)
- [ ] Organizar pastas (`_Project/Scripts`, `_Project/Prefabs`, `_Project/Scenes`,
      `_Project/Materials`, `_Project/Art`, `_Project/Audio`)
- [ ] Criar cena `Main`
- [ ] Criar cena `Test` (para testar mecânicas isoladas sem sujar a cena principal)
- [ ] Configurar o novo Input System (pacote `com.unity.inputsystem`)
- [ ] Configurar Git + `.gitignore` específico para Unity
- [ ] Primeiro commit ("Initial commit - project setup")

### O que vou aprender
- URP vs Built-in Render Pipeline (por que URP é o padrão atual)
- Convenção de organização de pastas em projetos Unity profissionais
- Scenes: o que são e como o Unity carrega/troca entre elas
- Input System novo vs antigo (`Input.GetKey` vs `InputAction`)
- `.gitignore` para Unity (por que `Library/`, `Temp/`, `Obj/` nunca vão pro Git)

### Critério de conclusão
Projeto abre sem erros, pastas organizadas, repositório Git inicializado com o
primeiro commit feito.

### ✅ O que eu devo saber agora?
- Por que não versionar a pasta `Library/` no Git?
- Qual a diferença entre o Input System novo e o `Input.GetAxis` antigo?
- Para que serve ter uma cena `Test` separada da cena `Main`?

---

# BLOCO 2 — Movimentação

### Objetivo
Ter um personagem que anda, corre e pula, sem bugs.

### Checklist
- [ ] Criar Capsule (placeholder do personagem)
- [ ] Adicionar Rigidbody
- [ ] Adicionar Collider
- [ ] Criar script `PlayerController.cs`
- [ ] Implementar movimento (frente/trás/lados)
- [ ] Implementar corrida (Shift ou botão)
- [ ] Implementar pulo

### O que vou aprender
- `GameObject` e `Component` (a base de tudo no Unity)
- `Transform` (posição, rotação, escala)
- `Rigidbody` e `Collider` (física básica)
- `Vector3` (representação de posição/direção em 3D)
- `Time.deltaTime` (por que todo movimento depende dele)
- Novo Input System (`InputAction`, `PlayerInput`)
- `MonoBehaviour` (classe base de todo script de comportamento)
- `Update()` vs `FixedUpdate()` (quando usar cada um)
- Organização de scripts (namespaces, pastas por responsabilidade)

### Critério de conclusão
O personagem anda, corre e pula de forma fluida, sem travar em quinas nem
atravessar o chão.

### ✅ O que eu devo saber agora?
- O que é um GameObject?
- O que é um Component?
- O que faz um Rigidbody?
- Quando usar `Update()` e quando usar `FixedUpdate()`?
- O que é um `Vector3`?
- Como mover um objeto no código (qual API usar)?
- Por que multiplicar velocidade por `Time.deltaTime`?

---

# BLOCO 3 — Câmera

### Objetivo
Câmera que segue o jogador de forma suave e agradável.

### Checklist
- [ ] Câmera seguindo o jogador
- [ ] Rotação da câmera (orbital ou fixa, decidir no Bloco 0)
- [ ] Zoom (opcional, scroll do mouse)
- [ ] Suavização de movimento (sem "trancos")

### O que vou aprender
- `Vector3.Lerp` / `SmoothDamp` (interpolação suave entre posições)
- Cinemachine (pacote oficial da Unity para câmeras, se optar por usá-lo)
- Diferença entre câmera em "espaço do mundo" vs "espaço local"
- Conceito de "camera rig" (objeto pai que carrega a câmera)

### Critério de conclusão
Câmera acompanha o jogador sem tremer, sem atravessar paredes e sem
atraso perceptível incômodo.

### ✅ O que eu devo saber agora?
- O que faz `Vector3.Lerp` e por que ele evita movimento "robótico"?
- O que é Cinemachine e por que ela simplifica câmeras no Unity?
- Por que colocar a câmera dentro de um objeto "rig" pai facilita ajustes?

---

# BLOCO 4 — Interação

### Objetivo
Permitir que o jogador detecte e interaja com objetos do cenário.

### Checklist
- [ ] Detectar objetos próximos (Raycast ou Trigger Collider)
- [ ] Botão de interação (tecla E / botão do gamepad)
- [ ] Pegar objeto (anexar ao jogador)
- [ ] Soltar objeto

### O que vou aprender
- `Physics.Raycast` (detecção de objetos por raio invisível)
- `OnTriggerEnter` / `OnTriggerExit` (colisores como "sensores")
- Interfaces em C# (ex: `IInteragivel`) para padronizar objetos interagíveis
- Parenting dinâmico de objetos (`transform.SetParent`)

### Critério de conclusão
O jogador consegue se aproximar de um objeto, pressionar o botão de
interação, pegar o objeto e soltá-lo em outro lugar.

### ✅ O que eu devo saber agora?
- Diferença entre `Raycast` e `Trigger Collider` para detectar objetos?
- Para que serve uma interface como `IInteragivel` no lugar de checar tags?
- O que acontece com a física de um objeto quando ele vira filho do jogador?

---

# BLOCO 5 — Bolo

### Objetivo
Criar o objeto central do jogo: o bolo que o jogador carrega e entrega.

### Checklist
- [ ] Modelo 3D (placeholder ou asset simples)
- [ ] Material (aparência visual)
- [ ] Collider
- [ ] Rigidbody

### O que vou aprender
- Diferença entre `Mesh`, `Material` e `Shader`
- Colliders convexos vs não-convexos (limitações de física)
- Prefabs (por que o bolo deve virar um Prefab reutilizável)

### Critério de conclusão
O bolo existe como Prefab, pode ser pego pelo sistema de interação do
Bloco 4 e reage à física.

### ✅ O que eu devo saber agora?
- O que é um Prefab e por que ele evita duplicar trabalho?
- Qual a diferença entre Material e Shader?
- Por que um Rigidbody sem massa ajustada pode se comportar de forma estranha?

---

# BLOCO 6 — Física

### Objetivo
Sistema de física que dá "vida" ao bolo: ele balança, pode cair e quebrar
qualidade se for maltratado.

### Checklist
- [ ] Balançar (o bolo reage ao movimento do jogador)
- [ ] Cair (se o jogador tropeçar ou colidir forte)
- [ ] Colidir (com cenário, NPCs, obstáculos)
- [ ] Perder qualidade (sistema de "dano" ao bolo)

### O que vou aprender
- `PhysicsMaterial` (atrito e elasticidade)
- Detecção de colisão com força (`OnCollisionEnter` + `collision.relativeVelocity`)
- Máquina de estados simples (bolo: intacto → balançando → caído → destruído)
- Eventos em C# (`Action`, `UnityEvent`) para avisar outros sistemas quando o
  bolo muda de estado

### Critério de conclusão
O bolo reage de forma crível ao movimento e a colisões, e o jogo sabe
identificar quando a "qualidade" do bolo caiu.

### ✅ O que eu devo saber agora?
- O que é `PhysicsMaterial` e o que ele controla?
- Como pegar a força de um impacto via `OnCollisionEnter`?
- O que é uma máquina de estados e por que ela organiza melhor esse
  comportamento do que vários `if` soltos?

---

# BLOCO 7 — HUD

### Objetivo
Interface na tela mostrando informações relevantes ao jogador.

### Checklist
- [ ] Canvas configurado (Screen Space - Overlay ou Camera)
- [ ] Indicador de qualidade do bolo
- [ ] Timer/contador de entregas
- [ ] Feedback visual de interação disponível

### O que vou aprender
- Unity UI (`Canvas`, `RectTransform`, `Image`, `Text`/`TextMeshPro`)
- Diferença entre Screen Space e World Space UI
- Data binding simples (atualizar UI quando uma variável do jogo muda)
- Padrão Observer aplicado a UI (UI "escuta" eventos em vez de checar toda hora)

### Critério de conclusão
HUD atualiza em tempo real conforme o estado do bolo e do jogo mudam.

### ✅ O que eu devo saber agora?
- O que é um `RectTransform` e como ele difere de um `Transform` normal?
- Por que TextMeshPro é preferido ao `Text` legado?
- O que é o padrão Observer e como ele evita "checar toda hora no Update"?

---

# BLOCO 8 — Pedidos

### Objetivo
Sistema de pedidos: o jogador recebe um destino/cliente e precisa entregar
o bolo lá.

### Checklist
- [ ] Estrutura de dados de um "Pedido" (cliente, local, prazo, recompensa)
- [ ] Geração de pedidos (aleatória ou sequencial)
- [ ] Validação de entrega (chegou no lugar certo, com o bolo em bom estado?)
- [ ] Recompensa/pontuação

### O que vou aprender
- `ScriptableObject` (estrutura de dados reutilizável e configurável no Editor)
- Listas e filas em C# (`List<T>`, `Queue<T>`) para gerenciar pedidos
- Serialização de dados no Unity (`[SerializeField]`)
- Lógica de validação de condições múltiplas (local certo + prazo + qualidade)

### Critério de conclusão
O jogador recebe um pedido, entrega o bolo, e o jogo valida corretamente
sucesso ou falha.

### ✅ O que eu devo saber agora?
- O que é um `ScriptableObject` e quando usar em vez de uma classe comum?
- Diferença entre `List<T>` e `Queue<T>` — qual serve melhor para uma fila
  de pedidos?
- Por que `[SerializeField]` aparece no Inspector mesmo em campos privados?

---

# BLOCO 9 — NPCs

### Objetivo
Personagens não-jogáveis que dão vida à cidade (clientes, pedestres).

### Checklist
- [ ] NPC parado com diálogo simples
- [ ] NPC com rota de patrulha (NavMesh ou waypoints)
- [ ] Reação do NPC à entrega (feliz, bravo, neutro)

### O que vou aprender
- NavMesh e NavMeshAgent (pathfinding automático da Unity)
- Waypoints manuais como alternativa mais simples ao NavMesh
- Máquinas de estado para comportamento de NPC (parado, andando, reagindo)
- Animator básico (transições de animação por estado)

### Critério de conclusão
Pelo menos um NPC anda por uma rota e reage de forma diferente conforme
o resultado da entrega.

### ✅ O que eu devo saber agora?
- O que é NavMesh e o que ele resolve automaticamente pra você?
- Quando faz mais sentido usar waypoints manuais em vez de NavMesh?
- Como o Animator do Unity decide qual animação tocar?

---

# BLOCO 10 — Cidade

### Objetivo
Construir o cenário onde o jogo acontece.

### Checklist
- [ ] Layout básico das ruas/quarteirões
- [ ] Prédios/props (placeholders ou assets)
- [ ] Pontos de entrega definidos no mapa
- [ ] Iluminação básica (URP lighting)

### O que vou aprender
- Level design básico (fluxo de jogador, pontos de referência visual)
- Lightmapping / Global Illumination no URP
- Occlusion Culling (otimização de renderização)
- Organização de cena grande (uso de pastas/parents para não bagunçar a Hierarchy)

### Critério de conclusão
Cidade jogável, com pontos de entrega claros e performance estável.

### ✅ O que eu devo saber agora?
- O que é Occlusion Culling e por que ele importa em cidades grandes?
- Diferença entre luz em tempo real (realtime) e luz "assada" (baked)?
- Por que organizar a Hierarchy em pastas/parents ajuda a manter o projeto saudável?

---

# BLOCO 11 — Sons

### Objetivo
Áudio: música ambiente, efeitos sonoros, feedback sonoro de ações.

### Checklist
- [ ] Música de fundo
- [ ] SFX de passos, pulo, interação
- [ ] SFX de entrega (sucesso/falha)
- [ ] Mixagem básica (volumes balanceados)

### O que vou aprender
- `AudioSource` e `AudioClip`
- `AudioMixer` (grupos de volume: música, SFX, UI)
- Pooling de áudio (evitar recriar `AudioSource` toda hora)
- 3D Sound (spatial blend) vs som 2D

### Critério de conclusão
Jogo tem trilha sonora e efeitos sonoros para as principais ações,
sem sons cortando ou sobrepondo de forma incômoda.

### ✅ O que eu devo saber agora?
- Qual a diferença entre `AudioSource` e `AudioClip`?
- Para que serve um `AudioMixer` com grupos separados?
- O que é "spatial blend" e quando um som deve ser 3D?

---

# BLOCO 12 — Polimento

### Objetivo
Refinar tudo: bugs, performance, sensação de jogo ("game feel").

### Checklist
- [ ] Corrigir bugs conhecidos (ver `Bugs.md`)
- [ ] Ajustar profiler (performance, sem quedas de FPS)
- [ ] Adicionar "juice" (partículas, screen shake leve, feedback tátil)
- [ ] Revisar balanceamento (dificuldade, prazos de entrega)

### O que vou aprender
- Unity Profiler (CPU, GPU, memória)
- Object Pooling (reaproveitar objetos em vez de instanciar/destruir toda hora)
- Conceito de "game feel" / "juiciness" (por que pequenos detalhes importam)
- Boas práticas de otimização (draw calls, batching)

### Critério de conclusão
Jogo roda estável, sem bugs críticos, e "parece bom de jogar" (não só funciona).

### ✅ O que eu devo saber agora?
- Como usar o Profiler para identificar um gargalo de performance?
- O que é Object Pooling e por que ele evita picos de Garbage Collection?
- O que significa "game feel" na prática — dê um exemplo do seu próprio jogo.

---

# BLOCO 13 — Demo Steam

### Objetivo
Empacotar uma demo jogável para publicar (Steam ou itch.io como teste).

### Checklist
- [ ] Build final (Windows, testado do zero)
- [ ] Tela de menu inicial
- [ ] Créditos
- [ ] Página da loja (descrição, screenshots, capa)
- [ ] Checklist de submissão (Steamworks ou itch.io)

### O que vou aprender
- Processo de Build no Unity (configurações de Player Settings)
- Steamworks SDK — visão geral (ou itch.io como alternativa mais simples)
- Como escrever uma descrição de loja que vende o jogo
- Checklist de QA antes de lançar (o que testar antes de publicar)

### Critério de conclusão
Build funcionando em uma máquina limpa, com página de loja pronta.

### ✅ O que eu devo saber agora?
- Quais os principais passos entre "jogo terminado no Editor" e "build jogável"?
- O que costuma dar errado em um build que não aparecia no Editor?
- O que uma página de loja precisa ter, no mínimo, para atrair um clique?

---

# DECISÕES DO BLOCO 0
*(preencher aqui conforme for definindo o jogo)*

- Nome provisório:
- Objetivo do jogo:
- Gameplay (loop principal):
- Público-alvo:
- Plataforma:
- Mecânicas principais:
- Obstáculos:
- Fluxo do jogo:
