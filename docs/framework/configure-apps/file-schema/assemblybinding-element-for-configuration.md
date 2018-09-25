---
title: '&lt;assemblyBinding&gt; elemento para &lt;configuração&gt;'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/assemblyBinding
helpviewer_keywords:
- assemblyBinding Element
- <assemblyBinding> Element
ms.assetid: 6cc55983-b894-449b-8e26-b258e53939cd
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 5693b92ac35a357ff1f8643d0eb9ec2105acecb4
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47073457"
---
# <a name="assemblybinding-element-for-configuration"></a><span data-ttu-id="9745f-102">\<assemblyBinding > elemento para \<configuration ></span><span class="sxs-lookup"><span data-stu-id="9745f-102">\<assemblyBinding> element for \<configuration></span></span>

<span data-ttu-id="9745f-103">Especifica a diretiva de ligação de assembly no nível de configuração.</span><span class="sxs-lookup"><span data-stu-id="9745f-103">Specifies assembly binding policy at the configuration level.</span></span>

<span data-ttu-id="9745f-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="9745f-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="9745f-105">&nbsp;&nbsp;**\<assemblyBinding >**</span><span class="sxs-lookup"><span data-stu-id="9745f-105">&nbsp;&nbsp;**\<assemblyBinding>**</span></span>

## <a name="syntax"></a><span data-ttu-id="9745f-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9745f-106">Syntax</span></span>

```xml
<assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
  <!-- Configuration files to include. -->
</assemblyBinding>
```

## <a name="attribute"></a><span data-ttu-id="9745f-107">Atributo</span><span class="sxs-lookup"><span data-stu-id="9745f-107">Attribute</span></span>

|           | <span data-ttu-id="9745f-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="9745f-108">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="9745f-109">**xmlns**</span><span class="sxs-lookup"><span data-stu-id="9745f-109">**xmlns**</span></span> | <span data-ttu-id="9745f-110">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="9745f-110">Required attribute.</span></span><br><br><span data-ttu-id="9745f-111">Especifica o namespace XML necessário para a associação de assembly.</span><span class="sxs-lookup"><span data-stu-id="9745f-111">Specifies the XML namespace required for assembly binding.</span></span> <span data-ttu-id="9745f-112">Use a cadeia de caracteres "urn: schemas-microsoft-v1" como o valor.</span><span class="sxs-lookup"><span data-stu-id="9745f-112">Use the string "urn:schemas-microsoft-com:asm.v1" as the value.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="9745f-113">Elemento pai</span><span class="sxs-lookup"><span data-stu-id="9745f-113">Parent element</span></span>

|     | <span data-ttu-id="9745f-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="9745f-114">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="9745f-115">**\<configuration>**</span><span class="sxs-lookup"><span data-stu-id="9745f-115">**\<configuration>**</span></span>](~/docs/framework/configure-apps/file-schema/configuration-element.md) | <span data-ttu-id="9745f-116">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9745f-116">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-element"></a><span data-ttu-id="9745f-117">Elemento filho</span><span class="sxs-lookup"><span data-stu-id="9745f-117">Child element</span></span>

|     | <span data-ttu-id="9745f-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="9745f-118">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="9745f-119">**\<linkedConfiguration >**</span><span class="sxs-lookup"><span data-stu-id="9745f-119">**\<linkedConfiguration>**</span></span>](~/docs/framework/configure-apps/file-schema/linkedconfiguration-element.md) | <span data-ttu-id="9745f-120">Especifica um arquivo de configuração a ser incluído.</span><span class="sxs-lookup"><span data-stu-id="9745f-120">Specifies a configuration file to include.</span></span> |

## <a name="remarks"></a><span data-ttu-id="9745f-121">Comentários</span><span class="sxs-lookup"><span data-stu-id="9745f-121">Remarks</span></span>

<span data-ttu-id="9745f-122">O [  **\<linkedConfiguration >** ](~/docs/framework/configure-apps/file-schema/linkedconfiguration-element.md) elemento simplifica o gerenciamento de assemblies de componente, permitindo que os arquivos de configuração de aplicativo para incluir o assembly de arquivos de configuração locais bem conhecidos, em vez de duplicar as definições de configuração de assembly.</span><span class="sxs-lookup"><span data-stu-id="9745f-122">The [**\<linkedConfiguration>**](~/docs/framework/configure-apps/file-schema/linkedconfiguration-element.md) element simplifies the management of component assemblies by allowing application configuration files to include assembly configuration files in well-known locations, rather than duplicating assembly configuration settings.</span></span>

> [!NOTE]
> <span data-ttu-id="9745f-123">O  **\<linkedConfiguration >** elemento não tem suporte para aplicativos com manifestos do Windows lado a lado.</span><span class="sxs-lookup"><span data-stu-id="9745f-123">The **\<linkedConfiguration>** element is not supported for applications with Windows side-by-side manifests.</span></span>

## <a name="example"></a><span data-ttu-id="9745f-124">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9745f-124">Example</span></span>

<span data-ttu-id="9745f-125">O exemplo a seguir mostra como incluir um arquivo de configuração no disco rígido local:</span><span class="sxs-lookup"><span data-stu-id="9745f-125">The following example shows how to include a configuration file on the local hard disk:</span></span>

```xml
<configuration>
  <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
    <linkedConfiguration href="file://c:\Program Files\Contoso\sharedConfig.xml" />
  </assemblyBinding>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="9745f-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9745f-126">See also</span></span>

[<span data-ttu-id="9745f-127">Esquema de arquivo de configuração para o .NET Framework</span><span class="sxs-lookup"><span data-stu-id="9745f-127">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
