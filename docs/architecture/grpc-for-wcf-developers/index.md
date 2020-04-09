---
title: ASP.NET Core gRPC para Desenvolvedores WCF - gRPC para Desenvolvedores WCF
description: Introdução à construção de serviços gRPC em ASP.NET Core 3.0 para desenvolvedores WCF
ms.date: 09/02/2019
ms.openlocfilehash: 175dfbf1880a0937615543c248fba3bed0e25c23
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2020
ms.locfileid: "80988954"
---
# <a name="aspnet-core-grpc-for-wcf-developers"></a><span data-ttu-id="765d4-103">ASP.NET Core gRPC para desenvolvedores do WCF</span><span class="sxs-lookup"><span data-stu-id="765d4-103">ASP.NET Core gRPC for WCF Developers</span></span>

![imagem da capa](./media/cover.png)

<span data-ttu-id="765d4-105">PUBLICADO POR</span><span class="sxs-lookup"><span data-stu-id="765d4-105">PUBLISHED BY</span></span>

<span data-ttu-id="765d4-106">Divisão de Desenvolvedores Microsoft, equipes dos produtos .NET e Visual Studio</span><span class="sxs-lookup"><span data-stu-id="765d4-106">Microsoft Developer Division, .NET, and Visual Studio product teams</span></span>

<span data-ttu-id="765d4-107">Uma divisão da Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="765d4-107">A division of Microsoft Corporation</span></span>

<span data-ttu-id="765d4-108">One Microsoft Way</span><span class="sxs-lookup"><span data-stu-id="765d4-108">One Microsoft Way</span></span>

<span data-ttu-id="765d4-109">Redmond, Washington 98052-6399</span><span class="sxs-lookup"><span data-stu-id="765d4-109">Redmond, Washington 98052-6399</span></span>

<span data-ttu-id="765d4-110">Copyright © 2019, Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="765d4-110">Copyright © 2019 by Microsoft Corporation</span></span>

<span data-ttu-id="765d4-111">Todos os direitos reservados.</span><span class="sxs-lookup"><span data-stu-id="765d4-111">All rights reserved.</span></span> <span data-ttu-id="765d4-112">Nenhuma parte do conteúdo deste guia pode ser reproduzida ou transmitida de nenhuma forma nem por nenhum meio sem a permissão por escrito do publicador.</span><span class="sxs-lookup"><span data-stu-id="765d4-112">No part of the contents of this book may be reproduced or transmitted in any form or by any means without the written permission of the publisher.</span></span>

<span data-ttu-id="765d4-113">Este livro é fornecido “no estado em que se encontra” e expressa os pontos de vista e as opiniões do autor.</span><span class="sxs-lookup"><span data-stu-id="765d4-113">This book is provided "as-is" and expresses the author's views and opinions.</span></span> <span data-ttu-id="765d4-114">Os pontos de vista, as opiniões e as informações expressos neste guia, incluindo URLs e outras referências a sites da Internet, podem ser alteradas sem aviso prévio.</span><span class="sxs-lookup"><span data-stu-id="765d4-114">The views, opinions and information expressed in this book, including URL and other Internet website references, may change without notice.</span></span>

<span data-ttu-id="765d4-115"> Alguns exemplos aqui representados são fornecidos somente para fins de ilustração e são fictícios.</span><span class="sxs-lookup"><span data-stu-id="765d4-115">Some examples depicted herein are provided for illustration only and are fictitious.</span></span> <span data-ttu-id="765d4-116">Nenhuma associação ou conexão real é intencional ou deve ser inferida.</span><span class="sxs-lookup"><span data-stu-id="765d4-116">No real association or connection is intended or should be inferred.</span></span>

<span data-ttu-id="765d4-117">A Microsoft e as marcas listadas em https://www.microsoft.com na página da Web "Marcas" são marcas comerciais do grupo de empresas Microsoft.</span><span class="sxs-lookup"><span data-stu-id="765d4-117">Microsoft and the trademarks listed at https://www.microsoft.com on the "Trademarks" webpage are trademarks of the Microsoft group of companies.</span></span>

<span data-ttu-id="765d4-118">O logotipo da baleia Docker é uma marca registrada da Docker, Inc. Usada por permissão.</span><span class="sxs-lookup"><span data-stu-id="765d4-118">The Docker whale logo is a registered trademark of Docker, Inc. Used by permission.</span></span>

