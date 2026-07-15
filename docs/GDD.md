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

> ⚠️ **REGRA DE OURO — NUNCA COPIAR E COLAR CÓDIGO PRONTO**
> O objetivo aqui é aprender fazendo, não só ter o jogo funcionando. Sempre que
> for escrever um script:
> - Peça pra explicar o código **pedaço por pedaço** (uma variável, um método
>   por vez), nunca o arquivo inteiro de uma vez.
> - **Digite você mesmo** cada linha — não copie de um bloco de código pronto.
> - Antes de aceitar uma explicação como certa, tente responder "o que essa
>   linha faz?" com suas próprias palavras primeiro.
> - O `.md` de explicação de cada bloco (o "porquê" da solução) deve ser
>   escrito com as suas palavras, não copiado da explicação recebida.
> Se em algum momento a conversa cair direto pra "aqui está o arquivo pronto
> pra baixar", pare e peça pra recomeçar no formato de explicação por partes.

---

# STATUS DO PROJETO

- [x] Bloco 0 - Planejamento
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

> ⚠️ Nota de coerência (2026-07-15): o jogador **já começa com o bolo** (ver
> decisão em `Ideias.md`/DevLog), então "pegar objeto" não se aplica mais.
> O bloco foi redirecionado para **detecção de zona de entrega**: o Trigger
> Collider passa a ficar no ponto de entrega/NPC, não mais ao redor do
> Player. Os conceitos (`OnTriggerEnter`, `IInteragivel`) continuam os
> mesmos, só a aplicação muda.

### Objetivo
Permitir que o jogo detecte quando o jogador chega a um ponto de entrega
(carregando o bolo) e dispare a lógica de interação correspondente.

### Checklist
- [ ] Trigger Collider no ponto de entrega (não mais no Player)
- [ ] Detectar chegada do jogador (`OnTriggerEnter`)
- [ ] Interface `IInteragivel` (ou `IPontoDeEntrega`) para padronizar pontos de entrega
- [ ] Feedback básico ao chegar (placeholder: Debug.Log ou cor mudando)

### O que vou aprender
- `OnTriggerEnter` / `OnTriggerExit` (colisores como "sensores")
- Interfaces em C# (ex: `IInteragivel`) para padronizar objetos interagíveis
- Tags/comparação de objetos (`CompareTag`) para identificar o Player que
  entrou no trigger

### Critério de conclusão
O jogador, carregando o bolo, entra na zona de entrega e o jogo detecta
essa chegada corretamente.

### ✅ O que eu devo saber agora?
- Por que um Trigger Collider serve como "sensor" sem bloquear o movimento?
- Para que serve uma interface como `IInteragivel` no lugar de checar tags?
- Por que usar `CompareTag` em vez de comparar strings diretamente?

---

# BLOCO 5 — Bolo

> ⚠️ Nota de coerência (2026-07-15): já que o bolo **nasce com o jogador**
> (ver nota do Bloco 4), o objetivo muda de "objeto solto no cenário à
> espera de ser pego" para "objeto já anexado (parented) ao Player desde
> o início da fase". O sistema de interação do Bloco 4 passa a cuidar só
> da **entrega**, não da coleta.

### Objetivo
Criar o objeto central do jogo: o bolo que o jogador carrega desde o
início e entrega no ponto de destino.

### Checklist
- [ ] Modelo 3D (placeholder ou asset simples)
- [ ] Material (aparência visual)
- [ ] Collider
- [ ] Rigidbody
- [ ] Bolo posicionado como filho do Player (parenting) ao iniciar a fase
- [ ] Prefab do bolo (pra reaproveitar entre fases)

### O que vou aprender
- Diferença entre `Mesh`, `Material` e `Shader`
- Colliders convexos vs não-convexos (limitações de física)
- Prefabs (por que o bolo deve virar um Prefab reutilizável)
- Parenting no Editor vs via código (`transform.SetParent`) e como isso
  afeta Rigidbody/física de um objeto filho

### Critério de conclusão
O bolo existe como Prefab, aparece anexado ao Player desde o início da
fase, e reage à física (mesmo que ainda de forma simples — o balanço
"de verdade" fica pro Bloco 6).

### ✅ O que eu devo saber agora?
- O que é um Prefab e por que ele evita duplicar trabalho?
- Qual a diferença entre Material e Shader?
- Por que um Rigidbody sem massa ajustada pode se comportar de forma estranha?
- O que muda na física de um objeto quando ele é filho (child) de outro
  objeto com Rigidbody?

---

# BLOCO 6 — Física

