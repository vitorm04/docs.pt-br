---
title: '&lt;disableFusionUpdatesFromADManager&gt; elemento'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- disableFusionUpdatesFromADManager element
- <disableFusionUpdatesFromADManager> element
ms.assetid: 58d2866c-37bd-4ffa-abaf-ff35926a2939
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d4aa3343e7f3f60bbf6a57340d858c1ef12197bb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="ltdisablefusionupdatesfromadmanagergt-element"></a><span data-ttu-id="5dde1-102">&lt;disableFusionUpdatesFromADManager&gt; elemento</span><span class="sxs-lookup"><span data-stu-id="5dde1-102">&lt;disableFusionUpdatesFromADManager&gt; Element</span></span>
<span data-ttu-id="5dde1-103">Especifica se o comportamento padrão, que é permitir que o host de tempo de execução substitua as definições de configuração de um domínio de aplicativo, está desabilitado.</span><span class="sxs-lookup"><span data-stu-id="5dde1-103">Specifies whether the default behavior, which is to allow the runtime host to override configuration settings for an application domain, is disabled.</span></span>  
  
 <span data-ttu-id="5dde1-104">\<Configuração > elemento</span><span class="sxs-lookup"><span data-stu-id="5dde1-104">\<configuration> Element</span></span>  
<span data-ttu-id="5dde1-105">\<tempo de execução > elemento</span><span class="sxs-lookup"><span data-stu-id="5dde1-105">\<runtime> Element</span></span>  
<span data-ttu-id="5dde1-106">\<disableFusionUpdatesFromADManager ></span><span class="sxs-lookup"><span data-stu-id="5dde1-106">\<disableFusionUpdatesFromADManager></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5dde1-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5dde1-107">Syntax</span></span>  
  
