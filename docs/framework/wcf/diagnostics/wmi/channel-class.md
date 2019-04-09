---
title: Classe de canal
ms.date: 03/30/2017
ms.assetid: d9fae2ca-209c-4341-a0f5-6b79d1a67776
ms.openlocfilehash: f60a3946617b0994db1ba9e9ddf43be863be81f9
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59128837"
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
