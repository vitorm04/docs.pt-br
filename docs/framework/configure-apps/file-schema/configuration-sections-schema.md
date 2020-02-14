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
ms.openlocfilehash: b97fea90be301e791bc4109142e6a8b8e1dedaa1
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77214771"
---
# <a name="configuration-sections-schema"></a><span data-ttu-id="3d0d6-102">Esquema de seções de configuração</span><span class="sxs-lookup"><span data-stu-id="3d0d6-102">Configuration sections schema</span></span>

<span data-ttu-id="3d0d6-103">O esquema de seções de configuração contém elementos que definem configurações personalizadas em arquivos de configuração.</span><span class="sxs-lookup"><span data-stu-id="3d0d6-103">The configuration sections schema contains elements that define custom settings in configuration files.</span></span> <span data-ttu-id="3d0d6-104">Para obter informações gerais sobre esquemas e arquivos de configuração, consulte [esquema do arquivo de configuração para o .NET Framework](index.md).</span><span class="sxs-lookup"><span data-stu-id="3d0d6-104">For general information on configuration files and schemas, see [Configuration file schema for the .NET Framework](index.md).</span></span>

<span data-ttu-id="3d0d6-105">[ **\<configuration>** ](configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="3d0d6-105">[**\<configuration>**](configuration-element.md) </span></span>  
<span data-ttu-id="3d0d6-106">[ **\<configsections >** ](configsections-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="3d0d6-106">[**\<configSections>**](configsections-element-for-configuration.md) </span></span>  
<span data-ttu-id="3d0d6-107">[ **\<limpar >** ](clear-element-for-configsections.md) </span><span class="sxs-lookup"><span data-stu-id="3d0d6-107">[**\<clear>**](clear-element-for-configsections.md) </span></span>  
<span data-ttu-id="3d0d6-108">[ **\<remover >** ](remove-element-for-configsections.md) </span><span class="sxs-lookup"><span data-stu-id="3d0d6-108">[**\<remove>**](remove-element-for-configsections.md) </span></span>  
<span data-ttu-id="3d0d6-109">[ **> da seção\<** ](section-element.md) </span><span class="sxs-lookup"><span data-stu-id="3d0d6-109">[**\<section>**](section-element.md) </span></span>  
[<span data-ttu-id="3d0d6-110"> **\<> de seção**</span><span class="sxs-lookup"><span data-stu-id="3d0d6-110">**\<sectionGroup>**</span></span>](sectiongroup-element-for-configsections.md)

|     | <span data-ttu-id="3d0d6-111">DESCRIÇÃO</span><span class="sxs-lookup"><span data-stu-id="3d0d6-111">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="3d0d6-112"> **\<limpar >** para **\<configSections >** </span><span class="sxs-lookup"><span data-stu-id="3d0d6-112">**\<clear>** for **\<configSections>**</span></span>](clear-element-for-configsections.md) | <span data-ttu-id="3d0d6-113">Limpa todas as seções e grupos de seções definidos anteriormente.</span><span class="sxs-lookup"><span data-stu-id="3d0d6-113">Clears all previously defined sections and section groups.</span></span> |
| [<span data-ttu-id="3d0d6-114"> **\<clear>** </span><span class="sxs-lookup"><span data-stu-id="3d0d6-114">**\<clear>**</span></span>](clear-element-for-configsections.md) | <span data-ttu-id="3d0d6-115">Limpa todas as seções e grupos de seções definidos anteriormente.</span><span class="sxs-lookup"><span data-stu-id="3d0d6-115">Clears all previously defined sections and section groups.</span></span> |
| [<span data-ttu-id="3d0d6-116"> **\<configSections >** </span><span class="sxs-lookup"><span data-stu-id="3d0d6-116">**\<configSections>**</span></span>](configsections-element-for-configuration.md) | <span data-ttu-id="3d0d6-117">Contém as declarações de namespace e seção de configuração.</span><span class="sxs-lookup"><span data-stu-id="3d0d6-117">Contains configuration section and namespace declarations.</span></span> |
| [<span data-ttu-id="3d0d6-118"> **\<remover >** para **\<configSections >** </span><span class="sxs-lookup"><span data-stu-id="3d0d6-118">**\<remove>** for **\<configSections>**</span></span>](remove-element-for-configsections.md) | <span data-ttu-id="3d0d6-119">Remove uma seção ou um grupo de seções predefinido.</span><span class="sxs-lookup"><span data-stu-id="3d0d6-119">Removes a predefined section or section group.</span></span> |
| [<span data-ttu-id="3d0d6-120"> **\<seção >** para **\<configSections >** e **\<** ></span><span class="sxs-lookup"><span data-stu-id="3d0d6-120">**\<section>** for **\<configSections>** and **\<sectionGroup>**</span></span>](section-element.md) | <span data-ttu-id="3d0d6-121">Contém uma declaração de seção de configuração.</span><span class="sxs-lookup"><span data-stu-id="3d0d6-121">Contains a configuration section declaration.</span></span> |
| [<span data-ttu-id="3d0d6-122"> **> de\<** do\<de seções para os **configSections >** </span><span class="sxs-lookup"><span data-stu-id="3d0d6-122">**\<sectionGroup>** for **\<configSections>**</span></span>](sectiongroup-element-for-configsections.md) | <span data-ttu-id="3d0d6-123">Define um namespace para seções de configuração.</span><span class="sxs-lookup"><span data-stu-id="3d0d6-123">Defines a namespace for configuration sections.</span></span> |
