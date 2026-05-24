# 📱 TelePronto — Protótipo de Baixa Fidelidade

> Atividade Prática — Interação Humano-Computador & UX  
> Centro Universitário UNA · Professor Daniel Henrique Matos de Paiva

---

## 👥 Aluno

| Nome | 
|------|
Lucas Nascimento

---

## 🗂️ Estrutura do Repositório

```
ihcux-tele-pronto/
├── README.md
└── /prototipo
    ├── prototipo.png
    └── prototipo.pdf
```

---

## 🖥️ Telas do Protótipo

O protótipo contempla **6 telas principais**, cobrindo o fluxo completo do usuário dentro do TelePronto:

| # | Tela | Descrição |
|---|------|-----------|
| 1 | **Home / Dashboard** | Atalhos para "Consulta Agora", "Meus Remédios", histórico e farmácias próximas |
| 2 | **Fluxo de Triagem** | Chatbot / formulário de sintomas com corpo humano interativo |
| 3 | **Sala de Espera Virtual** | Posição na fila, tempo estimado e botão de cancelamento com confirmação |
| 4 | **Vídeo-Chamada** | Interface de consulta com controles de mudo, câmera e chat |
| 5 | **Minha Receita** | Prescrição digital com QR Code para farmácias conveniadas |
| 6 | **Configuração de Alarme** | Agendamento de lembretes de medicação |

---

## ♿ Análise de Acessibilidade

O design do TelePronto foi pensado desde o início para um público que pode estar com a visão turva, dedos trêmulos ou alto nível de estresse — condições comuns em pessoas que não estão se sentindo bem.

### Visão comprometida
- **Tipografia generosa**: fonte mínima de 18px no corpo do texto e 24px em títulos, sem fontes decorativas que dificultam a leitura.
- **Contraste elevado**: paleta de alto contraste (texto escuro sobre fundo claro ou vice-versa), respeitando a proporção mínima de 4,5:1 recomendada pelas WCAG 2.1.
- **Ícones com rótulo**: nenhum ícone aparece sozinho — todos possuem legenda textual abaixo, eliminando ambiguidade.
- **Modo escuro nativo**: disponível para reduzir o cansaço visual em ambientes de pouca luz.

### Dedos trêmulos / mobilidade reduzida
- **Botões grandes**: área de toque mínima de 56×56 dp, muito acima do mínimo de 44px recomendado pelo Material Design e Apple HIG.
- **Espaçamento generoso entre elementos interativos**: evita toques acidentais em botões adjacentes.
- **Ações destrutivas protegidas**: qualquer ação irreversível (encerrar consulta, cancelar fila) exige confirmação em duas etapas.
- **Rolar é mais seguro que tocar**: listas longas são preferidas a menus suspensos, pois o gesto de rolagem é mais tolerante a imprecisão.

### Usuário em estado de estresse
- **Linguagem simples e direta**: sem jargões médicos nas instruções da interface.
- **Fluxo linear**: cada tela apresenta **uma única ação principal** destacada visualmente, evitando sobrecarga cognitiva.
- **Feedback visual constante**: indicadores de progresso (barras e etapas numeradas) informam ao usuário onde ele está no fluxo.
- **Botão de Emergência sempre visível**: fixo no canto superior direito de todas as telas, com ícone de cruz vermelha e rótulo "Emergência — Ligue 192".

---

## 🚨 Fluxo Crítico — Iniciar uma Consulta de Urgência

Abaixo está o caminho mínimo para um usuário iniciar uma consulta de urgência, do zero até falar com um médico:

```
1. HOME
   └─ Toca em "Consulta Agora" (botão principal, centro da tela)

2. TRIAGEM
   └─ Seleciona região do corpo afetada (mapa corporal)
   └─ Escolhe até 3 sintomas na lista rápida
   └─ Confirma: "Estou com dor aguda / mal-estar intenso"
   └─ Toca em "Iniciar Atendimento"

3. SALA DE ESPERA VIRTUAL
   └─ Sistema exibe posição na fila e tempo estimado
   └─ Notificação automática quando for a vez do paciente

4. VÍDEO-CHAMADA
   └─ Tela de espera: câmera ligada, aguardando médico entrar
   └─ Médico entra → consulta iniciada
   └─ Ao término, receita é gerada automaticamente

5. RECEITA DIGITAL
   └─ QR Code disponível imediatamente para farmácias conveniadas
```

**Tempo estimado do fluxo completo (triagem + espera + consulta):** ~20 minutos para casos leves.

---

## 🛡️ Prevenção de Erros

### Encerramento acidental da consulta
O principal risco identificado foi o usuário tocar sem querer no botão de encerrar durante a vídeo-chamada. As seguintes estratégias foram adotadas:

- **Botão "Encerrar" posicionado longe dos controles frequentes** (mudo e câmera): fica no canto inferior direito, enquanto mudo e câmera ficam centralizados.
- **Confirmação obrigatória em duas etapas**: ao tocar em "Encerrar", um modal pergunta *"Tem certeza que deseja sair da consulta? O médico ainda está na linha."*, com os botões "Voltar à consulta" (destaque verde) e "Sim, encerrar" (texto vermelho discreto).
- **Zona de segurança (dead zone)**: área de 20px ao redor do botão "Encerrar" não registra toque, prevenindo acionamento por deslize acidental.

### Outros erros prevenidos

| Situação de risco | Solução implementada |
|---|---|
| Usuário submete triagem sem preencher sintomas | Botão "Avançar" desabilitado até selecionar ao menos 1 sintoma |
| Câmera/microfone negados pelo SO | Tela de aviso antes da chamada com passo a passo para liberar permissões |
| Queda de conexão durante a espera | Banner persistente de reconexão automática; posição na fila é preservada |
| Lembrete de remédio no horário errado | Tela de confirmação com resumo legível ("Amanhã às 08h — Dipirona 500mg") antes de salvar |


---

## 🔗 Links

- **Board no Miro:** *(inserir link público do board)*
- **Repositório GitHub:** [github.com/seu-usuario/ihcux-tele-pronto](https://github.com/seu-usuario/ihcux-tele-pronto)

---

> *"Design para saúde é design de responsabilidade. Um ícone mal interpretado aqui pode gerar um erro médico ou um atraso no atendimento. Foquem na clareza absoluta!"*  
> — Professor Daniel Henrique Matos de Paiva
