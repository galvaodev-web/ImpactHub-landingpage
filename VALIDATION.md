# Validação — ImpactHub

Validação realizada em 10/11/2026 com Chromium, React 19, TypeScript e Vite. O HTML original foi mantido intacto.

## Resultado

- `npm test`: **8 testes aprovados**.
- `npm run build`: **aprovado**, com verificação TypeScript e geração de `dist/`.
- Comparação geométrica: posições e dimensões idênticas nos elementos verificados em todas as seis larguras.
- Sem overflow horizontal, imagens quebradas ou erros de console na implementação.
- Carregamento da fonte DM Sans verificado.
- Inspeção visual das capturas desktop e mobile realizada.

| Largura | Pixels diferentes fora da foto substituída | Diferença na captura completa | Geometria |
| ------- | -----------------------------------------: | ----------------------------: | --------- |
| 375 px  |                                         42 |                     0,001296% | Idêntica  |
| 390 px  |                                         42 |                     0,001270% | Idêntica  |
| 768 px  |                                         38 |                     0,000724% | Idêntica  |
| 1280 px |                                         11 |                     0,000113% | Idêntica  |
| 1440 px |                                         11 |                     0,000098% | Idêntica  |
| 1920 px |                                          9 |                     0,000058% | Idêntica  |

O percentual usa o número de pixels da captura completa como denominador. A comparação usa `pixelmatch` com limiar de cor de 0,1, desconsiderando antialiasing conforme o comportamento padrão da ferramenta. Os números não representam identidade absoluta de todos os pixels.

## Exceção visual documentada

A URL da foto da primeira campanha no HTML retorna HTTP 404. A versão React usa a foto de animais já presente na quinta campanha. Apenas o retângulo dessa foto é excluído da métrica acima; sua posição e suas dimensões permanecem na verificação geométrica. Os arquivos `artifacts/visual/reference-*.png`, `react-*.png` e `diff-*.png` mostram as capturas e a diferença bruta, incluindo a substituição. Os arquivos `comparison-*.json` registram o retângulo excluído, a contagem bruta de diferenças e as medições completas.

## Interações verificadas

- Todos os filtros, contagem de campanhas, setas e limites do carrossel.
- Ajuste do índice ao redimensionar e navegação por gesto no mobile.
- Menu mobile, links internos e fechamento após navegar.
- Seleção de valor predefinido, valor personalizado com centavos e bloqueio de valor negativo.
- Seleção de material e quantidade; bloqueio de quantidade zero.
- Confirmações demonstrativas, retorno ao formulário e avisos de ausência de transação real.
- Modal institucional de ONG, fechamento pelo fundo e pela tecla Escape.
- Foco inicial, contenção de foco e retorno ao botão de origem.
- Abertura e fechamento das quatro perguntas frequentes.

As verificações automatizadas cobrem Chromium. As fotografias e fontes externas precisam de conexão com a internet. Não foi feita integração com backend ou publicação em hospedagem.
