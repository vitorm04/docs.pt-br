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
# <a name="modernizing-desktop-apps-on-windows-10-with-net-core-31"></a><span data-ttu-id="015f1-103">Modernizando os aplicativos da área de trabalho no Windows 10 com o .NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="015f1-103">Modernizing Desktop Apps on Windows 10 with .NET Core 3.1</span></span>

![Captura de tela que mostra a capa do livro eletrônico de aplicativos de área de trabalho Modern.](./media/modernizing-existing-desktop-apps-ebook-cover.png)

<span data-ttu-id="015f1-105">PUBLICADO POR</span><span class="sxs-lookup"><span data-stu-id="015f1-105">PUBLISHED BY</span></span>

<span data-ttu-id="015f1-106">Divisão de Desenvolvedores Microsoft, equipes dos produtos .NET e Visual Studio</span><span class="sxs-lookup"><span data-stu-id="015f1-106">Microsoft Developer Division, .NET, and Visual Studio product teams</span></span>

<span data-ttu-id="015f1-107">Uma divisão da Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="015f1-107">A division of Microsoft Corporation</span></span>

<span data-ttu-id="015f1-108">One Microsoft Way</span><span class="sxs-lookup"><span data-stu-id="015f1-108">One Microsoft Way</span></span>

<span data-ttu-id="015f1-109">Redmond, Washington 98052-6399</span><span class="sxs-lookup"><span data-stu-id="015f1-109">Redmond, Washington 98052-6399</span></span>

<span data-ttu-id="015f1-110">Copyright © 2020 da Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="015f1-110">Copyright © 2020 by Microsoft Corporation</span></span>

<span data-ttu-id="015f1-111">Todos os direitos reservados.</span><span class="sxs-lookup"><span data-stu-id="015f1-111">All rights reserved.</span></span> <span data-ttu-id="015f1-112">Nenhuma parte do conteúdo deste guia pode ser reproduzida ou transmitida de nenhuma forma nem por nenhum meio sem a permissão por escrito do publicador.</span><span class="sxs-lookup"><span data-stu-id="015f1-112">No part of the contents of this book may be reproduced or transmitted in any form or by any means without the written permission of the publisher.</span></span>

<span data-ttu-id="015f1-113">Este livro é fornecido “no estado em que se encontra” e expressa os pontos de vista e as opiniões do autor.</span><span class="sxs-lookup"><span data-stu-id="015f1-113">This book is provided "as-is" and expresses the author's views and opinions.</span></span> <span data-ttu-id="015f1-114">Os pontos de vista, as opiniões e as informações expressos neste guia, incluindo URLs e outras referências a sites da Internet, podem ser alteradas sem aviso prévio.</span><span class="sxs-lookup"><span data-stu-id="015f1-114">The views, opinions and information expressed in this book, including URL and other Internet website references, may change without notice.</span></span>

<span data-ttu-id="015f1-115"> Alguns exemplos aqui representados são fornecidos somente para fins de ilustração e são fictícios.</span><span class="sxs-lookup"><span data-stu-id="015f1-115">Some examples depicted herein are provided for illustration only and are fictitious.</span></span> <span data-ttu-id="015f1-116">Nenhuma associação ou conexão real é intencional ou deve ser inferida.</span><span class="sxs-lookup"><span data-stu-id="015f1-116">No real association or connection is intended or should be inferred.</span></span>

<span data-ttu-id="015f1-117">A Microsoft e as marcas listadas em <https://www.microsoft.com> na página da Web "Marcas" são marcas comerciais do grupo de empresas Microsoft.</span><span class="sxs-lookup"><span data-stu-id="015f1-117">Microsoft and the trademarks listed at <https://www.microsoft.com> on the "Trademarks" webpage are trademarks of the Microsoft group of companies.</span></span>

<span data-ttu-id="015f1-118">Mac e macOS são marcas comerciais da Apple Inc.</span><span class="sxs-lookup"><span data-stu-id="015f1-118">Mac and macOS are trademarks of Apple Inc.</span></span>

<span data-ttu-id="015f1-119">Todas as outras marcas e logotipos são propriedade de seus respectivos proprietários.</span><span class="sxs-lookup"><span data-stu-id="015f1-119">All other marks and logos are property of their respective owners.</span></span>

<span data-ttu-id="015f1-120">Coautores:</span><span class="sxs-lookup"><span data-stu-id="015f1-120">Co-Authors:</span></span>

> <span data-ttu-id="015f1-121">**Olia Gavrysh**, gerente de programas, equipe do .net, Microsoft</span><span class="sxs-lookup"><span data-stu-id="015f1-121">**Olia Gavrysh**, Program Manager, .NET team, Microsoft</span></span>

