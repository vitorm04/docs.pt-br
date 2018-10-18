---
title: Diretrizes da biblioteca de software livre
description: Práticas recomendadas para que os desenvolvedores criem bibliotecas .NET de alta qualidade.
author: jamesnk
ms.author: mairaw
ms.date: 10/02/2018
ms.openlocfilehash: 50fb745f7eb65abcaca76cebaf9991c48f559e59
ms.sourcegitcommit: e42d09e5966dd9fd02847d3e7eeb4ec0877069f8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2018
ms.locfileid: "49374882"
---
# <a name="open-source-library-guidance"></a><span data-ttu-id="e049c-103">Diretrizes da biblioteca de software livre</span><span class="sxs-lookup"><span data-stu-id="e049c-103">Open-source library guidance</span></span>

<span data-ttu-id="e049c-104">Estas diretrizes fornecem recomendações para que os desenvolvedores criem bibliotecas .NET de alta qualidade.</span><span class="sxs-lookup"><span data-stu-id="e049c-104">This guidance provides recommendations for developers to create high-quality .NET libraries.</span></span> <span data-ttu-id="e049c-105">Esta documentação concentra-se no *quê* e no *porquê* ao criar uma biblioteca .NET, não no *como*.</span><span class="sxs-lookup"><span data-stu-id="e049c-105">This documentation focuses on the *what* and the *why* when building a .NET library, not the *how*.</span></span>

<span data-ttu-id="e049c-106">Aspectos das bibliotecas .NET de software livre de alta qualidade:</span><span class="sxs-lookup"><span data-stu-id="e049c-106">Aspects of high-quality open-source .NET libraries:</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="e049c-107">**Inclusivas** – as bibliotecas .NET de qualidade esforçam-se para dar suporte a várias plataformas e aplicativos.</span><span class="sxs-lookup"><span data-stu-id="e049c-107">**Inclusive** - Good .NET libraries strive to support many platforms and applications.</span></span>
> * <span data-ttu-id="e049c-108">**Estáveis** – as bibliotecas .NET de qualidade coexistem no ecossistema do .NET, em execução em aplicativos criados com várias bibliotecas.</span><span class="sxs-lookup"><span data-stu-id="e049c-108">**Stable** - Good .NET libraries coexist in the .NET ecosystem, running in applications built with many libraries.</span></span>
> * <span data-ttu-id="e049c-109">**Projetadas para evoluir** – as bibliotecas .NET devem melhorar e evoluir ao longo do tempo, continuando a dar suporte aos usuários existentes.</span><span class="sxs-lookup"><span data-stu-id="e049c-109">**Designed to evolve** - .NET libraries should improve and evolve over time, while supporting existing users.</span></span>
> * <span data-ttu-id="e049c-110">**Depuráveis** – as bibliotecas .NET devem usar as ferramentas mais recentes para criar uma ótima experiência de depuração para os usuários.</span><span class="sxs-lookup"><span data-stu-id="e049c-110">**Debuggable** - .NET libraries should use the latest tools to create a great debugging experience for users.</span></span>
> * <span data-ttu-id="e049c-111">**Confiáveis** – as bibliotecas .NET têm a confiança dos desenvolvedores por publicarem no NuGet usando práticas recomendadas de segurança.</span><span class="sxs-lookup"><span data-stu-id="e049c-111">**Trusted** - .NET libraries have developers' trust by publishing to NuGet using security best practices.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="e049c-112">Introdução</span><span class="sxs-lookup"><span data-stu-id="e049c-112">Get Started</span></span>](./get-started.md)

## <a name="recommendations"></a><span data-ttu-id="e049c-113">Recomendações</span><span class="sxs-lookup"><span data-stu-id="e049c-113">Recommendations</span></span>

<span data-ttu-id="e049c-114">Com cada artigo, há uma lista de recomendações para a biblioteca .NET usando **Fazer**, **Considerar**, **Evitar** e **Não fazer**.</span><span class="sxs-lookup"><span data-stu-id="e049c-114">With each article, there is a list of recommendations for your .NET library using **Do**, **Consider**, **Avoid**, and **Do not**.</span></span> <span data-ttu-id="e049c-115">O texto de cada recomendação indica a intensidade em que ela deve ser seguida.</span><span class="sxs-lookup"><span data-stu-id="e049c-115">The wording of each recommendation indicates how strongly it should be followed.</span></span>

<span data-ttu-id="e049c-116">Uma recomendação **Fazer** é aquela que quase sempre deve ser seguida:</span><span class="sxs-lookup"><span data-stu-id="e049c-116">A **Do** recommendation is one that should almost always be followed:</span></span>

<span data-ttu-id="e049c-117">**✔️ FAZER** a distribuição de sua biblioteca usando um pacote NuGet.</span><span class="sxs-lookup"><span data-stu-id="e049c-117">**✔️ DO** distribute your library using a NuGet package.</span></span>

<span data-ttu-id="e049c-118">Por outro lado, as recomendações **Considerar** geralmente devem ser seguidas, mas há exceções à regra legítimas e você não precisará se preocupar caso não possa seguir as diretrizes:</span><span class="sxs-lookup"><span data-stu-id="e049c-118">On the other hand, **Consider** recommendations should generally be followed, but there are legitimate exceptions to the rule and you shouldn't feel bad about not following the guidance:</span></span>

<span data-ttu-id="e049c-119">**✔️ CONSIDERAR** o uso do [SemVer 2.0.0](https://semver.org/) para criar a versão do seu pacote NuGet.</span><span class="sxs-lookup"><span data-stu-id="e049c-119">**✔️ CONSIDER** using [SemVer 2.0.0](https://semver.org/) to version your NuGet package.</span></span>

<span data-ttu-id="e049c-120">As recomendações **Evitar** são coisas que geralmente não são ideais, mas há casos em que quebrar a regra, às vezes, faz sentido:</span><span class="sxs-lookup"><span data-stu-id="e049c-120">**Avoid** recommendations are things that are generally not a good idea, but breaking the rule sometimes makes sense:</span></span>

<span data-ttu-id="e049c-121">**❌ EVITAR** referências do pacote NuGet que demandam uma versão exata.</span><span class="sxs-lookup"><span data-stu-id="e049c-121">**❌ AVOID** NuGet package references that demand an exact version.</span></span>

<span data-ttu-id="e049c-122">E, finalmente, **Não fazer** indica algo que você quase nunca deve fazer:</span><span class="sxs-lookup"><span data-stu-id="e049c-122">And finally, **do not** indicates something you should almost never do:</span></span>

<span data-ttu-id="e049c-123">**❌ NÃO FAZER** a publicação de versões de nome forte e sem nome forte da biblioteca.</span><span class="sxs-lookup"><span data-stu-id="e049c-123">**❌ DO NOT** publish strong-named and non-strong-named versions of your library.</span></span> <span data-ttu-id="e049c-124">Por exemplo, `Contoso.Api` e `Contoso.Api.StrongNamed`.</span><span class="sxs-lookup"><span data-stu-id="e049c-124">For example, `Contoso.Api` and `Contoso.Api.StrongNamed`.</span></span>

>[!div class="step-by-step"]
[<span data-ttu-id="e049c-125">Avançar</span><span class="sxs-lookup"><span data-stu-id="e049c-125">Next</span></span>](./get-started.md)
