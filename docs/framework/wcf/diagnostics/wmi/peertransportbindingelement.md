---
title: PeerTransportBindingElement
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 40bf6be2-8087-4cb3-a66c-408d53eb9269
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 48364c2bcfa50476ac5f9f00f87c17f97dc14017
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="peertransportbindingelement"></a>PeerTransportBindingElement
PeerTransportBindingElement  
  
## <a name="syntax"></a>Sintaxe  
  
```  
class PeerTransportBindingElement : TransportBindingElement  
{  
  string ListenIPAddress;  
  sint32 Port;  
  PeerSecuritySettings Security;  
};  
```  
  
## <a name="methods"></a>Métodos  
 A classe PeerTransportBindingElement não define nenhum método.  
  
## <a name="properties"></a>Propriedades  
 A classe PeerTransportBindingElement tem as seguintes propriedades:  
  
### <a name="listenipaddress"></a>listenIPAddress  
 Tipo de dados: cadeia de caracteres  
  
 Tipo de acesso: somente leitura  
  
 O endereço IP no qual o nó par escuta as mensagens.  
  
### <a name="port"></a>Porta  
 Tipo de dados: sint32  
  
 Tipo de acesso: somente leitura  
  
 A porta de interface de rede no qual essa processos de associação pares de mensagens do canal.  
  
### <a name="security"></a>Segurança  
 Tipo de dados: PeerSecuritySettings  
  
 Tipo de acesso: somente leitura  
  
 Configurações de segurança de transporte ponto a ponto.  
  
## <a name="requirements"></a>Requisitos  
  
|MOF|Declarado em Servicemodel.mof.|  
|---------|-----------------------------------|  
|Namespace|Definido em root\ServiceModel|  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Channels.PeerTransportBindingElement>
