---
title: Convertendo um aplicativo NetTcpBinding em um aplicativo de canal par
ms.date: 03/30/2017
ms.assetid: d4137292-a923-4b8f-8594-42276f2d3ce2
ms.openlocfilehash: b89afbe59b73288ba357fa55ec5d55c1fb18352b
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65582794"
---
# <a name="converting-a-nettcpbinding-application-to-a-peer-channel-application"></a>Convertendo um aplicativo NetTcpBinding em um aplicativo de canal par
Você pode criar conexões entre os clientes que usam o [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)] usando associações que descrevem os parâmetros da conexão. Convertendo um aplicativo do .NET Framework para usar conexões ponto a ponto exige uma ligação que dá suporte a essa tecnologia, ao fazer conexões de cliente. Canal par fornece uma associação chamada <xref:System.ServiceModel.NetPeerTcpBinding>, que pode ser usado de maneira semelhante para o <xref:System.ServiceModel.NetTcpBinding>. As principais diferenças incluem a especificação de um serviço de resolvedor e definindo as configurações de segurança.  
  
 Se um aplicativo estiver usando o resolvedor padrão e configurações de segurança, converter um aplicativo normal baseada em cliente/servidor para usar o canal de mesmo nível envolve a alteração do nome da associação de "NetTcpBinding" para "NetPeerTcpBinding" na caixa de diálogo arquivo de configuração — você não precisa alterar a base de código do aplicativo.  
  
## <a name="see-also"></a>Consulte também

- [Compilando um aplicativo de canal par](../../../../docs/framework/wcf/feature-details/building-a-peer-channel-application.md)
- [Associações fornecidas pelo sistema](../../../../docs/framework/wcf/system-provided-bindings.md)
