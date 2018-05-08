---
title: Classe de canal
ms.date: 03/30/2017
ms.assetid: d9fae2ca-209c-4341-a0f5-6b79d1a67776
ms.openlocfilehash: 4b7c66560c0c136a258c527d8a681d491eb50aae
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="channel-class"></a>Classe de canal
Canal  
  
## <a name="syntax"></a>Sintaxe  
  
```  
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
 A classe de canal não define nenhum método.  
  
## <a name="properties"></a>Propriedades  
 A classe de canal tem as seguintes propriedades.  
  
### <a name="localaddress"></a>LocalAddress  
 Tipo de dados: cadeia de caracteres  
  
 Tipo de acesso: somente leitura  
  
 O ponto de extremidade local para o canal.  
  
### <a name="ref"></a>ref  
 Tipo de dados: ponto de extremidade  
  
 Tipo de acesso: somente leitura  
  
 Uma referência ao ponto de extremidade de canal se conecta ao.  
  
### <a name="remoteaddress"></a>RemoteAddress  
 Tipo de dados: cadeia de caracteres  
  
 Tipo de acesso: somente leitura  
  
 O endereço remoto associado ao canal.  
  
### <a name="sessionid"></a>SessionId  
 Tipo de dados: cadeia de caracteres  
  
 Tipo de acesso: somente leitura  
  
 A sessão atual Id, se houver.  
  
### <a name="type"></a>Tipo  
 Tipo de dados: cadeia de caracteres  
  
 Tipo de acesso: somente leitura  
  
 O tipo de canal.  
  
## <a name="requirements"></a>Requisitos  
  
|MOF|Declarado em Servicemodel.mof.|  
|---------|-----------------------------------|  
|Namespace|Definido em root\ServiceModel|  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Channels.ChannelBase>
