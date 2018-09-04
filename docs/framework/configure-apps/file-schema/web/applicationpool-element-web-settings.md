---
title: '&lt;applicationPool&gt; (configurações da Web)'
ms.date: 03/30/2017
helpviewer_keywords:
- applicationPool element
- <applicationPool> element
ms.assetid: 46d1baaa-e343-4639-b70d-2a43a9f62b2a
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 1a129abca5888120d03c42689ac825d768733a9d
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/03/2018
ms.locfileid: "43489936"
---
# <a name="ltapplicationpoolgt-element-web-settings"></a>&lt;applicationPool&gt; (configurações da Web)
Especifica as configurações que são usadas pelo ASP.NET para gerenciar o comportamento de todo o processo quando um aplicativo ASP.NET estiver em execução no modo integrado [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] ou uma versão posterior.  
  
> [!IMPORTANT]
>  Esse elemento e o recurso ele dá suporte a funcionam apenas se seu aplicativo ASP.NET estiver hospedado em [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] ou versões posteriores.  
  
 \<configuration>  
\<System. Web > (configurações da Web)  
\<applicationPool > (configurações da Web)  
  
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
|`maxConcurrentRequestsPerCPU`|Especifica a quantidade de solicitações simultâneas por CPU, o ASP.NET permite.|  
|`maxConcurrentThreadsPerCPU`|Especifica quantos threads simultâneos podem estar em execução para um pool de aplicativos para cada CPU. Isso fornece uma maneira alternativa para controlar a simultaneidade ASP.NET, porque você pode limitar o número de threads gerenciados que pode ser usado por CPU para atender às solicitações. Por padrão, essa configuração é 0, o que significa que o ASP.NET não limita o número de threads que podem ser criados por CPU, embora o pool de threads do CLR também limita o número de threads que podem ser criados.|  
|`requestQueueLimit`|Especifica o número máximo de solicitações que podem ser enfileiradas para o ASP.NET em um único processo. Quando dois ou mais aplicativos ASP.NET executados em um único pool de aplicativos, o conjunto cumulativo de solicitações sendo feitas para qualquer aplicativo no pool de aplicativos está sujeito a essa configuração.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<system.web>](../../../../../docs/framework/configure-apps/file-schema/web/system-web-element-web-settings.md)|Contém informações sobre como o ASP.NET interage com um aplicativo host.|  
  
## <a name="remarks"></a>Comentários  
 Quando você executa [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] ou uma versão posterior no modo integrado, essa combinação de elemento permite que você configure como o ASP.NET gerencia solicitações de threads e filas quando o aplicativo é hospedado em um pool de aplicativos do IIS. Se você executa o IIS 6 ou executar [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] no modo clássico ou no modo ISAPI, essas configurações são ignoradas.  
  
 O `applicationPool` configurações se aplicam a todos os pools de aplicativos que são executados em uma versão específica do .NET Framework. As configurações estão contidas em um arquivo ASPNET config. Há uma versão desse arquivo para as versões 2.0 e 4.0 do .NET Framework. (As versões 3.0 e 3.5 do .NET Framework compartilham arquivo ASPNET config com a versão 2.0.)  
  
> [!IMPORTANT]
>  Se você executar [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] em [!INCLUDE[win7](../../../../../includes/win7-md.md)], você pode configurar um arquivo ASPNET separado para cada pool de aplicativos. Isso lhe permite personalizar o desempenho dos threads para cada pool de aplicativos.  
  
 Para o `maxConcurrentRequestsPerCPU` definindo, a configuração padrão de "5000" no [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] efetivamente desativa a limitação de solicitação que é controlado pelo ASP.NET, a menos que você realmente tem mais de 5000 solicitações por CPU. A configuração padrão em vez disso, depende do pool de threads do CLR para gerenciar automaticamente a simultaneidade por CPU. Aplicativos que fazem uso extensivo de processamento assíncrono da solicitação, ou que têm muitas solicitações de longa execução bloqueadas em e/s, de rede se beneficiará o limite padrão de aumento no [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)]. Definindo `maxConcurrentRequestsPerCPU` como zero desativa o uso de threads gerenciados para processar solicitações ASP.NET. Quando um aplicativo é executado em um pool de aplicativos do IIS, fique de solicitações no thread de e/s do IIS e, portanto, a simultaneidade é limitada pelas configurações de thread do IIS.  
  
 O `requestQueueLimit` configuração funciona da mesma forma que o `requestQueueLimit` atributo da [processModel](https://msdn.microsoft.com/library/4b8fe20e-74c8-4566-b72c-ce5f83c8e32d) elemento, que é definido nos arquivos Web. config para aplicativos ASP.NET. No entanto, o `requestQueueLimit` substituições de configuração em um arquivo ASPNET o `requestQueueLimit` definindo em um arquivo Web. config. Em outras palavras, se ambos os atributos são definidos (por padrão, isso é verdadeiro), o `requestQueueLimit` configuração no arquivo ASPNET config tem precedência.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como configurar o comportamento de todo o processo do ASP.NET no arquivo ASPNET config nas seguintes circunstâncias:  
  
-   O aplicativo é hospedado em um [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] pool de aplicativos.  
  
-   [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] está em execução no modo integrado.  
  
-   O aplicativo está usando o [!INCLUDE[net_v35SP1_short](../../../../../includes/net-v35sp1-short-md.md)] ou uma versão posterior.  
  
 Os valores no exemplo são os valores padrão.  
  
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
