---
title: Arquitetando aplicativos .NET nativos de nuvem para o Azure
description: Um guia para a criação de aplicativos nativos de nuvem que aproveitam contêineres, microservices e recursos sem servidor do Azure.
author: ardalis
ms.date: 05/13/2020
ms.openlocfilehash: b315f097b1584bd93f694c10f36ee7524d7e020a
ms.sourcegitcommit: ee5b798427f81237a3c23d1fd81fff7fdc21e8d3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/28/2020
ms.locfileid: "84144377"
---
# <a name="architecting-cloud-native-net-applications-for-azure"></a><span data-ttu-id="220cf-103">Arquitetando aplicativos .NET nativos de nuvem para o Azure</span><span class="sxs-lookup"><span data-stu-id="220cf-103">Architecting Cloud Native .NET Applications for Azure</span></span>

![imagem da capa](./media/cover.png)

<span data-ttu-id="220cf-105">**Edição v. 1.0**</span><span class="sxs-lookup"><span data-stu-id="220cf-105">**EDITION v.1.0**</span></span>

<span data-ttu-id="220cf-106">PUBLICADO POR</span><span class="sxs-lookup"><span data-stu-id="220cf-106">PUBLISHED BY</span></span>

<span data-ttu-id="220cf-107">Divisão de Desenvolvedores Microsoft, equipes dos produtos .NET e Visual Studio</span><span class="sxs-lookup"><span data-stu-id="220cf-107">Microsoft Developer Division, .NET, and Visual Studio product teams</span></span>

<span data-ttu-id="220cf-108">Uma divisão da Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="220cf-108">A division of Microsoft Corporation</span></span>

<span data-ttu-id="220cf-109">One Microsoft Way</span><span class="sxs-lookup"><span data-stu-id="220cf-109">One Microsoft Way</span></span>

<span data-ttu-id="220cf-110">Redmond, Washington 98052-6399</span><span class="sxs-lookup"><span data-stu-id="220cf-110">Redmond, Washington 98052-6399</span></span>

<span data-ttu-id="220cf-111">Copyright &copy; 2020 da Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="220cf-111">Copyright &copy; 2020 by Microsoft Corporation</span></span>

<span data-ttu-id="220cf-112">Todos os direitos reservados.</span><span class="sxs-lookup"><span data-stu-id="220cf-112">All rights reserved.</span></span> <span data-ttu-id="220cf-113">Nenhuma parte do conteúdo deste guia pode ser reproduzida ou transmitida de nenhuma forma nem por nenhum meio sem a permissão por escrito do publicador.</span><span class="sxs-lookup"><span data-stu-id="220cf-113">No part of the contents of this book may be reproduced or transmitted in any form or by any means without the written permission of the publisher.</span></span>

<span data-ttu-id="220cf-114">Este livro é fornecido “no estado em que se encontra” e expressa os pontos de vista e as opiniões do autor.</span><span class="sxs-lookup"><span data-stu-id="220cf-114">This book is provided "as-is" and expresses the author's views and opinions.</span></span> <span data-ttu-id="220cf-115">Os pontos de vista, as opiniões e as informações expressos neste livro, incluindo URLs e outras referências a sites da Internet, podem ser alteradas sem aviso prévio.</span><span class="sxs-lookup"><span data-stu-id="220cf-115">The views, opinions, and information expressed in this book, including URL and other Internet website references, may change without notice.</span></span>

<span data-ttu-id="220cf-116"> Alguns exemplos aqui representados são fornecidos somente para fins de ilustração e são fictícios.</span><span class="sxs-lookup"><span data-stu-id="220cf-116">Some examples depicted herein are provided for illustration only and are fictitious.</span></span> <span data-ttu-id="220cf-117">Nenhuma associação ou conexão real é intencional ou deve ser inferida.</span><span class="sxs-lookup"><span data-stu-id="220cf-117">No real association or connection is intended or should be inferred.</span></span>

<span data-ttu-id="220cf-118">A Microsoft e as marcas listadas em <https://www.microsoft.com> na página da Web "Marcas" são marcas comerciais do grupo de empresas Microsoft.</span><span class="sxs-lookup"><span data-stu-id="220cf-118">Microsoft and the trademarks listed at <https://www.microsoft.com> on the "Trademarks" webpage are trademarks of the Microsoft group of companies.</span></span>

<span data-ttu-id="220cf-119">Mac e macOS são marcas comerciais da Apple Inc.</span><span class="sxs-lookup"><span data-stu-id="220cf-119">Mac and macOS are trademarks of Apple Inc.</span></span>

<span data-ttu-id="220cf-120">O logotipo de redistribuição do Docker é uma marca registrada do Docker, Inc. usada pela permissão.</span><span class="sxs-lookup"><span data-stu-id="220cf-120">The Docker whale logo is a registered trademark of Docker, Inc. Used by permission.</span></span>

