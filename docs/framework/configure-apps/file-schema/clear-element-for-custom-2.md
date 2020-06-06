---
title: <clear>elemento para NameValueSectionHandler e DictionarySectionHandler
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName/clear
helpviewer_keywords:
- clear Element
- <clear> Element
ms.assetid: ff2294ec-fb82-4b0c-933e-ae185433fc7b
ms.openlocfilehash: f6d860f35d22002030ffa3d09dd0d8a96116bf5e
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "77214751"
---
# <a name="clear-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a><span data-ttu-id="7848b-102">\<clear>elemento para NameValueSectionHandler e DictionarySectionHandler</span><span class="sxs-lookup"><span data-stu-id="7848b-102">\<clear> element for NameValueSectionHandler and DictionarySectionHandler</span></span>

<span data-ttu-id="7848b-103">Limpa todas as configurações definidas anteriormente em uma seção.</span><span class="sxs-lookup"><span data-stu-id="7848b-103">Clears all previously defined settings in a section.</span></span>

[**\<configuration>**](configuration-element.md)\
&nbsp;&nbsp;[**\<sectionName>**](custom-element-2.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**

## <a name="syntax"></a><span data-ttu-id="7848b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7848b-104">Syntax</span></span>

```xml
<clear />
```

## <a name="attributes"></a><span data-ttu-id="7848b-105">Atributos</span><span class="sxs-lookup"><span data-stu-id="7848b-105">Attributes</span></span>

<span data-ttu-id="7848b-106">Nenhum</span><span class="sxs-lookup"><span data-stu-id="7848b-106">None</span></span>

## <a name="parent-element"></a><span data-ttu-id="7848b-107">Elemento pai</span><span class="sxs-lookup"><span data-stu-id="7848b-107">Parent element</span></span>

|     | <span data-ttu-id="7848b-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="7848b-108">Description</span></span> |
| --- | ------------|
| [<span data-ttu-id="7848b-109">**\<sectionName>** Elementos</span><span class="sxs-lookup"><span data-stu-id="7848b-109">**\<sectionName>** Element</span></span>](custom-element-2.md) | <span data-ttu-id="7848b-110">Define as configurações para seções de configuração personalizadas que usam as <xref:System.Configuration.NameValueSectionHandler> <xref:System.Configuration.DictionarySectionHandler> classes e.</span><span class="sxs-lookup"><span data-stu-id="7848b-110">Defines settings for custom configuration sections that use the <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler> classes.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="7848b-111">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="7848b-111">Child elements</span></span>

<span data-ttu-id="7848b-112">Nenhum</span><span class="sxs-lookup"><span data-stu-id="7848b-112">None</span></span>

## <a name="remarks"></a><span data-ttu-id="7848b-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="7848b-113">Remarks</span></span>

<span data-ttu-id="7848b-114">Você pode usar o **\<clear>** elemento para remover todas as configurações do aplicativo que foram definidas em um nível mais alto na hierarquia do arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="7848b-114">You can use the **\<clear>** element to remove all settings from your application that were defined at a higher level in the configuration file hierarchy.</span></span>

## <a name="example"></a><span data-ttu-id="7848b-115">Exemplo</span><span class="sxs-lookup"><span data-stu-id="7848b-115">Example</span></span>

<span data-ttu-id="7848b-116">Este exemplo define um arquivo de configuração de computador e um arquivo de configuração de aplicativo e mostra como usar o **\<clear>** elemento em um arquivo de configuração de aplicativo para limpar as seções definidas anteriormente no arquivo de configuração de computador.</span><span class="sxs-lookup"><span data-stu-id="7848b-116">This example defines a machine configuration file and an application configuration file and shows how to use the **\<clear>** element in an application configuration file to clear sections previously defined in the machine configuration file.</span></span>

<span data-ttu-id="7848b-117">O código do arquivo de configuração do computador a seguir declara a seção **\<mySection>** :</span><span class="sxs-lookup"><span data-stu-id="7848b-117">The following machine configuration file code declares the section **\<mySection>**:</span></span>

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

<span data-ttu-id="7848b-118">O código do arquivo de configuração de aplicativo a seguir remove todas as configurações de **\<mySection>** .</span><span class="sxs-lookup"><span data-stu-id="7848b-118">The following application configuration file code removes all settings from **\<mySection>**.</span></span> <span data-ttu-id="7848b-119">O aplicativo não pode recuperar nenhuma das configurações que foram declaradas no na **\<mySection>** seção do arquivo de configuração do computador.</span><span class="sxs-lookup"><span data-stu-id="7848b-119">The application cannot retrieve any of the settings that were declared in the in the **\<mySection>** section of the machine configuration file.</span></span>

```xml
<!-- Application configuration file -->
<configuration>
  <mySection>
    <clear/>
  </mySection>
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="7848b-120">Arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="7848b-120">Configuration file</span></span>

<span data-ttu-id="7848b-121">Esse elemento pode ser usado no arquivo de configuração do aplicativo, no arquivo de configuração do computador (*Machine. config*) e nos arquivos *Web. config* que não estão no nível do diretório do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="7848b-121">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="7848b-122">Confira também</span><span class="sxs-lookup"><span data-stu-id="7848b-122">See also</span></span>

- [<span data-ttu-id="7848b-123">Esquema do arquivo de configuração para o .NET Framework</span><span class="sxs-lookup"><span data-stu-id="7848b-123">Configuration file schema for the .NET Framework</span></span>](index.md)
