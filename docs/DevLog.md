# 📔 DevLog — Cake Run

Registro de cada sessão de desenvolvimento. Preencher ao final de cada sessão,
mesmo que curta. Isso vira histórico de aprendizado e prova de progresso pro
portfólio.

---

## Como preencher cada entrada

```
## [AAAA-MM-DD] Bloco X - <nome do bloco>

**Tempo investido:** Xh

**O que fiz:**
-

**O que aprendi (conceitos novos):**
-

**Dificuldades / bugs encontrados:**
-

**Próximo passo:**
-
```

---

## [Exemplo] 2026-07-10 — Bloco 1 - Configuração do Projeto

**Tempo investido:** 1h30

**O que fiz:**
- Criei o projeto Unity com template URP
- Organizei as pastas em `_Project/Scripts`, `_Project/Prefabs`, etc.
- Configurei o Input System novo
- Inicializei o Git com `.gitignore` da Unity

**O que aprendi (conceitos novos):**
- Diferença entre URP e Built-in Render Pipeline
- Por que `Library/` e `Temp/` nunca devem ir pro Git

**Dificuldades / bugs encontrados:**
- Nenhuma, setup tranquilo

**Próximo passo:**
- Começar Bloco 2 (Movimentação)

---

*(suas entradas reais começam abaixo)*

---

## [2026-07-10] Bloco 2 - Movimentação (correção de método)

**O que aconteceu:**
Recebi um `PlayerController.cs` pronto pra baixar e colar no projeto. Parei e
percebi que isso quebrava a regra de "aprender fazendo" que definimos lá no
início — ia virar só copiar/colar sem entender.

**Decisão:**
Adicionei a "REGRA DE OURO" no topo do GDD.md: nenhum código deve ser copiado
pronto. Toda implementação daqui pra frente é explicada pedaço por pedaço, eu
digito, e só depois escrevo o `.md` de explicação com minhas próprias palavras.

**Próximo passo:**
Recomeçar o `PlayerController.cs` do zero, parte por parte, digitando eu mesmo.

---

## [2026-07-10] Bloco 2 - Movimentação (ponto de parada)

**Tempo investido:** ~1h (setup do Player + início do script)

**O que fiz:**
- Criei o GameObject `Player` (usei Cube em vez de Capsule, tudo bem como
  placeholder)
- Adicionei Rigidbody com `Freeze Rotation X` e `Freeze Rotation Z` marcados
  (pra não tombar de lado com forças/colisões)
- Criei o arquivo `PlayerController.cs` em `Assets/_Project/Scripts`
- Comecei a entender por que a classe herda de `MonoBehaviour` (dá acesso a
  Start/Update, permite virar Component, dá acesso a transform/gameObject)

**O que aprendi (conceitos novos):**
- Para que serve `MonoBehaviour` e por que o script precisa herdar dele
- Por que travar rotação X/Z no Rigidbody evita o personagem tombar

**Dificuldades / bugs encontrados:**
- Nenhum bug, só cansaço mesmo — parei antes de digitar a primeira variável
  de verdade pra não estudar mal.

**Próximo passo (CONTINUA DAQUI):**
1. Retomar no `PlayerController.cs`, ainda vazio de lógica
2. Escrever a linha `private Rigidbody rb;` e entender pra que serve (fazer
   o palpite antes de receber a explicação)
3. Seguir pro `Awake()` com `GetComponent<Rigidbody>()`
4. Depois: `OnMove`, `OnJump`, `OnSprint`, `Update`/`FixedUpdate` — sempre
   pedaço por pedaço, digitando na mão (ver REGRA DE OURO no topo do GDD.md)