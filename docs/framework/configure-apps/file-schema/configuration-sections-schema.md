---
title: "Esquema de seções de configuração"
ms.date: 05/02/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- configuration settings [.NET Framework], custom
- schema configuration settings
- configuration sections [.NET Framework]
- custom elements
- configuration schema [.NET Framework], custom settings in configuration files
- elements [.NET Framework], custom settings in configuration files
ms.assetid: 6e4cc793-c526-4007-b4e9-37d56295f2cb
author: guardrex
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: da9af8fd24f1bf6e6effd411ad37490a4ee08804
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="configuration-sections-schema"></a><span data-ttu-id="aaa4e-102">Esquema de seções de configuração</span><span class="sxs-lookup"><span data-stu-id="aaa4e-102">Configuration sections schema</span></span>

<span data-ttu-id="aaa4e-103">O esquema de seções de configuração contém elementos que definem as configurações personalizadas em arquivos de configuração.</span><span class="sxs-lookup"><span data-stu-id="aaa4e-103">The configuration sections schema contains elements that define custom settings in configuration files.</span></span> <span data-ttu-id="aaa4e-104">Para obter informações gerais sobre esquemas e arquivos de configuração, consulte [esquema de arquivo de configuração para o .NET Framework](~/docs/framework/configure-apps/file-schema/index.md).</span><span class="sxs-lookup"><span data-stu-id="aaa4e-104">For general information on configuration files and schemas, see [Configuration file schema for the .NET Framework](~/docs/framework/configure-apps/file-schema/index.md).</span></span>

<span data-ttu-id="aaa4e-105">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="aaa4e-105">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="aaa4e-106">[**\<configSections >**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="aaa4e-106">[**\<configSections>**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) </span></span>  
<span data-ttu-id="aaa4e-107">[**\<Limpar >**](~/docs/framework/configure-apps/file-schema/clear-element-for-configsections.md) </span><span class="sxs-lookup"><span data-stu-id="aaa4e-107">[**\<clear>**](~/docs/framework/configure-apps/file-schema/clear-element-for-configsections.md) </span></span>  
<span data-ttu-id="aaa4e-108">[**\<Remover >**](~/docs/framework/configure-apps/file-schema/remove-element-for-configsections.md) </span><span class="sxs-lookup"><span data-stu-id="aaa4e-108">[**\<remove>**](~/docs/framework/configure-apps/file-schema/remove-element-for-configsections.md) </span></span>  
<span data-ttu-id="aaa4e-109">[**\<seção >**](~/docs/framework/configure-apps/file-schema/section-element.md) </span><span class="sxs-lookup"><span data-stu-id="aaa4e-109">[**\<section>**](~/docs/framework/configure-apps/file-schema/section-element.md) </span></span>  
[<span data-ttu-id="aaa4e-110">**\<sectionGroup >**</span><span class="sxs-lookup"><span data-stu-id="aaa4e-110">**\<sectionGroup>**</span></span>](~/docs/framework/configure-apps/file-schema/sectiongroup-element-for-configsections.md)

|     | <span data-ttu-id="aaa4e-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="aaa4e-111">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="aaa4e-112">**\<Limpar >** para  **\<configSections >**</span><span class="sxs-lookup"><span data-stu-id="aaa4e-112">**\<clear>** for **\<configSections>**</span></span>](~/docs/framework/configure-apps/file-schema/clear-element-for-configsections.md) | <span data-ttu-id="aaa4e-113">Limpa todas as seções definidas anteriormente e grupos de seções.</span><span class="sxs-lookup"><span data-stu-id="aaa4e-113">Clears all previously defined sections and section groups.</span></span> |
| [<span data-ttu-id="aaa4e-114">**\<clear>**</span><span class="sxs-lookup"><span data-stu-id="aaa4e-114">**\<clear>**</span></span>](~/docs/framework/configure-apps/file-schema/clear-element-for-configsections.md) | <span data-ttu-id="aaa4e-115">Limpa todas as seções definidas anteriormente e grupos de seções.</span><span class="sxs-lookup"><span data-stu-id="aaa4e-115">Clears all previously defined sections and section groups.</span></span> |
| [<span data-ttu-id="aaa4e-116">**\<configSections >**</span><span class="sxs-lookup"><span data-stu-id="aaa4e-116">**\<configSections>**</span></span>](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) | <span data-ttu-id="aaa4e-117">Contém declarações de namespace e de seção de configuração.</span><span class="sxs-lookup"><span data-stu-id="aaa4e-117">Contains configuration section and namespace declarations.</span></span> |
| [<span data-ttu-id="aaa4e-118">**\<Remover >** para  **\<configSections >**</span><span class="sxs-lookup"><span data-stu-id="aaa4e-118">**\<remove>** for **\<configSections>**</span></span>](~/docs/framework/configure-apps/file-schema/remove-element-for-configsections.md) | <span data-ttu-id="aaa4e-119">Remove uma seção predefinida ou grupo de seção.</span><span class="sxs-lookup"><span data-stu-id="aaa4e-119">Removes a predefined section or section group.</span></span> |
| [<span data-ttu-id="aaa4e-120">**\<seção >** para  **\<configSections >** e  **\<sectionGroup >**</span><span class="sxs-lookup"><span data-stu-id="aaa4e-120">**\<section>** for **\<configSections>** and **\<sectionGroup>**</span></span>](~/docs/framework/configure-apps/file-schema/section-element.md) | <span data-ttu-id="aaa4e-121">Contém uma declaração de seção de configuração.</span><span class="sxs-lookup"><span data-stu-id="aaa4e-121">Contains a configuration section declaration.</span></span> |
| [<span data-ttu-id="aaa4e-122">**\<sectionGroup >** para  **\<configSections >**</span><span class="sxs-lookup"><span data-stu-id="aaa4e-122">**\<sectionGroup>** for **\<configSections>**</span></span>](~/docs/framework/configure-apps/file-schema/sectiongroup-element-for-configsections.md) | <span data-ttu-id="aaa4e-123">Define um namespace para seções de configuração.</span><span class="sxs-lookup"><span data-stu-id="aaa4e-123">Defines a namespace for configuration sections.</span></span> |
