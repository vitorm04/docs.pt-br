---
title: Escolha entre aplicativos Web tradicionais e aplicativos de página única
description: Saiba como escolher entre aplicativos Web tradicionais e SPAs (aplicativos de única página) ao criar aplicativos Web.
author: ardalis
ms.author: wiwagn
ms.date: 12/04/2019
ms.openlocfilehash: d4ed76455001c1a0b8e2e2f1bb90ce8715dd0052
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77450102"
---
# <a name="choose-between-traditional-web-apps-and-single-page-apps-spas"></a>Escolher entre aplicativos Web tradicionais e SPAs (aplicativos de página única)

> "Lei de Atwood: qualquer aplicativo que pode ser escrito em JavaScript será, em última análise, escrito em JavaScript."  
> _\-Jeff Atwood_

Há duas abordagens gerais para a criação de aplicativos Web hoje: os aplicativos Web tradicionais que executam a maior parte da lógica do aplicativo no servidor e os SPAs (aplicativos de página única) que executam a maior parte da lógica da interface do usuário em um navegador da Web, comunicando-se com o servidor Web principalmente por meio de APIs Web. Uma abordagem híbrida também é possível, sendo a mais simples hospedar um ou mais subaplicativos ricos semelhantes a SPA dentro de um aplicativo web tradicional maior.

Use aplicativos web tradicionais quando:

- Os requisitos do lado do cliente do aplicativo são simples ou até mesmo somente leitura.

- Seu aplicativo precisa funcionar em navegadores sem suporte a JavaScript.

- Sua equipe não está familiarizada com as técnicas de desenvolvimento do JavaScript ou do TypeScript.

Use um SPA quando:

- Seu aplicativo precisa expor uma interface do usuário avançada com muitos recursos.

- Sua equipe está familiarizada com o desenvolvimento do JavaScript e/ou do TypeScript.

- Seu aplicativo já deve expor uma API para outros clientes (internos ou públicos).

Além disso, as estruturas de SPA exigem um maior conhecimento em arquitetura e segurança. Elas passam por uma maior variação devido a atualizações frequentes e novas estruturas comparado aos aplicativos Web tradicionais. Configurar processos automatizados de construção e implantação e utilizar opções de implantação como contêineres pode ser mais difícil com aplicativos SPA do que aplicativos web tradicionais.

As melhorias na experiência do usuário possibilitadas pela abordagem do SPA devem ser ponderadas em relação a essas considerações.

## <a name="blazor"></a>Blazor

