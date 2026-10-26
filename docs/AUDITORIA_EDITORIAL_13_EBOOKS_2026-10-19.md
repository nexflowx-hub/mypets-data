# MyPets — Auditoria editorial dos 13 eBooks (primeira passagem)

Data: 2026-10-19
Âmbito: coleção "Cuidar Melhor", idioma principal pt-BR.
Repositório canónico: nexflowx-hub/mypets-data.
Estado desta revisão: **TRIAGEM EDITORIAL DOCUMENTADA — NÃO É HOMOLOGAÇÃO FINAL**.
Estado do catálogo observado: biblioteca draft-v2; metadados dos 13 guias editorial-draft, versão 2.0.0-draft; índice web 2.4.0-rc2.

## 1. Método e limites

Inspeção dos 13 manuscritos Markdown integrais, seus 13 ficheiros de fontes, 13 metadados, 13 previews, source registry, media registry, índice e atlas de 64 raças; contagem de palavras e headings; avaliação editorial contextual de passagens de treino, toxicologia/alimentação, saúde oral e segurança infantil; confronto pontual com páginas oficiais da AVSAB, WSAVA e ASPCA.

**O que esta passagem NÃO comprova:** fact-check linha a linha de todas as afirmações; validação veterinária por profissional habilitado; revisão jurídica da oferta; leitura visual de 100% das páginas finais/PDFs; licença/atribuição e disponibilidade de cada media no browser; aprovação da experiência paga; QA automatizado do Reader completo. Nenhum guia deve ser declarado sales-ready exclusivamente por este relatório.

Padrão interno de referência: docs/CONTENT_STANDARD.md (guia-padrão aprox. 5.000–7.000 palavras úteis; flagship 7.000–10.000+, conforme assunto, sem enchimento) e docs/ARCHITECTURE.md (fonte única, revisão versionada, multimédia licenciada, QA e distribuição segura).

## 2. Resumo quantitativo

- 13/13 manuscritos acessíveis e 13/13 guias com ledgers de fontes.
- 5/13 atingem 5.000 palavras; 8/13 ficam abaixo da meta editorial indicativa (oito títulos, incluindo o sexto com 4.974 palavras). A meta não deve ser preenchida com texto artificial.
- 103 posicionamentos de media, incluindo 13 vídeos e 50 componentes visuais originais, registados nos metadados. Todos os IDs não originais de media apontam para o registry. Não significa que cada vídeo/imagem renderize de facto ou tenha direitos homologados.
- Atlas: 64 perfis estruturados; 64 referências de fotografia em 63 IDs distintos. A fotografia "Bichon Frisé and Poodle" é partilhada pelos perfis Bichon Frisé e Poodle; rever identificação, recorte e legenda por perfil.
- 13 previews extremamente breves: aproximadamente 68–128 palavras. Insuficientes para demonstrar por si só a profundidade de conteúdos que serão vendidos.
- Hierarquia de headings excessivamente fragmentada; em vários guias dezenas de capítulos H2 têm menos de 45 palavras.
- Duplicações de slugs de headings em diversos guias; os identificadores repetidos exigem resolução consistente entre HTML, índice e âncoras.
- Títulos de capa/catálogo e títulos H1 divergem nos guias 07 e 10.
- Inconsistência editorial pt-BR: formas "bebé", "stress" em vários manuscritos; estabelecer glossário e harmonizar, sem alterar citações/títulos originais de fontes.

## 3. Quadro por obra

