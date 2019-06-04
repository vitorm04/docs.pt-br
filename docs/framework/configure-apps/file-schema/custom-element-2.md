---
title: Elemento personalizado para NameValueSectionHandler e DictionarySectionHandler
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName
helpviewer_keywords:
- custom element
ms.assetid: 2303031f-4c1d-4df4-bca1-e9bd96ca40dc
author: rpetrusha
ms.author: mairaw
ms.openlocfilehash: 8636050b2618d1b2c2da0c08c756b0ed221c7f6f
ms.sourcegitcommit: 621a5f6df00152006160987395b93b5b55f7ffcd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66300767"
---
# <a name="custom-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a><span data-ttu-id="19970-102">Elemento personalizado para NameValueSectionHandler e DictionarySectionHandler</span><span class="sxs-lookup"><span data-stu-id="19970-102">Custom element for NameValueSectionHandler and DictionarySectionHandler</span></span>

<span data-ttu-id="19970-103">Define as configurações para seções de configuração personalizadas que usam o <xref:System.Configuration.NameValueSectionHandler> e <xref:System.Configuration.DictionarySectionHandler> classes.</span><span class="sxs-lookup"><span data-stu-id="19970-103">Defines settings for custom configuration sections that use the <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler> classes.</span></span>

<span data-ttu-id="19970-104">[ **\<configuration>** ](~/docs/framework/configure-apps/file-schema/configuration-element.md)\\</span><span class="sxs-lookup"><span data-stu-id="19970-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md)\\</span></span>
<span data-ttu-id="19970-105">&nbsp;&nbsp; **\<sectionName>**</span><span class="sxs-lookup"><span data-stu-id="19970-105">&nbsp;&nbsp;**\<sectionName>**</span></span>

## <a name="attributes"></a><span data-ttu-id="19970-106">Atributos</span><span class="sxs-lookup"><span data-stu-id="19970-106">Attributes</span></span>

<span data-ttu-id="19970-107">Nenhum</span><span class="sxs-lookup"><span data-stu-id="19970-107">None</span></span>

## <a name="parent-element"></a><span data-ttu-id="19970-108">Elemento pai</span><span class="sxs-lookup"><span data-stu-id="19970-108">Parent element</span></span>

|     | <span data-ttu-id="19970-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="19970-109">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="19970-110"> *\*\<configuration>** </span><span class="sxs-lookup"><span data-stu-id="19970-110">**\<configuration>**</span></span>](~/docs/framework/configure-apps/file-schema/configuration-element.md) | <span data-ttu-id="19970-111">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="19970-111">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="19970-112">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="19970-112">Child elements</span></span>

|     | <span data-ttu-id="19970-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="19970-113">Description</span></span> |
| --- | ----------- |
| <span data-ttu-id="19970-114">[ **\<Adicionar >** ](~/docs/framework/configure-apps/file-schema/add-element-for-custom-2.md) para <xref:System.Configuration.NameValueSectionHandler> e <xref:System.Configuration.DictionarySectionHandler></span><span class="sxs-lookup"><span data-stu-id="19970-114">[**\<add>**](~/docs/framework/configure-apps/file-schema/add-element-for-custom-2.md) for <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler></span></span>  | <span data-ttu-id="19970-115">Adiciona as configurações de aplicativo personalizado.</span><span class="sxs-lookup"><span data-stu-id="19970-115">Adds custom application settings.</span></span> |
| <span data-ttu-id="19970-116">[ **\<Remover >** ](~/docs/framework/configure-apps/file-schema/remove-element-for-custom-2.md) para <xref:System.Configuration.NameValueSectionHandler> e <xref:System.Configuration.DictionarySectionHandler></span><span class="sxs-lookup"><span data-stu-id="19970-116">[**\<remove>**](~/docs/framework/configure-apps/file-schema/remove-element-for-custom-2.md) for <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler></span></span> | <span data-ttu-id="19970-117">Remove uma configuração definida anteriormente.</span><span class="sxs-lookup"><span data-stu-id="19970-117">Removes a previously defined setting.</span></span> |
| <span data-ttu-id="19970-118">[ **\<Limpar >** ](~/docs/framework/configure-apps/file-schema/clear-element-for-custom-2.md) para <xref:System.Configuration.NameValueSectionHandler> e <xref:System.Configuration.DictionarySectionHandler></span><span class="sxs-lookup"><span data-stu-id="19970-118">[**\<clear>**](~/docs/framework/configure-apps/file-schema/clear-element-for-custom-2.md) for <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler></span></span> | <span data-ttu-id="19970-119">Limpa todas as configurações definidas anteriormente em uma seção.</span><span class="sxs-lookup"><span data-stu-id="19970-119">Clears all previously defined settings in a section.</span></span> |

