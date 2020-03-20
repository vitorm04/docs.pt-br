---
title: Elemento <system.web> (Configurações da Web)
ms.date: 03/30/2017
helpviewer_keywords:
- Web.config configuration file [ASP.NET]
- system.Web element
- <system.Web> element
- ASP.NET configuration system
- configuration files [ASP.NET]
ms.assetid: 24c4cf4f-ad32-42b2-b040-8e4549e2855e
ms.openlocfilehash: b37b05bdf90630251cbfcf86751243a3a8b77663
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152835"
---
# <a name="systemweb-element-web-settings"></a>\<system.web> Element (Web Settings) [Elemento system.web> (configurações da Web)]
Contém informações sobre como a camada de hospedagem ASP.NET gerencia o comportamento em todo o processo.  
  
[**\<>de configuração**](../configuration-element.md)  
&nbsp;&nbsp;**\<system.web>**  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<system.web>  
</system.web>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  

As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  

Nenhum.  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<>de pool de aplicativos](applicationpool-element-web-settings.md)|Especifica as configurações de configuração para pools de aplicativos IIS em um arquivo aspnet.config.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<>de configuração](../configuration-element.md)|Especifica o elemento raiz em cada arquivo de configuração que é usado pelos aplicativos common language runtime e .NET Framework.|  
  
## <a name="remarks"></a>Comentários  

O `system.web` elemento e `applicationPool` seu elemento filho foram adicionados ao Quadro .NET a partir do Quadro .NET 3.5 SP1. Quando você executa versões IIS 7.0 ou posteriores no modo Integrado, essa combinação de elementos permite configurar como ASP.NET gerencia threads e como ele faz filas quando ASP.NET está hospedado em um pool de aplicativos IIS. Se você executar versões IIS 7.0 ou posteriores no modo Classic ou ISAPI, essas configurações serão ignoradas.  
  
## <a name="example"></a>Exemplo  

O exemplo a seguir mostra como configurar ASP.NET comportamento em todo o processo no arquivo aspnet.config quando ASP.NET está hospedado em um pool de aplicativos IIS. O exemplo pressupõe que o IIS está sendo executado no modo Integrado e que o aplicativo está usando o .NET Framework 3.5 SP1 ou uma versão posterior. Esse comportamento não ocorre em versões do Quadro .NET antes do Quadro .NET 3.5 SP1. Os valores no exemplo são os valores padrão.  
  
```xml  
<configuration>  
  <system.web>  
    <applicationPool
        maxConcurrentRequestsPerCPU="5000"
        maxConcurrentThreadsPerCPU="0"
        requestQueueLimit="5000" />  
  </system.web>  
</configuration>  
```  
  
## <a name="element-information"></a>Informações do elemento  
  
|||  
|-|-|  
|Namespace||  
|Nome do Esquema||  
|Arquivo de validação||  
|Pode ser vazio||  
  
## <a name="see-also"></a>Confira também

- [\<aplicativoPool> Element (Configurações da Web)](applicationpool-element-web-settings.md)