O ASP.NET Core 3.0 apresenta um novo modelo para a criação de uma interface do usuário sofisticada, interativa e combinável chamado Blazor. O lado do servidor Blazor permite que os desenvolvedores construam interface do usuário com razor no servidor e para que este código seja entregue ao navegador e executado do lado do cliente usando [o WebAssembly](https://webassembly.org/). O lado do servidor Blazor está disponível agora com ASP.NET Core 3.0 ou posterior. O lado do cliente blazor deve estar disponível em 2020.

O Blazor fornece uma nova terceira opção a ser considerada ao avaliar se deve construir um aplicativo web puramente renderizado por servidor ou um SPA. Você pode construir comportamentos ricos, semelhantes a SPA, do lado do cliente usando o Blazor, sem a necessidade de um desenvolvimento JavaScript significativo. Os aplicativos Blazor podem chamar APIs para solicitar dados ou executar operações do lado do servidor.

Considere construir sua aplicação web com blazor quando:

- Seu aplicativo deve expor uma interface de usuário rica

- Sua equipe está mais confortável com o desenvolvimento .NET do que o desenvolvimento javaScript ou TypeScript

Para saber mais sobre o Blazor, confira a [Introdução ao Blazor](https://blazor.net/docs/get-started.html).

## <a name="when-to-choose-traditional-web-apps"></a>Quando escolher aplicativos Web tradicionais

A seguir há uma explicação mais detalhada dos motivos já mencionados para escolher os aplicativos Web tradicionais.

**Seu aplicativo tem requisitos simples do lado do cliente, possivelmente somente leitura**

Muitos aplicativos Web são consumidos principalmente em um modo somente leitura pela grande maioria de seus usuários. Os aplicativos somente leitura (ou predominantemente de leitura) tendem a ser muito mais simples do que aqueles que mantêm e manipulam uma grande quantidade de estado. Por exemplo, um mecanismo de pesquisa pode consistir em um único ponto de entrada com uma caixa de texto e uma segunda página para exibição dos resultados da pesquisa. Os usuários anônimos podem fazer solicitações com facilidade, e há pouca necessidade de uma lógica do lado do cliente. Da mesma forma, um aplicativo voltado para o público de um sistema de gerenciamento de conteúdo ou blog normalmente consiste principalmente em conteúdo com pouco comportamento do lado do cliente. Esses aplicativos são facilmente construídos como aplicativos web tradicionais baseados em servidor, que executam lógica no servidor web e renderizam HTML para serem exibidos no navegador. O fato de que cada página exclusiva do site tem sua própria URL que pode ser marcada e indexada por mecanismos de pesquisa (por padrão, sem a necessidade de adicioná-la como um recurso separado do aplicativo) também é um benefício claro nesses cenários.

**Seu aplicativo precisa funcionar em navegadores sem suporte a JavaScript**

Os aplicativos Web que precisam funcionar em navegadores com suporte limitado ou nenhum suporte a JavaScript precisam ser escritos com fluxos de trabalho de aplicativo Web tradicional (ou, pelo menos, poder fazer fallback para esse comportamento). Os SPAs exigem um JavaScript do lado do cliente para funcionar; se ele não estiver disponível, os SPAs não serão uma boa opção.

**Sua equipe não está familiarizada com as técnicas de desenvolvimento JavaScript ou TypeScript**

Caso sua equipe não esteja familiarizada com o JavaScript ou o TypeScript, mas esteja familiarizada com o desenvolvimento de aplicativos Web do lado do servidor, provavelmente, ela poderá fornecer um aplicativo Web tradicional mais rapidamente do que um SPA. A menos que o aprendizado de programação de SPAs seja uma meta ou a experiência do usuário proporcionada por um SPA seja necessária, os aplicativos Web tradicionais serão uma opção mais produtiva para equipes que já estão familiarizadas com sua criação.

## <a name="when-to-choose-spas"></a>Quando escolher SPAs

Veja a seguir uma explicação mais detalhada de quando escolher um estilo de desenvolvimento de Aplicativos de Página Única para seu aplicativo Web.

**Seu aplicativo precisa expor uma interface do usuário avançada com muitos recursos**

Os SPAs podem dar suporte à funcionalidade avançada do lado do cliente que não exige o recarregamento da página conforme os usuários executam ações ou navegam entre as áreas do aplicativo. OS SPAs podem ser carregados com mais agilidade, buscando dados em segundo plano, e as ações de usuário individuais são mais ágeis na resposta pois os recarregamentos de página inteira são raros. Os SPAs podem dar suporte a atualizações incrementais, salvando formulários ou documentos parcialmente preenchidos sem que o usuário precise clicar em um botão para enviar um formulário. Os SPAs podem ser compatíveis com comportamentos avançados do lado do cliente, como operações do tipo "arrastar e soltar", com muito mais agilidade do que os aplicativos tradicionais. Os SPAs podem ser designados para serem executados em um modo desconectado, fazendo atualizações em um modelo do lado do cliente que são, por fim, sincronizadas com o servidor depois que uma conexão é restabelecida. Escolha um aplicativo no estilo SPA se os requisitos do seu aplicativo incluem uma funcionalidade rica que vai além do que os formulários HTML típicos oferecem.

Frequentemente, os SPAs precisam implementar recursos incorporados aos aplicativos web tradicionais, como exibir uma URL significativa na barra de endereços refletindo a operação atual (e permitir que os usuários marquem ou vinculem profundamente a essa URL para retornar a ela). Os SPAs também devem permitir que os usuários usem os botões Voltar e Avançar do navegador com resultados que não os surpreenderão.

**Sua equipe está familiarizada com o desenvolvimento do JavaScript e/ou TypeScript**

A configuração de SPAs exige familiaridade com o JavaScript e/ou o TypeScript e bibliotecas e técnicas de programação do lado do cliente. Sua equipe deve ser competente na escrita de JavaScript moderno usando uma estrutura de SPA como o Angular.

> ### <a name="references--spa-frameworks"></a>Referências – Estruturas de SPA
>
> - **Angular**  
>   <https://angular.io>
> - **Reagir**
>   <https://reactjs.org/>
> - **Comparação de Estruturas em JavaScript**  
>   <https://jsreport.io/the-ultimate-guide-to-javascript-frameworks/>

**Sua aplicação já deve expor uma API para outros clientes (internos ou públicos)**

Caso você já esteja dando suporte a uma API Web para uso por outros clientes, poderá ser necessário menos esforço para criar uma implementação de SPA que utiliza essas APIs em vez de reproduzir a lógica no formulário do lado do servidor. Os SPAs fazem uso extensivo de APIs Web para consultar e atualizar os dados conforme os usuários interagem com o aplicativo.

## <a name="when-to-choose-blazor"></a>Quando escolher Blazor

A seguir, uma explicação mais detalhada de quando escolher Blazor para o seu aplicativo web.

**Seu aplicativo deve expor uma interface de usuário rica**

Como spas baseados em JavaScript, os aplicativos Blazor podem suportar o comportamento do cliente rico sem recargas de página. Esses aplicativos são mais responsivos aos usuários, buscando apenas os dados (ou HTML) necessários para responder a uma determinada interação do usuário. Projetados corretamente, os aplicativos Blazor do lado do servidor podem ser configurados para serem executados como aplicativos Blazor do lado do cliente com alterações mínimas assim que esse recurso for suportado.

**Sua equipe está mais confortável com o desenvolvimento .NET do que o desenvolvimento javaScript ou TypeScript**

Muitos desenvolvedores são mais produtivos com .NET e Razor do que com linguagens do lado do cliente, como JavaScript ou TypeScript. Como o lado do servidor do aplicativo já está sendo desenvolvido com o .NET, o uso do Blazor garante que todos os desenvolvedores .NET da equipe possam entender e potencialmente construir o comportamento da parte frontal do aplicativo.

## <a name="decision-table"></a>Tabela de decisão

A tabela de decisão a seguir resume alguns dos fatores básicos a serem considerados ao escolher entre um aplicativo web tradicional, um SPA ou um aplicativo Blazor.

| **Fator**                                           | **Aplicativo Web tradicional** | **Aplicativo de página única** | **Aplicativo Blazor**  |
| ---------------------------------------------------- | ----------------------- | --------------------------- | --------------- |
| É necessária a familiaridade da equipe com JavaScript/TypeScript | **Mínimo**             | **Obrigatório**                | **Mínimo**     |
| Suporte a navegadores sem scripts                   | **Suportado**           | **Não suportado**           | **Suportado**   |
| Comportamento mínimo do aplicativo do lado do cliente             | **Apropriado**         | **Exagero**                | **Viável**      |
| Requisitos avançados e complexos de interface do usuário            | **Limitado**             | **Apropriado**             | **Apropriado** |

>[!div class="step-by-step"]
>[Próximo](modern-web-applications-characteristics.md)
>[anterior](architectural-principles.md)