> <span data-ttu-id="015f1-122">**Miguel Anjo Castejón Dominguez**, arquiteto de inovação, Kabel</span><span class="sxs-lookup"><span data-stu-id="015f1-122">**Miguel Angel Castejón Dominguez**, Innovation Architect, Kabel</span></span>

<span data-ttu-id="015f1-123">Participantes e revisores:</span><span class="sxs-lookup"><span data-stu-id="015f1-123">Participants and reviewers:</span></span>

> <span data-ttu-id="015f1-124">**Maira Wenzel**, gerente de programas sênior, equipe do .net, Microsoft</span><span class="sxs-lookup"><span data-stu-id="015f1-124">**Maira Wenzel**, Senior Program Manager, .NET team, Microsoft</span></span>

> <span data-ttu-id="015f1-125">**Andy de Gorge**, desenvolvedor de conteúdo sênior, equipe de docs .net, Microsoft</span><span class="sxs-lookup"><span data-stu-id="015f1-125">**Andy De Gorge**, Senior Content Developer, .NET docs team, Microsoft</span></span>

> <span data-ttu-id="015f1-126">**Miguel Ramos**, gerente de programas sênior, equipe da plataforma de desenvolvedor do Windows, Microsoft</span><span class="sxs-lookup"><span data-stu-id="015f1-126">**Miguel Ramos**, Senior Program Manager, Windows Developer Platform team, Microsoft</span></span>

> <span data-ttu-id="015f1-127">**Adam Braden**, gerente de programa principal, equipe da plataforma de desenvolvedor do Windows, Microsoft</span><span class="sxs-lookup"><span data-stu-id="015f1-127">**Adam Braden**, Principal Program Manager, Windows Developer Platform team, Microsoft</span></span>

> <span data-ttu-id="015f1-128">**Ricardo Minguez Pablos**, gerente de programas sênior, equipe do Azure IOT, Microsoft</span><span class="sxs-lookup"><span data-stu-id="015f1-128">**Ricardo Minguez Pablos**, Senior Program Manager, Azure IoT team, Microsoft</span></span>

> <span data-ttu-id="015f1-129">**Nish Anil**, gerente de programas sênior, equipe do .net, Microsoft</span><span class="sxs-lookup"><span data-stu-id="015f1-129">**Nish Anil**, Senior Program Manager, .NET team, Microsoft</span></span>

> <span data-ttu-id="015f1-130">**Beth Massi**, gerente de marketing de produtos sênior, Microsoft</span><span class="sxs-lookup"><span data-stu-id="015f1-130">**Beth Massi**, Senior Product Marketing Manager, Microsoft</span></span>

> <span data-ttu-id="015f1-131">**Scott Hunter**, gerente de programa do diretor de parceiros, equipe do .net, Microsoft</span><span class="sxs-lookup"><span data-stu-id="015f1-131">**Scott Hunter**, Partner Director Program Manager, .NET team, Microsoft</span></span>

> <span data-ttu-id="015f1-132">**Marta Fuentes Lara**, Kabel</span><span class="sxs-lookup"><span data-stu-id="015f1-132">**Marta Fuentes Lara**, Kabel</span></span>

> <span data-ttu-id="015f1-133">**Raúl Fernández de nicaraguense**, Kabel</span><span class="sxs-lookup"><span data-stu-id="015f1-133">**Raúl Fernández de Córdoba**, Kabel</span></span>

> <span data-ttu-id="015f1-134">**Antonio Manuel Fernández cantos**, Kabel</span><span class="sxs-lookup"><span data-stu-id="015f1-134">**Antonio Manuel Fernández Cantos**, Kabel</span></span>

## <a name="introduction"></a><span data-ttu-id="015f1-135">Introdução</span><span class="sxs-lookup"><span data-stu-id="015f1-135">Introduction</span></span>

