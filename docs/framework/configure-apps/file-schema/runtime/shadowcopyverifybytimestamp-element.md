---
title: '&lt;shadowCopyVerifyByTimestamp&gt; Element'
ms.date: 03/30/2017
helpviewer_keywords:
- <shadowCopyTimeStampVerification> element
- shadowCopyTimeStampVerification element
ms.assetid: 2f1648e5-997b-435e-a4f9-d236c574c66c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9a37e41aa653fb3cd5990b75f3c5467a88660113
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54622254"
---
# <a name="ltshadowcopyverifybytimestampgt-element"></a><span data-ttu-id="b5cdf-102">&lt;shadowCopyVerifyByTimestamp&gt; Element</span><span class="sxs-lookup"><span data-stu-id="b5cdf-102">&lt;shadowCopyVerifyByTimestamp&gt; Element</span></span>
<span data-ttu-id="b5cdf-103">Especifica se a cópia de sombra usa o comportamento de inicialização padrão introduzido no [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] ou reverte para o comportamento de inicialização de versões anteriores do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b5cdf-103">Specifies whether shadow copying uses the default startup behavior introduced in the [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], or reverts to the startup behavior of earlier versions of the .NET Framework.</span></span>  
  
 <span data-ttu-id="b5cdf-104">\<Configuração > elemento</span><span class="sxs-lookup"><span data-stu-id="b5cdf-104">\<configuration> Element</span></span>  
<span data-ttu-id="b5cdf-105">\<tempo de execução > elemento</span><span class="sxs-lookup"><span data-stu-id="b5cdf-105">\<runtime> Element</span></span>  
<span data-ttu-id="b5cdf-106">\<elemento shadowCopyVerifyByTimestamp > elemento</span><span class="sxs-lookup"><span data-stu-id="b5cdf-106">\<shadowCopyVerifyByTimestamp> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b5cdf-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b5cdf-107">Syntax</span></span>  
  
