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
ms.openlocfilehash: 5e3bd1b1734fc7fba50b72785531a8b001d6d741
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71698160"
---
# <a name="network-settings-schema"></a>Esquema de configurações de rede
As configurações de rede especificam como o .NET Framework se conecta à Internet.

As configurações do @no__t -0system. net > especificam como o .NET Framework se conecta à rede. A tabela a seguir descreve a função de cada elemento de configuração filho no [\<system.Net> Element (Network Settings)](system-net-element-network-settings.md) [Elemento system.Net> (configurações de rede)].  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<authenticationModules> Element (Network Settings)](authenticationmodules-element-network-settings.md) [Elemento authenticationModules> (configurações de rede)]|Especifica os módulos usados para autenticar solicitações de Internet.|  
|[\<connectionManagement> Element (Network Settings)](connectionmanagement-element-network-settings.md) [Elemento connectionManagement> (configurações de rede)]|Especifica o número máximo de conexões com host da Internet.|  
|[\<defaultProxy> Element (Network Settings)](defaultproxy-element-network-settings.md) [Elemento defaultProxy> (configurações de rede)]|Especifica o servidor proxy usado para solicitações HTTP para a Internet.|  
|[\<mailSettings> Element (Network Settings)](mailsettings-element-network-settings.md) [Elemento mailSettings> (configurações de rede)]|Contém configurações para opções de envio de email.|  
|[\<requestCaching> Element (Network Settings)](requestcaching-element-network-settings.md) [Elemento requestCaching> (configurações de rede)]|Controla o mecanismo de cache para solicitações de rede.|  
|[\<webRequestModules> Element (Network Settings)](webrequestmodules-element-network-settings.md) [Elemento webRequestModules> (configurações de rede)]|Especifica os módulos usados para solicitar informações de hosts da Internet.|  
  
As configurações de > \<uri especificam como o .NET Framework trata os endereços da Web expressos usando URIs (identificadores de recursos uniformes). A tabela a seguir descreve a função de cada elemento de configuração filho no [elemento \<uri > (configurações de URI)](uri-element-uri-settings.md).  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<idn> Element (Uri Settings)](idn-element-uri-settings.md) [Elemento idn> (configurações de URI)]|Especifica se a análise de IDN (Nome de Domínio Internacionalizado) será aplicada aos nomes de domínio.|  
|[\<iriParsing> Element (Uri Settings)](iriparsing-element-uri-settings.md) [Elemento iriParsing> (configurações de URI)]|Especifica se a análise de IRI (Identificador de Recurso Internacional) é aplicada a um <xref:System.Uri> e se as regras de análise de IRI devem ser aplicada.|  
|[\<schemeSettings> Element (Uri Settings)](schemesettings-element-uri-settings.md) [Elemento schemeSettings> (configurações de URI)]|Especifica como um <xref:System.Uri> será analisado quanto a esquemas específicos.|  
  
## <a name="see-also"></a>Consulte também

- [Configurando aplicativos da Internet](../../../network-programming/configuring-internet-applications.md)
- [Esquema de arquivos de configuração](../index.md)
