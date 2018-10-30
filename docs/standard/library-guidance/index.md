---
title: Diretrizes da biblioteca de software livre
description: Práticas recomendadas para que os desenvolvedores criem bibliotecas .NET de alta qualidade.
author: jamesnk
ms.author: mairaw
ms.date: 10/17/2018
ms.openlocfilehash: ca95cb5ba1ebf27464397b7850ac02aabded1a5b
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50188619"
---
# <a name="open-source-library-guidance"></a><span data-ttu-id="cc3c0-103">Diretrizes da biblioteca de software livre</span><span class="sxs-lookup"><span data-stu-id="cc3c0-103">Open-source library guidance</span></span>

<span data-ttu-id="cc3c0-104">Estas diretrizes fornecem recomendações para que os desenvolvedores criem bibliotecas .NET de alta qualidade.</span><span class="sxs-lookup"><span data-stu-id="cc3c0-104">This guidance provides recommendations for developers to create high-quality .NET libraries.</span></span> <span data-ttu-id="cc3c0-105">Esta documentação concentra-se no *quê* e no *porquê* ao criar uma biblioteca .NET, não no *como*.</span><span class="sxs-lookup"><span data-stu-id="cc3c0-105">This documentation focuses on the *what* and the *why* when building a .NET library, not the *how*.</span></span>

<span data-ttu-id="cc3c0-106">Aspectos das bibliotecas .NET de software livre de alta qualidade:</span><span class="sxs-lookup"><span data-stu-id="cc3c0-106">Aspects of high-quality open-source .NET libraries:</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="cc3c0-107">**Inclusivas** – as bibliotecas .NET de qualidade se esforçam para dar suporte a várias plataformas, linguagens de programação e aplicativos.</span><span class="sxs-lookup"><span data-stu-id="cc3c0-107">**Inclusive** - Good .NET libraries strive to support many platforms, programming languages, and applications.</span></span>
> * <span data-ttu-id="cc3c0-108">**Estáveis** – as bibliotecas .NET de qualidade coexistem no ecossistema do .NET, em execução em aplicativos criados com várias bibliotecas.</span><span class="sxs-lookup"><span data-stu-id="cc3c0-108">**Stable** - Good .NET libraries coexist in the .NET ecosystem, running in applications built with many libraries.</span></span>
> * <span data-ttu-id="cc3c0-109">**Projetadas para evoluir** – as bibliotecas .NET devem melhorar e evoluir ao longo do tempo, continuando a dar suporte aos usuários existentes.</span><span class="sxs-lookup"><span data-stu-id="cc3c0-109">**Designed to evolve** - .NET libraries should improve and evolve over time, while supporting existing users.</span></span>
> * <span data-ttu-id="cc3c0-110">**Depuráveis** – as bibliotecas .NET devem usar as ferramentas mais recentes para criar uma ótima experiência de depuração para os usuários.</span><span class="sxs-lookup"><span data-stu-id="cc3c0-110">**Debuggable** - .NET libraries should use the latest tools to create a great debugging experience for users.</span></span>
> * <span data-ttu-id="cc3c0-111">**Confiáveis** – as bibliotecas .NET têm a confiança dos desenvolvedores por publicarem no NuGet usando práticas recomendadas de segurança.</span><span class="sxs-lookup"><span data-stu-id="cc3c0-111">**Trusted** - .NET libraries have developers' trust by publishing to NuGet using security best practices.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="cc3c0-112">Introdução</span><span class="sxs-lookup"><span data-stu-id="cc3c0-112">Get Started</span></span>](./get-started.md)

## <a name="types-of-recommendations"></a><span data-ttu-id="cc3c0-113">Tipos de recomendações</span><span class="sxs-lookup"><span data-stu-id="cc3c0-113">Types of recommendations</span></span>

<span data-ttu-id="cc3c0-114">Cada artigo apresenta quatro tipos de recomendação: **Fazer**, **Considerar**, **Evitar** e **Não fazer**.</span><span class="sxs-lookup"><span data-stu-id="cc3c0-114">Each article presents four types of recommendations: **Do**, **Consider**, **Avoid**, and **Do not**.</span></span> <span data-ttu-id="cc3c0-115">O tipo de recomendação indica a intensidade em que ela deve ser seguida.</span><span class="sxs-lookup"><span data-stu-id="cc3c0-115">The type of recommendation indicates how strongly it should be followed.</span></span>

<span data-ttu-id="cc3c0-116">Procure quase sempre seguir a recomendação **Fazer**.</span><span class="sxs-lookup"><span data-stu-id="cc3c0-116">You should almost always follow a **Do** recommendation.</span></span> <span data-ttu-id="cc3c0-117">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="cc3c0-117">For example:</span></span>

<span data-ttu-id="cc3c0-118">**✔️ FAZER** a distribuição de sua biblioteca usando um pacote NuGet.</span><span class="sxs-lookup"><span data-stu-id="cc3c0-118">**✔️ DO** distribute your library using a NuGet package.</span></span>

<span data-ttu-id="cc3c0-119">Por outro lado, as recomendações **Considerar** geralmente devem ser seguidas, mas há exceções à regra legítimas e você não precisará se preocupar caso não possa seguir as diretrizes:</span><span class="sxs-lookup"><span data-stu-id="cc3c0-119">On the other hand, **Consider** recommendations should generally be followed, but there are legitimate exceptions to the rule and you shouldn't feel bad about not following the guidance:</span></span>

<span data-ttu-id="cc3c0-120">**✔️ CONSIDERAR** o uso do [SemVer 2.0.0](https://semver.org/) para criar a versão do seu pacote NuGet.</span><span class="sxs-lookup"><span data-stu-id="cc3c0-120">**✔️ CONSIDER** using [SemVer 2.0.0](https://semver.org/) to version your NuGet package.</span></span>

<span data-ttu-id="cc3c0-121">As recomendações **Evitar** mencionam coisas que em geral não são ideais, mas há casos em que, às vezes, quebrar a regra faz sentido:</span><span class="sxs-lookup"><span data-stu-id="cc3c0-121">**Avoid** recommendations mention things that are generally not a good idea, but breaking the rule sometimes makes sense:</span></span>

<span data-ttu-id="cc3c0-122">**❌ EVITAR** referências do pacote NuGet que demandam uma versão exata.</span><span class="sxs-lookup"><span data-stu-id="cc3c0-122">**❌ AVOID** NuGet package references that demand an exact version.</span></span>

<span data-ttu-id="cc3c0-123">Por fim, as recomendações **Não fazer** indicam algo que você quase nunca deve fazer:</span><span class="sxs-lookup"><span data-stu-id="cc3c0-123">And finally, **Do not** recommendations indicate something you should almost never do:</span></span>

<span data-ttu-id="cc3c0-124">**❌ NÃO FAZER** a publicação de versões de nome forte e sem nome forte da biblioteca.</span><span class="sxs-lookup"><span data-stu-id="cc3c0-124">**❌ DO NOT** publish strong-named and non-strong-named versions of your library.</span></span> <span data-ttu-id="cc3c0-125">Por exemplo, `Contoso.Api` e `Contoso.Api.StrongNamed`.</span><span class="sxs-lookup"><span data-stu-id="cc3c0-125">For example, `Contoso.Api` and `Contoso.Api.StrongNamed`.</span></span>

>[!div class="step-by-step"]
[<span data-ttu-id="cc3c0-126">Avançar</span><span class="sxs-lookup"><span data-stu-id="cc3c0-126">Next</span></span>](./get-started.md)
