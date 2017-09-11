---
title: Compatibilidade de aplicativos no .NET Framework
ms.custom: 
ms.date: 05/19/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
- app-compat
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- application compatibility
- .NET Framework application compatibility
- .NET Framework changes
caps.latest.revision: 19
ms.assetid: c4ba3ff2-fe59-4c5d-9e0b-86bba3cd865c
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: b3c7df2984c2c9e8af308ca8070f7207d11ba49e
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---

# <a name="application-compatibility-in-the-net-framework"></a><span data-ttu-id="ca0f1-102">Compatibilidade de aplicativos no .NET Framework</span><span class="sxs-lookup"><span data-stu-id="ca0f1-102">Application Compatibility in the .NET Framework</span></span>

## <a name="introduction"></a><span data-ttu-id="ca0f1-103">Introdução</span><span class="sxs-lookup"><span data-stu-id="ca0f1-103">Introduction</span></span>

<span data-ttu-id="ca0f1-104">A compatibilidade é uma meta muito importante de cada versão do .NET.</span><span class="sxs-lookup"><span data-stu-id="ca0f1-104">Compatibility is a very important goal of each .NET release.</span></span> <span data-ttu-id="ca0f1-105">A compatibilidade garante que cada versão é aditiva e, portanto, as versões anteriores ainda funcionarão.</span><span class="sxs-lookup"><span data-stu-id="ca0f1-105">Compatibility ensures that each version is additive, so previous versions will still work.</span></span> <span data-ttu-id="ca0f1-106">Por outro lado, as alterações na funcionalidade anterior (para melhorar o desempenho, resolver problemas de segurança ou corrigir bugs) podem causar problemas de compatibilidade no código ou nos aplicativos existentes que são executados em uma versão posterior.</span><span class="sxs-lookup"><span data-stu-id="ca0f1-106">On the other hand, changes to previous functionality (to improve performance, address security issues, or fix bugs) can cause compatibility problems in existing code or existing applications that run under a later version.</span></span> <span data-ttu-id="ca0f1-107">O .NET Framework reconhece as alterações de redirecionamento e de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="ca0f1-107">The .NET Framework recognizes retargeting changes and runtime changes.</span></span> <span data-ttu-id="ca0f1-108">As alterações de redirecionamento afetam os aplicativos que se destinam a uma versão específica do .NET Framework, mas que são executados em uma versão posterior.</span><span class="sxs-lookup"><span data-stu-id="ca0f1-108">Retargeting changes affect applications that target a specific version of the .NET Framework but are running on a later version.</span></span> <span data-ttu-id="ca0f1-109">As alterações de tempo de execução afetam todos os aplicativos executados em uma versão específica.</span><span class="sxs-lookup"><span data-stu-id="ca0f1-109">Runtime changes affect all applications running on a particular version.</span></span>

<span data-ttu-id="ca0f1-110">Cada aplicativo se destina a uma versão específica do .NET Framework, que pode ser especificada por meio da:</span><span class="sxs-lookup"><span data-stu-id="ca0f1-110">Each app targets a specific version of the .NET Framework, which can be specified by:</span></span>

- <span data-ttu-id="ca0f1-111">Definição de uma estrutura de destino no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="ca0f1-111">Defining a target framework in Visual Studio.</span></span>
- <span data-ttu-id="ca0f1-112">Especificação da estrutura de destino em um arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="ca0f1-112">Specifying the target framework in a project file.</span></span>
- <span data-ttu-id="ca0f1-113">Aplicação de um <xref:System.Runtime.Versioning.TargetFrameworkAttribute> ao código-fonte.</span><span class="sxs-lookup"><span data-stu-id="ca0f1-113">Applying a <xref:System.Runtime.Versioning.TargetFrameworkAttribute> to the source code.</span></span>

