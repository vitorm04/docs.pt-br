---
title: TransportBindingElement
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 54ecfbee-53c0-410c-a7fa-a98f2e40c545
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c2605e1a1f88434a9052059ac3ebdce429d6d6c8
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="transportbindingelement"></a>TransportBindingElement
TransportBindingElement  
  
## <a name="syntax"></a>Sintaxe  
  
```  
class TransportBindingElement : BindingElement  
{  
  boolean ManualAddressing;  
  sint64 MaxBufferPoolSize;  
  sint64 MaxReceivedMessageSize;  
  string Scheme;  
};  
```  
  
## <a name="methods"></a>Métodos  
 A classe de TransportBindingElement não define nenhum método.  
  
## <a name="properties"></a>Propriedades  
 A classe de TransportBindingElement tem as seguintes propriedades:  
  
### <a name="manualaddressing"></a>manualAddressing  
 Tipo de dados: boolean  
  
 Tipo de acesso: somente leitura  
  
 Um valor booleano que especifica se o usuário deseja assumir o controle do endereçamento da mensagem.  
  
### <a name="maxbufferpoolsize"></a>maxBufferPoolSize  
 Tipo de dados: sint64  
  
 Tipo de acesso: somente leitura  
  
 O tamanho do pool de buffer máximo para a associação.  
  
### <a name="maxreceivedmessagesize"></a>maxReceivedMessageSize  
 Tipo de dados: sint64  
  
 Tipo de acesso: somente leitura  
  
 O tamanho máximo para uma mensagem que é processada por essa associação.  
  
### <a name="scheme"></a>Esquema  
 Tipo de dados: cadeia de caracteres  
  
 Tipo de acesso: somente leitura  
  
 O esquema URI para o transporte.  
  
## <a name="requirements"></a>Requisitos  
  
|MOF|Declarado em Servicemodel.mof.|  
|---------|-----------------------------------|  
|Namespace|Definido em root\ServiceModel|  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Channels.TransportBindingElement>
