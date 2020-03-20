---
title: Elemento <applicationPool> (configurações da Web)
ms.date: 03/30/2017
helpviewer_keywords:
- applicationPool element
- <applicationPool> element
ms.assetid: 46d1baaa-e343-4639-b70d-2a43a9f62b2a
ms.openlocfilehash: 6feaa801610fa0ffbbf47575f25aff29fa46a66c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152848"
---
# <a name="applicationpool-element-web-settings"></a>\<applicationPool> Element (Web Settings) [Elemento applicationPool> (configurações da Web)]
Especifica as configurações usadas por ASP.NET para gerenciar o comportamento em todo o processo quando um aplicativo ASP.NET está sendo executado no modo Integrado no IIS 7.0 ou em uma versão posterior.  
  
> [!IMPORTANT]
> Esse elemento e o recurso que ele suporta só funcionam se o aplicativo ASP.NET estiver hospedado nas versões IIS 7.0 ou posteriores.  
  
[**\<>de configuração**](../configuration-element.md)  
&nbsp;&nbsp;[**\<system.web>**](system-web-element-web-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;**\<>de pool de aplicativos**  
  
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
|`maxConcurrentRequestsPerCPU`|Especifica quantas solicitações simultâneas ASP.NET permite por CPU.|  
|`maxConcurrentThreadsPerCPU`|Especifica quantos threads simultâneos podem ser executados para um pool de aplicativos para cada CPU. Isso fornece uma maneira alternativa de controlar ASP.NET simultâneo, porque você pode limitar o número de threads gerenciados que podem ser usados por CPU para atender solicitações. Por padrão, essa configuração é 0, o que significa que ASP.NET não limita o número de threads que podem ser criados por CPU, embora o pool de threads CLR também limite o número de threads que podem ser criados.|  
|`requestQueueLimit`|Especifica o número máximo de solicitações que podem ser enfileiradas para ASP.NET em um único processo. Quando dois ou mais aplicativos ASP.NET são executados em um único pool de aplicativos, o conjunto cumulativo de solicitações que estão sendo feitas a qualquer aplicativo no pool de aplicativos está sujeito a essa configuração.|  
  
### <a name="child-elements"></a>Elementos filho  
 Nenhum.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<system.web>](system-web-element-web-settings.md)|Contém informações sobre como ASP.NET interage com um aplicativo host.|  
  
## <a name="remarks"></a>Comentários  

Quando você executa o IIS 7.0 ou uma versão posterior no modo Integrado, essa combinação de elementos permite configurar como ASP.NET gerencia threads e filas de solicitações quando o aplicativo está hospedado em um pool de aplicativos IIS. Se você executar o IIS 6 ou executar o IIS 7.0 no modo Classic ou no modo ISAPI, essas configurações serão ignoradas.  
  
As `applicationPool` configurações se aplicam a todos os pools de aplicativos executados em uma versão específica do .NET Framework. As configurações estão contidas em um arquivo aspnet.config. Há uma versão deste arquivo para as versões 2.0 e 4.0 do .NET Framework. (As versões 3.0 e 3.5 do .NET Framework compartilham o arquivo aspnet.config com a versão 2.0.)  
  
> [!IMPORTANT]
> Se você executar o IIS 7.0 no Windows 7, você poderá configurar um arquivo aspnet.config separado para cada pool de aplicativos. Isso permite que você adapte o desempenho dos threads para cada pool de aplicativos.  
  
Para `maxConcurrentRequestsPerCPU` a configuração, a configuração padrão de "5000" no Quadro .NET 4 efetivamente desliga o estrangulamento da solicitação que é controlada por ASP.NET, a menos que você realmente tenha 5000 ou mais solicitações por CPU. A configuração padrão depende, em vez disso, do pool de threads CLR para gerenciar automaticamente a concorrência por CPU. Os aplicativos que fazem uso extensivo do processamento de solicitações assíncronas, ou que têm muitas solicitações de longo prazo bloqueadas na I/O da rede, se beneficiarão do limite de inadimplência aumentado no Quadro .NET 4. A `maxConcurrentRequestsPerCPU` configuração para zero desliga o uso de threads gerenciados para processar ASP.NET solicitações. Quando um aplicativo é executado em um pool de aplicativos IIS, as solicitações permanecem no segmento IIS I/O e, portanto, a concorrência é estrangulada pelas configurações de rosca do IIS.  
  
A `requestQueueLimit` configuração funciona da `requestQueueLimit` mesma forma que o atributo do elemento [processModel,](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7w2sway1(v=vs.100)) que é definido nos arquivos Web.config para aplicativos ASP.NET. No entanto, a `requestQueueLimit` configuração em um arquivo `requestQueueLimit` aspnet.config substitui a configuração em um arquivo Web.config. Em outras palavras, se ambos os atributos forem definidos (por padrão, isso é verdade), a `requestQueueLimit` configuração no arquivo aspnet.config tem precedência.  
  
## <a name="example"></a>Exemplo  

O exemplo a seguir mostra como configurar ASP.NET comportamento em todo o processo no arquivo aspnet.config nas seguintes circunstâncias:  
  
- O aplicativo está hospedado em um pool de aplicativos IIS 7.0.  
  
- O IIS 7.0 está sendo executado no modo Integrado.  
  
- O aplicativo está usando o .NET Framework 3.5 SP1 ou uma versão posterior.  
  
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
|Nome do Esquema||  
|Arquivo de validação||  
|Pode ser vazio||  
  
## <a name="see-also"></a>Confira também

- [\<system.web> Element (Configurações da Web)](system-web-element-web-settings.md)
