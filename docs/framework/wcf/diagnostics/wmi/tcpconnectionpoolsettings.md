---
title: TcpConnectionPoolSettings
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 19acfba3-c057-4dbc-bac7-8674d7844d83
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 04e6a457a9f4c3f93a52f851aafe70578b7d7444
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="tcpconnectionpoolsettings"></a>TcpConnectionPoolSettings
TcpConnectionPoolSettings  
  
## <a name="syntax"></a>Sintaxe  
  
```  
class TcpConnectionPoolSettings  
{  
  string GroupName;  
  datetime IdleTimeout;  
  datetime LeaseTimeout;  
  sint32 MaxOutboundConnectionsPerEndpoint;  
};  
```  
  
## <a name="methods"></a>Métodos  
 A classe TcpConnectionPoolSettings não define nenhum método.  
  
## <a name="properties"></a>Propriedades  
 A classe TcpConnectionPoolSettings tem as seguintes propriedades:  
  
### <a name="groupname"></a>Nome de grupo  
 Tipo de dados: cadeia de caracteres  
  
 Tipo de acesso: somente leitura  
  
 O nome do grupo do pool de conexão usado para o elemento de associação.  
  
### <a name="idletimeout"></a>IdleTimeout  
 Tipo de dados: datetime  
  
 Tipo de acesso: somente leitura  
  
 O tempo máximo que a conexão pode ficar ociosa antes de ser desconectada.  
  
### <a name="leasetimeout"></a>LeaseTimeout  
 Tipo de dados: datetime  
  
 Tipo de acesso: somente leitura  
  
 O tempo máximo para a operação de concessão seja concluída antes do tempo limite.  
  
### <a name="maxoutboundconnectionsperendpoint"></a>MaxOutboundConnectionsPerEndpoint  
 Tipo de dados: sint32  
  
 Tipo de acesso: somente leitura  
  
 O máximo de conexões de saída para cada ponto de extremidade.  
  
## <a name="requirements"></a>Requisitos  
  
|MOF|Declarado em Servicemodel.mof.|  
|---------|-----------------------------------|  
|Namespace|Definido em root\ServiceModel|  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Channels.TcpConnectionPoolSettings>
