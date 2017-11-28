---
title: '&lt;linkedConfiguration&gt; elemento'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "6"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: bfea438ec19303c35ad9d7a2816cb7b9473a00c0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="linkedconfiguration-element"></a><span data-ttu-id="5635a-102">\<linkedConfiguration > elemento</span><span class="sxs-lookup"><span data-stu-id="5635a-102">\<linkedConfiguration> element</span></span>

<span data-ttu-id="5635a-103">Especifica um arquivo de configuração a ser incluído.</span><span class="sxs-lookup"><span data-stu-id="5635a-103">Specifies a configuration file to include.</span></span>

<span data-ttu-id="5635a-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="5635a-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="5635a-105">&nbsp;&nbsp;[**\<assemblyBinding >**](~/docs/framework/configure-apps/file-schema/assemblybinding-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="5635a-105">&nbsp;&nbsp;[**\<assemblyBinding>**](~/docs/framework/configure-apps/file-schema/assemblybinding-element-for-configuration.md) </span></span>  
<span data-ttu-id="5635a-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<linkedConfiguration >**</span><span class="sxs-lookup"><span data-stu-id="5635a-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<linkedConfiguration>**</span></span>

## <a name="syntax"></a><span data-ttu-id="5635a-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5635a-107">Syntax</span></span>

```xml
<linkedConfiguration href="URL of linked configuration file" />
```

## <a name="attribute"></a><span data-ttu-id="5635a-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="5635a-108">Attribute</span></span>

|           | <span data-ttu-id="5635a-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="5635a-109">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="5635a-110">**href**</span><span class="sxs-lookup"><span data-stu-id="5635a-110">**href**</span></span>  | <span data-ttu-id="5635a-111">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="5635a-111">Required attribute.</span></span><br><br><span data-ttu-id="5635a-112">A URL do arquivo de configuração a ser incluído.</span><span class="sxs-lookup"><span data-stu-id="5635a-112">The URL of the configuration file to include.</span></span> <span data-ttu-id="5635a-113">O único formato com suporte para o **href** atributo é `file://`.</span><span class="sxs-lookup"><span data-stu-id="5635a-113">The only format supported for the **href** attribute is `file://`.</span></span> <span data-ttu-id="5635a-114">Há suporte para arquivos locais e UNC.</span><span class="sxs-lookup"><span data-stu-id="5635a-114">Local files and UNC files are supported.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="5635a-115">Elemento pai</span><span class="sxs-lookup"><span data-stu-id="5635a-115">Parent element</span></span>

|     | <span data-ttu-id="5635a-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="5635a-116">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="5635a-117">**\<assemblyBinding >** elemento</span><span class="sxs-lookup"><span data-stu-id="5635a-117">**\<assemblyBinding>** Element</span></span>](~/docs/framework/configure-apps/file-schema/assemblybinding-element-for-configuration.md) | <span data-ttu-id="5635a-118">Especifica a diretiva de ligação de assembly no nível de configuração.</span><span class="sxs-lookup"><span data-stu-id="5635a-118">Specifies assembly binding policy at the configuration level.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="5635a-119">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="5635a-119">Child elements</span></span>

<span data-ttu-id="5635a-120">Nenhum</span><span class="sxs-lookup"><span data-stu-id="5635a-120">None</span></span>

## <a name="remarks"></a><span data-ttu-id="5635a-121">Comentários</span><span class="sxs-lookup"><span data-stu-id="5635a-121">Remarks</span></span>

<span data-ttu-id="5635a-122">O  **\<linkedConfiguration >** elemento simplifica a manutenção de assemblies do componente.</span><span class="sxs-lookup"><span data-stu-id="5635a-122">The **\<linkedConfiguration>** element simplifies servicing for component assemblies.</span></span> <span data-ttu-id="5635a-123">Se um ou mais aplicativos usam um assembly que tem um arquivo de configuração que residem em um local conhecido, os arquivos de configuração dos aplicativos que usam o assembly podem usar o  **\<linkedConfiguration >** elemento para incluir o arquivo de configuração do assembly, em vez de incluindo informações de configuração diretamente.</span><span class="sxs-lookup"><span data-stu-id="5635a-123">If one or more applications use an assembly that has a configuration file residing in a well-known location, the configuration files of the applications that use the assembly can use the **\<linkedConfiguration>** element to include the assembly configuration file, rather than including configuration information directly.</span></span> <span data-ttu-id="5635a-124">Quando o componente de assembly é atendida, atualizando o arquivo de configuração comuns fornece informações de configuração atualizada para todos os aplicativos que usam o assembly.</span><span class="sxs-lookup"><span data-stu-id="5635a-124">When the component assembly is serviced, updating the common configuration file provides updated configuration information to all applications that use the assembly.</span></span>

> [!NOTE]
> <span data-ttu-id="5635a-125">O  **\<linkedConfiguration >** elemento não tem suporte para aplicativos com manifestos de lado a lado do Windows.</span><span class="sxs-lookup"><span data-stu-id="5635a-125">The **\<linkedConfiguration>** element is not supported for applications with Windows side-by-side manifests.</span></span>

<span data-ttu-id="5635a-126">As seguintes regras regem o uso de arquivos de configuração vinculada:</span><span class="sxs-lookup"><span data-stu-id="5635a-126">The following rules govern the use of linked configuration files:</span></span>

- <span data-ttu-id="5635a-127">As configurações nos arquivos de configuração incluídos somente afetam a diretiva de associação do carregador e são usadas apenas pelo carregador.</span><span class="sxs-lookup"><span data-stu-id="5635a-127">The settings in included configuration files only affect loader binding policy and are used only by the loader.</span></span> <span data-ttu-id="5635a-128">Os arquivos de configuração incluídos podem ter configurações diferentes políticas de associação, mas essas configurações não terão nenhum efeito.</span><span class="sxs-lookup"><span data-stu-id="5635a-128">The included configuration files can have settings other than binding policies, but those settings don't have any effect.</span></span>

- <span data-ttu-id="5635a-129">O único formato com suporte para o `href` atributo é `file://`.</span><span class="sxs-lookup"><span data-stu-id="5635a-129">The only format supported for the `href` attribute is `file://`.</span></span> <span data-ttu-id="5635a-130">Há suporte para arquivos locais e UNC.</span><span class="sxs-lookup"><span data-stu-id="5635a-130">Local files and UNC files are supported.</span></span>

- <span data-ttu-id="5635a-131">Não há nenhuma restrição no número de configurações vinculadas por arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="5635a-131">There is no constraint on the number of linked configurations per configuration file.</span></span>

- <span data-ttu-id="5635a-132">Todos os arquivos de configuração vinculados serão mesclados para formar um arquivo, semelhante ao comportamento da `#include` diretiva em C/C++.</span><span class="sxs-lookup"><span data-stu-id="5635a-132">All linked configuration files are merged to form one file, similar to the behavior of the `#include` directive in C/C++.</span></span>

- <span data-ttu-id="5635a-133">O  **\<linkedConfiguration >** elemento é permitido somente em arquivos de configuração do aplicativo; é ignorado em *Machine. config*.</span><span class="sxs-lookup"><span data-stu-id="5635a-133">The **\<linkedConfiguration>** element is allowed only in application configuration files; it's ignored in *Machine.config*.</span></span>

- <span data-ttu-id="5635a-134">Referências circulares são detectadas e encerradas.</span><span class="sxs-lookup"><span data-stu-id="5635a-134">Circular references are detected and terminated.</span></span> <span data-ttu-id="5635a-135">Ou seja, se o  **\<linkedConfiguration >** elementos de uma série de arquivos de configuração formam um loop, o loop é detectado e interrompido.</span><span class="sxs-lookup"><span data-stu-id="5635a-135">That is, if the **\<linkedConfiguration>** elements of a series of configuration files form a loop, the loop is detected and stopped.</span></span>

## <a name="example"></a><span data-ttu-id="5635a-136">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5635a-136">Example</span></span>

<span data-ttu-id="5635a-137">O exemplo a seguir mostra como incluir um arquivo de configuração do disco rígido local:</span><span class="sxs-lookup"><span data-stu-id="5635a-137">The following example shows how to include configuration file from the local hard disk:</span></span>

```xml
<configuration>
  <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
    <linkedConfiguration href="file://c:\Program Files\Contoso\sharedConfig.xml"/>
  </assemblyBinding>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="5635a-138">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5635a-138">See also</span></span>

<span data-ttu-id="5635a-139">[**\<assemblyBinding >** elemento](~/docs/framework/configure-apps/file-schema/assemblybinding-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="5635a-139">[**\<assemblyBinding>** Element](~/docs/framework/configure-apps/file-schema/assemblybinding-element-for-configuration.md) </span></span>  
[<span data-ttu-id="5635a-140">Esquema de arquivo de configuração para o .NET Framework</span><span class="sxs-lookup"><span data-stu-id="5635a-140">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
