---
title: Elemento personalizado para SingleTagSectionHandler
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName
helpviewer_keywords:
- custom element
ms.assetid: e62056c6-b351-40eb-afc0-cc13fc44e45e
ms.openlocfilehash: a40f35838655f6021af0b2e966335803ec8c16b4
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "80635393"
---
# <a name="custom-element-for-singletagsectionhandler"></a><span data-ttu-id="6957b-102">Elemento personalizado para SingleTagSectionHandler</span><span class="sxs-lookup"><span data-stu-id="6957b-102">Custom element for SingleTagSectionHandler</span></span>

<span data-ttu-id="6957b-103">Define as configurações em uma seção de configuração personalizada que é definida por um \<section> elemento e usa a <xref:System.Configuration.SingleTagSectionHandler> classe.</span><span class="sxs-lookup"><span data-stu-id="6957b-103">Defines settings in a custom configuration section that is defined by a \<section> element and uses the <xref:System.Configuration.SingleTagSectionHandler> class.</span></span>

<span data-ttu-id="6957b-104">[**\<configuration>**](configuration-element.md) &nbsp;&nbsp;*\<sectionName>*</span><span class="sxs-lookup"><span data-stu-id="6957b-104">[**\<configuration>**](configuration-element.md) &nbsp;&nbsp;*\<sectionName>*</span></span>

## <a name="syntax"></a><span data-ttu-id="6957b-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6957b-105">Syntax</span></span>

```xml
<sectionName key="value" key2="value2" />
```

## <a name="attributes"></a><span data-ttu-id="6957b-106">Atributos</span><span class="sxs-lookup"><span data-stu-id="6957b-106">Attributes</span></span>

<span data-ttu-id="6957b-107">Atributos e valores de atributo são definidos pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="6957b-107">Attributes and attribute values are user defined.</span></span>

## <a name="parent-element"></a><span data-ttu-id="6957b-108">Elemento pai</span><span class="sxs-lookup"><span data-stu-id="6957b-108">Parent element</span></span>

|     | <span data-ttu-id="6957b-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="6957b-109">Description</span></span> |
| --- | ----------- |
| [**\<configuration>**](configuration-element.md) | <span data-ttu-id="6957b-110">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6957b-110">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="6957b-111">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="6957b-111">Child elements</span></span>

<span data-ttu-id="6957b-112">Nenhum</span><span class="sxs-lookup"><span data-stu-id="6957b-112">None</span></span>

## <a name="remarks"></a><span data-ttu-id="6957b-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="6957b-113">Remarks</span></span>

<span data-ttu-id="6957b-114">O **\<sectionName>** elemento é um elemento personalizado definido por uma [**\<section>**](section-element.md) marca no [**\<configSections>**](configsections-element-for-configuration.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="6957b-114">The **\<sectionName>** element is a custom element defined by a [**\<section>**](section-element.md) tag in the [**\<configSections>**](configsections-element-for-configuration.md) element.</span></span> <span data-ttu-id="6957b-115">O sistema de configuração retorna um <xref:System.Collections.IDictionary> objeto quando você chama <xref:System.Configuration.Configuration.GetSection(System.String)?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="6957b-115">The configuration system returns a <xref:System.Collections.IDictionary> object when you call <xref:System.Configuration.Configuration.GetSection(System.String)?displayProperty=nameWithType>.</span></span>

## <a name="example"></a><span data-ttu-id="6957b-116">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6957b-116">Example</span></span>

<span data-ttu-id="6957b-117">O exemplo a seguir declara um elemento personalizado chamado **\<sampleSection>** que contém as configurações lidas pela <xref:System.Configuration.SingleTagSectionHandler> classe:</span><span class="sxs-lookup"><span data-stu-id="6957b-117">The following example declares a custom element called **\<sampleSection>** that contains settings read by the <xref:System.Configuration.SingleTagSectionHandler> class:</span></span>

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

## <a name="configuration-file"></a><span data-ttu-id="6957b-118">Arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="6957b-118">Configuration file</span></span>

<span data-ttu-id="6957b-119">Esse elemento pode ser usado no arquivo de configuração do aplicativo, no arquivo de configuração do computador (*Machine. config*) e nos arquivos *Web. config* que não estão no nível do diretório do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="6957b-119">This element can be used in the application configuration file, the machine configuration file (*Machine.config*), and *Web.config* files that aren't at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="6957b-120">Confira também</span><span class="sxs-lookup"><span data-stu-id="6957b-120">See also</span></span>

- [<span data-ttu-id="6957b-121">Esquema do arquivo de configuração para o .NET Framework</span><span class="sxs-lookup"><span data-stu-id="6957b-121">Configuration file schema for the .NET Framework</span></span>](index.md)
