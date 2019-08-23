---
title: Elemento <assemblyBinding> para <configuration>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/assemblyBinding
helpviewer_keywords:
- assemblyBinding Element
- <assemblyBinding> Element
ms.assetid: 6cc55983-b894-449b-8e26-b258e53939cd
ms.openlocfilehash: e0b83c4b3573ab6819654e72cac1bf3e4a0ba637
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69921268"
---
# <a name="assemblybinding-element-for-configuration"></a><span data-ttu-id="bb487-102">\<elemento de > assemblyBinding \<para > de configuração</span><span class="sxs-lookup"><span data-stu-id="bb487-102">\<assemblyBinding> element for \<configuration></span></span>

<span data-ttu-id="bb487-103">Especifica a diretiva de ligação de assembly no nível de configuração.</span><span class="sxs-lookup"><span data-stu-id="bb487-103">Specifies assembly binding policy at the configuration level.</span></span>

<span data-ttu-id="bb487-104">[ **\<configuration>** ](configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="bb487-104">[**\<configuration>**](configuration-element.md) </span></span>  
<span data-ttu-id="bb487-105">&nbsp;&nbsp; **\<assemblyBinding>**</span><span class="sxs-lookup"><span data-stu-id="bb487-105">&nbsp;&nbsp;**\<assemblyBinding>**</span></span>

## <a name="syntax"></a><span data-ttu-id="bb487-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bb487-106">Syntax</span></span>

```xml
<assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
  <!-- Configuration files to include. -->
</assemblyBinding>
```

## <a name="attribute"></a><span data-ttu-id="bb487-107">Atributo</span><span class="sxs-lookup"><span data-stu-id="bb487-107">Attribute</span></span>

|           | <span data-ttu-id="bb487-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="bb487-108">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="bb487-109">**xmlns**</span><span class="sxs-lookup"><span data-stu-id="bb487-109">**xmlns**</span></span> | <span data-ttu-id="bb487-110">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="bb487-110">Required attribute.</span></span><br><br><span data-ttu-id="bb487-111">Especifica o namespace XML necessário para a associação de assembly.</span><span class="sxs-lookup"><span data-stu-id="bb487-111">Specifies the XML namespace required for assembly binding.</span></span> <span data-ttu-id="bb487-112">Use a cadeia de caracteres "urn: schemas-microsoft-com: asm. v1" como o valor.</span><span class="sxs-lookup"><span data-stu-id="bb487-112">Use the string "urn:schemas-microsoft-com:asm.v1" as the value.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="bb487-113">Elemento pai</span><span class="sxs-lookup"><span data-stu-id="bb487-113">Parent element</span></span>

|     | <span data-ttu-id="bb487-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="bb487-114">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="bb487-115"> **\<configuration>** </span><span class="sxs-lookup"><span data-stu-id="bb487-115">**\<configuration>**</span></span>](configuration-element.md) | <span data-ttu-id="bb487-116">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="bb487-116">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-element"></a><span data-ttu-id="bb487-117">Elemento filho</span><span class="sxs-lookup"><span data-stu-id="bb487-117">Child element</span></span>

|     | <span data-ttu-id="bb487-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="bb487-118">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="bb487-119"> **\<linkedConfiguration>** </span><span class="sxs-lookup"><span data-stu-id="bb487-119">**\<linkedConfiguration>**</span></span>](linkedconfiguration-element.md) | <span data-ttu-id="bb487-120">Especifica um arquivo de configuração a ser incluído.</span><span class="sxs-lookup"><span data-stu-id="bb487-120">Specifies a configuration file to include.</span></span> |

## <a name="remarks"></a><span data-ttu-id="bb487-121">Comentários</span><span class="sxs-lookup"><span data-stu-id="bb487-121">Remarks</span></span>

<span data-ttu-id="bb487-122">O elemento > linkedConfiguration simplifica o gerenciamento de assemblies de componente, permitindo que os arquivos de configuração de aplicativo incluam arquivos de configuração de assembly em locais bem conhecidos, em vez de duplicar o assembly [ **\<** ](linkedconfiguration-element.md) definições de configuração.</span><span class="sxs-lookup"><span data-stu-id="bb487-122">The [**\<linkedConfiguration>**](linkedconfiguration-element.md) element simplifies the management of component assemblies by allowing application configuration files to include assembly configuration files in well-known locations, rather than duplicating assembly configuration settings.</span></span>

> [!NOTE]
> <span data-ttu-id="bb487-123">O elemento de  **\<> linkedConfiguration** não tem suporte para aplicativos com manifestos lado a lado do Windows.</span><span class="sxs-lookup"><span data-stu-id="bb487-123">The **\<linkedConfiguration>** element is not supported for applications with Windows side-by-side manifests.</span></span>

## <a name="example"></a><span data-ttu-id="bb487-124">Exemplo</span><span class="sxs-lookup"><span data-stu-id="bb487-124">Example</span></span>

<span data-ttu-id="bb487-125">O exemplo a seguir mostra como incluir um arquivo de configuração no disco rígido local:</span><span class="sxs-lookup"><span data-stu-id="bb487-125">The following example shows how to include a configuration file on the local hard disk:</span></span>

```xml
<configuration>
  <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
    <linkedConfiguration href="file://c:\Program Files\Contoso\sharedConfig.xml" />
  </assemblyBinding>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="bb487-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bb487-126">See also</span></span>

- [<span data-ttu-id="bb487-127">Esquema do arquivo de configuração para o .NET Framework</span><span class="sxs-lookup"><span data-stu-id="bb487-127">Configuration file schema for the .NET Framework</span></span>](index.md)