<span data-ttu-id="765d4-119">Todas as outras marcas e logotipos são propriedade de seus respectivos proprietários.</span><span class="sxs-lookup"><span data-stu-id="765d4-119">All other marks and logos are property of their respective owners.</span></span>

<span data-ttu-id="765d4-120">Autores:</span><span class="sxs-lookup"><span data-stu-id="765d4-120">Authors:</span></span>

> <span data-ttu-id="765d4-121">**Mark Rendle** - Diretor Técnico - [Recode Visual](https://visualrecode.com)</span><span class="sxs-lookup"><span data-stu-id="765d4-121">**Mark Rendle** - Chief Technical Officer - [Visual Recode](https://visualrecode.com)</span></span>
>
> <span data-ttu-id="765d4-122">**Miranda Steiner** - Autor Técnico</span><span class="sxs-lookup"><span data-stu-id="765d4-122">**Miranda Steiner** - Technical Author</span></span>

<span data-ttu-id="765d4-123">Editor:</span><span class="sxs-lookup"><span data-stu-id="765d4-123">Editor:</span></span>

> <span data-ttu-id="765d4-124">**Maira Wenzel** - Sr. Content Developer - Microsoft</span><span class="sxs-lookup"><span data-stu-id="765d4-124">**Maira Wenzel** - Sr. Content Developer - Microsoft</span></span>

## <a name="introduction"></a><span data-ttu-id="765d4-125">Introdução</span><span class="sxs-lookup"><span data-stu-id="765d4-125">Introduction</span></span>

<span data-ttu-id="765d4-126">gRPC é uma estrutura moderna para a construção de serviços em rede e aplicativos distribuídos.</span><span class="sxs-lookup"><span data-stu-id="765d4-126">gRPC is a modern framework for building networked services and distributed applications.</span></span> <span data-ttu-id="765d4-127">Imagine o desempenho das ligações NetTCP da Windows Communication Foundation (WCF), combinadas com a interoperabilidade multiplataforma do SOAP.</span><span class="sxs-lookup"><span data-stu-id="765d4-127">Imagine the performance of Windows Communication Foundation (WCF) NetTCP bindings, combined with the cross-platform interoperability of SOAP.</span></span> <span data-ttu-id="765d4-128">O gRPC é baseado em HTTP/2 e no protocolo de codificação de mensagens Protobuf para fornecer comunicação de alto desempenho e baixa largura de banda entre aplicativos e serviços.</span><span class="sxs-lookup"><span data-stu-id="765d4-128">gRPC builds on HTTP/2 and the Protobuf message-encoding protocol to provide high performance, low-bandwidth communication between applications and services.</span></span> <span data-ttu-id="765d4-129">Ele suporta a geração de código de servidor e cliente nas linguagens e plataformas de programação mais populares, incluindo .NET, Java, Python, Node.js, Go e C++.</span><span class="sxs-lookup"><span data-stu-id="765d4-129">It supports server and client code generation across most popular programming languages and platforms, including .NET, Java, Python, Node.js, Go, and C++.</span></span> <span data-ttu-id="765d4-130">Com o suporte de primeira classe para o gRPC em ASP.NET Core 3.0, ao lado das ferramentas e bibliotecas gRPC existentes para .NET 4.x, é uma excelente alternativa ao WCF para equipes de desenvolvimento que buscam adotar o .NET Core em suas organizações.</span><span class="sxs-lookup"><span data-stu-id="765d4-130">With the first-class support for gRPC in ASP.NET Core 3.0, alongside the existing gRPC tools and libraries for .NET 4.x, it's an excellent alternative to WCF for development teams looking to adopt .NET Core in their organizations.</span></span>

## <a name="who-should-use-this-guide"></a><span data-ttu-id="765d4-131">Quem deve usar este guia</span><span class="sxs-lookup"><span data-stu-id="765d4-131">Who should use this guide</span></span>

<span data-ttu-id="765d4-132">Este guia foi escrito para desenvolvedores que trabalham em .NET Framework ou .NET Core que já usaram o WCF, e que estão buscando migrar seus aplicativos para um ambiente RPC moderno para versões .NET Core 3.0 e posteriores.</span><span class="sxs-lookup"><span data-stu-id="765d4-132">This guide was written for developers working in .NET Framework or .NET Core who have previously used WCF, and who are seeking to migrate their applications to a modern RPC environment for .NET Core 3.0 and later versions.</span></span> <span data-ttu-id="765d4-133">De forma mais geral, se você estiver atualizando ou considerando atualizar para .NET Core 3.0, e quiser usar as ferramentas gRPC incorporadas, este guia também é útil.</span><span class="sxs-lookup"><span data-stu-id="765d4-133">More generally, if you are upgrading, or considering upgrading, to .NET Core 3.0, and you want to use the built-in gRPC tools, this guide is also useful.</span></span>

## <a name="how-you-can-use-this-guide"></a><span data-ttu-id="765d4-134">Como você pode usar este guia</span><span class="sxs-lookup"><span data-stu-id="765d4-134">How you can use this guide</span></span>

<span data-ttu-id="765d4-135">Esta é uma breve introdução à construção de serviços gRPC em ASP.NET Núcleo 3.0, com referência particular ao WCF como uma plataforma análoga.</span><span class="sxs-lookup"><span data-stu-id="765d4-135">This is a short introduction to building gRPC Services in ASP.NET Core 3.0, with particular reference to WCF as an analogous platform.</span></span> <span data-ttu-id="765d4-136">Ele explica os princípios do gRPC, relacionando cada conceito às características equivalentes do WCF, e oferece orientação para migrar uma aplicação wcf existente para gRPC.</span><span class="sxs-lookup"><span data-stu-id="765d4-136">It explains the principles of gRPC, relating each concept to the equivalent features of WCF, and offers guidance for migrating an existing WCF application to gRPC.</span></span> <span data-ttu-id="765d4-137">Também é útil para desenvolvedores que têm experiência com WCF e estão procurando aprender gRPC para construir novos serviços.</span><span class="sxs-lookup"><span data-stu-id="765d4-137">It's also useful for developers who have experience with WCF and are looking to learn gRPC to build new services.</span></span> <span data-ttu-id="765d4-138">Você pode usar os aplicativos de amostra como um modelo ou referência para seus próprios projetos, e você está livre para copiar e reutilizar códigos do livro ou suas amostras.</span><span class="sxs-lookup"><span data-stu-id="765d4-138">You can use the sample applications as a template or reference for your own projects, and you are free to copy and reuse code from the book or its samples.</span></span>

<span data-ttu-id="765d4-139">Fique à vontade para encaminhar este guia para sua equipe para ajudar a garantir um entendimento comum dessas considerações e oportunidades.</span><span class="sxs-lookup"><span data-stu-id="765d4-139">Feel free to forward this guide to your team to help ensure a common understanding of these considerations and opportunities.</span></span> <span data-ttu-id="765d4-140">Ter todos trabalhando a partir de um conjunto comum de termos e princípios subjacentes ajuda a garantir a aplicação consistente de padrões e práticas arquitetônicas.</span><span class="sxs-lookup"><span data-stu-id="765d4-140">Having everybody working from a common set of terms and underlying principles helps ensure consistent application of architectural patterns and practices.</span></span>

## <a name="references"></a><span data-ttu-id="765d4-141">Referências</span><span class="sxs-lookup"><span data-stu-id="765d4-141">References</span></span>

- <span data-ttu-id="765d4-142">**site gRPC**
  <https://grpc.io></span><span class="sxs-lookup"><span data-stu-id="765d4-142">**gRPC website**
<https://grpc.io></span></span>
- <span data-ttu-id="765d4-143">**Escolhendo entre o .NET Core e o .NET Framework para aplicativos de servidor**
  <https://docs.microsoft.com/dotnet/standard/choosing-core-framework-server></span><span class="sxs-lookup"><span data-stu-id="765d4-143">**Choosing between .NET Core and .NET Framework for server apps**
<https://docs.microsoft.com/dotnet/standard/choosing-core-framework-server></span></span>

>[!div class="step-by-step"]
>[<span data-ttu-id="765d4-144">Avançar</span><span class="sxs-lookup"><span data-stu-id="765d4-144">Next</span></span>](introduction.md)
