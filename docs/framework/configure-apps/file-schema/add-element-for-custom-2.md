---
title: <add>elemento para NameValueSectionHandler e DictionarySectionHandler
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName/add
helpviewer_keywords:
- add Element
- <add> Element
ms.assetid: 0d4ddb53-eb2b-49c0-9c33-a8dec5c39b46
ms.openlocfilehash: 57722f3518fad12cb8e6e35d68f40bb8465bdd86
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "77215436"
---
# <a name="add-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a><span data-ttu-id="47754-102">\<add>elemento para NameValueSectionHandler e DictionarySectionHandler</span><span class="sxs-lookup"><span data-stu-id="47754-102">\<add> element for NameValueSectionHandler and DictionarySectionHandler</span></span>

<span data-ttu-id="47754-103">Adiciona configurações de aplicativo personalizadas.</span><span class="sxs-lookup"><span data-stu-id="47754-103">Adds custom application settings.</span></span> <span data-ttu-id="47754-104">Cada **\<add>** marca contém um par de chave/valor.</span><span class="sxs-lookup"><span data-stu-id="47754-104">Each **\<add>** tag contains a key/value pair.</span></span>

[**\<configuration>**](configuration-element.md)\
&nbsp;&nbsp;[**\<sectionName>**](custom-element-2.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**

## <a name="syntax"></a><span data-ttu-id="47754-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="47754-105">Syntax</span></span>

```xml
<add key="key" value="value" />
```

## <a name="attributes"></a><span data-ttu-id="47754-106">Atributos</span><span class="sxs-lookup"><span data-stu-id="47754-106">Attributes</span></span>

| <span data-ttu-id="47754-107">Atributo</span><span class="sxs-lookup"><span data-stu-id="47754-107">Attribute</span></span> | <span data-ttu-id="47754-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="47754-108">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="47754-109">**chave**</span><span class="sxs-lookup"><span data-stu-id="47754-109">**key**</span></span>   | <span data-ttu-id="47754-110">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="47754-110">Required attribute.</span></span><br><br><span data-ttu-id="47754-111">Especifica o nome da configuração.</span><span class="sxs-lookup"><span data-stu-id="47754-111">Specifies the name of the setting.</span></span> |
| <span data-ttu-id="47754-112">**value**</span><span class="sxs-lookup"><span data-stu-id="47754-112">**value**</span></span> | <span data-ttu-id="47754-113">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="47754-113">Required attribute.</span></span><br><br><span data-ttu-id="47754-114">Especifica o valor da configuração.</span><span class="sxs-lookup"><span data-stu-id="47754-114">Specifies the value of the setting.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="47754-115">Elemento pai</span><span class="sxs-lookup"><span data-stu-id="47754-115">Parent element</span></span>

| <span data-ttu-id="47754-116">Elemento</span><span class="sxs-lookup"><span data-stu-id="47754-116">Element</span></span> | <span data-ttu-id="47754-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="47754-117">Description</span></span> |
| ------- | ------------|
| [<span data-ttu-id="47754-118">**\<sectionName>** Elementos</span><span class="sxs-lookup"><span data-stu-id="47754-118">**\<sectionName>** Element</span></span>](custom-element-2.md) | <span data-ttu-id="47754-119">Define as configurações para seções de configuração personalizadas que usam as <xref:System.Configuration.NameValueSectionHandler> <xref:System.Configuration.DictionarySectionHandler> classes e.</span><span class="sxs-lookup"><span data-stu-id="47754-119">Defines settings for custom configuration sections that use the <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler> classes.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="47754-120">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="47754-120">Child elements</span></span>

<span data-ttu-id="47754-121">Nenhum</span><span class="sxs-lookup"><span data-stu-id="47754-121">None</span></span>

## <a name="example"></a><span data-ttu-id="47754-122">Exemplo</span><span class="sxs-lookup"><span data-stu-id="47754-122">Example</span></span>

<span data-ttu-id="47754-123">O exemplo a seguir mostra como definir uma seção de configuração personalizada e usar o **\<add>** elemento para colocar as configurações na seção:</span><span class="sxs-lookup"><span data-stu-id="47754-123">The following example shows how to define a custom configuration section and use the **\<add>** element to put settings into the section:</span></span>

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

## <a name="configuration-file"></a><span data-ttu-id="47754-124">Arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="47754-124">Configuration file</span></span>

<span data-ttu-id="47754-125">Esse elemento pode ser usado no arquivo de configuração do aplicativo, no arquivo de configuração do computador (*Machine. config*) e nos arquivos *Web. config* que não estão no nível do diretório do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="47754-125">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="47754-126">Confira também</span><span class="sxs-lookup"><span data-stu-id="47754-126">See also</span></span>

- [<span data-ttu-id="47754-127">Esquema do arquivo de configuração para o .NET Framework</span><span class="sxs-lookup"><span data-stu-id="47754-127">Configuration file schema for the .NET Framework</span></span>](index.md)
