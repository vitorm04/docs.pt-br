---
title: ASP.NET Core gRPC para desenvolvedores do WCF – gRPC para desenvolvedores do WCF
description: A SER ESCRITO
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: dc39fc96e7154fb50acd0b65a58586b3fa12ab50
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71696915"
---
# <a name="aspnet-core-grpc-for-wcf-developers"></a><span data-ttu-id="09236-103">ASP.NET Core gRPC para desenvolvedores do WCF</span><span class="sxs-lookup"><span data-stu-id="09236-103">ASP.NET Core gRPC for WCF Developers</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

![imagem da capa](./media/cover.png)

<span data-ttu-id="09236-105">PUBLICADO POR</span><span class="sxs-lookup"><span data-stu-id="09236-105">PUBLISHED BY</span></span>

<span data-ttu-id="09236-106">Divisão de Desenvolvedores Microsoft, equipes dos produtos .NET e Visual Studio</span><span class="sxs-lookup"><span data-stu-id="09236-106">Microsoft Developer Division, .NET, and Visual Studio product teams</span></span>

<span data-ttu-id="09236-107">Uma divisão da Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="09236-107">A division of Microsoft Corporation</span></span>

<span data-ttu-id="09236-108">One Microsoft Way</span><span class="sxs-lookup"><span data-stu-id="09236-108">One Microsoft Way</span></span>

<span data-ttu-id="09236-109">Redmond, Washington 98052-6399</span><span class="sxs-lookup"><span data-stu-id="09236-109">Redmond, Washington 98052-6399</span></span>

<span data-ttu-id="09236-110">Copyright © 2019, Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="09236-110">Copyright © 2019 by Microsoft Corporation</span></span>

<span data-ttu-id="09236-111">Todos os direitos reservados.</span><span class="sxs-lookup"><span data-stu-id="09236-111">All rights reserved.</span></span> <span data-ttu-id="09236-112">Nenhuma parte do conteúdo deste guia pode ser reproduzida ou transmitida de nenhuma forma nem por nenhum meio sem a permissão por escrito do publicador.</span><span class="sxs-lookup"><span data-stu-id="09236-112">No part of the contents of this book may be reproduced or transmitted in any form or by any means without the written permission of the publisher.</span></span>

<span data-ttu-id="09236-113">Este manual é fornecido "no estado em que se encontra" e expressa os pontos de vista e as opiniões do autor.</span><span class="sxs-lookup"><span data-stu-id="09236-113">This book is provided “as-is” and expresses the author’s views and opinions.</span></span> <span data-ttu-id="09236-114">Os pontos de vista, as opiniões e as informações expressos neste guia, incluindo URLs e outras referências a sites da Internet, podem ser alteradas sem aviso prévio.</span><span class="sxs-lookup"><span data-stu-id="09236-114">The views, opinions and information expressed in this book, including URL and other Internet website references, may change without notice.</span></span>

<span data-ttu-id="09236-115">Alguns exemplos aqui representados são fornecidos apenas para ilustração e são fictícios.</span><span class="sxs-lookup"><span data-stu-id="09236-115">Some examples depicted herein are provided for illustration only and are fictitious.</span></span> <span data-ttu-id="09236-116">Nenhuma associação ou conexão real é intencional ou deve ser deduzida.</span><span class="sxs-lookup"><span data-stu-id="09236-116">No real association or connection is intended or should be inferred.</span></span>

<span data-ttu-id="09236-117">A Microsoft e as marcas comerciais listadas em https://www.microsoft.com na página da Web “Marcas comerciais” são marcas comerciais do grupo de empresas da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="09236-117">Microsoft and the trademarks listed at https://www.microsoft.com on the “Trademarks” webpage are trademarks of the Microsoft group of companies.</span></span>

<span data-ttu-id="09236-118">O logotipo de baleia do Docker é uma marca registrada da Docker, Inc. usado mediante permissão.</span><span class="sxs-lookup"><span data-stu-id="09236-118">The Docker whale logo is a registered trademark of Docker, Inc. Used by permission.</span></span>

<span data-ttu-id="09236-119">Todas as outras marcas e logotipos são propriedade de seus respectivos proprietários.</span><span class="sxs-lookup"><span data-stu-id="09236-119">All other marks and logos are property of their respective owners.</span></span>

<span data-ttu-id="09236-120">Autor:</span><span class="sxs-lookup"><span data-stu-id="09236-120">Author:</span></span>

