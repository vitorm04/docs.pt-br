---
title: Tecnologias da Web comuns do lado do cliente
description: Projetar aplicativos Web modernos com o ASP.NET Core e o Azure | Tecnologias da Web comuns do lado do cliente
author: ardalis
ms.author: wiwagn
ms.date: 10/07/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: c77b6fecdea3620a4f807dfa9b3501f78bb247d2
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2018
---
# <a name="common-client-side-web-technologies"></a>Tecnologias da Web comuns do lado do cliente

> "Os sites devem ter uma bela aparência em todo lugar."  
> _- Paul Cookson_

## <a name="summary"></a>Resumo

Os aplicativos ASP.NET Core são aplicativos Web e normalmente se baseiam em tecnologias da Web do lado do cliente como HTML, CSS e JavaScript. Ao separar o conteúdo da página (o HTML) de seu layout e estilo (o CSS) e seu comportamento (por meio do JavaScript), os aplicativos Web complexos podem aproveitar o princípio da Separação de Interesses. As alterações futuras na estrutura, no design ou no comportamento do aplicativo podem ser feitas com mais facilidade quando esses interesses não são entrelaçados.

Embora o HTML e o CSS sejam relativamente estáveis, o JavaScript, por meio das estruturas do aplicativo e dos utilitários com os quais os desenvolvedores trabalham para criar aplicativos baseados na Web, está evoluindo em uma velocidade vertiginosa. Este capítulo examina algumas maneiras pelas quais o JavaScript é usado por desenvolvedores da Web como parte do desenvolvimento de aplicativos, além de fornecer uma visão geral de alto nível das bibliotecas do lado do cliente Angular e React.

## <a name="html"></a>HTML

A linguagem HTML é a linguagem de marcação padrão usada para criar páginas da Web e aplicativos Web. Seus elementos formam os blocos de construção de páginas, representando o texto formatado, imagens, entradas de formulário e outras estruturas. Quando um navegador faz uma solicitação para uma URL, independentemente se ele está buscando uma página ou um aplicativo, a primeira coisa retornada é um documento HTML. Esse documento HTML pode referenciar ou incluir informações adicionais sobre sua aparência e o layout na forma de CSS ou sobre seu comportamento na forma de JavaScript.

## <a name="css"></a>CSS

O CSS (folhas de estilos em cascata) é usado para controlar a aparência e o layout de elementos HTML. Os estilos CSS podem ser aplicados diretamente a um elemento HTML, definidos separadamente na mesma página ou definidos em um arquivo separado e referenciados pela página. Os estilos são aplicados em cascata de acordo com a forma como são usados para selecionar determinado elemento HTML. Por exemplo, um estilo pode se aplicar a um documento inteiro, mas ser substituído por um estilo aplicado a um elemento específico. Da mesma forma, um estilo específico a um elemento é substituído por um estilo aplicado a uma classe CSS que foi aplicada ao elemento, que, por sua vez, é substituído por um estilo direcionado a uma instância específica desse elemento (por meio de sua ID). Figura 6-1

**Figura 6-1.** Regras de especificidade do CSS, na ordem.

![](./media/image6-1.png)

É melhor manter os estilos em seus próprios arquivos de folha de estilos separados e usar a cascata baseada em seleção para implementar estilos consistentes e reutilizáveis dentro do aplicativo. A colocação das regras de estilo em HTML deve ser evitada e a aplicação de estilos a elementos individuais específicos (em vez de classes inteiras de elementos ou elementos que tiveram determinada classe CSS aplicada a eles) deve ser uma exceção, não a regra.

### <a name="css-preprocessors"></a>Pré-processadores do CSS

