---
title: Tempo de execução e redirecionamento de alterações - .NET Framework
ms.date: 10/29/2019
helpviewer_keywords:
- application compatibility
- .NET Framework application compatibility
- .NET Framework changes
ms.assetid: c4ba3ff2-fe59-4c5d-9e0b-86bba3cd865c
ms.openlocfilehash: c46f781d495b87a4f24e77935df7c4814c8567ae
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73196702"
---
# <a name="application-compatibility-in-the-net-framework"></a><span data-ttu-id="c8e62-102">Compatibilidade de aplicativos no Framework .NET</span><span class="sxs-lookup"><span data-stu-id="c8e62-102">Application compatibility in the .NET Framework</span></span>

<span data-ttu-id="c8e62-103">A compatibilidade é um objetivo importante de cada versão .NET.</span><span class="sxs-lookup"><span data-stu-id="c8e62-103">Compatibility is an important goal of each .NET release.</span></span> <span data-ttu-id="c8e62-104">A compatibilidade garante que cada versão seja aditiva, de modo que as versões anteriores continuarão a funcionar.</span><span class="sxs-lookup"><span data-stu-id="c8e62-104">Compatibility ensures that each version is additive, so previous versions will continue to work.</span></span> <span data-ttu-id="c8e62-105">Por outro lado, alterações na funcionalidade anterior (por exemplo, para melhorar o desempenho, resolver problemas de segurança ou corrigir bugs) podem causar problemas de compatibilidade no código existente ou aplicativos existentes que são executados em uma versão posterior.</span><span class="sxs-lookup"><span data-stu-id="c8e62-105">On the other hand, changes to previous functionality (for example, to improve performance, address security issues, or fix bugs) can cause compatibility problems in existing code or existing applications that run under a later version.</span></span>

<span data-ttu-id="c8e62-106">Cada aplicativo tem como alvo uma versão específica do .NET Framework por:</span><span class="sxs-lookup"><span data-stu-id="c8e62-106">Each app targets a specific version of the .NET Framework by:</span></span>

- <span data-ttu-id="c8e62-107">Definição de uma estrutura de destino no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c8e62-107">Defining a target framework in Visual Studio.</span></span>
- <span data-ttu-id="c8e62-108">Especificação da estrutura de destino em um arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="c8e62-108">Specifying the target framework in a project file.</span></span>
- <span data-ttu-id="c8e62-109">Aplicação de um <xref:System.Runtime.Versioning.TargetFrameworkAttribute> ao código-fonte.</span><span class="sxs-lookup"><span data-stu-id="c8e62-109">Applying a <xref:System.Runtime.Versioning.TargetFrameworkAttribute> to the source code.</span></span>

<span data-ttu-id="c8e62-110">Ao migrar de uma versão do .NET Framework para outra, existem dois tipos de alterações a considerar:</span><span class="sxs-lookup"><span data-stu-id="c8e62-110">When migrating from one version of the .NET Framework to another, there are two types of changes to consider:</span></span>

