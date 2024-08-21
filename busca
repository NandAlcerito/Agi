// cypress/integration/busca_artigos_order.spec.js

describe('Busca e Ordenação de Artigos no Blog', () => {
    it('Realiza busca e exibe artigos ordenados por data decrescente', () => {
        // Passo 1: Acessar a página principal do site
        cy.visit('https://blogdoagi.com.br');

        // Passo 2: Realizar a busca
        cy.get('input[type="search"]') // Seletor para campo de pesquisa
            .type('valor')             // Digita o texto da busca
            .type('{enter}');          // Pressiona Enter

        // Passo 3: Coletar as datas de publicação e os títulos dos artigos
        cy.get('.post') // Ajuste o seletor conforme a estrutura do seu HTML
        .then($articles => {
            const articlesData = [];

            // Percorre cada artigo para coletar as datas
            $articles.each((index, article) => {
                const title = Cypress.$(article).find('h2.entry-title a').text().trim(); // Seletor para o título
                const dateText = Cypress.$(article).find('.published').text().trim(); // Seletor para a data
                
                // Converte a data para um objeto Date
                const dateParts = dateText.split('/').reverse(); // Converte de dd/mm/yyyy para yyyy-mm-dd
                const date = new Date(dateParts.join('-'));
                articlesData.push({ title, date, element: article });
            });

            // Passo 4: Ordenar os artigos por data em ordem decrescente
            const sortedArticles = articlesData.sort((a, b) => b.date - a.date);
            
            // Passo 5: Atualizar a página com os artigos ordenados
            const orderedArticlesContainer = [];

            sortedArticles.forEach(({ title, element }) => {
                orderedArticlesContainer.push(element);
            });

            // Remover todos os artigos do DOM atual e adicionar os artigos ordenados
            cy.get('.ast-row').empty().then(() => {
                orderedArticlesContainer.forEach(article => {
                    cy.get('.ast-row').append(article); // Adiciona os artigos ordenados
                });
            });

            // Passo 6: Verificar se os artigos estão na ordem correta
            const orderedDates = sortedArticles.map(article => article.date);
            // Checa se a data está em ordem decrescente
            expect(orderedDates).to.deep.equal(orderedArticles.map(article => {
                const dateText = Cypress.$(article).find('.published').text().trim();
                const dateParts = dateText.split('/').reverse();
                return new Date(dateParts.join('-'));
            }).sort((a, b) => b - a)); // Ordena as datas em ordem decrescente
        });
    });
});
