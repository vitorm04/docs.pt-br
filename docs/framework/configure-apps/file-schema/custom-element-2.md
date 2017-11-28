---
title: Elemento personalizado para NameValueSectionHandler e DictionarySectionHandler
ms.date: 05/01/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: article
f1_keywords: http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName
helpviewer_keywords: custom element
ms.assetid: 2303031f-4c1d-4df4-bca1-e9bd96ca40dc
author: guardrex
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: a9722493ec62952d7cbc07d478687b8495d24f95
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="custom-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a><span data-ttu-id="d8bd7-102">Elemento personalizado para NameValueSectionHandler e DictionarySectionHandler</span><span class="sxs-lookup"><span data-stu-id="d8bd7-102">Custom element for NameValueSectionHandler and DictionarySectionHandler</span></span>

<span data-ttu-id="d8bd7-103">Define as configurações para as seções de configuração personalizadas que usam o <xref:System.Configuration.NameValueSectionHandler> e <xref:System.Configuration.DictionarySectionHandler> classes.</span><span class="sxs-lookup"><span data-stu-id="d8bd7-103">Defines settings for custom configuration sections that use the <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler> classes.</span></span>

<span data-ttu-id="d8bd7-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="d8bd7-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="d8bd7-105">&nbsp;&nbsp;**\<sectionName >**</span><span class="sxs-lookup"><span data-stu-id="d8bd7-105">&nbsp;&nbsp;**\<sectionName>**</span></span>

## <a name="attributes"></a><span data-ttu-id="d8bd7-106">Atributos</span><span class="sxs-lookup"><span data-stu-id="d8bd7-106">Attributes</span></span>

<span data-ttu-id="d8bd7-107">Nenhum</span><span class="sxs-lookup"><span data-stu-id="d8bd7-107">None</span></span>

## <a name="parent-element"></a><span data-ttu-id="d8bd7-108">Elemento pai</span><span class="sxs-lookup"><span data-stu-id="d8bd7-108">Parent element</span></span>

|     | <span data-ttu-id="d8bd7-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="d8bd7-109">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="d8bd7-110">**\<configuration>**</span><span class="sxs-lookup"><span data-stu-id="d8bd7-110">**\<configuration>**</span></span>](~/docs/framework/configure-apps/file-schema/configuration-element.md) | <span data-ttu-id="d8bd7-111">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d8bd7-111">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="d8bd7-112">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="d8bd7-112">Child elements</span></span>

|     | <span data-ttu-id="d8bd7-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="d8bd7-113">Description</span></span> |
| --- | ----------- |
| <span data-ttu-id="d8bd7-114">[**\<Adicionar >** ](~/docs/framework/configure-apps/file-schema/add-element-for-custom-2.md) para <xref:System.Configuration.NameValueSectionHandler> e<xref:System.Configuration.DictionarySectionHandler></span><span class="sxs-lookup"><span data-stu-id="d8bd7-114">[**\<add>**](~/docs/framework/configure-apps/file-schema/add-element-for-custom-2.md) for <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler></span></span>  | <span data-ttu-id="d8bd7-115">Adiciona as configurações de aplicativo personalizado.</span><span class="sxs-lookup"><span data-stu-id="d8bd7-115">Adds custom application settings.</span></span> |
| <span data-ttu-id="d8bd7-116">[**\<Remover >** ](~/docs/framework/configure-apps/file-schema/remove-element-for-custom-2.md) para <xref:System.Configuration.NameValueSectionHandler> e<xref:System.Configuration.DictionarySectionHandler></span><span class="sxs-lookup"><span data-stu-id="d8bd7-116">[**\<remove>**](~/docs/framework/configure-apps/file-schema/remove-element-for-custom-2.md) for <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler></span></span> |    <span data-ttu-id="d8bd7-117">Remove uma configuração definida anteriormente.</span><span class="sxs-lookup"><span data-stu-id="d8bd7-117">Removes a previously defined setting.</span></span> |
| <span data-ttu-id="d8bd7-118">[**\<Limpar >** ](~/docs/framework/configure-apps/file-schema/clear-element-for-custom-2.md) para <xref:System.Configuration.NameValueSectionHandler> e<xref:System.Configuration.DictionarySectionHandler></span><span class="sxs-lookup"><span data-stu-id="d8bd7-118">[**\<clear>**](~/docs/framework/configure-apps/file-schema/clear-element-for-custom-2.md) for <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler></span></span> | <span data-ttu-id="d8bd7-119">Limpa todas as configurações previamente definidas em uma seção.</span><span class="sxs-lookup"><span data-stu-id="d8bd7-119">Clears all previously defined settings in a section.</span></span> |

