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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155343"
---
# <a name="configsections-element-for-configuration"></a><span data-ttu-id="55f94-102">\<configureSes> \<elemento para configuração></span><span class="sxs-lookup"><span data-stu-id="55f94-102">\<configSections> element for \<configuration></span></span>

<span data-ttu-id="55f94-103">Contém seção de configuração e declarações de namespace.</span><span class="sxs-lookup"><span data-stu-id="55f94-103">Contains configuration section and namespace declarations.</span></span>

<span data-ttu-id="55f94-104">configuração &nbsp; &nbsp; [\*\* \<>\*\*](configuration-element.md) \*\* \<configuraçãoSeções>\*\*</span><span class="sxs-lookup"><span data-stu-id="55f94-104">[**\<configuration>**](configuration-element.md) &nbsp;&nbsp;**\<configSections>**</span></span>

## <a name="attributes"></a><span data-ttu-id="55f94-105">Atributos</span><span class="sxs-lookup"><span data-stu-id="55f94-105">Attributes</span></span>

<span data-ttu-id="55f94-106">Nenhum</span><span class="sxs-lookup"><span data-stu-id="55f94-106">None</span></span>

## <a name="parent-element"></a><span data-ttu-id="55f94-107">Elemento pai</span><span class="sxs-lookup"><span data-stu-id="55f94-107">Parent element</span></span>

|     | <span data-ttu-id="55f94-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="55f94-108">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="55f94-109">**\<>de configuração**</span><span class="sxs-lookup"><span data-stu-id="55f94-109">**\<configuration>**</span></span>](configuration-element.md) | <span data-ttu-id="55f94-110">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="55f94-110">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="55f94-111">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="55f94-111">Child elements</span></span>

|     | <span data-ttu-id="55f94-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="55f94-112">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="55f94-113">**\<>de seção**</span><span class="sxs-lookup"><span data-stu-id="55f94-113">**\<section>**</span></span>](section-element.md) | <span data-ttu-id="55f94-114">Contém uma declaração de seção de configuração.</span><span class="sxs-lookup"><span data-stu-id="55f94-114">Contains a configuration section declaration.</span></span> |
| [<span data-ttu-id="55f94-115">**\<>de sectionGroup**</span><span class="sxs-lookup"><span data-stu-id="55f94-115">**\<sectionGroup>**</span></span>](sectiongroup-element-for-configsections.md) | <span data-ttu-id="55f94-116">Define um namespace para seções de configuração.</span><span class="sxs-lookup"><span data-stu-id="55f94-116">Defines a namespace for configuration sections.</span></span> |
| [<span data-ttu-id="55f94-117">**\<remover>**</span><span class="sxs-lookup"><span data-stu-id="55f94-117">**\<remove>**</span></span>](remove-element-for-configsections.md) | <span data-ttu-id="55f94-118">Remove uma seção ou grupo de seção predefinido.</span><span class="sxs-lookup"><span data-stu-id="55f94-118">Removes a predefined section or section group.</span></span> |
| [<span data-ttu-id="55f94-119">**\<claro>**</span><span class="sxs-lookup"><span data-stu-id="55f94-119">**\<clear>**</span></span>](clear-element-for-configsections.md) | <span data-ttu-id="55f94-120">Limpa todas as seções e grupos de seção previamente definidos.</span><span class="sxs-lookup"><span data-stu-id="55f94-120">Clears all previously defined sections and section groups.</span></span> |

## <a name="remarks"></a><span data-ttu-id="55f94-121">Comentários</span><span class="sxs-lookup"><span data-stu-id="55f94-121">Remarks</span></span>

<span data-ttu-id="55f94-122">Se este elemento estiver em um arquivo de configuração, ele deve ser o primeiro elemento filho do \*\* \<elemento>configuração.\*\*</span><span class="sxs-lookup"><span data-stu-id="55f94-122">If this element is in a configuration file, it must be the first child element of the **\<configuration>** element.</span></span>

## <a name="example"></a><span data-ttu-id="55f94-123">Exemplo</span><span class="sxs-lookup"><span data-stu-id="55f94-123">Example</span></span>

<span data-ttu-id="55f94-124">O exemplo a seguir mostra como definir uma seção de configuração e definir configurações para essa seção:</span><span class="sxs-lookup"><span data-stu-id="55f94-124">The following example shows how to define a configuration section and define settings for that section:</span></span>

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

## <a name="configuration-file"></a><span data-ttu-id="55f94-125">Arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="55f94-125">Configuration file</span></span>

<span data-ttu-id="55f94-126">Esse elemento pode ser usado no arquivo de configuração do aplicativo, no arquivo de configuração da máquina *(Machine.config)* e nos arquivos *Web.config* que não estão no nível do diretório do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="55f94-126">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="55f94-127">Confira também</span><span class="sxs-lookup"><span data-stu-id="55f94-127">See also</span></span>

- [<span data-ttu-id="55f94-128">Esquema de arquivo de configuração para o Framework .NET</span><span class="sxs-lookup"><span data-stu-id="55f94-128">Configuration file schema for the .NET Framework</span></span>](index.md)