- [<span data-ttu-id="c8e62-111">Alterações de tempo de execução</span><span class="sxs-lookup"><span data-stu-id="c8e62-111">Runtime changes</span></span>](#runtime-changes)
- [<span data-ttu-id="c8e62-112">Redirecionamento de alterações</span><span class="sxs-lookup"><span data-stu-id="c8e62-112">Retargeting changes</span></span>](#retargeting-changes)

## <a name="runtime-changes"></a><span data-ttu-id="c8e62-113">Alterações em runtime</span><span class="sxs-lookup"><span data-stu-id="c8e62-113">Runtime changes</span></span>

<span data-ttu-id="c8e62-114">Problemas de tempo de execução são aqueles que surgem quando um novo tempo de execução é colocado em uma máquina e o comportamento de um aplicativo muda.</span><span class="sxs-lookup"><span data-stu-id="c8e62-114">Runtime issues are those that arise when a new runtime is placed on a machine and an app's behavior changes.</span></span> <span data-ttu-id="c8e62-115">Ao ser executado em uma versão mais recente do que o que foi visado, o .NET Framework usa comportamento *peculiar* para imitar a versão direcionada mais antiga.</span><span class="sxs-lookup"><span data-stu-id="c8e62-115">When running on a newer version than what was targeted, the .NET Framework uses *quirked* behavior to mimic the older targeted version.</span></span> <span data-ttu-id="c8e62-116">O aplicativo é executado na versão mais recente, mas age como se estivesse sendo executado na versão mais antiga.</span><span class="sxs-lookup"><span data-stu-id="c8e62-116">The app runs on the newer version but acts as if it's running on the older version.</span></span> <span data-ttu-id="c8e62-117">Muitos dos problemas de compatibilidade entre versões do .NET Framework são atenuados com esse modelo de peculiaridade.</span><span class="sxs-lookup"><span data-stu-id="c8e62-117">Many of the compatibility issues between versions of the .NET Framework are mitigated through this quirking model.</span></span> <span data-ttu-id="c8e62-118">Por exemplo, se um binário foi compilado para o .NET Framework 4.0, mas é executado em uma máquina com o .NET Framework 4.5 ou posterior, ele será executado no modo de compatibilidade .NET Framework 4.0.</span><span class="sxs-lookup"><span data-stu-id="c8e62-118">For example, if a binary was compiled for .NET Framework 4.0 but runs on a machine with .NET Framework 4.5 or later, it runs in .NET Framework 4.0 compatibility mode.</span></span> <span data-ttu-id="c8e62-119">Isso significa que muitas das alterações na versão posterior não afetam o binário.</span><span class="sxs-lookup"><span data-stu-id="c8e62-119">This means that many of the changes in the later version don't affect the binary.</span></span>

<span data-ttu-id="c8e62-120">A versão do .NET Framework que um aplicativo segmenta é determinada pela versão de destino do conjunto de entrada para o domínio do aplicativo em que o código é executado.</span><span class="sxs-lookup"><span data-stu-id="c8e62-120">The version of the .NET Framework that an application targets is determined by the target version of the entry assembly for the application domain that the code runs in.</span></span> <span data-ttu-id="c8e62-121">Todos os conjuntos adicionais carregados nesse destino de domínio visam essa versão.</span><span class="sxs-lookup"><span data-stu-id="c8e62-121">All additional assemblies loaded in that application domain target that version.</span></span> <span data-ttu-id="c8e62-122">Por exemplo, no caso de um executável, a versão que os alvos executáveis são o modo de compatibilidade que todos os conjuntos nesse domínio de aplicativo são executados.</span><span class="sxs-lookup"><span data-stu-id="c8e62-122">For example, in the case of an executable, the version that the executable targets is the compatibility mode all assemblies in that application domain run under.</span></span>

<span data-ttu-id="c8e62-123">Para ver uma lista de alterações de tempo de execução que se aplicam ao seu ambiente, selecione a versão .NET Framework que você está mirando no momento e, em seguida, a versão para a qual deseja migrar:</span><span class="sxs-lookup"><span data-stu-id="c8e62-123">To see a list of runtime changes that apply to your environment, select the .NET Framework version you're currently targeting and then the version you wish to migrate to:</span></span>

[!INCLUDE[versionselector](../../../includes/migration-guide/runtime/versionselector.md)]

## <a name="retargeting-changes"></a><span data-ttu-id="c8e62-124">Alterações de redirecionamento</span><span class="sxs-lookup"><span data-stu-id="c8e62-124">Retargeting changes</span></span>

<span data-ttu-id="c8e62-125">As alterações de redirecionamento são aquelas que surgem quando um conjunto é recompilado para atingir uma versão mais recente.</span><span class="sxs-lookup"><span data-stu-id="c8e62-125">Retargeting changes are those that arise when an assembly is recompiled to target a newer version.</span></span> <span data-ttu-id="c8e62-126">Direcionar uma versão mais recente significa que o conjunto opta pelos novos recursos, bem como possíveis problemas de compatibilidade para recursos antigos.</span><span class="sxs-lookup"><span data-stu-id="c8e62-126">Targeting a newer version means the assembly opts into the new features as well as potential compatibility issues for old features.</span></span>

<span data-ttu-id="c8e62-127">Para ver uma lista de alterações de redirecionamento que se aplicam ao seu ambiente, selecione a versão .NET Framework que você está mirando no momento e, em seguida, a versão para a qual deseja migrar:</span><span class="sxs-lookup"><span data-stu-id="c8e62-127">To see a list of retargeting changes that apply to your environment, select the .NET Framework version you're currently targeting and then the version you wish to migrate to:</span></span>

[!INCLUDE[versionselector](../../../includes/migration-guide/retargeting/versionselector.md)]

## <a name="impact-classification"></a><span data-ttu-id="c8e62-128">Classificação de impacto</span><span class="sxs-lookup"><span data-stu-id="c8e62-128">Impact classification</span></span>

<span data-ttu-id="c8e62-129">Nos tópicos que descrevem as alterações de tempo de execução e redirecionamento, por exemplo, [redirecionando alterações para migrar de 4.7.2 para 4.8](retargeting/4.7.2-4.8.md), os itens individuais são classificados pelo impacto esperado da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="c8e62-129">In the topics that describe runtime and retargeting changes, for example, [Retargeting changes for migrating from 4.7.2 to 4.8](retargeting/4.7.2-4.8.md), individual items are classified by their expected impact as follows:</span></span>

<span data-ttu-id="c8e62-130">**Principais**</span><span class="sxs-lookup"><span data-stu-id="c8e62-130">**Major**</span></span>\
<span data-ttu-id="c8e62-131">Uma alteração significativa que afeta um grande número de aplicativos ou que exige a modificação significativa do código.</span><span class="sxs-lookup"><span data-stu-id="c8e62-131">A significant change that affects a large number of apps or that requires substantial modification of code.</span></span>

<span data-ttu-id="c8e62-132">**Menor**</span><span class="sxs-lookup"><span data-stu-id="c8e62-132">**Minor**</span></span>\
<span data-ttu-id="c8e62-133">Uma alteração que afeta um pequeno número de aplicativos ou que exige modificação secundária do código.</span><span class="sxs-lookup"><span data-stu-id="c8e62-133">A change that affects a small number of apps or that requires minor modification of code.</span></span>

<span data-ttu-id="c8e62-134">**Caixa de borda**</span><span class="sxs-lookup"><span data-stu-id="c8e62-134">**Edge case**</span></span>\
<span data-ttu-id="c8e62-135">Uma alteração que afeta aplicativos em cenários muito específicos que não são comuns.</span><span class="sxs-lookup"><span data-stu-id="c8e62-135">A change that affects apps under very specific scenarios that are not common.</span></span>

<span data-ttu-id="c8e62-136">**Transparente**</span><span class="sxs-lookup"><span data-stu-id="c8e62-136">**Transparent**</span></span>\
<span data-ttu-id="c8e62-137">Uma alteração que não tem efeito visível para o desenvolvedor ou o usuário do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c8e62-137">A change that has no noticeable effect on the app's developer or user.</span></span> <span data-ttu-id="c8e62-138">O aplicativo não deve exigir modificação por conta dessa alteração.</span><span class="sxs-lookup"><span data-stu-id="c8e62-138">The app should not require modification because of this change.</span></span>

## <a name="see-also"></a><span data-ttu-id="c8e62-139">Confira também</span><span class="sxs-lookup"><span data-stu-id="c8e62-139">See also</span></span>

- [<span data-ttu-id="c8e62-140">Versões e dependências</span><span class="sxs-lookup"><span data-stu-id="c8e62-140">Versions and dependencies</span></span>](versions-and-dependencies.md)
- [<span data-ttu-id="c8e62-141">Novidades</span><span class="sxs-lookup"><span data-stu-id="c8e62-141">What's new</span></span>](../whats-new/index.md)
- [<span data-ttu-id="c8e62-142">O que é obsoleto</span><span class="sxs-lookup"><span data-stu-id="c8e62-142">What's obsolete</span></span>](../whats-new/whats-obsolete.md)
