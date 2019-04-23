---
title: Esquema de configurações de rede
ms.date: 03/30/2017
helpviewer_keywords:
- elements [.NET Framework], network configuration elements
- sending data, network configuration elements
- receiving data, network configuration elements
- configuration settings [.NET Framework], networks
- Internet, network configuration elements
- network configuration elements
- network settings
- connections [.NET Framework], network configuration elements
- network resources, network configuration elements
ms.assetid: f1de5a0f-76c5-4833-819f-5222b8146340
ms.openlocfilehash: 71d945e6046a8648a812de939f197429bc695808
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59148285"
---
# <a name="network-settings-schema"></a>Esquema de configurações de rede
As configurações de rede especificam como o .NET Framework se conecta à Internet. A tabela a seguir descreve a função de cada elemento de configuração filho no [\<system.Net> Element (Network Settings)](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md) [Elemento system.Net> (configurações de rede)].  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<authenticationModules> Element (Network Settings)](../../../../../docs/framework/configure-apps/file-schema/network/authenticationmodules-element-network-settings.md) [Elemento authenticationModules> (configurações de rede)]|Especifica os módulos usados para autenticar solicitações de Internet.|  
|[\<connectionManagement> Element (Network Settings)](../../../../../docs/framework/configure-apps/file-schema/network/connectionmanagement-element-network-settings.md) [Elemento connectionManagement> (configurações de rede)]|Especifica o número máximo de conexões com host da Internet.|  
|[\<defaultProxy> Element (Network Settings)](../../../../../docs/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings.md) [Elemento defaultProxy> (configurações de rede)]|Especifica o servidor proxy usado para solicitações HTTP para a Internet.|  
|[\<mailSettings> Element (Network Settings)](../../../../../docs/framework/configure-apps/file-schema/network/mailsettings-element-network-settings.md) [Elemento mailSettings> (configurações de rede)]|Contém configurações para opções de envio de email.|  
|[\<requestCaching> Element (Network Settings)](../../../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md) [Elemento requestCaching> (configurações de rede)]|Controla o mecanismo de cache para solicitações de rede.|  
|[\<webRequestModules> Element (Network Settings)](../../../../../docs/framework/configure-apps/file-schema/network/webrequestmodules-element-network-settings.md) [Elemento webRequestModules> (configurações de rede)]|Especifica os módulos usados para solicitar informações de hosts da Internet.|  
  
 As configurações de URI especificam como o .NET Framework controla endereços da Web expressos usando URIs (Uniform Resource Identifiers). A tabela a seguir descreve a função de cada elemento de configuração filho no [\<Uri> Element (Uri Settings)](../../../../../docs/framework/configure-apps/file-schema/network/uri-element-uri-settings.md) [Elemento Uri> (configurações de URI)].  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<idn> Element (Uri Settings)](../../../../../docs/framework/configure-apps/file-schema/network/idn-element-uri-settings.md) [Elemento idn> (configurações de URI)]|Especifica se a análise de IDN (Nome de Domínio Internacionalizado) será aplicada aos nomes de domínio.|  
|[\<iriParsing> Element (Uri Settings)](../../../../../docs/framework/configure-apps/file-schema/network/iriparsing-element-uri-settings.md) [Elemento iriParsing> (configurações de URI)]|Especifica se a análise de IRI (Identificador de Recurso Internacional) é aplicada a um <xref:System.Uri> e se as regras de análise de IRI devem ser aplicada.|  
|[\<schemeSettings> Element (Uri Settings)](../../../../../docs/framework/configure-apps/file-schema/network/schemesettings-element-uri-settings.md) [Elemento schemeSettings> (configurações de URI)]|Especifica como um <xref:System.Uri> será analisado quanto a esquemas específicos.|  
  
## <a name="see-also"></a>Consulte também

- [Configurando aplicativos da Internet](../../../../../docs/framework/network-programming/configuring-internet-applications.md)
- [Esquema de arquivos de configuração](../../../../../docs/framework/configure-apps/file-schema/index.md)
