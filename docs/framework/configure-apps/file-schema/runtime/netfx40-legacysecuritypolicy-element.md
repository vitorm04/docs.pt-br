---
title: Elemento < NetFx40_LegacySecurityPolicy >
ms.date: 03/30/2017
helpviewer_keywords:
- <NetFx40_LegacySecurityPolicy> element
- NetFx40_LegacySecurityPolicy element
ms.assetid: 07132b9c-4a72-4710-99d7-e702405e02d4
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0d0a3f7c0ae3a6c4a8c1518e7dd6bad9b2473374
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55264733"
---
# <a name="netfx40legacysecuritypolicy-element"></a><span data-ttu-id="3851e-102">\<NetFx40_LegacySecurityPolicy > elemento</span><span class="sxs-lookup"><span data-stu-id="3851e-102">\<NetFx40_LegacySecurityPolicy> Element</span></span>
<span data-ttu-id="3851e-103">Especifica se o tempo de execução usa a política de CAS (Segurança de Acesso do Código) herdada.</span><span class="sxs-lookup"><span data-stu-id="3851e-103">Specifies whether the runtime uses legacy code access security (CAS) policy.</span></span>  
  
 <span data-ttu-id="3851e-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="3851e-104">\<configuration></span></span>  
<span data-ttu-id="3851e-105">\<runtime></span><span class="sxs-lookup"><span data-stu-id="3851e-105">\<runtime></span></span>  
<span data-ttu-id="3851e-106"><NetFx40_LegacySecurityPolicy></span><span class="sxs-lookup"><span data-stu-id="3851e-106"><NetFx40_LegacySecurityPolicy></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3851e-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3851e-107">Syntax</span></span>  
  
