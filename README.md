# Acervo — Publicações Adventistas

Protótipo funcional de interface para uma biblioteca digital independente: busca, filtros por categoria, páginas em abas, detalhes por publicação e layouts responsivos.

## Dados localizados em fontes editoriais

A interface reúne quatorze registros: edições bibliográficas específicas verificadas e títulos descritos na página CPB Magabooks. Consulte [`FONTES.md`](FONTES.md) para fontes, ISBNs, paginação e limitações por edição. As imagens remotas são servidas pela CPB e ainda exigem confirmação de licença para redistribuição; as descrições são editoriais e não avaliações independentes. O arquivo `app.js` usa esses links e apresenta as fontes nos detalhes dos livros.

## Precisão e cobertura

Os registros em `app.js` são apenas uma amostra de desenvolvimento, **não um catálogo oficial vigente, completo ou verificado**. Títulos e descrições editoriais foram localizados em páginas CPB e do Ministério de Publicações; detalhes completos de edição existem apenas para parte deles. Três capas de edições específicas foram associadas a URLs extraídas das respectivas páginas de produto; as demais foram omitidas porque não confirmei a imagem exata. Campos bibliográficos não confirmados aparecem como informação não localizada ou são explicitamente sinalizados. A plataforma não é oficial nem endossada pela Igreja Adventista.

## Uso

Abra `index.html` no navegador. Busca por título/autor/categoria, filtros, controles da faixa horizontal e diálogo de detalhes funcionam localmente. A tela de login é informativa; não autentica nem coleta credenciais. Preços SELS e estoque não são mostrados sem fonte pública vigente verificada. O site estático está publicado pelo GitHub Pages. Não há backend, banco persistente, painel editorial, autenticação real, favoritos, listas ou importador conectados; também não há suíte de testes automatizada.

## Próximas etapas de produção

1. Comparar cada região com o catálogo oficial vigente do Ministério de Publicações e da editora responsável; guardar data de consulta e evidências por campo. Priorizar CPB e fontes oficiais adventistas regionais. Não declarar completude antes dessa comparação documentada.
2. Usar PostgreSQL/Supabase (ou equivalente) para persistência, Auth para sessões, Storage para imagens licenciadas e políticas RLS para segurança. Não colocar chave `service_role` no cliente.
3. Fazer importação CSV/JSON validada no servidor, com deduplicação, revisão editorial pendente, auditoria de mudanças e publicação controlada.
4. Para recursos dinâmicos, configurar backend e variáveis de ambiente em serviço seguro. A hospedagem estática atual já usa GitHub Pages ligado à branch principal.
5. Publicar política LGPD, retenção e exclusão antes de coletar dados pessoais. Avaliações de eficácia devem citar evidências independentes específicas e método; não atribuir eficácia por autoridade ou depoimentos.

## Fontes e imagens

Referências iniciais a verificar: [Casa Publicadora Brasileira](https://www.cpb.com.br/) e [Ministério de Publicações Adventista](https://www.adventistas.org/pt/publicacoes/). Os dados bibliográficos foram consultados nas fichas citadas em `FONTES.md`; preços e estoque foram excluídos por serem variáveis e não necessários para esta atualização. Usar somente capas editoriais com origem e licença/condição de uso registradas; ISBN pode auxiliar a correspondência, mas não comprova licença de imagem.

## Esquema de dados

Uma proposta PostgreSQL está em `database/schema.sql`; ainda não foi aplicada a um serviço. Inclui catálogo regional, relações de autores, edições, categorias, fontes por campo, imagens e licenças, revisões de evidência, favoritos e listas privadas, funções, status editorial e logs de auditoria.
