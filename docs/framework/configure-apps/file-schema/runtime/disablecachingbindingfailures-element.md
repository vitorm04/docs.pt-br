---
title: Elemento <disableCachingBindingFailures>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#disableCachingBindingFailures
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/disableCachingBindingFailures
helpviewer_keywords:
- assemblies [.NET Framework],caching binding failures
- caching assembly binding failures
- <disableCachingBindingFailures> element
- disableCachingBindingFailures element
ms.assetid: bf598873-83b7-48de-8955-00b0504fbad0
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d5b45ea4b30677d17e72685b16c19f9192c8c144
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252674"
---
# <a name="disablecachingbindingfailures-element"></a><span data-ttu-id="0a896-102">\<Elemento de > disableCachingBindingFailures</span><span class="sxs-lookup"><span data-stu-id="0a896-102">\<disableCachingBindingFailures> Element</span></span>
<span data-ttu-id="0a896-103">Especifica se é para desabilitar o cache de falhas de associação que ocorrem porque o assembly não foi encontrado pela investigação.</span><span class="sxs-lookup"><span data-stu-id="0a896-103">Specifies whether to disable the caching of binding failures that occur because the assembly was not found by probing.</span></span>  
  
<span data-ttu-id="0a896-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="0a896-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="0a896-105">&nbsp;&nbsp;[ **\<> de tempo de execução**](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="0a896-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="0a896-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<disableCachingBindingFailures>**</span><span class="sxs-lookup"><span data-stu-id="0a896-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<disableCachingBindingFailures>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0a896-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0a896-107">Syntax</span></span>  
  
```xml  
<disableCachingBindingFailures enabled="0|1"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0a896-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="0a896-108">Attributes and Elements</span></span>  
 <span data-ttu-id="0a896-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="0a896-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0a896-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="0a896-110">Attributes</span></span>  
  
|<span data-ttu-id="0a896-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="0a896-111">Attribute</span></span>|<span data-ttu-id="0a896-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="0a896-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0a896-113">enabled</span><span class="sxs-lookup"><span data-stu-id="0a896-113">enabled</span></span>|<span data-ttu-id="0a896-114">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="0a896-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="0a896-115">Especifica se é para desabilitar o cache de falhas de associação que ocorrem porque o assembly não foi encontrado pela investigação.</span><span class="sxs-lookup"><span data-stu-id="0a896-115">Specifies whether to disable the caching of binding failures that occur because the assembly was not found by probing.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="0a896-116">Atributo habilitado</span><span class="sxs-lookup"><span data-stu-id="0a896-116">enabled Attribute</span></span>  
  
|<span data-ttu-id="0a896-117">Valor</span><span class="sxs-lookup"><span data-stu-id="0a896-117">Value</span></span>|<span data-ttu-id="0a896-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="0a896-118">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="0a896-119">0</span><span class="sxs-lookup"><span data-stu-id="0a896-119">0</span></span>|<span data-ttu-id="0a896-120">Não desabilite o cache de falhas de associação que ocorrem porque o assembly não foi encontrado pela investigação.</span><span class="sxs-lookup"><span data-stu-id="0a896-120">Do not disable the caching of binding failures that occur because the assembly was not found by probing.</span></span> <span data-ttu-id="0a896-121">Esse é o comportamento de associação padrão a partir do .NET Framework versão 2,0.</span><span class="sxs-lookup"><span data-stu-id="0a896-121">This is the default binding behavior starting with the .NET Framework version 2.0.</span></span>|  
|<span data-ttu-id="0a896-122">1</span><span class="sxs-lookup"><span data-stu-id="0a896-122">1</span></span>|<span data-ttu-id="0a896-123">Desabilite o cache de falhas de associação que ocorrem porque o assembly não foi encontrado pela investigação.</span><span class="sxs-lookup"><span data-stu-id="0a896-123">Disable the caching of binding failures that occur because the assembly was not found by probing.</span></span> <span data-ttu-id="0a896-124">Essa configuração reverte para o comportamento de associação do .NET Framework versão 1,1.</span><span class="sxs-lookup"><span data-stu-id="0a896-124">This setting reverts to the binding behavior of the .NET Framework version 1.1.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0a896-125">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="0a896-125">Child Elements</span></span>  
 <span data-ttu-id="0a896-126">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="0a896-126">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0a896-127">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="0a896-127">Parent Elements</span></span>  
  
|<span data-ttu-id="0a896-128">Elemento</span><span class="sxs-lookup"><span data-stu-id="0a896-128">Element</span></span>|<span data-ttu-id="0a896-129">Descrição</span><span class="sxs-lookup"><span data-stu-id="0a896-129">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="0a896-130">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="0a896-130">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="0a896-131">Contém informações sobre associação do assembly e coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="0a896-131">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0a896-132">Comentários</span><span class="sxs-lookup"><span data-stu-id="0a896-132">Remarks</span></span>  
 <span data-ttu-id="0a896-133">A partir do .NET Framework versão 2,0, o comportamento padrão para carregar assemblies é armazenar em cache todas as falhas de associação e carregamento.</span><span class="sxs-lookup"><span data-stu-id="0a896-133">Starting with the .NET Framework version 2.0, the default behavior for loading assemblies is to cache all binding and loading failures.</span></span> <span data-ttu-id="0a896-134">Ou seja, se uma tentativa de carregar um assembly falhar, as solicitações subsequentes para carregar o mesmo assembly falharão imediatamente, sem nenhuma tentativa de localizar o assembly.</span><span class="sxs-lookup"><span data-stu-id="0a896-134">That is, if an attempt to load an assembly fails, subsequent requests to load the same assembly fail immediately, without any attempt to locate the assembly.</span></span> <span data-ttu-id="0a896-135">Esse elemento desabilita esse comportamento padrão para falhas de associação que ocorrem porque o assembly não foi encontrado no caminho de investigação.</span><span class="sxs-lookup"><span data-stu-id="0a896-135">This element disables that default behavior for binding failures that occur because the assembly could not be found in the probing path.</span></span> <span data-ttu-id="0a896-136">Essas falhas geram <xref:System.IO.FileNotFoundException>.</span><span class="sxs-lookup"><span data-stu-id="0a896-136">These failures throw <xref:System.IO.FileNotFoundException>.</span></span>  
  
 <span data-ttu-id="0a896-137">Algumas falhas de ligação e carregamento não são afetadas por esse elemento e sempre são armazenadas em cache.</span><span class="sxs-lookup"><span data-stu-id="0a896-137">Some binding and loading failures are not affected by this element, and are always cached.</span></span> <span data-ttu-id="0a896-138">Essas falhas ocorrem porque o assembly foi encontrado, mas não pôde ser carregado.</span><span class="sxs-lookup"><span data-stu-id="0a896-138">These failures occur because the assembly was found but could not be loaded.</span></span> <span data-ttu-id="0a896-139">Eles <xref:System.BadImageFormatException> lançam <xref:System.IO.FileLoadException>ou.</span><span class="sxs-lookup"><span data-stu-id="0a896-139">They throw <xref:System.BadImageFormatException> or <xref:System.IO.FileLoadException>.</span></span> <span data-ttu-id="0a896-140">A lista a seguir inclui alguns exemplos de tais falhas.</span><span class="sxs-lookup"><span data-stu-id="0a896-140">The following list includes some examples of such failures.</span></span>  
  
- <span data-ttu-id="0a896-141">Se você tentar carregar um arquivo não for um assembly válido, as tentativas subsequentes de carregar o assembly falharão mesmo que o arquivo incorreto seja substituído pelo assembly correto.</span><span class="sxs-lookup"><span data-stu-id="0a896-141">If you attempt to load a file is not a valid assembly, subsequent attempts to load the assembly will fail even if the bad file is replaced with the correct assembly.</span></span>  
  
- <span data-ttu-id="0a896-142">Se você tentar carregar um assembly que está bloqueado pelo sistema de arquivos, as tentativas subsequentes de carregar o assembly falharão mesmo depois que o assembly for liberado pelo sistema de arquivos.</span><span class="sxs-lookup"><span data-stu-id="0a896-142">If you attempt to load an assembly that is locked by the file system, subsequent attempts to load the assembly will fail even after the assembly is released by the file system.</span></span>  
  
- <span data-ttu-id="0a896-143">Se uma ou mais versões do assembly que você está tentando carregar estiver no caminho de investigação, mas a versão específica que você está solicitando não estiver entre elas, as tentativas subsequentes de carregar essa versão falharão mesmo que a versão correta seja movida para o caminho de investigação.</span><span class="sxs-lookup"><span data-stu-id="0a896-143">If one or more versions of the assembly that you are attempting to load is in the probing path, but the specific version you are requesting is not among them, subsequent attempts to load that version will fail even if the correct version is moved into the probing path.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0a896-144">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0a896-144">Example</span></span>  
 <span data-ttu-id="0a896-145">O exemplo a seguir mostra como desabilitar o cache de falhas de associação de assembly que ocorrem porque o assembly não foi encontrado pela investigação.</span><span class="sxs-lookup"><span data-stu-id="0a896-145">The following example shows how to disable the caching of assembly binding failures that occur because the assembly was not found by probing.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <disableCachingBindingFailures enabled="1" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="0a896-146">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0a896-146">See also</span></span>

- [<span data-ttu-id="0a896-147">Esquema de configurações do tempo de execução</span><span class="sxs-lookup"><span data-stu-id="0a896-147">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="0a896-148">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="0a896-148">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="0a896-149">Como o tempo de execução localiza assemblies</span><span class="sxs-lookup"><span data-stu-id="0a896-149">How the Runtime Locates Assemblies</span></span>](../../../deployment/how-the-runtime-locates-assemblies.md)
