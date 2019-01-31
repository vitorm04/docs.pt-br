---
title: Elemento <disableFusionUpdatesFromADManager>
ms.date: 03/30/2017
helpviewer_keywords:
- disableFusionUpdatesFromADManager element
- <disableFusionUpdatesFromADManager> element
ms.assetid: 58d2866c-37bd-4ffa-abaf-ff35926a2939
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c2734060c855b59e5ff47ae674862dc57b7ddb5e
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55270755"
---
# <a name="disablefusionupdatesfromadmanager-element"></a>\<disableFusionUpdatesFromADManager > elemento
Especifica se o comportamento padrão, que é permitir que o host de tempo de execução substitua as definições de configuração de um domínio de aplicativo, está desabilitado.  
  
 \<Configuração > elemento  
\<tempo de execução > elemento  
\<disableFusionUpdatesFromADManager>  
  
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
|0|Não desabilite a capacidade de substituir as configurações de fusão. Esse é o comportamento padrão, começando com o [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)].|  
|1|Desabilite a capacidade de substituir as configurações de fusão. Isso será revertido para o comportamento de versões anteriores do .NET Framework.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|`configuration`|O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.|  
|`runtime`|Contém informações sobre associação do assembly e coleta de lixo.|  
  
## <a name="remarks"></a>Comentários  
 Começando com o [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], o comportamento padrão é permitir que o <xref:System.AppDomainManager> objeto a substituir as definições de configuração usando o <xref:System.AppDomainSetup.ConfigurationFile%2A> propriedade ou o <xref:System.AppDomainSetup.SetConfigurationBytes%2A> método da <xref:System.AppDomainSetup> objeto que é passado para sua implementação dos <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> método, em sua subclasse de <xref:System.AppDomainManager>. Para o domínio de aplicativo padrão, as configurações alteradas substituirão as configurações que foram especificadas pelo arquivo de configuração de aplicativo. Para outros domínios de aplicativo, elas substituirão as configurações de configuração que foram passadas para o <xref:System.AppDomainManager.CreateDomain%2A?displayProperty=nameWithType> ou <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> método.  
  
 Você pode passar novas informações de configuração ou passar null (`Nothing` no Visual Basic) para eliminar informações de configuração que foi passadas.  
  
 Não passe informações de configuração para ambos os <xref:System.AppDomainSetup.ConfigurationFile%2A> propriedade e o <xref:System.AppDomainSetup.SetConfigurationBytes%2A> método. Se você passar informações de configuração como "ambas", as informações que você passa para o <xref:System.AppDomainSetup.ConfigurationFile%2A> propriedade será ignorada, pois o <xref:System.AppDomainSetup.SetConfigurationBytes%2A> método substitui as informações de configuração do arquivo de configuração de aplicativo. Se você usar o <xref:System.AppDomainSetup.ConfigurationFile%2A> propriedade, você pode passar nulo (`Nothing` no Visual Basic) para o <xref:System.AppDomainSetup.SetConfigurationBytes%2A> método para eliminar quaisquer bytes de configuração que foram especificados na chamada para o <xref:System.AppDomainManager.CreateDomain%2A?displayProperty=nameWithType> ou <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> método.  
  
 Além das informações de configuração, você pode alterar as configurações a seguir na <xref:System.AppDomainSetup> objeto que é passado para sua implementação do <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> método: <xref:System.AppDomainSetup.ApplicationBase%2A>, <xref:System.AppDomainSetup.ApplicationName%2A>, <xref:System.AppDomainSetup.CachePath%2A>, <xref:System.AppDomainSetup.DisallowApplicationBaseProbing%2A>, <xref:System.AppDomainSetup.DisallowBindingRedirects%2A> , <xref:System.AppDomainSetup.DisallowCodeDownload%2A>, <xref:System.AppDomainSetup.DisallowPublisherPolicy%2A>, <xref:System.AppDomainSetup.DynamicBase%2A>, <xref:System.AppDomainSetup.LoaderOptimization%2A>, <xref:System.AppDomainSetup.PrivateBinPath%2A>, <xref:System.AppDomainSetup.PrivateBinPathProbe%2A>, <xref:System.AppDomainSetup.ShadowCopyDirectories%2A>, e <xref:System.AppDomainSetup.ShadowCopyFiles%2A>.  
  
 Como uma alternativa ao uso de `<disableFusionUpdatesFromADManager>` elemento, você pode desabilitar o comportamento padrão ao criar uma configuração do registro ou definindo uma variável de ambiente. No registro, crie um valor DWORD denominado `COMPLUS_disableFusionUpdatesFromADManager` sob `HKCU\Software\Microsoft\.NETFramework` ou `HKLM\Software\Microsoft\.NETFramework`e defina o valor como 1. Na linha de comando, defina a variável de ambiente `COMPLUS_disableFusionUpdatesFromADManager` como 1.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como desabilitar a capacidade de substituir as configurações de fusão, usando o `<disableFusionUpdatesFromADManager>` elemento.  
  
```xml  
<configuration>  
   <runtime>  
      <disableFusionUpdatesFromADManager enabled="1" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Consulte também
- [Esquema de configurações do tempo de execução](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [Esquema de arquivos de configuração](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [Como o tempo de execução localiza assemblies](../../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
