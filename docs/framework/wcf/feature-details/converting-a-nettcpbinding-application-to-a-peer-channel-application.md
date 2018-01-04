---
title: Convertendo um aplicativo NetTcpBinding em um aplicativo de canal par
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d4137292-a923-4b8f-8594-42276f2d3ce2
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1ee46e34aea14c4ee9ce23c807170104173f2704
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="converting-a-nettcpbinding-application-to-a-peer-channel-application"></a>Convertendo um aplicativo NetTcpBinding em um aplicativo de canal par
Você pode criar conexões entre os clientes que usam o [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)] usando associações que descrevem os parâmetros de conexão. Convertendo um [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] aplicativo para usar conexões ponto a ponto requer uma associação que dá suporte a essa tecnologia ao fazer conexões de cliente. Canal par fornece uma associação chamada <xref:System.ServiceModel.NetPeerTcpBinding>, que pode ser usado de maneira semelhante para o <xref:System.ServiceModel.NetTcpBinding>. Principais diferenças incluem especificar um serviço de resolução e definir as configurações de segurança.  
  
 Se um aplicativo está usando o resolvedor padrão e as configurações de segurança, convertendo um aplicativo baseado em cliente/servidor normal para usar o canal par envolve a alteração do nome da associação de "NetTcpBinding" para "NetPeerTcpBinding" do aplicativo arquivo de configuração, você não precisa alterar a base de código do aplicativo.  
  
## <a name="see-also"></a>Consulte também  
 [Compilando um aplicativo de canal par](../../../../docs/framework/wcf/feature-details/building-a-peer-channel-application.md)  
 [Associações fornecidas pelo sistema](../../../../docs/framework/wcf/system-provided-bindings.md)