```xml  
<NetFx40_LegacySecurityPolicy  
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3851e-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="3851e-108">Attributes and Elements</span></span>  
 <span data-ttu-id="3851e-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="3851e-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3851e-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="3851e-110">Attributes</span></span>  
  
|<span data-ttu-id="3851e-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="3851e-111">Attribute</span></span>|<span data-ttu-id="3851e-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="3851e-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="3851e-113">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="3851e-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="3851e-114">Especifica se o tempo de execução usa a política CAS herdada.</span><span class="sxs-lookup"><span data-stu-id="3851e-114">Specifies whether the runtime uses legacy CAS policy.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="3851e-115">Atributo habilitado</span><span class="sxs-lookup"><span data-stu-id="3851e-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="3851e-116">Valor</span><span class="sxs-lookup"><span data-stu-id="3851e-116">Value</span></span>|<span data-ttu-id="3851e-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="3851e-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="3851e-118">O tempo de execução não usa a política CAS herdada.</span><span class="sxs-lookup"><span data-stu-id="3851e-118">The runtime does not use legacy CAS policy.</span></span> <span data-ttu-id="3851e-119">Esse é o padrão.</span><span class="sxs-lookup"><span data-stu-id="3851e-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="3851e-120">O tempo de execução usa a política CAS herdada.</span><span class="sxs-lookup"><span data-stu-id="3851e-120">The runtime uses legacy CAS policy.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3851e-121">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="3851e-121">Child Elements</span></span>  
 <span data-ttu-id="3851e-122">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="3851e-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3851e-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="3851e-123">Parent Elements</span></span>  
  
|<span data-ttu-id="3851e-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="3851e-124">Element</span></span>|<span data-ttu-id="3851e-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="3851e-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="3851e-126">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3851e-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="3851e-127">Contém informações sobre opções de inicialização do tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="3851e-127">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3851e-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="3851e-128">Remarks</span></span>  
 <span data-ttu-id="3851e-129">No .NET Framework versão 3.5 e versões anteriores, a política de CAS está sempre em vigor.</span><span class="sxs-lookup"><span data-stu-id="3851e-129">In the .NET Framework version 3.5 and earlier versions, CAS policy is always in effect.</span></span> <span data-ttu-id="3851e-130">No [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], política de CAS deve estar habilitada.</span><span class="sxs-lookup"><span data-stu-id="3851e-130">In the [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], CAS policy must be enabled.</span></span>  
  
 <span data-ttu-id="3851e-131">Política de CAS é específico da versão.</span><span class="sxs-lookup"><span data-stu-id="3851e-131">CAS policy is version-specific.</span></span> <span data-ttu-id="3851e-132">As políticas personalizadas do CAS que existem nas versões anteriores do .NET Framework devem ser especificadas novamente no [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3851e-132">Custom CAS policies that exist in earlier versions of the .NET Framework must be respecified in the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)].</span></span>  
  
 <span data-ttu-id="3851e-133">Aplicando o `<NetFx40_LegacySecurityPolicy>` elemento para um [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] assembly não afeta [código transparente de segurança](../../../../../docs/framework/misc/security-transparent-code.md); as regras de transparência ainda se aplicam.</span><span class="sxs-lookup"><span data-stu-id="3851e-133">Applying the `<NetFx40_LegacySecurityPolicy>` element to a [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] assembly does not affect [security-transparent code](../../../../../docs/framework/misc/security-transparent-code.md); the transparency rules still apply.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="3851e-134">Aplicando o `<NetFx40_LegacySecurityPolicy>` elemento pode resultar em penalidades de desempenho significativos para os assemblies de imagem nativa criados pelo [gerador de imagem nativa (Ngen.exe)](../../../../../docs/framework/tools/ngen-exe-native-image-generator.md) que não estão instaladas no [cache de assembly global ](../../../../../docs/framework/app-domains/gac.md).</span><span class="sxs-lookup"><span data-stu-id="3851e-134">Applying the `<NetFx40_LegacySecurityPolicy>` element can result in significant performance penalties for native image assemblies created by the [Native Image Generator (Ngen.exe)](../../../../../docs/framework/tools/ngen-exe-native-image-generator.md) that are not installed in the [global assembly cache](../../../../../docs/framework/app-domains/gac.md).</span></span> <span data-ttu-id="3851e-135">A degradação do desempenho é causada pela incapacidade do tempo de execução para carregar os assemblies como imagens nativas, quando o atributo é aplicado, resultando em seus que está sendo carregado assemblies como just-in-time.</span><span class="sxs-lookup"><span data-stu-id="3851e-135">The performance degradation is caused by the inability of the runtime to load the assemblies as native images when the attribute is applied, resulting in their being loaded as just-in-time assemblies.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3851e-136">Se você especificar uma versão do .NET Framework de destino que é anterior a [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] nas configurações do projeto para o seu projeto do Visual Studio, política de CAS será habilitada, incluindo as políticas personalizadas de CAS especificado para essa versão.</span><span class="sxs-lookup"><span data-stu-id="3851e-136">If you specify a target .NET Framework version that is earlier than the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] in the project settings for your Visual Studio project, CAS policy will be enabled, including any custom CAS policies you specified for that version.</span></span> <span data-ttu-id="3851e-137">No entanto, você não poderá usar um novo [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] tipos e membros.</span><span class="sxs-lookup"><span data-stu-id="3851e-137">However, you will not be able to use new [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] types and members.</span></span> <span data-ttu-id="3851e-138">Você também pode especificar uma versão anterior do .NET Framework usando o [ \<supportedRuntime > elemento](../../../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md) no esquema de configurações de inicialização em seu [arquivo de configuração de aplicativo](../../../../../docs/framework/configure-apps/index.md).</span><span class="sxs-lookup"><span data-stu-id="3851e-138">You can also specify an earlier version of the .NET Framework by using the [\<supportedRuntime> element](../../../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md) in the startup settings schema in your [application configuration file](../../../../../docs/framework/configure-apps/index.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3851e-139">Sintaxe do arquivo de configuração diferencia maiusculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="3851e-139">Configuration file syntax is case-sensitive.</span></span> <span data-ttu-id="3851e-140">Você deve usar a sintaxe conforme fornecidos nas seções de sintaxe e exemplo.</span><span class="sxs-lookup"><span data-stu-id="3851e-140">You should use the syntax as provided in the Syntax and Example sections.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="3851e-141">Arquivo de Configuração</span><span class="sxs-lookup"><span data-stu-id="3851e-141">Configuration File</span></span>  
 <span data-ttu-id="3851e-142">Esse elemento pode ser usado apenas no arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="3851e-142">This element can be used only in the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3851e-143">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3851e-143">Example</span></span>  
 <span data-ttu-id="3851e-144">O exemplo a seguir mostra como habilitar a política CAS herdada para um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="3851e-144">The following example shows how to enable legacy CAS policy for an application.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <NetFx40_LegacySecurityPolicy enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="3851e-145">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3851e-145">See also</span></span>
- [<span data-ttu-id="3851e-146">Esquema de configurações do tempo de execução</span><span class="sxs-lookup"><span data-stu-id="3851e-146">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="3851e-147">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="3851e-147">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
