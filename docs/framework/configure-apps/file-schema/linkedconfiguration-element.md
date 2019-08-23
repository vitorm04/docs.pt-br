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
ms.openlocfilehash: a0b56ac66302f11c59c149197a84bb96691282a5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69921010"
---
# <a name="linkedconfiguration-element"></a><span data-ttu-id="bb4ab-102">\<elemento de > linkedConfiguration</span><span class="sxs-lookup"><span data-stu-id="bb4ab-102">\<linkedConfiguration> element</span></span>

<span data-ttu-id="bb4ab-103">Especifica um arquivo de configuração a ser incluído.</span><span class="sxs-lookup"><span data-stu-id="bb4ab-103">Specifies a configuration file to include.</span></span>

<span data-ttu-id="bb4ab-104">[ **\<configuration>** ](configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="bb4ab-104">[**\<configuration>**](configuration-element.md) </span></span>  
<span data-ttu-id="bb4ab-105">&nbsp;&nbsp;[ **\<assemblyBinding>** ](assemblybinding-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="bb4ab-105">&nbsp;&nbsp;[**\<assemblyBinding>**](assemblybinding-element-for-configuration.md) </span></span>  
<span data-ttu-id="bb4ab-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<linkedConfiguration>**</span><span class="sxs-lookup"><span data-stu-id="bb4ab-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<linkedConfiguration>**</span></span>

## <a name="syntax"></a><span data-ttu-id="bb4ab-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bb4ab-107">Syntax</span></span>

```xml
<linkedConfiguration href="URL of linked configuration file" />
```

## <a name="attribute"></a><span data-ttu-id="bb4ab-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="bb4ab-108">Attribute</span></span>

|           | <span data-ttu-id="bb4ab-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="bb4ab-109">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="bb4ab-110">**href**</span><span class="sxs-lookup"><span data-stu-id="bb4ab-110">**href**</span></span>  | <span data-ttu-id="bb4ab-111">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="bb4ab-111">Required attribute.</span></span><br><br><span data-ttu-id="bb4ab-112">A URL do arquivo de configuração a ser incluído.</span><span class="sxs-lookup"><span data-stu-id="bb4ab-112">The URL of the configuration file to include.</span></span> <span data-ttu-id="bb4ab-113">O único formato com suporte para o atributo href `file://`é.</span><span class="sxs-lookup"><span data-stu-id="bb4ab-113">The only format supported for the **href** attribute is `file://`.</span></span> <span data-ttu-id="bb4ab-114">Há suporte para arquivos locais e arquivos UNC.</span><span class="sxs-lookup"><span data-stu-id="bb4ab-114">Local files and UNC files are supported.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="bb4ab-115">Elemento pai</span><span class="sxs-lookup"><span data-stu-id="bb4ab-115">Parent element</span></span>

|     | <span data-ttu-id="bb4ab-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="bb4ab-116">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="bb4ab-117">elemento de > assemblyBinding  **\<** </span><span class="sxs-lookup"><span data-stu-id="bb4ab-117">**\<assemblyBinding>** Element</span></span>](assemblybinding-element-for-configuration.md) | <span data-ttu-id="bb4ab-118">Especifica a diretiva de ligação de assembly no nível de configuração.</span><span class="sxs-lookup"><span data-stu-id="bb4ab-118">Specifies assembly binding policy at the configuration level.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="bb4ab-119">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="bb4ab-119">Child elements</span></span>

<span data-ttu-id="bb4ab-120">Nenhum</span><span class="sxs-lookup"><span data-stu-id="bb4ab-120">None</span></span>

## <a name="remarks"></a><span data-ttu-id="bb4ab-121">Comentários</span><span class="sxs-lookup"><span data-stu-id="bb4ab-121">Remarks</span></span>

<span data-ttu-id="bb4ab-122">O elemento  **\<> linkedConfiguration** simplifica a manutenção de assemblies de componente.</span><span class="sxs-lookup"><span data-stu-id="bb4ab-122">The **\<linkedConfiguration>** element simplifies servicing for component assemblies.</span></span> <span data-ttu-id="bb4ab-123">Se um ou mais aplicativos usarem um assembly que tenha um arquivo de configuração que resida em um local bem conhecido, os arquivos de configuração dos aplicativos que usam o assembly poderão usar o  **\<elemento > linkedConfiguration** para incluir o arquivo de configuração do assembly, em vez de incluir informações de configuração diretamente.</span><span class="sxs-lookup"><span data-stu-id="bb4ab-123">If one or more applications use an assembly that has a configuration file residing in a well-known location, the configuration files of the applications that use the assembly can use the **\<linkedConfiguration>** element to include the assembly configuration file, rather than including configuration information directly.</span></span> <span data-ttu-id="bb4ab-124">Quando o assembly de componente é atendido, a atualização do arquivo de configuração comum fornece informações de configuração atualizadas para todos os aplicativos que usam o assembly.</span><span class="sxs-lookup"><span data-stu-id="bb4ab-124">When the component assembly is serviced, updating the common configuration file provides updated configuration information to all applications that use the assembly.</span></span>

> [!NOTE]
> <span data-ttu-id="bb4ab-125">O elemento de  **\<> linkedConfiguration** não tem suporte para aplicativos com manifestos lado a lado do Windows.</span><span class="sxs-lookup"><span data-stu-id="bb4ab-125">The **\<linkedConfiguration>** element is not supported for applications with Windows side-by-side manifests.</span></span>

<span data-ttu-id="bb4ab-126">As regras a seguir regem o uso de arquivos de configuração vinculados:</span><span class="sxs-lookup"><span data-stu-id="bb4ab-126">The following rules govern the use of linked configuration files:</span></span>

- <span data-ttu-id="bb4ab-127">As configurações nos arquivos de configuração incluídos afetam apenas a política de associação do carregador e são usadas somente pelo carregador.</span><span class="sxs-lookup"><span data-stu-id="bb4ab-127">The settings in included configuration files only affect loader binding policy and are used only by the loader.</span></span> <span data-ttu-id="bb4ab-128">Os arquivos de configuração incluídos podem ter configurações diferentes de diretivas de associação, mas essas configurações não têm nenhum efeito.</span><span class="sxs-lookup"><span data-stu-id="bb4ab-128">The included configuration files can have settings other than binding policies, but those settings don't have any effect.</span></span>

- <span data-ttu-id="bb4ab-129">O único formato com suporte para `href` o atributo `file://`é.</span><span class="sxs-lookup"><span data-stu-id="bb4ab-129">The only format supported for the `href` attribute is `file://`.</span></span> <span data-ttu-id="bb4ab-130">Há suporte para arquivos locais e arquivos UNC.</span><span class="sxs-lookup"><span data-stu-id="bb4ab-130">Local files and UNC files are supported.</span></span>

- <span data-ttu-id="bb4ab-131">Não há nenhuma restrição quanto ao número de configurações vinculadas por arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="bb4ab-131">There is no constraint on the number of linked configurations per configuration file.</span></span>

- <span data-ttu-id="bb4ab-132">Todos os arquivos de configuração vinculados são mesclados para formar um arquivo, semelhante ao comportamento `#include` da diretiva em CC++/.</span><span class="sxs-lookup"><span data-stu-id="bb4ab-132">All linked configuration files are merged to form one file, similar to the behavior of the `#include` directive in C/C++.</span></span>

- <span data-ttu-id="bb4ab-133">**O\<elemento > linkedConfiguration** é permitido somente em arquivos de configuração de aplicativo; ele é ignorado em *Machine. config*.</span><span class="sxs-lookup"><span data-stu-id="bb4ab-133">The **\<linkedConfiguration>** element is allowed only in application configuration files; it's ignored in *Machine.config*.</span></span>

- <span data-ttu-id="bb4ab-134">Referências circulares são detectadas e terminadas.</span><span class="sxs-lookup"><span data-stu-id="bb4ab-134">Circular references are detected and terminated.</span></span> <span data-ttu-id="bb4ab-135">Ou seja, se o  **\<linkedConfiguration >** elementos de uma série de arquivos de configuração formam um loop, o loop será detectado e interrompido.</span><span class="sxs-lookup"><span data-stu-id="bb4ab-135">That is, if the **\<linkedConfiguration>** elements of a series of configuration files form a loop, the loop is detected and stopped.</span></span>

## <a name="example"></a><span data-ttu-id="bb4ab-136">Exemplo</span><span class="sxs-lookup"><span data-stu-id="bb4ab-136">Example</span></span>

<span data-ttu-id="bb4ab-137">O exemplo a seguir mostra como incluir o arquivo de configuração do disco rígido local:</span><span class="sxs-lookup"><span data-stu-id="bb4ab-137">The following example shows how to include configuration file from the local hard disk:</span></span>

```xml
<configuration>
  <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
    <linkedConfiguration href="file://c:\Program Files\Contoso\sharedConfig.xml"/>
  </assemblyBinding>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="bb4ab-138">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bb4ab-138">See also</span></span>

- [<span data-ttu-id="bb4ab-139">elemento de > assemblyBinding  **\<** </span><span class="sxs-lookup"><span data-stu-id="bb4ab-139">**\<assemblyBinding>** Element</span></span>](assemblybinding-element-for-configuration.md)
- [<span data-ttu-id="bb4ab-140">Esquema do arquivo de configuração para o .NET Framework</span><span class="sxs-lookup"><span data-stu-id="bb4ab-140">Configuration file schema for the .NET Framework</span></span>](index.md)
