---
title: Convertendo um aplicativo NetTcpBinding em um aplicativo de canal par
ms.date: 03/30/2017
ms.assetid: d4137292-a923-4b8f-8594-42276f2d3ce2
ms.openlocfilehash: 42266d8c7c04e2d8f3f1e4734d9a05181c3f1ea3
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84595551"
---
# <a name="converting-a-nettcpbinding-application-to-a-peer-channel-application"></a><span data-ttu-id="96d43-102">Convertendo um aplicativo NetTcpBinding em um aplicativo de canal par</span><span class="sxs-lookup"><span data-stu-id="96d43-102">Converting a NetTcpBinding Application to a Peer Channel Application</span></span>
<span data-ttu-id="96d43-103">Você pode criar conexões entre clientes usando o WinFX usando associações que descrevem os parâmetros da conexão.</span><span class="sxs-lookup"><span data-stu-id="96d43-103">You can create connections between clients using the WinFX by using bindings that describe the parameters of the connection.</span></span> <span data-ttu-id="96d43-104">Converter um aplicativo .NET Framework para usar conexões ponto a ponto requer uma associação que dá suporte a essa tecnologia ao fazer conexões de cliente.</span><span class="sxs-lookup"><span data-stu-id="96d43-104">Converting a .NET Framework application to use peer-to-peer connections requires a binding that supports this technology when making client connections.</span></span> <span data-ttu-id="96d43-105">O canal par fornece uma associação chamada <xref:System.ServiceModel.NetPeerTcpBinding> , que pode ser usada de forma semelhante ao <xref:System.ServiceModel.NetTcpBinding> .</span><span class="sxs-lookup"><span data-stu-id="96d43-105">Peer Channel provides a binding called <xref:System.ServiceModel.NetPeerTcpBinding>, which you can use in a similar way to the <xref:System.ServiceModel.NetTcpBinding>.</span></span> <span data-ttu-id="96d43-106">As principais diferenças incluem a especificação de um serviço de resolvedor e a definição de configurações de segurança.</span><span class="sxs-lookup"><span data-stu-id="96d43-106">Key differences include specifying a resolver service and defining security settings.</span></span>  
  
 <span data-ttu-id="96d43-107">Se um aplicativo estiver usando o resolvedor padrão e as configurações de segurança, converter um aplicativo normal baseado em cliente/servidor para usar o canal de pares envolve alterar o nome da Associação de "NetTcpbinding" para "NetPeerTcpBinding" no arquivo de configuração do aplicativo — você não precisa alterar a base de código do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="96d43-107">If an application is using the default resolver and security settings, converting a normal client/server-based application to use Peer Channel entails changing the name of the binding from "NetTcpBinding" to "NetPeerTcpBinding" in the application’s configuration file—you do not have to change the application code base.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96d43-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="96d43-108">See also</span></span>

- [<span data-ttu-id="96d43-109">Compilando um aplicativo de canal par</span><span class="sxs-lookup"><span data-stu-id="96d43-109">Building a Peer Channel Application</span></span>](building-a-peer-channel-application.md)
- [<span data-ttu-id="96d43-110">Associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="96d43-110">System-Provided Bindings</span></span>](../system-provided-bindings.md)
