---
title: Elemento personalizado para SingleTagSectionHandler
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName
helpviewer_keywords:
- custom element
ms.assetid: e62056c6-b351-40eb-afc0-cc13fc44e45e
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ac2d01121e81b545556fb082fa7b82c31cccf9da
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73118844"
---
# <a name="custom-element-for-singletagsectionhandler"></a><span data-ttu-id="a2715-102">Elemento personalizado para SingleTagSectionHandler</span><span class="sxs-lookup"><span data-stu-id="a2715-102">Custom element for SingleTagSectionHandler</span></span>

<span data-ttu-id="a2715-103">Define as configurações em uma seção de configuração personalizada que é definida por um \<seção > elemento e usa a classe <xref:System.Configuration.SingleTagSectionHandler>.</span><span class="sxs-lookup"><span data-stu-id="a2715-103">Defines settings in a custom configuration section that is defined by a \<section> element and uses the <xref:System.Configuration.SingleTagSectionHandler> class.</span></span>

<span data-ttu-id="a2715-104">[ **\<configuration>** ](configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="a2715-104">[**\<configuration>**](configuration-element.md) </span></span>  
<span data-ttu-id="a2715-105">&nbsp;&nbsp; *\<sectionName>*</span><span class="sxs-lookup"><span data-stu-id="a2715-105">&nbsp;&nbsp;*\<sectionName>*</span></span>

## <a name="syntax"></a><span data-ttu-id="a2715-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a2715-106">Syntax</span></span>

```xml
<sectionName key="value" key2="value2" ... />
```

## <a name="attributes"></a><span data-ttu-id="a2715-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="a2715-107">Attributes</span></span>

<span data-ttu-id="a2715-108">Atributos e valores de atributo são definidos pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="a2715-108">Attributes and attribute values are user defined.</span></span>

## <a name="parent-element"></a><span data-ttu-id="a2715-109">Elemento pai</span><span class="sxs-lookup"><span data-stu-id="a2715-109">Parent element</span></span>

|     | <span data-ttu-id="a2715-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="a2715-110">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="a2715-111"> **\<configuration>** </span><span class="sxs-lookup"><span data-stu-id="a2715-111">**\<configuration>**</span></span>](configuration-element.md) | <span data-ttu-id="a2715-112">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a2715-112">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="a2715-113">Child elements</span><span class="sxs-lookup"><span data-stu-id="a2715-113">Child elements</span></span>

<span data-ttu-id="a2715-114">Nenhum</span><span class="sxs-lookup"><span data-stu-id="a2715-114">None</span></span>

## <a name="remarks"></a><span data-ttu-id="a2715-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="a2715-115">Remarks</span></span>

<span data-ttu-id="a2715-116">O elemento **\<sectionname >** é um elemento personalizado definido por uma [**seção\<>** ](section-element.md) marca no elemento [ **\<configSections >** ](configsections-element-for-configuration.md) .</span><span class="sxs-lookup"><span data-stu-id="a2715-116">The **\<sectionName>** element is a custom element defined by a [**\<section>**](section-element.md) tag in the [**\<configSections>**](configsections-element-for-configuration.md) element.</span></span> <span data-ttu-id="a2715-117">O sistema de configuração retorna um objeto <xref:System.Collections.IDictionary> quando você chama <xref:System.Configuration.Configuration.GetSection(System.String)?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="a2715-117">The configuration system returns a <xref:System.Collections.IDictionary> object when you call <xref:System.Configuration.Configuration.GetSection(System.String)?displayProperty=nameWithType>.</span></span>

## <a name="example"></a><span data-ttu-id="a2715-118">{1&gt;Exemplo&lt;1}</span><span class="sxs-lookup"><span data-stu-id="a2715-118">Example</span></span>

<span data-ttu-id="a2715-119">O exemplo a seguir declara um elemento personalizado chamado **\<sampleSection >** que contém as configurações lidas pela classe <xref:System.Configuration.SingleTagSectionHandler>:</span><span class="sxs-lookup"><span data-stu-id="a2715-119">The following example declares a custom element called **\<sampleSection>** that contains settings read by the <xref:System.Configuration.SingleTagSectionHandler> class:</span></span>

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

## <a name="configuration-file"></a><span data-ttu-id="a2715-120">arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="a2715-120">Configuration file</span></span>

<span data-ttu-id="a2715-121">Esse elemento pode ser usado no arquivo de configuração do aplicativo, no arquivo de configuração do computador (*Machine. config*) e nos arquivos *Web. config* que não estão no nível do diretório do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a2715-121">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="a2715-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a2715-122">See also</span></span>

- [<span data-ttu-id="a2715-123">Esquema do arquivo de configuração para o .NET Framework</span><span class="sxs-lookup"><span data-stu-id="a2715-123">Configuration file schema for the .NET Framework</span></span>](index.md)
