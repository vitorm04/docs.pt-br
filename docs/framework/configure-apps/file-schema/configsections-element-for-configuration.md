---
title: Elemento <configSections> para <configuration>
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections
helpviewer_keywords:
- configSections Element
- <configSections> Element
ms.assetid: 9f963c1b-dc3f-4220-a8b6-2dd7a5a8e039
author: rpetrusha
ms.author: mairaw
ms.openlocfilehash: 31b53837e24029fc7ff0b576d95c0213041a434e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69927664"
---
# <a name="configsections-element-for-configuration"></a><span data-ttu-id="c9d03-102">\<configSections > elemento para \<a configuração ></span><span class="sxs-lookup"><span data-stu-id="c9d03-102">\<configSections> element for \<configuration></span></span>

<span data-ttu-id="c9d03-103">Contém as declarações de namespace e seção de configuração.</span><span class="sxs-lookup"><span data-stu-id="c9d03-103">Contains configuration section and namespace declarations.</span></span>

<span data-ttu-id="c9d03-104">[ **\<configuration>** ](configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="c9d03-104">[**\<configuration>**](configuration-element.md) </span></span>  
<span data-ttu-id="c9d03-105">&nbsp;&nbsp; **\<configSections>**</span><span class="sxs-lookup"><span data-stu-id="c9d03-105">&nbsp;&nbsp;**\<configSections>**</span></span>

## <a name="attributes"></a><span data-ttu-id="c9d03-106">Atributos</span><span class="sxs-lookup"><span data-stu-id="c9d03-106">Attributes</span></span>

<span data-ttu-id="c9d03-107">Nenhum</span><span class="sxs-lookup"><span data-stu-id="c9d03-107">None</span></span>

## <a name="parent-element"></a><span data-ttu-id="c9d03-108">Elemento pai</span><span class="sxs-lookup"><span data-stu-id="c9d03-108">Parent element</span></span>

|     | <span data-ttu-id="c9d03-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="c9d03-109">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="c9d03-110"> **\<configuration>** </span><span class="sxs-lookup"><span data-stu-id="c9d03-110">**\<configuration>**</span></span>](configuration-element.md) | <span data-ttu-id="c9d03-111">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c9d03-111">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="c9d03-112">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="c9d03-112">Child elements</span></span>

|     | <span data-ttu-id="c9d03-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="c9d03-113">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="c9d03-114"> **\<> da seção**</span><span class="sxs-lookup"><span data-stu-id="c9d03-114">**\<section>**</span></span>](section-element.md) | <span data-ttu-id="c9d03-115">Contém uma declaração de seção de configuração.</span><span class="sxs-lookup"><span data-stu-id="c9d03-115">Contains a configuration section declaration.</span></span> |
| [<span data-ttu-id="c9d03-116"> **\<sectionGroup>** </span><span class="sxs-lookup"><span data-stu-id="c9d03-116">**\<sectionGroup>**</span></span>](sectiongroup-element-for-configsections.md) | <span data-ttu-id="c9d03-117">Define um namespace para seções de configuração.</span><span class="sxs-lookup"><span data-stu-id="c9d03-117">Defines a namespace for configuration sections.</span></span> |
| [<span data-ttu-id="c9d03-118"> **\<remove>** </span><span class="sxs-lookup"><span data-stu-id="c9d03-118">**\<remove>**</span></span>](remove-element-for-configsections.md) | <span data-ttu-id="c9d03-119">Remove uma seção ou um grupo de seções predefinido.</span><span class="sxs-lookup"><span data-stu-id="c9d03-119">Removes a predefined section or section group.</span></span> |
| [<span data-ttu-id="c9d03-120"> **\<clear>** </span><span class="sxs-lookup"><span data-stu-id="c9d03-120">**\<clear>**</span></span>](clear-element-for-configsections.md) | <span data-ttu-id="c9d03-121">Limpa todas as seções e grupos de seções definidos anteriormente.</span><span class="sxs-lookup"><span data-stu-id="c9d03-121">Clears all previously defined sections and section groups.</span></span> |

## <a name="remarks"></a><span data-ttu-id="c9d03-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="c9d03-122">Remarks</span></span>

<span data-ttu-id="c9d03-123">Se esse elemento estiver em um arquivo de configuração, ele deverá ser o primeiro elemento filho do  **\<elemento Configuration >** .</span><span class="sxs-lookup"><span data-stu-id="c9d03-123">If this element is in a configuration file, it must be the first child element of the **\<configuration>** element.</span></span>

## <a name="example"></a><span data-ttu-id="c9d03-124">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c9d03-124">Example</span></span>

<span data-ttu-id="c9d03-125">O exemplo a seguir mostra como definir uma seção de configuração e definir as configurações para essa seção:</span><span class="sxs-lookup"><span data-stu-id="c9d03-125">The following example shows how to define a configuration section and define settings for that section:</span></span>

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

## <a name="configuration-file"></a><span data-ttu-id="c9d03-126">arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="c9d03-126">Configuration file</span></span>

<span data-ttu-id="c9d03-127">Esse elemento pode ser usado no arquivo de configuração do aplicativo, no arquivo de configuração do computador (*Machine. config*) e nos arquivos *Web. config* que não estão no nível do diretório do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c9d03-127">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="c9d03-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c9d03-128">See also</span></span>

- [<span data-ttu-id="c9d03-129">Esquema do arquivo de configuração para o .NET Framework</span><span class="sxs-lookup"><span data-stu-id="c9d03-129">Configuration file schema for the .NET Framework</span></span>](index.md)
