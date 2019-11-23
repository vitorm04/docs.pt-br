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
ms.openlocfilehash: 5c5c857d4494b6d78b819e56bae4213abc5e2035
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71699100"
---
# <a name="systemweb-element-web-settings"></a>Elemento de > de \<System. Web (configurações da Web)
Contém informações sobre como a camada de hospedagem ASP.NET gerencia o comportamento de todo o processo.  
  
[ **\<configuration>** ](../configuration-element.md)  
&nbsp;&nbsp; **\<System. web >**  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<system.web>  
</system.web>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  

As seções a seguir descrevem os atributos, bem como os elementos filhos e pais.  
  
### <a name="attributes"></a>Atributos  

None.  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<applicationPool>](applicationpool-element-web-settings.md)|Especifica as definições de configuração para pools de aplicativos do IIS em um arquivo Aspnet. config.|  
  
### <a name="parent-elements"></a>Elementos Pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<configuration>](../configuration-element.md)|Especifica o elemento raiz em cada arquivo de configuração que é usado pelo Common Language Runtime e .NET Framework aplicativos.|  
  
## <a name="remarks"></a>Comentários  

O elemento `system.web` e seu elemento `applicationPool` filho foram adicionados à .NET Framework a partir do .NET Framework 3,5 SP1. Quando você executa o IIS 7,0 ou versões posteriores no modo integrado, essa combinação de elementos permite que você configure como o ASP.NET gerencia threads e como ele enfileira solicitações quando o ASP.NET está hospedado em um pool de aplicativos do IIS. Se você executar o IIS 7,0 ou versões posteriores no modo clássico ou ISAPI, essas configurações serão ignoradas.  
  
## <a name="example"></a>{1&gt;Exemplo&lt;1}  

O exemplo a seguir mostra como configurar o comportamento do ASP.NET em todo o processo no arquivo Aspnet. config quando o ASP.NET está hospedado em um pool de aplicativos do IIS. O exemplo supõe que o IIS está sendo executado no modo integrado e que o aplicativo está usando o .NET Framework 3,5 SP1 ou uma versão posterior. Esse comportamento não ocorre em versões do .NET Framework anteriores ao .NET Framework 3,5 SP1. Os valores no exemplo são os valores padrão.  
  
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
|{1&gt;Namespace&lt;1}||  
|Schema Name||  
|Arquivo de validação||  
|Pode estar vazio||  
  
## <a name="see-also"></a>Consulte também

- [\<applicationPool> Element (Web Settings)](applicationpool-element-web-settings.md) [Elemento applicationPool> (configurações da Web)]