```xml  
<shadowCopyVerifyByTimestamp enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b5cdf-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="b5cdf-108">Attributes and Elements</span></span>  
 <span data-ttu-id="b5cdf-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="b5cdf-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b5cdf-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="b5cdf-110">Attributes</span></span>  
  
|<span data-ttu-id="b5cdf-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="b5cdf-111">Attribute</span></span>|<span data-ttu-id="b5cdf-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="b5cdf-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b5cdf-113">habilitado</span><span class="sxs-lookup"><span data-stu-id="b5cdf-113">enabled</span></span>|<span data-ttu-id="b5cdf-114">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="b5cdf-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="b5cdf-115">Especifica se os domínios de aplicativos que usam a cópia de sombra comparam carimbos de data / hora do assembly ao iniciar, para determinar se um assembly foi atualizado antes do conjunto de cópias de sombra.</span><span class="sxs-lookup"><span data-stu-id="b5cdf-115">Specifies whether application domains that use shadow copying compare assembly time stamps when starting up, to determine whether an assembly has been updated before shadow copying the assembly.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="b5cdf-116">Atributo habilitado</span><span class="sxs-lookup"><span data-stu-id="b5cdf-116">enabled Attribute</span></span>  
  
|<span data-ttu-id="b5cdf-117">Valor</span><span class="sxs-lookup"><span data-stu-id="b5cdf-117">Value</span></span>|<span data-ttu-id="b5cdf-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="b5cdf-118">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="b5cdf-119">true</span><span class="sxs-lookup"><span data-stu-id="b5cdf-119">true</span></span>|<span data-ttu-id="b5cdf-120">Na inicialização, copia apenas os assemblies tenham sido atualizados desde a última foram copiados para o diretório de cópia de sombra.</span><span class="sxs-lookup"><span data-stu-id="b5cdf-120">At startup, copies only assemblies that have been updated since they were last copied to the shadow copy directory.</span></span> <span data-ttu-id="b5cdf-121">Esse é o padrão para o [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b5cdf-121">This is the default for the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)].</span></span>|  
|<span data-ttu-id="b5cdf-122">false</span><span class="sxs-lookup"><span data-stu-id="b5cdf-122">false</span></span>|<span data-ttu-id="b5cdf-123">Reverte para o comportamento de inicialização de versões anteriores do .NET Framework, que foi copiar todos os arquivos na inicialização.</span><span class="sxs-lookup"><span data-stu-id="b5cdf-123">Reverts to the startup behavior of previous versions of the .NET Framework, which was to copy all files at startup.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b5cdf-124">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="b5cdf-124">Child Elements</span></span>  
 <span data-ttu-id="b5cdf-125">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="b5cdf-125">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b5cdf-126">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="b5cdf-126">Parent Elements</span></span>  
  
|<span data-ttu-id="b5cdf-127">Elemento</span><span class="sxs-lookup"><span data-stu-id="b5cdf-127">Element</span></span>|<span data-ttu-id="b5cdf-128">Descrição</span><span class="sxs-lookup"><span data-stu-id="b5cdf-128">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="b5cdf-129">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b5cdf-129">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="b5cdf-130">Contém informações sobre associação do assembly e coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="b5cdf-130">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b5cdf-131">Comentários</span><span class="sxs-lookup"><span data-stu-id="b5cdf-131">Remarks</span></span>  
 <span data-ttu-id="b5cdf-132">Começando com o [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], assemblies são apenas se seus carimbos de data / hora que indicam que eles foram alterados desde que eles pela última vez foram copiados para o diretório de cópia de sombra de cópia de sombra.</span><span class="sxs-lookup"><span data-stu-id="b5cdf-132">Starting with the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], assemblies are shadow copied only if their time stamps indicate that they have changed since they were last copied to the shadow copy directory.</span></span> <span data-ttu-id="b5cdf-133">Isso melhora os tempos de inicialização para muitos aplicativos que usam a cópia de sombra, conforme descrito em [cópias de sombra de Assemblies](../../../../../docs/framework/app-domains/shadow-copy-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="b5cdf-133">This improves startup times for many applications that use shadow copying, as described in [Shadow Copying Assemblies](../../../../../docs/framework/app-domains/shadow-copy-assemblies.md).</span></span> <span data-ttu-id="b5cdf-134">Aplicativos que têm um alto percentual e uma frequência de atualizações do assembly não podem se beneficiar dessa mudança no comportamento.</span><span class="sxs-lookup"><span data-stu-id="b5cdf-134">Applications that have a high percentage and frequency of assembly updates might not benefit from this change in behavior.</span></span> <span data-ttu-id="b5cdf-135">Nesse caso, você pode usar esse elemento para restaurar o comportamento de versões anteriores do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b5cdf-135">In that case, you can use this element to restore the behavior of previous versions of the .NET Framework.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b5cdf-136">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b5cdf-136">Example</span></span>  
 <span data-ttu-id="b5cdf-137">O exemplo a seguir mostra como desabilitar o comportamento de inicialização padrão de cópia de sombra no [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)]e reverter para o comportamento de inicialização de versões anteriores do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b5cdf-137">The following example shows how to disable the default startup behavior of shadow copying in the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], and revert to the startup behavior of previous versions of the .NET Framework.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <shadowCopyVerifyByTimestamp enabled="false" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="b5cdf-138">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b5cdf-138">See also</span></span>
- [<span data-ttu-id="b5cdf-139">Esquema de configurações do tempo de execução</span><span class="sxs-lookup"><span data-stu-id="b5cdf-139">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="b5cdf-140">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="b5cdf-140">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="b5cdf-141">Cópias de sombra de assemblies</span><span class="sxs-lookup"><span data-stu-id="b5cdf-141">Shadow Copying Assemblies</span></span>](../../../../../docs/framework/app-domains/shadow-copy-assemblies.md)
