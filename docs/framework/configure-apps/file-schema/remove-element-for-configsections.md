---
title: '&lt;remover&gt; elemento para &lt;configSections&gt;'
ms.date: 05/01/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: article
f1_keywords: http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/remove
helpviewer_keywords:
- remove Element
- <remove> Element
ms.assetid: ae4d82e0-e8fe-468c-81ab-46d63c4d66a8
author: guardrex
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bf2cb49fbeb01ad176a1d24d711cebc97ba14004
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="remove-element-for-configsections"></a><span data-ttu-id="4c057-102">\<Remover > elemento \<configSections ></span><span class="sxs-lookup"><span data-stu-id="4c057-102">\<remove> element for \<configSections></span></span>

<span data-ttu-id="4c057-103">Remove uma seção predefinida ou grupo de seção.</span><span class="sxs-lookup"><span data-stu-id="4c057-103">Removes a predefined section or section group.</span></span>

<span data-ttu-id="4c057-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="4c057-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="4c057-105">&nbsp;&nbsp;[**\<configSections >**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="4c057-105">&nbsp;&nbsp;[**\<configSections>**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) </span></span>  
<span data-ttu-id="4c057-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<Remover >**</span><span class="sxs-lookup"><span data-stu-id="4c057-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**</span></span>

## <a name="syntax"></a><span data-ttu-id="4c057-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4c057-107">Syntax</span></span>

```xml
<remove name="section name or section group name" />
```

## <a name="attribute"></a><span data-ttu-id="4c057-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="4c057-108">Attribute</span></span>

|           | <span data-ttu-id="4c057-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="4c057-109">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="4c057-110">**name**</span><span class="sxs-lookup"><span data-stu-id="4c057-110">**name**</span></span>  | <span data-ttu-id="4c057-111">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="4c057-111">Required attribute.</span></span><br><br><span data-ttu-id="4c057-112">Especifica o nome da seção ou grupo da seção para remover.</span><span class="sxs-lookup"><span data-stu-id="4c057-112">Specifies the name of the section or section group to remove.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="4c057-113">Elemento pai</span><span class="sxs-lookup"><span data-stu-id="4c057-113">Parent element</span></span>

|     | <span data-ttu-id="4c057-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="4c057-114">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="4c057-115">**\<configSections >** elemento</span><span class="sxs-lookup"><span data-stu-id="4c057-115">**\<configSections>** Element</span></span>](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) | <span data-ttu-id="4c057-116">Contém declarações de namespace e de seção de configuração.</span><span class="sxs-lookup"><span data-stu-id="4c057-116">Contains configuration section and namespace declarations.</span></span> |

# <a name="child-elements"></a><span data-ttu-id="4c057-117">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="4c057-117">Child elements</span></span>

<span data-ttu-id="4c057-118">Nenhum</span><span class="sxs-lookup"><span data-stu-id="4c057-118">None</span></span>

## <a name="remarks"></a><span data-ttu-id="4c057-119">Comentários</span><span class="sxs-lookup"><span data-stu-id="4c057-119">Remarks</span></span>

<span data-ttu-id="4c057-120">Você pode usar o  **\<remover >** elemento remover seções e grupos de seções do seu aplicativo que foram definidas em um nível superior na hierarquia de arquivos de configuração.</span><span class="sxs-lookup"><span data-stu-id="4c057-120">You can use the **\<remove>** element to remove sections and section groups from your application that were defined at a higher level in the configuration file hierarchy.</span></span>

## <a name="example"></a><span data-ttu-id="4c057-121">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4c057-121">Example</span></span>

<span data-ttu-id="4c057-122">O exemplo a seguir mostra como usar o  **\<remover >** elemento em um arquivo de configuração do aplicativo para remover uma seção definida anteriormente no arquivo de configuração da máquina.</span><span class="sxs-lookup"><span data-stu-id="4c057-122">The following example shows how to use the **\<remove>** element in an application configuration file to remove a section previously defined in the machine configuration file.</span></span>

<span data-ttu-id="4c057-123">O seguinte código de arquivo de configuração de máquina declara a seção  **\<sampleSection >**:</span><span class="sxs-lookup"><span data-stu-id="4c057-123">The following machine configuration file code declares the section **\<sampleSection>**:</span></span>

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

<span data-ttu-id="4c057-124">O seguinte código de arquivo de configuração de aplicativo remove o  **\<sampleSection >** seção.</span><span class="sxs-lookup"><span data-stu-id="4c057-124">The following application configuration file code removes the **\<sampleSection>** section.</span></span> <span data-ttu-id="4c057-125">Após a remoção, o aplicativo não é possível recuperar as configurações no  **\<sampleSection >**.</span><span class="sxs-lookup"><span data-stu-id="4c057-125">After removal, the application cannot retrieve the settings in **\<sampleSection>**.</span></span>

```xml
<!-- Application configuration file -->
<configuration>
  <configSections>
    <remove name="sampleSection"/>
  </configSections>
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="4c057-126">arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="4c057-126">Configuration file</span></span>

<span data-ttu-id="4c057-127">Esse elemento pode ser usado no arquivo de configuração do aplicativo, o arquivo de configuração de máquina (*Machine. config*), e *Web. config* arquivos que não estão no nível de diretório do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="4c057-127">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="4c057-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4c057-128">See also</span></span>

[<span data-ttu-id="4c057-129">Esquema de arquivo de configuração para o .NET Framework</span><span class="sxs-lookup"><span data-stu-id="4c057-129">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
