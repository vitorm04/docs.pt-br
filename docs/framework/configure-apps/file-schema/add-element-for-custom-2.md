---
title: elemento <add> para NameValueSectionHandler e DictionarySectionHandler
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName/add
helpviewer_keywords:
- add Element
- <add> Element
ms.assetid: 0d4ddb53-eb2b-49c0-9c33-a8dec5c39b46
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a9e7d68530ae1f0666fc4940ffe7605c3bf8dfe3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73119610"
---
# <a name="add-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a><span data-ttu-id="a9feb-102">\<Adicionar > elemento para NameValueSectionHandler e DictionarySectionHandler</span><span class="sxs-lookup"><span data-stu-id="a9feb-102">\<add> element for NameValueSectionHandler and DictionarySectionHandler</span></span>

<span data-ttu-id="a9feb-103">Adiciona configurações de aplicativo personalizadas.</span><span class="sxs-lookup"><span data-stu-id="a9feb-103">Adds custom application settings.</span></span> <span data-ttu-id="a9feb-104">Cada **\<adicionar >** marca contém um par chave/valor.</span><span class="sxs-lookup"><span data-stu-id="a9feb-104">Each **\<add>** tag contains a key/value pair.</span></span>

<span data-ttu-id="a9feb-105">[ **\<configuration>** ](configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="a9feb-105">[**\<configuration>**](configuration-element.md) </span></span>  
<span data-ttu-id="a9feb-106">&nbsp;&nbsp;[ **\<sectionname >** ](custom-element-2.md) </span><span class="sxs-lookup"><span data-stu-id="a9feb-106">&nbsp;&nbsp;[**\<sectionName>**](custom-element-2.md) </span></span>  
<span data-ttu-id="a9feb-107">&nbsp;&nbsp;&nbsp;&nbsp; **\<adicionar >**</span><span class="sxs-lookup"><span data-stu-id="a9feb-107">&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>

## <a name="syntax"></a><span data-ttu-id="a9feb-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a9feb-108">Syntax</span></span>

```xml
<add key="key" value="value" />
```

## <a name="attributes"></a><span data-ttu-id="a9feb-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="a9feb-109">Attributes</span></span>

| <span data-ttu-id="a9feb-110">Atributo</span><span class="sxs-lookup"><span data-stu-id="a9feb-110">Attribute</span></span> | <span data-ttu-id="a9feb-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="a9feb-111">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="a9feb-112">**key**</span><span class="sxs-lookup"><span data-stu-id="a9feb-112">**key**</span></span>   | <span data-ttu-id="a9feb-113">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="a9feb-113">Required attribute.</span></span><br><br><span data-ttu-id="a9feb-114">Especifica o nome da configuração.</span><span class="sxs-lookup"><span data-stu-id="a9feb-114">Specifies the name of the setting.</span></span> |
| <span data-ttu-id="a9feb-115">**value**</span><span class="sxs-lookup"><span data-stu-id="a9feb-115">**value**</span></span> | <span data-ttu-id="a9feb-116">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="a9feb-116">Required attribute.</span></span><br><br><span data-ttu-id="a9feb-117">Especifica o valor da configuração.</span><span class="sxs-lookup"><span data-stu-id="a9feb-117">Specifies the value of the setting.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="a9feb-118">Elemento pai</span><span class="sxs-lookup"><span data-stu-id="a9feb-118">Parent element</span></span>

| <span data-ttu-id="a9feb-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="a9feb-119">Element</span></span> | <span data-ttu-id="a9feb-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="a9feb-120">Description</span></span> |
| ------- | ------------|
| [<span data-ttu-id="a9feb-121"> **\<sectionname >** Elementos</span><span class="sxs-lookup"><span data-stu-id="a9feb-121">**\<sectionName>** Element</span></span>](custom-element-2.md) | <span data-ttu-id="a9feb-122">Define as configurações para seções de configuração personalizadas que usam as classes <xref:System.Configuration.NameValueSectionHandler> e <xref:System.Configuration.DictionarySectionHandler>.</span><span class="sxs-lookup"><span data-stu-id="a9feb-122">Defines settings for custom configuration sections that use the <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler> classes.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="a9feb-123">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="a9feb-123">Child elements</span></span>

<span data-ttu-id="a9feb-124">Nenhum</span><span class="sxs-lookup"><span data-stu-id="a9feb-124">None</span></span>

## <a name="example"></a><span data-ttu-id="a9feb-125">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a9feb-125">Example</span></span>

<span data-ttu-id="a9feb-126">O exemplo a seguir mostra como definir uma seção de configuração personalizada e usar o **\<adicionar >** elemento para colocar as configurações na seção:</span><span class="sxs-lookup"><span data-stu-id="a9feb-126">The following example shows how to define a custom configuration section and use the **\<add>** element to put settings into the section:</span></span>

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

## <a name="configuration-file"></a><span data-ttu-id="a9feb-127">arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="a9feb-127">Configuration file</span></span>

<span data-ttu-id="a9feb-128">Esse elemento pode ser usado no arquivo de configuração do aplicativo, no arquivo de configuração do computador (*Machine. config*) e nos arquivos *Web. config* que não estão no nível do diretório do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a9feb-128">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="a9feb-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a9feb-129">See also</span></span>

- [<span data-ttu-id="a9feb-130">Esquema do arquivo de configuração para o .NET Framework</span><span class="sxs-lookup"><span data-stu-id="a9feb-130">Configuration file schema for the .NET Framework</span></span>](index.md)
