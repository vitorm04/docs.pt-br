---
title: Elemento personalizado para SingleTagSectionHandler
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName
helpviewer_keywords:
- custom element
ms.assetid: e62056c6-b351-40eb-afc0-cc13fc44e45e
ms.openlocfilehash: 0d765a9789ad566428b1fbda6c0863b10b98c363
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/27/2020
ms.locfileid: "80345070"
---
# <a name="custom-element-for-singletagsectionhandler"></a><span data-ttu-id="7d153-102">Elemento personalizado para SingleTagSectionHandler</span><span class="sxs-lookup"><span data-stu-id="7d153-102">Custom element for SingleTagSectionHandler</span></span>

<span data-ttu-id="7d153-103">Define configurações em uma seção de \<configuração personalizada definida <xref:System.Configuration.SingleTagSectionHandler> por uma seção> elemento e usa a classe.</span><span class="sxs-lookup"><span data-stu-id="7d153-103">Defines settings in a custom configuration section that is defined by a \<section> element and uses the <xref:System.Configuration.SingleTagSectionHandler> class.</span></span>

<span data-ttu-id="7d153-104">configuração &nbsp; &nbsp; [\*\* \<>\*\*](configuration-element.md) \* \<seçãoNome>\*</span><span class="sxs-lookup"><span data-stu-id="7d153-104">[**\<configuration>**](configuration-element.md) &nbsp;&nbsp;*\<sectionName>*</span></span>

## <a name="syntax"></a><span data-ttu-id="7d153-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7d153-105">Syntax</span></span>

```xml
<sectionName key="value" key2="value2" />
```

## <a name="attributes"></a><span data-ttu-id="7d153-106">Atributos</span><span class="sxs-lookup"><span data-stu-id="7d153-106">Attributes</span></span>

<span data-ttu-id="7d153-107">Atributos e valores de atributos são definidos pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="7d153-107">Attributes and attribute values are user defined.</span></span>

## <a name="parent-element"></a><span data-ttu-id="7d153-108">Elemento pai</span><span class="sxs-lookup"><span data-stu-id="7d153-108">Parent element</span></span>

|     | <span data-ttu-id="7d153-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="7d153-109">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="7d153-110">**\<>de configuração**</span><span class="sxs-lookup"><span data-stu-id="7d153-110">**\<configuration>**</span></span>](configuration-element.md) | <span data-ttu-id="7d153-111">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="7d153-111">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="7d153-112">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="7d153-112">Child elements</span></span>

<span data-ttu-id="7d153-113">Nenhum</span><span class="sxs-lookup"><span data-stu-id="7d153-113">None</span></span>

## <a name="remarks"></a><span data-ttu-id="7d153-114">Comentários</span><span class="sxs-lookup"><span data-stu-id="7d153-114">Remarks</span></span>

<span data-ttu-id="7d153-115">O \*\* \<\*\* elemento sectionName>é um elemento personalizado definido por uma [\*\* \<seção>\*\*](section-element.md) tag no [\*\* \<elemento>configSeções.\*\*](configsections-element-for-configuration.md)</span><span class="sxs-lookup"><span data-stu-id="7d153-115">The **\<sectionName>** element is a custom element defined by a [**\<section>**](section-element.md) tag in the [**\<configSections>**](configsections-element-for-configuration.md) element.</span></span> <span data-ttu-id="7d153-116">O sistema de <xref:System.Collections.IDictionary> configuração <xref:System.Configuration.Configuration.GetSection(System.String)?displayProperty=nameWithType>retorna um objeto quando você chama .</span><span class="sxs-lookup"><span data-stu-id="7d153-116">The configuration system returns a <xref:System.Collections.IDictionary> object when you call <xref:System.Configuration.Configuration.GetSection(System.String)?displayProperty=nameWithType>.</span></span>

## <a name="example"></a><span data-ttu-id="7d153-117">Exemplo</span><span class="sxs-lookup"><span data-stu-id="7d153-117">Example</span></span>

<span data-ttu-id="7d153-118">O exemplo a seguir declara um elemento personalizado chamado <xref:System.Configuration.SingleTagSectionHandler> \*\* \<sampleSection>\*\* que contém configurações lidas pela classe:</span><span class="sxs-lookup"><span data-stu-id="7d153-118">The following example declares a custom element called **\<sampleSection>** that contains settings read by the <xref:System.Configuration.SingleTagSectionHandler> class:</span></span>

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

## <a name="configuration-file"></a><span data-ttu-id="7d153-119">Arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="7d153-119">Configuration file</span></span>

<span data-ttu-id="7d153-120">Esse elemento pode ser usado no arquivo de configuração do aplicativo, no arquivo de configuração da máquina *(Machine.config)* e nos arquivos *Web.config* que não estão no nível do diretório do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="7d153-120">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="7d153-121">Confira também</span><span class="sxs-lookup"><span data-stu-id="7d153-121">See also</span></span>

- [<span data-ttu-id="7d153-122">Esquema de arquivo de configuração para o Framework .NET</span><span class="sxs-lookup"><span data-stu-id="7d153-122">Configuration file schema for the .NET Framework</span></span>](index.md)
