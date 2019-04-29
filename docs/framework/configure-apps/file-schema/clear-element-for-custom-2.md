---
title: <clear> elemento para NameValueSectionHandler e DictionarySectionHandler
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName/clear
helpviewer_keywords:
- clear Element
- <clear> Element
ms.assetid: ff2294ec-fb82-4b0c-933e-ae185433fc7b
author: guardrex
ms.author: mairaw
ms.openlocfilehash: ad3ac93b2a7f92cd33787620fc0caa2b632aa072
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61705357"
---
# <a name="clear-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a><span data-ttu-id="9c004-102">\<Limpar > elemento para NameValueSectionHandler e DictionarySectionHandler</span><span class="sxs-lookup"><span data-stu-id="9c004-102">\<clear> element for NameValueSectionHandler and DictionarySectionHandler</span></span>

<span data-ttu-id="9c004-103">Limpa todas as configurações definidas anteriormente em uma seção.</span><span class="sxs-lookup"><span data-stu-id="9c004-103">Clears all previously defined settings in a section.</span></span>

<span data-ttu-id="9c004-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="9c004-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="9c004-105">&nbsp;&nbsp;[**\<sectionName>**](~/docs/framework/configure-apps/file-schema/custom-element-2.md) </span><span class="sxs-lookup"><span data-stu-id="9c004-105">&nbsp;&nbsp;[**\<sectionName>**](~/docs/framework/configure-apps/file-schema/custom-element-2.md) </span></span>  
<span data-ttu-id="9c004-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**</span><span class="sxs-lookup"><span data-stu-id="9c004-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**</span></span>

## <a name="syntax"></a><span data-ttu-id="9c004-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9c004-107">Syntax</span></span>

```xml
<clear />
```

## <a name="attributes"></a><span data-ttu-id="9c004-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="9c004-108">Attributes</span></span>

<span data-ttu-id="9c004-109">Nenhum</span><span class="sxs-lookup"><span data-stu-id="9c004-109">None</span></span>

## <a name="parent-element"></a><span data-ttu-id="9c004-110">Elemento pai</span><span class="sxs-lookup"><span data-stu-id="9c004-110">Parent element</span></span>

|     | <span data-ttu-id="9c004-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="9c004-111">Description</span></span> |
| --- | ------------|
| [<span data-ttu-id="9c004-112">**\<sectionName >** elemento</span><span class="sxs-lookup"><span data-stu-id="9c004-112">**\<sectionName>** Element</span></span>](~/docs/framework/configure-apps/file-schema/custom-element-2.md) | <span data-ttu-id="9c004-113">Define as configurações para seções de configuração personalizadas que usam o <xref:System.Configuration.NameValueSectionHandler> e <xref:System.Configuration.DictionarySectionHandler> classes.</span><span class="sxs-lookup"><span data-stu-id="9c004-113">Defines settings for custom configuration sections that use the <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler> classes.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="9c004-114">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="9c004-114">Child elements</span></span>

<span data-ttu-id="9c004-115">Nenhum</span><span class="sxs-lookup"><span data-stu-id="9c004-115">None</span></span>

## <a name="remarks"></a><span data-ttu-id="9c004-116">Comentários</span><span class="sxs-lookup"><span data-stu-id="9c004-116">Remarks</span></span>

<span data-ttu-id="9c004-117">Você pode usar o  **\<limpar >** elemento para remover todas as configurações do aplicativo que foram definidos em um nível mais alto na hierarquia do arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="9c004-117">You can use the **\<clear>** element to remove all settings from your application that were defined at a higher level in the configuration file hierarchy.</span></span>

## <a name="example"></a><span data-ttu-id="9c004-118">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9c004-118">Example</span></span>

<span data-ttu-id="9c004-119">Este exemplo define um arquivo de configuração do computador e um arquivo de configuração de aplicativo e mostra como usar o  **\<limpar >** elemento em um arquivo de configuração de aplicativo para limpar as seções definidas anteriormente no arquivo de configuração do computador.</span><span class="sxs-lookup"><span data-stu-id="9c004-119">This example defines a machine configuration file and an application configuration file and shows how to use the **\<clear>** element in an application configuration file to clear sections previously defined in the machine configuration file.</span></span>

<span data-ttu-id="9c004-120">O seguinte código de arquivo de configuração de máquina declara a seção  **\<mySection >**:</span><span class="sxs-lookup"><span data-stu-id="9c004-120">The following machine configuration file code declares the section **\<mySection>**:</span></span>

```xml
<!-- Machine.config file -->
<configuration>
  <configSections>
    <section name="mySection" type="System.Configuration.NameValueSectionHandler,System" />
  </configSections>
  <mySection>
    <add key="key1" value="value1" />
    <add key="key2" value="value2" />
  </mySection>
</configuration>
```

<span data-ttu-id="9c004-121">O seguinte código de arquivo de configuração de aplicativo remove todas as configurações de  **\<mySection >**.</span><span class="sxs-lookup"><span data-stu-id="9c004-121">The following application configuration file code removes all settings from **\<mySection>**.</span></span> <span data-ttu-id="9c004-122">O aplicativo não é possível recuperar as configurações que foram declarados nas na  **\<mySection >** seção do arquivo de configuração de máquina.</span><span class="sxs-lookup"><span data-stu-id="9c004-122">The application cannot retrieve any of the settings that were declared in the in the **\<mySection>** section of the machine configuration file.</span></span>

```xml
<!-- Application configuration file -->
<configuration>
  <mySection>
    <clear/>
  </mySection>
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="9c004-123">arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="9c004-123">Configuration file</span></span>

<span data-ttu-id="9c004-124">Esse elemento pode ser usado no arquivo de configuração do aplicativo, arquivo de configuração de máquina (*Machine. config*), e *Web. config* arquivos que não estão no nível de diretório do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="9c004-124">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="9c004-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9c004-125">See also</span></span>

- [<span data-ttu-id="9c004-126">Esquema de arquivo de configuração para o .NET Framework</span><span class="sxs-lookup"><span data-stu-id="9c004-126">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
