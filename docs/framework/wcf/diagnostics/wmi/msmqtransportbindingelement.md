---
title: MsmqTransportBindingElement
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1c89f073-9ed3-4025-a8c5-13535a0f526b
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c4cfa3d58127fa560f39ce0dcfe51b97ded6223a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="msmqtransportbindingelement"></a>MsmqTransportBindingElement
MsmqTransportBindingElement  
  
## <a name="syntax"></a>Sintaxe  
  
```  
class MsmqTransportBindingElement : MsmqBindingElementBase  
{  
  sint32 MaxPoolSize;  
  string QueueTransferProtocol;  
  boolean UseActiveDirectory;  
};  
```  
  
## <a name="methods"></a>Métodos  
 A classe MsmqTransportBindingElement não define nenhum método.  
  
## <a name="properties"></a>Propriedades  
 A classe MsmqTransportBindingElement tem as seguintes propriedades:  
  
### <a name="maxpoolsize"></a>MaxPoolSize  
 Tipo de dados: sint32  
  
 Tipo de acesso: somente leitura  
  
 O tamanho máximo do pool que contém objetos de mensagem MSMQ internos.  
  
### <a name="queuetransferprotocol"></a>QueueTransferProtocol  
 Tipo de dados: cadeia de caracteres  
  
 Tipo de acesso: somente leitura  
  
 Um valor de enumeração que indica o transporte de canal de comunicação em fila que esta associação usa.  
  
### <a name="useactivedirectory"></a>Propriedade UseActiveDirectory  
 Tipo de dados: boolean  
  
 Tipo de acesso: somente leitura  
  
 Retorna um valor booliano que indica se os endereços da fila devem ser convertidos usando o Active Directory.  
  
## <a name="requirements"></a>Requisitos  
  
|MOF|Declarado em Servicemodel.mof.|  
|---------|-----------------------------------|  
|Namespace|Definido em root\ServiceModel|  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Channels.MsmqTransportBindingElement>
