---
title: Elemento <clear> para <configSections>
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/clear
helpviewer_keywords:
- clear Element
- <clear> Element
ms.assetid: 77f1d761-ff45-4001-8f36-3a3e5c41fa63
ms.openlocfilehash: 66abd7f057bc6d060e50a889a945281d07c97592
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155421"
---
# <a name="clear-element-for-configsections"></a><span data-ttu-id="131fd-102">\<elemento> \<clara para configuraçõesSeções></span><span class="sxs-lookup"><span data-stu-id="131fd-102">\<clear> element for \<configSections></span></span>

<span data-ttu-id="131fd-103">Limpa todas as seções e grupos de seção previamente definidos.</span><span class="sxs-lookup"><span data-stu-id="131fd-103">Clears all previously defined sections and section groups.</span></span>

<span data-ttu-id="131fd-104">&nbsp; &nbsp; &nbsp; &nbsp; \*\* \<\*\* [\*\* \<configuração>\*\*](configuration-element.md) &nbsp; &nbsp;configSeções>>claras [\*\* \<\*\*](configsections-element-for-configuration.md)</span><span class="sxs-lookup"><span data-stu-id="131fd-104">[**\<configuration>**](configuration-element.md) &nbsp;&nbsp;[**\<configSections>**](configsections-element-for-configuration.md) &nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**</span></span>

## <a name="syntax"></a><span data-ttu-id="131fd-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="131fd-105">Syntax</span></span>

```xml
<clear/>
```

## <a name="attribute"></a><span data-ttu-id="131fd-106">Atributo</span><span class="sxs-lookup"><span data-stu-id="131fd-106">Attribute</span></span>

|           | <span data-ttu-id="131fd-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="131fd-107">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="131fd-108">**name**</span><span class="sxs-lookup"><span data-stu-id="131fd-108">**name**</span></span>  | <span data-ttu-id="131fd-109">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="131fd-109">Required attribute.</span></span><br><br><span data-ttu-id="131fd-110">Especifica o nome da seção ou do grupo de seção a ser removido.</span><span class="sxs-lookup"><span data-stu-id="131fd-110">Specifies the name of the section or section group to remove.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="131fd-111">Elemento pai</span><span class="sxs-lookup"><span data-stu-id="131fd-111">Parent element</span></span>

|     | <span data-ttu-id="131fd-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="131fd-112">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="131fd-113">\*\* \<configSeções>\*\* Elemento</span><span class="sxs-lookup"><span data-stu-id="131fd-113">**\<configSections>** Element</span></span>](configsections-element-for-configuration.md) | <span data-ttu-id="131fd-114">Contém seção de configuração e declarações de namespace.</span><span class="sxs-lookup"><span data-stu-id="131fd-114">Contains configuration section and namespace declarations.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="131fd-115">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="131fd-115">Child elements</span></span>

<span data-ttu-id="131fd-116">Nenhum</span><span class="sxs-lookup"><span data-stu-id="131fd-116">None</span></span>

## <a name="remarks"></a><span data-ttu-id="131fd-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="131fd-117">Remarks</span></span>

<span data-ttu-id="131fd-118">O elemento \*\* \<clear>\*\* remove todas as seções e grupos de seção do seu aplicativo que foram definidos anteriormente no arquivo de configuração atual ou em um nível mais alto na hierarquia do arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="131fd-118">The **\<clear>** element removes all sections and section groups from your application that were defined earlier in the current configuration file or at a higher level in the configuration file hierarchy.</span></span>

## <a name="example"></a><span data-ttu-id="131fd-119">Exemplo</span><span class="sxs-lookup"><span data-stu-id="131fd-119">Example</span></span>

<span data-ttu-id="131fd-120">Este exemplo define um arquivo de configuração da máquina \*\* \<\*\* e um arquivo de configuração de aplicativo e mostra como usar o elemento clear>em um arquivo de configuração de aplicativo para limpar seções definidas anteriormente no arquivo de configuração da máquina.</span><span class="sxs-lookup"><span data-stu-id="131fd-120">This example defines a machine configuration file and an application configuration file and shows how to use the **\<clear>** element in an application configuration file to clear sections previously defined in the machine configuration file.</span></span>

<span data-ttu-id="131fd-121">O código de arquivo de configuração da máquina a seguir declara duas seções, \*\* \<sampleSection>\*\* e \*\* \<outra>SampleSection \*\*, que são lidas antes do arquivo de configuração do aplicativo:</span><span class="sxs-lookup"><span data-stu-id="131fd-121">The following machine configuration file code declares two sections, **\<sampleSection>** and **\<anotherSampleSection>**, which are read before the application configuration file:</span></span>

```xml
<!-- Machine.config file -->
<configuration>
  <configSections>
    <section name="sampleSection"
             type="System.Configuration.SingleTagSectionHandler" />
    <section name="anotherSampleSection"
             type="System.Configuration.NameValueSectionHandler" />
  </configSections>
  <sampleSection setting1="Value1"
                 setting2="value two"
                 setting3="third value" />
</configuration>
```

<span data-ttu-id="131fd-122">O código de arquivo de configuração do aplicativo a seguir limpa todas as seções declaradas anteriormente.</span><span class="sxs-lookup"><span data-stu-id="131fd-122">The following application configuration file code clears all previously declared sections.</span></span> <span data-ttu-id="131fd-123">O aplicativo não pode usar ou recuperar configurações em qualquer uma das seções que foram declaradas no arquivo de configuração da máquina.</span><span class="sxs-lookup"><span data-stu-id="131fd-123">The application cannot use or retrieve settings in either of the sections that were declared in the machine configuration file.</span></span> <span data-ttu-id="131fd-124">No entanto, ele pode usar configurações de \*\* \<outra Seção>\*\* porque vem depois do \*\* \<\*\* elemento>claro.</span><span class="sxs-lookup"><span data-stu-id="131fd-124">However, it can use settings from **\<anotherSection>** because it comes after the **\<clear>** element.</span></span>

```xml
<!-- Application configuration file -->
<configuration>
  <configSections>
    <clear/>
    <section name="anotherSection"
             type="System.Configuration.NameValueSectionHandler" />
  </configSections>
  <anotherSection setting1="Value1"
                 setting2="value two"
                 setting3="third value" />
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="131fd-125">Arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="131fd-125">Configuration file</span></span>

<span data-ttu-id="131fd-126">Esse elemento pode ser usado no arquivo de configuração do aplicativo, no arquivo de configuração da máquina *(Machine.config)* e nos arquivos *Web.config* que não estão no nível do diretório do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="131fd-126">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="131fd-127">Confira também</span><span class="sxs-lookup"><span data-stu-id="131fd-127">See also</span></span>

- [<span data-ttu-id="131fd-128">Esquema de arquivo de configuração para o Framework .NET</span><span class="sxs-lookup"><span data-stu-id="131fd-128">Configuration file schema for the .NET Framework</span></span>](index.md)
