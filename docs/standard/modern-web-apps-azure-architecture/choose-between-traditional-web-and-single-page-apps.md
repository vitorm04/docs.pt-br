---
title: "Escolha entre aplicativos web tradicionais e aplicativos de única página"
description: Projetar aplicativos web modernos com ASP.NET Core e Microsoft Azure
author: ardalis
ms.author: wiwagn
ms.date: 10/06/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: eb830ede1b644700a80f0e9fac2f3608deb88276
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/23/2017
---
# <a name="choose-between-traditional-web-apps-and-single-page-apps-spas"></a>Escolha entre aplicativos Web tradicionais e aplicativos de página única (SPAs)

> "Lei do Atwood: qualquer aplicativo que pode ser gravado em JavaScript, eventualmente serão gravados em JavaScript."  
> _\- Jeff Atwood_

## <a name="summary"></a>Resumo

Há duas abordagens gerais para a criação de aplicativos web hoje: aplicativos web tradicionais que realizar a maior parte da lógica do aplicativo no servidor e aplicativos de página única (SPAs) que executam a maioria da lógica de interface de usuário em um navegador da web, comunicação com o servidor de web principalmente por meio de APIs da web. Uma abordagem híbrida também é possível, o que está sendo mais simples de host um ou mais avançados como SPA sub aplicativos dentro de um aplicativo da web tradicional maior.

Você deve usar os aplicativos web tradicionais quando:

-   Requisitos do lado do cliente do aplicativo são simples ou até mesmo somente leitura.

-   Seu aplicativo precisa funcionar em navegadores sem suporte a JavaScript.

-   Sua equipe estiver familiarizado com JavaScript ou TypeScript técnicas de desenvolvimento.

Você deve usar um SPA quando:

-   Seu aplicativo deve expor uma interface de usuário sofisticada com muitos recursos.

-   Sua equipe estiver familiarizado com o desenvolvimento de JavaScript e/ou TypeScript.

-   O aplicativo já deve expor uma API para outros clientes (públicos ou internos).

Além disso, as estruturas do SPA exigem maior arquitetura e experiência em segurança. Eles experimentam variação maior devido a atualizações frequentes e novas estruturas de aplicativos web tradicionais. Configurando processos de compilação e implantação automatizados e utilizando as opções de implantação como contêineres são mais difíceis com aplicativos SPA que os aplicativos web tradicionais.

Melhorias na experiência do usuário tornou possível pelo modelo do SPA devem ser avaliadas em relação a essas considerações.

## <a name="when-to-choose-traditional-web-apps"></a>Quando escolher aplicativos web tradicionais

A seguir está uma explicação mais detalhada dos motivos declarados anteriormente para aplicativos web tradicionais de separação.

**Seu aplicativo tem requisitos simples, possivelmente somente leitura, do lado do cliente**

Muitos aplicativos web são consumidos principalmente de modo somente leitura, a grande maioria de seus usuários. Aplicativos somente leitura (ou predominantemente de leitura) tendem a ser muito mais simples do que aqueles que manter e manipular uma grande quantidade de estado. Por exemplo, um mecanismo de pesquisa pode consistir em um único ponto de entrada com uma caixa de texto e uma segunda página para exibir os resultados da pesquisa. Usuários anônimos podem facilmente fazer solicitações, e há pouca necessidade de lógica do lado do cliente. Da mesma forma, um blog ou conteúdo do sistema de gerenciamento voltado ao público normalmente consiste principalmente de conteúdo com pouca comportamento do lado do cliente. Esses aplicativos facilmente criados como aplicativos web tradicionais com base em servidor que executar lógica no servidor web e renderizam HTML a ser exibida no navegador. O fato de que cada página exclusiva do site possui sua própria URL que pode ser indexado por mecanismos de pesquisa (por padrão, sem a necessidade de adicioná-lo como um recurso separado do aplicativo) e o indicador também é um benefício claro nesses cenários.

**Seu aplicativo precisa funcionar em navegadores sem suporte a JavaScript**

Aplicativos da Web que precisam para funcionar em navegadores com acesso limitado ou nenhum suporte a JavaScript devem ser escritos usando fluxos de trabalho de aplicativo da web tradicional (ou pelo menos ser capaz de fazer fallback para tal comportamento). SPAs exigem JavaScript do lado do cliente para a função; Se não estiver disponível, SPAs não são uma boa opção.

