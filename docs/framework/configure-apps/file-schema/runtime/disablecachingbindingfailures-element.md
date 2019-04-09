---
title: <disableCachingBindingFailures> Elemento
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
ms.openlocfilehash: 4893adaf528f1a9ef8fc8eab8027406fd8520cc2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59159270"
---
# <a name="disablecachingbindingfailures-element"></a><span data-ttu-id="9bb93-102">\<disableCachingBindingFailures > elemento</span><span class="sxs-lookup"><span data-stu-id="9bb93-102">\<disableCachingBindingFailures> Element</span></span>
<span data-ttu-id="9bb93-103">Especifica se é necessário desabilitar o cache de falhas que ocorrem porque o assembly não foi encontrado por investigação de associação.</span><span class="sxs-lookup"><span data-stu-id="9bb93-103">Specifies whether to disable the caching of binding failures that occur because the assembly was not found by probing.</span></span>  
  
 <span data-ttu-id="9bb93-104">\<Configuração > elemento</span><span class="sxs-lookup"><span data-stu-id="9bb93-104">\<configuration> Element</span></span>  
<span data-ttu-id="9bb93-105">\<tempo de execução > elemento</span><span class="sxs-lookup"><span data-stu-id="9bb93-105">\<runtime> Element</span></span>  
<span data-ttu-id="9bb93-106">\<disableCachingBindingFailures></span><span class="sxs-lookup"><span data-stu-id="9bb93-106">\<disableCachingBindingFailures></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9bb93-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9bb93-107">Syntax</span></span>  
  
