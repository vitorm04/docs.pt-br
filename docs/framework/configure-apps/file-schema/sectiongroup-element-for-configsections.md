---
title: Elemento <sectionGroup> para <configSections>
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/sectionGroup
helpviewer_keywords:
- sectionGroup Element
- <sectionGroup> Element
ms.assetid: 6c27f9e2-809c-4bc9-aca9-72f90360e7a3
author: rpetrusha
ms.author: mairaw
ms.openlocfilehash: 4e28e8ccea1090e6a5704b541e09dc11681278ed
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920646"
---
# <a name="sectiongroup-element-for-configsections"></a><span data-ttu-id="3e241-102">\<elemento de > de seção \<para configSections ></span><span class="sxs-lookup"><span data-stu-id="3e241-102">\<sectionGroup> element for \<configSections></span></span>

<span data-ttu-id="3e241-103">Define um namespace para seções de configuração.</span><span class="sxs-lookup"><span data-stu-id="3e241-103">Defines a namespace for configuration sections.</span></span>

<span data-ttu-id="3e241-104">[ **\<configuration>** ](configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="3e241-104">[**\<configuration>**](configuration-element.md) </span></span>  
<span data-ttu-id="3e241-105">&nbsp;&nbsp;[ **\<configSections>** ](configsections-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="3e241-105">&nbsp;&nbsp;[**\<configSections>**](configsections-element-for-configuration.md) </span></span>  
<span data-ttu-id="3e241-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<sectionGroup>**</span><span class="sxs-lookup"><span data-stu-id="3e241-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<sectionGroup>**</span></span>

## <a name="syntax"></a><span data-ttu-id="3e241-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3e241-107">Syntax</span></span>

```xml
<sectionGroup name="section group name">
  <!-- Configuration sections -->
</sectionGroup>
```

## <a name="attribute"></a><span data-ttu-id="3e241-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="3e241-108">Attribute</span></span>

|           | <span data-ttu-id="3e241-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="3e241-109">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="3e241-110">**name**</span><span class="sxs-lookup"><span data-stu-id="3e241-110">**name**</span></span>  | <span data-ttu-id="3e241-111">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="3e241-111">Required attribute.</span></span><br><br><span data-ttu-id="3e241-112">Especifica o nome do grupo de seções que você está definindo.</span><span class="sxs-lookup"><span data-stu-id="3e241-112">Specifies the name of the section group you are defining.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="3e241-113">Elemento pai</span><span class="sxs-lookup"><span data-stu-id="3e241-113">Parent element</span></span>

|     | <span data-ttu-id="3e241-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="3e241-114">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="3e241-115">configSections > elemento  **\<** </span><span class="sxs-lookup"><span data-stu-id="3e241-115">**\<configSections>** Element</span></span>](configsections-element-for-configuration.md) | <span data-ttu-id="3e241-116">Contém as declarações de namespace e seção de configuração.</span><span class="sxs-lookup"><span data-stu-id="3e241-116">Contains configuration section and namespace declarations.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="3e241-117">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="3e241-117">Child elements</span></span>

|     | <span data-ttu-id="3e241-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="3e241-118">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="3e241-119"> **\<> da seção**</span><span class="sxs-lookup"><span data-stu-id="3e241-119">**\<section>**</span></span>](section-element.md) | <span data-ttu-id="3e241-120">Contém uma declaração de seção de configuração.</span><span class="sxs-lookup"><span data-stu-id="3e241-120">Contains a configuration section declaration.</span></span> |

## <a name="remarks"></a><span data-ttu-id="3e241-121">Comentários</span><span class="sxs-lookup"><span data-stu-id="3e241-121">Remarks</span></span>

<span data-ttu-id="3e241-122">Declarar um grupo de seções cria uma marca de contêiner para seções de configuração e garante que não haja conflitos de nomenclatura com seções de configuração definidas por outra pessoa.</span><span class="sxs-lookup"><span data-stu-id="3e241-122">Declaring a section group creates a container tag for configuration sections and ensures that there are no naming conflicts with configuration sections defined by someone else.</span></span> <span data-ttu-id="3e241-123">Você pode aninhar  **\<** elementos de > de seção entre si.</span><span class="sxs-lookup"><span data-stu-id="3e241-123">You can nest **\<sectionGroup>** elements within each other.</span></span>

## <a name="example"></a><span data-ttu-id="3e241-124">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3e241-124">Example</span></span>

<span data-ttu-id="3e241-125">O exemplo a seguir mostra como declarar um grupo de seções e declarar seções dentro de um grupo de seções:</span><span class="sxs-lookup"><span data-stu-id="3e241-125">The following example shows how to declare a section group and declare sections within a section group:</span></span>

```xml
<configuration>
  <configSections>
    <sectionGroup name="mySectionGroup">
      <section name="mySection"
               type="System.Configuration.NameValueSectionHandler,System" />
    </sectionGroup>
  </configSections>
  <mySectionGroup>
    <mySection>
      <add key="key1" value="value1" />
    </mySection>
  </mySectionGroup>
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="3e241-126">arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="3e241-126">Configuration file</span></span>

<span data-ttu-id="3e241-127">Esse elemento pode ser usado no arquivo de configuração do aplicativo, no arquivo de configuração do computador (*Machine. config*) e nos arquivos *Web. config* que não estão no nível do diretório do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="3e241-127">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="3e241-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3e241-128">See also</span></span>

- [<span data-ttu-id="3e241-129">Esquema do arquivo de configuração para o .NET Framework</span><span class="sxs-lookup"><span data-stu-id="3e241-129">Configuration file schema for the .NET Framework</span></span>](index.md)
