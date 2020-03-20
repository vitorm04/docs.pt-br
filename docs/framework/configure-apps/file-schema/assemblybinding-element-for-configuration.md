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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155473"
---
# <a name="assemblybinding-element-for-configuration"></a><span data-ttu-id="a8259-102">\<montagemElemento de \<> de vinculação para> de configuração</span><span class="sxs-lookup"><span data-stu-id="a8259-102">\<assemblyBinding> element for \<configuration></span></span>

<span data-ttu-id="a8259-103">Especifica a diretiva de ligação de assembly no nível de configuração.</span><span class="sxs-lookup"><span data-stu-id="a8259-103">Specifies assembly binding policy at the configuration level.</span></span>

<span data-ttu-id="a8259-104">configuração &nbsp; &nbsp; [\*\* \<>\*\*](configuration-element.md) \*\* \<montagem>vinculante\*\*</span><span class="sxs-lookup"><span data-stu-id="a8259-104">[**\<configuration>**](configuration-element.md) &nbsp;&nbsp;**\<assemblyBinding>**</span></span>

## <a name="syntax"></a><span data-ttu-id="a8259-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a8259-105">Syntax</span></span>

```xml
<assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
  <!-- Configuration files to include. -->
</assemblyBinding>
```

## <a name="attribute"></a><span data-ttu-id="a8259-106">Atributo</span><span class="sxs-lookup"><span data-stu-id="a8259-106">Attribute</span></span>

|           | <span data-ttu-id="a8259-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="a8259-107">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="a8259-108">**xmlns**</span><span class="sxs-lookup"><span data-stu-id="a8259-108">**xmlns**</span></span> | <span data-ttu-id="a8259-109">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="a8259-109">Required attribute.</span></span><br><br><span data-ttu-id="a8259-110">Especifica o espaço de nome XML necessário para a vinculação do conjunto.</span><span class="sxs-lookup"><span data-stu-id="a8259-110">Specifies the XML namespace required for assembly binding.</span></span> <span data-ttu-id="a8259-111">Use a string "urna:schemas-microsoft-com:asm.v1" como valor.</span><span class="sxs-lookup"><span data-stu-id="a8259-111">Use the string "urn:schemas-microsoft-com:asm.v1" as the value.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="a8259-112">Elemento pai</span><span class="sxs-lookup"><span data-stu-id="a8259-112">Parent element</span></span>

|     | <span data-ttu-id="a8259-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="a8259-113">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="a8259-114">**\<>de configuração**</span><span class="sxs-lookup"><span data-stu-id="a8259-114">**\<configuration>**</span></span>](configuration-element.md) | <span data-ttu-id="a8259-115">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a8259-115">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-element"></a><span data-ttu-id="a8259-116">Elemento filho</span><span class="sxs-lookup"><span data-stu-id="a8259-116">Child element</span></span>

|     | <span data-ttu-id="a8259-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="a8259-117">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="a8259-118">**\<>de configuração de linked**</span><span class="sxs-lookup"><span data-stu-id="a8259-118">**\<linkedConfiguration>**</span></span>](linkedconfiguration-element.md) | <span data-ttu-id="a8259-119">Especifica um arquivo de configuração a ser incluído.</span><span class="sxs-lookup"><span data-stu-id="a8259-119">Specifies a configuration file to include.</span></span> |

## <a name="remarks"></a><span data-ttu-id="a8259-120">Comentários</span><span class="sxs-lookup"><span data-stu-id="a8259-120">Remarks</span></span>

<span data-ttu-id="a8259-121">O elemento [\*\* \<linkedConfiguration>\*\*](linkedconfiguration-element.md) simplifica o gerenciamento de conjuntos de componentes, permitindo que os arquivos de configuração de aplicativos incluam arquivos de configuração de montagem em locais conhecidos, em vez de duplicar configurações de configuração de montagem.</span><span class="sxs-lookup"><span data-stu-id="a8259-121">The [**\<linkedConfiguration>**](linkedconfiguration-element.md) element simplifies the management of component assemblies by allowing application configuration files to include assembly configuration files in well-known locations, rather than duplicating assembly configuration settings.</span></span>

> [!NOTE]
> <span data-ttu-id="a8259-122">O elemento \*\* \<linkedConfiguration>\*\* não é suportado para aplicativos com manifestos lado a lado do Windows.</span><span class="sxs-lookup"><span data-stu-id="a8259-122">The **\<linkedConfiguration>** element is not supported for applications with Windows side-by-side manifests.</span></span>

## <a name="example"></a><span data-ttu-id="a8259-123">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a8259-123">Example</span></span>

<span data-ttu-id="a8259-124">O exemplo a seguir mostra como incluir um arquivo de configuração no disco rígido local:</span><span class="sxs-lookup"><span data-stu-id="a8259-124">The following example shows how to include a configuration file on the local hard disk:</span></span>

```xml
<configuration>
  <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
    <linkedConfiguration href="file://c:\Program Files\Contoso\sharedConfig.xml" />
  </assemblyBinding>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="a8259-125">Confira também</span><span class="sxs-lookup"><span data-stu-id="a8259-125">See also</span></span>

- [<span data-ttu-id="a8259-126">Esquema de arquivo de configuração para o Framework .NET</span><span class="sxs-lookup"><span data-stu-id="a8259-126">Configuration file schema for the .NET Framework</span></span>](index.md)