```xml  
<disableCachingBindingFailures enabled="0|1"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9bb93-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="9bb93-108">Attributes and Elements</span></span>  
 <span data-ttu-id="9bb93-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="9bb93-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9bb93-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="9bb93-110">Attributes</span></span>  
  
|<span data-ttu-id="9bb93-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="9bb93-111">Attribute</span></span>|<span data-ttu-id="9bb93-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="9bb93-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9bb93-113">habilitado</span><span class="sxs-lookup"><span data-stu-id="9bb93-113">enabled</span></span>|<span data-ttu-id="9bb93-114">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="9bb93-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="9bb93-115">Especifica se é necessário desabilitar o cache de falhas que ocorrem porque o assembly não foi encontrado por investigação de associação.</span><span class="sxs-lookup"><span data-stu-id="9bb93-115">Specifies whether to disable the caching of binding failures that occur because the assembly was not found by probing.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="9bb93-116">Atributo habilitado</span><span class="sxs-lookup"><span data-stu-id="9bb93-116">enabled Attribute</span></span>  
  
|<span data-ttu-id="9bb93-117">Valor</span><span class="sxs-lookup"><span data-stu-id="9bb93-117">Value</span></span>|<span data-ttu-id="9bb93-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="9bb93-118">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="9bb93-119">0</span><span class="sxs-lookup"><span data-stu-id="9bb93-119">0</span></span>|<span data-ttu-id="9bb93-120">Não desabilite o cache de falhas que ocorrem porque o assembly não foi encontrado por investigação de associação.</span><span class="sxs-lookup"><span data-stu-id="9bb93-120">Do not disable the caching of binding failures that occur because the assembly was not found by probing.</span></span> <span data-ttu-id="9bb93-121">Esse é o comportamento de associação padrão começando com o .NET Framework versão 2.0.</span><span class="sxs-lookup"><span data-stu-id="9bb93-121">This is the default binding behavior starting with the .NET Framework version 2.0.</span></span>|  
|<span data-ttu-id="9bb93-122">1</span><span class="sxs-lookup"><span data-stu-id="9bb93-122">1</span></span>|<span data-ttu-id="9bb93-123">Desabilite o cache de falhas que ocorrem porque o assembly não foi encontrado por investigação de associação.</span><span class="sxs-lookup"><span data-stu-id="9bb93-123">Disable the caching of binding failures that occur because the assembly was not found by probing.</span></span> <span data-ttu-id="9bb93-124">Essa configuração será revertido para o comportamento de associação do .NET Framework versão 1.1.</span><span class="sxs-lookup"><span data-stu-id="9bb93-124">This setting reverts to the binding behavior of the .NET Framework version 1.1.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9bb93-125">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="9bb93-125">Child Elements</span></span>  
 <span data-ttu-id="9bb93-126">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="9bb93-126">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9bb93-127">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="9bb93-127">Parent Elements</span></span>  
  
|<span data-ttu-id="9bb93-128">Elemento</span><span class="sxs-lookup"><span data-stu-id="9bb93-128">Element</span></span>|<span data-ttu-id="9bb93-129">Descrição</span><span class="sxs-lookup"><span data-stu-id="9bb93-129">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="9bb93-130">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9bb93-130">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="9bb93-131">Contém informações sobre associação do assembly e coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="9bb93-131">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9bb93-132">Comentários</span><span class="sxs-lookup"><span data-stu-id="9bb93-132">Remarks</span></span>  
 <span data-ttu-id="9bb93-133">Começando com o .NET Framework versão 2.0, o comportamento padrão de carregamento de assemblies é armazenar em cache todos os associação e falhas de carregamento.</span><span class="sxs-lookup"><span data-stu-id="9bb93-133">Starting with the .NET Framework version 2.0, the default behavior for loading assemblies is to cache all binding and loading failures.</span></span> <span data-ttu-id="9bb93-134">Ou seja, se uma tentativa de carregar um assembly falhar, as solicitações subsequentes para carregar o mesmo assembly falham imediatamente, sem qualquer tentativa de localizar o assembly.</span><span class="sxs-lookup"><span data-stu-id="9bb93-134">That is, if an attempt to load an assembly fails, subsequent requests to load the same assembly fail immediately, without any attempt to locate the assembly.</span></span> <span data-ttu-id="9bb93-135">Esse elemento desabilita o comportamento padrão para falhas que ocorrem porque o assembly não pôde ser encontrado no caminho de investigação de associação.</span><span class="sxs-lookup"><span data-stu-id="9bb93-135">This element disables that default behavior for binding failures that occur because the assembly could not be found in the probing path.</span></span> <span data-ttu-id="9bb93-136">Essas falhas lançar <xref:System.IO.FileNotFoundException>.</span><span class="sxs-lookup"><span data-stu-id="9bb93-136">These failures throw <xref:System.IO.FileNotFoundException>.</span></span>  
  
 <span data-ttu-id="9bb93-137">Alguns associação e falhas de carregamento não são afetados por este elemento e sempre são armazenados em cache.</span><span class="sxs-lookup"><span data-stu-id="9bb93-137">Some binding and loading failures are not affected by this element, and are always cached.</span></span> <span data-ttu-id="9bb93-138">Essas falhas ocorrem porque o assembly foi encontrado, mas não pôde ser carregado.</span><span class="sxs-lookup"><span data-stu-id="9bb93-138">These failures occur because the assembly was found but could not be loaded.</span></span> <span data-ttu-id="9bb93-139">Elas geram <xref:System.BadImageFormatException> ou <xref:System.IO.FileLoadException>.</span><span class="sxs-lookup"><span data-stu-id="9bb93-139">They throw <xref:System.BadImageFormatException> or <xref:System.IO.FileLoadException>.</span></span> <span data-ttu-id="9bb93-140">A lista a seguir inclui alguns exemplos de tais falhas.</span><span class="sxs-lookup"><span data-stu-id="9bb93-140">The following list includes some examples of such failures.</span></span>  
  
-   <span data-ttu-id="9bb93-141">Se você tentar carregar um arquivo não é um assembly válido, as tentativas subsequentes para carregar o assembly falhará mesmo se o arquivo inválido é substituído com o assembly correto.</span><span class="sxs-lookup"><span data-stu-id="9bb93-141">If you attempt to load a file is not a valid assembly, subsequent attempts to load the assembly will fail even if the bad file is replaced with the correct assembly.</span></span>  
  
-   <span data-ttu-id="9bb93-142">Se você tentar carregar um assembly que está bloqueado pelo sistema de arquivos, as tentativas subsequentes para carregar o assembly falhará mesmo depois que o assembly é liberado pelo sistema de arquivos.</span><span class="sxs-lookup"><span data-stu-id="9bb93-142">If you attempt to load an assembly that is locked by the file system, subsequent attempts to load the assembly will fail even after the assembly is released by the file system.</span></span>  
  
-   <span data-ttu-id="9bb93-143">Se uma ou mais versões do assembly que você está tentando carregar está no caminho de investigação, mas a versão específica que você está solicitando não está entre eles, tentativas subsequentes para carregar dessa versão falhará, mesmo se a versão correta é movida para o caminho de investigação.</span><span class="sxs-lookup"><span data-stu-id="9bb93-143">If one or more versions of the assembly that you are attempting to load is in the probing path, but the specific version you are requesting is not among them, subsequent attempts to load that version will fail even if the correct version is moved into the probing path.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9bb93-144">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9bb93-144">Example</span></span>  
 <span data-ttu-id="9bb93-145">O exemplo a seguir mostra como desabilitar o cache de falhas de associação de assembly que ocorrem porque o assembly não foi encontrado por sondagem.</span><span class="sxs-lookup"><span data-stu-id="9bb93-145">The following example shows how to disable the caching of assembly binding failures that occur because the assembly was not found by probing.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <disableCachingBindingFailures enabled="1" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="9bb93-146">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9bb93-146">See also</span></span>

- [<span data-ttu-id="9bb93-147">Esquema de configurações do tempo de execução</span><span class="sxs-lookup"><span data-stu-id="9bb93-147">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="9bb93-148">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="9bb93-148">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="9bb93-149">Como o tempo de execução localiza assemblies</span><span class="sxs-lookup"><span data-stu-id="9bb93-149">How the Runtime Locates Assemblies</span></span>](../../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
