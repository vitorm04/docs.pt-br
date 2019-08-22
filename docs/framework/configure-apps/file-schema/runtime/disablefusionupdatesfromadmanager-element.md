---
title: Elemento <disableFusionUpdatesFromADManager>
ms.date: 03/30/2017
helpviewer_keywords:
- disableFusionUpdatesFromADManager element
- <disableFusionUpdatesFromADManager> element
ms.assetid: 58d2866c-37bd-4ffa-abaf-ff35926a2939
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a1923e70143ea2a158447eccdb35d347fe4f51ea
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663777"
---
# <a name="disablefusionupdatesfromadmanager-element"></a><span data-ttu-id="1226b-102">\<Elemento de > disableFusionUpdatesFromADManager</span><span class="sxs-lookup"><span data-stu-id="1226b-102">\<disableFusionUpdatesFromADManager> Element</span></span>
<span data-ttu-id="1226b-103">Especifica se o comportamento padrão, que é permitir que o host de tempo de execução substitua as definições de configuração de um domínio de aplicativo, está desabilitado.</span><span class="sxs-lookup"><span data-stu-id="1226b-103">Specifies whether the default behavior, which is to allow the runtime host to override configuration settings for an application domain, is disabled.</span></span>  
  
 <span data-ttu-id="1226b-104">\<Elemento de > de configuração</span><span class="sxs-lookup"><span data-stu-id="1226b-104">\<configuration> Element</span></span>  
<span data-ttu-id="1226b-105">\<Elemento de > de tempo de execução</span><span class="sxs-lookup"><span data-stu-id="1226b-105">\<runtime> Element</span></span>  
<span data-ttu-id="1226b-106">\<disableFusionUpdatesFromADManager></span><span class="sxs-lookup"><span data-stu-id="1226b-106">\<disableFusionUpdatesFromADManager></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1226b-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1226b-107">Syntax</span></span>  
  
