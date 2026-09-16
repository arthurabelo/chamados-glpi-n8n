# ChamadosGLPI

Automação em n8n para monitoramento, consolidação e disparo de alertas de chamados do GLPI (com foco em atrasos/SLA) via WhatsApp, com suporte a notificações em grupo e envio direto para os técnicos responsáveis.

## 🚀 O que esse workflow faz?
* **Consulta automatizada:** Busca as saved searches (buscas salvas) do GLPI em horários programados.
* **Trava inteligente:** Verifica se o dia atual é feriado ou ponto facultativo antes de rodar.
* **Consolidação de dados:** Trata os dados do CSV exportado e filtra chamados em atraso por nível/grupo.
* **Notificações em grupo:** Envia resumos consolidados formatados para os grupos do WhatsApp.
* **Cobrança individual:** Dispara mensagens privadas automáticas direto para os técnicos que possuem chamados atrasados.

---

## ⚙️ Pré-requisitos e Ambiente

Para rodar este workflow sem dor de cabeça, você vai precisar de:

1. Uma instância do [n8n](https://n8n.io/) rodando e acessível (seja self-hosted ou cloud).
2. Uma API de WhatsApp configurada (como a [Evolution API](https://doc.evolution-api.com/) usada nos nós de HTTP Request).
3. Acesso a uma conta no GLPI com permissões para executar buscas salvas e exportações.

---

## 🛠️ Como Configurar o Projeto

1. **Baixe o arquivo** `ChamadosGLPI.json` deste repositório.
2. No seu painel do n8n, crie um novo workflow e **importe** o JSON.
3. Configure o nó **`Variaveis`** logo no início do fluxo com os seus dados de acesso:
    * `glpiBaseUrl`: URL base do seu GLPI (ex: `https://glpi.suaempresa.com`)
    * `glpiUser`: Seu usuário de serviço ou pessoal
    * `glpiPass`: Sua senha de acesso
4. Atualize os **IDs das Buscas Salvas (savedsearches_id)** no nó de mapeamento/backup de acordo com os IDs configurados no seu GLPI.
5. Ajuste os números de WhatsApp dos grupos e o mapeamento de contatos dos técnicos no nó **`Edit Fields - Contatos e menções`** para corresponder à sua base real.
6. Verifique os nós de requisição HTTP da Evolution API para garantir que a **URL do servidor**, a **porta** e a **API Key** apontam para o seu ambiente.

---