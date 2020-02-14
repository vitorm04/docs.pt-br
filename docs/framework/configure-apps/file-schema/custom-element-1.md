---
title: Elemento personalizado para SingleTagSectionHandler
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName
helpviewer_keywords:
- custom element
ms.assetid: e62056c6-b351-40eb-afc0-cc13fc44e45e
ms.openlocfilehash: 1d0431085a04d3fb817dfe0883779acc4d693084
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77214782"
---
# <a name="custom-element-for-singletagsectionhandler"></a><span data-ttu-id="53a7c-102">Elemento personalizado para SingleTagSectionHandler</span><span class="sxs-lookup"><span data-stu-id="53a7c-102">Custom element for SingleTagSectionHandler</span></span>

<span data-ttu-id="53a7c-103">Define as configurações em uma seção de configuração personalizada que é definida por um \<seção > elemento e usa a classe <xref:System.Configuration.SingleTagSectionHandler>.</span><span class="sxs-lookup"><span data-stu-id="53a7c-103">Defines settings in a custom configuration section that is defined by a \<section> element and uses the <xref:System.Configuration.SingleTagSectionHandler> class.</span></span>

<span data-ttu-id="53a7c-104">[ **\<configuration>** ](configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="53a7c-104">[**\<configuration>**](configuration-element.md) </span></span>  
<span data-ttu-id="53a7c-105">&nbsp;&nbsp; *\<sectionname >*</span><span class="sxs-lookup"><span data-stu-id="53a7c-105">&nbsp;&nbsp;*\<sectionName>*</span></span>

## <a name="syntax"></a><span data-ttu-id="53a7c-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="53a7c-106">Syntax</span></span>

```xml
<sectionName key="value" key2="value2" ... />
```

## <a name="attributes"></a><span data-ttu-id="53a7c-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="53a7c-107">Attributes</span></span>

<span data-ttu-id="53a7c-108">Atributos e valores de atributo são definidos pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="53a7c-108">Attributes and attribute values are user defined.</span></span>

## <a name="parent-element"></a><span data-ttu-id="53a7c-109">Elemento pai</span><span class="sxs-lookup"><span data-stu-id="53a7c-109">Parent element</span></span>

|     | <span data-ttu-id="53a7c-110">DESCRIÇÃO</span><span class="sxs-lookup"><span data-stu-id="53a7c-110">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="53a7c-111"> **\<configuration>** </span><span class="sxs-lookup"><span data-stu-id="53a7c-111">**\<configuration>**</span></span>](configuration-element.md) | <span data-ttu-id="53a7c-112">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="53a7c-112">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="53a7c-113">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="53a7c-113">Child elements</span></span>

<span data-ttu-id="53a7c-114">Nenhum</span><span class="sxs-lookup"><span data-stu-id="53a7c-114">None</span></span>

## <a name="remarks"></a><span data-ttu-id="53a7c-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="53a7c-115">Remarks</span></span>

<span data-ttu-id="53a7c-116">O elemento **\<sectionname >** é um elemento personalizado definido por uma [**seção\<>** ](section-element.md) marca no elemento [ **\<configSections >** ](configsections-element-for-configuration.md) .</span><span class="sxs-lookup"><span data-stu-id="53a7c-116">The **\<sectionName>** element is a custom element defined by a [**\<section>**](section-element.md) tag in the [**\<configSections>**](configsections-element-for-configuration.md) element.</span></span> <span data-ttu-id="53a7c-117">O sistema de configuração retorna um objeto <xref:System.Collections.IDictionary> quando você chama <xref:System.Configuration.Configuration.GetSection(System.String)?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="53a7c-117">The configuration system returns a <xref:System.Collections.IDictionary> object when you call <xref:System.Configuration.Configuration.GetSection(System.String)?displayProperty=nameWithType>.</span></span>

## <a name="example"></a><span data-ttu-id="53a7c-118">Exemplo</span><span class="sxs-lookup"><span data-stu-id="53a7c-118">Example</span></span>

<span data-ttu-id="53a7c-119">O exemplo a seguir declara um elemento personalizado chamado **\<sampleSection >** que contém as configurações lidas pela classe <xref:System.Configuration.SingleTagSectionHandler>:</span><span class="sxs-lookup"><span data-stu-id="53a7c-119">The following example declares a custom element called **\<sampleSection>** that contains settings read by the <xref:System.Configuration.SingleTagSectionHandler> class:</span></span>

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

## <a name="configuration-file"></a><span data-ttu-id="53a7c-120">Arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="53a7c-120">Configuration file</span></span>

<span data-ttu-id="53a7c-121">Esse elemento pode ser usado no arquivo de configuração do aplicativo, no arquivo de configuração do computador (*Machine. config*) e nos arquivos *Web. config* que não estão no nível do diretório do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="53a7c-121">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="53a7c-122">Confira também</span><span class="sxs-lookup"><span data-stu-id="53a7c-122">See also</span></span>

- [<span data-ttu-id="53a7c-123">Esquema do arquivo de configuração para o .NET Framework</span><span class="sxs-lookup"><span data-stu-id="53a7c-123">Configuration file schema for the .NET Framework</span></span>](index.md)