<span data-ttu-id="ca0f1-114">Quando for executado em uma versão mais recente do que a versão à qual foi destinado, o .NET Framework usará o comportamento peculiar para simular a versão de destino mais antiga.</span><span class="sxs-lookup"><span data-stu-id="ca0f1-114">When running on a newer version than what was targeted, the .NET Framework will use quirked behavior to mimic the older targeted version.</span></span> <span data-ttu-id="ca0f1-115">Em outras palavras, o aplicativo será executado na versão mais recente do Framework, mas atuará como se estivesse sendo executado na versão mais antiga.</span><span class="sxs-lookup"><span data-stu-id="ca0f1-115">In other words, the app will run on the newer version of the Framework, but act as if it's running on the older version.</span></span> <span data-ttu-id="ca0f1-116">Muitos dos problemas de compatibilidade entre versões do .NET Framework são atenuados com esse modelo de peculiaridade.</span><span class="sxs-lookup"><span data-stu-id="ca0f1-116">Many of the compatibility issues between versions of the .NET Framework are mitigated through this quirking model.</span></span>

## <a name="runtime-changes"></a><span data-ttu-id="ca0f1-117">Alterações em tempo de execução</span><span class="sxs-lookup"><span data-stu-id="ca0f1-117">Runtime changes</span></span>

<span data-ttu-id="ca0f1-118">Problemas de tempo de execução são aqueles que surgem quando um novo tempo de execução é colocado em um computador e os mesmos binários são executados, mas um comportamento diferente é observado.</span><span class="sxs-lookup"><span data-stu-id="ca0f1-118">Runtime issues are those that arise when a new runtime is placed on a machine and the same binaries are run, but different behavior is seen.</span></span> <span data-ttu-id="ca0f1-119">Se um binário foi compilado para o .NET Framework 4.0, ele será executado no modo de compatibilidade do .NET Framework 4.0 na versão 4.5 ou em versões posteriores.</span><span class="sxs-lookup"><span data-stu-id="ca0f1-119">If a binary was compiled for .NET Framework 4.0 it will run in .NET Framework 4.0 compatibility mode on 4.5 or later versions.</span></span> <span data-ttu-id="ca0f1-120">Muitas das alterações que afetam a versão 4.5 não afetarão um binário compilado para a versão 4.0.</span><span class="sxs-lookup"><span data-stu-id="ca0f1-120">Many of the changes that affect 4.5 will not affect a binary compiled for 4.0.</span></span> <span data-ttu-id="ca0f1-121">Isso é específico a um AppDomain e depende das configurações do assembly de entrada.</span><span class="sxs-lookup"><span data-stu-id="ca0f1-121">This is specific to the AppDomain and depends on the settings of the entry assembly.</span></span>

## <a name="retargeting-changes"></a><span data-ttu-id="ca0f1-122">Alterações de redirecionamento</span><span class="sxs-lookup"><span data-stu-id="ca0f1-122">Retargeting changes</span></span>

<span data-ttu-id="ca0f1-123">Problemas de redirecionamento são aqueles que surgem quando um assembly que era destinado à versão 4.0 agora está definido para ter a versão 4.5 como destino.</span><span class="sxs-lookup"><span data-stu-id="ca0f1-123">Retargeting issues are those that arise when an assembly that was targeting 4.0 is now set to target 4.5.</span></span> <span data-ttu-id="ca0f1-124">Agora o assembly aceita os novos recursos, bem como os possíveis problemas de compatibilidade dos recursos antigos.</span><span class="sxs-lookup"><span data-stu-id="ca0f1-124">Now the assembly opts into the new features as well as potential compatibility issues to old features.</span></span> <span data-ttu-id="ca0f1-125">Novamente, isso é determinado pelo assembly de entrada e, portanto, o aplicativo de console que usa o assembly ou o site que referencia o assembly.</span><span class="sxs-lookup"><span data-stu-id="ca0f1-125">Again, this is dictated by the entry assembly, so the console app that uses the assembly, or the website that references the assembly.</span></span>

## <a name="net-compatibility-diagnostics"></a><span data-ttu-id="ca0f1-126">Diagnóstico de Compatibilidade do .NET</span><span class="sxs-lookup"><span data-stu-id="ca0f1-126">.NET Compatibility Diagnostics</span></span>

