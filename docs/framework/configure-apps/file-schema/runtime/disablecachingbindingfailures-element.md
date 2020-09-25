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
ms.openlocfilehash: c9e608bfd54b641564a9095076455e10dd8653fb
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91176117"
---
# <a name="disablecachingbindingfailures-element"></a><span data-ttu-id="ced3a-102">Elemento \<disableCachingBindingFailures></span><span class="sxs-lookup"><span data-stu-id="ced3a-102">\<disableCachingBindingFailures> Element</span></span>

<span data-ttu-id="ced3a-103">Especifica se é para desabilitar o cache de falhas de associação que ocorrem porque o assembly não foi encontrado pela investigação.</span><span class="sxs-lookup"><span data-stu-id="ced3a-103">Specifies whether to disable the caching of binding failures that occur because the assembly was not found by probing.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<disableCachingBindingFailures>**  
  
## <a name="syntax"></a><span data-ttu-id="ced3a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ced3a-104">Syntax</span></span>  
  
```xml  
<disableCachingBindingFailures enabled="0|1"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ced3a-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="ced3a-105">Attributes and Elements</span></span>  

 <span data-ttu-id="ced3a-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="ced3a-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ced3a-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="ced3a-107">Attributes</span></span>  
  
|<span data-ttu-id="ced3a-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="ced3a-108">Attribute</span></span>|<span data-ttu-id="ced3a-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="ced3a-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ced3a-110">Habilitado</span><span class="sxs-lookup"><span data-stu-id="ced3a-110">enabled</span></span>|<span data-ttu-id="ced3a-111">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="ced3a-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="ced3a-112">Especifica se é para desabilitar o cache de falhas de associação que ocorrem porque o assembly não foi encontrado pela investigação.</span><span class="sxs-lookup"><span data-stu-id="ced3a-112">Specifies whether to disable the caching of binding failures that occur because the assembly was not found by probing.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="ced3a-113">Atributo habilitado</span><span class="sxs-lookup"><span data-stu-id="ced3a-113">enabled Attribute</span></span>  
  
|<span data-ttu-id="ced3a-114">Valor</span><span class="sxs-lookup"><span data-stu-id="ced3a-114">Value</span></span>|<span data-ttu-id="ced3a-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="ced3a-115">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="ced3a-116">0</span><span class="sxs-lookup"><span data-stu-id="ced3a-116">0</span></span>|<span data-ttu-id="ced3a-117">Não desabilite o cache de falhas de associação que ocorrem porque o assembly não foi encontrado pela investigação.</span><span class="sxs-lookup"><span data-stu-id="ced3a-117">Do not disable the caching of binding failures that occur because the assembly was not found by probing.</span></span> <span data-ttu-id="ced3a-118">Esse é o comportamento de associação padrão a partir do .NET Framework versão 2,0.</span><span class="sxs-lookup"><span data-stu-id="ced3a-118">This is the default binding behavior starting with the .NET Framework version 2.0.</span></span>|  
|<span data-ttu-id="ced3a-119">1</span><span class="sxs-lookup"><span data-stu-id="ced3a-119">1</span></span>|<span data-ttu-id="ced3a-120">Desabilite o cache de falhas de associação que ocorrem porque o assembly não foi encontrado pela investigação.</span><span class="sxs-lookup"><span data-stu-id="ced3a-120">Disable the caching of binding failures that occur because the assembly was not found by probing.</span></span> <span data-ttu-id="ced3a-121">Essa configuração reverte para o comportamento de associação do .NET Framework versão 1,1.</span><span class="sxs-lookup"><span data-stu-id="ced3a-121">This setting reverts to the binding behavior of the .NET Framework version 1.1.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ced3a-122">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="ced3a-122">Child Elements</span></span>  

 <span data-ttu-id="ced3a-123">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="ced3a-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ced3a-124">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="ced3a-124">Parent Elements</span></span>  
  
|<span data-ttu-id="ced3a-125">Elemento</span><span class="sxs-lookup"><span data-stu-id="ced3a-125">Element</span></span>|<span data-ttu-id="ced3a-126">Descrição</span><span class="sxs-lookup"><span data-stu-id="ced3a-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="ced3a-127">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ced3a-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="ced3a-128">Contém informações sobre associação do assembly e coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="ced3a-128">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ced3a-129">Comentários</span><span class="sxs-lookup"><span data-stu-id="ced3a-129">Remarks</span></span>  

 <span data-ttu-id="ced3a-130">A partir do .NET Framework versão 2,0, o comportamento padrão para carregar assemblies é armazenar em cache todas as falhas de associação e carregamento.</span><span class="sxs-lookup"><span data-stu-id="ced3a-130">Starting with the .NET Framework version 2.0, the default behavior for loading assemblies is to cache all binding and loading failures.</span></span> <span data-ttu-id="ced3a-131">Ou seja, se uma tentativa de carregar um assembly falhar, as solicitações subsequentes para carregar o mesmo assembly falharão imediatamente, sem nenhuma tentativa de localizar o assembly.</span><span class="sxs-lookup"><span data-stu-id="ced3a-131">That is, if an attempt to load an assembly fails, subsequent requests to load the same assembly fail immediately, without any attempt to locate the assembly.</span></span> <span data-ttu-id="ced3a-132">Esse elemento desabilita esse comportamento padrão para falhas de associação que ocorrem porque o assembly não foi encontrado no caminho de investigação.</span><span class="sxs-lookup"><span data-stu-id="ced3a-132">This element disables that default behavior for binding failures that occur because the assembly could not be found in the probing path.</span></span> <span data-ttu-id="ced3a-133">Essas falhas geram <xref:System.IO.FileNotFoundException> .</span><span class="sxs-lookup"><span data-stu-id="ced3a-133">These failures throw <xref:System.IO.FileNotFoundException>.</span></span>  
  
 <span data-ttu-id="ced3a-134">Algumas falhas de ligação e carregamento não são afetadas por esse elemento e sempre são armazenadas em cache.</span><span class="sxs-lookup"><span data-stu-id="ced3a-134">Some binding and loading failures are not affected by this element, and are always cached.</span></span> <span data-ttu-id="ced3a-135">Essas falhas ocorrem porque o assembly foi encontrado, mas não pôde ser carregado.</span><span class="sxs-lookup"><span data-stu-id="ced3a-135">These failures occur because the assembly was found but could not be loaded.</span></span> <span data-ttu-id="ced3a-136">Eles lançam <xref:System.BadImageFormatException> ou <xref:System.IO.FileLoadException> .</span><span class="sxs-lookup"><span data-stu-id="ced3a-136">They throw <xref:System.BadImageFormatException> or <xref:System.IO.FileLoadException>.</span></span> <span data-ttu-id="ced3a-137">A lista a seguir inclui alguns exemplos de tais falhas.</span><span class="sxs-lookup"><span data-stu-id="ced3a-137">The following list includes some examples of such failures.</span></span>  
  
- <span data-ttu-id="ced3a-138">Se você tentar carregar um arquivo não for um assembly válido, as tentativas subsequentes de carregar o assembly falharão mesmo que o arquivo incorreto seja substituído pelo assembly correto.</span><span class="sxs-lookup"><span data-stu-id="ced3a-138">If you attempt to load a file is not a valid assembly, subsequent attempts to load the assembly will fail even if the bad file is replaced with the correct assembly.</span></span>  
  
- <span data-ttu-id="ced3a-139">Se você tentar carregar um assembly que está bloqueado pelo sistema de arquivos, as tentativas subsequentes de carregar o assembly falharão mesmo depois que o assembly for liberado pelo sistema de arquivos.</span><span class="sxs-lookup"><span data-stu-id="ced3a-139">If you attempt to load an assembly that is locked by the file system, subsequent attempts to load the assembly will fail even after the assembly is released by the file system.</span></span>  
  
- <span data-ttu-id="ced3a-140">Se uma ou mais versões do assembly que você está tentando carregar estiver no caminho de investigação, mas a versão específica que você está solicitando não estiver entre elas, as tentativas subsequentes de carregar essa versão falharão mesmo que a versão correta seja movida para o caminho de investigação.</span><span class="sxs-lookup"><span data-stu-id="ced3a-140">If one or more versions of the assembly that you are attempting to load is in the probing path, but the specific version you are requesting is not among them, subsequent attempts to load that version will fail even if the correct version is moved into the probing path.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ced3a-141">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ced3a-141">Example</span></span>  

 <span data-ttu-id="ced3a-142">O exemplo a seguir mostra como desabilitar o cache de falhas de associação de assembly que ocorrem porque o assembly não foi encontrado pela investigação.</span><span class="sxs-lookup"><span data-stu-id="ced3a-142">The following example shows how to disable the caching of assembly binding failures that occur because the assembly was not found by probing.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <disableCachingBindingFailures enabled="1" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ced3a-143">Confira também</span><span class="sxs-lookup"><span data-stu-id="ced3a-143">See also</span></span>

- [<span data-ttu-id="ced3a-144">Esquema de configurações do runtime</span><span class="sxs-lookup"><span data-stu-id="ced3a-144">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="ced3a-145">Esquema do arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="ced3a-145">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="ced3a-146">Como o runtime localiza assemblies</span><span class="sxs-lookup"><span data-stu-id="ced3a-146">How the Runtime Locates Assemblies</span></span>](../../../deployment/how-the-runtime-locates-assemblies.md)
