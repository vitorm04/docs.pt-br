---
title: Elemento <configSections> para <configuration>
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections
helpviewer_keywords:
- configSections Element
- <configSections> Element
ms.assetid: 9f963c1b-dc3f-4220-a8b6-2dd7a5a8e039
ms.openlocfilehash: 1e4bb7a7cfb0b140ca6d13c162708c3c30bd496d
ms.sourcegitcommit: 2543a78be6e246aa010a01decf58889de53d1636
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/17/2020
ms.locfileid: "86441681"
---
# <a name="configsections-element-for-configuration"></a><span data-ttu-id="a1684-102">Elemento \<configSections> para \<configuration></span><span class="sxs-lookup"><span data-stu-id="a1684-102">\<configSections> element for \<configuration></span></span>

<span data-ttu-id="a1684-103">Contém as declarações de namespace e seção de configuração.</span><span class="sxs-lookup"><span data-stu-id="a1684-103">Contains configuration section and namespace declarations.</span></span>

<span data-ttu-id="a1684-104">[**\<configuration>**](configuration-element.md) &nbsp;&nbsp;**\<configSections>**</span><span class="sxs-lookup"><span data-stu-id="a1684-104">[**\<configuration>**](configuration-element.md) &nbsp;&nbsp;**\<configSections>**</span></span>

## <a name="attributes"></a><span data-ttu-id="a1684-105">Atributos</span><span class="sxs-lookup"><span data-stu-id="a1684-105">Attributes</span></span>

<span data-ttu-id="a1684-106">Nenhum</span><span class="sxs-lookup"><span data-stu-id="a1684-106">None</span></span>

## <a name="parent-element"></a><span data-ttu-id="a1684-107">Elemento pai</span><span class="sxs-lookup"><span data-stu-id="a1684-107">Parent element</span></span>

|     | <span data-ttu-id="a1684-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="a1684-108">Description</span></span> |
| --- | ----------- |
| [**\<configuration>**](configuration-element.md) | <span data-ttu-id="a1684-109">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a1684-109">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="a1684-110">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="a1684-110">Child elements</span></span>

|     | <span data-ttu-id="a1684-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="a1684-111">Description</span></span> |
| --- | ----------- |
| [**\<section>**](section-element.md) | <span data-ttu-id="a1684-112">Contém uma declaração de seção de configuração.</span><span class="sxs-lookup"><span data-stu-id="a1684-112">Contains a configuration section declaration.</span></span> |
| [**\<sectionGroup>**](sectiongroup-element-for-configsections.md) | <span data-ttu-id="a1684-113">Define um namespace para seções de configuração.</span><span class="sxs-lookup"><span data-stu-id="a1684-113">Defines a namespace for configuration sections.</span></span> |

## <a name="remarks"></a><span data-ttu-id="a1684-114">Comentários</span><span class="sxs-lookup"><span data-stu-id="a1684-114">Remarks</span></span>

<span data-ttu-id="a1684-115">Se esse elemento estiver em um arquivo de configuração, ele deverá ser o primeiro elemento filho do **\<configuration>** elemento.</span><span class="sxs-lookup"><span data-stu-id="a1684-115">If this element is in a configuration file, it must be the first child element of the **\<configuration>** element.</span></span>

## <a name="example"></a><span data-ttu-id="a1684-116">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a1684-116">Example</span></span>

<span data-ttu-id="a1684-117">O exemplo a seguir mostra como definir uma seção de configuração e definir as configurações para essa seção:</span><span class="sxs-lookup"><span data-stu-id="a1684-117">The following example shows how to define a configuration section and define settings for that section:</span></span>

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

## <a name="configuration-file"></a><span data-ttu-id="a1684-118">Arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="a1684-118">Configuration file</span></span>

<span data-ttu-id="a1684-119">Esse elemento pode ser usado no arquivo de configuração do aplicativo, no arquivo de configuração do computador (*Machine.config*) e *Web.config* arquivos que não estão no nível do diretório do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a1684-119">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="a1684-120">Confira também</span><span class="sxs-lookup"><span data-stu-id="a1684-120">See also</span></span>

- [<span data-ttu-id="a1684-121">Esquema do arquivo de configuração para o .NET Framework</span><span class="sxs-lookup"><span data-stu-id="a1684-121">Configuration file schema for the .NET Framework</span></span>](index.md)
