---
title: Introdução à criação de bibliotecas do .NET de alta qualidade
description: Introdução à criação de bibliotecas do .NET.
author: jamesnk
ms.author: mairaw
ms.date: 10/02/2018
ms.openlocfilehash: 05466de1469fc765570b8250301e8404cd5df173
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53145719"
---
# <a name="get-started"></a><span data-ttu-id="b2c3d-103">Introdução</span><span class="sxs-lookup"><span data-stu-id="b2c3d-103">Get started</span></span>

## <a name="cross-platform-targetingcross-platform-targetingmd"></a>[<span data-ttu-id="b2c3d-104">Direcionamento de plataforma cruzada</span><span class="sxs-lookup"><span data-stu-id="b2c3d-104">Cross-platform targeting</span></span>](./cross-platform-targeting.md)

<span data-ttu-id="b2c3d-105">Como usar o .NET Standard e multiplataforma para criar bibliotecas de multiplataforma.</span><span class="sxs-lookup"><span data-stu-id="b2c3d-105">How to use .NET Standard and multi-targeting to create cross-platform libraries.</span></span> <span data-ttu-id="b2c3d-106">O .NET é executado em muitos locais e boas bibliotecas do .NET devem buscar dar suporte a tantas plataformas e desenvolvedores quanto possível.</span><span class="sxs-lookup"><span data-stu-id="b2c3d-106">.NET runs in many places, and good .NET libraries should strive to support as many platforms and developers as possible.</span></span>

## <a name="strong-namingstrong-namingmd"></a>[<span data-ttu-id="b2c3d-107">Nomenclatura forte</span><span class="sxs-lookup"><span data-stu-id="b2c3d-107">Strong naming</span></span>](./strong-naming.md)

<span data-ttu-id="b2c3d-108">Saiba mais sobre o nome forte e suas vantagens e desvantagens.</span><span class="sxs-lookup"><span data-stu-id="b2c3d-108">Learn about strong naming and its advantages and disadvantages.</span></span> <span data-ttu-id="b2c3d-109">Dar um nome forte a uma biblioteca .NET permite que a maioria dos desenvolvedores use-a e é uma prática recomendada.</span><span class="sxs-lookup"><span data-stu-id="b2c3d-109">Strong naming a .NET library allows the most developers to use it and is a recommended best practice.</span></span>

## <a name="nuget-and-open-source-librariesnugetmd"></a>[<span data-ttu-id="b2c3d-110">Bibliotecas do NuGet e de software livre</span><span class="sxs-lookup"><span data-stu-id="b2c3d-110">NuGet and open-source libraries</span></span>](./nuget.md)

<span data-ttu-id="b2c3d-111">A melhor maneira de criar pacotes do NuGet para bibliotecas do .NET de código-fonte aberto, incluindo metadados recomendados para todos os pacotes publicamente publicados em NuGet.org.</span><span class="sxs-lookup"><span data-stu-id="b2c3d-111">The best way to create NuGet packages for open-source .NET libraries, including recommended metadata for all packages published publicly on NuGet.org.</span></span>

### <a name="dependenciesdependenciesmd"></a>[<span data-ttu-id="b2c3d-112">Dependências</span><span class="sxs-lookup"><span data-stu-id="b2c3d-112">Dependencies</span></span>](./dependencies.md)

<span data-ttu-id="b2c3d-113">O NuGet torna fácil usar pacotes existentes ao criar uma biblioteca do .NET.</span><span class="sxs-lookup"><span data-stu-id="b2c3d-113">NuGet makes it easy to use existing packages when building a .NET library.</span></span> <span data-ttu-id="b2c3d-114">Saiba mais sobre as origens comuns de atrito de dependências do NuGet e como evitá-las.</span><span class="sxs-lookup"><span data-stu-id="b2c3d-114">Learn about NuGet dependencies' common sources of friction and how to avoid them.</span></span>

