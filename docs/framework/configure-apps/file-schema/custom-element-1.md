---
title: Elemento personalizado para SingleTagSectionHandler
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName
helpviewer_keywords:
- custom element
ms.assetid: e62056c6-b351-40eb-afc0-cc13fc44e45e
author: guardrex
ms.author: mairaw
ms.openlocfilehash: bfc2a916e37ac27d45746eb268912b3752f4d80f
ms.sourcegitcommit: 7156c0b9e4ce4ce5ecf48ce3d925403b638b680c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/26/2019
ms.locfileid: "58464431"
---
# <a name="custom-element-for-singletagsectionhandler"></a><span data-ttu-id="a3987-102">Elemento personalizado para SingleTagSectionHandler</span><span class="sxs-lookup"><span data-stu-id="a3987-102">Custom element for SingleTagSectionHandler</span></span>

<span data-ttu-id="a3987-103">Define as configurações em uma seção de configuração personalizada que é definida por uma \<seção > elemento e usa o <xref:System.Configuration.SingleTagSectionHandler> classe.</span><span class="sxs-lookup"><span data-stu-id="a3987-103">Defines settings in a custom configuration section that is defined by a \<section> element and uses the <xref:System.Configuration.SingleTagSectionHandler> class.</span></span>

<span data-ttu-id="a3987-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="a3987-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="a3987-105">&nbsp;&nbsp;*\<sectionName>*</span><span class="sxs-lookup"><span data-stu-id="a3987-105">&nbsp;&nbsp;*\<sectionName>*</span></span>

## <a name="syntax"></a><span data-ttu-id="a3987-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a3987-106">Syntax</span></span>

```xml
<sectionName key="value" key2="value2" ... />
```

## <a name="attributes"></a><span data-ttu-id="a3987-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="a3987-107">Attributes</span></span>

<span data-ttu-id="a3987-108">Atributos e valores de atributo são definidos pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="a3987-108">Attributes and attribute values are user defined.</span></span>

## <a name="parent-element"></a><span data-ttu-id="a3987-109">Elemento pai</span><span class="sxs-lookup"><span data-stu-id="a3987-109">Parent element</span></span>

|     | <span data-ttu-id="a3987-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="a3987-110">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="a3987-111">**\<configuration>**</span><span class="sxs-lookup"><span data-stu-id="a3987-111">**\<configuration>**</span></span>](~/docs/framework/configure-apps/file-schema/configuration-element.md) | <span data-ttu-id="a3987-112">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a3987-112">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="a3987-113">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="a3987-113">Child elements</span></span>

<span data-ttu-id="a3987-114">Nenhum</span><span class="sxs-lookup"><span data-stu-id="a3987-114">None</span></span>

## <a name="remarks"></a><span data-ttu-id="a3987-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="a3987-115">Remarks</span></span>

<span data-ttu-id="a3987-116">O  **\<sectionName >** é um elemento personalizado definido por uma [  **\<seção >** ](~/docs/framework/configure-apps/file-schema/section-element.md) marcar no [  **\<configSections >** ](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="a3987-116">The **\<sectionName>** element is a custom element defined by a [**\<section>**](~/docs/framework/configure-apps/file-schema/section-element.md) tag in the [**\<configSections>**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) element.</span></span> <span data-ttu-id="a3987-117">O sistema de configuração retorna um <xref:System.Collections.IDictionary> do objeto quando você chama <xref:System.Configuration.Configuration.GetSection(System.String)?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="a3987-117">The configuration system returns a <xref:System.Collections.IDictionary> object when you call <xref:System.Configuration.Configuration.GetSection(System.String)?displayProperty=nameWithType>.</span></span>

## <a name="example"></a><span data-ttu-id="a3987-118">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a3987-118">Example</span></span>

<span data-ttu-id="a3987-119">O exemplo a seguir declara um elemento personalizado chamado  **\<sampleSection >** que contém as configurações lidas pelo <xref:System.Configuration.SingleTagSectionHandler> classe:</span><span class="sxs-lookup"><span data-stu-id="a3987-119">The following example declares a custom element called **\<sampleSection>** that contains settings read by the <xref:System.Configuration.SingleTagSectionHandler> class:</span></span>

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

## <a name="configuration-file"></a><span data-ttu-id="a3987-120">arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="a3987-120">Configuration file</span></span>

<span data-ttu-id="a3987-121">Esse elemento pode ser usado no arquivo de configuração do aplicativo, arquivo de configuração de máquina (*Machine. config*), e *Web. config* arquivos que não estão no nível de diretório do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a3987-121">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="a3987-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a3987-122">See also</span></span>

- [<span data-ttu-id="a3987-123">Esquema de arquivo de configuração para o .NET Framework</span><span class="sxs-lookup"><span data-stu-id="a3987-123">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