<span data-ttu-id="220cf-121">Todas as outras marcas e logotipos são propriedade de seus respectivos proprietários.</span><span class="sxs-lookup"><span data-stu-id="220cf-121">All other marks and logos are property of their respective owners.</span></span>

<span data-ttu-id="220cf-122">Autores:</span><span class="sxs-lookup"><span data-stu-id="220cf-122">Authors:</span></span>

> <span data-ttu-id="220cf-123">**Rob Vettor**, arquiteto de sistema de nuvem principal/arquiteto de IP- [thinkingincloudnative.com](https://thinkingincloudnative.com/about/), Microsoft</span><span class="sxs-lookup"><span data-stu-id="220cf-123">**Rob Vettor**, Principal Cloud System Architect/IP Architect - [thinkingincloudnative.com](https://thinkingincloudnative.com/about/), Microsoft</span></span>
>
> <span data-ttu-id="220cf-124">**Steve "ardalis" Smith**, arquiteto de software e instrutor- [Ardalis.com](https://ardalis.com)</span><span class="sxs-lookup"><span data-stu-id="220cf-124">**Steve "ardalis" Smith**, Software Architect and Trainer - [Ardalis.com](https://ardalis.com)</span></span>

<span data-ttu-id="220cf-125">Participantes e revisores:</span><span class="sxs-lookup"><span data-stu-id="220cf-125">Participants and Reviewers:</span></span>

> <span data-ttu-id="220cf-126">**Cesar de la Torre**, gerente de programa principal, equipe do .net, Microsoft</span><span class="sxs-lookup"><span data-stu-id="220cf-126">**Cesar De la Torre**, Principal Program Manager, .NET team, Microsoft</span></span>
>
> <span data-ttu-id="220cf-127">**Nish Anil**, gerente de programas sênior, equipe do .net, Microsoft</span><span class="sxs-lookup"><span data-stu-id="220cf-127">**Nish Anil**, Senior Program Manager, .NET team, Microsoft</span></span>
>
> <span data-ttu-id="220cf-128">**Jeremy Likness**, gerente de programas sênior, equipe do .net, Microsoft</span><span class="sxs-lookup"><span data-stu-id="220cf-128">**Jeremy Likness**, Senior Program Manager, .NET team, Microsoft</span></span>
>
> <span data-ttu-id="220cf-129">**Cecil Phillip**, defensora da nuvem sênior, Microsoft</span><span class="sxs-lookup"><span data-stu-id="220cf-129">**Cecil Phillip**, Senior Cloud Advocate, Microsoft</span></span>

<span data-ttu-id="220cf-130">Editores:</span><span class="sxs-lookup"><span data-stu-id="220cf-130">Editors:</span></span>

> <span data-ttu-id="220cf-131">**Maira Wenzel**, gerente de programas, equipe do .net, Microsoft</span><span class="sxs-lookup"><span data-stu-id="220cf-131">**Maira Wenzel**, Program Manager, .NET team, Microsoft</span></span>

## <a name="version"></a><span data-ttu-id="220cf-132">Versão</span><span class="sxs-lookup"><span data-stu-id="220cf-132">Version</span></span>

<span data-ttu-id="220cf-133">Este guia foi escrito para abranger a versão **3,1 do .NET Core** junto com muitas atualizações adicionais relacionadas à mesma "onda" de tecnologias (isto é, Azure e tecnologias de terceiros adicionais) que coincidem no tempo com a versão 3,1 do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="220cf-133">This guide has been written to cover **.NET Core 3.1** version along with many additional updates related to the same “wave” of technologies (that is, Azure and additional third-party technologies) coinciding in time with the .NET Core 3.1 release.</span></span>

## <a name="who-should-use-this-guide"></a><span data-ttu-id="220cf-134">Quem deve usar este guia</span><span class="sxs-lookup"><span data-stu-id="220cf-134">Who should use this guide</span></span>

<span data-ttu-id="220cf-135">O público-alvo deste guia é, principalmente, desenvolvedores, líderes de desenvolvimento e arquitetos interessados em aprender a criar aplicativos projetados para a nuvem.</span><span class="sxs-lookup"><span data-stu-id="220cf-135">The audience for this guide is mainly developers, development leads, and architects who are interested in learning how to build applications designed for the cloud.</span></span>

<span data-ttu-id="220cf-136">Um público-alvo secundário são responsáveis pelas decisões técnicas que planejam escolher se desejam criar seus aplicativos usando uma abordagem nativa de nuvem.</span><span class="sxs-lookup"><span data-stu-id="220cf-136">A secondary audience is technical decision-makers who plan to choose whether to build their applications using a cloud-native approach.</span></span>

## <a name="how-you-can-use-this-guide"></a><span data-ttu-id="220cf-137">Como você pode usar este guia</span><span class="sxs-lookup"><span data-stu-id="220cf-137">How you can use this guide</span></span>

<span data-ttu-id="220cf-138">Este guia começa definindo a nuvem nativa e introduzindo um aplicativo de referência criado usando princípios e tecnologias nativas de nuvem.</span><span class="sxs-lookup"><span data-stu-id="220cf-138">This guide begins by defining cloud native and introducing a reference application built using cloud-native principles and technologies.</span></span> <span data-ttu-id="220cf-139">Além desses dois primeiros capítulos, o restante do livro é dividido em capítulos específicos focados em tópicos comuns à maioria dos aplicativos nativos de nuvem.</span><span class="sxs-lookup"><span data-stu-id="220cf-139">Beyond these first two chapters, the rest of the book is broken up into specific chapters focused on topics common to most cloud-native applications.</span></span> <span data-ttu-id="220cf-140">Você pode ir para qualquer um desses capítulos para saber mais sobre abordagens nativas de nuvem para:</span><span class="sxs-lookup"><span data-stu-id="220cf-140">You can jump to any of these chapters to learn about cloud-native approaches to:</span></span>

- <span data-ttu-id="220cf-141">Dados e acesso a dados</span><span class="sxs-lookup"><span data-stu-id="220cf-141">Data and data access</span></span>
- <span data-ttu-id="220cf-142">Padrões de comunicação</span><span class="sxs-lookup"><span data-stu-id="220cf-142">Communication patterns</span></span>
- <span data-ttu-id="220cf-143">Dimensionamento e escalabilidade</span><span class="sxs-lookup"><span data-stu-id="220cf-143">Scaling and scalability</span></span>
- <span data-ttu-id="220cf-144">Resiliência do aplicativo</span><span class="sxs-lookup"><span data-stu-id="220cf-144">Application resiliency</span></span>
- <span data-ttu-id="220cf-145">Monitoramento e integridade</span><span class="sxs-lookup"><span data-stu-id="220cf-145">Monitoring and health</span></span>
- <span data-ttu-id="220cf-146">Identidade e segurança</span><span class="sxs-lookup"><span data-stu-id="220cf-146">Identity and security</span></span>
- <span data-ttu-id="220cf-147">DevOps</span><span class="sxs-lookup"><span data-stu-id="220cf-147">DevOps</span></span>

<span data-ttu-id="220cf-148">Este guia está disponível em formato PDF e online.</span><span class="sxs-lookup"><span data-stu-id="220cf-148">This guide is available both in PDF form and online.</span></span> <span data-ttu-id="220cf-149">Fique à vontade para encaminhar este documento ou links para sua versão online para sua equipe para ajudar a garantir uma compreensão comum desses tópicos.</span><span class="sxs-lookup"><span data-stu-id="220cf-149">Feel free to forward this document or links to its online version to your team to help ensure common understanding of these topics.</span></span> <span data-ttu-id="220cf-150">A maioria desses tópicos se beneficia de uma compreensão consistente dos princípios e padrões subjacentes, bem como das compensações envolvidas em decisões relacionadas a esses tópicos.</span><span class="sxs-lookup"><span data-stu-id="220cf-150">Most of these topics benefit from a consistent understanding of the underlying principles and patterns, as well as the trade-offs involved in decisions related to these topics.</span></span> <span data-ttu-id="220cf-151">Nosso objetivo com este documento é equipar equipes e seus líderes com as informações de que precisam para tomar decisões bem informadas sobre a arquitetura, o desenvolvimento e a hospedagem dos seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="220cf-151">Our goal with this document is to equip teams and their leaders with the information they need to make well-informed decisions for their applications' architecture, development, and hosting.</span></span>

## <a name="send-your-feedback"></a><span data-ttu-id="220cf-152">Envie seus comentários</span><span class="sxs-lookup"><span data-stu-id="220cf-152">Send your feedback</span></span>

<span data-ttu-id="220cf-153">Este livro e exemplos relacionados estão em constante evolução, para que seus comentários sejam bem-vindos!</span><span class="sxs-lookup"><span data-stu-id="220cf-153">This book and related samples are constantly evolving, so your feedback is welcomed!</span></span> <span data-ttu-id="220cf-154">Se você tiver comentários sobre como esse livro pode ser melhorado, use a seção de comentários na parte inferior de qualquer página criada com base nos [problemas do GitHub](https://github.com/dotnet/docs/issues).</span><span class="sxs-lookup"><span data-stu-id="220cf-154">If you have comments about how this book can be improved, use the feedback section at the bottom of any page built on [GitHub issues](https://github.com/dotnet/docs/issues).</span></span>

>[!div class="step-by-step"]
>[<span data-ttu-id="220cf-155">Avançar</span><span class="sxs-lookup"><span data-stu-id="220cf-155">Next</span></span>](introduction.md)
