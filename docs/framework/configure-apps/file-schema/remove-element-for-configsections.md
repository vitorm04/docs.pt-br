---
title: Elemento <remove> para <configSections>
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/remove
helpviewer_keywords:
- remove Element
- <remove> Element
ms.assetid: ae4d82e0-e8fe-468c-81ab-46d63c4d66a8
author: mairaw
ms.author: mairaw
ms.openlocfilehash: efc7208aa51cbf6abdb2fe151d48071c0aa95b5c
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/14/2019
ms.locfileid: "74089048"
---
# <a name="remove-element-for-configsections"></a><span data-ttu-id="e750b-102">\<remover > elemento para \<configSections ></span><span class="sxs-lookup"><span data-stu-id="e750b-102">\<remove> element for \<configSections></span></span>

<span data-ttu-id="e750b-103">Remove uma seção ou um grupo de seções predefinido.</span><span class="sxs-lookup"><span data-stu-id="e750b-103">Removes a predefined section or section group.</span></span>

<span data-ttu-id="e750b-104">[ **\<configuration>** ](configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="e750b-104">[**\<configuration>**](configuration-element.md)</span></span>\
<span data-ttu-id="e750b-105">&nbsp;&nbsp;[ **\<configsections >** ](configsections-element-for-configuration.md)</span><span class="sxs-lookup"><span data-stu-id="e750b-105">&nbsp;&nbsp;[**\<configSections>**](configsections-element-for-configuration.md)</span></span>\
<span data-ttu-id="e750b-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<remover >**</span><span class="sxs-lookup"><span data-stu-id="e750b-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**</span></span>

## <a name="syntax"></a><span data-ttu-id="e750b-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e750b-107">Syntax</span></span>

```xml
<remove name="section name or section group name" />
```

## <a name="attribute"></a><span data-ttu-id="e750b-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="e750b-108">Attribute</span></span>

|           | <span data-ttu-id="e750b-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="e750b-109">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="e750b-110">**name**</span><span class="sxs-lookup"><span data-stu-id="e750b-110">**name**</span></span>  | <span data-ttu-id="e750b-111">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="e750b-111">Required attribute.</span></span><br><br><span data-ttu-id="e750b-112">Especifica o nome da seção ou do grupo de seções a ser removido.</span><span class="sxs-lookup"><span data-stu-id="e750b-112">Specifies the name of the section or section group to remove.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="e750b-113">Elemento pai</span><span class="sxs-lookup"><span data-stu-id="e750b-113">Parent element</span></span>

|     | <span data-ttu-id="e750b-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="e750b-114">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="e750b-115"> **\<configsections >** Elementos</span><span class="sxs-lookup"><span data-stu-id="e750b-115">**\<configSections>** Element</span></span>](configsections-element-for-configuration.md) | <span data-ttu-id="e750b-116">Contém as declarações de namespace e seção de configuração.</span><span class="sxs-lookup"><span data-stu-id="e750b-116">Contains configuration section and namespace declarations.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="e750b-117">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="e750b-117">Child elements</span></span>

<span data-ttu-id="e750b-118">Nenhum</span><span class="sxs-lookup"><span data-stu-id="e750b-118">None</span></span>

## <a name="remarks"></a><span data-ttu-id="e750b-119">Comentários</span><span class="sxs-lookup"><span data-stu-id="e750b-119">Remarks</span></span>

<span data-ttu-id="e750b-120">Você pode usar a **\<remover >** elemento para remover seções e grupos de seções do seu aplicativo que foram definidos em um nível mais alto na hierarquia do arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="e750b-120">You can use the **\<remove>** element to remove sections and section groups from your application that were defined at a higher level in the configuration file hierarchy.</span></span>

## <a name="example"></a><span data-ttu-id="e750b-121">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e750b-121">Example</span></span>

<span data-ttu-id="e750b-122">O exemplo a seguir mostra como usar o elemento **\<remover >** em um arquivo de configuração de aplicativo para remover uma seção definida anteriormente no arquivo de configuração de computador.</span><span class="sxs-lookup"><span data-stu-id="e750b-122">The following example shows how to use the **\<remove>** element in an application configuration file to remove a section previously defined in the machine configuration file.</span></span>

<span data-ttu-id="e750b-123">O código do arquivo de configuração do computador a seguir declara a seção **\<sampleSection >** :</span><span class="sxs-lookup"><span data-stu-id="e750b-123">The following machine configuration file code declares the section **\<sampleSection>**:</span></span>

```xml
<!-- Machine.config file -->
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

<span data-ttu-id="e750b-124">O código do arquivo de configuração de aplicativo a seguir remove a seção **\<sampleSection >** .</span><span class="sxs-lookup"><span data-stu-id="e750b-124">The following application configuration file code removes the **\<sampleSection>** section.</span></span> <span data-ttu-id="e750b-125">Após a remoção, o aplicativo não poderá recuperar as configurações em **\<sampleSection >** .</span><span class="sxs-lookup"><span data-stu-id="e750b-125">After removal, the application cannot retrieve the settings in **\<sampleSection>**.</span></span>

```xml
<!-- Application configuration file -->
<configuration>
  <configSections>
    <remove name="sampleSection"/>
  </configSections>
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="e750b-126">arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="e750b-126">Configuration file</span></span>

<span data-ttu-id="e750b-127">Esse elemento pode ser usado no arquivo de configuração do aplicativo, no arquivo de configuração do computador (*Machine. config*) e nos arquivos *Web. config* que não estão no nível do diretório do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e750b-127">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="e750b-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e750b-128">See also</span></span>

- [<span data-ttu-id="e750b-129">Esquema do arquivo de configuração para o .NET Framework</span><span class="sxs-lookup"><span data-stu-id="e750b-129">Configuration file schema for the .NET Framework</span></span>](index.md)
