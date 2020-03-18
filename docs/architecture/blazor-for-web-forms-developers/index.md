---
title: Blazor para desenvolvedores do ASP.NET Web Forms
description: Aprenda a criar aplicativos web full-stack com .NET usando Blazor e .NET Core de forma simples e familiar.
author: danroth27
ms.author: daroth
ms.date: 09/11/2019
ms.openlocfilehash: 394d11038b59f4cbe9e9955df43b6198eb5daaf8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73088124"
---
# <a name="blazor-for-aspnet-web-forms-developers"></a>Blazor para desenvolvedores do ASP.NET Web Forms

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

![Captura de tela que mostra a capa do e-book Serverless Apps.](./media/index/blazor-for-web-forms-developers-cover.png)

> DOWNLOAD disponível em: <https://aka.ms/blazor-ebook>

PUBLICADO POR

Divisão de Desenvolvedores Microsoft, equipes dos produtos .NET e Visual Studio

Uma divisão da Microsoft Corporation

One Microsoft Way

Redmond, Washington 98052-6399

Copyright © 2019, Microsoft Corporation

Todos os direitos reservados. Nenhuma parte do conteúdo deste guia pode ser reproduzida ou transmitida de nenhuma forma nem por nenhum meio sem a permissão por escrito do publicador.

Este livro é fornecido “no estado em que se encontra” e expressa os pontos de vista e as opiniões do autor. Os pontos de vista, as opiniões e as informações expressos neste guia, incluindo URLs e outras referências a sites da Internet, podem ser alteradas sem aviso prévio.

 Alguns exemplos aqui representados são fornecidos somente para fins de ilustração e são fictícios. Nenhuma associação ou conexão real é intencional ou deve ser inferida.

A Microsoft e as marcas listadas em <https://www.microsoft.com> na página da Web "Marcas" são marcas comerciais do grupo de empresas Microsoft.

Mac e macOS são marcas comerciais da Apple Inc.

Todas as outras marcas e logotipos são propriedade de seus respectivos proprietários.

Autores:

> **[Daniel Roth](https://github.com/danroth27)**, Gerente de Programa principal da Microsoft Corp.

> **[Jeff Fritz,](https://github.com/csharpfritz)** gerente sênior de programas da Microsoft Corp.

> **[Taylor Southwick,](https://github.com/twsouthwick)** Engenheiro sênior de Software, Microsoft Corp.

> **[Scott Addie](https://github.com/scottaddie)**, Desenvolvedor Sênior de Conteúdo, Microsoft Corp.

## <a name="introduction"></a>Introdução

O .NET há muito apoia o desenvolvimento de aplicativos web através de ASP.NET, um conjunto abrangente de frameworks e ferramentas para a construção de qualquer tipo de aplicativo web. ASP.NET tem sua própria linhagem de frameworks e tecnologias web começando todo o caminho de volta com as clássicas Páginas ativas do servidor (ASP). Frameworks como ASP.NET Formulários da Web, ASP.NET MVC, ASP.NET Páginas da Web e, mais recentemente, ASP.NET Core, fornecem uma maneira produtiva e poderosa de criar aplicativos web *renderizados por servidor,* onde o conteúdo de Interface do Usuário é gerado dinamicamente no servidor em resposta a solicitações HTTP. Cada ASP.NET estrutura atende a um público diferente e filosofia de construção de aplicativos. ASP.NET Web Forms enviados com a versão original do .NET Framework e habilitados para o desenvolvimento da Web usando muitos dos padrões familiares aos desenvolvedores de desktop, como controles de interface do usuário reutilizáveis com manuseio simples de eventos. No entanto, nenhuma das ofertas de ASP.NET fornece uma maneira de executar códigos executados no navegador do usuário. Para fazer isso é necessário escrever JavaScript e usar qualquer uma das muitas estruturas e ferramentas JavaScript que entraram e saíram da popularidade ao longo dos anos: jQuery, Knockout, Angular, React e assim por diante.

[Blazor](https://blazor.net) é uma nova estrutura web que muda o que é possível ao criar aplicativos web com .NET. Blazor é uma estrutura de UI web do lado do cliente baseada em C# em vez de JavaScript. Com o Blazor, você pode escrever sua lógica do lado do cliente e componentes de Interface do Usuário em C#, compilá-los em conjuntos normais .NET e executá-los diretamente no navegador usando um novo padrão web aberto chamado WebAssembly. Ou, alternativamente, o Blazor pode executar seus componentes de Interface do Usuário .NET no servidor e lidar com todas as interações de Interface do Usuário de forma fluida durante uma conexão em tempo real com o navegador. Quando emparelhado com o .NET em execução no servidor, o Blazor permite o desenvolvimento web de pilha cheia com o .NET. Embora o Blazor compartilhe muitas semelhanças com ASP.NET Web Forms, como ter um modelo de componente reutilizável e uma maneira simples de lidar com eventos de usuários, ele também se baseia nas bases do .NET Core para fornecer uma experiência moderna e de desenvolvimento web de alto desempenho.

Este livro apresenta ASP.NET desenvolvedores da Web Forms ao Blazor de uma forma familiar e conveniente. Introduz conceitos blazor em paralelo com conceitos análogos em ASP.NET Web Forms, ao mesmo tempo em que explica novos conceitos que podem ser menos familiares. Ele abrange uma ampla gama de tópicos e preocupações, incluindo autoria de componentes, roteamento, layout, configuração e segurança. E embora o conteúdo deste livro seja principalmente para permitir um novo desenvolvimento, ele também abrange diretrizes e estratégias para migrar ASP.NET Formulários web existentes para Blazor para quando você quiser modernizar um aplicativo existente.

## <a name="who-should-use-the-book"></a>Quem deve usar o livro

Este livro é para ASP.NET desenvolvedores da Web Forms que procuram uma introdução ao Blazor que se relacione com seus conhecimentos e habilidades existentes. Este livro pode ajudar a começar rapidamente em um novo projeto baseado em Blazor ou para ajudar a traçar um roteiro para modernizar um aplicativo de Formulários web ASP.NET existente.

## <a name="how-to-use-the-book"></a>Como usar o livro

A primeira parte deste livro abrange o que blazor é e o compara ao desenvolvimento de aplicativos web com ASP.NET Web Forms. O livro então abrange uma variedade de tópicos blazor, capítulo por capítulo, e relaciona cada conceito blazor ao conceito correspondente em ASP.NET Web Forms, ou explica completamente quaisquer conceitos completamente novos. O livro também se refere regularmente a um aplicativo de amostragem completo implementado em ASP.NET Web Forms e Blazor para demonstrar os recursos de Blazor e para fornecer um estudo de caso para migrar de ASP.NET Web Forms para Blazor. Você pode encontrar ambas as implementações do aplicativo de exemplo (ASP.NET web forms e versões Blazor) no [GitHub](https://github.com/dotnet-architecture/eshoponblazor).

## <a name="what-this-book-doesnt-cover"></a>O que este livro não cobre

Este livro é uma introdução a Blazor, não um guia de migração abrangente. Embora inclua orientações sobre como abordar a migração de um projeto de ASP.NET Web Forms para Blazor, ele não tenta cobrir todas as nuances e detalhes. Para obter orientações mais gerais sobre a migração de ASP.NET para ASP.NET Core, consulte a [orientação de migração](https://docs.microsoft.com/aspnet/core/migration/proper-to-2x/) na documentação do Núcleo ASP.NET.

### <a name="additional-resources"></a>Recursos adicionais

Você pode encontrar a página inicial <https://blazor.net>oficial do Blazor e a documentação em .

## <a name="send-your-feedback"></a>Envie seus comentários

Este livro e amostras relacionadas estão em constante evolução, por isso seu feedback é bem-vindo! Se você tiver comentários sobre como este livro pode ser melhorado, use a seção de feedback na parte inferior de qualquer página construída em [problemas do GitHub](https://github.com/dotnet/docs/issues).

>[!div class="step-by-step"]
>[Avançar](introduction.md)
