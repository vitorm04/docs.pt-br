---
title: Elemento <shadowCopyVerifyByTimestamp>
ms.date: 03/30/2017
helpviewer_keywords:
- <shadowCopyTimeStampVerification> element
- shadowCopyTimeStampVerification element
ms.assetid: 2f1648e5-997b-435e-a4f9-d236c574c66c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6f3ea57364832553d16c7e34fc887b1c9f821602
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663445"
---
# <a name="shadowcopyverifybytimestamp-element"></a><span data-ttu-id="d8af0-102">\<Elemento shadowCopyVerifyByTimestamp></span><span class="sxs-lookup"><span data-stu-id="d8af0-102">\<shadowCopyVerifyByTimestamp> Element</span></span>
<span data-ttu-id="d8af0-103">Especifica se a cópia de sombra usa o comportamento de inicialização padrão introduzido no .NET Framework 4 ou reverte para o comportamento de inicialização de versões anteriores do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d8af0-103">Specifies whether shadow copying uses the default startup behavior introduced in the .NET Framework 4, or reverts to the startup behavior of earlier versions of the .NET Framework.</span></span>  
  
 <span data-ttu-id="d8af0-104">\<Elemento de > de configuração</span><span class="sxs-lookup"><span data-stu-id="d8af0-104">\<configuration> Element</span></span>  
<span data-ttu-id="d8af0-105">\<Elemento de > de tempo de execução</span><span class="sxs-lookup"><span data-stu-id="d8af0-105">\<runtime> Element</span></span>  
<span data-ttu-id="d8af0-106">\<Elemento shadowCopyVerifyByTimestamp></span><span class="sxs-lookup"><span data-stu-id="d8af0-106">\<shadowCopyVerifyByTimestamp> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d8af0-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d8af0-107">Syntax</span></span>  
  
```xml  
<shadowCopyVerifyByTimestamp enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d8af0-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="d8af0-108">Attributes and Elements</span></span>  
 <span data-ttu-id="d8af0-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="d8af0-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d8af0-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="d8af0-110">Attributes</span></span>  
  
|<span data-ttu-id="d8af0-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="d8af0-111">Attribute</span></span>|<span data-ttu-id="d8af0-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="d8af0-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d8af0-113">habilitado</span><span class="sxs-lookup"><span data-stu-id="d8af0-113">enabled</span></span>|<span data-ttu-id="d8af0-114">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="d8af0-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="d8af0-115">Especifica se os domínios de aplicativo que usam a cópia de sombra comparam carimbos de data/hora ao iniciar, para determinar se um assembly foi atualizado antes de copiar a sombra do assembly.</span><span class="sxs-lookup"><span data-stu-id="d8af0-115">Specifies whether application domains that use shadow copying compare assembly time stamps when starting up, to determine whether an assembly has been updated before shadow copying the assembly.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="d8af0-116">Atributo habilitado</span><span class="sxs-lookup"><span data-stu-id="d8af0-116">enabled Attribute</span></span>  
  
|<span data-ttu-id="d8af0-117">Valor</span><span class="sxs-lookup"><span data-stu-id="d8af0-117">Value</span></span>|<span data-ttu-id="d8af0-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="d8af0-118">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="d8af0-119">true</span><span class="sxs-lookup"><span data-stu-id="d8af0-119">true</span></span>|<span data-ttu-id="d8af0-120">Na inicialização, o copia somente os assemblies que foram atualizados desde a última vez que foram copiados para o diretório de cópia de sombra.</span><span class="sxs-lookup"><span data-stu-id="d8af0-120">At startup, copies only assemblies that have been updated since they were last copied to the shadow copy directory.</span></span> <span data-ttu-id="d8af0-121">Esse é o padrão para o .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="d8af0-121">This is the default for the .NET Framework 4.</span></span>|  
|<span data-ttu-id="d8af0-122">false</span><span class="sxs-lookup"><span data-stu-id="d8af0-122">false</span></span>|<span data-ttu-id="d8af0-123">Reverte para o comportamento de inicialização de versões anteriores do .NET Framework, que era copiar todos os arquivos na inicialização.</span><span class="sxs-lookup"><span data-stu-id="d8af0-123">Reverts to the startup behavior of previous versions of the .NET Framework, which was to copy all files at startup.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d8af0-124">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="d8af0-124">Child Elements</span></span>  
 <span data-ttu-id="d8af0-125">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="d8af0-125">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d8af0-126">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="d8af0-126">Parent Elements</span></span>  
  
|<span data-ttu-id="d8af0-127">Elemento</span><span class="sxs-lookup"><span data-stu-id="d8af0-127">Element</span></span>|<span data-ttu-id="d8af0-128">Descrição</span><span class="sxs-lookup"><span data-stu-id="d8af0-128">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="d8af0-129">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d8af0-129">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="d8af0-130">Contém informações sobre associação do assembly e coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="d8af0-130">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d8af0-131">Comentários</span><span class="sxs-lookup"><span data-stu-id="d8af0-131">Remarks</span></span>  
 <span data-ttu-id="d8af0-132">A partir do .NET Framework 4, os assemblies serão copiados por sombra somente se os carimbos de data/hora indicarem que foram alterados desde que foram copiados pela última vez para o diretório de cópia de sombra.</span><span class="sxs-lookup"><span data-stu-id="d8af0-132">Starting with the .NET Framework 4, assemblies are shadow copied only if their time stamps indicate that they have changed since they were last copied to the shadow copy directory.</span></span> <span data-ttu-id="d8af0-133">Isso melhora os tempos de inicialização para muitos aplicativos que usam cópia de sombra, conforme descrito em [assemblies de cópia de sombra](../../../app-domains/shadow-copy-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="d8af0-133">This improves startup times for many applications that use shadow copying, as described in [Shadow Copying Assemblies](../../../app-domains/shadow-copy-assemblies.md).</span></span> <span data-ttu-id="d8af0-134">Aplicativos que têm uma alta porcentagem e frequência de atualizações de assembly podem não se beneficiar dessa alteração no comportamento.</span><span class="sxs-lookup"><span data-stu-id="d8af0-134">Applications that have a high percentage and frequency of assembly updates might not benefit from this change in behavior.</span></span> <span data-ttu-id="d8af0-135">Nesse caso, você pode usar esse elemento para restaurar o comportamento de versões anteriores do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d8af0-135">In that case, you can use this element to restore the behavior of previous versions of the .NET Framework.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d8af0-136">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d8af0-136">Example</span></span>  
 <span data-ttu-id="d8af0-137">O exemplo a seguir mostra como desabilitar o comportamento de inicialização padrão da cópia de sombra no .NET Framework 4 e reverter para o comportamento de inicialização de versões anteriores do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d8af0-137">The following example shows how to disable the default startup behavior of shadow copying in the .NET Framework 4, and revert to the startup behavior of previous versions of the .NET Framework.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <shadowCopyVerifyByTimestamp enabled="false" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d8af0-138">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d8af0-138">See also</span></span>

- [<span data-ttu-id="d8af0-139">Esquema de configurações do tempo de execução</span><span class="sxs-lookup"><span data-stu-id="d8af0-139">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="d8af0-140">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="d8af0-140">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="d8af0-141">Cópias de sombra de assemblies</span><span class="sxs-lookup"><span data-stu-id="d8af0-141">Shadow Copying Assemblies</span></span>](../../../app-domains/shadow-copy-assemblies.md)
