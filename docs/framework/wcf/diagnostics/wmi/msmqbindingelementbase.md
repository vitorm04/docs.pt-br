---
title: MsmqBindingElementBase
ms.date: 03/30/2017
ms.assetid: 210d41ab-a2a4-4d7a-afd2-0916c08a4015
ms.openlocfilehash: e7f4cf41168bd1e5483524195e20541d896a6569
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50183185"
---
# <a name="msmqbindingelementbase"></a>MsmqBindingElementBase
MsmqBindingElementBase  
  
## <a name="syntax"></a>Sintaxe  
  
```csharp  
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
 A classe MsmqBindingElementBase não define quaisquer métodos.  
  
## <a name="properties"></a>Propriedades  
 A classe MsmqBindingElementBase tem as seguintes propriedades:  
  
### <a name="customdeadletterqueue"></a>customDeadLetterQueue  
 Tipo de dados: cadeia de caracteres  
  
 Tipo de acesso: somente leitura  
  
 Um URI que contém o local da fila de mensagens mortas de cada aplicativo, onde as mensagens que expiraram ou tiveram uma falha de transferência ou entrega são colocadas.  
  
### <a name="deadletterqueue"></a>deadLetterQueue  
 Tipo de dados: cadeia de caracteres  
  
 Tipo de acesso: somente leitura  
  
 Um valor de enumeração que indica o tipo de fila de mensagens mortas a ser usada.  
  
### <a name="durable"></a>duráveis  
 Tipo de dados: boolean  
  
 Tipo de acesso: somente leitura  
  
 Um valor que indica se as mensagens processadas por essa associação são duráveis ou voláteis.  
  
### <a name="exactlyonce"></a>exactlyOnce  
 Tipo de dados: boolean  
  
 Tipo de acesso: somente leitura  
  
 Um valor booliano que indica se as mensagens processadas por essa associação são recebidas exatamente uma vez.  
  
### <a name="maxretrycycles"></a>maxRetryCycles  
 Tipo de dados: sint32  
  
 Tipo de acesso: somente leitura  
  
 O número máximo de ciclos de repetição para tentar entregar mensagens para o aplicativo de recebimento.  
  
### <a name="receiveerrorhandling"></a>receiveErrorHandling  
 Tipo de dados: cadeia de caracteres  
  
 Tipo de acesso: somente leitura  
  
 As configurações para manipulação de mensagens suspeitas.  
  
### <a name="receiveretrycount"></a>receiveRetryCount  
 Tipo de dados: sint32  
  
 Tipo de acesso: somente leitura  
  
 O número máximo de repetição imediata tentativas em uma mensagem que é lida da fila de aplicativos.  
  
### <a name="retrycycledelay"></a>retryCycleDelay  
 Tipo de dados: datetime  
  
 Tipo de acesso: somente leitura  
  
 Um valor que indica o tempo de espera entre ciclos ao tentar entregar uma mensagem que não pôde ser entregue imediatamente.  
  
### <a name="timetolive"></a>timeToLive  
 Tipo de dados: datetime  
  
 Tipo de acesso: somente leitura  
  
 O intervalo de tempo que indica quanto tempo as mensagens processadas por essa associação pode ser na fila antes de expirarem.  
  
### <a name="usemsmqtracing"></a>useMsmqTracing  
 Tipo de dados: boolean  
  
 Tipo de acesso: somente leitura  
  
 Um valor booliano que indica se as mensagens processadas por essa associação deve ser rastreado.  
  
### <a name="usesourcejournal"></a>useSourceJournal  
 Tipo de dados: boolean  
  
 Tipo de acesso: somente leitura  
  
 Um valor booliano que indica se as cópias de mensagens processadas por essa associação devem ser armazenadas na fila de diário de origem.  
  
## <a name="requirements"></a>Requisitos  
  
|MOF|Declarado em Servicemodel.mof.|  
|---------|-----------------------------------|  
|Namespace|Definido no root\ServiceModel|  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.NetMsmqBinding>  
 <xref:System.ServiceModel.MsmqBindingBase>
