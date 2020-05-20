---
title: Modernizando os aplicativos da área de trabalho no Windows 10 com o .NET Core 3,1
description: Saiba como modernizar os aplicativos de área de trabalho existentes com o .NET Core 3,1
ms.date: 05/12/2020
ms.openlocfilehash: 5861f806a9158ef761c47bc23e51327d4e2d0480
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83423232"
---
# <a name="modernizing-desktop-apps-on-windows-10-with-net-core-31"></a>Modernizando os aplicativos da área de trabalho no Windows 10 com o .NET Core 3,1

![Captura de tela que mostra a capa do livro eletrônico de aplicativos de área de trabalho Modern.](./media/modernizing-existing-desktop-apps-ebook-cover.png)

PUBLICADO POR

Divisão de Desenvolvedores Microsoft, equipes dos produtos .NET e Visual Studio

Uma divisão da Microsoft Corporation

One Microsoft Way

Redmond, Washington 98052-6399

Copyright © 2020 da Microsoft Corporation

Todos os direitos reservados. Nenhuma parte do conteúdo deste guia pode ser reproduzida ou transmitida de nenhuma forma nem por nenhum meio sem a permissão por escrito do publicador.

Este livro é fornecido “no estado em que se encontra” e expressa os pontos de vista e as opiniões do autor. Os pontos de vista, as opiniões e as informações expressos neste guia, incluindo URLs e outras referências a sites da Internet, podem ser alteradas sem aviso prévio.

 Alguns exemplos aqui representados são fornecidos somente para fins de ilustração e são fictícios. Nenhuma associação ou conexão real é intencional ou deve ser inferida.

A Microsoft e as marcas listadas em <https://www.microsoft.com> na página da Web "Marcas" são marcas comerciais do grupo de empresas Microsoft.

Mac e macOS são marcas comerciais da Apple Inc.

Todas as outras marcas e logotipos são propriedade de seus respectivos proprietários.

Coautores:

> **Olia Gavrysh**, gerente de programas, equipe do .net, Microsoft

> **Miguel Anjo Castejón Dominguez**, arquiteto de inovação, Kabel

Participantes e revisores:

> **Maira Wenzel**, gerente de programas sênior, equipe do .net, Microsoft

> **Andy de Gorge**, desenvolvedor de conteúdo sênior, equipe de docs .net, Microsoft

> **Miguel Ramos**, gerente de programas sênior, equipe da plataforma de desenvolvedor do Windows, Microsoft

> **Adam Braden**, gerente de programa principal, equipe da plataforma de desenvolvedor do Windows, Microsoft

> **Ricardo Minguez Pablos**, gerente de programas sênior, equipe do Azure IOT, Microsoft

> **Nish Anil**, gerente de programas sênior, equipe do .net, Microsoft

> **Beth Massi**, gerente de marketing de produtos sênior, Microsoft

> **Scott Hunter**, gerente de programa do diretor de parceiros, equipe do .net, Microsoft

> **Marta Fuentes Lara**, Kabel

> **Raúl Fernández de nicaraguense**, Kabel

> **Antonio Manuel Fernández cantos**, Kabel

## <a name="introduction"></a>Introdução

Este livro trata de estratégias que você pode adotar para mover seus aplicativos de área de trabalho existentes por meio do caminho de modernização e incorporar os recursos mais recentes de tempo de execução, idioma e plataforma. Você descobrirá que não há nenhuma receita exclusiva, pois cada aplicativo é diferente e, portanto, seus requisitos e preferências. A boa notícia é que há abordagens comuns que você pode aplicar para adicionar novos recursos e funcionalidades aos seus aplicativos. Alguns deles nem mesmo exigirão grandes modificações do seu código. Neste livro, revelaremos como todos esses recursos funcionam nos bastidores e explicaremos a mecânica de suas implementações. Além disso, você encontrará alguns cenários comuns para modernizar os aplicativos de área de trabalho existentes mostrados em detalhes, para que você possa encontrar inspiração para a evolução de seus projetos.

A abordagem da Microsoft para modernizar os aplicativos existentes é oferecer a você a flexibilidade para criar seu próprio caminho personalizado. Todas as estratégias de modernização descritas neste livro são, na maior parte, independentes. Você pode escolher aqueles que são relevantes para seu aplicativo e ignorar outros que não são importantes para você. Em outras palavras, você pode misturar e combinar as estratégias para atender melhor às suas necessidades de aplicativo.

## <a name="who-should-use-the-book"></a>Quem deve usar o livro

Nós escrevemos este livro para desenvolvedores e arquitetos de soluções que desejam modernizar os Windows Forms existentes e os aplicativos de área de trabalho do WPF para aproveitar os benefícios do .NET Core e do Windows 10.

Você também poderá encontrar esse livro útil se for um tomador de decisões técnicas, como um arquiteto corporativo ou um líder de desenvolvimento ou diretor que queira uma visão geral dos benefícios da atualização dos aplicativos de área de trabalho existentes.

## <a name="how-to-use-the-book"></a>Como usar o livro

Este livro aborda o "porquê" – por que você pode querer modernizar seus aplicativos existentes e os benefícios específicos obtidos usando o NET Core 3,1 e MSIX para modernizar seus aplicativos de desktop. O conteúdo do livro foi projetado para arquitetos e tomadores de decisões técnicas que desejam uma visão geral, mas que não precisam se concentrar na implementação e nos detalhes técnicos e passo a passo.

Ao longo dos diferentes capítulos, trechos de código de exemplo de implementação e capturas de tela são fornecidos, com o capítulo 5 dedicado a apresentar um processo completo de migração para aplicativos de exemplo.

## <a name="what-this-book-doesnt-cover"></a>O que este livro não abrange

Este livro aborda um subconjunto específico de cenários que se concentram em cenários de comparação de precisão e deslocamento, descrevendo a maneira de aproveitar os benefícios da modernização sem o esforço de reescrever código.

Este livro não é sobre o desenvolvimento de aplicativos modernos com o .NET Core do zero ou sobre a introdução ao Windows Forms e ao WPF. Ele se concentra em como você pode atualizar os aplicativos de área de trabalho existentes com as tecnologias mais recentes para o desenvolvimento de desktops.

## <a name="samples-used-in-this-book"></a>Exemplos usados neste livro

Para destacar as etapas necessárias para executar uma modernização, vamos usar um aplicativo de exemplo chamado `eShopModernizing` . Esse aplicativo tem dois tipos, Windows Forms e WPF, e mostraremos um processo passo a passo sobre como executar a modernização em ambos os núcleos para o .NET Core.

Além disso, no repositório GitHub para este livro, você encontrará os resultados do processo, com o qual você pode consultar se decidir seguir o tutorial passo a passo.

## <a name="send-your-feedback"></a>Envie seus comentários

Este livro e exemplos relacionados estão em constante evolução, para que seus comentários sejam bem-vindos! Se você tiver comentários sobre como esse livro pode ser melhorado, use a seção de comentários na parte inferior de qualquer página criada com base nos [problemas do GitHub](https://github.com/dotnet/docs/issues).

>[!div class="step-by-step"]
>[Avançar](why-modern-applications.md)
