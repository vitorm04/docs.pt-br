---
title: Elemento <remove> para <configSections>
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/remove
helpviewer_keywords:
- remove Element
- <remove> Element
ms.assetid: ae4d82e0-e8fe-468c-81ab-46d63c4d66a8
author: rpetrusha
ms.author: mairaw
ms.openlocfilehash: 7c0173879c692588cc2e15f0b14a5687bb0404fb
ms.sourcegitcommit: 621a5f6df00152006160987395b93b5b55f7ffcd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66300667"
---
# <a name="remove-element-for-configsections"></a><span data-ttu-id="b9f85-102">\<Remover > elemento para \<configSections ></span><span class="sxs-lookup"><span data-stu-id="b9f85-102">\<remove> element for \<configSections></span></span>

<span data-ttu-id="b9f85-103">Remove uma seção predefinidos ou grupo da seção.</span><span class="sxs-lookup"><span data-stu-id="b9f85-103">Removes a predefined section or section group.</span></span>

<span data-ttu-id="b9f85-104">[ **\<configuration>** ](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="b9f85-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="b9f85-105">&nbsp;&nbsp;[ **\<configSections>** ](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="b9f85-105">&nbsp;&nbsp;[**\<configSections>**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) </span></span>  
<span data-ttu-id="b9f85-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<remove>**</span><span class="sxs-lookup"><span data-stu-id="b9f85-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**</span></span>

## <a name="syntax"></a><span data-ttu-id="b9f85-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b9f85-107">Syntax</span></span>

```xml
<remove name="section name or section group name" />
```

## <a name="attribute"></a><span data-ttu-id="b9f85-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="b9f85-108">Attribute</span></span>

|           | <span data-ttu-id="b9f85-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="b9f85-109">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="b9f85-110">**name**</span><span class="sxs-lookup"><span data-stu-id="b9f85-110">**name**</span></span>  | <span data-ttu-id="b9f85-111">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="b9f85-111">Required attribute.</span></span><br><br><span data-ttu-id="b9f85-112">Especifica o nome da seção ou grupo da seção a ser removido.</span><span class="sxs-lookup"><span data-stu-id="b9f85-112">Specifies the name of the section or section group to remove.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="b9f85-113">Elemento pai</span><span class="sxs-lookup"><span data-stu-id="b9f85-113">Parent element</span></span>

|     | <span data-ttu-id="b9f85-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="b9f85-114">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="b9f85-115"> *\*\<configSections>** Element</span><span class="sxs-lookup"><span data-stu-id="b9f85-115">**\<configSections>** Element</span></span>](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) | <span data-ttu-id="b9f85-116">Contém as declarações de namespace e a seção de configuração.</span><span class="sxs-lookup"><span data-stu-id="b9f85-116">Contains configuration section and namespace declarations.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="b9f85-117">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="b9f85-117">Child elements</span></span>

<span data-ttu-id="b9f85-118">Nenhum</span><span class="sxs-lookup"><span data-stu-id="b9f85-118">None</span></span>

## <a name="remarks"></a><span data-ttu-id="b9f85-119">Comentários</span><span class="sxs-lookup"><span data-stu-id="b9f85-119">Remarks</span></span>

<span data-ttu-id="b9f85-120">Você pode usar o  **\<remover >** elemento remover seções e grupos de seções do seu aplicativo que foram definidos em um nível mais alto na hierarquia do arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="b9f85-120">You can use the **\<remove>** element to remove sections and section groups from your application that were defined at a higher level in the configuration file hierarchy.</span></span>

## <a name="example"></a><span data-ttu-id="b9f85-121">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b9f85-121">Example</span></span>

<span data-ttu-id="b9f85-122">O exemplo a seguir mostra como usar o  **\<remover >** elemento em um arquivo de configuração de aplicativo para remover uma seção definida anteriormente no arquivo de configuração do computador.</span><span class="sxs-lookup"><span data-stu-id="b9f85-122">The following example shows how to use the **\<remove>** element in an application configuration file to remove a section previously defined in the machine configuration file.</span></span>

<span data-ttu-id="b9f85-123">O seguinte código de arquivo de configuração de máquina declara a seção  **\<sampleSection >** :</span><span class="sxs-lookup"><span data-stu-id="b9f85-123">The following machine configuration file code declares the section **\<sampleSection>**:</span></span>

```xml
<!-- Machine.config file -->
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

<span data-ttu-id="b9f85-124">O seguinte código de arquivo de configuração de aplicativo remove o  **\<sampleSection >** seção.</span><span class="sxs-lookup"><span data-stu-id="b9f85-124">The following application configuration file code removes the **\<sampleSection>** section.</span></span> <span data-ttu-id="b9f85-125">Após a remoção, o aplicativo não é possível recuperar as configurações no  **\<sampleSection >** .</span><span class="sxs-lookup"><span data-stu-id="b9f85-125">After removal, the application cannot retrieve the settings in **\<sampleSection>**.</span></span>

```xml
<!-- Application configuration file -->
<configuration>
  <configSections>
    <remove name="sampleSection"/>
  </configSections>
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="b9f85-126">arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="b9f85-126">Configuration file</span></span>

<span data-ttu-id="b9f85-127">Esse elemento pode ser usado no arquivo de configuração do aplicativo, arquivo de configuração de máquina (*Machine. config*), e *Web. config* arquivos que não estão no nível de diretório do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b9f85-127">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="b9f85-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b9f85-128">See also</span></span>

- [<span data-ttu-id="b9f85-129">Esquema de arquivo de configuração para o .NET Framework</span><span class="sxs-lookup"><span data-stu-id="b9f85-129">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
