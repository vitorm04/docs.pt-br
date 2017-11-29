---
title: '&lt;serviceThrottling&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a337d064-1e64-4209-b4a9-db7fdb7e3eaf
caps.latest.revision: "22"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 6ba0f3a442e3598322f223be63b64a811c8f785a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="ltservicethrottlinggt"></a>&lt;serviceThrottling&gt;
Especifica o mecanismo de limitação de um serviço do Windows Communication Foundation (WCF).  
  
 \<sistema. ServiceModel >  
\<comportamentos >  
\<serviceBehaviors >  
\<comportamento >  
\<serviceThrottling >  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<serviceThrottling maxConcurrentCalls="Integer"  
    maxConcurrentInstances="Integer"  
    maxConcurrentSessions="Integer" />  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|maxConcurrentCalls|Um número inteiro positivo que limita o número de mensagens que são processadas atualmente por meio de um <xref:System.ServiceModel.ServiceHost>. As chamadas além do limite são enfileiradas. Definir esse valor como 0 é equivalente a defini-lo como Int32.MaxValue. O padrão é 16 * número de processadores.|  
|maxConcurrentInstances|Um número inteiro positivo que limita o número de objetos <xref:System.ServiceModel.InstanceContext> executados ao mesmo tempo em um <xref:System.ServiceModel.ServiceHost>. As solicitações para criar instâncias adicionais serão enfileiradas e concluídas quando um slot abaixo do limite ficar disponível. A opção é a soma de maxConcurrentSessions e MaxConcurrentCalls|  
|maxConcurrentSessions|Um número inteiro positivo que limita o número de sessões que um objeto <xref:System.ServiceModel.ServiceHost> pode aceitar.<br /><br /> O serviço aceitará conexões além do limite, mas somente os canais abaixo do limite estarão ativos (as mensagens são lidas do canal). Definir esse valor como 0 é equivalente a defini-lo como Int32.MaxValue. O padrão é 100 * contagem de processadores.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<comportamento >](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|Especifica um elemento de comportamento.|  
  
## <a name="remarks"></a>Comentários  
 Os controles de limitação colocam limites no número de chamadas simultâneas, instâncias ou sessões para evitar a sobrecarga de consumo de recursos.  
  
 Um rastreamento é gravado cada vez que o valor dos atributos é atingido. O primeiro rastreamento é gravado como um aviso.  
  
## <a name="example"></a>Exemplo  
 O seguinte exemplo de configuração especifica que o serviço limita o máximo de chamadas simultâneas para 2, e o número máximo de instâncias simultâneas para 10. Para obter um exemplo detalhado de executar este exemplo, consulte [limitação](../../../../../docs/framework/wcf/samples/throttling.md).  
  
```xml  
<behaviors>   
  <serviceBehaviors>   
    <behavior name="CalculatorServiceBehavior">   
      <serviceDebug includeExceptionDetailInFaults="False" />   
      <serviceMetadata httpGetEnabled="True"/>   
      <!-- Specify throttling behavior -->  
      <serviceThrottling maxConcurrentCalls="2"   
           maxConcurrentInstances="10"/>   
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Description.ServiceThrottlingBehavior>  
 <xref:System.ServiceModel.Configuration.ServiceThrottlingElement>  
 [Utilizando o ServiceThrottlingBehavior para desempenho do serviço WCF de controle](../../../../../docs/framework/wcf/feature-details/using-servicethrottlingbehavior-to-control-wcf-service-performance.md)
