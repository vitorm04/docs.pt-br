---
title: Validação do lado do cliente (validação nas camadas de apresentação)
description: Arquitetura de microsserviços do .NET para aplicativos .NET em contêineres | Validação do lado do cliente (validação nas camadas de apresentação)
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: 2adce39561dd2b97910155ebed595a2df7785c11
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="client-side-validation-validation-in-the-presentation-layers"></a>Validação do lado do cliente (validação nas camadas de apresentação)

Mesmo quando a fonte de verdade for o modelo de domínio e, em último caso, você precisar ter validação no nível de modelo de domínio, a validação ainda poderá ser manipulada tanto no nível de modelo de domínio (lado do servidor) quanto do lado do cliente.

A validação do lado do cliente é uma ótima conveniência para usuários. Ela economiza tempo que de outra forma seria gasto aguardando uma viagem de ida e volta que talvez retorne erros de validação. Em termos de negócios, até mesmo algumas frações de segundos multiplicadas por centenas de vezes por dia chega a ser muito tempo, despesa e frustração. A validação imediata e simples permite que os usuários trabalhem com mais eficiência e façam contribuições e produzam entradas e saídas de melhor qualidade.

Como o modelo de exibição e o modelo de domínio são diferentes, a validação do modelo de exibição e do modelo de domínio podem ser semelhantes, mas têm um propósito diferente. Se estiver preocupado com DRY (o princípio Don't Repeat Yourself), considere que, nesse caso, a reutilização de código poderá significar também acoplamento e, em aplicativos empresariais, será mais importante não acoplar o lado do servidor com o do cliente do que seguir o princípio DRY.

Mesmo ao usar a validação do lado do cliente, você sempre deve validar seus comandos ou DTOs de entrada no código do servidor, porque as APIs do servidor são um possível vetor de ataque. Geralmente, fazer as duas é a melhor opção, porque se você tiver um aplicativo cliente, de uma perspectiva do UX, será melhor ser proativo e não permitir que o usuário insira informações inválidas.

Portanto, no código do lado do cliente você normalmente valida os ViewModels. Você também pode validar os DTOs ou comandos de saída do cliente antes de enviá-los aos serviços.

A implementação de validação do lado do cliente depende de qual tipo de aplicativo cliente você está criando. Será diferente se você estiver validando dados em um aplicativo Web MVC da Web com a maioria do código em .NET, um aplicativo Web SPA com a validação sendo codificada em JavaScript ou TypeScript ou um aplicativo móvel codificado com Xamarin e C\#.

## <a name="additional-resources"></a>Recursos adicionais

### <a name="validation-in-xamarin-mobile-apps"></a>Validação de aplicativos móveis Xamarin

-   **Validar a entrada de texto e exibir erros**
    [*https://developer.xamarin.com/recipes/ios/standard\_controls/text\_field/validate\_input/*](https://developer.xamarin.com/recipes/ios/standard_controls/text_field/validate_input/)

-   **Chamada de retorno de validação**
    [*https://developer.xamarin.com/samples/xamarin-forms/XAML/ValidationCallback/*](https://developer.xamarin.com/samples/xamarin-forms/XAML/ValidationCallback/)

### <a name="validation-in-aspnet-core-apps"></a>Validação em aplicativos ASP.NET Core

-   **Rick Anderson. Adicionando validação**
    [*https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation*](https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation)

### <a name="validation-in-spa-web-apps-angular-2-typescript-javascript"></a>Validação em aplicativos Web SPA (Angular 2, TypeScript, JavaScript)

-   **Ado Kukic. Validação de formulário angular 2** **
    **[*https://scotch.io/tutorials/angular-2-form-validation*](https://scotch.io/tutorials/angular-2-form-validation)

-   **Validação de formulário**
    [*https://angular.io/docs/ts/latest/cookbook/form-validation.html*](https://angular.io/docs/ts/latest/cookbook/form-validation.html)

-   **Validação.** Documentação da Breeze.
    [*https://breeze.github.io/doc-js/validation.html*](https://breeze.github.io/doc-js/validation.html)

Em resumo, estes são os conceitos mais importantes no que diz respeito à validação:

-   Entidades e agregações devem impor sua própria consistência e serem "sempre válidas". Raízes agregadas são responsáveis pela consistência de várias entidades dentro da mesma agregação.

-   Se você acha que uma entidade precisa entrar em um estado inválido, considere usar um modelo de objeto diferente – por exemplo, usar um DTO temporário até criar a entidade de domínio definitiva.

-   Se precisar criar vários objetos relacionados, como uma agregação, e eles apenas forem válidos depois que todos tiverem sido criados, considere usar o padrão de fábrica.

-   Estruturas de validação são mais bem usadas em camadas específicas, como a camada de apresentação ou a camada de serviço/do aplicativo, mas geralmente não na camada de modelo de domínio, porque você precisaria usar uma dependência de alta segurança em uma estrutura de infraestrutura.

-   Na maioria dos casos, ter validação redundante no lado do cliente é bom, porque o aplicativo pode ser proativo.


>[!div class="step-by-step"]
[Anterior] (domain-model-layer-validations.md) [Próximo] (domain-events-design-implementation.md)