> 💡 Nota de design (2026-07-15, atualizada): testamos `SpringJoint` primeiro,
> mas a calibração (Spring/Damper/Mass/Sleep Threshold) se mostrou instável
> e imprevisível — o bolo ficava "pesado" em velocidades baixas. Decisão:
> o bolo segue o Player via **script** (`Vector3.Lerp` + Rigidbody
> `Kinematic`, mesmo padrão do `CameraFollow` do Bloco 3), o que dá controle
> direto e previsível sobre o "atraso" de movimento. O Rigidbody/Collider do
> bolo continuam existindo para detecção de colisão com obstáculos, mas a
> posição é controlada por código, não por física bruta.
> Obstáculos cômicos que desestabilizam o bolo (brainstorm inicial, mover
> pra `Ideias.md`/Bloco 10 quando for desenhar fases): pombo sobrevoando e
> "sujando" o caminho, pessoa regando plantas na calçada, etc. — cada um
> aplicando um pequeno impulso/força ao bolo ou ao Player no momento da
> colisão/trigger.

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

> ⚠️ PIVOT DE DESIGN (2026-07-15): o game loop mudou de "cidade aberta +
> pedidos/entregas" para **progressão vertical com checkpoints**, inspirado
> diretamente em Carry The Glass. Ver detalhes logo abaixo. Isso reduz o
> escopo (não precisa de cidade aberta, sistema de pedidos com prazo, nem
> vários NPCs de rota) e foca o jogo no que já está funcionando: o bolo
> instável seguindo o Player e reagindo a obstáculos.

- Nome provisório: Cake Run
- Objetivo do jogo: O jogador tem a finalidade de conseguir fazer a entrega do bolo
  porque ele é um chefe que recebe pedidos constantemente por ser um bom chefe
  culinário. (o que o jogador faz e por quê)
- Gameplay (loop principal, ATUALIZADO): O jogador (chefe) sobe verticalmente
  por uma estrutura/prédio carregando um bolo instável, desviando de
  obstáculos cômicos no caminho (pombo sujando o caminho, pessoa regando
  plantas, etc.) que desequilibram o bolo. Existem **checkpoints** em pontos
  específicos da subida. Duas condições de "reset":
  - **Bolo caiu** (qualidade chegou a 0 / estado `Caido`): volta pro último checkpoint.
  - **Personagem caiu de uma altura** (saiu da estrutura, caiu lá embaixo):
    volta pro último checkpoint (ou pro início, se ainda não passou de nenhum) —
    **não é uma morte**, é só um "ops, começa dali de novo", mantendo o tom
    cômico/leve do jogo.
  **Vibe escolhida: Caótico/cômico — física exagerada, tombos engraçados.**
- Público-alvo: livre
- Plataforma: Inicialmente PC (futuramente há uma expectativa caso dê um bom
  retorno de mudar para o mobile porque tenho licença da play store)
- Mecânicas principais (ATUALIZADO):
  - Carregar o bolo sozinho (solo, MVP) equilibrando com física exagerada
  - Correr, pular e **subir** por uma estrutura vertical
  - Colisões cômicas que desestabilizam o bolo (tombos, escorregões)
  - Sistema de **checkpoints**: bolo caiu ou personagem caiu → volta pro
    último checkpoint (substitui o antigo sistema de pedidos/prazo)
  - **Futuro (pós-MVP): co-op local — dois jogadores carregando o mesmo bolo
    juntos, inspirado em "Carry the Glass". Ver `Ideias.md` para o roadmap
    dessa fase.**
- Obstáculos:
  - Pisos escorregadios / rampas
  - Obstáculos cômicos ao longo da subida (pombo, regador, etc.) que
    desestabilizam o bolo
  - Quedas (do personagem, ou do bolo perdendo qualidade)
- Fluxo do jogo:
  - **Menu principal:** Iniciar Partida / Opções / Sair
  - **Iniciar Partida:** jogo estruturado em **fases verticais**. Cada fase
    é uma subida com checkpoints e obstáculos crescentes em dificuldade.
  - **Opções:** tela com abas/switch — Controles, Áudio (Música on/off +
    volume, SFX on/off + volume), Resolução/Gráficos.
  - **Sair:** encerra o jogo e fecha a aplicação.

  > ⚠️ Nota de coerência: isso muda o Bloco 8 (Pedidos) de "sistema de
  > pedido/cliente/prazo" para "sistema de checkpoints" e o Bloco 9 (NPCs)
  > deixa de ser central para o MVP (pode virar decoração/pós-MVP). O
  > Bloco 10 (Cidade) já tinha sido ajustado antes para "fases menores" em
  > vez de cidade aberta — agora fica ainda mais específico: fases
  > **verticais**, não horizontais.