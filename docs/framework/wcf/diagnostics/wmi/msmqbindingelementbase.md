---
title: MsmqBindingElementBase
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 210d41ab-a2a4-4d7a-afd2-0916c08a4015
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 009596ee8fd7218a07487183d932e91dad07797c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="msmqbindingelementbase"></a>MsmqBindingElementBase
MsmqBindingElementBase  
  
## <a name="syntax"></a>Sintaxe  
  
```  
class MsmqBindingElementBase : TransportBindingElement  
{  
  string CustomDeadLetterQueue;  
  string DeadLetterQueue;  
  boolean Durable;  
  boolean ExactlyOnce;  
  sint32 MaxRetryCycles;  
  string ReceiveErrorHandling;  
  sint32 ReceiveRetryCount;  
  datetime RetryCycleDelay;  
  datetime TimeToLive;  
  boolean UseMsmqTracing;  
  boolean UseSourceJournal;  
};  
```  
  
## <a name="methods"></a>Métodos  
 A classe MsmqBindingElementBase não define nenhum método.  
  
## <a name="properties"></a>Propriedades  
 A classe MsmqBindingElementBase tem as seguintes propriedades:  
  
### <a name="customdeadletterqueue"></a>CustomDeadLetterQueue  
 Tipo de dados: cadeia de caracteres  
  
 Tipo de acesso: somente leitura  
  
 Um URI que contém o local da fila de mensagens mortas para cada aplicativo, onde as mensagens que expiraram ou tiveram uma falha de transferência ou entrega são colocadas.  
  
### <a name="deadletterqueue"></a>DeadLetterQueue  
 Tipo de dados: cadeia de caracteres  
  
 Tipo de acesso: somente leitura  
  
 Um valor de enumeração que indica o tipo de fila de mensagens mortas a usar.  
  
### <a name="durable"></a>duráveis  
 Tipo de dados: boolean  
  
 Tipo de acesso: somente leitura  
  
 Um valor que indica se as mensagens processadas por essa associação são duráveis ou voláteis.  
  
### <a name="exactlyonce"></a>ExactlyOnce  
 Tipo de dados: boolean  
  
 Tipo de acesso: somente leitura  
  
 Um valor booliano que indica se as mensagens processadas por essa associação serão recebidas exatamente uma vez.  
  
### <a name="maxretrycycles"></a>MaxRetryCycles  
 Tipo de dados: sint32  
  
 Tipo de acesso: somente leitura  
  
 O número máximo de ciclos de repetição para tentar entregar mensagens para o aplicativo receptor.  
  
### <a name="receiveerrorhandling"></a>ReceiveErrorHandling  
 Tipo de dados: cadeia de caracteres  
  
 Tipo de acesso: somente leitura  
  
 As configurações para manipulação de mensagens suspeitas.  
  
### <a name="receiveretrycount"></a>ReceiveRetryCount  
 Tipo de dados: sint32  
  
 Tipo de acesso: somente leitura  
  
 O número máximo de repetição imediatas tentativas em uma mensagem que é lida da fila de aplicativos.  
  
### <a name="retrycycledelay"></a>RetryCycleDelay  
 Tipo de dados: datetime  
  
 Tipo de acesso: somente leitura  
  
 Um valor que indica o tempo de espera entre os ciclos de tentativa de entregar uma mensagem que não pôde ser entregue imediatamente.  
  
### <a name="timetolive"></a>TimeToLive  
 Tipo de dados: datetime  
  
 Tipo de acesso: somente leitura  
  
 O intervalo de tempo que indica quanto tempo as mensagens processadas por essa associação pode ser na fila antes de expirarem.  
  
### <a name="usemsmqtracing"></a>UseMsmqTracing  
 Tipo de dados: boolean  
  
 Tipo de acesso: somente leitura  
  
 Um valor booliano que indica se as mensagens processadas por essa associação deve ser rastreado.  
  
### <a name="usesourcejournal"></a>UseSourceJournal  
 Tipo de dados: boolean  
  
 Tipo de acesso: somente leitura  
  
 Um valor booliano que indica se cópias de mensagens processadas por essa associação devem ser armazenadas na fila de diário de origem.  
  
## <a name="requirements"></a>Requisitos  
  
|MOF|Declarado em Servicemodel.mof.|  
|---------|-----------------------------------|  
|Namespace|Definido em root\ServiceModel|  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.NetMsmqBinding>  
 <xref:System.ServiceModel.MsmqBindingBase>
