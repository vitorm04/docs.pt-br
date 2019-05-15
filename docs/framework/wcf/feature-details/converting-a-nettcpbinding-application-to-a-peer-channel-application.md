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
# <a name="converting-a-nettcpbinding-application-to-a-peer-channel-application"></a><span data-ttu-id="eb1da-102">Convertendo um aplicativo NetTcpBinding em um aplicativo de canal par</span><span class="sxs-lookup"><span data-stu-id="eb1da-102">Converting a NetTcpBinding Application to a Peer Channel Application</span></span>
<span data-ttu-id="eb1da-103">Você pode criar conexões entre os clientes que usam o [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)] usando associações que descrevem os parâmetros da conexão.</span><span class="sxs-lookup"><span data-stu-id="eb1da-103">You can create connections between clients using the [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)] by using bindings that describe the parameters of the connection.</span></span> <span data-ttu-id="eb1da-104">Convertendo um aplicativo do .NET Framework para usar conexões ponto a ponto exige uma ligação que dá suporte a essa tecnologia, ao fazer conexões de cliente.</span><span class="sxs-lookup"><span data-stu-id="eb1da-104">Converting a .NET Framework application to use peer-to-peer connections requires a binding that supports this technology when making client connections.</span></span> <span data-ttu-id="eb1da-105">Canal par fornece uma associação chamada <xref:System.ServiceModel.NetPeerTcpBinding>, que pode ser usado de maneira semelhante para o <xref:System.ServiceModel.NetTcpBinding>.</span><span class="sxs-lookup"><span data-stu-id="eb1da-105">Peer Channel provides a binding called <xref:System.ServiceModel.NetPeerTcpBinding>, which you can use in a similar way to the <xref:System.ServiceModel.NetTcpBinding>.</span></span> <span data-ttu-id="eb1da-106">As principais diferenças incluem a especificação de um serviço de resolvedor e definindo as configurações de segurança.</span><span class="sxs-lookup"><span data-stu-id="eb1da-106">Key differences include specifying a resolver service and defining security settings.</span></span>  
  
 <span data-ttu-id="eb1da-107">Se um aplicativo estiver usando o resolvedor padrão e configurações de segurança, converter um aplicativo normal baseada em cliente/servidor para usar o canal de mesmo nível envolve a alteração do nome da associação de "NetTcpBinding" para "NetPeerTcpBinding" na caixa de diálogo arquivo de configuração — você não precisa alterar a base de código do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="eb1da-107">If an application is using the default resolver and security settings, converting a normal client/server-based application to use Peer Channel entails changing the name of the binding from "NetTcpBinding" to "NetPeerTcpBinding" in the application’s configuration file—you do not have to change the application code base.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb1da-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="eb1da-108">See also</span></span>

- [<span data-ttu-id="eb1da-109">Compilando um aplicativo de canal par</span><span class="sxs-lookup"><span data-stu-id="eb1da-109">Building a Peer Channel Application</span></span>](../../../../docs/framework/wcf/feature-details/building-a-peer-channel-application.md)
- [<span data-ttu-id="eb1da-110">Associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="eb1da-110">System-Provided Bindings</span></span>](../../../../docs/framework/wcf/system-provided-bindings.md)