> <span data-ttu-id="09236-121">**Mark** diretor técnico de Rendle – [recódigo Visual](https://visualrecode.com)</span><span class="sxs-lookup"><span data-stu-id="09236-121">**Mark Rendle** - Chief Technical Officer - [Visual Recode](https://visualrecode.com)</span></span>
>
> <span data-ttu-id="09236-122">**Miranda Steiner** – autor técnico</span><span class="sxs-lookup"><span data-stu-id="09236-122">**Miranda Steiner** - Technical Author</span></span>

<span data-ttu-id="09236-123">Editores:</span><span class="sxs-lookup"><span data-stu-id="09236-123">Editors:</span></span>

> <span data-ttu-id="09236-124">**Maira Wenzel** -Sr Content Developer-Microsoft</span><span class="sxs-lookup"><span data-stu-id="09236-124">**Maira Wenzel** - Sr Content Developer - Microsoft</span></span>

## <a name="introduction"></a><span data-ttu-id="09236-125">Introdução</span><span class="sxs-lookup"><span data-stu-id="09236-125">Introduction</span></span>

<span data-ttu-id="09236-126">TODO</span><span class="sxs-lookup"><span data-stu-id="09236-126">TODO</span></span>

## <a name="purpose"></a><span data-ttu-id="09236-127">Finalidade</span><span class="sxs-lookup"><span data-stu-id="09236-127">Purpose</span></span>

<span data-ttu-id="09236-128">TODO</span><span class="sxs-lookup"><span data-stu-id="09236-128">TODO</span></span>

## <a name="who-should-use-this-guide"></a><span data-ttu-id="09236-129">Quem deve usar este guia</span><span class="sxs-lookup"><span data-stu-id="09236-129">Who should use this guide</span></span>

<span data-ttu-id="09236-130">**ATUALIZAR ESTE**</span><span class="sxs-lookup"><span data-stu-id="09236-130">**UPDATE THIS**</span></span>

<span data-ttu-id="09236-131">O público-alvo deste guia é desenvolvedores do WCF, líderes de desenvolvimento e arquitetos interessados em migrar soluções WCF no .NET 4 e versões anteriores para ASP.NET Core 3,0 usando os serviços gRPCs.</span><span class="sxs-lookup"><span data-stu-id="09236-131">The audience for this guide is WCF developers, development leads, and architects who are interested in migrating WCF solutions on .NET 4 and earlier to ASP.NET Core 3.0 using gRPC services.</span></span>

## <a name="how-you-can-use-this-guide"></a><span data-ttu-id="09236-132">Como você pode usar este guia</span><span class="sxs-lookup"><span data-stu-id="09236-132">How you can use this guide</span></span>

<span data-ttu-id="09236-133">**ATUALIZAR ESTE**</span><span class="sxs-lookup"><span data-stu-id="09236-133">**UPDATE THIS**</span></span>

<span data-ttu-id="09236-134">Esta é uma breve introdução à criação de serviços gRPCs no ASP.NET Core 3,0 com referência específica ao WCF como uma plataforma análoga.</span><span class="sxs-lookup"><span data-stu-id="09236-134">This is a short introduction to building gRPC Services in ASP.NET Core 3.0 with particular reference to WCF as an analogous platform.</span></span> <span data-ttu-id="09236-135">Ele explica os princípios de gRPC, relacionando cada conceito aos recursos equivalentes do WCF e oferece orientação para migrar um aplicativo WCF existente para o gRPC.</span><span class="sxs-lookup"><span data-stu-id="09236-135">It explains the principles of gRPC, relating each concept to the equivalent features of WCF, and offers guidance for migrating an existing WCF application to gRPC.</span></span> <span data-ttu-id="09236-136">Ele também é útil para desenvolvedores que têm experiência com o WCF e procuram aprender a gRPC para criar novos serviços.</span><span class="sxs-lookup"><span data-stu-id="09236-136">It is also useful for developers who have experience of WCF and are looking to learn gRPC to build new services.</span></span> <span data-ttu-id="09236-137">O aplicativo de exemplo pode ser usado como um modelo ou referência para seus próprios projetos, e você pode copiar e reutilizar o código do livro ou de seus exemplos.</span><span class="sxs-lookup"><span data-stu-id="09236-137">The sample application can be used as a template or reference for your own projects, and you are free to copy and reuse code from the book or its samples.</span></span>

<span data-ttu-id="09236-138">Fique à vontade para encaminhar este guia para sua equipe para ajudar a garantir um entendimento comum dessas considerações e oportunidades.</span><span class="sxs-lookup"><span data-stu-id="09236-138">Feel free to forward this guide to your team to help ensure a common understanding of these considerations and opportunities.</span></span> <span data-ttu-id="09236-139">Quando todas as pessoas trabalham com um conjunto comum de terminologia e de princípios subjacentes é mais fácil garantir a aplicação consistente dos padrões e das práticas de arquitetura.</span><span class="sxs-lookup"><span data-stu-id="09236-139">Having everybody working from a common set of terminology and underlying principles helps ensure consistent application of architectural patterns and practices.</span></span>

## <a name="references"></a><span data-ttu-id="09236-140">Referências</span><span class="sxs-lookup"><span data-stu-id="09236-140">References</span></span>

- <span data-ttu-id="09236-141">**site da gRPC**</span><span class="sxs-lookup"><span data-stu-id="09236-141">**gRPC web site**</span></span>  
  <https://grpc.io>
- <span data-ttu-id="09236-142">**Escolhendo entre o .NET Core e .NET Framework para aplicativos de servidor**</span><span class="sxs-lookup"><span data-stu-id="09236-142">**Choosing between .NET Core and .NET Framework for server apps**</span></span>  
  <https://docs.microsoft.com/dotnet/standard/choosing-core-framework-server>

>[!div class="step-by-step"]
>[<span data-ttu-id="09236-143">Avançar</span><span class="sxs-lookup"><span data-stu-id="09236-143">Next</span></span>](introduction.md)
