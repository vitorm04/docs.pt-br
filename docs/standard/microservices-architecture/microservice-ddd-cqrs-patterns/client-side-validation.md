---
title: "Validação do lado do cliente (validação nas camadas de apresentação)"
description: "Arquitetura de Microservices .NET para aplicativos .NET em contêineres | Validação do lado do cliente (validação nas camadas de apresentação)"
keywords: "Docker, Microsserviços, ASP.NET, Contêiner"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: db88a3b5c95afdc8d5a20094105f1f5991483ed6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="client-side-validation-validation-in-the-presentation-layers"></a>Validação do lado do cliente (validação nas camadas de apresentação)

Mesmo quando a fonte de verdade é o modelo de domínio e, por fim, você deve ter a validação no nível do modelo de domínio, a validação ainda pode ser tratada no nível do modelo de domínio (do lado do servidor) e do lado do cliente.

Validação do lado do cliente é uma ótima conveniência para usuários. Ele salva o tempo que outra forma seriam passam aguardando uma viagem de ida e para o servidor que pode retornar erros de validação. Em termos de negócios, até mesmo algumas frações de segundos multiplicados centenas de vezes por dia adiciona a muito tempo, despesas e frustração. Validação de imediata e simples permite que os usuários trabalhem com mais eficiência e produzir a melhor qualidade de entrada e saída.

Como o modelo de exibição e o modelo de domínio são diferentes, validação do modelo de exibição e a validação do modelo de domínio podem ser semelhantes, mas têm um propósito diferente. Se você estiver preocupado sobre simulação (não repita por conta própria entidade de segurança), considere que nesse caso reutilização de código também pode significar acoplamento e aplicativos corporativos é mais importante não acoplar o lado do servidor para o lado do cliente que para siga o princípio seco.

Mesmo ao usar a validação do lado do cliente, você sempre deve validar seus comandos ou DTOs de entrada no código do servidor, porque o servidor APIs são um vetor de ataque. Geralmente, fazer as duas é a melhor opção porque se você tiver um aplicativo cliente, de uma perspectiva UX, é melhor ser proativo e não permitir que o usuário insira informações inválidas.

Portanto, no código do lado do cliente é geralmente validar ViewModels. Você também pode validar o cliente DTOs ou comandos de saída antes de enviá-los para os serviços.

A implementação de validação do lado do cliente depende de qual tipo de aplicativo cliente que você está criando. Ele será diferente se você estiver validando dados em um aplicativo web MVC da web com a maior parte do código no .NET, um aplicativo web que está sendo codificado em JavaScript ou TypeScript, a validação SPA ou codificado de um aplicativo móvel com o Xamarin e C\#.

## <a name="additional-resources"></a>Recursos adicionais

### <a name="validation-in-xamarin-mobile-apps"></a>Validação de aplicativos móveis do Xamarin

-   **Validar a entrada de texto e mostrar erros**
    [*https://developer.xamarin.com/recipes/ios/standard\_controles/texto\_campo/Validar\_entrada /*](https://developer.xamarin.com/recipes/ios/standard_controls/text_field/validate_input/)

-   **Retorno de chamada de validação**
    [*https://developer.xamarin.com/samples/xamarin-forms/XAML/ValidationCallback/*](https://developer.xamarin.com/samples/xamarin-forms/XAML/ValidationCallback/)

### <a name="validation-in-aspnet-core-apps"></a>Validação em aplicativos ASP.NET Core

-   **Rick Anderson. Adicionando validação**
    [*https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation*](https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation)

### <a name="validation-in-spa-web-apps-angular-2-typescript-javascript"></a>Validação em SPA Web apps (Angular 2, TypeScript, JavaScript)

-   **Kukic ADO. Validação do formulário angular 2** **
     ** [ *https://scotch.io/tutorials/angular-2-form-validation*](https://scotch.io/tutorials/angular-2-form-validation)

-   **Validação do formulário**
    [*https://angular.io/docs/ts/latest/cookbook/form-validation.html*](https://angular.io/docs/ts/latest/cookbook/form-validation.html)

-   **Validação.** Documentação muito fácil.
    [*http://Breeze.GitHub.IO/doc-js/Validation.HTML*](http://breeze.github.io/doc-js/validation.html)

Em resumo, estes são os conceitos mais importantes no que diz respeito à validação:

-   Entidades e agregações devem impor sua próprias consistência e ser "sempre válido". Raízes agregadas são responsáveis por consistência de várias entidade na mesma agregação.

-   Se você achar que precisa de uma entidade para inserir um estado inválido, considere o uso de um modelo de objeto diferente — por exemplo, usando um DTO temporário até que você criar a entidade de domínio final.

-   Se você precisar criar vários objetos relacionados, como uma agregação, e eles são válidos somente depois que todos eles foram criados, considere usar o padrão de fábrica.

-   Estruturas de validação são melhor usadas em camadas específicas, como a camada de apresentação ou camada de serviço do aplicativo, mas geralmente não na camada de modelo de domínio, porque você precisa executar uma dependência de alta segurança em uma estrutura de infraestrutura.

-   Na maioria dos casos, ter redundância validação no lado do cliente é bom, porque o aplicativo pode ser proativo.


>[!div class="step-by-step"]
[Anterior] (domínio-modelo-camada-validations.md) [Avançar] (domínio-eventos-design-implementation.md)
