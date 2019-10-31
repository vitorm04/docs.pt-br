---
title: Elemento personalizado para NameValueSectionHandler e DictionarySectionHandler
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName
helpviewer_keywords:
- custom element
ms.assetid: 2303031f-4c1d-4df4-bca1-e9bd96ca40dc
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d73c07d58bb226346cb99a1fe50b12bb0e7e746e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73118538"
---
# <a name="custom-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a><span data-ttu-id="9ca16-102">Elemento personalizado para NameValueSectionHandler e DictionarySectionHandler</span><span class="sxs-lookup"><span data-stu-id="9ca16-102">Custom element for NameValueSectionHandler and DictionarySectionHandler</span></span>

<span data-ttu-id="9ca16-103">Define as configurações para seções de configuração personalizadas que usam as classes <xref:System.Configuration.NameValueSectionHandler> e <xref:System.Configuration.DictionarySectionHandler>.</span><span class="sxs-lookup"><span data-stu-id="9ca16-103">Defines settings for custom configuration sections that use the <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler> classes.</span></span>

<span data-ttu-id="9ca16-104">[ **\<configuration>** ](configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="9ca16-104">[**\<configuration>**](configuration-element.md)</span></span>\
<span data-ttu-id="9ca16-105">&nbsp;&nbsp; **\<sectionname >**</span><span class="sxs-lookup"><span data-stu-id="9ca16-105">&nbsp;&nbsp;**\<sectionName>**</span></span>

## <a name="attributes"></a><span data-ttu-id="9ca16-106">Atributos</span><span class="sxs-lookup"><span data-stu-id="9ca16-106">Attributes</span></span>

<span data-ttu-id="9ca16-107">Nenhum</span><span class="sxs-lookup"><span data-stu-id="9ca16-107">None</span></span>

## <a name="parent-element"></a><span data-ttu-id="9ca16-108">Elemento pai</span><span class="sxs-lookup"><span data-stu-id="9ca16-108">Parent element</span></span>

|     | <span data-ttu-id="9ca16-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="9ca16-109">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="9ca16-110"> **\<configuration>** </span><span class="sxs-lookup"><span data-stu-id="9ca16-110">**\<configuration>**</span></span>](configuration-element.md) | <span data-ttu-id="9ca16-111">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9ca16-111">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="9ca16-112">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="9ca16-112">Child elements</span></span>

|     | <span data-ttu-id="9ca16-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="9ca16-113">Description</span></span> |
| --- | ----------- |
| <span data-ttu-id="9ca16-114">[ **\<adicionar >** ](add-element-for-custom-2.md) para <xref:System.Configuration.NameValueSectionHandler> e <xref:System.Configuration.DictionarySectionHandler></span><span class="sxs-lookup"><span data-stu-id="9ca16-114">[**\<add>**](add-element-for-custom-2.md) for <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler></span></span>  | <span data-ttu-id="9ca16-115">Adiciona configurações de aplicativo personalizadas.</span><span class="sxs-lookup"><span data-stu-id="9ca16-115">Adds custom application settings.</span></span> |
| <span data-ttu-id="9ca16-116">[ **\<remover >** ](remove-element-for-custom-2.md) para <xref:System.Configuration.NameValueSectionHandler> e <xref:System.Configuration.DictionarySectionHandler></span><span class="sxs-lookup"><span data-stu-id="9ca16-116">[**\<remove>**](remove-element-for-custom-2.md) for <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler></span></span> | <span data-ttu-id="9ca16-117">Remove uma configuração definida anteriormente.</span><span class="sxs-lookup"><span data-stu-id="9ca16-117">Removes a previously defined setting.</span></span> |
| <span data-ttu-id="9ca16-118">[ **\<limpar >** ](clear-element-for-custom-2.md) para <xref:System.Configuration.NameValueSectionHandler> e <xref:System.Configuration.DictionarySectionHandler></span><span class="sxs-lookup"><span data-stu-id="9ca16-118">[**\<clear>**](clear-element-for-custom-2.md) for <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler></span></span> | <span data-ttu-id="9ca16-119">Limpa todas as configurações definidas anteriormente em uma seção.</span><span class="sxs-lookup"><span data-stu-id="9ca16-119">Clears all previously defined settings in a section.</span></span> |

## <a name="remarks"></a><span data-ttu-id="9ca16-120">Comentários</span><span class="sxs-lookup"><span data-stu-id="9ca16-120">Remarks</span></span>

<span data-ttu-id="9ca16-121">O elemento **\<sectionname >** é um elemento personalizado definido por uma **seção\<** marca no elemento **\<configSections >** .</span><span class="sxs-lookup"><span data-stu-id="9ca16-121">The **\<sectionName>** element is a custom element defined by a **\<section>** tag in the **\<configSections>** element.</span></span>

<span data-ttu-id="9ca16-122">A tabela a seguir mostra o tipo de objeto que o método ConfigurationSettings. GetConfig retorna para cada manipulador de seção de configuração:</span><span class="sxs-lookup"><span data-stu-id="9ca16-122">The following table shows the type of object the ConfigurationSettings.GetConfig method returns for each configuration section handler:</span></span>

| <span data-ttu-id="9ca16-123">Manipulador da seção de configuração</span><span class="sxs-lookup"><span data-stu-id="9ca16-123">Configuration section handler</span></span>                        | <span data-ttu-id="9ca16-124">Tipo de retorno</span><span class="sxs-lookup"><span data-stu-id="9ca16-124">Return type</span></span>                                                |
| ---------------------------------------------------- | ---------------------------------------------------------- |
| <xref:System.Configuration.NameValueSectionHandler>  | <xref:System.Collections.Specialized.NameValueCollection>  |
| <xref:System.Configuration.DictionarySectionHandler> | <xref:System.Collections.IDictionary>                      |

## <a name="example"></a><span data-ttu-id="9ca16-125">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9ca16-125">Example</span></span>

<span data-ttu-id="9ca16-126">O exemplo a seguir mostra como declarar seções que usam as classes <xref:System.Configuration.DictionarySectionHandler> e <xref:System.Configuration.NameValueSectionHandler>.</span><span class="sxs-lookup"><span data-stu-id="9ca16-126">The following example shows how to declare sections that use the <xref:System.Configuration.DictionarySectionHandler> and <xref:System.Configuration.NameValueSectionHandler> classes.</span></span>

<span data-ttu-id="9ca16-127">O primeiro elemento personalizado é **\<dictionarySample >** , que contém as configurações lidas pela classe <xref:System.Configuration.DictionarySectionHandler> no assembly `System.dll`.</span><span class="sxs-lookup"><span data-stu-id="9ca16-127">The first custom element is **\<dictionarySample>**, which contains settings read by the <xref:System.Configuration.DictionarySectionHandler> class in the `System.dll` assembly.</span></span> <span data-ttu-id="9ca16-128">O segundo elemento personalizado é **\<> myseção**, que contém as configurações lidas pela classe <xref:System.Configuration.NameValueSectionHandler> no assembly `System.dll`.</span><span class="sxs-lookup"><span data-stu-id="9ca16-128">The second custom element is **\<mySection>**, which contains settings read by the <xref:System.Configuration.NameValueSectionHandler> class in the `System.dll` assembly.</span></span>

```xml
<configuration>
  <configSections>
    <section name="dictionarySample" type="System.Configuration.DictionarySectionHandler,System" />
    <sectionGroup name="mySectionGroup">
      <section name="mySection" type="System.Configuration.NameValueSectionHandler,System" />
    </sectionGroup>
  </configSections>
  <dictionarySample>
    <add key="myKey" value="myValue" />
  </dictionarySample>
  <mySectionGroup>
    <mySection>
      <add key="key1" value="value1" />
    </mySection>
  </mySectionGroup>
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="9ca16-129">arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="9ca16-129">Configuration file</span></span>

<span data-ttu-id="9ca16-130">Esse elemento pode ser usado no arquivo de configuração do aplicativo, no arquivo de configuração do computador (*Machine. config*) e nos arquivos *Web. config* que não estão no nível do diretório do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="9ca16-130">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="9ca16-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9ca16-131">See also</span></span>

- [<span data-ttu-id="9ca16-132">Esquema do arquivo de configuração para o .NET Framework</span><span class="sxs-lookup"><span data-stu-id="9ca16-132">Configuration file schema for the .NET Framework</span></span>](index.md)