<span data-ttu-id="ca0f1-127">O Diagnóstico de Compatibilidade do .NET são analisadores capacitados pelo Roslyn que ajudam a identificar problemas de compatibilidade de aplicativos entre versões do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ca0f1-127">The .NET Compatibility Diagnostics are Roslyn-powered analyzers that help identify application compatibility issues between versions of the .NET Framework.</span></span> <span data-ttu-id="ca0f1-128">Esta lista contém todos os analisadores disponíveis, embora apenas um subconjunto seja aplicado a qualquer migração específica.</span><span class="sxs-lookup"><span data-stu-id="ca0f1-128">This list contains all of the analyzers available, although only a subset will apply to any specific migration.</span></span> <span data-ttu-id="ca0f1-129">Os analisadores determinarão quais problemas se aplicam à migração planejada e os trará à tona.</span><span class="sxs-lookup"><span data-stu-id="ca0f1-129">The analyzers will determine which issues are applicable for the planned migration and will only surface those.</span></span>

<span data-ttu-id="ca0f1-130">Cada problema inclui as seguintes informações:</span><span class="sxs-lookup"><span data-stu-id="ca0f1-130">Each issue includes the following information:</span></span>

-   <span data-ttu-id="ca0f1-131">A descrição do que mudou em relação a uma versão anterior.</span><span class="sxs-lookup"><span data-stu-id="ca0f1-131">The description of what has changed from a previous version.</span></span>

-   <span data-ttu-id="ca0f1-132">Como a alteração afeta os clientes e se alguma solução alternativa está disponível para preservar a compatibilidade entre versões.</span><span class="sxs-lookup"><span data-stu-id="ca0f1-132">How the change affects customers and whether any workarounds are available to preserve compatibility across versions.</span></span>

-   <span data-ttu-id="ca0f1-133">Uma avaliação da importância da alteração.</span><span class="sxs-lookup"><span data-stu-id="ca0f1-133">An assessment of how important the change is.</span></span> <span data-ttu-id="ca0f1-134">O problema de compatibilidade de aplicativos é categorizado como se segue:</span><span class="sxs-lookup"><span data-stu-id="ca0f1-134">Application compatibility issue are categorized as follows:</span></span>

    |   |   |
    |---|---|
    |<span data-ttu-id="ca0f1-135">Principal</span><span class="sxs-lookup"><span data-stu-id="ca0f1-135">Major</span></span>|<span data-ttu-id="ca0f1-136">Uma alteração significativa que afeta um grande número de aplicativos ou que exige a modificação significativa do código.</span><span class="sxs-lookup"><span data-stu-id="ca0f1-136">A significant change that affects a large number of apps or requires substantial modification of code.</span></span>|
    |<span data-ttu-id="ca0f1-137">Secundário</span><span class="sxs-lookup"><span data-stu-id="ca0f1-137">Minor</span></span>|<span data-ttu-id="ca0f1-138">Uma alteração que afeta um pequeno número de aplicativos ou que exige modificação secundária do código.</span><span class="sxs-lookup"><span data-stu-id="ca0f1-138">A change that affects a small number of apps or that requires minor modification of code.</span></span>|
    |<span data-ttu-id="ca0f1-139">Caso de borda</span><span class="sxs-lookup"><span data-stu-id="ca0f1-139">Edge case</span></span>|<span data-ttu-id="ca0f1-140">Uma alteração que afeta aplicativos em cenários muito específicos que não são comuns.</span><span class="sxs-lookup"><span data-stu-id="ca0f1-140">A change that affects apps under very specific, uncommon scenarios.</span></span>|
    |<span data-ttu-id="ca0f1-141">Transparente</span><span class="sxs-lookup"><span data-stu-id="ca0f1-141">Transparent</span></span>|<span data-ttu-id="ca0f1-142">Uma alteração que não afeta visivelmente o desenvolvedor nem o usuário do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ca0f1-142">A change with no noticeable effect on the application's developer or user.</span></span>|

