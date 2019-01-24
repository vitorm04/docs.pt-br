---
title: '&lt;Desmarque&gt; elemento para &lt;configSections&gt;'
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/clear
helpviewer_keywords:
- clear Element
- <clear> Element
ms.assetid: 77f1d761-ff45-4001-8f36-3a3e5c41fa63
author: guardrex
ms.author: mairaw
ms.openlocfilehash: 9439e2ac7634b242c9f847346f7dcf265d6ab419
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54677999"
---
# <a name="clear-element-for-configsections"></a><span data-ttu-id="55bef-102">\<Limpar > elemento para \<configSections ></span><span class="sxs-lookup"><span data-stu-id="55bef-102">\<clear> element for \<configSections></span></span>

<span data-ttu-id="55bef-103">Limpa todas as seções definidas anteriormente e grupos de seções.</span><span class="sxs-lookup"><span data-stu-id="55bef-103">Clears all previously defined sections and section groups.</span></span>

<span data-ttu-id="55bef-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="55bef-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="55bef-105">&nbsp;&nbsp;[**\<configSections>**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="55bef-105">&nbsp;&nbsp;[**\<configSections>**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) </span></span>  
<span data-ttu-id="55bef-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**</span><span class="sxs-lookup"><span data-stu-id="55bef-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**</span></span>

## <a name="syntax"></a><span data-ttu-id="55bef-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="55bef-107">Syntax</span></span>

```xml
<clear/>
```

## <a name="attribute"></a><span data-ttu-id="55bef-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="55bef-108">Attribute</span></span>

|           | <span data-ttu-id="55bef-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="55bef-109">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="55bef-110">**name**</span><span class="sxs-lookup"><span data-stu-id="55bef-110">**name**</span></span>  | <span data-ttu-id="55bef-111">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="55bef-111">Required attribute.</span></span><br><br><span data-ttu-id="55bef-112">Especifica o nome da seção ou grupo da seção a ser removido.</span><span class="sxs-lookup"><span data-stu-id="55bef-112">Specifies the name of the section or section group to remove.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="55bef-113">Elemento pai</span><span class="sxs-lookup"><span data-stu-id="55bef-113">Parent element</span></span>

|     | <span data-ttu-id="55bef-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="55bef-114">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="55bef-115">**\<configSections>** Element</span><span class="sxs-lookup"><span data-stu-id="55bef-115">**\<configSections>** Element</span></span>](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) | <span data-ttu-id="55bef-116">Contém as declarações de namespace e a seção de configuração.</span><span class="sxs-lookup"><span data-stu-id="55bef-116">Contains configuration section and namespace declarations.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="55bef-117">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="55bef-117">Child elements</span></span>

<span data-ttu-id="55bef-118">Nenhum</span><span class="sxs-lookup"><span data-stu-id="55bef-118">None</span></span>

## <a name="remarks"></a><span data-ttu-id="55bef-119">Comentários</span><span class="sxs-lookup"><span data-stu-id="55bef-119">Remarks</span></span>

<span data-ttu-id="55bef-120">O  **\<limpar >** elemento remove todas as seções e grupos de seções do seu aplicativo que foram definidos anteriormente no arquivo de configuração atual ou em um nível mais alto na hierarquia do arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="55bef-120">The **\<clear>** element removes all sections and section groups from your application that were defined earlier in the current configuration file or at a higher level in the configuration file hierarchy.</span></span>

## <a name="example"></a><span data-ttu-id="55bef-121">Exemplo</span><span class="sxs-lookup"><span data-stu-id="55bef-121">Example</span></span>

<span data-ttu-id="55bef-122">Este exemplo define um arquivo de configuração do computador e um arquivo de configuração de aplicativo e mostra como usar o  **\<limpar >** elemento em um arquivo de configuração de aplicativo para limpar as seções definidas anteriormente no arquivo de configuração do computador.</span><span class="sxs-lookup"><span data-stu-id="55bef-122">This example defines a machine configuration file and an application configuration file and shows how to use the **\<clear>** element in an application configuration file to clear sections previously defined in the machine configuration file.</span></span>

<span data-ttu-id="55bef-123">O seguinte código de arquivo de configuração de máquina declara duas seções,  **\<sampleSection >** e  **\<anotherSampleSection >**, que são lidos antes que o aplicativo arquivo de configuração:</span><span class="sxs-lookup"><span data-stu-id="55bef-123">The following machine configuration file code declares two sections, **\<sampleSection>** and **\<anotherSampleSection>**, which are read before the application configuration file:</span></span>

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

<span data-ttu-id="55bef-124">O seguinte código de arquivo de configuração de aplicativo limpa todas as seções declaradas anteriormente.</span><span class="sxs-lookup"><span data-stu-id="55bef-124">The following application configuration file code clears all previously declared sections.</span></span> <span data-ttu-id="55bef-125">O aplicativo não pode usar ou recuperar as configurações em qualquer uma das seções que foram declaradas no arquivo de configuração do computador.</span><span class="sxs-lookup"><span data-stu-id="55bef-125">The application cannot use or retrieve settings in either of the sections that were declared in the machine configuration file.</span></span> <span data-ttu-id="55bef-126">No entanto, ele pode usar as configurações do  **\<anotherSection >** porque ele vem após o  **\<limpar >** elemento.</span><span class="sxs-lookup"><span data-stu-id="55bef-126">However, it can use settings from **\<anotherSection>** because it comes after the **\<clear>** element.</span></span>

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

## <a name="configuration-file"></a><span data-ttu-id="55bef-127">arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="55bef-127">Configuration file</span></span>

<span data-ttu-id="55bef-128">Esse elemento pode ser usado no arquivo de configuração do aplicativo, arquivo de configuração de máquina (*Machine. config*), e *Web. config* arquivos que não estão no nível de diretório do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="55bef-128">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="55bef-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="55bef-129">See also</span></span>

- [<span data-ttu-id="55bef-130">Esquema de arquivo de configuração para o .NET Framework</span><span class="sxs-lookup"><span data-stu-id="55bef-130">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
