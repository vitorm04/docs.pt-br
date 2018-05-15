---
title: '&lt;Limpar&gt; elemento para NameValueSectionHandler e DictionarySectionHandler'
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName/clear
helpviewer_keywords:
- clear Element
- <clear> Element
ms.assetid: ff2294ec-fb82-4b0c-933e-ae185433fc7b
author: guardrex
ms.author: mairaw
ms.openlocfilehash: a1cbd682faa4c60e50bc3b73b58ef226dd599da2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="clear-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a><span data-ttu-id="6f41b-102">\<Limpar > elemento NameValueSectionHandler e DictionarySectionHandler</span><span class="sxs-lookup"><span data-stu-id="6f41b-102">\<clear> element for NameValueSectionHandler and DictionarySectionHandler</span></span>

<span data-ttu-id="6f41b-103">Limpa todas as configurações previamente definidas em uma seção.</span><span class="sxs-lookup"><span data-stu-id="6f41b-103">Clears all previously defined settings in a section.</span></span>

<span data-ttu-id="6f41b-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="6f41b-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="6f41b-105">&nbsp;&nbsp;[**\<sectionName >**](~/docs/framework/configure-apps/file-schema/custom-element-2.md) </span><span class="sxs-lookup"><span data-stu-id="6f41b-105">&nbsp;&nbsp;[**\<sectionName>**](~/docs/framework/configure-apps/file-schema/custom-element-2.md) </span></span>  
<span data-ttu-id="6f41b-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<Limpar >**</span><span class="sxs-lookup"><span data-stu-id="6f41b-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**</span></span>

## <a name="syntax"></a><span data-ttu-id="6f41b-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6f41b-107">Syntax</span></span>

```xml
<clear />
```

## <a name="attributes"></a><span data-ttu-id="6f41b-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="6f41b-108">Attributes</span></span>

<span data-ttu-id="6f41b-109">Nenhum</span><span class="sxs-lookup"><span data-stu-id="6f41b-109">None</span></span>

## <a name="parent-element"></a><span data-ttu-id="6f41b-110">Elemento pai</span><span class="sxs-lookup"><span data-stu-id="6f41b-110">Parent element</span></span>

|     | <span data-ttu-id="6f41b-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="6f41b-111">Description</span></span> |
| --- | ------------|
| [<span data-ttu-id="6f41b-112">**\<sectionName >** elemento</span><span class="sxs-lookup"><span data-stu-id="6f41b-112">**\<sectionName>** Element</span></span>](~/docs/framework/configure-apps/file-schema/custom-element-2.md) | <span data-ttu-id="6f41b-113">Define as configurações para as seções de configuração personalizadas que usam o <xref:System.Configuration.NameValueSectionHandler> e <xref:System.Configuration.DictionarySectionHandler> classes.</span><span class="sxs-lookup"><span data-stu-id="6f41b-113">Defines settings for custom configuration sections that use the <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler> classes.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="6f41b-114">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="6f41b-114">Child elements</span></span>

<span data-ttu-id="6f41b-115">Nenhum</span><span class="sxs-lookup"><span data-stu-id="6f41b-115">None</span></span>

## <a name="remarks"></a><span data-ttu-id="6f41b-116">Comentários</span><span class="sxs-lookup"><span data-stu-id="6f41b-116">Remarks</span></span>

<span data-ttu-id="6f41b-117">Você pode usar o  **\<limpar >** elemento para remover todas as configurações do aplicativo que foram definidas em um nível superior na hierarquia de arquivos de configuração.</span><span class="sxs-lookup"><span data-stu-id="6f41b-117">You can use the **\<clear>** element to remove all settings from your application that were defined at a higher level in the configuration file hierarchy.</span></span>

## <a name="example"></a><span data-ttu-id="6f41b-118">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6f41b-118">Example</span></span>

<span data-ttu-id="6f41b-119">Este exemplo define um arquivo de configuração do computador e um arquivo de configuração do aplicativo e mostra como usar o  **\<limpar >** elemento em um arquivo de configuração do aplicativo para limpar seções definidas anteriormente no arquivo de configuração de máquina.</span><span class="sxs-lookup"><span data-stu-id="6f41b-119">This example defines a machine configuration file and an application configuration file and shows how to use the **\<clear>** element in an application configuration file to clear sections previously defined in the machine configuration file.</span></span>

<span data-ttu-id="6f41b-120">O seguinte código de arquivo de configuração de máquina declara a seção  **\<mySection >**:</span><span class="sxs-lookup"><span data-stu-id="6f41b-120">The following machine configuration file code declares the section **\<mySection>**:</span></span>

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

<span data-ttu-id="6f41b-121">O seguinte código de arquivo de configuração de aplicativo remove todas as configurações de  **\<mySection >**.</span><span class="sxs-lookup"><span data-stu-id="6f41b-121">The following application configuration file code removes all settings from **\<mySection>**.</span></span> <span data-ttu-id="6f41b-122">O aplicativo não é possível recuperar as configurações que foram declarados no no  **\<mySection >** seção do arquivo de configuração de máquina.</span><span class="sxs-lookup"><span data-stu-id="6f41b-122">The application cannot retrieve any of the settings that were declared in the in the **\<mySection>** section of the machine configuration file.</span></span>

```xml
<!-- Application configuration file -->
<configuration>
  <mySection>
    <clear/>
  </mySection>
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="6f41b-123">arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="6f41b-123">Configuration file</span></span>

<span data-ttu-id="6f41b-124">Esse elemento pode ser usado no arquivo de configuração do aplicativo, o arquivo de configuração de máquina (*Machine. config*), e *Web. config* arquivos que não estão no nível de diretório do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="6f41b-124">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="6f41b-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6f41b-125">See also</span></span>

[<span data-ttu-id="6f41b-126">Esquema de arquivo de configuração para o .NET Framework</span><span class="sxs-lookup"><span data-stu-id="6f41b-126">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
