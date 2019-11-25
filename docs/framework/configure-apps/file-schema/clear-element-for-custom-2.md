---
title: elemento <clear> para NameValueSectionHandler e DictionarySectionHandler
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName/clear
helpviewer_keywords:
- clear Element
- <clear> Element
ms.assetid: ff2294ec-fb82-4b0c-933e-ae185433fc7b
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fff5a5c2a523480f2eaebb127ec98ff6e9908acf
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/14/2019
ms.locfileid: "74088708"
---
# <a name="clear-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a><span data-ttu-id="cde4a-102">\<limpar > elemento para NameValueSectionHandler e DictionarySectionHandler</span><span class="sxs-lookup"><span data-stu-id="cde4a-102">\<clear> element for NameValueSectionHandler and DictionarySectionHandler</span></span>

<span data-ttu-id="cde4a-103">Limpa todas as configurações definidas anteriormente em uma seção.</span><span class="sxs-lookup"><span data-stu-id="cde4a-103">Clears all previously defined settings in a section.</span></span>

<span data-ttu-id="cde4a-104">[ **\<configuration>** ](configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="cde4a-104">[**\<configuration>**](configuration-element.md)</span></span>\
<span data-ttu-id="cde4a-105">&nbsp;&nbsp;[ **\<sectionname >** ](custom-element-2.md)</span><span class="sxs-lookup"><span data-stu-id="cde4a-105">&nbsp;&nbsp;[**\<sectionName>**](custom-element-2.md)</span></span>\
<span data-ttu-id="cde4a-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<desmarque >**</span><span class="sxs-lookup"><span data-stu-id="cde4a-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**</span></span>

## <a name="syntax"></a><span data-ttu-id="cde4a-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cde4a-107">Syntax</span></span>

```xml
<clear />
```

## <a name="attributes"></a><span data-ttu-id="cde4a-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="cde4a-108">Attributes</span></span>

<span data-ttu-id="cde4a-109">Nenhum</span><span class="sxs-lookup"><span data-stu-id="cde4a-109">None</span></span>

## <a name="parent-element"></a><span data-ttu-id="cde4a-110">Elemento pai</span><span class="sxs-lookup"><span data-stu-id="cde4a-110">Parent element</span></span>

|     | <span data-ttu-id="cde4a-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="cde4a-111">Description</span></span> |
| --- | ------------|
| [<span data-ttu-id="cde4a-112"> **\<sectionname >** Elementos</span><span class="sxs-lookup"><span data-stu-id="cde4a-112">**\<sectionName>** Element</span></span>](custom-element-2.md) | <span data-ttu-id="cde4a-113">Define as configurações para seções de configuração personalizadas que usam as classes <xref:System.Configuration.NameValueSectionHandler> e <xref:System.Configuration.DictionarySectionHandler>.</span><span class="sxs-lookup"><span data-stu-id="cde4a-113">Defines settings for custom configuration sections that use the <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler> classes.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="cde4a-114">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="cde4a-114">Child elements</span></span>

<span data-ttu-id="cde4a-115">Nenhum</span><span class="sxs-lookup"><span data-stu-id="cde4a-115">None</span></span>

## <a name="remarks"></a><span data-ttu-id="cde4a-116">Comentários</span><span class="sxs-lookup"><span data-stu-id="cde4a-116">Remarks</span></span>

<span data-ttu-id="cde4a-117">Você pode usar o elemento **\<clear >** para remover todas as configurações do seu aplicativo que foram definidas em um nível mais alto na hierarquia do arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="cde4a-117">You can use the **\<clear>** element to remove all settings from your application that were defined at a higher level in the configuration file hierarchy.</span></span>

## <a name="example"></a><span data-ttu-id="cde4a-118">Exemplo</span><span class="sxs-lookup"><span data-stu-id="cde4a-118">Example</span></span>

<span data-ttu-id="cde4a-119">Este exemplo define um arquivo de configuração de computador e um arquivo de configuração de aplicativo e mostra como usar o **\<apagar >** elemento em um arquivo de configuração de aplicativo para limpar as seções definidas anteriormente no arquivo de configuração de computador.</span><span class="sxs-lookup"><span data-stu-id="cde4a-119">This example defines a machine configuration file and an application configuration file and shows how to use the **\<clear>** element in an application configuration file to clear sections previously defined in the machine configuration file.</span></span>

<span data-ttu-id="cde4a-120">O código do arquivo de configuração do computador a seguir declara a seção **\<myseção >** :</span><span class="sxs-lookup"><span data-stu-id="cde4a-120">The following machine configuration file code declares the section **\<mySection>**:</span></span>

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

<span data-ttu-id="cde4a-121">O código do arquivo de configuração de aplicativo a seguir remove todas as configurações de **\<myseção >** .</span><span class="sxs-lookup"><span data-stu-id="cde4a-121">The following application configuration file code removes all settings from **\<mySection>**.</span></span> <span data-ttu-id="cde4a-122">O aplicativo não pode recuperar nenhuma das configurações que foram declaradas no na seção **\<myseção >** do arquivo de configuração do computador.</span><span class="sxs-lookup"><span data-stu-id="cde4a-122">The application cannot retrieve any of the settings that were declared in the in the **\<mySection>** section of the machine configuration file.</span></span>

```xml
<!-- Application configuration file -->
<configuration>
  <mySection>
    <clear/>
  </mySection>
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="cde4a-123">arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="cde4a-123">Configuration file</span></span>

<span data-ttu-id="cde4a-124">Esse elemento pode ser usado no arquivo de configuração do aplicativo, no arquivo de configuração do computador (*Machine. config*) e nos arquivos *Web. config* que não estão no nível do diretório do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="cde4a-124">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="cde4a-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cde4a-125">See also</span></span>

- [<span data-ttu-id="cde4a-126">Esquema do arquivo de configuração para o .NET Framework</span><span class="sxs-lookup"><span data-stu-id="cde4a-126">Configuration file schema for the .NET Framework</span></span>](index.md)
