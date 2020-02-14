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
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77215258"
---
# <a name="sectiongroup-element-for-configsections"></a><span data-ttu-id="dee03-102">\<elemento > de seção para \<configSections ></span><span class="sxs-lookup"><span data-stu-id="dee03-102">\<sectionGroup> element for \<configSections></span></span>

<span data-ttu-id="dee03-103">Define um namespace para seções de configuração.</span><span class="sxs-lookup"><span data-stu-id="dee03-103">Defines a namespace for configuration sections.</span></span>

<span data-ttu-id="dee03-104">[ **\<configuration>** ](configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="dee03-104">[**\<configuration>**](configuration-element.md)</span></span>\
<span data-ttu-id="dee03-105">&nbsp;&nbsp;[ **\<configsections >** ](configsections-element-for-configuration.md)</span><span class="sxs-lookup"><span data-stu-id="dee03-105">&nbsp;&nbsp;[**\<configSections>**](configsections-element-for-configuration.md)</span></span>\
<span data-ttu-id="dee03-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<da seção** ></span><span class="sxs-lookup"><span data-stu-id="dee03-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<sectionGroup>**</span></span>

## <a name="syntax"></a><span data-ttu-id="dee03-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="dee03-107">Syntax</span></span>

```xml
<sectionGroup name="section group name">
  <!-- Configuration sections -->
</sectionGroup>
```

## <a name="attribute"></a><span data-ttu-id="dee03-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="dee03-108">Attribute</span></span>

|           | <span data-ttu-id="dee03-109">DESCRIÇÃO</span><span class="sxs-lookup"><span data-stu-id="dee03-109">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="dee03-110">**name**</span><span class="sxs-lookup"><span data-stu-id="dee03-110">**name**</span></span>  | <span data-ttu-id="dee03-111">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="dee03-111">Required attribute.</span></span><br><br><span data-ttu-id="dee03-112">Especifica o nome do grupo de seções que você está definindo.</span><span class="sxs-lookup"><span data-stu-id="dee03-112">Specifies the name of the section group you are defining.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="dee03-113">Elemento pai</span><span class="sxs-lookup"><span data-stu-id="dee03-113">Parent element</span></span>

|     | <span data-ttu-id="dee03-114">DESCRIÇÃO</span><span class="sxs-lookup"><span data-stu-id="dee03-114">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="dee03-115"> **\<configsections >** Elementos</span><span class="sxs-lookup"><span data-stu-id="dee03-115">**\<configSections>** Element</span></span>](configsections-element-for-configuration.md) | <span data-ttu-id="dee03-116">Contém as declarações de namespace e seção de configuração.</span><span class="sxs-lookup"><span data-stu-id="dee03-116">Contains configuration section and namespace declarations.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="dee03-117">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="dee03-117">Child elements</span></span>

|     | <span data-ttu-id="dee03-118">DESCRIÇÃO</span><span class="sxs-lookup"><span data-stu-id="dee03-118">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="dee03-119"> **\<seção >** </span><span class="sxs-lookup"><span data-stu-id="dee03-119">**\<section>**</span></span>](section-element.md) | <span data-ttu-id="dee03-120">Contém uma declaração de seção de configuração.</span><span class="sxs-lookup"><span data-stu-id="dee03-120">Contains a configuration section declaration.</span></span> |

## <a name="remarks"></a><span data-ttu-id="dee03-121">Comentários</span><span class="sxs-lookup"><span data-stu-id="dee03-121">Remarks</span></span>

<span data-ttu-id="dee03-122">Declarar um grupo de seções cria uma marca de contêiner para seções de configuração e garante que não haja conflitos de nomenclatura com seções de configuração definidas por outra pessoa.</span><span class="sxs-lookup"><span data-stu-id="dee03-122">Declaring a section group creates a container tag for configuration sections and ensures that there are no naming conflicts with configuration sections defined by someone else.</span></span> <span data-ttu-id="dee03-123">Você pode aninhar\<elementos do **> de seções** entre si.</span><span class="sxs-lookup"><span data-stu-id="dee03-123">You can nest **\<sectionGroup>** elements within each other.</span></span>

## <a name="example"></a><span data-ttu-id="dee03-124">Exemplo</span><span class="sxs-lookup"><span data-stu-id="dee03-124">Example</span></span>

<span data-ttu-id="dee03-125">O exemplo a seguir mostra como declarar um grupo de seções e declarar seções dentro de um grupo de seções:</span><span class="sxs-lookup"><span data-stu-id="dee03-125">The following example shows how to declare a section group and declare sections within a section group:</span></span>

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

## <a name="configuration-file"></a><span data-ttu-id="dee03-126">Arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="dee03-126">Configuration file</span></span>

<span data-ttu-id="dee03-127">Esse elemento pode ser usado no arquivo de configuração do aplicativo, no arquivo de configuração do computador (*Machine. config*) e nos arquivos *Web. config* que não estão no nível do diretório do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="dee03-127">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="dee03-128">Confira também</span><span class="sxs-lookup"><span data-stu-id="dee03-128">See also</span></span>

- [<span data-ttu-id="dee03-129">Esquema do arquivo de configuração para o .NET Framework</span><span class="sxs-lookup"><span data-stu-id="dee03-129">Configuration file schema for the .NET Framework</span></span>](index.md)
