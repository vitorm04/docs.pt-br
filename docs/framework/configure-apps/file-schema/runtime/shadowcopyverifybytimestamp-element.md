---
title: '&lt;shadowCopyVerifyByTimestamp&gt; elemento'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- <shadowCopyTimeStampVerification> element
- shadowCopyTimeStampVerification element
ms.assetid: 2f1648e5-997b-435e-a4f9-d236c574c66c
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bae98c91c8a9b68ec7c21b142bc9f004c7bc1394
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ltshadowcopyverifybytimestampgt-element"></a><span data-ttu-id="41094-102">&lt;shadowCopyVerifyByTimestamp&gt; elemento</span><span class="sxs-lookup"><span data-stu-id="41094-102">&lt;shadowCopyVerifyByTimestamp&gt; Element</span></span>
<span data-ttu-id="41094-103">Especifica se a cópia de sombra usa o comportamento de inicialização padrão introduzido no [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] ou reverte para o comportamento de inicialização de versões anteriores do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="41094-103">Specifies whether shadow copying uses the default startup behavior introduced in the [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], or reverts to the startup behavior of earlier versions of the .NET Framework.</span></span>  
  
 <span data-ttu-id="41094-104">\<Configuração > elemento</span><span class="sxs-lookup"><span data-stu-id="41094-104">\<configuration> Element</span></span>  
<span data-ttu-id="41094-105">\<tempo de execução > elemento</span><span class="sxs-lookup"><span data-stu-id="41094-105">\<runtime> Element</span></span>  
<span data-ttu-id="41094-106">\<shadowCopyVerifyByTimestamp > elemento</span><span class="sxs-lookup"><span data-stu-id="41094-106">\<shadowCopyVerifyByTimestamp> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="41094-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="41094-107">Syntax</span></span>  
  
```xml  
<shadowCopyVerifyByTimestamp enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="41094-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="41094-108">Attributes and Elements</span></span>  
 <span data-ttu-id="41094-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="41094-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="41094-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="41094-110">Attributes</span></span>  
  
|<span data-ttu-id="41094-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="41094-111">Attribute</span></span>|<span data-ttu-id="41094-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="41094-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="41094-113">Habilitado</span><span class="sxs-lookup"><span data-stu-id="41094-113">enabled</span></span>|<span data-ttu-id="41094-114">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="41094-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="41094-115">Especifica se os domínios de aplicativos que usam a cópia de sombra comparam os carimbos de hora do assembly ao iniciar, para determinar se um assembly foi atualizado antes do conjunto de cópias de sombra.</span><span class="sxs-lookup"><span data-stu-id="41094-115">Specifies whether application domains that use shadow copying compare assembly time stamps when starting up, to determine whether an assembly has been updated before shadow copying the assembly.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="41094-116">Atributo habilitado</span><span class="sxs-lookup"><span data-stu-id="41094-116">enabled Attribute</span></span>  
  
|<span data-ttu-id="41094-117">Valor</span><span class="sxs-lookup"><span data-stu-id="41094-117">Value</span></span>|<span data-ttu-id="41094-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="41094-118">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="41094-119">true</span><span class="sxs-lookup"><span data-stu-id="41094-119">true</span></span>|<span data-ttu-id="41094-120">Na inicialização, copia apenas os assemblies que foram atualizados desde a última foram copiados para o diretório de cópia de sombra.</span><span class="sxs-lookup"><span data-stu-id="41094-120">At startup, copies only assemblies that have been updated since they were last copied to the shadow copy directory.</span></span> <span data-ttu-id="41094-121">Esse é o padrão para o [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="41094-121">This is the default for the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)].</span></span>|  
|<span data-ttu-id="41094-122">false</span><span class="sxs-lookup"><span data-stu-id="41094-122">false</span></span>|<span data-ttu-id="41094-123">Reverte para o comportamento de inicialização de versões anteriores do .NET Framework, que era copiar todos os arquivos na inicialização.</span><span class="sxs-lookup"><span data-stu-id="41094-123">Reverts to the startup behavior of previous versions of the .NET Framework, which was to copy all files at startup.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="41094-124">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="41094-124">Child Elements</span></span>  
 <span data-ttu-id="41094-125">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="41094-125">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="41094-126">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="41094-126">Parent Elements</span></span>  
  
|<span data-ttu-id="41094-127">Elemento</span><span class="sxs-lookup"><span data-stu-id="41094-127">Element</span></span>|<span data-ttu-id="41094-128">Descrição</span><span class="sxs-lookup"><span data-stu-id="41094-128">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="41094-129">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="41094-129">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="41094-130">Contém informações sobre associação do assembly e coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="41094-130">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="41094-131">Comentários</span><span class="sxs-lookup"><span data-stu-id="41094-131">Remarks</span></span>  
 <span data-ttu-id="41094-132">Começando com o [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], os assemblies são copiados somente se seus carimbos de data / hora indicar que foram alteradas desde a última foram copiados para o diretório de cópia de sombra de sombra.</span><span class="sxs-lookup"><span data-stu-id="41094-132">Starting with the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], assemblies are shadow copied only if their time stamps indicate that they have changed since they were last copied to the shadow copy directory.</span></span> <span data-ttu-id="41094-133">Isso melhora o tempo de inicialização para muitos aplicativos que usam a cópia de sombra, conforme descrito em [cópia de sombra de Assemblies](../../../../../docs/framework/app-domains/shadow-copy-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="41094-133">This improves startup times for many applications that use shadow copying, as described in [Shadow Copying Assemblies](../../../../../docs/framework/app-domains/shadow-copy-assemblies.md).</span></span> <span data-ttu-id="41094-134">Aplicativos que têm uma porcentagem alta e a frequência de atualizações do assembly não podem se beneficiar dessa alteração no comportamento.</span><span class="sxs-lookup"><span data-stu-id="41094-134">Applications that have a high percentage and frequency of assembly updates might not benefit from this change in behavior.</span></span> <span data-ttu-id="41094-135">Nesse caso, você pode usar esse elemento para restaurar o comportamento de versões anteriores do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="41094-135">In that case, you can use this element to restore the behavior of previous versions of the .NET Framework.</span></span>  
  
## <a name="example"></a><span data-ttu-id="41094-136">Exemplo</span><span class="sxs-lookup"><span data-stu-id="41094-136">Example</span></span>  
 <span data-ttu-id="41094-137">O exemplo a seguir mostra como desabilitar o comportamento de inicialização padrão de cópia de sombra no [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)]e reverter para o comportamento de inicialização de versões anteriores do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="41094-137">The following example shows how to disable the default startup behavior of shadow copying in the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], and revert to the startup behavior of previous versions of the .NET Framework.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <shadowCopyVerifyByTimestamp enabled="false" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="41094-138">Consulte também</span><span class="sxs-lookup"><span data-stu-id="41094-138">See Also</span></span>  
 [<span data-ttu-id="41094-139">Esquema de configurações do tempo de execução</span><span class="sxs-lookup"><span data-stu-id="41094-139">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="41094-140">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="41094-140">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="41094-141">Cópias de sombra de assemblies</span><span class="sxs-lookup"><span data-stu-id="41094-141">Shadow Copying Assemblies</span></span>](../../../../../docs/framework/app-domains/shadow-copy-assemblies.md)