```xml  
<disableFusionUpdatesFromADManager enabled="0|1"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5dde1-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="5dde1-108">Attributes and Elements</span></span>  
 <span data-ttu-id="5dde1-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="5dde1-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5dde1-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="5dde1-110">Attributes</span></span>  
  
|<span data-ttu-id="5dde1-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="5dde1-111">Attribute</span></span>|<span data-ttu-id="5dde1-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="5dde1-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5dde1-113">Habilitado</span><span class="sxs-lookup"><span data-stu-id="5dde1-113">enabled</span></span>|<span data-ttu-id="5dde1-114">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="5dde1-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="5dde1-115">Especifica se a capacidade de padrão para substituir as definições de fusão está desabilitada.</span><span class="sxs-lookup"><span data-stu-id="5dde1-115">Specifies whether the default ability to override Fusion settings is disabled.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="5dde1-116">Atributo habilitado</span><span class="sxs-lookup"><span data-stu-id="5dde1-116">enabled Attribute</span></span>  
  
|<span data-ttu-id="5dde1-117">Valor</span><span class="sxs-lookup"><span data-stu-id="5dde1-117">Value</span></span>|<span data-ttu-id="5dde1-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="5dde1-118">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="5dde1-119">0</span><span class="sxs-lookup"><span data-stu-id="5dde1-119">0</span></span>|<span data-ttu-id="5dde1-120">Não desabilite a habilidade de substituir configurações de fusão.</span><span class="sxs-lookup"><span data-stu-id="5dde1-120">Do not disable the ability to override Fusion settings.</span></span> <span data-ttu-id="5dde1-121">Esse é o comportamento padrão, começando com o [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5dde1-121">This is the default behavior, starting with the [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)].</span></span>|  
|<span data-ttu-id="5dde1-122">1</span><span class="sxs-lookup"><span data-stu-id="5dde1-122">1</span></span>|<span data-ttu-id="5dde1-123">Desabilite a capacidade de substituir configurações de fusão.</span><span class="sxs-lookup"><span data-stu-id="5dde1-123">Disable the ability to override Fusion settings.</span></span> <span data-ttu-id="5dde1-124">Isso será revertido para o comportamento de versões anteriores do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="5dde1-124">This reverts to the behavior of earlier versions of the .NET Framework.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5dde1-125">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="5dde1-125">Child Elements</span></span>  
 <span data-ttu-id="5dde1-126">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="5dde1-126">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5dde1-127">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="5dde1-127">Parent Elements</span></span>  
  
|<span data-ttu-id="5dde1-128">Elemento</span><span class="sxs-lookup"><span data-stu-id="5dde1-128">Element</span></span>|<span data-ttu-id="5dde1-129">Descrição</span><span class="sxs-lookup"><span data-stu-id="5dde1-129">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="5dde1-130">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="5dde1-130">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="5dde1-131">Contém informações sobre associação do assembly e coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="5dde1-131">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5dde1-132">Comentários</span><span class="sxs-lookup"><span data-stu-id="5dde1-132">Remarks</span></span>  
 <span data-ttu-id="5dde1-133">Começando com o [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], o comportamento padrão é permitir que o <xref:System.AppDomainManager> objeto substituir as definições de configuração usando o <xref:System.AppDomainSetup.ConfigurationFile%2A> propriedade ou o <xref:System.AppDomainSetup.SetConfigurationBytes%2A> método do <xref:System.AppDomainSetup> objeto que é passado para sua implementação do <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> método na sua subclasse de <xref:System.AppDomainManager>.</span><span class="sxs-lookup"><span data-stu-id="5dde1-133">Starting with the [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], the default behavior is to allow the <xref:System.AppDomainManager> object to override configuration settings by using the <xref:System.AppDomainSetup.ConfigurationFile%2A> property or the <xref:System.AppDomainSetup.SetConfigurationBytes%2A> method of the <xref:System.AppDomainSetup> object that is passed to your implementation of the <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> method, in your subclass of <xref:System.AppDomainManager>.</span></span> <span data-ttu-id="5dde1-134">Para o domínio de aplicativo padrão, as configurações que você alterar substituirão as configurações que foram especificadas pelo arquivo de configuração de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="5dde1-134">For the default application domain, the settings you change override the settings that were specified by the application configuration file.</span></span> <span data-ttu-id="5dde1-135">Para outros domínios de aplicativo, elas substituirão as configurações que foram passadas para o <xref:System.AppDomainManager.CreateDomain%2A?displayProperty=nameWithType> ou <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> método.</span><span class="sxs-lookup"><span data-stu-id="5dde1-135">For other application domains, they override the configuration settings that were passed to the <xref:System.AppDomainManager.CreateDomain%2A?displayProperty=nameWithType> or <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="5dde1-136">Você pode passar novas informações de configuração ou passar nulo (`Nothing` no Visual Basic) para eliminar as informações de configuração que foi passadas.</span><span class="sxs-lookup"><span data-stu-id="5dde1-136">You can either pass new configuration information, or pass null (`Nothing` in Visual Basic) to eliminate configuration information that was passed in.</span></span>  
  
 <span data-ttu-id="5dde1-137">Não passe informações de configuração para ambos os <xref:System.AppDomainSetup.ConfigurationFile%2A> propriedade e o <xref:System.AppDomainSetup.SetConfigurationBytes%2A> método.</span><span class="sxs-lookup"><span data-stu-id="5dde1-137">Do not pass configuration information to both the <xref:System.AppDomainSetup.ConfigurationFile%2A> property and the <xref:System.AppDomainSetup.SetConfigurationBytes%2A> method.</span></span> <span data-ttu-id="5dde1-138">Se você transmitir informações de configuração para ambas, as informações que você passa para o <xref:System.AppDomainSetup.ConfigurationFile%2A> propriedade será ignorada, pois o <xref:System.AppDomainSetup.SetConfigurationBytes%2A> método substitui as informações de configuração do arquivo de configuração de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="5dde1-138">If you pass configuration information to both, the information you pass to the <xref:System.AppDomainSetup.ConfigurationFile%2A> property is ignored, because the <xref:System.AppDomainSetup.SetConfigurationBytes%2A> method overrides configuration information from the application configuration file.</span></span> <span data-ttu-id="5dde1-139">Se você usar o <xref:System.AppDomainSetup.ConfigurationFile%2A> propriedade, você pode passar nulo (`Nothing` no Visual Basic) para o <xref:System.AppDomainSetup.SetConfigurationBytes%2A> método para eliminar qualquer bytes de configuração que foram especificados na chamada para o <xref:System.AppDomainManager.CreateDomain%2A?displayProperty=nameWithType> ou <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> método.</span><span class="sxs-lookup"><span data-stu-id="5dde1-139">If you use the <xref:System.AppDomainSetup.ConfigurationFile%2A> property, you can pass null (`Nothing` in Visual Basic) to the <xref:System.AppDomainSetup.SetConfigurationBytes%2A> method to eliminate any configuration bytes that were specified in the call to the <xref:System.AppDomainManager.CreateDomain%2A?displayProperty=nameWithType> or <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="5dde1-140">Além das informações de configuração, você pode alterar as configurações a seguir no <xref:System.AppDomainSetup> que é passado para a implementação do objeto de <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> método: <xref:System.AppDomainSetup.ApplicationBase%2A>, <xref:System.AppDomainSetup.ApplicationName%2A>, <xref:System.AppDomainSetup.CachePath%2A>, <xref:System.AppDomainSetup.DisallowApplicationBaseProbing%2A>, <xref:System.AppDomainSetup.DisallowBindingRedirects%2A> , <xref:System.AppDomainSetup.DisallowCodeDownload%2A>, <xref:System.AppDomainSetup.DisallowPublisherPolicy%2A>, <xref:System.AppDomainSetup.DynamicBase%2A>, <xref:System.AppDomainSetup.LoaderOptimization%2A>, <xref:System.AppDomainSetup.PrivateBinPath%2A>, <xref:System.AppDomainSetup.PrivateBinPathProbe%2A>, <xref:System.AppDomainSetup.ShadowCopyDirectories%2A>, e <xref:System.AppDomainSetup.ShadowCopyFiles%2A>.</span><span class="sxs-lookup"><span data-stu-id="5dde1-140">In addition to configuration information, you can change the following settings on the <xref:System.AppDomainSetup> object that is passed to your implementation of the <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> method: <xref:System.AppDomainSetup.ApplicationBase%2A>, <xref:System.AppDomainSetup.ApplicationName%2A>, <xref:System.AppDomainSetup.CachePath%2A>, <xref:System.AppDomainSetup.DisallowApplicationBaseProbing%2A>, <xref:System.AppDomainSetup.DisallowBindingRedirects%2A>, <xref:System.AppDomainSetup.DisallowCodeDownload%2A>, <xref:System.AppDomainSetup.DisallowPublisherPolicy%2A>, <xref:System.AppDomainSetup.DynamicBase%2A>, <xref:System.AppDomainSetup.LoaderOptimization%2A>, <xref:System.AppDomainSetup.PrivateBinPath%2A>, <xref:System.AppDomainSetup.PrivateBinPathProbe%2A>, <xref:System.AppDomainSetup.ShadowCopyDirectories%2A>, and <xref:System.AppDomainSetup.ShadowCopyFiles%2A>.</span></span>  
  
 <span data-ttu-id="5dde1-141">Como uma alternativa ao uso de `<disableFusionUpdatesFromADManager>` elemento, você pode desabilitar o comportamento padrão criando uma configuração de registro ou definindo uma variável de ambiente.</span><span class="sxs-lookup"><span data-stu-id="5dde1-141">As an alternative to using the `<disableFusionUpdatesFromADManager>` element, you can disable the default behavior by creating a registry setting or by setting an environment variable.</span></span> <span data-ttu-id="5dde1-142">No registro, crie um valor DWORD chamado `COMPLUS_disableFusionUpdatesFromADManager` em `HKCU\Software\Microsoft\.NETFramework` ou `HKLM\Software\Microsoft\.NETFramework`e defina o valor como 1.</span><span class="sxs-lookup"><span data-stu-id="5dde1-142">In the registry, create a DWORD value named `COMPLUS_disableFusionUpdatesFromADManager` under `HKCU\Software\Microsoft\.NETFramework` or `HKLM\Software\Microsoft\.NETFramework`, and set the value to 1.</span></span> <span data-ttu-id="5dde1-143">Na linha de comando, defina a variável de ambiente `COMPLUS_disableFusionUpdatesFromADManager` como 1.</span><span class="sxs-lookup"><span data-stu-id="5dde1-143">At the command line, set the environment variable `COMPLUS_disableFusionUpdatesFromADManager` to 1.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5dde1-144">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5dde1-144">Example</span></span>  
 <span data-ttu-id="5dde1-145">O exemplo a seguir mostra como desabilitar a capacidade de substituir configurações de fusão usando o `<disableFusionUpdatesFromADManager>` elemento.</span><span class="sxs-lookup"><span data-stu-id="5dde1-145">The following example shows how to disable the ability to override Fusion settings by using the `<disableFusionUpdatesFromADManager>` element.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <disableFusionUpdatesFromADManager enabled="1" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="5dde1-146">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5dde1-146">See Also</span></span>  
 [<span data-ttu-id="5dde1-147">Esquema de configurações do tempo de execução</span><span class="sxs-lookup"><span data-stu-id="5dde1-147">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="5dde1-148">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="5dde1-148">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="5dde1-149">Como o tempo de execução localiza assemblies</span><span class="sxs-lookup"><span data-stu-id="5dde1-149">How the Runtime Locates Assemblies</span></span>](../../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
