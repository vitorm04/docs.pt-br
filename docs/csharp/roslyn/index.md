---
title: Como usar o SDK do Compilador .NET | Guia do C#
description: "Explore as APIs do Roslyn para criar diagnóstico e correções de código automáticos"
keywords: .NET, .NET Core, C#, Roslyn,
ms.date: 06/25/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: abed9e00-2ddc-468e-9cca-d033bd6a7e36
redirect_url: /dotnet/csharp/index
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: b227d67fd5431da328e1686fd9afc6a3b9db035e
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---

# <a name="-using-the-net-compiler-sdk"></a><span data-ttu-id="65abc-104">🔧 Usando o SDK do compilador .NET</span><span class="sxs-lookup"><span data-stu-id="65abc-104">🔧 Using the .NET Compiler SDK</span></span>

> <span data-ttu-id="65abc-105">**Observação**</span><span class="sxs-lookup"><span data-stu-id="65abc-105">**Note**</span></span>
> 
> <span data-ttu-id="65abc-106">Este tópico ainda não foi criado!</span><span class="sxs-lookup"><span data-stu-id="65abc-106">This topic hasn’t been written yet!</span></span> 
>
> <span data-ttu-id="65abc-107">Agradecemos a sua contribuição para ajudar a moldar o escopo e a abordagem.</span><span class="sxs-lookup"><span data-stu-id="65abc-107">We welcome your input to help shape the scope and approach.</span></span> <span data-ttu-id="65abc-108">Você pode acompanhar o status e fornecer comentários sobre esse [problema](https://github.com/dotnet/docs/issues/972) no GitHub.</span><span class="sxs-lookup"><span data-stu-id="65abc-108">You can track the status and provide input on this [issue](https://github.com/dotnet/docs/issues/972) at GitHub.</span></span>
> 
> <span data-ttu-id="65abc-109">Se você quiser examinar os primeiros rascunhos e esboços deste tópico, deixe uma nota com suas informações de contato no problema.</span><span class="sxs-lookup"><span data-stu-id="65abc-109">If you would like to review early drafts and outlines of this topic, please leave a note with your contact information in the issue.</span></span>
>
> <span data-ttu-id="65abc-110">Saiba mais sobre como você pode contribuir com o [GitHub](https://github.com/dotnet/docs/blob/master/CONTRIBUTING.md).</span><span class="sxs-lookup"><span data-stu-id="65abc-110">Learn more about how you can contribute on [GitHub](https://github.com/dotnet/docs/blob/master/CONTRIBUTING.md).</span></span>
>

<span data-ttu-id="65abc-111">Este é um metatópico de uma seção inteira.</span><span class="sxs-lookup"><span data-stu-id="65abc-111">This is a meta-topic for an entire section.</span></span> <span data-ttu-id="65abc-112">As áreas que precisam ser abordadas aqui incluem:</span><span class="sxs-lookup"><span data-stu-id="65abc-112">Areas that need to be covered here include:</span></span> 
* <span data-ttu-id="65abc-113">Guia de Introdução</span><span class="sxs-lookup"><span data-stu-id="65abc-113">Getting Started</span></span>
* <span data-ttu-id="65abc-114">Exemplos e tutoriais</span><span class="sxs-lookup"><span data-stu-id="65abc-114">Samples and tutorials</span></span>
* <span data-ttu-id="65abc-115">conteúdo conceitual</span><span class="sxs-lookup"><span data-stu-id="65abc-115">conceptual content</span></span>
* <span data-ttu-id="65abc-116">modelo geral das APIs</span><span class="sxs-lookup"><span data-stu-id="65abc-116">overall model of the APIs</span></span>
* <span data-ttu-id="65abc-117">links para exemplos no repositório [roslyn-analyzers](http://github.com/dotnet/roslyn-analyzers)</span><span class="sxs-lookup"><span data-stu-id="65abc-117">links to samples on the [roslyn-analyzers](http://github.com/dotnet/roslyn-analyzers) repository</span></span>
* <span data-ttu-id="65abc-118">links para outro conteúdo de referência</span><span class="sxs-lookup"><span data-stu-id="65abc-118">links to other reference content</span></span>

