---
title: Esquema de seções de configuração
ms.date: 05/02/2017
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
ms.openlocfilehash: edd2b2e11b02d69b7bba7c3cc7d8a9a0814e0c51
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61674812"
---
# <a name="configuration-sections-schema"></a><span data-ttu-id="a97e4-102">Esquema de seções de configuração</span><span class="sxs-lookup"><span data-stu-id="a97e4-102">Configuration sections schema</span></span>

<span data-ttu-id="a97e4-103">O esquema de seções de configuração contém elementos que definem as configurações personalizadas em arquivos de configuração.</span><span class="sxs-lookup"><span data-stu-id="a97e4-103">The configuration sections schema contains elements that define custom settings in configuration files.</span></span> <span data-ttu-id="a97e4-104">Para obter informações gerais sobre esquemas e arquivos de configuração, consulte [esquema de arquivo de configuração para o .NET Framework](~/docs/framework/configure-apps/file-schema/index.md).</span><span class="sxs-lookup"><span data-stu-id="a97e4-104">For general information on configuration files and schemas, see [Configuration file schema for the .NET Framework](~/docs/framework/configure-apps/file-schema/index.md).</span></span>

<span data-ttu-id="a97e4-105">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="a97e4-105">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="a97e4-106">[**\<configSections>**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="a97e4-106">[**\<configSections>**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) </span></span>  
<span data-ttu-id="a97e4-107">[**\<clear>**](~/docs/framework/configure-apps/file-schema/clear-element-for-configsections.md) </span><span class="sxs-lookup"><span data-stu-id="a97e4-107">[**\<clear>**](~/docs/framework/configure-apps/file-schema/clear-element-for-configsections.md) </span></span>  
<span data-ttu-id="a97e4-108">[**\<remove>**](~/docs/framework/configure-apps/file-schema/remove-element-for-configsections.md) </span><span class="sxs-lookup"><span data-stu-id="a97e4-108">[**\<remove>**](~/docs/framework/configure-apps/file-schema/remove-element-for-configsections.md) </span></span>  
<span data-ttu-id="a97e4-109">[**\<section>**](~/docs/framework/configure-apps/file-schema/section-element.md) </span><span class="sxs-lookup"><span data-stu-id="a97e4-109">[**\<section>**](~/docs/framework/configure-apps/file-schema/section-element.md) </span></span>  
[<span data-ttu-id="a97e4-110">**\<sectionGroup>**</span><span class="sxs-lookup"><span data-stu-id="a97e4-110">**\<sectionGroup>**</span></span>](~/docs/framework/configure-apps/file-schema/sectiongroup-element-for-configsections.md)

|     | <span data-ttu-id="a97e4-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="a97e4-111">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="a97e4-112">**\<clear>** for **\<configSections>**</span><span class="sxs-lookup"><span data-stu-id="a97e4-112">**\<clear>** for **\<configSections>**</span></span>](~/docs/framework/configure-apps/file-schema/clear-element-for-configsections.md) | <span data-ttu-id="a97e4-113">Limpa todas as seções definidas anteriormente e grupos de seções.</span><span class="sxs-lookup"><span data-stu-id="a97e4-113">Clears all previously defined sections and section groups.</span></span> |
| [<span data-ttu-id="a97e4-114">**\<clear>**</span><span class="sxs-lookup"><span data-stu-id="a97e4-114">**\<clear>**</span></span>](~/docs/framework/configure-apps/file-schema/clear-element-for-configsections.md) | <span data-ttu-id="a97e4-115">Limpa todas as seções definidas anteriormente e grupos de seções.</span><span class="sxs-lookup"><span data-stu-id="a97e4-115">Clears all previously defined sections and section groups.</span></span> |
| [<span data-ttu-id="a97e4-116">**\<configSections>**</span><span class="sxs-lookup"><span data-stu-id="a97e4-116">**\<configSections>**</span></span>](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) | <span data-ttu-id="a97e4-117">Contém as declarações de namespace e a seção de configuração.</span><span class="sxs-lookup"><span data-stu-id="a97e4-117">Contains configuration section and namespace declarations.</span></span> |
| [<span data-ttu-id="a97e4-118">**\<Remover >** para  **\<configSections >**</span><span class="sxs-lookup"><span data-stu-id="a97e4-118">**\<remove>** for **\<configSections>**</span></span>](~/docs/framework/configure-apps/file-schema/remove-element-for-configsections.md) | <span data-ttu-id="a97e4-119">Remove uma seção predefinidos ou grupo da seção.</span><span class="sxs-lookup"><span data-stu-id="a97e4-119">Removes a predefined section or section group.</span></span> |
| [<span data-ttu-id="a97e4-120">**\<seção >** para  **\<configSections >** e  **\<sectionGroup >**</span><span class="sxs-lookup"><span data-stu-id="a97e4-120">**\<section>** for **\<configSections>** and **\<sectionGroup>**</span></span>](~/docs/framework/configure-apps/file-schema/section-element.md) | <span data-ttu-id="a97e4-121">Contém uma declaração de seção de configuração.</span><span class="sxs-lookup"><span data-stu-id="a97e4-121">Contains a configuration section declaration.</span></span> |
| [<span data-ttu-id="a97e4-122">**\<sectionGroup>** for **\<configSections>**</span><span class="sxs-lookup"><span data-stu-id="a97e4-122">**\<sectionGroup>** for **\<configSections>**</span></span>](~/docs/framework/configure-apps/file-schema/sectiongroup-element-for-configsections.md) | <span data-ttu-id="a97e4-123">Define um namespace para seções de configuração.</span><span class="sxs-lookup"><span data-stu-id="a97e4-123">Defines a namespace for configuration sections.</span></span> |
