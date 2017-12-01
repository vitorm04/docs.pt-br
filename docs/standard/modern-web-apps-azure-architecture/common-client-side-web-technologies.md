---
title: Tecnologias de web do lado cliente comuns
description: Projetar aplicativos Web modernos com ASP.NET Core e o Azure | Tecnologias de web do lado cliente comuns
author: ardalis
ms.author: wiwagn
ms.date: 10/07/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.openlocfilehash: 1084aee3d81a5df6ac99d6ec0e2ef647b4173c24
ms.sourcegitcommit: bbde43da655ae7bea1977f7af7345eb87bd7fd5f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/21/2017
---
# <a name="common-client-side-web-technologies"></a>Tecnologias de Web do lado cliente comuns

> "Sites devem aparência de dentro e fora."  
> _-Paul Cookson_

## <a name="summary"></a>Resumo

Aplicativos do ASP.NET Core são aplicativos web e eles normalmente se baseiam em tecnologias da web do lado do cliente como HTML, CSS e JavaScript. Separando o conteúdo da página (HTML) de seu layout e estilo (CSS) e seu comportamento (via JavaScript), aplicativos web complexos podem aproveitar o princípio de separação de preocupações. As alterações futuras na estrutura, o design ou o comportamento do aplicativo podem ser feitas mais facilmente quando essas preocupações não são entrelaçadas.

Enquanto o HTML e CSS são relativamente estável, JavaScript, por meio de estruturas de aplicativo e os desenvolvedores de utilitários trabalham com para criar aplicativos baseados na web, está desenvolvendo em uma velocidade. Este capítulo examina algumas maneiras que JavaScript é usado por desenvolvedores da web como parte do desenvolvimento de aplicativos, que fornece uma visão geral das bibliotecas do lado de cliente Angular e reagir.

## <a name="html"></a>HTML

HTML (linguagem de marcação de hipertexto) é a linguagem de marcação padrão usada para criar páginas da web e aplicativos da web. Os blocos de construção de páginas, que representa o texto formatado, imagens, entradas do formulário e outras estruturas de formulário de seus elementos. Quando um navegador faz uma solicitação para uma URL, se a busca de uma página ou um aplicativo, a primeira coisa que é retornado é um documento HTML. Este documento HTML pode referenciar ou incluir informações adicionais sobre sua aparência e o layout na forma de CSS ou comportamento na forma de JavaScript.

## <a name="css"></a>CSS

CSS (folhas de estilo em cascata) é usada para controlar a aparência e o layout de elementos HTML. Estilos CSS podem ser aplicados diretamente a um elemento HTML, definidos separadamente na mesma página, ou definidos em um arquivo separado e referenciados pela página. Estilos em cascata com base em como eles são usados para selecionar um determinado elemento HTML. Por exemplo, um estilo pode se aplicar a um documento inteiro, mas poderia ser substituído por um estilo aplicado a um determinado elemento. Da mesma forma, um estilo de elemento específico poderia ser substituído por um estilo aplicado a uma classe CSS aplicada ao elemento, que por sua vez deve ser substituído por um estilo de direcionamento de uma instância específica do elemento (por meio de sua id). Figura 6-1

**Figura 6-1.** Regras de CSS especificidade, na ordem.

![](./media/image6-1.png)

É melhor para manter os estilos em seus próprios arquivos de folha de estilos separada e para usar a seleção baseada em cascata para implementar consistentes e reutilizáveis estilos dentro do aplicativo. Colocar as regras de estilo de HTML deve ser evitado e aplicando estilos para elementos individuais específicos (em vez de classes inteiras de elementos ou elementos que tiveram uma determinada classe CSS aplicada a eles) deve ser uma exceção, não a regra.

### <a name="css-preprocessors"></a>Pré-processadores CSS

