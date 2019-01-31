---
title: Elemento <configSections> para <configuration>
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections
helpviewer_keywords:
- configSections Element
- <configSections> Element
ms.assetid: 9f963c1b-dc3f-4220-a8b6-2dd7a5a8e039
author: guardrex
ms.author: mairaw
ms.openlocfilehash: dc2bb949c7db4f70c20c3c0b687cacafed8696df
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55266761"
---
# <a name="configsections-element-for-configuration"></a><span data-ttu-id="c3362-102">\<configSections > elemento para \<configuration ></span><span class="sxs-lookup"><span data-stu-id="c3362-102">\<configSections> element for \<configuration></span></span>

<span data-ttu-id="c3362-103">Contém as declarações de namespace e a seção de configuração.</span><span class="sxs-lookup"><span data-stu-id="c3362-103">Contains configuration section and namespace declarations.</span></span>

<span data-ttu-id="c3362-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="c3362-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="c3362-105">&nbsp;&nbsp;**\<configSections>**</span><span class="sxs-lookup"><span data-stu-id="c3362-105">&nbsp;&nbsp;**\<configSections>**</span></span>

## <a name="attributes"></a><span data-ttu-id="c3362-106">Atributos</span><span class="sxs-lookup"><span data-stu-id="c3362-106">Attributes</span></span>

<span data-ttu-id="c3362-107">Nenhum</span><span class="sxs-lookup"><span data-stu-id="c3362-107">None</span></span>

## <a name="parent-element"></a><span data-ttu-id="c3362-108">Elemento pai</span><span class="sxs-lookup"><span data-stu-id="c3362-108">Parent element</span></span>

|     | <span data-ttu-id="c3362-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="c3362-109">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="c3362-110">**\<configuration>**</span><span class="sxs-lookup"><span data-stu-id="c3362-110">**\<configuration>**</span></span>](~/docs/framework/configure-apps/file-schema/configuration-element.md) | <span data-ttu-id="c3362-111">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c3362-111">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="c3362-112">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="c3362-112">Child elements</span></span>

|     | <span data-ttu-id="c3362-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="c3362-113">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="c3362-114">**\<section>**</span><span class="sxs-lookup"><span data-stu-id="c3362-114">**\<section>**</span></span>](~/docs/framework/configure-apps/file-schema/section-element.md) | <span data-ttu-id="c3362-115">Contém uma declaração de seção de configuração.</span><span class="sxs-lookup"><span data-stu-id="c3362-115">Contains a configuration section declaration.</span></span> |
| [<span data-ttu-id="c3362-116">**\<sectionGroup>**</span><span class="sxs-lookup"><span data-stu-id="c3362-116">**\<sectionGroup>**</span></span>](~/docs/framework/configure-apps/file-schema/sectiongroup-element-for-configsections.md) | <span data-ttu-id="c3362-117">Define um namespace para seções de configuração.</span><span class="sxs-lookup"><span data-stu-id="c3362-117">Defines a namespace for configuration sections.</span></span> |
| [<span data-ttu-id="c3362-118">**\<remove>**</span><span class="sxs-lookup"><span data-stu-id="c3362-118">**\<remove>**</span></span>](~/docs/framework/configure-apps/file-schema/remove-element-for-configsections.md) | <span data-ttu-id="c3362-119">Remove uma seção predefinidos ou grupo da seção.</span><span class="sxs-lookup"><span data-stu-id="c3362-119">Removes a predefined section or section group.</span></span> |
| [<span data-ttu-id="c3362-120">**\<clear>**</span><span class="sxs-lookup"><span data-stu-id="c3362-120">**\<clear>**</span></span>](~/docs/framework/configure-apps/file-schema/clear-element-for-configsections.md) | <span data-ttu-id="c3362-121">Limpa todas as seções definidas anteriormente e grupos de seções.</span><span class="sxs-lookup"><span data-stu-id="c3362-121">Clears all previously defined sections and section groups.</span></span> |

## <a name="remarks"></a><span data-ttu-id="c3362-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="c3362-122">Remarks</span></span>

<span data-ttu-id="c3362-123">Se esse elemento estiver em um arquivo de configuração, ele deve ser o primeiro elemento filho do  **\<configuration >** elemento.</span><span class="sxs-lookup"><span data-stu-id="c3362-123">If this element is in a configuration file, it must be the first child element of the **\<configuration>** element.</span></span>

## <a name="example"></a><span data-ttu-id="c3362-124">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c3362-124">Example</span></span>

<span data-ttu-id="c3362-125">O exemplo a seguir mostra como definir uma seção de configuração e definir as configurações dessa seção:</span><span class="sxs-lookup"><span data-stu-id="c3362-125">The following example shows how to define a configuration section and define settings for that section:</span></span>

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

## <a name="configuration-file"></a><span data-ttu-id="c3362-126">arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="c3362-126">Configuration file</span></span>

<span data-ttu-id="c3362-127">Esse elemento pode ser usado no arquivo de configuração do aplicativo, arquivo de configuração de máquina (*Machine. config*), e *Web. config* arquivos que não estão no nível de diretório do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c3362-127">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="c3362-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c3362-128">See also</span></span>

- [<span data-ttu-id="c3362-129">Esquema de arquivo de configuração para o .NET Framework</span><span class="sxs-lookup"><span data-stu-id="c3362-129">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
