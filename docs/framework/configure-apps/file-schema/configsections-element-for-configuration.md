---
title: "&lt;configSections&gt; elemento para &lt;configuração&gt;"
ms.date: 05/01/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: article
f1_keywords: http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections
helpviewer_keywords:
- configSections Element
- <configSections> Element
ms.assetid: 9f963c1b-dc3f-4220-a8b6-2dd7a5a8e039
author: guardrex
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 145a2a5cc23758c9fd2211c2da7fee0bbd736f0f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="configsections-element-for-configuration"></a><span data-ttu-id="8f518-102">\<configSections > elemento \<Configuração ></span><span class="sxs-lookup"><span data-stu-id="8f518-102">\<configSections> element for \<configuration></span></span>

<span data-ttu-id="8f518-103">Contém declarações de namespace e de seção de configuração.</span><span class="sxs-lookup"><span data-stu-id="8f518-103">Contains configuration section and namespace declarations.</span></span>

<span data-ttu-id="8f518-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="8f518-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="8f518-105">&nbsp;&nbsp;**\<configSections >**</span><span class="sxs-lookup"><span data-stu-id="8f518-105">&nbsp;&nbsp;**\<configSections>**</span></span>

## <a name="attributes"></a><span data-ttu-id="8f518-106">Atributos</span><span class="sxs-lookup"><span data-stu-id="8f518-106">Attributes</span></span>

<span data-ttu-id="8f518-107">Nenhum</span><span class="sxs-lookup"><span data-stu-id="8f518-107">None</span></span>

## <a name="parent-element"></a><span data-ttu-id="8f518-108">Elemento pai</span><span class="sxs-lookup"><span data-stu-id="8f518-108">Parent element</span></span>

|     | <span data-ttu-id="8f518-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="8f518-109">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="8f518-110">**\<configuration>**</span><span class="sxs-lookup"><span data-stu-id="8f518-110">**\<configuration>**</span></span>](~/docs/framework/configure-apps/file-schema/configuration-element.md) | <span data-ttu-id="8f518-111">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="8f518-111">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="8f518-112">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="8f518-112">Child elements</span></span>

|     | <span data-ttu-id="8f518-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="8f518-113">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="8f518-114">**\<seção >**</span><span class="sxs-lookup"><span data-stu-id="8f518-114">**\<section>**</span></span>](~/docs/framework/configure-apps/file-schema/section-element.md) | <span data-ttu-id="8f518-115">Contém uma declaração de seção de configuração.</span><span class="sxs-lookup"><span data-stu-id="8f518-115">Contains a configuration section declaration.</span></span> |
| [<span data-ttu-id="8f518-116">**\<sectionGroup >**</span><span class="sxs-lookup"><span data-stu-id="8f518-116">**\<sectionGroup>**</span></span>](~/docs/framework/configure-apps/file-schema/sectiongroup-element-for-configsections.md) | <span data-ttu-id="8f518-117">Define um namespace para seções de configuração.</span><span class="sxs-lookup"><span data-stu-id="8f518-117">Defines a namespace for configuration sections.</span></span> |
| [<span data-ttu-id="8f518-118">**\<remove>**</span><span class="sxs-lookup"><span data-stu-id="8f518-118">**\<remove>**</span></span>](~/docs/framework/configure-apps/file-schema/remove-element-for-configsections.md) | <span data-ttu-id="8f518-119">Remove uma seção predefinida ou grupo de seção.</span><span class="sxs-lookup"><span data-stu-id="8f518-119">Removes a predefined section or section group.</span></span> |
| [<span data-ttu-id="8f518-120">**\<clear>**</span><span class="sxs-lookup"><span data-stu-id="8f518-120">**\<clear>**</span></span>](~/docs/framework/configure-apps/file-schema/clear-element-for-configsections.md) | <span data-ttu-id="8f518-121">Limpa todas as seções definidas anteriormente e grupos de seções.</span><span class="sxs-lookup"><span data-stu-id="8f518-121">Clears all previously defined sections and section groups.</span></span> |

## <a name="remarks"></a><span data-ttu-id="8f518-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="8f518-122">Remarks</span></span>

<span data-ttu-id="8f518-123">Se esse elemento estiver em um arquivo de configuração, ele deve ser o primeiro elemento filho do  **\<Configuração >** elemento.</span><span class="sxs-lookup"><span data-stu-id="8f518-123">If this element is in a configuration file, it must be the first child element of the **\<configuration>** element.</span></span>

## <a name="example"></a><span data-ttu-id="8f518-124">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8f518-124">Example</span></span>

<span data-ttu-id="8f518-125">O exemplo a seguir mostra como definir uma seção de configuração e definir configurações para essa seção:</span><span class="sxs-lookup"><span data-stu-id="8f518-125">The following example shows how to define a configuration section and define settings for that section:</span></span>

```xml
<configuration>
  <configSections>
    <section name="sampleSection"
             type="System.Configuration.SingleTagSectionHandler" />
  </configSections>
  <sampleSection setting1="Value1" 
                 setting2="value two" 
                 setting3="third value" />
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="8f518-126">arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="8f518-126">Configuration file</span></span>

<span data-ttu-id="8f518-127">Esse elemento pode ser usado no arquivo de configuração do aplicativo, o arquivo de configuração de máquina (*Machine. config*), e *Web. config* arquivos que não estão no nível de diretório do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="8f518-127">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="8f518-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8f518-128">See also</span></span>

[<span data-ttu-id="8f518-129">Esquema de arquivo de configuração para o .NET Framework</span><span class="sxs-lookup"><span data-stu-id="8f518-129">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