### <a name="sourcelinksourcelinkmd"></a>[<span data-ttu-id="b2c3d-115">SourceLink</span><span class="sxs-lookup"><span data-stu-id="b2c3d-115">SourceLink</span></span>](./sourcelink.md)

<span data-ttu-id="b2c3d-116">O SourceLink é uma ótima ferramenta que permite que os usuários da sua biblioteca do .NET intervir em seu código-fonte durante a depuração.</span><span class="sxs-lookup"><span data-stu-id="b2c3d-116">SourceLink is a great tool that allows users of your .NET library to step into its source code while debugging.</span></span> <span data-ttu-id="b2c3d-117">Este artigo é uma visão geral do que é SourceLink e por que você deve usá-lo.</span><span class="sxs-lookup"><span data-stu-id="b2c3d-117">This article is an overview of what SourceLink is and why you should use it.</span></span>

### <a name="publishingpublish-nuget-packagemd"></a>[<span data-ttu-id="b2c3d-118">Publicação</span><span class="sxs-lookup"><span data-stu-id="b2c3d-118">Publishing</span></span>](./publish-nuget-package.md)

<span data-ttu-id="b2c3d-119">Embora o NuGet.org seja o repositório mais amplamente conhecido e usado, há muitos locais para publicar pacotes do NuGet.</span><span class="sxs-lookup"><span data-stu-id="b2c3d-119">While NuGet.org is the most widely known and used repository, there are many places to publish NuGet packages.</span></span> <span data-ttu-id="b2c3d-120">Saiba mais sobre os diferentes repositórios de pacote do NuGet disponíveis e práticas recomendadas de segurança para a publicação de uma biblioteca do .NET.</span><span class="sxs-lookup"><span data-stu-id="b2c3d-120">Learn about the different NuGet package repositories available, and security best practices for publishing a .NET library.</span></span>

## <a name="versioningversioningmd"></a>[<span data-ttu-id="b2c3d-121">Controle de versão</span><span class="sxs-lookup"><span data-stu-id="b2c3d-121">Versioning</span></span>](./versioning.md)

<span data-ttu-id="b2c3d-122">Boas bibliotecas do .NET evoluem ao longo do tempo, adicionando recursos, corrigindo bugs e melhorando o desempenho em versões posteriores.</span><span class="sxs-lookup"><span data-stu-id="b2c3d-122">Good .NET libraries evolve over time, adding features, fixing bugs, and improving performance in later releases.</span></span> <span data-ttu-id="b2c3d-123">Saiba mais sobre os vários números de versão e como comunicar alterações significativas para os desenvolvedores.</span><span class="sxs-lookup"><span data-stu-id="b2c3d-123">Learn about the various version numbers and how to communicate breaking changes to developers.</span></span>

### <a name="breaking-changesbreaking-changesmd"></a>[<span data-ttu-id="b2c3d-124">Alterações significativas</span><span class="sxs-lookup"><span data-stu-id="b2c3d-124">Breaking changes</span></span>](./breaking-changes.md)

<span data-ttu-id="b2c3d-125">É importante que uma biblioteca .NET encontre um equilíbrio entre a estabilidade para usuários existentes e a inovação para o futuro.</span><span class="sxs-lookup"><span data-stu-id="b2c3d-125">It's important for a .NET library to find a balance between stability for existing users and innovation for the future.</span></span> <span data-ttu-id="b2c3d-126">Saiba mais sobre os diferentes tipos de alterações da falha e estratégias para adição de novos recursos, ao mesmo tempo mantendo a compatibilidade com versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="b2c3d-126">Learn about the different kinds of breaking changes and strategies for adding new features while maintaining backwards compatibility.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="b2c3d-127">[Anterior](index.md)
>[Próximo](cross-platform-targeting.md)</span><span class="sxs-lookup"><span data-stu-id="b2c3d-127">[Previous](index.md)
[Next](cross-platform-targeting.md)</span></span>