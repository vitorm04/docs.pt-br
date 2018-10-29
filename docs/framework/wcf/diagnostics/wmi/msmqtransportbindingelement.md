---
title: MsmqTransportBindingElement
ms.date: 03/30/2017
ms.assetid: 1c89f073-9ed3-4025-a8c5-13535a0f526b
ms.openlocfilehash: 33cd9c427ed5ad04eaf9e9889f60f091f335d1e7
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/28/2018
ms.locfileid: "50198101"
---
# <a name="msmqtransportbindingelement"></a>MsmqTransportBindingElement
MsmqTransportBindingElement  
  
## <a name="syntax"></a>Sintaxe  
  
```csharp
class MsmqTransportBindingElement : MsmqBindingElementBase  
{  
  sint32 MaxPoolSize;  
  string QueueTransferProtocol;  
  boolean UseActiveDirectory;  
};  
```  
  
## <a name="methods"></a>Métodos  
 A classe MsmqTransportBindingElement não define quaisquer métodos.  
  
## <a name="properties"></a>Propriedades  
 A classe MsmqTransportBindingElement tem as seguintes propriedades:  
  
### <a name="maxpoolsize"></a>MaxPoolSize  
 Tipo de dados: sint32  
  
 Tipo de acesso: somente leitura  
  
 O tamanho máximo do pool que contém objetos de mensagem MSMQ internos.  
  
### <a name="queuetransferprotocol"></a>queueTransferProtocol  
 Tipo de dados: cadeia de caracteres  
  
 Tipo de acesso: somente leitura  
  
 Um valor de enumeração que indica o transporte de canal de comunicação em fila que esta associação usa.  
  
### <a name="useactivedirectory"></a>UseActiveDirectory  
 Tipo de dados: boolean  
  
 Tipo de acesso: somente leitura  
  
 Retorna um valor booliano que indica se os endereços da fila devem ser convertidos usando o Active Directory.  
  
## <a name="requirements"></a>Requisitos  
  
|MOF|Declarado em Servicemodel.mof.|  
|---------|-----------------------------------|  
|Namespace|Definido no root\ServiceModel|  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Channels.MsmqTransportBindingElement>
