# Contexto do projeto — Site Costa, Pereira & Scapin (Advocacia)

> Este arquivo resume o projeto para dar contexto a novas sessões (inclusive no Claude Code).
> O site inteiro está em um único arquivo: `index.html` (HTML + CSS + JS embutidos).

## Visão geral

Landing page institucional de página única para o escritório de advocacia **Costa, Pereira & Scapin**.
É um site estático (sem framework, sem build), publicado na **Vercel** em `sitecpsadv.vercel.app`.
O objetivo principal é converter visitantes em contato via **WhatsApp**. Atendimento **100% online, em todo o Brasil** (sem endereço físico / sem atendimento presencial).

## Dados reais do cliente (usar exatamente estes)

- **Nome do escritório:** Costa, Pereira & Scapin — Advocacia e Consultoria Jurídica
- **WhatsApp:** (55) 99154-0761 — formato para link `wa.me`: `5555991540761`
- **E-mail:** ncwadvogadosassociados@gmail.com
- **Instagram:** https://www.instagram.com/cpsadvs/ (perfil: @cpsadvs)
- **Advogados / equipe (sem fotos, por opção do cliente):**
  - Caren Costa — OAB/RS 134.851
  - Wilson Pereira — OAB/RS 134.764
  - Neide Scapin — Previdenciarista (Direito Previdenciário; sem OAB informada)
- **Áreas de atuação:** Direito Civil, Empresarial, Trabalhista, de Família, Previdenciário e do Consumidor.

## Identidade visual

- **Cores (design tokens no `:root`):** navy `#0E2A47`, navy-deep `#091b30`, petrol `#1F496D`, gold `#C8A86A`, gold-light `#DCC08F`; fundos branco/`#F7F8FA`.
- **Tipografia:** títulos em **Cormorant Garamond** (serifada); textos em **Manrope** (sans). Carregadas via Google Fonts.
- **Estilo:** sóbrio, elegante, tom institucional. Detalhes em dourado, molduras de canto, fundo navy no hero.
- **Logo:** recriado como **SVG vetorial** (nome do escritório + subtítulo sobre fundo navy), no lugar da imagem original de baixa resolução. Fica no visual do hero.

## Estrutura e ordem das seções

Hero → Escritório → Áreas de Atuação → Diferenciais → Como Funciona → Equipe → FAQ → Contato (CTA) → Rodapé.

O **menu segue a ordem real das seções**: Home, Escritório, Áreas de Atuação, Diferenciais, Equipe, FAQ, Contato. ("Como Funciona" existe como seção, mas não está no menu — decisão para não sobrecarregar a barra.) Menu mobile e links do rodapé espelham essa ordem.

## Decisões já tomadas (manter, salvo pedido em contrário)

- **Sem fotos** dos advogados (cards apenas com monograma, nome, papel e OAB).
- **Sem depoimentos** — foram removidos por serem fictícios. Ver nota de ética abaixo antes de reintroduzir.
- **Atendimento apenas online** — remover/evitar menções a "presencial"; reforçar o online como diferencial.
- **Removidos:** botão de LinkedIn e seção de localização/mapa (atendimento remoto).
- **Ícone do WhatsApp:** usar o glifo **oficial** (não o ícone genérico anterior).
- Botão WhatsApp e ícone do Instagram no cabeçalho aparecem só no **desktop** (>1180px); no mobile ficam dentro do menu ☰.

## Compatibilidade com navegadores/dispositivos antigos (IMPORTANTE)

O cliente e usuários finais podem usar aparelhos antigos (ex.: **iPhone 7 / Safari antigo**). Evitar recursos recentes sem fallback:

- Usar `top/right/bottom/left` explícitos **em vez de `inset`** (só existe no Safari 14.1+).
- Não depender só de `transform` para esconder overlays (menu mobile): usar também **`visibility:hidden`** quando fechado (proteção à prova de falha).
- Prefixar `-webkit-` quando necessário (ex.: `backdrop-filter`).
- Atenção: **`gap` em flexbox** só existe no iOS 14.1+ — se precisar de espaçamento garantido em telas antigas, prever fallback (margens).
- Atenção também a `aspect-ratio` (Safari 15+), usado em vários pontos — considerar fallback se surgir problema.
- Sempre validar responsividade e, idealmente, testar no dispositivo/navegador real.

## Nota de ética (publicidade advocatícia — OAB)

A publicidade de advogados no Brasil é restritiva (Provimento 205/2021 da OAB). Evitar promessas de resultado e ter cautela com depoimentos. Se for reintroduzir depoimentos, usar avaliações reais e verificáveis e revisar com os advogados.

## Notas técnicas

- Arquivo único `index.html`, sem dependências além das fontes do Google.
- JS embutido cuida de: montagem dos links do WhatsApp (a partir de `WHATSAPP_NUMBER`), estado "scrolled" do cabeçalho, menu mobile, parallax sutil do hero, reveal on scroll e acordeão do FAQ.
- Deploy: Vercel.
