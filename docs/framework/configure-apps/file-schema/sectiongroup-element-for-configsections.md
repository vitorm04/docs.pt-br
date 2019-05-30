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
ms.openlocfilehash: 750708483f9680745eef4531d86fa7ecaa329f51
ms.sourcegitcommit: 621a5f6df00152006160987395b93b5b55f7ffcd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66301188"
---
# <a name="sectiongroup-element-for-configsections"></a><span data-ttu-id="a9348-102">\<sectionGroup > elemento para \<configSections ></span><span class="sxs-lookup"><span data-stu-id="a9348-102">\<sectionGroup> element for \<configSections></span></span>

<span data-ttu-id="a9348-103">Define um namespace para seções de configuração.</span><span class="sxs-lookup"><span data-stu-id="a9348-103">Defines a namespace for configuration sections.</span></span>

<span data-ttu-id="a9348-104">[ **\<configuration>** ](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="a9348-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="a9348-105">&nbsp;&nbsp;[ **\<configSections>** ](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="a9348-105">&nbsp;&nbsp;[**\<configSections>**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) </span></span>  
<span data-ttu-id="a9348-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<sectionGroup>**</span><span class="sxs-lookup"><span data-stu-id="a9348-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<sectionGroup>**</span></span>

## <a name="syntax"></a><span data-ttu-id="a9348-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a9348-107">Syntax</span></span>

```xml
<sectionGroup name="section group name">
  <!-- Configuration sections -->
</sectionGroup>
```

## <a name="attribute"></a><span data-ttu-id="a9348-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="a9348-108">Attribute</span></span>

|           | <span data-ttu-id="a9348-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="a9348-109">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="a9348-110">**name**</span><span class="sxs-lookup"><span data-stu-id="a9348-110">**name**</span></span>  | <span data-ttu-id="a9348-111">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="a9348-111">Required attribute.</span></span><br><br><span data-ttu-id="a9348-112">Especifica o nome do grupo de seções que você está definindo.</span><span class="sxs-lookup"><span data-stu-id="a9348-112">Specifies the name of the section group you are defining.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="a9348-113">Elemento pai</span><span class="sxs-lookup"><span data-stu-id="a9348-113">Parent element</span></span>

|     | <span data-ttu-id="a9348-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="a9348-114">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="a9348-115"> *\*\<configSections>** Element</span><span class="sxs-lookup"><span data-stu-id="a9348-115">**\<configSections>** Element</span></span>](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) | <span data-ttu-id="a9348-116">Contém as declarações de namespace e a seção de configuração.</span><span class="sxs-lookup"><span data-stu-id="a9348-116">Contains configuration section and namespace declarations.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="a9348-117">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="a9348-117">Child elements</span></span>

|     | <span data-ttu-id="a9348-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="a9348-118">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="a9348-119"> *\*\<section>** </span><span class="sxs-lookup"><span data-stu-id="a9348-119">**\<section>**</span></span>](~/docs/framework/configure-apps/file-schema/section-element.md) | <span data-ttu-id="a9348-120">Contém uma declaração de seção de configuração.</span><span class="sxs-lookup"><span data-stu-id="a9348-120">Contains a configuration section declaration.</span></span> |

## <a name="remarks"></a><span data-ttu-id="a9348-121">Comentários</span><span class="sxs-lookup"><span data-stu-id="a9348-121">Remarks</span></span>

<span data-ttu-id="a9348-122">Declarando um grupo de seção cria uma marca de contêiner para as seções de configuração e garante que não haja nenhum conflito de nomenclatura com seções de configuração definidas por outra pessoa.</span><span class="sxs-lookup"><span data-stu-id="a9348-122">Declaring a section group creates a container tag for configuration sections and ensures that there are no naming conflicts with configuration sections defined by someone else.</span></span> <span data-ttu-id="a9348-123">Você pode aninhar  **\<sectionGroup >** elementos dentro do outro.</span><span class="sxs-lookup"><span data-stu-id="a9348-123">You can nest **\<sectionGroup>** elements within each other.</span></span>

## <a name="example"></a><span data-ttu-id="a9348-124">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a9348-124">Example</span></span>

<span data-ttu-id="a9348-125">O exemplo a seguir mostra como declarar um grupo de seção e declarar seções dentro de um grupo de seções:</span><span class="sxs-lookup"><span data-stu-id="a9348-125">The following example shows how to declare a section group and declare sections within a section group:</span></span>

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

## <a name="configuration-file"></a><span data-ttu-id="a9348-126">arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="a9348-126">Configuration file</span></span>

<span data-ttu-id="a9348-127">Esse elemento pode ser usado no arquivo de configuração do aplicativo, arquivo de configuração de máquina (*Machine. config*), e *Web. config* arquivos que não estão no nível de diretório do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a9348-127">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="a9348-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a9348-128">See also</span></span>

- [<span data-ttu-id="a9348-129">Esquema de arquivo de configuração para o .NET Framework</span><span class="sxs-lookup"><span data-stu-id="a9348-129">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
