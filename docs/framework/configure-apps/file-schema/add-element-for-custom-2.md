---
title: '&lt;Adicionar&gt; elemento para NameValueSectionHandler e DictionarySectionHandler'
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName/add
helpviewer_keywords:
- add Element
- <add> Element
ms.assetid: 0d4ddb53-eb2b-49c0-9c33-a8dec5c39b46
author: guardrex
ms.author: mairaw
ms.openlocfilehash: 502f86e49d68e456d8e64e00e7632aa603cafbe9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54523903"
---
# <a name="add-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a><span data-ttu-id="05482-102">\<Adicionar > elemento para NameValueSectionHandler e DictionarySectionHandler</span><span class="sxs-lookup"><span data-stu-id="05482-102">\<add> element for NameValueSectionHandler and DictionarySectionHandler</span></span>

<span data-ttu-id="05482-103">Adiciona as configurações de aplicativo personalizado.</span><span class="sxs-lookup"><span data-stu-id="05482-103">Adds custom application settings.</span></span> <span data-ttu-id="05482-104">Cada  **\<Adicionar >** marca contém um par chave/valor.</span><span class="sxs-lookup"><span data-stu-id="05482-104">Each **\<add>** tag contains a key/value pair.</span></span>

<span data-ttu-id="05482-105">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="05482-105">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="05482-106">&nbsp;&nbsp;[**\<sectionName>**](~/docs/framework/configure-apps/file-schema/custom-element-2.md) </span><span class="sxs-lookup"><span data-stu-id="05482-106">&nbsp;&nbsp;[**\<sectionName>**](~/docs/framework/configure-apps/file-schema/custom-element-2.md) </span></span>  
<span data-ttu-id="05482-107">&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span><span class="sxs-lookup"><span data-stu-id="05482-107">&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>

## <a name="syntax"></a><span data-ttu-id="05482-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="05482-108">Syntax</span></span>

```xml
<add key="key" value="value" />
```

## <a name="attributes"></a><span data-ttu-id="05482-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="05482-109">Attributes</span></span>

| <span data-ttu-id="05482-110">Atributo</span><span class="sxs-lookup"><span data-stu-id="05482-110">Attribute</span></span> | <span data-ttu-id="05482-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="05482-111">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="05482-112">**key**</span><span class="sxs-lookup"><span data-stu-id="05482-112">**key**</span></span>   | <span data-ttu-id="05482-113">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="05482-113">Required attribute.</span></span><br><br><span data-ttu-id="05482-114">Especifica o nome da configuração.</span><span class="sxs-lookup"><span data-stu-id="05482-114">Specifies the name of the setting.</span></span> |
| <span data-ttu-id="05482-115">**value**</span><span class="sxs-lookup"><span data-stu-id="05482-115">**value**</span></span> | <span data-ttu-id="05482-116">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="05482-116">Required attribute.</span></span><br><br><span data-ttu-id="05482-117">Especifica o valor da configuração.</span><span class="sxs-lookup"><span data-stu-id="05482-117">Specifies the value of the setting.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="05482-118">Elemento pai</span><span class="sxs-lookup"><span data-stu-id="05482-118">Parent element</span></span>

| <span data-ttu-id="05482-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="05482-119">Element</span></span> | <span data-ttu-id="05482-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="05482-120">Description</span></span> |
| ------- | ------------|
| [<span data-ttu-id="05482-121">**\<sectionName >** elemento</span><span class="sxs-lookup"><span data-stu-id="05482-121">**\<sectionName>** Element</span></span>](~/docs/framework/configure-apps/file-schema/custom-element-2.md) | <span data-ttu-id="05482-122">Define as configurações para seções de configuração personalizadas que usam o <xref:System.Configuration.NameValueSectionHandler> e <xref:System.Configuration.DictionarySectionHandler> classes.</span><span class="sxs-lookup"><span data-stu-id="05482-122">Defines settings for custom configuration sections that use the <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler> classes.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="05482-123">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="05482-123">Child elements</span></span>

<span data-ttu-id="05482-124">Nenhum</span><span class="sxs-lookup"><span data-stu-id="05482-124">None</span></span>

## <a name="example"></a><span data-ttu-id="05482-125">Exemplo</span><span class="sxs-lookup"><span data-stu-id="05482-125">Example</span></span>

<span data-ttu-id="05482-126">O exemplo a seguir mostra como definir uma seção de configuração personalizada e usar o  **\<Adicionar >** elemento colocar configurações na seção:</span><span class="sxs-lookup"><span data-stu-id="05482-126">The following example shows how to define a custom configuration section and use the **\<add>** element to put settings into the section:</span></span>

```xml
<configuration>
  <configSections>
    <section name="dictionarySample" type="System.Configuration.DictionarySectionHandler,System" />
  </configSections>
  <dictionarySample>
    <add key="myKey" value="myValue" />
  </dictionarySample>
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="05482-127">arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="05482-127">Configuration file</span></span>

<span data-ttu-id="05482-128">Esse elemento pode ser usado no arquivo de configuração do aplicativo, arquivo de configuração de máquina (*Machine. config*), e *Web. config* arquivos que não estão no nível de diretório do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="05482-128">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="05482-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="05482-129">See also</span></span>

- [<span data-ttu-id="05482-130">Esquema de arquivo de configuração para o .NET Framework</span><span class="sxs-lookup"><span data-stu-id="05482-130">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
