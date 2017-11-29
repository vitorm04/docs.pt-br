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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: c130093b9600c324e7179febce6857341b8a7d3c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
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
