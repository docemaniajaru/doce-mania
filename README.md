# Doce Mania — primeira versão (PWA)

## O que já funciona
- Catálogo responsivo para celular e computador.
- Busca de produtos.
- Carrinho com quantidades, subtotal e taxa de entrega ajustável.
- Formulário de cliente, endereço, pagamento, troco e observações.
- Montagem de mensagem e abertura do WhatsApp para o cliente confirmar o envio.
- Manifest e service worker básicos para instalação como aplicativo web.

## Importante antes de publicar
Esta é uma versão inicial funcional do catálogo, não um sistema completo de gestão. Os preços são exemplos iniciais e precisam ser conferidos. O produto sem preço configurado não pode ser adicionado. A taxa de entrega começa em R$ 0,00 e precisa ser ajustada conforme o pedido/bairro.

### 1. Configure o WhatsApp
Abra `index.html` em um editor de texto e procure:
`const WHATSAPP_NUMBER = "";`
Troque o conteúdo vazio pelo número comercial em formato internacional, só números, com 55 + DDD + número. Exemplo fictício: `5569999999999`.

### 2. Confira produtos e preços
No mesmo arquivo, procure `const products = [` e ajuste nomes, descrições e preços conforme o cardápio real da Doce Mania. Os valores de R$ 23, R$ 29 e R$ 20 são exemplos baseados nas informações discutidas; valide-os antes de usar comercialmente.

### 3. Teste localmente
- Extraia o ZIP.
- Abra `index.html` no navegador para testar catálogo e carrinho.
- Para testar o service worker/PWA, hospede os arquivos em HTTPS ou use um servidor local. O service worker não funciona de forma completa abrindo `file://`.

### 4. Publique gratuitamente como site
Uma opção é GitHub Pages:
1. Crie uma conta em https://github.com/
2. Crie um repositório público, por exemplo `doce-mania`.
3. Envie `index.html`, `manifest.json` e `sw.js` para a raiz.
4. Em Settings → Pages, escolha a branch principal e a pasta raiz.
5. Aguarde a publicação e abra o endereço HTTPS informado pelo GitHub.

Alternativa: https://pages.cloudflare.com/ ou https://vercel.com/

### 5. Instalação no Android
Depois de publicado em HTTPS, abra o site no Chrome do Android e use o menu ⋮ → “Adicionar à tela inicial” ou “Instalar app” quando aparecer.

## Limitações conhecidas desta versão
- O pedido é encaminhado ao WhatsApp, mas o cliente precisa tocar em Enviar.
- Não há painel administrativo, banco de dados, estoque sincronizado, cálculo automático por bairro, rastreamento ou integração de pagamento online.
- O pagamento por cartão é combinado na entrega; não é processado pelo aplicativo.
- O catálogo utiliza emojis ilustrativos, não fotos reais dos produtos.
- Não foram incluídos o logotipo original nem as cores exatas porque os arquivos de marca não foram anexados nesta etapa. A paleta inicial vinho/rosa/dourado pode ser ajustada ao logo real.

## Fontes oficiais
- GitHub Pages: https://docs.github.com/pages
- Progressive Web Apps: https://web.dev/learn/pwa/
- WhatsApp Click to Chat: https://faq.whatsapp.com/5913398998672934


## Taxas de entrega por bairro
O seletor de bairro calcula automaticamente as taxas fornecidas pela Doce Mania: R$ 8, R$ 9, R$ 10, R$ 12 ou R$ 16 conforme a tabela recebida. O WhatsApp comercial está configurado para 556992484868. Revise os produtos e preços demonstrativos antes de publicar. A imagem logo.png usa a logo enviada.


## Painel administrativo (versão inicial)

Abra `admin.html` para editar produtos e taxas por bairro, salvar as alterações no navegador e exportar/importar a configuração JSON. A versão atual usa `localStorage`, portanto as alterações ficam apenas no navegador/aparelho em que foram salvas. Isso não atualiza automaticamente a loja publicada para todos os clientes. Para sincronização real entre dispositivos, é necessário conectar um backend/banco de dados e proteger o painel com autenticação.

As taxas incluídas seguem a tabela fornecida:
- Setores 01, 02 e 03 — R$ 8,00
- Setores 04, 05, 06 e 07 — R$ 8,00
- Luzia Abranches / 1A — R$ 8,00
- Jardim dos Estados — R$ 9,00
- Jardim Novo Estado — R$ 9,00
- Parque Universitário — R$ 9,00
- Setor Industrial — R$ 8,00
- Savana Park — R$ 9,00
- Orleans — R$ 9,00
- Jardim Morumbi — R$ 9,00
- Setor 08 — R$ 10,00
- Jardim Primavera — R$ 12,00
- Jardim Europa / 627 — R$ 16,00
- Frigon ou Depósito 628 — R$ 16,00
