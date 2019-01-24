---
title: Classe de canal
ms.date: 03/30/2017
ms.assetid: d9fae2ca-209c-4341-a0f5-6b79d1a67776
ms.openlocfilehash: 3fbf398cca7ae9adbbecb9439bf3cbd32eb03969
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54668386"
---
# <a name="channel-class"></a>Classe de canal
Canal  
  
## <a name="syntax"></a>Sintaxe  
  
```csharp
class Channel  
{  
  string LocalAddress;  
  Endpoint ref;  
  string RemoteAddress;  
  string SessionId;  
  string Type;  
};  
```  
  
## <a name="methods"></a>Métodos  
 A classe de canal não define quaisquer métodos.  
  
## <a name="properties"></a>Propriedades  
 A classe de canal tem as propriedades a seguir.  
  
### <a name="localaddress"></a>LocalAddress  
 Tipo de dados: cadeia de caracteres  
  
 Tipo de acesso: Somente leitura  
  
 O ponto de extremidade local para o canal.  
  
### <a name="ref"></a>ref  
 Tipo de dados: Ponto de extremidade  
  
 Tipo de acesso: Somente leitura  
  
 Uma referência para o ponto de extremidade do canal se conecta ao.  
  
### <a name="remoteaddress"></a>RemoteAddress  
 Tipo de dados: cadeia de caracteres  
  
 Tipo de acesso: Somente leitura  
  
 O endereço remoto associado ao canal.  
  
### <a name="sessionid"></a>SessionId  
 Tipo de dados: cadeia de caracteres  
  
 Tipo de acesso: Somente leitura  
  
 A sessão atual de Id, se houver.  
  
### <a name="type"></a>Tipo  
 Tipo de dados: cadeia de caracteres  
  
 Tipo de acesso: Somente leitura  
  
 O tipo de canal.  
  
## <a name="requirements"></a>Requisitos  
  
|MOF|Declarado em Servicemodel.mof.|  
|---------|-----------------------------------|  
|Namespace|Definido no root\ServiceModel|  
  
## <a name="see-also"></a>Consulte também
- <xref:System.ServiceModel.Channels.ChannelBase>
