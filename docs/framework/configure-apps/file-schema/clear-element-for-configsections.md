---
title: Elemento <clear> para <configSections>
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/clear
helpviewer_keywords:
- clear Element
- <clear> Element
ms.assetid: 77f1d761-ff45-4001-8f36-3a3e5c41fa63
author: rpetrusha
ms.author: mairaw
ms.openlocfilehash: c06fca8b83638fb47bedb21863cb9b200cd211f3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69927739"
---
# <a name="clear-element-for-configsections"></a><span data-ttu-id="48170-102">\<limpar > elemento para \<configSections ></span><span class="sxs-lookup"><span data-stu-id="48170-102">\<clear> element for \<configSections></span></span>

<span data-ttu-id="48170-103">Limpa todas as seções e grupos de seções definidos anteriormente.</span><span class="sxs-lookup"><span data-stu-id="48170-103">Clears all previously defined sections and section groups.</span></span>

<span data-ttu-id="48170-104">[ **\<configuration>** ](configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="48170-104">[**\<configuration>**](configuration-element.md) </span></span>  
<span data-ttu-id="48170-105">&nbsp;&nbsp;[ **\<configSections>** ](configsections-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="48170-105">&nbsp;&nbsp;[**\<configSections>**](configsections-element-for-configuration.md) </span></span>  
<span data-ttu-id="48170-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<clear>**</span><span class="sxs-lookup"><span data-stu-id="48170-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**</span></span>

## <a name="syntax"></a><span data-ttu-id="48170-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="48170-107">Syntax</span></span>

```xml
<clear/>
```

## <a name="attribute"></a><span data-ttu-id="48170-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="48170-108">Attribute</span></span>

|           | <span data-ttu-id="48170-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="48170-109">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="48170-110">**name**</span><span class="sxs-lookup"><span data-stu-id="48170-110">**name**</span></span>  | <span data-ttu-id="48170-111">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="48170-111">Required attribute.</span></span><br><br><span data-ttu-id="48170-112">Especifica o nome da seção ou do grupo de seções a ser removido.</span><span class="sxs-lookup"><span data-stu-id="48170-112">Specifies the name of the section or section group to remove.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="48170-113">Elemento pai</span><span class="sxs-lookup"><span data-stu-id="48170-113">Parent element</span></span>

|     | <span data-ttu-id="48170-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="48170-114">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="48170-115">configSections > elemento  **\<** </span><span class="sxs-lookup"><span data-stu-id="48170-115">**\<configSections>** Element</span></span>](configsections-element-for-configuration.md) | <span data-ttu-id="48170-116">Contém as declarações de namespace e seção de configuração.</span><span class="sxs-lookup"><span data-stu-id="48170-116">Contains configuration section and namespace declarations.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="48170-117">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="48170-117">Child elements</span></span>

<span data-ttu-id="48170-118">Nenhum</span><span class="sxs-lookup"><span data-stu-id="48170-118">None</span></span>

## <a name="remarks"></a><span data-ttu-id="48170-119">Comentários</span><span class="sxs-lookup"><span data-stu-id="48170-119">Remarks</span></span>

<span data-ttu-id="48170-120">O elemento Clear > remove todas as seções e grupos de seção do aplicativo que foram definidos anteriormente no arquivo de configuração atual ou em um nível superior na hierarquia do arquivo de configuração.  **\<**</span><span class="sxs-lookup"><span data-stu-id="48170-120">The **\<clear>** element removes all sections and section groups from your application that were defined earlier in the current configuration file or at a higher level in the configuration file hierarchy.</span></span>

## <a name="example"></a><span data-ttu-id="48170-121">Exemplo</span><span class="sxs-lookup"><span data-stu-id="48170-121">Example</span></span>

<span data-ttu-id="48170-122">Este exemplo define um arquivo de configuração de computador e um arquivo de configuração de aplicativo e mostra como usar o  **\<elemento Clear >** em um arquivo de configuração de aplicativo para limpar as seções definidas anteriormente na configuração do computador Grupo.</span><span class="sxs-lookup"><span data-stu-id="48170-122">This example defines a machine configuration file and an application configuration file and shows how to use the **\<clear>** element in an application configuration file to clear sections previously defined in the machine configuration file.</span></span>

<span data-ttu-id="48170-123">O código do arquivo de configuração do computador a seguir declara duas seções,  **\<sampleSection >** e  **\<anotherSampleSection >** , que são lidas antes do arquivo de configuração do aplicativo:</span><span class="sxs-lookup"><span data-stu-id="48170-123">The following machine configuration file code declares two sections, **\<sampleSection>** and **\<anotherSampleSection>**, which are read before the application configuration file:</span></span>

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

<span data-ttu-id="48170-124">O código do arquivo de configuração de aplicativo a seguir limpa todas as seções declaradas anteriormente.</span><span class="sxs-lookup"><span data-stu-id="48170-124">The following application configuration file code clears all previously declared sections.</span></span> <span data-ttu-id="48170-125">O aplicativo não pode usar ou recuperar as configurações em nenhuma das seções que foram declaradas no arquivo de configuração da máquina.</span><span class="sxs-lookup"><span data-stu-id="48170-125">The application cannot use or retrieve settings in either of the sections that were declared in the machine configuration file.</span></span> <span data-ttu-id="48170-126">No entanto, ele pode usar as configurações de  **\<anotherSection >** porque ele vem após o  **\<elemento Clear >** .</span><span class="sxs-lookup"><span data-stu-id="48170-126">However, it can use settings from **\<anotherSection>** because it comes after the **\<clear>** element.</span></span>

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

## <a name="configuration-file"></a><span data-ttu-id="48170-127">arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="48170-127">Configuration file</span></span>

<span data-ttu-id="48170-128">Esse elemento pode ser usado no arquivo de configuração do aplicativo, no arquivo de configuração do computador (*Machine. config*) e nos arquivos *Web. config* que não estão no nível do diretório do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="48170-128">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="48170-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="48170-129">See also</span></span>

- [<span data-ttu-id="48170-130">Esquema do arquivo de configuração para o .NET Framework</span><span class="sxs-lookup"><span data-stu-id="48170-130">Configuration file schema for the .NET Framework</span></span>](index.md)
