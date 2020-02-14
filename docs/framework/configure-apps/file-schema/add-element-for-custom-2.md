---
title: elemento <add> para NameValueSectionHandler e DictionarySectionHandler
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName/add
helpviewer_keywords:
- add Element
- <add> Element
ms.assetid: 0d4ddb53-eb2b-49c0-9c33-a8dec5c39b46
ms.openlocfilehash: 57722f3518fad12cb8e6e35d68f40bb8465bdd86
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77215436"
---
# <a name="add-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a><span data-ttu-id="58e1e-102">\<Adicionar > elemento para NameValueSectionHandler e DictionarySectionHandler</span><span class="sxs-lookup"><span data-stu-id="58e1e-102">\<add> element for NameValueSectionHandler and DictionarySectionHandler</span></span>

<span data-ttu-id="58e1e-103">Adiciona configurações de aplicativo personalizadas.</span><span class="sxs-lookup"><span data-stu-id="58e1e-103">Adds custom application settings.</span></span> <span data-ttu-id="58e1e-104">Cada **\<adicionar >** marca contém um par chave/valor.</span><span class="sxs-lookup"><span data-stu-id="58e1e-104">Each **\<add>** tag contains a key/value pair.</span></span>

<span data-ttu-id="58e1e-105">[ **\<configuration>** ](configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="58e1e-105">[**\<configuration>**](configuration-element.md)</span></span>\
<span data-ttu-id="58e1e-106">&nbsp;&nbsp;[ **\<sectionname >** ](custom-element-2.md)</span><span class="sxs-lookup"><span data-stu-id="58e1e-106">&nbsp;&nbsp;[**\<sectionName>**](custom-element-2.md)</span></span>\
<span data-ttu-id="58e1e-107">&nbsp;&nbsp;&nbsp;&nbsp; **\<adicionar >**</span><span class="sxs-lookup"><span data-stu-id="58e1e-107">&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>

## <a name="syntax"></a><span data-ttu-id="58e1e-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="58e1e-108">Syntax</span></span>

```xml
<add key="key" value="value" />
```

## <a name="attributes"></a><span data-ttu-id="58e1e-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="58e1e-109">Attributes</span></span>

| <span data-ttu-id="58e1e-110">Atributo</span><span class="sxs-lookup"><span data-stu-id="58e1e-110">Attribute</span></span> | <span data-ttu-id="58e1e-111">DESCRIÇÃO</span><span class="sxs-lookup"><span data-stu-id="58e1e-111">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="58e1e-112">**chave**</span><span class="sxs-lookup"><span data-stu-id="58e1e-112">**key**</span></span>   | <span data-ttu-id="58e1e-113">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="58e1e-113">Required attribute.</span></span><br><br><span data-ttu-id="58e1e-114">Especifica o nome da configuração.</span><span class="sxs-lookup"><span data-stu-id="58e1e-114">Specifies the name of the setting.</span></span> |
| <span data-ttu-id="58e1e-115">**value**</span><span class="sxs-lookup"><span data-stu-id="58e1e-115">**value**</span></span> | <span data-ttu-id="58e1e-116">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="58e1e-116">Required attribute.</span></span><br><br><span data-ttu-id="58e1e-117">Especifica o valor da configuração.</span><span class="sxs-lookup"><span data-stu-id="58e1e-117">Specifies the value of the setting.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="58e1e-118">Elemento pai</span><span class="sxs-lookup"><span data-stu-id="58e1e-118">Parent element</span></span>

| <span data-ttu-id="58e1e-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="58e1e-119">Element</span></span> | <span data-ttu-id="58e1e-120">DESCRIÇÃO</span><span class="sxs-lookup"><span data-stu-id="58e1e-120">Description</span></span> |
| ------- | ------------|
| [<span data-ttu-id="58e1e-121"> **\<sectionname >** Elementos</span><span class="sxs-lookup"><span data-stu-id="58e1e-121">**\<sectionName>** Element</span></span>](custom-element-2.md) | <span data-ttu-id="58e1e-122">Define as configurações para seções de configuração personalizadas que usam as classes <xref:System.Configuration.NameValueSectionHandler> e <xref:System.Configuration.DictionarySectionHandler>.</span><span class="sxs-lookup"><span data-stu-id="58e1e-122">Defines settings for custom configuration sections that use the <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler> classes.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="58e1e-123">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="58e1e-123">Child elements</span></span>

<span data-ttu-id="58e1e-124">Nenhum</span><span class="sxs-lookup"><span data-stu-id="58e1e-124">None</span></span>

## <a name="example"></a><span data-ttu-id="58e1e-125">Exemplo</span><span class="sxs-lookup"><span data-stu-id="58e1e-125">Example</span></span>

<span data-ttu-id="58e1e-126">O exemplo a seguir mostra como definir uma seção de configuração personalizada e usar o **\<adicionar >** elemento para colocar as configurações na seção:</span><span class="sxs-lookup"><span data-stu-id="58e1e-126">The following example shows how to define a custom configuration section and use the **\<add>** element to put settings into the section:</span></span>

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

## <a name="configuration-file"></a><span data-ttu-id="58e1e-127">Arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="58e1e-127">Configuration file</span></span>

<span data-ttu-id="58e1e-128">Esse elemento pode ser usado no arquivo de configuração do aplicativo, no arquivo de configuração do computador (*Machine. config*) e nos arquivos *Web. config* que não estão no nível do diretório do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="58e1e-128">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="58e1e-129">Confira também</span><span class="sxs-lookup"><span data-stu-id="58e1e-129">See also</span></span>

- [<span data-ttu-id="58e1e-130">Esquema do arquivo de configuração para o .NET Framework</span><span class="sxs-lookup"><span data-stu-id="58e1e-130">Configuration file schema for the .NET Framework</span></span>](index.md)
