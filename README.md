# ImpactHub

Landing page em React, TypeScript e Vite, migrada de `ImpactHub_Landing_Editorial_V2.html`. O HTML original permanece intacto para comparação.

## Executar localmente

Requer Node.js 22.12 ou superior.

```sh
npm ci
npm run dev
```

Abra o endereço exibido pelo Vite, normalmente `http://127.0.0.1:5173`.

```sh
npm run build
npm run preview
```

O build verifica o TypeScript e gera a aplicação estática em `dist/`.

## Organização

- `src/App.tsx`: composição da página e seleção do modal.
- `src/components/`: cabeçalho, rodapé e modal acessível de doação/ONG.
- `src/sections/`: oito seções na mesma ordem da referência, incluindo carrossel e FAQ.
- `src/data/`: campanhas tipadas e perguntas frequentes, separadas da apresentação.
- `src/styles/reference.css`: estilos da referência, preservados e formatados.
- `src/styles/accessibility.css`: ajustes para o carrossel React, toque e validação.
- `tests/landing.spec.ts`: comparação visual, responsividade e jornadas interativas.

## Comportamento

Navegação por âncoras, menu mobile, filtros por categoria, setas e gestos no carrossel, FAQ expansível e modal institucional de ONG. As doações financeiras permitem valores predefinidos ou personalizados; as materiais permitem escolher item e quantidade. Ambas terminam em confirmação explicitamente simulada.

O modal mantém o foco, permite fechamento com Escape ou clique no fundo e devolve o foco ao botão de origem. Valores financeiros inválidos e quantidades não inteiras ou menores que 1 são rejeitados. O carrossel aceita setas do teclado e corrige seu índice ao mudar de largura.

Não há backend, envio de formulários, cadastro, pagamento ou persistência de doações. O cadastro de ONG mantém o modal informativo do HTML; não foi acrescentado um formulário inexistente na referência. Para integração futura, os dados das campanhas podem ser substituídos por uma API e a simulação do modal por um fluxo de confirmação do servidor.

## Validação

```sh
npx playwright install chromium
npm test
```

Os testes abrem o HTML original e a versão React no mesmo navegador em 375, 390, 768, 1280, 1440 e 1920 px. Conferem as dimensões e posições das seções, títulos e imagens, comparam capturas completas e verificam ausência de overflow horizontal, erros de JavaScript e falhas de carregamento de imagens/fontes. As capturas e diferenças são gravadas em `artifacts/visual/`; o relatório interativo fica em `playwright-report/`.

As fotos continuam hospedadas no Unsplash e a fonte DM Sans no Google Fonts. A execução e a comparação visual precisam de conexão para carregar esses recursos.

### Diferença conhecida

A foto da primeira campanha no HTML (`photo-1457140072488-8c9b5d9da5bf`) retorna HTTP 404. A implementação reutiliza a foto de animais da quinta campanha. As capturas e os mapas de diferença preservam essa alteração; a métrica automática de fidelidade exclui apenas o retângulo dessa foto, identificado nos arquivos `comparison-*.json`. As posições e dimensões da foto continuam incluídas na comparação geométrica. O HTML original não foi alterado.
