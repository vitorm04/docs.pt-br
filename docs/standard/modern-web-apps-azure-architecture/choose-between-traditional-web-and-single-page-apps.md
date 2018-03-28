---
title: Escolha entre aplicativos Web tradicionais e aplicativos de página única
description: Projetar aplicativos Web modernos com o ASP.NET Core e o Microsoft Azure
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
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/23/2017
---
# <a name="choose-between-traditional-web-apps-and-single-page-apps-spas"></a>Escolher entre aplicativos Web tradicionais e SPAs (aplicativos de página única)

> "Lei de Atwood: qualquer aplicativo que pode ser escrito em JavaScript será, em última análise, escrito em JavaScript."  
> _\- Jeff Atwood_

## <a name="summary"></a>Resumo

Há duas abordagens gerais para a criação de aplicativos Web hoje: os aplicativos Web tradicionais que executam a maior parte da lógica do aplicativo no servidor e os SPAs (aplicativos de página única) que executam a maior parte da lógica da interface do usuário em um navegador da Web, comunicando-se com o servidor Web principalmente por meio de APIs Web. Uma abordagem híbrida também é possível, e a mais simples é hospedar um ou mais subaplicativos avançados semelhantes ao SPA dentro de um aplicativo Web tradicional maior.

Você deve usar os aplicativos Web tradicionais quando:

-   Os requisitos do lado do cliente do aplicativo são simples ou até mesmo somente leitura.

-   Seu aplicativo precisa funcionar em navegadores sem suporte a JavaScript.

-   Sua equipe não está familiarizada com as técnicas de desenvolvimento do JavaScript ou do TypeScript.

Você deve usar um SPA quando:

-   Seu aplicativo precisa expor uma interface do usuário avançada com muitos recursos.

-   Sua equipe está familiarizada com o desenvolvimento do JavaScript e/ou do TypeScript.

-   Seu aplicativo já deve expor uma API para outros clientes (internos ou públicos).

Além disso, as estruturas de SPA exigem um maior conhecimento em arquitetura e segurança. Elas passam por uma maior variação devido a atualizações frequentes e novas estruturas comparado aos aplicativos Web tradicionais. A configuração de processos de compilação e de implantação automatizados e a utilização de opções de implantação como contêineres são mais difíceis com aplicativos SPA do que com aplicativos Web tradicionais.

As melhorias na experiência do usuário possibilitadas pelo modelo do SPA devem ser avaliadas em relação a essas considerações.

## <a name="when-to-choose-traditional-web-apps"></a>Quando escolher aplicativos Web tradicionais

Veja a seguir uma explicação mais detalhada dos motivos para escolher aplicativos Web tradicionais mencionados anteriormente.

**Seu aplicativo tem requisitos simples do lado do cliente, possivelmente somente leitura**

Muitos aplicativos Web são consumidos principalmente em um modo somente leitura pela grande maioria de seus usuários. Os aplicativos somente leitura (ou predominantemente de leitura) tendem a ser muito mais simples do que aqueles que mantêm e manipulam uma grande quantidade de estado. Por exemplo, um mecanismo de pesquisa pode consistir em um único ponto de entrada com uma caixa de texto e uma segunda página para exibição dos resultados da pesquisa. Os usuários anônimos podem fazer solicitações com facilidade, e há pouca necessidade de uma lógica do lado do cliente. Da mesma forma, um aplicativo voltado para o público de um sistema de gerenciamento de conteúdo ou blog normalmente consiste principalmente em conteúdo com pouco comportamento do lado do cliente. Aplicativos desse tipo são criados com facilidade como aplicativos Web tradicionais baseados em servidor que executam a lógica no servidor Web e renderizam o HTML a ser exibido no navegador. O fato de que cada página exclusiva do site tem sua própria URL que pode ser marcada e indexada por mecanismos de pesquisa (por padrão, sem a necessidade de adicioná-la como um recurso separado do aplicativo) também é um benefício claro nesses cenários.

**Seu aplicativo precisa funcionar em navegadores sem suporte a JavaScript**

Os aplicativos Web que precisam funcionar em navegadores com suporte limitado ou nenhum suporte a JavaScript precisam ser escritos com fluxos de trabalho de aplicativo Web tradicional (ou, pelo menos, poder fazer fallback para esse comportamento). Os SPAs exigem um JavaScript do lado do cliente para funcionar; se ele não estiver disponível, os SPAs não serão uma boa opção.

