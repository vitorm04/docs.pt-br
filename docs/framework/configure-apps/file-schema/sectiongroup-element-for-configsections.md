---
title: Elemento <sectionGroup> para <configSections>
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/sectionGroup
helpviewer_keywords:
- sectionGroup Element
- <sectionGroup> Element
ms.assetid: 6c27f9e2-809c-4bc9-aca9-72f90360e7a3
ms.openlocfilehash: eb221027470fe6e485f8fcc4b939b71e4f219712
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "77215258"
---
# <a name="sectiongroup-element-for-configsections"></a><span data-ttu-id="4e2f5-102">Elemento \<sectionGroup> para \<configSections></span><span class="sxs-lookup"><span data-stu-id="4e2f5-102">\<sectionGroup> element for \<configSections></span></span>

<span data-ttu-id="4e2f5-103">Define um namespace para seções de configuração.</span><span class="sxs-lookup"><span data-stu-id="4e2f5-103">Defines a namespace for configuration sections.</span></span>

[**\<configuration>**](configuration-element.md)\
&nbsp;&nbsp;[**\<configSections>**](configsections-element-for-configuration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<sectionGroup>**

## <a name="syntax"></a><span data-ttu-id="4e2f5-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4e2f5-104">Syntax</span></span>

```xml
<sectionGroup name="section group name">
  <!-- Configuration sections -->
</sectionGroup>
```

## <a name="attribute"></a><span data-ttu-id="4e2f5-105">Atributo</span><span class="sxs-lookup"><span data-stu-id="4e2f5-105">Attribute</span></span>

|           | <span data-ttu-id="4e2f5-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="4e2f5-106">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="4e2f5-107">**name**</span><span class="sxs-lookup"><span data-stu-id="4e2f5-107">**name**</span></span>  | <span data-ttu-id="4e2f5-108">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="4e2f5-108">Required attribute.</span></span><br><br><span data-ttu-id="4e2f5-109">Especifica o nome do grupo de seções que você está definindo.</span><span class="sxs-lookup"><span data-stu-id="4e2f5-109">Specifies the name of the section group you are defining.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="4e2f5-110">Elemento pai</span><span class="sxs-lookup"><span data-stu-id="4e2f5-110">Parent element</span></span>

|     | <span data-ttu-id="4e2f5-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="4e2f5-111">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="4e2f5-112">**\<configSections>** Elementos</span><span class="sxs-lookup"><span data-stu-id="4e2f5-112">**\<configSections>** Element</span></span>](configsections-element-for-configuration.md) | <span data-ttu-id="4e2f5-113">Contém as declarações de namespace e seção de configuração.</span><span class="sxs-lookup"><span data-stu-id="4e2f5-113">Contains configuration section and namespace declarations.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="4e2f5-114">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="4e2f5-114">Child elements</span></span>

|     | <span data-ttu-id="4e2f5-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="4e2f5-115">Description</span></span> |
| --- | ----------- |
| [**\<section>**](section-element.md) | <span data-ttu-id="4e2f5-116">Contém uma declaração de seção de configuração.</span><span class="sxs-lookup"><span data-stu-id="4e2f5-116">Contains a configuration section declaration.</span></span> |

## <a name="remarks"></a><span data-ttu-id="4e2f5-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="4e2f5-117">Remarks</span></span>

<span data-ttu-id="4e2f5-118">Declarar um grupo de seções cria uma marca de contêiner para seções de configuração e garante que não haja conflitos de nomenclatura com seções de configuração definidas por outra pessoa.</span><span class="sxs-lookup"><span data-stu-id="4e2f5-118">Declaring a section group creates a container tag for configuration sections and ensures that there are no naming conflicts with configuration sections defined by someone else.</span></span> <span data-ttu-id="4e2f5-119">Você pode aninhar **\<sectionGroup>** elementos dentro uns dos outros.</span><span class="sxs-lookup"><span data-stu-id="4e2f5-119">You can nest **\<sectionGroup>** elements within each other.</span></span>

## <a name="example"></a><span data-ttu-id="4e2f5-120">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4e2f5-120">Example</span></span>

<span data-ttu-id="4e2f5-121">O exemplo a seguir mostra como declarar um grupo de seções e declarar seções dentro de um grupo de seções:</span><span class="sxs-lookup"><span data-stu-id="4e2f5-121">The following example shows how to declare a section group and declare sections within a section group:</span></span>

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

## <a name="configuration-file"></a><span data-ttu-id="4e2f5-122">Arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="4e2f5-122">Configuration file</span></span>

<span data-ttu-id="4e2f5-123">Esse elemento pode ser usado no arquivo de configuração do aplicativo, no arquivo de configuração do computador (*Machine. config*) e nos arquivos *Web. config* que não estão no nível do diretório do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="4e2f5-123">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="4e2f5-124">Confira também</span><span class="sxs-lookup"><span data-stu-id="4e2f5-124">See also</span></span>

- [<span data-ttu-id="4e2f5-125">Esquema do arquivo de configuração para o .NET Framework</span><span class="sxs-lookup"><span data-stu-id="4e2f5-125">Configuration file schema for the .NET Framework</span></span>](index.md)
