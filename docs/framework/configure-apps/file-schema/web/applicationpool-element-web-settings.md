---
title: '&lt;applicationPool&gt; elemento (configurações da Web)'
ms.date: 03/30/2017
helpviewer_keywords:
- applicationPool element
- <applicationPool> element
ms.assetid: 46d1baaa-e343-4639-b70d-2a43a9f62b2a
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: a2eafc6b5ad1446fd07518f877a8ec001ad8dbd6
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32757691"
---
# <a name="ltapplicationpoolgt-element-web-settings"></a>&lt;applicationPool&gt; elemento (configurações da Web)
Especifica as configurações que são usadas pelo ASP.NET para gerenciar o comportamento de todo o processo quando um aplicativo ASP.NET é executado no modo integrado em [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] ou uma versão posterior.  
  
> [!IMPORTANT]
>  Esse elemento e o recurso ele dá suporte só funciona se o seu aplicativo ASP.NET hospedado em [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] ou versões posteriores.  
  
 \<configuration>  
\<System. Web > elemento (configurações da Web)  
\<applicationPool > elemento (configurações da Web)  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<applicationPool   
    maxConcurrentRequestsPerCPU="5000"   
    maxConcurrentThreadsPerCPU="0"   
    requestQueueLimit="5000" />  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`maxConcurrentRequestsPerCPU`|Especifica a quantidade de solicitações simultâneas permitido pelo ASP.NET por CPU.|  
|`maxConcurrentThreadsPerCPU`|Especifica quantos threads simultâneos podem estar em execução para um pool de aplicativos para cada CPU. Isso fornece uma maneira alternativa de controle de simultaneidade do ASP.NET, porque você pode limitar o número de threads gerenciados que podem ser usados por CPU para atender a solicitações. Por padrão, essa configuração é 0, o que significa que o ASP.NET não limita o número de threads que podem ser criados por CPU, embora o pool de threads do CLR também limita o número de threads que podem ser criados.|  
|`requestQueueLimit`|Especifica o número máximo de solicitações que podem ser enfileiradas para o ASP.NET em um único processo. Quando dois ou mais aplicativos ASP.NET executados em um único pool de aplicativos, o conjunto cumulativo de solicitações sendo feitas a qualquer aplicativo no pool de aplicativos está sujeito a essa configuração.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<system.web>](../../../../../docs/framework/configure-apps/file-schema/web/system-web-element-web-settings.md)|Contém informações sobre como o ASP.NET interage com um aplicativo host.|  
  
## <a name="remarks"></a>Comentários  
 Quando você executa [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] ou uma versão posterior no modo integrado, essa combinação de elemento permite que você configure como o ASP.NET gerencia solicitações de threads e filas quando o aplicativo é hospedado em um pool de aplicativos do IIS. Se você executar o IIS 6 ou executar [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] no modo clássico ou no modo ISAPI, essas configurações são ignoradas.  
  
 O `applicationPool` configurações se aplicam a todos os pools de aplicativos que são executados em uma versão específica do .NET Framework. As configurações estão contidas em um arquivo ASPNET config. Há uma versão desse arquivo para as versões 2.0 e 4.0 do .NET Framework. (As versões 3.0 e 3.5 do .NET Framework compartilham o arquivo ASPNET config com a versão 2.0.)  
  
> [!IMPORTANT]
>  Se você executar [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] em [!INCLUDE[win7](../../../../../includes/win7-md.md)], você pode configurar um arquivo ASPNET separado para cada pool de aplicativos. Isso lhe permite personalizar o desempenho dos threads para cada pool de aplicativos.  
  
 Para o `maxConcurrentRequestsPerCPU` configuração, a configuração padrão de "5000" o [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] efetivamente desativa limitação de solicitação que é controlado pelo ASP.NET, a menos que você realmente tem 5000 ou mais solicitações por CPU. A configuração padrão depende em vez disso, o pool de threads do CLR para gerenciar automaticamente a simultaneidade por CPU. Aplicativos que fazem uso extensivo de processamento assíncrono da solicitação, ou que têm muitas solicitações de longa execução bloqueadas na rede e/s, se beneficiam o limite padrão de aumento no [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)]. Definindo `maxConcurrentRequestsPerCPU` como zero desativa o uso de threads gerenciados para processar solicitações ASP.NET. Quando um aplicativo é executado em um pool de aplicativos do IIS, solicitações permanecem no thread de e/s do IIS e, portanto, simultaneidade é limitada pelas configurações de thread do IIS.  
  
 O `requestQueueLimit` configuração funciona da mesma forma que o `requestQueueLimit` atributo do [processModel](http://msdn.microsoft.com/library/4b8fe20e-74c8-4566-b72c-ce5f83c8e32d) elemento, que é definido nos arquivos Web. config para aplicativos ASP.NET. No entanto, o `requestQueueLimit` configuração em um arquivo ASPNET substitui o `requestQueueLimit` configuração em um arquivo Web. config. Em outras palavras, se ambos os atributos são definidos (por padrão, isso é verdadeiro), o `requestQueueLimit` configuração no arquivo ASPNET terá precedência.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como configurar o comportamento de todo o processo do ASP.NET no arquivo ASPNET nas seguintes circunstâncias:  
  
-   O aplicativo é hospedado em um [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] pool de aplicativos.  
  
-   [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] está em execução no modo integrado.  
  
-   O aplicativo está usando o [!INCLUDE[net_v35SP1_short](../../../../../includes/net-v35sp1-short-md.md)] ou uma versão posterior.  
  
 Os valores de exemplo são os valores padrão.  
  
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
|Nome do esquema||  
|Arquivo de validação||  
|Pode ser vazio||  
  
## <a name="see-also"></a>Consulte também  
 [\<system.web> Element (Web Settings)](../../../../../docs/framework/configure-apps/file-schema/web/system-web-element-web-settings.md) [Elemento system.web> (configurações da Web)]
