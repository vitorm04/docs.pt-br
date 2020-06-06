---
title: Elemento <assemblyBinding> para <configuration>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/assemblyBinding
helpviewer_keywords:
- assemblyBinding Element
- <assemblyBinding> Element
ms.assetid: 6cc55983-b894-449b-8e26-b258e53939cd
ms.openlocfilehash: 21cf5e749b0dae310c3326f8abf82c6678fc97e9
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79155473"
---
# <a name="assemblybinding-element-for-configuration"></a><span data-ttu-id="ad68c-102">Elemento \<assemblyBinding> para \<configuration></span><span class="sxs-lookup"><span data-stu-id="ad68c-102">\<assemblyBinding> element for \<configuration></span></span>

<span data-ttu-id="ad68c-103">Especifica a diretiva de ligação de assembly no nível de configuração.</span><span class="sxs-lookup"><span data-stu-id="ad68c-103">Specifies assembly binding policy at the configuration level.</span></span>

<span data-ttu-id="ad68c-104">[**\<configuration>**](configuration-element.md) &nbsp;&nbsp;**\<assemblyBinding>**</span><span class="sxs-lookup"><span data-stu-id="ad68c-104">[**\<configuration>**](configuration-element.md) &nbsp;&nbsp;**\<assemblyBinding>**</span></span>

## <a name="syntax"></a><span data-ttu-id="ad68c-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ad68c-105">Syntax</span></span>

```xml
<assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
  <!-- Configuration files to include. -->
</assemblyBinding>
```

## <a name="attribute"></a><span data-ttu-id="ad68c-106">Atributo</span><span class="sxs-lookup"><span data-stu-id="ad68c-106">Attribute</span></span>

|           | <span data-ttu-id="ad68c-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="ad68c-107">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="ad68c-108">**xmlns**</span><span class="sxs-lookup"><span data-stu-id="ad68c-108">**xmlns**</span></span> | <span data-ttu-id="ad68c-109">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="ad68c-109">Required attribute.</span></span><br><br><span data-ttu-id="ad68c-110">Especifica o namespace XML necessário para a associação de assembly.</span><span class="sxs-lookup"><span data-stu-id="ad68c-110">Specifies the XML namespace required for assembly binding.</span></span> <span data-ttu-id="ad68c-111">Use a cadeia de caracteres "urn: schemas-microsoft-com: asm. v1" como o valor.</span><span class="sxs-lookup"><span data-stu-id="ad68c-111">Use the string "urn:schemas-microsoft-com:asm.v1" as the value.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="ad68c-112">Elemento pai</span><span class="sxs-lookup"><span data-stu-id="ad68c-112">Parent element</span></span>

|     | <span data-ttu-id="ad68c-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="ad68c-113">Description</span></span> |
| --- | ----------- |
| [**\<configuration>**](configuration-element.md) | <span data-ttu-id="ad68c-114">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ad68c-114">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-element"></a><span data-ttu-id="ad68c-115">Elemento filho</span><span class="sxs-lookup"><span data-stu-id="ad68c-115">Child element</span></span>

|     | <span data-ttu-id="ad68c-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="ad68c-116">Description</span></span> |
| --- | ----------- |
| [**\<linkedConfiguration>**](linkedconfiguration-element.md) | <span data-ttu-id="ad68c-117">Especifica um arquivo de configuração a ser incluído.</span><span class="sxs-lookup"><span data-stu-id="ad68c-117">Specifies a configuration file to include.</span></span> |

## <a name="remarks"></a><span data-ttu-id="ad68c-118">Comentários</span><span class="sxs-lookup"><span data-stu-id="ad68c-118">Remarks</span></span>

<span data-ttu-id="ad68c-119">O [**\<linkedConfiguration>**](linkedconfiguration-element.md) elemento simplifica o gerenciamento de assemblies de componente, permitindo que os arquivos de configuração de aplicativo incluam arquivos de configuração de assembly em locais bem conhecidos, em vez de duplicar as definições de configuração de assembly.</span><span class="sxs-lookup"><span data-stu-id="ad68c-119">The [**\<linkedConfiguration>**](linkedconfiguration-element.md) element simplifies the management of component assemblies by allowing application configuration files to include assembly configuration files in well-known locations, rather than duplicating assembly configuration settings.</span></span>

> [!NOTE]
> <span data-ttu-id="ad68c-120">O **\<linkedConfiguration>** elemento não tem suporte para aplicativos com manifestos lado a lado do Windows.</span><span class="sxs-lookup"><span data-stu-id="ad68c-120">The **\<linkedConfiguration>** element is not supported for applications with Windows side-by-side manifests.</span></span>

## <a name="example"></a><span data-ttu-id="ad68c-121">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ad68c-121">Example</span></span>

<span data-ttu-id="ad68c-122">O exemplo a seguir mostra como incluir um arquivo de configuração no disco rígido local:</span><span class="sxs-lookup"><span data-stu-id="ad68c-122">The following example shows how to include a configuration file on the local hard disk:</span></span>

```xml
<configuration>
  <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
    <linkedConfiguration href="file://c:\Program Files\Contoso\sharedConfig.xml" />
  </assemblyBinding>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="ad68c-123">Confira também</span><span class="sxs-lookup"><span data-stu-id="ad68c-123">See also</span></span>

- [<span data-ttu-id="ad68c-124">Esquema do arquivo de configuração para o .NET Framework</span><span class="sxs-lookup"><span data-stu-id="ad68c-124">Configuration file schema for the .NET Framework</span></span>](index.md)