```xml  
<disableFusionUpdatesFromADManager enabled="0|1"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1226b-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="1226b-108">Attributes and Elements</span></span>  
 <span data-ttu-id="1226b-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="1226b-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1226b-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="1226b-110">Attributes</span></span>  
  
|<span data-ttu-id="1226b-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="1226b-111">Attribute</span></span>|<span data-ttu-id="1226b-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="1226b-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1226b-113">habilitado</span><span class="sxs-lookup"><span data-stu-id="1226b-113">enabled</span></span>|<span data-ttu-id="1226b-114">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="1226b-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="1226b-115">Especifica se a capacidade padrão de substituir as configurações de fusão está desabilitada.</span><span class="sxs-lookup"><span data-stu-id="1226b-115">Specifies whether the default ability to override Fusion settings is disabled.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="1226b-116">Atributo habilitado</span><span class="sxs-lookup"><span data-stu-id="1226b-116">enabled Attribute</span></span>  
  
|<span data-ttu-id="1226b-117">Valor</span><span class="sxs-lookup"><span data-stu-id="1226b-117">Value</span></span>|<span data-ttu-id="1226b-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="1226b-118">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="1226b-119">0</span><span class="sxs-lookup"><span data-stu-id="1226b-119">0</span></span>|<span data-ttu-id="1226b-120">Não desabilite a capacidade de substituir as configurações de fusão.</span><span class="sxs-lookup"><span data-stu-id="1226b-120">Do not disable the ability to override Fusion settings.</span></span> <span data-ttu-id="1226b-121">Esse é o comportamento padrão, começando com o .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="1226b-121">This is the default behavior, starting with the .NET Framework 4.</span></span>|  
|<span data-ttu-id="1226b-122">1</span><span class="sxs-lookup"><span data-stu-id="1226b-122">1</span></span>|<span data-ttu-id="1226b-123">Desabilite a capacidade de substituir as configurações de fusão.</span><span class="sxs-lookup"><span data-stu-id="1226b-123">Disable the ability to override Fusion settings.</span></span> <span data-ttu-id="1226b-124">Isso reverte para o comportamento de versões anteriores do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="1226b-124">This reverts to the behavior of earlier versions of the .NET Framework.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1226b-125">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="1226b-125">Child Elements</span></span>  
 <span data-ttu-id="1226b-126">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="1226b-126">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1226b-127">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="1226b-127">Parent Elements</span></span>  
  
|<span data-ttu-id="1226b-128">Elemento</span><span class="sxs-lookup"><span data-stu-id="1226b-128">Element</span></span>|<span data-ttu-id="1226b-129">Descrição</span><span class="sxs-lookup"><span data-stu-id="1226b-129">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="1226b-130">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="1226b-130">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="1226b-131">Contém informações sobre associação do assembly e coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="1226b-131">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1226b-132">Comentários</span><span class="sxs-lookup"><span data-stu-id="1226b-132">Remarks</span></span>  
 <span data-ttu-id="1226b-133">Começando com o .NET Framework 4, o comportamento padrão é permitir que o <xref:System.AppDomainManager> objeto substitua as definições de configuração usando a <xref:System.AppDomainSetup.ConfigurationFile%2A> propriedade <xref:System.AppDomainSetup> ou o <xref:System.AppDomainSetup.SetConfigurationBytes%2A> método do objeto que é passado para sua implementação do método, em sua subclasse de <xref:System.AppDomainManager>. <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="1226b-133">Starting with the .NET Framework 4, the default behavior is to allow the <xref:System.AppDomainManager> object to override configuration settings by using the <xref:System.AppDomainSetup.ConfigurationFile%2A> property or the <xref:System.AppDomainSetup.SetConfigurationBytes%2A> method of the <xref:System.AppDomainSetup> object that is passed to your implementation of the <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> method, in your subclass of <xref:System.AppDomainManager>.</span></span> <span data-ttu-id="1226b-134">Para o domínio de aplicativo padrão, as configurações alteradas substituem as configurações que foram especificadas pelo arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1226b-134">For the default application domain, the settings you change override the settings that were specified by the application configuration file.</span></span> <span data-ttu-id="1226b-135">Para outros domínios de aplicativo, eles substituem as definições de configuração que foram <xref:System.AppDomainManager.CreateDomain%2A?displayProperty=nameWithType> passadas para o método ou <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="1226b-135">For other application domains, they override the configuration settings that were passed to the <xref:System.AppDomainManager.CreateDomain%2A?displayProperty=nameWithType> or <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="1226b-136">Você pode passar novas informações de configuração ou passar NULL (`Nothing` em Visual Basic) para eliminar informações de configuração que foram passadas.</span><span class="sxs-lookup"><span data-stu-id="1226b-136">You can either pass new configuration information, or pass null (`Nothing` in Visual Basic) to eliminate configuration information that was passed in.</span></span>  
  
 <span data-ttu-id="1226b-137">Não transmita informações de configuração para a <xref:System.AppDomainSetup.ConfigurationFile%2A> Propriedade e o <xref:System.AppDomainSetup.SetConfigurationBytes%2A> método.</span><span class="sxs-lookup"><span data-stu-id="1226b-137">Do not pass configuration information to both the <xref:System.AppDomainSetup.ConfigurationFile%2A> property and the <xref:System.AppDomainSetup.SetConfigurationBytes%2A> method.</span></span> <span data-ttu-id="1226b-138">Se você passar informações de configuração para ambos, as informações passadas para <xref:System.AppDomainSetup.ConfigurationFile%2A> a propriedade serão ignoradas, <xref:System.AppDomainSetup.SetConfigurationBytes%2A> pois o método substitui as informações de configuração do arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1226b-138">If you pass configuration information to both, the information you pass to the <xref:System.AppDomainSetup.ConfigurationFile%2A> property is ignored, because the <xref:System.AppDomainSetup.SetConfigurationBytes%2A> method overrides configuration information from the application configuration file.</span></span> <span data-ttu-id="1226b-139">Se você usar a <xref:System.AppDomainSetup.ConfigurationFile%2A> Propriedade, poderá passar NULL (`Nothing` em Visual Basic) para o <xref:System.AppDomainSetup.SetConfigurationBytes%2A> método para eliminar quaisquer bytes de configuração que foram especificados na chamada para o <xref:System.AppDomainManager.CreateDomain%2A?displayProperty=nameWithType> método ou <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="1226b-139">If you use the <xref:System.AppDomainSetup.ConfigurationFile%2A> property, you can pass null (`Nothing` in Visual Basic) to the <xref:System.AppDomainSetup.SetConfigurationBytes%2A> method to eliminate any configuration bytes that were specified in the call to the <xref:System.AppDomainManager.CreateDomain%2A?displayProperty=nameWithType> or <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="1226b-140">Além das informações de configuração, você pode alterar as seguintes <xref:System.AppDomainSetup> configurações no objeto que é passado para a implementação <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> do <xref:System.AppDomainSetup.DisallowApplicationBaseProbing%2A>método: <xref:System.AppDomainSetup.ApplicationBase%2A>, <xref:System.AppDomainSetup.ApplicationName%2A> <xref:System.AppDomainSetup.CachePath%2A>,,, <xref:System.AppDomainSetup.DisallowBindingRedirects%2A> ,,,,<xref:System.AppDomainSetup.DisallowPublisherPolicy%2A>,, ,<xref:System.AppDomainSetup.ShadowCopyDirectories%2A>e. <xref:System.AppDomainSetup.ShadowCopyFiles%2A> <xref:System.AppDomainSetup.PrivateBinPathProbe%2A> <xref:System.AppDomainSetup.DisallowCodeDownload%2A> <xref:System.AppDomainSetup.DynamicBase%2A> <xref:System.AppDomainSetup.LoaderOptimization%2A> <xref:System.AppDomainSetup.PrivateBinPath%2A></span><span class="sxs-lookup"><span data-stu-id="1226b-140">In addition to configuration information, you can change the following settings on the <xref:System.AppDomainSetup> object that is passed to your implementation of the <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> method: <xref:System.AppDomainSetup.ApplicationBase%2A>, <xref:System.AppDomainSetup.ApplicationName%2A>, <xref:System.AppDomainSetup.CachePath%2A>, <xref:System.AppDomainSetup.DisallowApplicationBaseProbing%2A>, <xref:System.AppDomainSetup.DisallowBindingRedirects%2A>, <xref:System.AppDomainSetup.DisallowCodeDownload%2A>, <xref:System.AppDomainSetup.DisallowPublisherPolicy%2A>, <xref:System.AppDomainSetup.DynamicBase%2A>, <xref:System.AppDomainSetup.LoaderOptimization%2A>, <xref:System.AppDomainSetup.PrivateBinPath%2A>, <xref:System.AppDomainSetup.PrivateBinPathProbe%2A>, <xref:System.AppDomainSetup.ShadowCopyDirectories%2A>, and <xref:System.AppDomainSetup.ShadowCopyFiles%2A>.</span></span>  
  
 <span data-ttu-id="1226b-141">Como alternativa ao uso do `<disableFusionUpdatesFromADManager>` elemento, você pode desabilitar o comportamento padrão criando uma configuração do registro ou definindo uma variável de ambiente.</span><span class="sxs-lookup"><span data-stu-id="1226b-141">As an alternative to using the `<disableFusionUpdatesFromADManager>` element, you can disable the default behavior by creating a registry setting or by setting an environment variable.</span></span> <span data-ttu-id="1226b-142">No registro, crie um valor DWORD chamado `COMPLUS_disableFusionUpdatesFromADManager` em `HKCU\Software\Microsoft\.NETFramework` ou `HKLM\Software\Microsoft\.NETFramework`e defina o valor como 1.</span><span class="sxs-lookup"><span data-stu-id="1226b-142">In the registry, create a DWORD value named `COMPLUS_disableFusionUpdatesFromADManager` under `HKCU\Software\Microsoft\.NETFramework` or `HKLM\Software\Microsoft\.NETFramework`, and set the value to 1.</span></span> <span data-ttu-id="1226b-143">Na linha de comando, defina a variável `COMPLUS_disableFusionUpdatesFromADManager` de ambiente como 1.</span><span class="sxs-lookup"><span data-stu-id="1226b-143">At the command line, set the environment variable `COMPLUS_disableFusionUpdatesFromADManager` to 1.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1226b-144">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1226b-144">Example</span></span>  
 <span data-ttu-id="1226b-145">O exemplo a seguir mostra como desabilitar a capacidade de substituir as configurações de fusão usando `<disableFusionUpdatesFromADManager>` o elemento.</span><span class="sxs-lookup"><span data-stu-id="1226b-145">The following example shows how to disable the ability to override Fusion settings by using the `<disableFusionUpdatesFromADManager>` element.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <disableFusionUpdatesFromADManager enabled="1" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="1226b-146">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1226b-146">See also</span></span>

- [<span data-ttu-id="1226b-147">Esquema de configurações do tempo de execução</span><span class="sxs-lookup"><span data-stu-id="1226b-147">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="1226b-148">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="1226b-148">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="1226b-149">Como o tempo de execução localiza assemblies</span><span class="sxs-lookup"><span data-stu-id="1226b-149">How the Runtime Locates Assemblies</span></span>](../../../deployment/how-the-runtime-locates-assemblies.md)
