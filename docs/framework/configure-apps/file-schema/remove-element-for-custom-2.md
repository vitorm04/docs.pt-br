---
title: <remove>elemento para NameValueSectionHandler e DictionarySectionHandler
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName/remove
helpviewer_keywords:
- remove Element
- <remove> Element
ms.assetid: 8d8af7f5-26c9-4db9-bbe4-b2a4e6949568
ms.openlocfilehash: d1e4f3478f6afd6a20c01c6b57a137020ee88f5f
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "77214764"
---
# <a name="remove-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a><span data-ttu-id="4f10c-102">\<remove>elemento para NameValueSectionHandler e DictionarySectionHandler</span><span class="sxs-lookup"><span data-stu-id="4f10c-102">\<remove> element for NameValueSectionHandler and DictionarySectionHandler</span></span>

<span data-ttu-id="4f10c-103">Remove uma configuração definida anteriormente.</span><span class="sxs-lookup"><span data-stu-id="4f10c-103">Removes a previously defined setting.</span></span>

[**\<configuration>**](configuration-element.md)\
&nbsp;&nbsp;[**\<sectionName>**](custom-element-2.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**

## <a name="syntax"></a><span data-ttu-id="4f10c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4f10c-104">Syntax</span></span>

```xml
<add remove="key" />
```

## <a name="attribute"></a><span data-ttu-id="4f10c-105">Atributo</span><span class="sxs-lookup"><span data-stu-id="4f10c-105">Attribute</span></span>

|           | <span data-ttu-id="4f10c-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="4f10c-106">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="4f10c-107">**chave**</span><span class="sxs-lookup"><span data-stu-id="4f10c-107">**key**</span></span>   | <span data-ttu-id="4f10c-108">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="4f10c-108">Required attribute.</span></span><br><br><span data-ttu-id="4f10c-109">Especifica o nome da configuração a ser removida.</span><span class="sxs-lookup"><span data-stu-id="4f10c-109">Specifies the name of the setting to remove.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="4f10c-110">Elemento pai</span><span class="sxs-lookup"><span data-stu-id="4f10c-110">Parent element</span></span>

| <span data-ttu-id="4f10c-111">Elemento</span><span class="sxs-lookup"><span data-stu-id="4f10c-111">Element</span></span> | <span data-ttu-id="4f10c-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="4f10c-112">Description</span></span> |
| ------- | ------------|
| [<span data-ttu-id="4f10c-113">**\<sectionName>** Elementos</span><span class="sxs-lookup"><span data-stu-id="4f10c-113">**\<sectionName>** Element</span></span>](custom-element-2.md) | <span data-ttu-id="4f10c-114">Define as configurações para seções de configuração personalizadas que usam as <xref:System.Configuration.NameValueSectionHandler> <xref:System.Configuration.DictionarySectionHandler> classes e.</span><span class="sxs-lookup"><span data-stu-id="4f10c-114">Defines settings for custom configuration sections that use the <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler> classes.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="4f10c-115">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="4f10c-115">Child elements</span></span>

<span data-ttu-id="4f10c-116">Nenhum</span><span class="sxs-lookup"><span data-stu-id="4f10c-116">None</span></span>

## <a name="remarks"></a><span data-ttu-id="4f10c-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="4f10c-117">Remarks</span></span>

<span data-ttu-id="4f10c-118">Você pode usar o **\<remove>** elemento para remover as configurações de seu aplicativo que foram definidas em um nível mais alto na hierarquia do arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="4f10c-118">You can use the **\<remove>** element to remove settings from your application that were defined at a higher level in the configuration file hierarchy.</span></span>

## <a name="example"></a><span data-ttu-id="4f10c-119">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4f10c-119">Example</span></span>

<span data-ttu-id="4f10c-120">O exemplo a seguir mostra como usar o **\<remove>** elemento em um arquivo de configuração de aplicativo para remover as configurações definidas anteriormente no arquivo de configuração do computador.</span><span class="sxs-lookup"><span data-stu-id="4f10c-120">The following example shows how to use the **\<remove>** element in an application configuration file to remove settings previously defined in the machine configuration file.</span></span>

<span data-ttu-id="4f10c-121">O código do arquivo de configuração do computador a seguir declara a seção **\<mySection>** e adiciona duas configurações, `key1` e `key2` , a ela:</span><span class="sxs-lookup"><span data-stu-id="4f10c-121">The following machine configuration file code declares the section **\<mySection>** and adds two settings, `key1` and `key2`, to it:</span></span>

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

<span data-ttu-id="4f10c-122">O código do arquivo de configuração de aplicativo a seguir remove a `key2` configuração de **\<mySection>** :</span><span class="sxs-lookup"><span data-stu-id="4f10c-122">The following application configuration file code removes the `key2` setting from **\<mySection>**:</span></span>

```xml
<!--Application configuration file -->
<configuration>
  <mySection>
    <remove key="key2" />
  </mySection>
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="4f10c-123">Arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="4f10c-123">Configuration file</span></span>

<span data-ttu-id="4f10c-124">Esse elemento pode ser usado no arquivo de configuração do aplicativo, no arquivo de configuração do computador (*Machine. config*) e nos arquivos *Web. config* que não estão no nível do diretório do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="4f10c-124">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="4f10c-125">Confira também</span><span class="sxs-lookup"><span data-stu-id="4f10c-125">See also</span></span>

- [<span data-ttu-id="4f10c-126">Esquema do arquivo de configuração para o .NET Framework</span><span class="sxs-lookup"><span data-stu-id="4f10c-126">Configuration file schema for the .NET Framework</span></span>](index.md)