## <a name="remarks"></a><span data-ttu-id="19970-120">Comentários</span><span class="sxs-lookup"><span data-stu-id="19970-120">Remarks</span></span>

<span data-ttu-id="19970-121">O  **\<sectionName >** é um elemento personalizado definido por uma  **\<seção >** marcar no  **\<configSections >** elemento.</span><span class="sxs-lookup"><span data-stu-id="19970-121">The **\<sectionName>** element is a custom element defined by a **\<section>** tag in the **\<configSections>** element.</span></span>

<span data-ttu-id="19970-122">A tabela a seguir mostra que o tipo de objeto, o método ConfigurationSettings.GetConfig retorna para cada manipulador de seção de configuração:</span><span class="sxs-lookup"><span data-stu-id="19970-122">The following table shows the type of object the ConfigurationSettings.GetConfig method returns for each configuration section handler:</span></span>

| <span data-ttu-id="19970-123">Manipulador de seção de configuração</span><span class="sxs-lookup"><span data-stu-id="19970-123">Configuration section handler</span></span>                        | <span data-ttu-id="19970-124">Tipo de retorno</span><span class="sxs-lookup"><span data-stu-id="19970-124">Return type</span></span>                                                |
| ---------------------------------------------------- | ---------------------------------------------------------- |
| <xref:System.Configuration.NameValueSectionHandler>  | <xref:System.Collections.Specialized.NameValueCollection>  |
| <xref:System.Configuration.DictionarySectionHandler> | <xref:System.Collections.IDictionary>                      |

## <a name="example"></a><span data-ttu-id="19970-125">Exemplo</span><span class="sxs-lookup"><span data-stu-id="19970-125">Example</span></span>

<span data-ttu-id="19970-126">O exemplo a seguir mostra como declarar seções que usam o <xref:System.Configuration.DictionarySectionHandler> e <xref:System.Configuration.NameValueSectionHandler> classes.</span><span class="sxs-lookup"><span data-stu-id="19970-126">The following example shows how to declare sections that use the <xref:System.Configuration.DictionarySectionHandler> and <xref:System.Configuration.NameValueSectionHandler> classes.</span></span>

<span data-ttu-id="19970-127">É o primeiro elemento personalizado  **\<dictionarySample >** , que contém as configurações lidas pelo <xref:System.Configuration.DictionarySectionHandler> classe o `System.dll` assembly.</span><span class="sxs-lookup"><span data-stu-id="19970-127">The first custom element is **\<dictionarySample>**, which contains settings read by the <xref:System.Configuration.DictionarySectionHandler> class in the `System.dll` assembly.</span></span> <span data-ttu-id="19970-128">O segundo elemento personalizado estiver  **\<mySection >** , que contém as configurações lidas pelo <xref:System.Configuration.NameValueSectionHandler> classe no `System.dll` assembly.</span><span class="sxs-lookup"><span data-stu-id="19970-128">The second custom element is **\<mySection>**, which contains settings read by the <xref:System.Configuration.NameValueSectionHandler> class in the `System.dll` assembly.</span></span>

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

## <a name="configuration-file"></a><span data-ttu-id="19970-129">arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="19970-129">Configuration file</span></span>

<span data-ttu-id="19970-130">Esse elemento pode ser usado no arquivo de configuração do aplicativo, arquivo de configuração de máquina (*Machine. config*), e *Web. config* arquivos que não estão no nível de diretório do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="19970-130">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="19970-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="19970-131">See also</span></span>

- [<span data-ttu-id="19970-132">Esquema de arquivo de configuração para o .NET Framework</span><span class="sxs-lookup"><span data-stu-id="19970-132">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