| # | Guia | Palavras aprox. | Fontes | Media/vídeos | Achado principal (prioridade) |
|---|---|---:|---:|---:|---|
| 01 | Cuidados Essenciais com o Seu Cão | 5.234 | 9 | 7 / 0 | Boa amplitude e limites de saúde; acrescentar referências diretamente verificáveis no próprio Reader/PDF e validar práticas veterinárias (P2). |
| 02 | Os Primeiros 30 Dias com um Filhote | 5.168 | 8 | 7 / 0 | Plano de 30 dias com entradas muito curtas; slug duplicado "estrategia" em headings; detalhar práticas e critérios de progressão (P1/P2). |
| 03 | Treino Gentil: 7 Comandos | 5.111 | 6 | 9 / 4 | 95 headings H2 num guia de 5,1k palavras; subtópicos como "Passo a passo" estão no nível errado e repetidos; reorganizar estrutura e TOC (P1). |
| 04 | Guia das Raças | 9.154 | 22 | 20 / 0 | 64 perfis reais no atlas, mas muitos perfis curtos, headings H3 como "pontos de atenção" repetidos 33 vezes; rever identificadores/legendas fotográficas e precisão das generalizações (P1). |
| 05 | Rotina de Alimentação e Bem-Estar | 5.065 | 7 | 6 / 2 | Necessidade de aviso local claro de ação imediata quando há ingestão suspeita de xilitol/uvas e outras substâncias tóxicas; vet review mandatória (P0). |
| 06 | Linguagem Corporal Canina | 4.974 | 5 | 8 / 0 | Próximo da meta de extensão; 7 dias do exercício resumidos em uma linha; rever progressão pedagógica e terminologia (P2). |
| 07 | Passeios sem Stress | 4.307 | 6 | 8 / 2 | Título H1 difere do catálogo; 53 seções H2 abaixo de 45 palavras; consolidar e aprofundar exemplos reais (P1/P2). |
| 08 | Ficar Sozinho em Casa | 4.181 | 4 | 6 / 0 | 68 seções H2 abaixo de 45 palavras; plano de dias extremamente compacto; esclarecer limites para suspeita de ansiedade de separação e revisão por especialista (P1/P2). |
| 09 | Cão em Apartamento | 4.130 | 5 | 7 / 2 | Dois conjuntos de headings "Dia 1" a "Dia 7" geram slugs duplicados; capítulos muito curtos; corrigir ancoragem antes do release (P1). |
| 10 | Higiene, Banho e Saúde Oral | 4.267 | 3 | 6 / 0 | H1 diverge do catálogo; semáforos "Verde/Amarelo/Vermelho" repetidos; 91 seções H2 abaixo de 45 palavras; vet review da odontologia (P1). |
| 11 | Adotei um Cão Adulto | 4.200 | 5 | 6 / 0 | Divisão excessiva em tópicos muito curtos; heading "saude" duplicado; aprofundar plano de adaptação e sinais de risco (P1/P2). |
| 12 | Cães e Crianças | 4.411 | 4 | 6 / 1 | Conteúdo de supervisão inicial adequado; heading semáforo duplicado e uso de "bebé" num livro pt-BR; QA de segurança com adulto/veterinário (P1). |
| 13 | 50 Ideias de Enriquecimento para Cães | 4.005 | 4 | 7 / 2 | Confirmadas 50 ideias numeradas, 1–50 sem falta; 102 seções H2 abaixo de 45 palavras; enriquecer instruções, segurança e adaptações por porte/idade (P1/P2). |

### Profundidade e utilidade

Uma obra premium não é avaliada exclusivamente pelo comprimento. Há conteúdo educativo útil, listas, planificadores, exercícios, linguagem acessível e preocupação com treino não aversivo. No entanto, os títulos 07–13 têm frequentemente secções de 20–40 palavras. A maior prioridade editorial é substituir uma sucessão de microsecções por capítulos com contexto, demonstração concreta, exemplos, alertas e exercícios verificáveis; não acrescentar enchimento para bater métricas.

## 4. Segurança e fontes

Pontos positivos amostrados:
- Treino Gentil: sete comandos identificáveis; abordagem baseada em recompensa e alerta para agressão/medo/pânico; orientação geral consistente com o position statement da AVSAB: https://avsab.org/wp-content/uploads/2021/08/AVSAB-Humane-Dog-Training-Position-Statement-2021.pdf
- Cães e Crianças: supervisão ativa, separação nos contextos de risco, não punir rosnado, não testar tolerância.
- Higiene e Saúde Oral: alerta de avaliação profissional, não usar pasta humana, instrução gradual; existência da referência 2026 confirmada em https://wsava.org/global-guidelines/dental-guidelines/
- Alimentação: rejeita dietas terapêuticas prescritas por leigos e dietas caseiras improvisadas; referência geral de toxicologia consistente com https://www.aspca.org/pet-care/aspca-poison-control/people-foods-avoid-feeding-your-pets

**Bloqueio de revisão clínica (P0):** no guia de alimentação, as secções locais "Uvas e passas" e "Xilitol" não explicam de forma suficientemente inequívoca o carácter potencialmente urgente da exposição. Acrescentar instrução editorial de contacto imediato com atendimento veterinário/centro toxicológico veterinário no caso de ingestão suspeita, sem aconselhar medidas caseiras, indução de vómito ou doses. Submeter a médico-veterinário para aprovação técnica.

