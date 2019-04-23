---
title: TransportBindingElement
ms.date: 03/30/2017
ms.assetid: 54ecfbee-53c0-410c-a7fa-a98f2e40c545
ms.openlocfilehash: bdb5ca7400a41dd724c2ad7fc76695a82874ded6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/22/2019
ms.locfileid: "59974169"
---
# <a name="transportbindingelement"></a>TransportBindingElement
TransportBindingElement  
  
## <a name="syntax"></a>Sintaxe  
  
```csharp
class TransportBindingElement : BindingElement  
{  
  boolean ManualAddressing;  
  sint64 MaxBufferPoolSize;  
  sint64 MaxReceivedMessageSize;  
  string Scheme;  
};  
```  
  
## <a name="methods"></a>Métodos  
 A classe de TransportBindingElement não define quaisquer métodos.  
  
## <a name="properties"></a>Propriedades  
 A classe de TransportBindingElement tem as seguintes propriedades:  
  
### <a name="manualaddressing"></a>ManualAddressing  
 Tipo de dados: boolean  
  
 Tipo de acesso: Somente leitura  
  
 Um valor booliano que especifica se o usuário deseja assumir o controle do endereçamento de mensagem.  
  
### <a name="maxbufferpoolsize"></a>MaxBufferPoolSize  
 Tipo de dados: sint64  
  
 Tipo de acesso: Somente leitura  
  
 O tamanho máximo do buffer do pool para a associação.  
  
### <a name="maxreceivedmessagesize"></a>MaxReceivedMessageSize  
 Tipo de dados: sint64  
  
 Tipo de acesso: Somente leitura  
  
 O tamanho máximo para uma mensagem que é processado por essa associação.  
  
### <a name="scheme"></a>Esquema  
 Tipo de dados: cadeia de caracteres  
  
 Tipo de acesso: Somente leitura  
  
 O esquema URI para o transporte.  
  
## <a name="requirements"></a>Requisitos  
  
|MOF|Declarado em Servicemodel.mof.|  
|---------|-----------------------------------|  
|Namespace|Definido no root\ServiceModel|  
  
## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.Channels.TransportBindingElement>