-   <span data-ttu-id="ca0f1-143">A versão indica quando a alteração aparece pela primeira vez na estrutura.</span><span class="sxs-lookup"><span data-stu-id="ca0f1-143">Version indicates when the change first appears in the framework.</span></span> <span data-ttu-id="ca0f1-144">Algumas alterações são introduzidas em uma versão específica e revertidas em uma versão posterior; isso também é indicado.</span><span class="sxs-lookup"><span data-stu-id="ca0f1-144">Some of the changes are introduced in a particular version and reverted in a later version; that is indicated as well.</span></span>

-   <span data-ttu-id="ca0f1-145">O tipo de alteração:</span><span class="sxs-lookup"><span data-stu-id="ca0f1-145">The type of change:</span></span>

    |   |   |
    |---|---|
    |<span data-ttu-id="ca0f1-146">Redirecionando</span><span class="sxs-lookup"><span data-stu-id="ca0f1-146">Retargeting</span></span>|<span data-ttu-id="ca0f1-147">A alteração afeta aplicativos que são recompilados para uma nova versão do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ca0f1-147">The change affects apps that are recompiled to target a new version of the .NET Framework.</span></span>|
    |<span data-ttu-id="ca0f1-148">Tempo de execução</span><span class="sxs-lookup"><span data-stu-id="ca0f1-148">Runtime</span></span>|<span data-ttu-id="ca0f1-149">A alteração afeta um aplicativo existente que se destina a uma versão anterior do .NET Framework, mas é executado em uma versão posterior.</span><span class="sxs-lookup"><span data-stu-id="ca0f1-149">The change affects an existing app that targets a previous version of the .NET Framework but runs on a later version.</span></span>|

-   <span data-ttu-id="ca0f1-150">As APIs afetadas, se houver.</span><span class="sxs-lookup"><span data-stu-id="ca0f1-150">The affected APIS, if any.</span></span>

-   <span data-ttu-id="ca0f1-151">As IDs do diagnóstico disponível</span><span class="sxs-lookup"><span data-stu-id="ca0f1-151">The IDs of the available diagnostics</span></span>

## <a name="usage"></a><span data-ttu-id="ca0f1-152">Uso</span><span class="sxs-lookup"><span data-stu-id="ca0f1-152">Usage</span></span>

<span data-ttu-id="ca0f1-153">Para começar, selecione o tipo de alteração de compatibilidade abaixo:</span><span class="sxs-lookup"><span data-stu-id="ca0f1-153">To begin, select the type of compatibility change below:</span></span>

- [<span data-ttu-id="ca0f1-154">Alterações de redirecionamento</span><span class="sxs-lookup"><span data-stu-id="ca0f1-154">Retargeting Changes</span></span>](./retargeting/index.md)
- [<span data-ttu-id="ca0f1-155">Alterações no tempo de execução</span><span class="sxs-lookup"><span data-stu-id="ca0f1-155">Runtime Changes</span></span>](./runtime/index.md)


## <a name="see-also"></a><span data-ttu-id="ca0f1-156">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ca0f1-156">See also</span></span>

<span data-ttu-id="ca0f1-157">[Versões e dependências](../../../docs/framework/migration-guide/versions-and-dependencies.md) </span><span class="sxs-lookup"><span data-stu-id="ca0f1-157">[Versions and Dependencies](../../../docs/framework/migration-guide/versions-and-dependencies.md) </span></span>  
<span data-ttu-id="ca0f1-158">[Novidades](../../../docs/framework/whats-new/index.md) </span><span class="sxs-lookup"><span data-stu-id="ca0f1-158">[What's New](../../../docs/framework/whats-new/index.md) </span></span>  
[<span data-ttu-id="ca0f1-159">O que está obsoleto na Biblioteca de Classes</span><span class="sxs-lookup"><span data-stu-id="ca0f1-159">What's Obsolete in the Class Library</span></span>](../../../docs/framework/whats-new/whats-obsolete.md)

