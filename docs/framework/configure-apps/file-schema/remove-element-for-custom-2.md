---
title: elemento <remove> para NameValueSectionHandler e DictionarySectionHandler
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName/remove
helpviewer_keywords:
- remove Element
- <remove> Element
ms.assetid: 8d8af7f5-26c9-4db9-bbe4-b2a4e6949568
author: mairaw
ms.author: mairaw
ms.openlocfilehash: dc1519a794e24e04074dd2a674ecc2c0f3666521
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73118559"
---
# <a name="remove-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a><span data-ttu-id="cff0d-102">\<remover > elemento para NameValueSectionHandler e DictionarySectionHandler</span><span class="sxs-lookup"><span data-stu-id="cff0d-102">\<remove> element for NameValueSectionHandler and DictionarySectionHandler</span></span>

<span data-ttu-id="cff0d-103">Remove uma configuração definida anteriormente.</span><span class="sxs-lookup"><span data-stu-id="cff0d-103">Removes a previously defined setting.</span></span>

<span data-ttu-id="cff0d-104">[ **\<configuration>** ](configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="cff0d-104">[**\<configuration>**](configuration-element.md) </span></span>  
<span data-ttu-id="cff0d-105">&nbsp;&nbsp;[ **\<sectionname >** ](custom-element-2.md) </span><span class="sxs-lookup"><span data-stu-id="cff0d-105">&nbsp;&nbsp;[**\<sectionName>**](custom-element-2.md) </span></span>  
<span data-ttu-id="cff0d-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<remover >**</span><span class="sxs-lookup"><span data-stu-id="cff0d-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**</span></span>

## <a name="syntax"></a><span data-ttu-id="cff0d-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cff0d-107">Syntax</span></span>

```xml
<add remove="key" />
```

## <a name="attribute"></a><span data-ttu-id="cff0d-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="cff0d-108">Attribute</span></span>

|           | <span data-ttu-id="cff0d-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="cff0d-109">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="cff0d-110">**key**</span><span class="sxs-lookup"><span data-stu-id="cff0d-110">**key**</span></span>   | <span data-ttu-id="cff0d-111">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="cff0d-111">Required attribute.</span></span><br><br><span data-ttu-id="cff0d-112">Especifica o nome da configuração a ser removida.</span><span class="sxs-lookup"><span data-stu-id="cff0d-112">Specifies the name of the setting to remove.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="cff0d-113">Elemento pai</span><span class="sxs-lookup"><span data-stu-id="cff0d-113">Parent element</span></span>

| <span data-ttu-id="cff0d-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="cff0d-114">Element</span></span> | <span data-ttu-id="cff0d-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="cff0d-115">Description</span></span> |
| ------- | ------------|
| [<span data-ttu-id="cff0d-116"> **\<sectionname >** Elementos</span><span class="sxs-lookup"><span data-stu-id="cff0d-116">**\<sectionName>** Element</span></span>](custom-element-2.md) | <span data-ttu-id="cff0d-117">Define as configurações para seções de configuração personalizadas que usam as classes <xref:System.Configuration.NameValueSectionHandler> e <xref:System.Configuration.DictionarySectionHandler>.</span><span class="sxs-lookup"><span data-stu-id="cff0d-117">Defines settings for custom configuration sections that use the <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler> classes.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="cff0d-118">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="cff0d-118">Child elements</span></span>

<span data-ttu-id="cff0d-119">Nenhum</span><span class="sxs-lookup"><span data-stu-id="cff0d-119">None</span></span>

## <a name="remarks"></a><span data-ttu-id="cff0d-120">Comentários</span><span class="sxs-lookup"><span data-stu-id="cff0d-120">Remarks</span></span>

<span data-ttu-id="cff0d-121">Você pode usar o elemento **\<remover >** para remover as configurações de seu aplicativo que foram definidas em um nível superior na hierarquia do arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="cff0d-121">You can use the **\<remove>** element to remove settings from your application that were defined at a higher level in the configuration file hierarchy.</span></span>

## <a name="example"></a><span data-ttu-id="cff0d-122">Exemplo</span><span class="sxs-lookup"><span data-stu-id="cff0d-122">Example</span></span>

<span data-ttu-id="cff0d-123">O exemplo a seguir mostra como usar o elemento **\<remover >** em um arquivo de configuração de aplicativo para remover as configurações definidas anteriormente no arquivo de configuração do computador.</span><span class="sxs-lookup"><span data-stu-id="cff0d-123">The following example shows how to use the **\<remove>** element in an application configuration file to remove settings previously defined in the machine configuration file.</span></span>

<span data-ttu-id="cff0d-124">O código do arquivo de configuração de computador a seguir declara a seção **\<myseção >** e adiciona duas configurações, `key1` e `key2`, a ela:</span><span class="sxs-lookup"><span data-stu-id="cff0d-124">The following machine configuration file code declares the section **\<mySection>** and adds two settings, `key1` and `key2`, to it:</span></span>

```xml
<!-- Machine.config file -->
<configuration>
  <configSections>
    <section name="mySection" type="System.Configuration.NameValueSectionHandler,System" />
  </configSections>
  <mySection>
    <add key="key1" value="value1" />
    <add key="key2" value="value2" />
  </mySection>
</configuration>
```

<span data-ttu-id="cff0d-125">O código do arquivo de configuração de aplicativo a seguir remove a configuração de `key2` da **\<myseção >** :</span><span class="sxs-lookup"><span data-stu-id="cff0d-125">The following application configuration file code removes the `key2` setting from **\<mySection>**:</span></span>

```xml
<!--Application configuration file -->
<configuration>
  <mySection>
    <remove key="key2" />
  </mySection>
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="cff0d-126">arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="cff0d-126">Configuration file</span></span>

<span data-ttu-id="cff0d-127">Esse elemento pode ser usado no arquivo de configuração do aplicativo, no arquivo de configuração do computador (*Machine. config*) e nos arquivos *Web. config* que não estão no nível do diretório do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="cff0d-127">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="cff0d-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cff0d-128">See also</span></span>

- [<span data-ttu-id="cff0d-129">Esquema do arquivo de configuração para o .NET Framework</span><span class="sxs-lookup"><span data-stu-id="cff0d-129">Configuration file schema for the .NET Framework</span></span>](index.md)