As folhas de estilos CSS não têm suporte para lógica condicional, variáveis e outros recursos de linguagem de programação. Portanto, folhas de estilos grandes geralmente incluem um lote de repetição, pois a mesma cor, fonte ou outra configuração é aplicada a muitas variações diferentes de elementos HTML e classes CSS. Os pré-processadores do CSS podem ajudar as folhas de estilos a seguirem o [princípio DRY](http://deviq.com/don-t-repeat-yourself/), com a adição de suporte para variáveis e lógica.

Os pré-processadores do CSS mais populares são o Sass e LESS. Ambos estendem o CSS e são compatíveis com versões anteriores dele, o que significa que um arquivo CSS simples é um arquivo do Sass ou LESS válido. O Sass é baseado em Ruby e o LESS é baseado em JavaScript e ambos costumam ser executados como parte do processo de desenvolvimento local. Os dois têm ferramentas de linha de comando disponíveis, bem como suporte interno no Visual Studio para executá-las com tarefas do Gulp ou Grunt.

## <a name="javascript"></a>JavaScript

O JavaScript é uma linguagem de programação dinâmica e interpretada que foi padronizada na especificação da linguagem ECMAScript. É a linguagem de programação da Web. Assim como o CSS, o JavaScript pode ser definido como atributos em elementos HTML, como blocos de script em uma página ou em arquivos separados. Assim como o CSS, é geralmente recomendado organizar o JavaScript em arquivos separados, mantendo-o separado tanto quanto possível do HTML encontrado em páginas da Web individuais ou exibições do aplicativo.

Ao trabalhar com o JavaScript no aplicativo Web, há algumas tarefas que você geralmente precisará executar:

-   Selecionar um elemento HTML e recuperar e/ou atualizar seu valor

-   Consultar dados em uma API Web

-   Enviar um comando para uma API Web (e responder a um retorno de chamada com seu resultado)

-   Realizar a validação

Você pode executar todas essas tarefas apenas com o JavaScript, mas muitas bibliotecas existem para facilitar essas tarefas. Uma das primeiras e mais bem-sucedidas dessas bibliotecas é o jQuery, que continua sendo uma opção popular para simplificar essas tarefas em páginas da Web. Para SPAs (Aplicativos de Página Única), o jQuery não fornece muitos dos recursos desejados oferecidos pelo Angular e React.

### <a name="legacy-web-apps-with-jquery"></a>Aplicativos Web herdados com o jQuery

Embora seja antigo de acordo com os padrões de estrutura do JavaScript, o jQuery continua sendo uma biblioteca muito usada para trabalhar com HTML/CSS e criar aplicativos que fazem chamadas AJAX a APIs Web. No entanto, o jQuery opera no nível do DOM (Modelo de Objeto do Documento) do navegador e, por padrão, oferece apenas um modelo de imperativo, em vez de declarativo.

Por exemplo, imagine que, se o valor da caixa de texto exceder 10, um elemento na página precisará ficar visível. No jQuery, isso normalmente será implementado com a escrita de um manipulador de eventos com um código que inspecionará o valor da caixa de texto e definirá a visibilidade do elemento de destino com base nesse valor. Essa é uma abordagem imperativa, baseada em código. Em vez disso, outra estrutura poderá usar a associação de dados para associar a visibilidade do elemento ao valor da caixa de texto de forma declarativa. Isso não exige nenhuma codificação, mas apenas a decoração dos elementos envolvidos com atributos de associação de dados. Conforme os comportamentos do lado do cliente ficam mais complexos, as abordagens de associação de dados frequentemente resultam em soluções mais simples com menos código e complexidade condicional.

### <a name="jquery-vs-a-spa-framework"></a>jQuery vs. uma estrutura de SPA

| **Fator** | **jQuery** | **Angular**|
|--------------------------|------------|-------------|
| Abstrai o DOM | **Sim** | **Sim** |
| Suporte do AJAX | **Sim** | **Sim** |
| Associação de dados declarativa | **No** | **Sim** |
| Roteamento no estilo MVC | **No** | **Sim** |
| Modelagem | **No** | **Sim** |
| Roteamento de link profundo | **No** | **Sim** |

A maioria dos recursos que o jQuery não tem intrinsecamente pode ser adicionada com a adição de outras bibliotecas. No entanto, uma estrutura de SPA como o Angular fornece esses recursos de forma mais integrada, pois foi projetado com todos eles em mente, desde o início. Além disso, o jQuery é uma biblioteca imperativa, o que significa que você precisa chamar funções do jQuery para fazer qualquer coisa com o jQuery. Grande parte do trabalho e da funcionalidade fornecida pelas estruturas de SPA pode ser feita de forma declarativa, sem a necessidade de codificação real.

A associação de dados é um ótimo exemplo disso. No jQuery, geralmente, é necessário apenas uma linha de código para obter o valor de um elemento DOM ou para definir o valor de um elemento. No entanto, você precisa escrever esse código sempre que precisa alterar o valor do elemento e, às vezes, isso acontecerá em várias funções em uma página. Outro exemplo comum é a visibilidade do elemento. No jQuery, pode haver muitos lugares diferentes em que você codificará para controlar se determinados elementos eram visíveis. Em cada um desses casos, ao usar a associação de dados, nenhuma codificação precisa ser feita. Você apenas vincula o valor ou a visibilidade dos elementos em questão a um *modelo de exibição* na página e as alterações nesse modelo de exibição são refletidas automaticamente nos elementos associados.

### <a name="angular-spas"></a>SPAs do Angular

O AngularJS rapidamente se tornou uma das estruturas de JavaScript mais populares do mundo. Com o Angular 2, a equipe reformulou totalmente a estrutura (usando o [TypeScript](https://www.typescriptlang.org/)) e passou a chamar o AngularJS de simplesmente Angular. Atualmente na versão 4, o Angular continua sendo uma estrutura robusta para a criação de Aplicativos de Página Única.

Os aplicativos do Angular baseiam-se em componentes. Os componentes combinam modelos HTML com objetos especiais e controlam uma parte da página. Um componente simples da documentação do Angular é mostrado aqui:

```js
import { Component } from '@angular/core';

@Component({
    selector: 'my-app',
    template: `<h1>Hello {{name}}</h1>`
})

export class AppComponent { name = 'Angular'; }
```

Os componentes são definidos com a função de decorador @Component, que usa metadados sobre o componente. A propriedade de seletor identifica a ID do elemento na página na qual esse componente será exibido. A propriedade de modelo é um modelo HTML simples que inclui um espaço reservado que corresponde à propriedade de nome do componente, definida na última linha.

Trabalhando com componentes e modelos, em vez de elementos DOM, os aplicativos do Angular podem operar em um nível superior de abstração e com menos código geral comparado aos aplicativos escritos apenas com JavaScript (também chamado "JS baunilha") ou com o jQuery. O Angular também impõe uma ordem de como organizar os arquivos de script do lado do cliente. Por convenção, os aplicativos do Angular usam uma estrutura de pastas comum, com arquivos de script de módulo e componente localizados em uma pasta do aplicativo. Os scripts do Angular referentes à criação, à implantação e ao teste do aplicativo geralmente estão localizados em uma pasta de nível superior.

O Angular também faz intenso uso de ferramentas de CLI (interface de linha de comando). A introdução ao desenvolvimento local com o Angular (supondo que você já tenha instalado o GIT e o npm) consiste em simplesmente clonar um repositório do GitHub e executar \`npm install\` e \`npm start\`. Além disso, o Angular fornece sua própria ferramenta de CLI que pode criar projetos, adicionar arquivos e ajudar com tarefas de teste, agrupamento e implantação. Essa facilidade de utilização das ferramentas de CLI tornam o Angular especialmente compatível com o ASP.NET Core, que também apresenta compatibilidade excelente com a CLI.

A Microsoft desenvolveu um aplicativo de referência, o [eShopOnContainers](http://aka.ms/MicroservicesArchitecture), que inclui uma implementação SPA do Angular. Esse aplicativo inclui módulos do Angular para gerenciar a cesta de compras da loja online, carregar e exibir itens do catálogo e manipular a criação de ordens. Exiba e baixe o aplicativo de exemplo no [GitHub](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/Web/WebSPA).

### <a name="react"></a>React

Ao contrário do Angular, que oferece uma implementação completa do padrão Modelo-Exibição-Controlador, o React está voltado para exibições. Ele não é uma estrutura, apenas uma biblioteca e, portanto, para criar um SPA, precisará utilizar bibliotecas adicionais.

Um dos recursos mais importantes do React é o uso de um DOM virtual. O DOM virtual oferece várias vantagens ao React, incluindo o desempenho (o DOM virtual pode otimizar quais partes do DOM real precisam ser atualizadas) e a capacidade de teste (sem a necessidade de ter um navegador para testar o React e suas interações com seu DOM virtual).

O React também é incomum na forma como funciona com HTML. Em vez de ter uma separação estrita entre o código e a marcação (talvez com a exibição das referências ao JavaScript em atributos HTML), o React adiciona o HTML diretamente ao seu código JavaScript como JSX. O JSX é uma sintaxe semelhante ao HTML que pode ser compilada até um JavaScript puro. Por exemplo:

```js
<ul>
{ authors.map(author =>
    <li key={author.id}>{author.name}</li>
)}
</ul>
```

Se você já conhece o JavaScript, aprender a usar o React deve ser fácil. A curva de aprendizado ou a sintaxe especial envolvida não é tão grande quanto a do Angular ou de outras bibliotecas populares.

Como o React não é uma estrutura completa, geralmente, você desejará ter outras bibliotecas para manipular aspectos como roteamento, chamadas à API Web e gerenciamento de dependências. A vantagem é que você pode escolher a melhor biblioteca para cada um deles, mas a desvantagem é que você precisa tomar todas essas decisões e verificar se todas as bibliotecas escolhidas funcionam bem em conjunto quando terminar. Caos deseje um bom ponto de partida, use um kit de início como o React Slingshot, que pré-empacota um conjunto de bibliotecas compatíveis com o React.

### <a name="choosing-a-spa-framework"></a>Escolhendo uma estrutura de SPA

Ao considerar qual estrutura de JavaScript funcionará melhor para dar suporte ao SPA, tenha em mente as seguintes considerações:

-   Sua equipe está familiarizada com a estrutura e suas dependências (incluindo o TypeScript em alguns casos)?

-   Quão "teimosa" é a estrutura e você concorda com sua forma padrão de fazer as coisas?

-   Ela (ou uma biblioteca complementar) inclui todos os recursos necessários para seu aplicativo?

-   Ela está bem documentada?

-   Quão ativa é sua comunidade? A criação de novos projetos é feita com ela?

-   Quão ativa é sua equipe principal? Os problemas estão sendo resolvidos e novas versões são fornecidas regularmente?

As estruturas de JavaScript continuam evoluindo em uma velocidade vertiginosa. Use as considerações listadas acima para ajudar a atenuar o risco de escolher uma estrutura da qual mais tarde você se arrependerá de ter uma dependência. Caso você seja particularmente avesso a riscos, considere uma estrutura que oferece suporte comercial e/ou que está sendo desenvolvida por uma empresa grande.

> ### <a name="references--client-web-technologies"></a>Referências – Tecnologias da Web do cliente
> - **HTML e CSS**  
> <https://www.w3.org/standards/webdesign/htmlcss>
> - **Sass vs. LESS**  
> <https://www.keycdn.com/blog/sass-vs-less/>
> - **Criando estilos para aplicativos ASP.NET Core com o LESS, Sass e Font Awesome**  
> <https://docs.microsoft.com/aspnet/core/client-side/less-sass-fa>
> - **Desenvolvimento do lado do cliente no ASP.NET Core**  
> <https://docs.microsoft.com/aspnet/core/client-side/>
> - **jQuery**  
> <https://jquery.com/>
> - **jQuery vs. AngularJS**  
> <https://www.airpair.com/angularjs/posts/jquery-angularjs-comparison-migration-walkthrough>
> - **Angular**  
> <https://angular.io/>
> - **React**  
> <https://facebook.github.io/react/>
> - **React Slingshot**  
> <https://github.com/coryhouse/react-slingshot>
> - **Comparação entre o React e o Angular 2**  
> <https://www.codementor.io/codementorteam/react-vs-angular-2-comparison-beginners-guide-lvz5710ha>
> - **As cinco melhores estruturas de JavaScript de 2017**  
> <https://hackernoon.com/5-best-javascript-frameworks-in-2017-7a63b3870282>

>[!div class="step-by-step"]
[Anterior] (common-web-application-architectures.md) [Próximo] (develop-asp-net-core-mvc-apps.md)