**Sua equipe não está familiarizada com as técnicas de desenvolvimento do JavaScript ou do TypeScript**

Caso sua equipe não esteja familiarizada com o JavaScript ou o TypeScript, mas esteja familiarizada com o desenvolvimento de aplicativos Web do lado do servidor, provavelmente, ela poderá fornecer um aplicativo Web tradicional mais rapidamente do que um SPA. A menos que o aprendizado de programação de SPAs seja uma meta ou a experiência do usuário proporcionada por um SPA seja necessária, os aplicativos Web tradicionais serão uma opção mais produtiva para equipes que já estão familiarizadas com sua criação.

## <a name="when-to-choose-spas"></a>Quando escolher SPAs

Veja a seguir uma explicação mais detalhada de quando escolher um estilo de desenvolvimento de Aplicativos de Página Única para seu aplicativo Web.

**Seu aplicativo precisa expor uma interface do usuário avançada com muitos recursos**

Os SPAs podem dar suporte à funcionalidade avançada do lado do cliente que não exige o recarregamento da página conforme os usuários executam ações ou navegam entre as áreas do aplicativo. OS SPAs podem ser carregados com mais agilidade, buscando dados em segundo plano, e as ações de usuário individuais são mais ágeis na resposta pois os recarregamentos de página inteira são raros. Os SPAs podem dar suporte a atualizações incrementais, salvando formulários ou documentos parcialmente preenchidos sem que o usuário precise clicar em um botão para enviar um formulário. Os SPAs podem ser compatíveis com comportamentos avançados do lado do cliente, como operações do tipo "arrastar e soltar", com muito mais agilidade do que os aplicativos tradicionais. Os SPAs podem ser designados para serem executados em um modo desconectado, fazendo atualizações em um modelo do lado do cliente que são, por fim, sincronizadas com o servidor depois que uma conexão é restabelecida. Você deve escolher um aplicativo no estilo SPA se os requisitos do aplicativo incluem uma funcionalidade avançada que vai além do que os formulários HTML típicos oferecem.

Observe que, com frequência, os SPAs precisam implementar recursos internos de aplicativos Web tradicionais, como a exibição de uma URL significativa na barra de endereços que reflete a operação atual (e permitindo que os usuários marquem ou criem um link profundo dessa URL para retornar a ela). Os SPAs também devem permitir que os usuários usem os botões Voltar e Avançar do navegador com resultados que não os surpreenderão.

**Sua equipe está familiarizado com o desenvolvimento do JavaScript e/ou do TypeScript**

A configuração de SPAs exige familiaridade com o JavaScript e/ou o TypeScript e bibliotecas e técnicas de programação do lado do cliente. Sua equipe deve ser competente na escrita de JavaScript moderno usando uma estrutura de SPA como o Angular.

> ### <a name="references--spa-frameworks"></a>Referências – Estruturas de SPA
> - **AngularJS**  
> <https://angularjs.org/>
> - **Comparação entre quatro estruturas de JavaScript populares**  
> <https://www.developereconomics.com/feature-comparison-of-4-popular-js-mv-frameworks>

**Seu aplicativo já deve expor uma API para outros clientes (internos ou públicos)**

Caso você já esteja dando suporte a uma API Web para uso por outros clientes, poderá ser necessário menos esforço para criar uma implementação de SPA que utiliza essas APIs em vez de reproduzir a lógica no formulário do lado do servidor. Os SPAs fazem uso extensivo de APIs Web para consultar e atualizar os dados conforme os usuários interagem com o aplicativo.

## <a name="decision-table--traditional-web-or-spa"></a>Tabela de decisão – Web tradicional ou SPA

A tabela de decisão a seguir resume alguns dos fatores básicos a serem considerados ao escolher entre um aplicativo Web tradicional e um SPA.

  | **Fator** | **Aplicativo Web tradicional** | **Aplicativo de página única** |
  |---|---|---|
  | É necessária a familiaridade da equipe com JavaScript/TypeScript | **Mínima** | **Necessária** |
  | Suporte a navegadores sem scripts | **Com suporte** | **Não compatível** |
  | Comportamento mínimo do aplicativo do lado do cliente | **Apropriado** | **Exagero** |
  | Requisitos avançados e complexos de interface do usuário | **Limitado** | **Apropriado** |

>[!div class="step-by-step"]
[Anterior] (modern-web-applications-characteristics.md) [Próximo](architectural-principles.md)
