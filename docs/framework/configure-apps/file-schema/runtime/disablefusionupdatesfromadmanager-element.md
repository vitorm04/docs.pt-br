---
title: Elemento <disableFusionUpdatesFromADManager>
ms.date: 03/30/2017
helpviewer_keywords:
- disableFusionUpdatesFromADManager element
- <disableFusionUpdatesFromADManager> element
ms.assetid: 58d2866c-37bd-4ffa-abaf-ff35926a2939
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b65711ad8c404d1c4f54a6197faf598e2215226f
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252657"
---
# <a name="disablefusionupdatesfromadmanager-element"></a>\<Elemento de > disableFusionUpdatesFromADManager
Especifica se o comportamento padrão, que é permitir que o host de tempo de execução substitua as definições de configuração de um domínio de aplicativo, está desabilitado.  
  
[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<> de tempo de execução**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp; **\<disableFusionUpdatesFromADManager>**  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<disableFusionUpdatesFromADManager enabled="0|1"/>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|enabled|Atributo obrigatório.<br /><br /> Especifica se a capacidade padrão de substituir as configurações de fusão está desabilitada.|  
  
## <a name="enabled-attribute"></a>Atributo habilitado  
  
|Valor|Descrição|  
|-----------|-----------------|  
|0|Não desabilite a capacidade de substituir as configurações de fusão. Esse é o comportamento padrão, começando com o .NET Framework 4.|  
|1|Desabilite a capacidade de substituir as configurações de fusão. Isso reverte para o comportamento de versões anteriores do .NET Framework.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|`configuration`|O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.|  
|`runtime`|Contém informações sobre associação do assembly e coleta de lixo.|  
  
## <a name="remarks"></a>Comentários  
 Começando com o .NET Framework 4, o comportamento padrão é permitir que o <xref:System.AppDomainManager> objeto substitua as definições de configuração usando a <xref:System.AppDomainSetup.ConfigurationFile%2A> propriedade <xref:System.AppDomainSetup> ou o <xref:System.AppDomainSetup.SetConfigurationBytes%2A> método do objeto que é passado para sua implementação do método, em sua subclasse de <xref:System.AppDomainManager>. <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> Para o domínio de aplicativo padrão, as configurações alteradas substituem as configurações que foram especificadas pelo arquivo de configuração do aplicativo. Para outros domínios de aplicativo, eles substituem as definições de configuração que foram <xref:System.AppDomainManager.CreateDomain%2A?displayProperty=nameWithType> passadas para o método ou <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> .  
  
 Você pode passar novas informações de configuração ou passar NULL (`Nothing` em Visual Basic) para eliminar informações de configuração que foram passadas.  
  
 Não transmita informações de configuração para a <xref:System.AppDomainSetup.ConfigurationFile%2A> Propriedade e o <xref:System.AppDomainSetup.SetConfigurationBytes%2A> método. Se você passar informações de configuração para ambos, as informações passadas para <xref:System.AppDomainSetup.ConfigurationFile%2A> a propriedade serão ignoradas, <xref:System.AppDomainSetup.SetConfigurationBytes%2A> pois o método substitui as informações de configuração do arquivo de configuração do aplicativo. Se você usar a <xref:System.AppDomainSetup.ConfigurationFile%2A> Propriedade, poderá passar NULL (`Nothing` em Visual Basic) para o <xref:System.AppDomainSetup.SetConfigurationBytes%2A> método para eliminar quaisquer bytes de configuração que foram especificados na chamada para o <xref:System.AppDomainManager.CreateDomain%2A?displayProperty=nameWithType> método ou <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> .  
  
 Além das informações de configuração, você pode alterar as seguintes <xref:System.AppDomainSetup> configurações no objeto que é passado para a implementação <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> do <xref:System.AppDomainSetup.DisallowApplicationBaseProbing%2A>método: <xref:System.AppDomainSetup.ApplicationBase%2A>, <xref:System.AppDomainSetup.ApplicationName%2A> <xref:System.AppDomainSetup.CachePath%2A>,,, <xref:System.AppDomainSetup.DisallowBindingRedirects%2A> ,,,,<xref:System.AppDomainSetup.DisallowPublisherPolicy%2A>,, ,<xref:System.AppDomainSetup.ShadowCopyDirectories%2A>e. <xref:System.AppDomainSetup.ShadowCopyFiles%2A> <xref:System.AppDomainSetup.PrivateBinPathProbe%2A> <xref:System.AppDomainSetup.DisallowCodeDownload%2A> <xref:System.AppDomainSetup.DynamicBase%2A> <xref:System.AppDomainSetup.LoaderOptimization%2A> <xref:System.AppDomainSetup.PrivateBinPath%2A>  
  
 Como alternativa ao uso do `<disableFusionUpdatesFromADManager>` elemento, você pode desabilitar o comportamento padrão criando uma configuração do registro ou definindo uma variável de ambiente. No registro, crie um valor DWORD chamado `COMPLUS_disableFusionUpdatesFromADManager` em `HKCU\Software\Microsoft\.NETFramework` ou `HKLM\Software\Microsoft\.NETFramework`e defina o valor como 1. Na linha de comando, defina a variável `COMPLUS_disableFusionUpdatesFromADManager` de ambiente como 1.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como desabilitar a capacidade de substituir as configurações de fusão usando `<disableFusionUpdatesFromADManager>` o elemento.  
  
```xml  
<configuration>  
   <runtime>  
      <disableFusionUpdatesFromADManager enabled="1" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Consulte também

- [Esquema de configurações do tempo de execução](index.md)
- [Esquema de arquivos de configuração](../index.md)
- [Como o tempo de execução localiza assemblies](../../../deployment/how-the-runtime-locates-assemblies.md)
