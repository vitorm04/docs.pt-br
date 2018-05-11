---
title: '&lt;sectionGroup&gt; elemento para &lt;configSections&gt;'
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/sectionGroup
helpviewer_keywords:
- sectionGroup Element
- <sectionGroup> Element
ms.assetid: 6c27f9e2-809c-4bc9-aca9-72f90360e7a3
author: guardrex
ms.author: mairaw
ms.openlocfilehash: b898c81700e95ec9bc94e04c5a76494b7ac4b0dc
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="sectiongroup-element-for-configsections"></a><span data-ttu-id="3a710-102">\<sectionGroup > elemento \<configSections ></span><span class="sxs-lookup"><span data-stu-id="3a710-102">\<sectionGroup> element for \<configSections></span></span>

<span data-ttu-id="3a710-103">Define um namespace para seções de configuração.</span><span class="sxs-lookup"><span data-stu-id="3a710-103">Defines a namespace for configuration sections.</span></span>

<span data-ttu-id="3a710-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="3a710-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="3a710-105">&nbsp;&nbsp;[**\<configSections >**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="3a710-105">&nbsp;&nbsp;[**\<configSections>**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) </span></span>  
<span data-ttu-id="3a710-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<sectionGroup >**</span><span class="sxs-lookup"><span data-stu-id="3a710-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<sectionGroup>**</span></span>

## <a name="syntax"></a><span data-ttu-id="3a710-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3a710-107">Syntax</span></span>

```xml
<sectionGroup name="section group name">
  <!-- Configuration sections -->
</sectionGroup>
```

## <a name="attribute"></a><span data-ttu-id="3a710-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="3a710-108">Attribute</span></span>

|           | <span data-ttu-id="3a710-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="3a710-109">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="3a710-110">**name**</span><span class="sxs-lookup"><span data-stu-id="3a710-110">**name**</span></span>  | <span data-ttu-id="3a710-111">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="3a710-111">Required attribute.</span></span><br><br><span data-ttu-id="3a710-112">Especifica o nome do grupo de seções que você está definindo.</span><span class="sxs-lookup"><span data-stu-id="3a710-112">Specifies the name of the section group you are defining.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="3a710-113">Elemento pai</span><span class="sxs-lookup"><span data-stu-id="3a710-113">Parent element</span></span>

|     | <span data-ttu-id="3a710-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="3a710-114">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="3a710-115">**\<configSections >** elemento</span><span class="sxs-lookup"><span data-stu-id="3a710-115">**\<configSections>** Element</span></span>](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) | <span data-ttu-id="3a710-116">Contém declarações de namespace e de seção de configuração.</span><span class="sxs-lookup"><span data-stu-id="3a710-116">Contains configuration section and namespace declarations.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="3a710-117">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="3a710-117">Child elements</span></span>

|     | <span data-ttu-id="3a710-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="3a710-118">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="3a710-119">**\<seção >**</span><span class="sxs-lookup"><span data-stu-id="3a710-119">**\<section>**</span></span>](~/docs/framework/configure-apps/file-schema/section-element.md) | <span data-ttu-id="3a710-120">Contém uma declaração de seção de configuração.</span><span class="sxs-lookup"><span data-stu-id="3a710-120">Contains a configuration section declaration.</span></span> |

## <a name="remarks"></a><span data-ttu-id="3a710-121">Comentários</span><span class="sxs-lookup"><span data-stu-id="3a710-121">Remarks</span></span>

<span data-ttu-id="3a710-122">Declarando um grupo de seção cria uma marca de contêiner para seções de configuração e garante que não haja nenhum conflito de nomenclatura com seções de configuração definidas por outra pessoa.</span><span class="sxs-lookup"><span data-stu-id="3a710-122">Declaring a section group creates a container tag for configuration sections and ensures that there are no naming conflicts with configuration sections defined by someone else.</span></span> <span data-ttu-id="3a710-123">Você pode aninhar  **\<sectionGroup >** elementos dentro do outro.</span><span class="sxs-lookup"><span data-stu-id="3a710-123">You can nest **\<sectionGroup>** elements within each other.</span></span>

## <a name="example"></a><span data-ttu-id="3a710-124">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3a710-124">Example</span></span>

<span data-ttu-id="3a710-125">O exemplo a seguir mostra como declarar um grupo de seções e declarar seções dentro de um grupo de seções:</span><span class="sxs-lookup"><span data-stu-id="3a710-125">The following example shows how to declare a section group and declare sections within a section group:</span></span>

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

## <a name="configuration-file"></a><span data-ttu-id="3a710-126">arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="3a710-126">Configuration file</span></span>

<span data-ttu-id="3a710-127">Esse elemento pode ser usado no arquivo de configuração do aplicativo, o arquivo de configuração de máquina (*Machine. config*), e *Web. config* arquivos que não estão no nível de diretório do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="3a710-127">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="3a710-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3a710-128">See also</span></span>

[<span data-ttu-id="3a710-129">Esquema de arquivo de configuração para o .NET Framework</span><span class="sxs-lookup"><span data-stu-id="3a710-129">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