## <a name="remarks"></a><span data-ttu-id="d8bd7-120">Comentários</span><span class="sxs-lookup"><span data-stu-id="d8bd7-120">Remarks</span></span>

<span data-ttu-id="d8bd7-121">O  **\<sectionName >** é um elemento personalizado definido por um  **\<seção >** marca no  **\<configSections >**elemento.</span><span class="sxs-lookup"><span data-stu-id="d8bd7-121">The **\<sectionName>** element is a custom element defined by a **\<section>** tag in the **\<configSections>** element.</span></span>

<span data-ttu-id="d8bd7-122">A tabela a seguir mostra que o tipo de objeto, o método ConfigurationSettings.GetConfig retorna para cada manipulador de seção de configuração:</span><span class="sxs-lookup"><span data-stu-id="d8bd7-122">The following table shows the type of object the ConfigurationSettings.GetConfig method returns for each configuration section handler:</span></span>

| <span data-ttu-id="d8bd7-123">Manipulador da seção de configuração</span><span class="sxs-lookup"><span data-stu-id="d8bd7-123">Configuration section handler</span></span>                        | <span data-ttu-id="d8bd7-124">Tipo de retorno</span><span class="sxs-lookup"><span data-stu-id="d8bd7-124">Return type</span></span>                                                |
| ---------------------------------------------------- | ---------------------------------------------------------- |
| <xref:System.Configuration.NameValueSectionHandler>  | <xref:System.Collections.Specialized.NameValueCollection>  |
| <xref:System.Configuration.DictionarySectionHandler> | <xref:System.Collections.IDictionary>                      |

## <a name="example"></a><span data-ttu-id="d8bd7-125">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d8bd7-125">Example</span></span>

<span data-ttu-id="d8bd7-126">O exemplo a seguir mostra como declarar seções que usam o <xref:System.Configuration.DictionarySectionHandler> e <xref:System.Configuration.NameValueSectionHandler> classes.</span><span class="sxs-lookup"><span data-stu-id="d8bd7-126">The following example shows how to declare sections that use the <xref:System.Configuration.DictionarySectionHandler> and <xref:System.Configuration.NameValueSectionHandler> classes.</span></span> 

<span data-ttu-id="d8bd7-127">O primeiro elemento personalizado é  **\<dictionarySample >**, que contém as configurações de leitura pelo <xref:System.Configuration.DictionarySectionHandler> classe no `System.dll` assembly.</span><span class="sxs-lookup"><span data-stu-id="d8bd7-127">The first custom element is **\<dictionarySample>**, which contains settings read by the <xref:System.Configuration.DictionarySectionHandler> class in the `System.dll` assembly.</span></span> <span data-ttu-id="d8bd7-128">O segundo elemento personalizado é  **\<mySection >**, que contém as configurações de leitura pelo <xref:System.Configuration.NameValueSectionHandler> classe no `System.dll` assembly.</span><span class="sxs-lookup"><span data-stu-id="d8bd7-128">The second custom element is **\<mySection>**, which contains settings read by the <xref:System.Configuration.NameValueSectionHandler> class in the `System.dll` assembly.</span></span>

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

## <a name="configuration-file"></a><span data-ttu-id="d8bd7-129">arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="d8bd7-129">Configuration file</span></span>

<span data-ttu-id="d8bd7-130">Esse elemento pode ser usado no arquivo de configuração do aplicativo, o arquivo de configuração de máquina (*Machine. config*), e *Web. config* arquivos que não estão no nível de diretório do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d8bd7-130">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="d8bd7-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d8bd7-131">See also</span></span>

[<span data-ttu-id="d8bd7-132">Esquema de arquivo de configuração para o .NET Framework</span><span class="sxs-lookup"><span data-stu-id="d8bd7-132">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
