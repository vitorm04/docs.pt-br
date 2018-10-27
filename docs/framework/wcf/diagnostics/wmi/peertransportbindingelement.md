---
title: PeerTransportBindingElement
ms.date: 03/30/2017
ms.assetid: 40bf6be2-8087-4cb3-a66c-408d53eb9269
ms.openlocfilehash: 58bf07b0429ca2435b5aae3683ef69951a10003e
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50185177"
---
# <a name="peertransportbindingelement"></a>PeerTransportBindingElement
PeerTransportBindingElement  
  
## <a name="syntax"></a>Sintaxe  
  
```csharp
class PeerTransportBindingElement : TransportBindingElement  
{  
  string ListenIPAddress;  
  sint32 Port;  
  PeerSecuritySettings Security;  
};  
```  
  
## <a name="methods"></a>Métodos  
 A classe PeerTransportBindingElement não define quaisquer métodos.  
  
## <a name="properties"></a>Propriedades  
 A classe PeerTransportBindingElement tem as seguintes propriedades:  
  
### <a name="listenipaddress"></a>listenIPAddress  
 Tipo de dados: cadeia de caracteres  
  
 Tipo de acesso: somente leitura  
  
 O endereço IP no qual o nó par escuta para mensagens.  
  
### <a name="port"></a>Porta  
 Tipo de dados: sint32  
  
 Tipo de acesso: somente leitura  
  
 A porta de interface de rede na qual o mensagens do canal de pares de processos de associação.  
  
### <a name="security"></a>Segurança  
 Tipo de dados: PeerSecuritySettings  
  
 Tipo de acesso: somente leitura  
  
 Configurações de segurança de transporte de par.  
  
## <a name="requirements"></a>Requisitos  
  
|MOF|Declarado em Servicemodel.mof.|  
|---------|-----------------------------------|  
|Namespace|Definido no root\ServiceModel|  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Channels.PeerTransportBindingElement>