**Sua equipe estiver familiarizado com as técnicas de desenvolvimento de JavaScript ou TypeScript**

Se sua equipe estiver familiarizada com JavaScript ou TypeScript, mas está familiarizada com o desenvolvimento de aplicativos do lado do servidor web, em seguida, eles provavelmente será capazes de fornecer um aplicativo da web tradicional mais rapidamente do que um SPA. A menos que learning para programa SPAs é uma meta ou a experiência do usuário proporcionada por um SPA é necessária, aplicativos web tradicionais são uma opção mais produtiva para equipes que já estão familiarizados com criá-los.

## <a name="when-to-choose-spas"></a>Quando escolher SPAs

A seguir está uma explicação mais detalhada de quando escolher um estilo de aplicativos de página única de desenvolvimento para seu aplicativo web.

**Seu aplicativo deve expor uma interface de usuário sofisticada com muitos recursos**

SPAs pode dar suporte a funcionalidade avançada do lado do cliente que não exija recarregar a página usuários executarem ações ou navegarem entre as áreas do aplicativo. SPAs pode carregar mais rapidamente, buscar dados em segundo plano, e as ações de usuário individuais são mais ágil na resposta como recargas de página inteira são raras. SPAs pode dar suporte a atualizações incrementais, salvando formulários parcialmente preenchidos ou documentos sem que o usuário tenha que clicar em um botão para enviar um formulário. SPAs pode dar suporte a comportamentos de cliente avançados, como arrastar e soltar muito mais rapidamente do que os aplicativos tradicionais. SPAs podem ser projetados para ser executado em modo desconectado, fazer atualizações em um modelo de cliente que eventualmente são sincronizados para o servidor quando uma conexão for restabelecida. Você deve escolher um aplicativo de estilo do SPA se os requisitos do aplicativo incluem funcionalidade avançada que vai além do que oferecem formulários HTML típicos.

Observe que com frequência SPAs necessário implementar recursos internos para aplicativos web tradicionais, como exibir uma URL significativa no endereço barra reflete a operação atual (e permitindo que os usuários para o indicador ou link profundo para essa URL para retornar a ela). SPAs também deve permitir que os usuários usem o navegador botões Voltar e Avançar com resultados que não é surpresa para eles.

**Sua equipe estiver familiarizado com o desenvolvimento de JavaScript e/ou TypeScript**

Gravar SPAs exige familiaridade com JavaScript e/ou TypeScript e técnicas de programação do lado do cliente e bibliotecas. Sua equipe deve ser competente na gravação moderno JavaScript usando uma estrutura SPA como Angular.

> ### <a name="references--spa-frameworks"></a>Referências – SPA estruturas
> - **AngularJS**  
> <https://angularjs.org/>
> - **Comparação de estruturas de JavaScript populares 4**  
> <https://www.developereconomics.com/feature-comparison-of-4-popular-js-mv-frameworks>

**O aplicativo já deve expor uma API para outros clientes (públicos ou internos)**

Se você já estiver dando suporte uma API da web para uso por outros clientes, ele pode exigir menos esforço para criar uma implementação do SPA que utiliza essas APIs em vez de reprodução a lógica no formulário do lado do servidor. SPAs fazem uso extensivo de APIs da web para consultar e atualizar dados, como os usuários interagem com o aplicativo.

## <a name="decision-table--traditional-web-or-spa"></a>Tabela de decisão – tradicional da Web ou SPA

A tabela de decisão a seguir resume alguns dos fatores a considerar ao escolher entre um aplicativo da web tradicional e um SPA básico.

  | **Factor** | **Aplicativo da Web tradicional** | **Aplicativo de página única** |
  |---|---|---|
  | Equipe necessária familiaridade com TypeScript/JavaScript | **Minimal** | **Necessária** |
  | Oferecer suporte a navegadores sem scripts | **Com suporte** | Sem suporte |
  | Comportamento do aplicativo cliente mínimo | **Well-Suited** | **Exagero** |
  | Requisitos de Interface de usuário avançadas e complexas | **Limitado** | **Well-Suited** |

>[!div class="step-by-step"]
[Anterior] (moderno-web-aplicativos-characteristics.md) [Avançar](architectural-principles.md)
