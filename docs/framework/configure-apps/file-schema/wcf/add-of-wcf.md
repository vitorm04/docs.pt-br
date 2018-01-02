---
title: '&lt;adicionar&gt; WCF'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c196f6d7-77f6-4266-973c-305b2b4dd8a2
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f1e8dac13f98b79e84b1281dbeec85a2500936b6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ltaddgt-of-wcf"></a>&lt;adicionar&gt; WCF
Configure um participante de rastreamento que escuta para registros de rastreamento emissores de tempo de execução diretamente e processá-los de forma que ele foi configurado. Isso inclui a escrita em uma saída específica (por exemplo, arquivo, Console, ETW), processamento/agregando os registros ou qualquer outra combinação que pode ser necessária.  
  
 Para obter mais informações no controle de fluxo de trabalho e participantes de rastreamento, consulte [fluxo de trabalho de rastreamento e rastreamento](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md) e [participantes de rastreamento](../../../../../docs/framework/windows-workflow-foundation/tracking-participants.md).  
  
 \<System. ServiceModel >  
\<controle >  
\<os participantes >  
\<add>  
  
## <a name="syntax"></a>Sintaxe  
  
```xml
   <tracking>    <participants>       <add name="String"            profileName="String"           type="String" />    </participants> </tracking>
```

## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|name|Uma cadeia de caracteres que especifica o nome de um participante de rastreamento.|  
|profileName|Uma cadeia de caracteres que especifica o nome do perfil de rastreamento que define os registros de rastreamento o participante de rastreamento tiver assinado.|  
|tipo|Uma cadeia de caracteres que especifica o tipo de um participante de rastreamento.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<os participantes >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/participants.md)|Uma lista de participantes de rastreamento|  
  
## <a name="remarks"></a>Comentários  
 Os participantes de rastreamento são usados para obter os dados de rastreamento emissores de fluxo de trabalho e armazená-lo em mídias diferentes. Da mesma forma, qualquer pós-processamento no controle de que registros também podem ser realizados o participante de rastreamento.  
  
 Vários participantes de rastreamento podem consumir os eventos de rastreamento simultaneamente. Cada participante de rastreamento pode ser associado um perfil de controle diferentes.  
  
 Um participante de rastreamento padrão é fornecido, que grava os registros de rastreamento em uma sessão do ETW. O participante é configurado em um serviço de fluxo de trabalho adicionando um comportamento acompanhamento- específico em um arquivo de configuração. Ativar um participante de rastreamento de ETW permite controlar os registros a serem exibidos no visualizador de eventos. Se isso não atender aos requisitos, você também poderá escrever um participante de rastreamento personalizado.  
  
## <a name="example"></a>Exemplo  
 O exemplo de configuração a seguir mostra o participante de rastreamento ETW padrão que está sendo configurado no arquivo Web. config.  
  
 A Id de provedor que usa o participante de rastreamento ETW para gravar os registros de rastreamento ETW é definida na `<diagnostics>` seção. O participante de rastreamento tem um perfil associado a ele para especificar os registros de rastreamento que tiver assinado. Isso é definido pelo `profileName` atributo o `<add>` elemento. Depois que eles são definidos, o participante de rastreamento é adicionado para o `<etwTracking>` comportamento de serviço. Isso adicionará os participantes de rastreamento selecionado para extensões da instância de fluxo de trabalho, para que eles começam a receber os registros de rastreamento.  
  
```xml  
<configuration>   
  <system.web>   
    <compilation targetFrameworkMoniker=".NETFramework,Version=v4.0"/>   
  </system.web>   
  <system.serviceModel>   
    <diagnostics etwProviderId="52A3165D-4AD9-405C-B1E8-7D9A257EAC9F" />                
    <tracking>   
      <participants>   
        <add name="EtwTrackingParticipant"   
             type="System.Activities.Tracking.EtwTrackingParticipant, System.Activities, Version=4.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35"   
             profileName="HealthMonitoring_Tracking_Profile"/>   
      </participants>   
    </tracking>   
    <behaviors>   
      <serviceBehaviors>   
        <behavior>   
          <etwTracking profileName="Sample Tracking Profile"/>  
        </behavior>   
      </serviceBehaviors>   
    </behaviors>   
  </system.serviceModel>   
</configuration>  
```  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.TrackingSection>  
 <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior>  
 <xref:System.ServiceModel.Activities.Configuration.EtwTrackingBehaviorElement>  
 [Acompanhamento e rastreamento de fluxo de trabalho](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [Acompanhando participantes](../../../../../docs/framework/windows-workflow-foundation/tracking-participants.md)