Validar também por especialista: estratégias de socialização/vacinação do filhote; sinais de pânico por separação; limites de avaliação comportamental; dados anatómicos e predisposição a doenças por raça; orientação para crianças e recém-nascidos; segurança de brinquedos alimentares.

Os ledgers referenciam IDs do source registry e não têm IDs de fonte desconhecidos. Porém, as bibliografias apresentadas nos próprios manuscritos geralmente descrevem entidades sem URL individual clicável, título preciso/data/revisão por afirmação. Criar um quadro de fontes para o produto (capítulo → alegação → fonte → URL → data de consulta → licença) e tornar as referências de leitura acessíveis ao consumidor.

## 5. Metadados, Reader e media

- A versão do índice e o estado dos metadados são distintos: índice 2.4.0-rc2 versus 13 metadata editorial-draft 2.0.0-draft e manifest draft-v2. Reconciliar states e changelog antes de qualquer tag/release.
- Em vários guias existem headings repetidos e slugs HTML duplicados, especialmente nas famílias "Dia 1–7", "Passo a passo", "Verde/Amarelo/Vermelho" e nas subseções de raça. No Reader, implementar IDs únicos determinísticos e sincronizar o índice, ou reestruturar corretamente a hierarquia de subtítulos.
- O último capítulo de vários manuscritos inclui instruções internas de implementação de media ("renderizar..."). Garantir que essas instruções não chegam ao PDF, EPUB ou downloads; o atual Reader usa uma rotina específica para ocultá-las, mas é necessário testar em todos os formatos.
- O registo de 103 colocações é um plano de media com referências, não uma certificação da renderização ou dos direitos. Validar cada asset, crédito, licenciamento, alt-text e link externo/embed, com evidência desktop/mobile e comportamento no modo impressão/PDF.
- O atlas de 64 perfis apresenta uma única imagem partilhada de dois cães para Poodle e Bichon Frisé, necessitando decisão de identidade visual e recorte por perfil; não assumir automaticamente que é uma imagem errada, pois o ficheiro identifica as duas raças.
- Os previews de 68–128 palavras devem incluir uma amostra contextual real, uma ou duas páginas úteis e indicativo fiel do que há no conteúdo completo, sem revelar todo o produto.

## 6. Gates de homologação

**P0 — segurança/credibilidade (bloqueia release editorial):**
1. Corrigir alertas de toxicologia no guia 05 e obter revisão veterinária qualificada para todas as obras com conteúdo de saúde/segurança.
2. Confirmar direitos, atribuições e disponibilidade dos media publicados, sobretudo vídeos de terceiros e fotografia de raças.
3. Aprovar explicitamente estados editoriais e congelar versões com checksums e revisão responsável.

**P1 — qualidade de produto e leitura:**
4. Corrigir IDs de headings duplicados e a estrutura H2/H3 dos títulos 02, 03, 04, 09, 10, 11, 12; regression test dos links do TOC.
5. Uniformizar títulos de catálogo/H1 dos guias 07 e 10; aplicar glossário pt-BR, sem misturar ortografias.
6. Enriquecer conteúdo fragmentado, especialmente 07–13, preservando originalidade, valor e acessibilidade.
7. Completar referências acessíveis no Reader/PDF e dar previews representativos.

**P2 — acabamento premium:**
8. QA de checklist, planos de dias, legendas, imagens, fontes e hierarquia visual em desktop/mobile.
9. Verificar PDF final e reader/impresso contra a mesma fonte canónica; garantir que não há instruções editoriais internas em formatos finais.
10. Gate de teste: lint/typecheck/build, QA de links, imagens, vídeos, navegação, índices, segurança de conteúdos protegidos e rollback.

## 7. Veredicto desta passagem

**EXIGE REVISÃO ANTES DA HOMOLOGAÇÃO EDITORIAL FINAL.** A coleção tem valor educativo e boa fundação de pesquisa, mas não está editorialmente pronta para receber certificação de versão final premium. Prosseguir em branch de trabalho com PR e correções por prioridade. Publicação na main, aprovação clínica e ativação comercial exigem os gates acima.

Este documento é uma auditoria de primeira passagem baseada em evidência do código/conteúdo e amostragem clínica editorial, e NÃO substitui a releitura humana/veterinária completa.
