---
title: PeerTransportBindingElement
ms.date: 03/30/2017
ms.assetid: 40bf6be2-8087-4cb3-a66c-408d53eb9269
ms.openlocfilehash: ba9031dad96f12c7c48b03f1da4af1b3adc6dd4f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/22/2019
ms.locfileid: "59980428"
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
  
### <a name="listenipaddress"></a>ListenIPAddress  
 Tipo de dados: cadeia de caracteres  
  
 Tipo de acesso: Somente leitura  
  
 O endereço IP no qual o nó par escuta para mensagens.  
  
### <a name="port"></a>Porta  
 Tipo de dados: sint32  
  
 Tipo de acesso: Somente leitura  
  
 A porta de interface de rede na qual o mensagens do canal de pares de processos de associação.  
  
### <a name="security"></a>Segurança  
 Tipo de dados: PeerSecuritySettings  
  
 Tipo de acesso: Somente leitura  
  
 Configurações de segurança de transporte de par.  
  
## <a name="requirements"></a>Requisitos  
  
|MOF|Declarado em Servicemodel.mof.|  
|---------|-----------------------------------|  
|Namespace|Definido no root\ServiceModel|  
  
## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.Channels.PeerTransportBindingElement>
