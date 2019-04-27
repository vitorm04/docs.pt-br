---
title: Elemento <configSections> para <configuration>
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections
helpviewer_keywords:
- configSections Element
- <configSections> Element
ms.assetid: 9f963c1b-dc3f-4220-a8b6-2dd7a5a8e039
author: guardrex
ms.author: mairaw
ms.openlocfilehash: dc2bb949c7db4f70c20c3c0b687cacafed8696df
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61674787"
---
# <a name="configsections-element-for-configuration"></a><span data-ttu-id="a7c4c-102">\<configSections > elemento para \<configuration ></span><span class="sxs-lookup"><span data-stu-id="a7c4c-102">\<configSections> element for \<configuration></span></span>

<span data-ttu-id="a7c4c-103">Contém as declarações de namespace e a seção de configuração.</span><span class="sxs-lookup"><span data-stu-id="a7c4c-103">Contains configuration section and namespace declarations.</span></span>

<span data-ttu-id="a7c4c-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="a7c4c-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="a7c4c-105">&nbsp;&nbsp;**\<configSections>**</span><span class="sxs-lookup"><span data-stu-id="a7c4c-105">&nbsp;&nbsp;**\<configSections>**</span></span>

## <a name="attributes"></a><span data-ttu-id="a7c4c-106">Atributos</span><span class="sxs-lookup"><span data-stu-id="a7c4c-106">Attributes</span></span>

<span data-ttu-id="a7c4c-107">Nenhum</span><span class="sxs-lookup"><span data-stu-id="a7c4c-107">None</span></span>

## <a name="parent-element"></a><span data-ttu-id="a7c4c-108">Elemento pai</span><span class="sxs-lookup"><span data-stu-id="a7c4c-108">Parent element</span></span>

|     | <span data-ttu-id="a7c4c-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="a7c4c-109">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="a7c4c-110">**\<configuration>**</span><span class="sxs-lookup"><span data-stu-id="a7c4c-110">**\<configuration>**</span></span>](~/docs/framework/configure-apps/file-schema/configuration-element.md) | <span data-ttu-id="a7c4c-111">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a7c4c-111">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="a7c4c-112">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="a7c4c-112">Child elements</span></span>

|     | <span data-ttu-id="a7c4c-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="a7c4c-113">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="a7c4c-114">**\<section>**</span><span class="sxs-lookup"><span data-stu-id="a7c4c-114">**\<section>**</span></span>](~/docs/framework/configure-apps/file-schema/section-element.md) | <span data-ttu-id="a7c4c-115">Contém uma declaração de seção de configuração.</span><span class="sxs-lookup"><span data-stu-id="a7c4c-115">Contains a configuration section declaration.</span></span> |
| [<span data-ttu-id="a7c4c-116">**\<sectionGroup>**</span><span class="sxs-lookup"><span data-stu-id="a7c4c-116">**\<sectionGroup>**</span></span>](~/docs/framework/configure-apps/file-schema/sectiongroup-element-for-configsections.md) | <span data-ttu-id="a7c4c-117">Define um namespace para seções de configuração.</span><span class="sxs-lookup"><span data-stu-id="a7c4c-117">Defines a namespace for configuration sections.</span></span> |
| [<span data-ttu-id="a7c4c-118">**\<remove>**</span><span class="sxs-lookup"><span data-stu-id="a7c4c-118">**\<remove>**</span></span>](~/docs/framework/configure-apps/file-schema/remove-element-for-configsections.md) | <span data-ttu-id="a7c4c-119">Remove uma seção predefinidos ou grupo da seção.</span><span class="sxs-lookup"><span data-stu-id="a7c4c-119">Removes a predefined section or section group.</span></span> |
| [<span data-ttu-id="a7c4c-120">**\<clear>**</span><span class="sxs-lookup"><span data-stu-id="a7c4c-120">**\<clear>**</span></span>](~/docs/framework/configure-apps/file-schema/clear-element-for-configsections.md) | <span data-ttu-id="a7c4c-121">Limpa todas as seções definidas anteriormente e grupos de seções.</span><span class="sxs-lookup"><span data-stu-id="a7c4c-121">Clears all previously defined sections and section groups.</span></span> |

## <a name="remarks"></a><span data-ttu-id="a7c4c-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="a7c4c-122">Remarks</span></span>

<span data-ttu-id="a7c4c-123">Se esse elemento estiver em um arquivo de configuração, ele deve ser o primeiro elemento filho do  **\<configuration >** elemento.</span><span class="sxs-lookup"><span data-stu-id="a7c4c-123">If this element is in a configuration file, it must be the first child element of the **\<configuration>** element.</span></span>

## <a name="example"></a><span data-ttu-id="a7c4c-124">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a7c4c-124">Example</span></span>

<span data-ttu-id="a7c4c-125">O exemplo a seguir mostra como definir uma seção de configuração e definir as configurações dessa seção:</span><span class="sxs-lookup"><span data-stu-id="a7c4c-125">The following example shows how to define a configuration section and define settings for that section:</span></span>

```xml
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

## <a name="configuration-file"></a><span data-ttu-id="a7c4c-126">arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="a7c4c-126">Configuration file</span></span>

<span data-ttu-id="a7c4c-127">Esse elemento pode ser usado no arquivo de configuração do aplicativo, arquivo de configuração de máquina (*Machine. config*), e *Web. config* arquivos que não estão no nível de diretório do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a7c4c-127">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="a7c4c-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a7c4c-128">See also</span></span>

- [<span data-ttu-id="a7c4c-129">Esquema de arquivo de configuração para o .NET Framework</span><span class="sxs-lookup"><span data-stu-id="a7c4c-129">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
