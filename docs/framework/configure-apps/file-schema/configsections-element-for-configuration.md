---
title: Elemento <configSections> para <configuration>
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections
helpviewer_keywords:
- configSections Element
- <configSections> Element
ms.assetid: 9f963c1b-dc3f-4220-a8b6-2dd7a5a8e039
ms.openlocfilehash: 55116f1fe6fdffffea8f26d8a4de783c7305ada3
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79155343"
---
# <a name="configsections-element-for-configuration"></a><span data-ttu-id="7b087-102">Elemento \<configSections> para \<configuration></span><span class="sxs-lookup"><span data-stu-id="7b087-102">\<configSections> element for \<configuration></span></span>

<span data-ttu-id="7b087-103">Contém as declarações de namespace e seção de configuração.</span><span class="sxs-lookup"><span data-stu-id="7b087-103">Contains configuration section and namespace declarations.</span></span>

<span data-ttu-id="7b087-104">[**\<configuration>**](configuration-element.md) &nbsp;&nbsp;**\<configSections>**</span><span class="sxs-lookup"><span data-stu-id="7b087-104">[**\<configuration>**](configuration-element.md) &nbsp;&nbsp;**\<configSections>**</span></span>

## <a name="attributes"></a><span data-ttu-id="7b087-105">Atributos</span><span class="sxs-lookup"><span data-stu-id="7b087-105">Attributes</span></span>

<span data-ttu-id="7b087-106">Nenhum</span><span class="sxs-lookup"><span data-stu-id="7b087-106">None</span></span>

## <a name="parent-element"></a><span data-ttu-id="7b087-107">Elemento pai</span><span class="sxs-lookup"><span data-stu-id="7b087-107">Parent element</span></span>

|     | <span data-ttu-id="7b087-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="7b087-108">Description</span></span> |
| --- | ----------- |
| [**\<configuration>**](configuration-element.md) | <span data-ttu-id="7b087-109">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="7b087-109">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="7b087-110">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="7b087-110">Child elements</span></span>

|     | <span data-ttu-id="7b087-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="7b087-111">Description</span></span> |
| --- | ----------- |
| [**\<section>**](section-element.md) | <span data-ttu-id="7b087-112">Contém uma declaração de seção de configuração.</span><span class="sxs-lookup"><span data-stu-id="7b087-112">Contains a configuration section declaration.</span></span> |
| [**\<sectionGroup>**](sectiongroup-element-for-configsections.md) | <span data-ttu-id="7b087-113">Define um namespace para seções de configuração.</span><span class="sxs-lookup"><span data-stu-id="7b087-113">Defines a namespace for configuration sections.</span></span> |
| [**\<remove>**](remove-element-for-configsections.md) | <span data-ttu-id="7b087-114">Remove uma seção ou um grupo de seções predefinido.</span><span class="sxs-lookup"><span data-stu-id="7b087-114">Removes a predefined section or section group.</span></span> |
| [**\<clear>**](clear-element-for-configsections.md) | <span data-ttu-id="7b087-115">Limpa todas as seções e grupos de seções definidos anteriormente.</span><span class="sxs-lookup"><span data-stu-id="7b087-115">Clears all previously defined sections and section groups.</span></span> |

## <a name="remarks"></a><span data-ttu-id="7b087-116">Comentários</span><span class="sxs-lookup"><span data-stu-id="7b087-116">Remarks</span></span>

<span data-ttu-id="7b087-117">Se esse elemento estiver em um arquivo de configuração, ele deverá ser o primeiro elemento filho do **\<configuration>** elemento.</span><span class="sxs-lookup"><span data-stu-id="7b087-117">If this element is in a configuration file, it must be the first child element of the **\<configuration>** element.</span></span>

## <a name="example"></a><span data-ttu-id="7b087-118">Exemplo</span><span class="sxs-lookup"><span data-stu-id="7b087-118">Example</span></span>

<span data-ttu-id="7b087-119">O exemplo a seguir mostra como definir uma seção de configuração e definir as configurações para essa seção:</span><span class="sxs-lookup"><span data-stu-id="7b087-119">The following example shows how to define a configuration section and define settings for that section:</span></span>

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

## <a name="configuration-file"></a><span data-ttu-id="7b087-120">Arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="7b087-120">Configuration file</span></span>

<span data-ttu-id="7b087-121">Esse elemento pode ser usado no arquivo de configuração do aplicativo, no arquivo de configuração do computador (*Machine. config*) e nos arquivos *Web. config* que não estão no nível do diretório do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="7b087-121">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="7b087-122">Confira também</span><span class="sxs-lookup"><span data-stu-id="7b087-122">See also</span></span>

- [<span data-ttu-id="7b087-123">Esquema do arquivo de configuração para o .NET Framework</span><span class="sxs-lookup"><span data-stu-id="7b087-123">Configuration file schema for the .NET Framework</span></span>](index.md)
