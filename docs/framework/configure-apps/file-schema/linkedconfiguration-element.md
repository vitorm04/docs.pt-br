---
title: Elemento <linkedConfiguration>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/assemblyBinding/linkedConfiguration
- http://schemas.microsoft.com/.NetConfiguration/v2.0#linkedConfiguration
helpviewer_keywords:
- configuration files [.NET Framework],linked configuration files
- <linkedConfiguration> element
- including configuration files
- linked configuration files
- linkedConfiguration Element
ms.assetid: 8eb34f3b-427e-4288-a7ff-c73f489deb45
ms.openlocfilehash: 14ee2275ecf690ab16ffaabd71fbbe7e1a4897bc
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "74087958"
---
# <a name="linkedconfiguration-element"></a><span data-ttu-id="5afd2-102">Elemento \<linkedConfiguration></span><span class="sxs-lookup"><span data-stu-id="5afd2-102">\<linkedConfiguration> element</span></span>

<span data-ttu-id="5afd2-103">Especifica um arquivo de configuração a ser incluído.</span><span class="sxs-lookup"><span data-stu-id="5afd2-103">Specifies a configuration file to include.</span></span>

[**\<configuration>**](configuration-element.md)\
&nbsp;&nbsp;[**\<assemblyBinding>**](assemblybinding-element-for-configuration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<linkedConfiguration>**

## <a name="syntax"></a><span data-ttu-id="5afd2-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5afd2-104">Syntax</span></span>

```xml
<linkedConfiguration href="URL of linked configuration file" />
```

## <a name="attribute"></a><span data-ttu-id="5afd2-105">Atributo</span><span class="sxs-lookup"><span data-stu-id="5afd2-105">Attribute</span></span>

|           | <span data-ttu-id="5afd2-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="5afd2-106">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="5afd2-107">**href**</span><span class="sxs-lookup"><span data-stu-id="5afd2-107">**href**</span></span>  | <span data-ttu-id="5afd2-108">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="5afd2-108">Required attribute.</span></span><br><br><span data-ttu-id="5afd2-109">A URL do arquivo de configuração a ser incluído.</span><span class="sxs-lookup"><span data-stu-id="5afd2-109">The URL of the configuration file to include.</span></span> <span data-ttu-id="5afd2-110">O único formato com suporte para o atributo **href** é `file://` .</span><span class="sxs-lookup"><span data-stu-id="5afd2-110">The only format supported for the **href** attribute is `file://`.</span></span> <span data-ttu-id="5afd2-111">Há suporte para arquivos locais e arquivos UNC.</span><span class="sxs-lookup"><span data-stu-id="5afd2-111">Local files and UNC files are supported.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="5afd2-112">Elemento pai</span><span class="sxs-lookup"><span data-stu-id="5afd2-112">Parent element</span></span>

|     | <span data-ttu-id="5afd2-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="5afd2-113">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="5afd2-114">**\<assemblyBinding>** Elementos</span><span class="sxs-lookup"><span data-stu-id="5afd2-114">**\<assemblyBinding>** Element</span></span>](assemblybinding-element-for-configuration.md) | <span data-ttu-id="5afd2-115">Especifica a diretiva de ligação de assembly no nível de configuração.</span><span class="sxs-lookup"><span data-stu-id="5afd2-115">Specifies assembly binding policy at the configuration level.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="5afd2-116">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="5afd2-116">Child elements</span></span>

<span data-ttu-id="5afd2-117">Nenhum</span><span class="sxs-lookup"><span data-stu-id="5afd2-117">None</span></span>

## <a name="remarks"></a><span data-ttu-id="5afd2-118">Comentários</span><span class="sxs-lookup"><span data-stu-id="5afd2-118">Remarks</span></span>

<span data-ttu-id="5afd2-119">O **\<linkedConfiguration>** elemento simplifica a manutenção de assemblies de componentes.</span><span class="sxs-lookup"><span data-stu-id="5afd2-119">The **\<linkedConfiguration>** element simplifies servicing for component assemblies.</span></span> <span data-ttu-id="5afd2-120">Se um ou mais aplicativos usarem um assembly que tenha um arquivo de configuração que resida em um local bem conhecido, os arquivos de configuração dos aplicativos que usam o assembly poderão usar o **\<linkedConfiguration>** elemento para incluir o arquivo de configuração do assembly, em vez de incluir informações de configuração diretamente.</span><span class="sxs-lookup"><span data-stu-id="5afd2-120">If one or more applications use an assembly that has a configuration file residing in a well-known location, the configuration files of the applications that use the assembly can use the **\<linkedConfiguration>** element to include the assembly configuration file, rather than including configuration information directly.</span></span> <span data-ttu-id="5afd2-121">Quando o assembly de componente é atendido, a atualização do arquivo de configuração comum fornece informações de configuração atualizadas para todos os aplicativos que usam o assembly.</span><span class="sxs-lookup"><span data-stu-id="5afd2-121">When the component assembly is serviced, updating the common configuration file provides updated configuration information to all applications that use the assembly.</span></span>

> [!NOTE]
> <span data-ttu-id="5afd2-122">O **\<linkedConfiguration>** elemento não tem suporte para aplicativos com manifestos lado a lado do Windows.</span><span class="sxs-lookup"><span data-stu-id="5afd2-122">The **\<linkedConfiguration>** element is not supported for applications with Windows side-by-side manifests.</span></span>

<span data-ttu-id="5afd2-123">As regras a seguir regem o uso de arquivos de configuração vinculados:</span><span class="sxs-lookup"><span data-stu-id="5afd2-123">The following rules govern the use of linked configuration files:</span></span>

- <span data-ttu-id="5afd2-124">As configurações nos arquivos de configuração incluídos afetam apenas a política de associação do carregador e são usadas somente pelo carregador.</span><span class="sxs-lookup"><span data-stu-id="5afd2-124">The settings in included configuration files only affect loader binding policy and are used only by the loader.</span></span> <span data-ttu-id="5afd2-125">Os arquivos de configuração incluídos podem ter configurações diferentes de diretivas de associação, mas essas configurações não têm nenhum efeito.</span><span class="sxs-lookup"><span data-stu-id="5afd2-125">The included configuration files can have settings other than binding policies, but those settings don't have any effect.</span></span>

- <span data-ttu-id="5afd2-126">O único formato com suporte para o `href` atributo é `file://` .</span><span class="sxs-lookup"><span data-stu-id="5afd2-126">The only format supported for the `href` attribute is `file://`.</span></span> <span data-ttu-id="5afd2-127">Há suporte para arquivos locais e arquivos UNC.</span><span class="sxs-lookup"><span data-stu-id="5afd2-127">Local files and UNC files are supported.</span></span>

- <span data-ttu-id="5afd2-128">Não há nenhuma restrição quanto ao número de configurações vinculadas por arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="5afd2-128">There is no constraint on the number of linked configurations per configuration file.</span></span>

- <span data-ttu-id="5afd2-129">Todos os arquivos de configuração vinculados são mesclados para formar um arquivo, semelhante ao comportamento da `#include` diretiva em C/C++.</span><span class="sxs-lookup"><span data-stu-id="5afd2-129">All linked configuration files are merged to form one file, similar to the behavior of the `#include` directive in C/C++.</span></span>

- <span data-ttu-id="5afd2-130">O **\<linkedConfiguration>** elemento é permitido somente em arquivos de configuração de aplicativo; ele é ignorado em *Machine. config*.</span><span class="sxs-lookup"><span data-stu-id="5afd2-130">The **\<linkedConfiguration>** element is allowed only in application configuration files; it's ignored in *Machine.config*.</span></span>

- <span data-ttu-id="5afd2-131">Referências circulares são detectadas e terminadas.</span><span class="sxs-lookup"><span data-stu-id="5afd2-131">Circular references are detected and terminated.</span></span> <span data-ttu-id="5afd2-132">Ou seja, se os **\<linkedConfiguration>** elementos de uma série de arquivos de configuração formam um loop, o loop é detectado e interrompido.</span><span class="sxs-lookup"><span data-stu-id="5afd2-132">That is, if the **\<linkedConfiguration>** elements of a series of configuration files form a loop, the loop is detected and stopped.</span></span>

## <a name="example"></a><span data-ttu-id="5afd2-133">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5afd2-133">Example</span></span>

<span data-ttu-id="5afd2-134">O exemplo a seguir mostra como incluir o arquivo de configuração do disco rígido local:</span><span class="sxs-lookup"><span data-stu-id="5afd2-134">The following example shows how to include configuration file from the local hard disk:</span></span>

```xml
<configuration>
  <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
    <linkedConfiguration href="file://c:\Program Files\Contoso\sharedConfig.xml"/>
  </assemblyBinding>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="5afd2-135">Confira também</span><span class="sxs-lookup"><span data-stu-id="5afd2-135">See also</span></span>

- [<span data-ttu-id="5afd2-136">**\<assemblyBinding>** Elementos</span><span class="sxs-lookup"><span data-stu-id="5afd2-136">**\<assemblyBinding>** Element</span></span>](assemblybinding-element-for-configuration.md)
- [<span data-ttu-id="5afd2-137">Esquema do arquivo de configuração para o .NET Framework</span><span class="sxs-lookup"><span data-stu-id="5afd2-137">Configuration file schema for the .NET Framework</span></span>](index.md)
