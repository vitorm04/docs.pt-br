---
title: Elemento personalizado para SingleTagSectionHandler
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName
helpviewer_keywords:
- custom element
ms.assetid: e62056c6-b351-40eb-afc0-cc13fc44e45e
author: rpetrusha
ms.author: mairaw
ms.openlocfilehash: 8fae3673fe72d036802cb1a8366aaa2430c38884
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69927495"
---
# <a name="custom-element-for-singletagsectionhandler"></a><span data-ttu-id="5dfae-102">Elemento personalizado para SingleTagSectionHandler</span><span class="sxs-lookup"><span data-stu-id="5dfae-102">Custom element for SingleTagSectionHandler</span></span>

<span data-ttu-id="5dfae-103">Define as configurações em uma seção de configuração personalizada que é definida \<por uma seção > elemento e <xref:System.Configuration.SingleTagSectionHandler> usa a classe.</span><span class="sxs-lookup"><span data-stu-id="5dfae-103">Defines settings in a custom configuration section that is defined by a \<section> element and uses the <xref:System.Configuration.SingleTagSectionHandler> class.</span></span>

<span data-ttu-id="5dfae-104">[ **\<configuration>** ](configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="5dfae-104">[**\<configuration>**](configuration-element.md) </span></span>  
<span data-ttu-id="5dfae-105">&nbsp;&nbsp; *\<sectionName>*</span><span class="sxs-lookup"><span data-stu-id="5dfae-105">&nbsp;&nbsp;*\<sectionName>*</span></span>

## <a name="syntax"></a><span data-ttu-id="5dfae-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5dfae-106">Syntax</span></span>

```xml
<sectionName key="value" key2="value2" ... />
```

## <a name="attributes"></a><span data-ttu-id="5dfae-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="5dfae-107">Attributes</span></span>

<span data-ttu-id="5dfae-108">Atributos e valores de atributo são definidos pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="5dfae-108">Attributes and attribute values are user defined.</span></span>

## <a name="parent-element"></a><span data-ttu-id="5dfae-109">Elemento pai</span><span class="sxs-lookup"><span data-stu-id="5dfae-109">Parent element</span></span>

|     | <span data-ttu-id="5dfae-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="5dfae-110">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="5dfae-111"> **\<configuration>** </span><span class="sxs-lookup"><span data-stu-id="5dfae-111">**\<configuration>**</span></span>](configuration-element.md) | <span data-ttu-id="5dfae-112">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="5dfae-112">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="5dfae-113">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="5dfae-113">Child elements</span></span>

<span data-ttu-id="5dfae-114">Nenhum</span><span class="sxs-lookup"><span data-stu-id="5dfae-114">None</span></span>

## <a name="remarks"></a><span data-ttu-id="5dfae-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="5dfae-115">Remarks</span></span>

<span data-ttu-id="5dfae-116">[ **\<** ](configsections-element-for-configuration.md)  **O\<elemento SectionName >** é um elemento personalizado definido por uma [ **\<seção >** ](section-element.md) tag no elemento configSections >.</span><span class="sxs-lookup"><span data-stu-id="5dfae-116">The **\<sectionName>** element is a custom element defined by a [**\<section>**](section-element.md) tag in the [**\<configSections>**](configsections-element-for-configuration.md) element.</span></span> <span data-ttu-id="5dfae-117">O sistema de configuração retorna <xref:System.Collections.IDictionary> um objeto quando você <xref:System.Configuration.Configuration.GetSection(System.String)?displayProperty=nameWithType>chama.</span><span class="sxs-lookup"><span data-stu-id="5dfae-117">The configuration system returns a <xref:System.Collections.IDictionary> object when you call <xref:System.Configuration.Configuration.GetSection(System.String)?displayProperty=nameWithType>.</span></span>

## <a name="example"></a><span data-ttu-id="5dfae-118">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5dfae-118">Example</span></span>

<span data-ttu-id="5dfae-119">O exemplo a seguir declara um elemento personalizado chamado  **\<sampleSection >** que contém <xref:System.Configuration.SingleTagSectionHandler> as configurações lidas pela classe:</span><span class="sxs-lookup"><span data-stu-id="5dfae-119">The following example declares a custom element called **\<sampleSection>** that contains settings read by the <xref:System.Configuration.SingleTagSectionHandler> class:</span></span>

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

## <a name="configuration-file"></a><span data-ttu-id="5dfae-120">arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="5dfae-120">Configuration file</span></span>

<span data-ttu-id="5dfae-121">Esse elemento pode ser usado no arquivo de configuração do aplicativo, no arquivo de configuração do computador (*Machine. config*) e nos arquivos *Web. config* que não estão no nível do diretório do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="5dfae-121">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="5dfae-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5dfae-122">See also</span></span>

- [<span data-ttu-id="5dfae-123">Esquema do arquivo de configuração para o .NET Framework</span><span class="sxs-lookup"><span data-stu-id="5dfae-123">Configuration file schema for the .NET Framework</span></span>](index.md)
