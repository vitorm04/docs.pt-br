---
title: '&lt;disableFusionUpdatesFromADManager&gt; elemento'
ms.date: 03/30/2017
helpviewer_keywords:
- disableFusionUpdatesFromADManager element
- <disableFusionUpdatesFromADManager> element
ms.assetid: 58d2866c-37bd-4ffa-abaf-ff35926a2939
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8e5e33cd3d250b26f0a83a87c4f7ce438af22e96
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="ltdisablefusionupdatesfromadmanagergt-element"></a>&lt;disableFusionUpdatesFromADManager&gt; elemento
Especifica se o comportamento padrão, que é permitir que o host de tempo de execução substitua as definições de configuração de um domínio de aplicativo, está desabilitado.  
  
 \<Configuração > elemento  
\<tempo de execução > elemento  
\<disableFusionUpdatesFromADManager >  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<disableFusionUpdatesFromADManager enabled="0|1"/>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|habilitado|Atributo obrigatório.<br /><br /> Especifica se a capacidade de padrão para substituir as definições de fusão está desabilitada.|  
  
## <a name="enabled-attribute"></a>Atributo habilitado  
  
|Valor|Descrição|  
|-----------|-----------------|  
|0|Não desabilite a habilidade de substituir configurações de fusão. Esse é o comportamento padrão, começando com o [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)].|  
|1|Desabilite a capacidade de substituir configurações de fusão. Isso será revertido para o comportamento de versões anteriores do .NET Framework.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|`configuration`|O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.|  
|`runtime`|Contém informações sobre associação do assembly e coleta de lixo.|  
  
## <a name="remarks"></a>Comentários  
 Começando com o [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], o comportamento padrão é permitir que o <xref:System.AppDomainManager> objeto substituir as definições de configuração usando o <xref:System.AppDomainSetup.ConfigurationFile%2A> propriedade ou o <xref:System.AppDomainSetup.SetConfigurationBytes%2A> método do <xref:System.AppDomainSetup> objeto que é passado para sua implementação do <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> método na sua subclasse de <xref:System.AppDomainManager>. Para o domínio de aplicativo padrão, as configurações que você alterar substituirão as configurações que foram especificadas pelo arquivo de configuração de aplicativo. Para outros domínios de aplicativo, elas substituirão as configurações que foram passadas para o <xref:System.AppDomainManager.CreateDomain%2A?displayProperty=nameWithType> ou <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> método.  
  
 Você pode passar novas informações de configuração ou passar nulo (`Nothing` no Visual Basic) para eliminar as informações de configuração que foi passadas.  
  
 Não passe informações de configuração para ambos os <xref:System.AppDomainSetup.ConfigurationFile%2A> propriedade e o <xref:System.AppDomainSetup.SetConfigurationBytes%2A> método. Se você transmitir informações de configuração para ambas, as informações que você passa para o <xref:System.AppDomainSetup.ConfigurationFile%2A> propriedade será ignorada, pois o <xref:System.AppDomainSetup.SetConfigurationBytes%2A> método substitui as informações de configuração do arquivo de configuração de aplicativo. Se você usar o <xref:System.AppDomainSetup.ConfigurationFile%2A> propriedade, você pode passar nulo (`Nothing` no Visual Basic) para o <xref:System.AppDomainSetup.SetConfigurationBytes%2A> método para eliminar qualquer bytes de configuração que foram especificados na chamada para o <xref:System.AppDomainManager.CreateDomain%2A?displayProperty=nameWithType> ou <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> método.  
  
 Além das informações de configuração, você pode alterar as configurações a seguir no <xref:System.AppDomainSetup> que é passado para a implementação do objeto de <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> método: <xref:System.AppDomainSetup.ApplicationBase%2A>, <xref:System.AppDomainSetup.ApplicationName%2A>, <xref:System.AppDomainSetup.CachePath%2A>, <xref:System.AppDomainSetup.DisallowApplicationBaseProbing%2A>, <xref:System.AppDomainSetup.DisallowBindingRedirects%2A> , <xref:System.AppDomainSetup.DisallowCodeDownload%2A>, <xref:System.AppDomainSetup.DisallowPublisherPolicy%2A>, <xref:System.AppDomainSetup.DynamicBase%2A>, <xref:System.AppDomainSetup.LoaderOptimization%2A>, <xref:System.AppDomainSetup.PrivateBinPath%2A>, <xref:System.AppDomainSetup.PrivateBinPathProbe%2A>, <xref:System.AppDomainSetup.ShadowCopyDirectories%2A>, e <xref:System.AppDomainSetup.ShadowCopyFiles%2A>.  
  
 Como uma alternativa ao uso de `<disableFusionUpdatesFromADManager>` elemento, você pode desabilitar o comportamento padrão criando uma configuração de registro ou definindo uma variável de ambiente. No registro, crie um valor DWORD chamado `COMPLUS_disableFusionUpdatesFromADManager` em `HKCU\Software\Microsoft\.NETFramework` ou `HKLM\Software\Microsoft\.NETFramework`e defina o valor como 1. Na linha de comando, defina a variável de ambiente `COMPLUS_disableFusionUpdatesFromADManager` como 1.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como desabilitar a capacidade de substituir configurações de fusão usando o `<disableFusionUpdatesFromADManager>` elemento.  
  
```xml  
<configuration>  
   <runtime>  
      <disableFusionUpdatesFromADManager enabled="1" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Consulte também  
 [Esquema de configurações do tempo de execução](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [Esquema de arquivos de configuração](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [Como o tempo de execução localiza assemblies](../../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