Folhas de estilo CSS não têm suporte para lógica condicional, variáveis e outros recursos de linguagem de programação. Assim, folhas de estilo grandes geralmente incluem um lote de repetição, como a mesma cor, fonte ou outra configuração é aplicada a muitas variações diferentes de elementos HTML e classes CSS. Os pré-processadores CSS podem ajudar suas folhas de estilo siga o [princípio seco](http://deviq.com/don-t-repeat-yourself/) adicionando suporte para variáveis e lógica.

Os pré-processadores CSS mais populares são Sass e menor. Ambos estendem CSS e são compatíveis com ele, que significa que um arquivo CSS simples é um Sass válido ou menos arquivos. Sass é baseado em Ruby menor é baseado em JavaScript e ambos geralmente são executados como parte do processo de desenvolvimento local. Ambos têm o comando de suporte disponível, bem como interno no Visual Studio das ferramentas de linha para executá-los usando o Gulp ou o Assistente de tarefas.

## <a name="javascript"></a>JavaScript

O JavaScript é uma linguagem de programação dinâmica e interpretada que foi padronizada na especificação da linguagem ECMAScript. É a linguagem de programação da web. Como o CSS, JavaScript pode ser definido como atributos dentro de elementos HTML, como blocos de script em uma página ou em arquivos separados. Como CSS, é geralmente recomendado para organizar JavaScript em arquivos separados, mantendo separado tanto quanto possível do HTML encontrado em páginas da web individuais ou exibições de aplicativo.

Ao trabalhar com JavaScript no seu aplicativo web, há algumas tarefas que você geralmente precisa executar:

-   Selecionando um elemento HTML e recuperando e/ou atualizar seu valor

-   Consultar uma API da Web para dados

-   Enviar um comando para uma API da Web (e responder a um retorno de chamada com seu resultado)

-   Executar a validação

Você pode executar todas essas tarefas com JavaScript sozinho, mas muitas bibliotecas existem para facilitar essas tarefas. Uma da primeira e mais bem-sucedidas dessas bibliotecas é jQuery, que continua a ser uma opção popular para simplificar essas tarefas em páginas da web. Para aplicativos de página única (SPAs), jQuery não fornece muitos dos recursos de desejado Angular e reagir oferecem.

### <a name="legacy-web-apps-with-jquery"></a>Aplicativos Web herdados com jQuery

Embora antigos por padrões de estrutura de JavaScript, jQuery continua a ser uma biblioteca muito mais usada para trabalhar com HTML/CSS e criação de aplicativos que fazem chamadas AJAX para APIs da web. No entanto, jQuery opera no nível do modelo de objeto de documento (DOM) navegador e, por padrão oferece apenas um modelo de imperativo, em vez de declarativa.

Por exemplo, imagine que se o valor da caixa de texto exceder 10, um elemento na página deve ficar visível. Em jQuery, isso seria normalmente ser implementado escrevendo um manipulador de eventos com o código de inspecionar o valor da caixa de texto e defina a visibilidade do elemento de destino com base nesse valor. Esta é uma abordagem imperativa, com base em código. Outra estrutura em vez disso, pode usar a associação de dados para associar a visibilidade do elemento para o valor da caixa de texto declarativamente. Isso não requer gravar nenhum código, mas em vez disso, requer apenas decorar os elementos envolvidos com atributos de associação de dados. Como os comportamentos do lado do cliente se tornar mais complexos, associação de dados se aproximar frequentemente resultam em soluções mais simples com menos código e complexidade condicional.

### <a name="jquery-vs-a-spa-framework"></a>jQuery vs uma estrutura SPA

| **Fator** | **jQuery** | **Angular**|
|--------------------------|------------|-------------|
| Abstrai o DOM | **Sim** | **Sim** |
| Suporte AJAX | **Sim** | **Sim** |
| Associação de dados declarativo | **No** | **Sim** |
| Roteamento de estilo MVC | **No** | **Sim** |
| Modelagem | **No** | **Sim** |
| Roteamento de Link profundo | **No** | **Sim** |

Maioria dos recursos do jQuery não tem intrinsecamente pode ser adicionadas com a adição de outras bibliotecas. No entanto, uma estrutura SPA como Angular fornece estes recursos de forma mais integrada, pois ele é foi projetado com todas elas em mente, desde o início. Além disso, o jQuery é uma biblioteca muito obrigatório, que significa que você precisa chamar funções jQuery para fazer algo com o jQuery. Muito do trabalho e funcionalidade que fornecem estruturas SPA declarativamente, pode ser feito sem exigir nenhum código real a ser gravado.

Associação de dados é um ótimo exemplo disso. Em jQuery, geralmente leva apenas uma linha de código para obter o valor de um elemento DOM ou para definir o valor de um elemento. No entanto, você precisa gravar este código sempre que você precisa alterar o valor do elemento e às vezes, isso acontecerá em várias funções em uma página. Outro exemplo comum é a visibilidade do elemento. JQuery, pode haver muitos lugares diferentes em que você escreve código para controlar se determinados elementos eram visíveis. Em cada um desses casos, ao usar a associação de dados, nenhum código precisa ser gravado. Você deve vincular simplesmente o valor ou a visibilidade do (s) em questão para um *viewmodel* na página e as alterações que viewmodel deve ser refletida automaticamente nos elementos associados.

### <a name="angular-spas"></a>SPAs angulares

AngularJS rapidamente se tornou uma das estruturas de JavaScript mais populares do mundo. Com Angular 2, a equipe recriado a estrutura de ponta a ponta para cima (usando [TypeScript](https://www.typescriptlang.org/)) e rebatizado do AngularJS para simplesmente Angular. Atualmente em versão 4, Angular continua a ser uma estrutura robusta para a criação de aplicativos de página única.

Aplicativos angulares são criados de componentes. Componentes de combinam modelos HTML com objetos especiais e controlam uma parte da página. Um componente simples de documentos do Angular é mostrado aqui:

```js
import { Component } from '@angular/core';

@Component({
    selector: 'my-app',
    template: `<h1>Hello {{name}}</h1>`
})

export class AppComponent { name = 'Angular'; }
```

Componentes são definidos usando o @Component função decorador, que usa metadados sobre o componente. A propriedade de seletor identifica a id do elemento na página da qual este componente será exibido. A propriedade de modelo é um modelo HTML simple que inclua um espaço reservado que corresponde à propriedade de nome do componente, definida na última linha.

Trabalhando com modelos, em vez de elementos DOM e os componentes de aplicativos Angular podem operar em um nível mais alto de abstração e com menos código geral que os aplicativos escritos usando apenas o JavaScript (também chamado de "baunilha JS") ou jQuery. Angular também impõe algumas ordem para organizar seus arquivos de script do lado do cliente. Por convenção, os aplicativos Angular usam uma estrutura de pasta comum, com arquivos de script de módulo e o componente localizados em uma pasta de aplicativo. Scripts angulares preocupado com a criação, implantação e teste o aplicativo geralmente estão localizados em uma pasta de nível superior.

Angular também faz grande uso de ferramentas de interface de linha de comando (CLI). Introdução ao desenvolvimento Angular localmente (supondo que você já tiver instalado de npm e git) consiste em simplesmente clonar um repositório do GitHub e execução \`de instalação de npm\` e \`npm iniciar\`. Além disso, Angular fornecido sua própria ferramenta CLI que pode criar projetos, adicionar arquivos e ajudar com tarefas de teste, empacotamento e implantação. Essa CLI ferramentas amigável torna Angular especialmente compatível com o ASP.NET Core, que também apresenta excelente suporte CLI.

A Microsoft desenvolveu um aplicativo de referência, [eShopOnContainers](http://aka.ms/MicroservicesArchitecture), que inclui uma implementação Angular SPA. Este aplicativo inclui módulos Angular para gerenciar o armazenamento online itens da cesta, carga e exibição do seu catálogo de compras e tratamento de criação de ordem. Você pode exibir e baixar o aplicativo de exemplo do [GitHub](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/Web/WebSPA).

### <a name="react"></a>reagir

Diferentemente de Angular, que oferece uma completa da implementação do padrão Model-View-Controller, reagir só está preocupada com modos de exibição. Não é uma estrutura, uma biblioteca, portanto, para criar um SPA precisará utilizar bibliotecas adicionais.

Um dos recursos mais importantes do reagir é o uso de DOM virtual. O DOM virtual fornece reagir com várias vantagens, inclusive a capacidade de teste (sem necessidade de um navegador para testar reagir e suas interações com seu DOM virtual) e desempenho (virtual DOM pode otimizar as partes do DOM real precisam ser atualizados).

Reagir também é incomum em como ele funciona com HTML. Em vez de uma separação estrita entre o código e marcação (com referências a JavaScript que aparecem nos atributos HTML talvez), reagir adiciona HTML diretamente no seu código JavaScript como JSX. JSX é a sintaxe de HTML que pode compilar até JavaScript puro. Por exemplo:

```js
<ul>
{ authors.map(author =>
    <li key={author.id}>{author.name}</li>
)}
</ul>
```

Se você já souber o JavaScript, reagir de aprendizagem deve ser fácil. Há não praticamente a mesma curva de aprendizado ou sintaxe especial envolvidas como com Angular ou outras bibliotecas populares.

Como reagir não está em uma estrutura completa, você geralmente fará outras bibliotecas para lidar com coisas como roteamento, chamadas de API e o gerenciamento de dependência na web. A vantagem é que você pode escolher a biblioteca recomendada para cada um deles, mas a desvantagem é que você precisa fazer todas essas decisões e verifique se todas as bibliotecas escolhidas funcionam bem em conjunto quando terminar. Se você quiser um bom ponto de partida, você pode usar um starter kit como reagir Slingshot, que prepackages um conjunto de bibliotecas compatíveis com reagir.

### <a name="choosing-a-spa-framework"></a>Escolher uma estrutura SPA

Ao considerar quais estrutura JavaScript funcionam melhor para dar suporte a SPA, tenha em mente as seguintes considerações:

-   Sua equipe esteja familiarizado com a estrutura e suas dependências (incluindo TypeScript em alguns casos)?

-   Como opinionated é a estrutura e concorde com sua forma padrão de fazer as coisas?

-   (Ou uma biblioteca complementar) inclui todos os recursos que seu aplicativo requer?

-   É bem documentados?

-   Está ativa como sua comunidade? Criação de novos projetos criados com ele?

-   Está ativo como sua equipe principal? Os problemas sejam resolvidas e novas versões são enviados regularmente?

Estruturas de JavaScript continuam a desenvolver com uma velocidade. Use as considerações listadas acima para ajudar a reduzir o risco de escolher uma estrutura que mais tarde será indesejado depende. Se você for particularmente avessas a riscos, considere uma estrutura que oferece suporte comercial e/ou está sendo desenvolvida por uma grande empresa.

> ### <a name="references--client-web-technologies"></a>Referências – tecnologias da Web do cliente
> - **HTML e CSS**  
> <https://www.w3.org/Standards/webdesign/htmlcss>
> - **Sass vs. MENOS**  
> <https://www.keycdn.com/blog/sass-VS-less/>
> - **Aplicativos ASP.NET Core com menos Sass e fonte incrível de estilo**  
> <https://docs.microsoft.com/ASPNET/Core/Client-Side/Less-sass-FA>
> - **Desenvolvimento do lado do cliente no ASP.NET Core**  
> <https://docs.microsoft.com/ASPNET/Core/Client-Side/>
> - **jQuery**  
> <https://jQuery.com/>
> - **jQuery vs AngularJS**  
> <https://www.airpair.com/angularjs/posts/jQuery-angularjs-Comparison-Migration-Walkthrough>
> - **Angular**  
> <https://angular.IO/>
> - **Reagir**  
> <https://Facebook.GitHub.IO/React/>
> - **Reagir Slingshot**  
> <https://GitHub.com/coryhouse/React-slingshot>
> - **Reagir vs Angular comparação de 2**  
> <https://www.codementor.IO/codementorteam/React-VS-angular-2-Comparison-Beginners-Guide-lvz5710ha>
> - **5 estruturas JavaScript melhor de 2017**  
> <https://hackernoon.com/5-Best-JavaScript-frameworks-in-2017-7a63b3870282>

>[!div class="step-by-step"]
[Anterior] (comum-web-aplicativo-architectures.md) [Avançar] (develop-asp-net-core-mvc-apps.md)
