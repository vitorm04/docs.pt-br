---
title: Interface IAppDomainSetup
ms.date: 03/30/2017
api_name:
- IAppDomainSetup
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IAppDomainSetup
helpviewer_keywords:
- IAppDomainSetup interface [.NET Framework hosting]
ms.assetid: 1844da85-c031-40bf-bea4-1a3d12a36c8c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cbcbc446eabcfcbc28c830f8860bde726c8eb6e3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33434762"
---
# <a name="iappdomainsetup-interface"></a>Interface IAppDomainSetup
Fornece propriedades que permitem que o host configurar um <xref:System.AppDomain?displayProperty=nameWithType> tipo antes de chamar o [Icorruntimehost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainex-method.md) método criá-la.  
  
## <a name="properties"></a>Propriedades  
  
|Propriedade|Descrição|  
|--------------|-----------------|  
|<xref:System.AppDomainSetup.ApplicationBase%2A>|Obtém ou define o nome do diretório que contém o aplicativo.|  
|<xref:System.AppDomainSetup.ApplicationName%2A>|Obtém ou define o nome do aplicativo.|  
|<xref:System.AppDomainSetup.CachePath%2A>|Obtém ou define o nome de uma área específica para o aplicativo em arquivos são copiados de sombra.|  
|<xref:System.AppDomainSetup.ConfigurationFile%2A>|Obtém ou define o nome do arquivo de configuração para um aplicativo.|  
|<xref:System.AppDomainSetup.DynamicBase%2A>|Obtém ou define o nome do diretório onde os arquivos gerados dinamicamente são armazenados e acessados.|  
|<xref:System.AppDomainSetup.LicenseFile%2A>|Obtém ou define o caminho para o arquivo de licença que está associado este domínio.|  
|<xref:System.AppDomainSetup.PrivateBinPath%2A>|Obtém ou define a lista de pastas, combinada com a <xref:System.AppDomainSetup.ApplicationBase%2A> diretório para investigação de assemblies privados.|  
|<xref:System.AppDomainSetup.PrivateBinPathProbe%2A>|Obtém ou define um valor de cadeia de caracteres que inclua ou exclua <xref:System.AppDomainSetup.ApplicationBase%2A> do caminho de pesquisa para o aplicativo.|  
|<xref:System.AppDomainSetup.ShadowCopyDirectories%2A>|Obtém ou define os nomes dos diretórios que contêm assemblies para ser copiado de sombra.|  
|<xref:System.AppDomainSetup.ShadowCopyFiles%2A>|Obtém ou define uma cadeia de caracteres que indica se a cópia de sombra é ativada ou desativada. Os valores válidos são "verdadeiro" ou "false".|  
  
## <a name="remarks"></a>Comentários  
 O `IAppDomainSetup` interface corresponde à gerenciado <xref:System.IAppDomainSetup> interface, que o <xref:System.AppDomainSetup> tipo implementa. Consulte <xref:System.IAppDomainSetup?displayProperty=nameWithType> para obter descrições detalhadas de suas propriedades.  
  
 `IAppDomainSetup` representa as informações de associação de assembly que podem ser adicionadas a um <xref:System.AppDomain> instância antes de sua criação. Por exemplo, um host pode definir o <xref:System.AppDomainSetup.ApplicationBase%2A> gerenciados de propriedade para estabelecer um diretório raiz que o common language runtime (CLR) sondas para assemblies.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE.h  
  
 **Biblioteca:** incluído como um recurso no MSCOREE  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.AppDomain>  
 <xref:System.AppDomainSetup>  
 <xref:System.IAppDomainSetup>  
 [Hospedagem de Interfaces](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
