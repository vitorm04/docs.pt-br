---
title: Elemento <disableFusionUpdatesFromADManager>
ms.date: 03/30/2017
helpviewer_keywords:
- disableFusionUpdatesFromADManager element
- <disableFusionUpdatesFromADManager> element
ms.assetid: 58d2866c-37bd-4ffa-abaf-ff35926a2939
ms.openlocfilehash: 4e7375fddaa98b45766b29d911d555f773edcafa
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73117451"
---
# <a name="disablefusionupdatesfromadmanager-element"></a><span data-ttu-id="067de-102">Elemento \<disableFusionUpdatesFromADManager></span><span class="sxs-lookup"><span data-stu-id="067de-102">\<disableFusionUpdatesFromADManager> Element</span></span>
<span data-ttu-id="067de-103">Especifica se o comportamento padrão, que é permitir que o host de runtime substitua as definições de configuração de um domínio de aplicativo, está desabilitado.</span><span class="sxs-lookup"><span data-stu-id="067de-103">Specifies whether the default behavior, which is to allow the runtime host to override configuration settings for an application domain, is disabled.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<disableFusionUpdatesFromADManager>**  
  
## <a name="syntax"></a><span data-ttu-id="067de-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="067de-104">Syntax</span></span>  
  
```xml  
<disableFusionUpdatesFromADManager enabled="0|1"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="067de-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="067de-105">Attributes and Elements</span></span>  
 <span data-ttu-id="067de-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="067de-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="067de-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="067de-107">Attributes</span></span>  
  
|<span data-ttu-id="067de-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="067de-108">Attribute</span></span>|<span data-ttu-id="067de-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="067de-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="067de-110">Habilitado</span><span class="sxs-lookup"><span data-stu-id="067de-110">enabled</span></span>|<span data-ttu-id="067de-111">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="067de-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="067de-112">Especifica se a capacidade padrão de substituir as configurações de fusão está desabilitada.</span><span class="sxs-lookup"><span data-stu-id="067de-112">Specifies whether the default ability to override Fusion settings is disabled.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="067de-113">Atributo habilitado</span><span class="sxs-lookup"><span data-stu-id="067de-113">enabled Attribute</span></span>  
  
|<span data-ttu-id="067de-114">Valor</span><span class="sxs-lookup"><span data-stu-id="067de-114">Value</span></span>|<span data-ttu-id="067de-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="067de-115">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="067de-116">0</span><span class="sxs-lookup"><span data-stu-id="067de-116">0</span></span>|<span data-ttu-id="067de-117">Não desabilite a capacidade de substituir as configurações de fusão.</span><span class="sxs-lookup"><span data-stu-id="067de-117">Do not disable the ability to override Fusion settings.</span></span> <span data-ttu-id="067de-118">Esse é o comportamento padrão, começando com o .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="067de-118">This is the default behavior, starting with the .NET Framework 4.</span></span>|  
|<span data-ttu-id="067de-119">1</span><span class="sxs-lookup"><span data-stu-id="067de-119">1</span></span>|<span data-ttu-id="067de-120">Desabilite a capacidade de substituir as configurações de fusão.</span><span class="sxs-lookup"><span data-stu-id="067de-120">Disable the ability to override Fusion settings.</span></span> <span data-ttu-id="067de-121">Isso reverte para o comportamento de versões anteriores do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="067de-121">This reverts to the behavior of earlier versions of the .NET Framework.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="067de-122">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="067de-122">Child Elements</span></span>  
 <span data-ttu-id="067de-123">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="067de-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="067de-124">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="067de-124">Parent Elements</span></span>  
  
|<span data-ttu-id="067de-125">Elemento</span><span class="sxs-lookup"><span data-stu-id="067de-125">Element</span></span>|<span data-ttu-id="067de-126">Descrição</span><span class="sxs-lookup"><span data-stu-id="067de-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="067de-127">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="067de-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="067de-128">Contém informações sobre associação do assembly e coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="067de-128">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="067de-129">Comentários</span><span class="sxs-lookup"><span data-stu-id="067de-129">Remarks</span></span>  
 <span data-ttu-id="067de-130">Começando com o .NET Framework 4, o comportamento padrão é permitir que o <xref:System.AppDomainManager> objeto substitua as definições de configuração usando a <xref:System.AppDomainSetup.ConfigurationFile%2A> propriedade ou o <xref:System.AppDomainSetup.SetConfigurationBytes%2A> método do <xref:System.AppDomainSetup> objeto que é passado para sua implementação do <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> método, em sua subclasse de <xref:System.AppDomainManager> .</span><span class="sxs-lookup"><span data-stu-id="067de-130">Starting with the .NET Framework 4, the default behavior is to allow the <xref:System.AppDomainManager> object to override configuration settings by using the <xref:System.AppDomainSetup.ConfigurationFile%2A> property or the <xref:System.AppDomainSetup.SetConfigurationBytes%2A> method of the <xref:System.AppDomainSetup> object that is passed to your implementation of the <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> method, in your subclass of <xref:System.AppDomainManager>.</span></span> <span data-ttu-id="067de-131">Para o domínio de aplicativo padrão, as configurações alteradas substituem as configurações que foram especificadas pelo arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="067de-131">For the default application domain, the settings you change override the settings that were specified by the application configuration file.</span></span> <span data-ttu-id="067de-132">Para outros domínios de aplicativo, eles substituem as definições de configuração que foram passadas para o <xref:System.AppDomainManager.CreateDomain%2A?displayProperty=nameWithType> <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> método ou.</span><span class="sxs-lookup"><span data-stu-id="067de-132">For other application domains, they override the configuration settings that were passed to the <xref:System.AppDomainManager.CreateDomain%2A?displayProperty=nameWithType> or <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="067de-133">Você pode passar novas informações de configuração ou passar NULL ( `Nothing` em Visual Basic) para eliminar informações de configuração que foram passadas.</span><span class="sxs-lookup"><span data-stu-id="067de-133">You can either pass new configuration information, or pass null (`Nothing` in Visual Basic) to eliminate configuration information that was passed in.</span></span>  
  
 <span data-ttu-id="067de-134">Não transmita informações de configuração para a <xref:System.AppDomainSetup.ConfigurationFile%2A> propriedade e o <xref:System.AppDomainSetup.SetConfigurationBytes%2A> método.</span><span class="sxs-lookup"><span data-stu-id="067de-134">Do not pass configuration information to both the <xref:System.AppDomainSetup.ConfigurationFile%2A> property and the <xref:System.AppDomainSetup.SetConfigurationBytes%2A> method.</span></span> <span data-ttu-id="067de-135">Se você passar informações de configuração para ambos, as informações passadas para a <xref:System.AppDomainSetup.ConfigurationFile%2A> propriedade serão ignoradas, pois o <xref:System.AppDomainSetup.SetConfigurationBytes%2A> método substitui as informações de configuração do arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="067de-135">If you pass configuration information to both, the information you pass to the <xref:System.AppDomainSetup.ConfigurationFile%2A> property is ignored, because the <xref:System.AppDomainSetup.SetConfigurationBytes%2A> method overrides configuration information from the application configuration file.</span></span> <span data-ttu-id="067de-136">Se você usar a <xref:System.AppDomainSetup.ConfigurationFile%2A> propriedade, poderá passar NULL ( `Nothing` em Visual Basic) para o <xref:System.AppDomainSetup.SetConfigurationBytes%2A> método para eliminar quaisquer bytes de configuração que foram especificados na chamada para o <xref:System.AppDomainManager.CreateDomain%2A?displayProperty=nameWithType> método ou <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="067de-136">If you use the <xref:System.AppDomainSetup.ConfigurationFile%2A> property, you can pass null (`Nothing` in Visual Basic) to the <xref:System.AppDomainSetup.SetConfigurationBytes%2A> method to eliminate any configuration bytes that were specified in the call to the <xref:System.AppDomainManager.CreateDomain%2A?displayProperty=nameWithType> or <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="067de-137">Além das informações de configuração, você pode alterar as seguintes configurações no <xref:System.AppDomainSetup> objeto que é passado para a implementação do método:,,,,,,,,,, <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> <xref:System.AppDomainSetup.ApplicationBase%2A> <xref:System.AppDomainSetup.ApplicationName%2A> <xref:System.AppDomainSetup.CachePath%2A> <xref:System.AppDomainSetup.DisallowApplicationBaseProbing%2A> <xref:System.AppDomainSetup.DisallowBindingRedirects%2A> <xref:System.AppDomainSetup.DisallowCodeDownload%2A> <xref:System.AppDomainSetup.DisallowPublisherPolicy%2A> <xref:System.AppDomainSetup.DynamicBase%2A> <xref:System.AppDomainSetup.LoaderOptimization%2A> <xref:System.AppDomainSetup.PrivateBinPath%2A> <xref:System.AppDomainSetup.PrivateBinPathProbe%2A> , <xref:System.AppDomainSetup.ShadowCopyDirectories%2A> e <xref:System.AppDomainSetup.ShadowCopyFiles%2A> .</span><span class="sxs-lookup"><span data-stu-id="067de-137">In addition to configuration information, you can change the following settings on the <xref:System.AppDomainSetup> object that is passed to your implementation of the <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> method: <xref:System.AppDomainSetup.ApplicationBase%2A>, <xref:System.AppDomainSetup.ApplicationName%2A>, <xref:System.AppDomainSetup.CachePath%2A>, <xref:System.AppDomainSetup.DisallowApplicationBaseProbing%2A>, <xref:System.AppDomainSetup.DisallowBindingRedirects%2A>, <xref:System.AppDomainSetup.DisallowCodeDownload%2A>, <xref:System.AppDomainSetup.DisallowPublisherPolicy%2A>, <xref:System.AppDomainSetup.DynamicBase%2A>, <xref:System.AppDomainSetup.LoaderOptimization%2A>, <xref:System.AppDomainSetup.PrivateBinPath%2A>, <xref:System.AppDomainSetup.PrivateBinPathProbe%2A>, <xref:System.AppDomainSetup.ShadowCopyDirectories%2A>, and <xref:System.AppDomainSetup.ShadowCopyFiles%2A>.</span></span>  
  
 <span data-ttu-id="067de-138">Como alternativa ao uso do `<disableFusionUpdatesFromADManager>` elemento, você pode desabilitar o comportamento padrão criando uma configuração do registro ou definindo uma variável de ambiente.</span><span class="sxs-lookup"><span data-stu-id="067de-138">As an alternative to using the `<disableFusionUpdatesFromADManager>` element, you can disable the default behavior by creating a registry setting or by setting an environment variable.</span></span> <span data-ttu-id="067de-139">No registro, crie um valor DWORD chamado `COMPLUS_disableFusionUpdatesFromADManager` em `HKCU\Software\Microsoft\.NETFramework` ou `HKLM\Software\Microsoft\.NETFramework` e defina o valor como 1.</span><span class="sxs-lookup"><span data-stu-id="067de-139">In the registry, create a DWORD value named `COMPLUS_disableFusionUpdatesFromADManager` under `HKCU\Software\Microsoft\.NETFramework` or `HKLM\Software\Microsoft\.NETFramework`, and set the value to 1.</span></span> <span data-ttu-id="067de-140">Na linha de comando, defina a variável de ambiente `COMPLUS_disableFusionUpdatesFromADManager` como 1.</span><span class="sxs-lookup"><span data-stu-id="067de-140">At the command line, set the environment variable `COMPLUS_disableFusionUpdatesFromADManager` to 1.</span></span>  
  
## <a name="example"></a><span data-ttu-id="067de-141">Exemplo</span><span class="sxs-lookup"><span data-stu-id="067de-141">Example</span></span>  
 <span data-ttu-id="067de-142">O exemplo a seguir mostra como desabilitar a capacidade de substituir as configurações de fusão usando o `<disableFusionUpdatesFromADManager>` elemento.</span><span class="sxs-lookup"><span data-stu-id="067de-142">The following example shows how to disable the ability to override Fusion settings by using the `<disableFusionUpdatesFromADManager>` element.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <disableFusionUpdatesFromADManager enabled="1" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="067de-143">Confira também</span><span class="sxs-lookup"><span data-stu-id="067de-143">See also</span></span>

- [<span data-ttu-id="067de-144">Esquema de configurações do runtime</span><span class="sxs-lookup"><span data-stu-id="067de-144">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="067de-145">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="067de-145">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="067de-146">Como o runtime localiza assemblies</span><span class="sxs-lookup"><span data-stu-id="067de-146">How the Runtime Locates Assemblies</span></span>](../../../deployment/how-the-runtime-locates-assemblies.md)