<span data-ttu-id="015f1-136">Este livro trata de estratégias que você pode adotar para mover seus aplicativos de área de trabalho existentes por meio do caminho de modernização e incorporar os recursos mais recentes de tempo de execução, idioma e plataforma.</span><span class="sxs-lookup"><span data-stu-id="015f1-136">This book is about strategies you can adopt to move your existing desktop applications through the path of modernization and incorporate the latest runtime, language, and platform features.</span></span> <span data-ttu-id="015f1-137">Você descobrirá que não há nenhuma receita exclusiva, pois cada aplicativo é diferente e, portanto, seus requisitos e preferências.</span><span class="sxs-lookup"><span data-stu-id="015f1-137">You'll discover that there's no unique recipe as each application is different, and so are your requirements and preferences.</span></span> <span data-ttu-id="015f1-138">A boa notícia é que há abordagens comuns que você pode aplicar para adicionar novos recursos e funcionalidades aos seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="015f1-138">The good news is that there are common approaches you can apply to add new features and capabilities to your applications.</span></span> <span data-ttu-id="015f1-139">Alguns deles nem mesmo exigirão grandes modificações do seu código.</span><span class="sxs-lookup"><span data-stu-id="015f1-139">Some of them won't even require major modifications of your code.</span></span> <span data-ttu-id="015f1-140">Neste livro, revelaremos como todos esses recursos funcionam nos bastidores e explicaremos a mecânica de suas implementações.</span><span class="sxs-lookup"><span data-stu-id="015f1-140">In this book, we'll reveal how all those features work behind the scenes and explain the mechanics of their implementations.</span></span> <span data-ttu-id="015f1-141">Além disso, você encontrará alguns cenários comuns para modernizar os aplicativos de área de trabalho existentes mostrados em detalhes, para que você possa encontrar inspiração para a evolução de seus projetos.</span><span class="sxs-lookup"><span data-stu-id="015f1-141">Moreover, you'll find some common scenarios for modernizing existing desktop applications shown in detail so you can find inspiration for evolving your projects.</span></span>

<span data-ttu-id="015f1-142">A abordagem da Microsoft para modernizar os aplicativos existentes é oferecer a você a flexibilidade para criar seu próprio caminho personalizado.</span><span class="sxs-lookup"><span data-stu-id="015f1-142">Microsoft's approach to modernizing existing applications is to give you the flexibility to create your own customized path.</span></span> <span data-ttu-id="015f1-143">Todas as estratégias de modernização descritas neste livro são, na maior parte, independentes.</span><span class="sxs-lookup"><span data-stu-id="015f1-143">All the modernization strategies described in this book are mostly independent.</span></span> <span data-ttu-id="015f1-144">Você pode escolher aqueles que são relevantes para seu aplicativo e ignorar outros que não são importantes para você.</span><span class="sxs-lookup"><span data-stu-id="015f1-144">You can choose ones that are relevant for your application and skip others that aren't important for you.</span></span> <span data-ttu-id="015f1-145">Em outras palavras, você pode misturar e combinar as estratégias para atender melhor às suas necessidades de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="015f1-145">In other words, you can mix and match the strategies to best address your application needs.</span></span>

## <a name="who-should-use-the-book"></a><span data-ttu-id="015f1-146">Quem deve usar o livro</span><span class="sxs-lookup"><span data-stu-id="015f1-146">Who should use the book</span></span>

<span data-ttu-id="015f1-147">Nós escrevemos este livro para desenvolvedores e arquitetos de soluções que desejam modernizar os Windows Forms existentes e os aplicativos de área de trabalho do WPF para aproveitar os benefícios do .NET Core e do Windows 10.</span><span class="sxs-lookup"><span data-stu-id="015f1-147">We wrote this book for developers and solution architects who want to modernize existing Windows Forms and WPF desktop applications to leverage the benefits of .NET Core and Windows 10.</span></span>

<span data-ttu-id="015f1-148">Você também poderá encontrar esse livro útil se for um tomador de decisões técnicas, como um arquiteto corporativo ou um líder de desenvolvimento ou diretor que queira uma visão geral dos benefícios da atualização dos aplicativos de área de trabalho existentes.</span><span class="sxs-lookup"><span data-stu-id="015f1-148">You might also find this book useful if you're a technical decision maker, such as an enterprise architect or a development lead or director who wants an overview of the benefits of updating existing desktop applications.</span></span>

## <a name="how-to-use-the-book"></a><span data-ttu-id="015f1-149">Como usar o livro</span><span class="sxs-lookup"><span data-stu-id="015f1-149">How to use the book</span></span>

<span data-ttu-id="015f1-150">Este livro aborda o "porquê" – por que você pode querer modernizar seus aplicativos existentes e os benefícios específicos obtidos usando o NET Core 3,1 e MSIX para modernizar seus aplicativos de desktop.</span><span class="sxs-lookup"><span data-stu-id="015f1-150">This book addresses the "why"—why you might want to modernize your existing applications, and the specific benefits you get from using NET Core 3.1 and MSIX to modernize your desktop apps.</span></span> <span data-ttu-id="015f1-151">O conteúdo do livro foi projetado para arquitetos e tomadores de decisões técnicas que desejam uma visão geral, mas que não precisam se concentrar na implementação e nos detalhes técnicos e passo a passo.</span><span class="sxs-lookup"><span data-stu-id="015f1-151">The content of the book is designed for architects and technical decision makers who want an overview, but who don't need to focus on implementation and technical, step-by-step details.</span></span>

