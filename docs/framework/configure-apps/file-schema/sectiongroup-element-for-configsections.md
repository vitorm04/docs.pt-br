---
title: Elemento <sectionGroup> para <configSections>
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/sectionGroup
helpviewer_keywords:
- sectionGroup Element
- <sectionGroup> Element
ms.assetid: 6c27f9e2-809c-4bc9-aca9-72f90360e7a3
author: guardrex
ms.author: mairaw
ms.openlocfilehash: ce0fa5bd77a7b9012d69fd5afab1f4c332f213a7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61673817"
---
# <a name="sectiongroup-element-for-configsections"></a><span data-ttu-id="f6f60-102">\<sectionGroup > elemento para \<configSections ></span><span class="sxs-lookup"><span data-stu-id="f6f60-102">\<sectionGroup> element for \<configSections></span></span>

<span data-ttu-id="f6f60-103">Define um namespace para seções de configuração.</span><span class="sxs-lookup"><span data-stu-id="f6f60-103">Defines a namespace for configuration sections.</span></span>

<span data-ttu-id="f6f60-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="f6f60-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="f6f60-105">&nbsp;&nbsp;[**\<configSections>**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="f6f60-105">&nbsp;&nbsp;[**\<configSections>**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) </span></span>  
<span data-ttu-id="f6f60-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<sectionGroup>**</span><span class="sxs-lookup"><span data-stu-id="f6f60-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<sectionGroup>**</span></span>

## <a name="syntax"></a><span data-ttu-id="f6f60-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f6f60-107">Syntax</span></span>

```xml
<sectionGroup name="section group name">
  <!-- Configuration sections -->
</sectionGroup>
```

## <a name="attribute"></a><span data-ttu-id="f6f60-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="f6f60-108">Attribute</span></span>

|           | <span data-ttu-id="f6f60-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="f6f60-109">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="f6f60-110">**name**</span><span class="sxs-lookup"><span data-stu-id="f6f60-110">**name**</span></span>  | <span data-ttu-id="f6f60-111">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="f6f60-111">Required attribute.</span></span><br><br><span data-ttu-id="f6f60-112">Especifica o nome do grupo de seções que você está definindo.</span><span class="sxs-lookup"><span data-stu-id="f6f60-112">Specifies the name of the section group you are defining.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="f6f60-113">Elemento pai</span><span class="sxs-lookup"><span data-stu-id="f6f60-113">Parent element</span></span>

|     | <span data-ttu-id="f6f60-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="f6f60-114">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="f6f60-115">**\<configSections>** Element</span><span class="sxs-lookup"><span data-stu-id="f6f60-115">**\<configSections>** Element</span></span>](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) | <span data-ttu-id="f6f60-116">Contém as declarações de namespace e a seção de configuração.</span><span class="sxs-lookup"><span data-stu-id="f6f60-116">Contains configuration section and namespace declarations.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="f6f60-117">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="f6f60-117">Child elements</span></span>

|     | <span data-ttu-id="f6f60-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="f6f60-118">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="f6f60-119">**\<section>**</span><span class="sxs-lookup"><span data-stu-id="f6f60-119">**\<section>**</span></span>](~/docs/framework/configure-apps/file-schema/section-element.md) | <span data-ttu-id="f6f60-120">Contém uma declaração de seção de configuração.</span><span class="sxs-lookup"><span data-stu-id="f6f60-120">Contains a configuration section declaration.</span></span> |

## <a name="remarks"></a><span data-ttu-id="f6f60-121">Comentários</span><span class="sxs-lookup"><span data-stu-id="f6f60-121">Remarks</span></span>

<span data-ttu-id="f6f60-122">Declarando um grupo de seção cria uma marca de contêiner para as seções de configuração e garante que não haja nenhum conflito de nomenclatura com seções de configuração definidas por outra pessoa.</span><span class="sxs-lookup"><span data-stu-id="f6f60-122">Declaring a section group creates a container tag for configuration sections and ensures that there are no naming conflicts with configuration sections defined by someone else.</span></span> <span data-ttu-id="f6f60-123">Você pode aninhar  **\<sectionGroup >** elementos dentro do outro.</span><span class="sxs-lookup"><span data-stu-id="f6f60-123">You can nest **\<sectionGroup>** elements within each other.</span></span>

## <a name="example"></a><span data-ttu-id="f6f60-124">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f6f60-124">Example</span></span>

<span data-ttu-id="f6f60-125">O exemplo a seguir mostra como declarar um grupo de seção e declarar seções dentro de um grupo de seções:</span><span class="sxs-lookup"><span data-stu-id="f6f60-125">The following example shows how to declare a section group and declare sections within a section group:</span></span>

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

## <a name="configuration-file"></a><span data-ttu-id="f6f60-126">arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="f6f60-126">Configuration file</span></span>

<span data-ttu-id="f6f60-127">Esse elemento pode ser usado no arquivo de configuração do aplicativo, arquivo de configuração de máquina (*Machine. config*), e *Web. config* arquivos que não estão no nível de diretório do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f6f60-127">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="f6f60-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f6f60-128">See also</span></span>

- [<span data-ttu-id="f6f60-129">Esquema de arquivo de configuração para o .NET Framework</span><span class="sxs-lookup"><span data-stu-id="f6f60-129">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
