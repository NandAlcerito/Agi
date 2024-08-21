// cypress/integration/busca_contato.spec.js

describe('Busca pela palavra "contato"', () => {
    it('O primeiro resultado deve redirecionar para https://agibank.com.br', () => {
        // Passo 1: Acessar a página principal do site.
        cy.visit('https://blogdoagi.com.br');

        // Passo 2: Realizar a busca.
        cy.get('input[type="search"]') // Seletor para o campo de pesquisa
            .type('contato')           // Digita o texto da busca
            .type('{enter}');          // Pressiona Enter

        // Passo 3: Verificar o primeiro resultado.
        cy.get('.post') // Seletor para os resultados da busca
            .first() // Seleciona o primeiro artigo
            .should('contain', 'Contato') // Verifica que o título contém a palavra "Contato"
            .find('a') // Seleciona o link dentro do primeiro resultado
            .then(($link) => {
                // Passo 4: Verifica se o link leva ao URL correto
                const url = $link.prop('href'); // Pega o atributo href do link
                expect(url).to.eq('https://agibank.com.br'); // Verifica se o link é o correto

                // Passo 5: Clicar no link e verificar o redirecionamento
                cy.wrap($link).click(); // Clica no link
            });

        // Passo 6: Verificar se foi redirecionado corretamente.
        cy.url().should('eq', 'https://agibank.com.br'); // Verifica se a URL atual é a correta
    });
});