<span data-ttu-id="015f1-152">Ao longo dos diferentes capítulos, trechos de código de exemplo de implementação e capturas de tela são fornecidos, com o capítulo 5 dedicado a apresentar um processo completo de migração para aplicativos de exemplo.</span><span class="sxs-lookup"><span data-stu-id="015f1-152">Along the different chapters, sample implementation code snippets and screenshots are provided, with chapter 5 devoted to showcase a complete migration process for sample applications.</span></span>

## <a name="what-this-book-doesnt-cover"></a><span data-ttu-id="015f1-153">O que este livro não abrange</span><span class="sxs-lookup"><span data-stu-id="015f1-153">What this book doesn't cover</span></span>

<span data-ttu-id="015f1-154">Este livro aborda um subconjunto específico de cenários que se concentram em cenários de comparação de precisão e deslocamento, descrevendo a maneira de aproveitar os benefícios da modernização sem o esforço de reescrever código.</span><span class="sxs-lookup"><span data-stu-id="015f1-154">This book covers a specific subset of scenarios that are focused on lift-and-shift scenarios, outlining the way to gain the benefits of modernizing without the effort of rewriting code.</span></span>

<span data-ttu-id="015f1-155">Este livro não é sobre o desenvolvimento de aplicativos modernos com o .NET Core do zero ou sobre a introdução ao Windows Forms e ao WPF.</span><span class="sxs-lookup"><span data-stu-id="015f1-155">This book isn't about developing modern applications with .NET Core from scratch or about getting started with Windows Forms and WPF.</span></span> <span data-ttu-id="015f1-156">Ele se concentra em como você pode atualizar os aplicativos de área de trabalho existentes com as tecnologias mais recentes para o desenvolvimento de desktops.</span><span class="sxs-lookup"><span data-stu-id="015f1-156">It focuses on how you can update existing desktop applications with the latest technologies for desktop development.</span></span>

## <a name="samples-used-in-this-book"></a><span data-ttu-id="015f1-157">Exemplos usados neste livro</span><span class="sxs-lookup"><span data-stu-id="015f1-157">Samples used in this book</span></span>

<span data-ttu-id="015f1-158">Para destacar as etapas necessárias para executar uma modernização, vamos usar um aplicativo de exemplo chamado `eShopModernizing` .</span><span class="sxs-lookup"><span data-stu-id="015f1-158">To highlight the necessary steps to perform a modernization, we'll be using a sample application called `eShopModernizing`.</span></span> <span data-ttu-id="015f1-159">Esse aplicativo tem dois tipos, Windows Forms e WPF, e mostraremos um processo passo a passo sobre como executar a modernização em ambos os núcleos para o .NET Core.</span><span class="sxs-lookup"><span data-stu-id="015f1-159">This application has two flavors, Windows Forms and WPF, and we'll show a step-by-step process on how to perform the modernization on both of them to .NET Core.</span></span>

<span data-ttu-id="015f1-160">Além disso, no repositório GitHub para este livro, você encontrará os resultados do processo, com o qual você pode consultar se decidir seguir o tutorial passo a passo.</span><span class="sxs-lookup"><span data-stu-id="015f1-160">Also, on the GitHub repository for this book, you'll find the results of the process, which you can consult with if you decide to follow the step-by-step tutorial.</span></span>

## <a name="send-your-feedback"></a><span data-ttu-id="015f1-161">Envie seus comentários</span><span class="sxs-lookup"><span data-stu-id="015f1-161">Send your feedback</span></span>

<span data-ttu-id="015f1-162">Este livro e exemplos relacionados estão em constante evolução, para que seus comentários sejam bem-vindos!</span><span class="sxs-lookup"><span data-stu-id="015f1-162">This book and related samples are constantly evolving, so your feedback is welcomed!</span></span> <span data-ttu-id="015f1-163">Se você tiver comentários sobre como esse livro pode ser melhorado, use a seção de comentários na parte inferior de qualquer página criada com base nos [problemas do GitHub](https://github.com/dotnet/docs/issues).</span><span class="sxs-lookup"><span data-stu-id="015f1-163">If you have comments about how this book can be improved, use the feedback section at the bottom of any page built on [GitHub issues](https://github.com/dotnet/docs/issues).</span></span>

>[!div class="step-by-step"]
>[<span data-ttu-id="015f1-164">Avançar</span><span class="sxs-lookup"><span data-stu-id="015f1-164">Next</span></span>](why-modern-applications.md)
