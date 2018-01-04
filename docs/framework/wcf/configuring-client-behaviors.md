---
title: Configurando comportamentos do cliente
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: df5b32fa-e73b-4e8e-b66f-357c748e0173
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ee79900b52ae0fa58e8fb9a5cbbf50f5a882c295
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="configuring-client-behaviors"></a><span data-ttu-id="40840-102">Configurando comportamentos do cliente</span><span class="sxs-lookup"><span data-stu-id="40840-102">Configuring Client Behaviors</span></span>
[!INCLUDE[indigo1](../../../includes/indigo1-md.md)]<span data-ttu-id="40840-103">configura os comportamentos de duas maneiras: referindo-se às configurações de comportamento – que são definidas no `<behavior>` seção de um arquivo de configuração do aplicativo de cliente – ou por meio de programação do aplicativo de chamada.</span><span class="sxs-lookup"><span data-stu-id="40840-103"> configures behaviors in two ways: either by referring to behavior configurations -- which are defined in the `<behavior>` section of a client application configuration file – or programmatically in the calling application.</span></span> <span data-ttu-id="40840-104">Este tópico descreve as duas abordagens.</span><span class="sxs-lookup"><span data-stu-id="40840-104">This topic describes both approaches.</span></span>  
  
 <span data-ttu-id="40840-105">Ao usar um arquivo de configuração, a configuração de comportamento é uma coleção nomeada de definições de configuração.</span><span class="sxs-lookup"><span data-stu-id="40840-105">When using a configuration file, behavior configuration is a named collection of configuration settings.</span></span> <span data-ttu-id="40840-106">O nome de cada configuração de comportamento deve ser exclusivo.</span><span class="sxs-lookup"><span data-stu-id="40840-106">The name of each behavior configuration must be unique.</span></span> <span data-ttu-id="40840-107">Essa cadeia de caracteres é usada no `behaviorConfiguration` atributo de uma configuração de ponto de extremidade para vincular o ponto de extremidade para o comportamento.</span><span class="sxs-lookup"><span data-stu-id="40840-107">This string is used in the `behaviorConfiguration` attribute of an endpoint configuration to link the endpoint to the behavior.</span></span>  
  
## <a name="example"></a><span data-ttu-id="40840-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="40840-108">Example</span></span>  
 <span data-ttu-id="40840-109">O código de configuração a seguir define um comportamento chamado `myBehavior`.</span><span class="sxs-lookup"><span data-stu-id="40840-109">The following configuration code defines a behavior called `myBehavior`.</span></span> <span data-ttu-id="40840-110">O ponto de extremidade do cliente faz referência a esse comportamento no `behaviorConfiguration` atributo.</span><span class="sxs-lookup"><span data-stu-id="40840-110">The client endpoint references this behavior in the `behaviorConfiguration` attribute.</span></span>  
  
```xml  
<configuration>  
    <system.serviceModel>  
        <behaviors>  
            <endpointBehaviors>  
                <behavior name="myBehavior">  
                    <clientVia />  
                </behavior>  
            </endpointBehaviors>  
        </behaviors>  
        <bindings>  
            <basicHttpBinding>  
                <binding name="myBinding" maxReceivedMessageSize="10000" />  
            </basicHttpBinding>  
        </bindings>  
        <client>  
            <endpoint address="myAddress" binding="basicHttpBinding" bindingConfiguration="myBinding" behaviorConfiguration="myBehavior" contract="myContract" />  
        </client>  
    </system.serviceModel>  
</configuration>  
```  
  
## <a name="using-behaviors-programmatically"></a><span data-ttu-id="40840-111">Usando comportamentos programaticamente</span><span class="sxs-lookup"><span data-stu-id="40840-111">Using Behaviors Programmatically</span></span>  
 <span data-ttu-id="40840-112">Você também pode configurar ou inserir comportamentos programaticamente Localizando apropriada `Behaviors` propriedade o [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] objeto de cliente ou o objeto de fábrica de canal do cliente antes da abertura do cliente.</span><span class="sxs-lookup"><span data-stu-id="40840-112">You can also configure or insert behaviors programmatically by locating the appropriate `Behaviors` property on the [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] client object or on the client channel factory object prior to opening the client.</span></span>  
  
## <a name="example"></a><span data-ttu-id="40840-113">Exemplo</span><span class="sxs-lookup"><span data-stu-id="40840-113">Example</span></span>  
 <span data-ttu-id="40840-114">O exemplo de código a seguir mostra como inserir programaticamente um comportamento acessando o <xref:System.ServiceModel.Description.ServiceEndpoint.Behaviors%2A> propriedade o <xref:System.ServiceModel.Description.ServiceEndpoint> retornado do <xref:System.ServiceModel.ChannelFactory.Endpoint%2A> propriedade antes da criação do objeto do canal.</span><span class="sxs-lookup"><span data-stu-id="40840-114">The following code example shows how to programmatically insert a behavior by accessing the <xref:System.ServiceModel.Description.ServiceEndpoint.Behaviors%2A> property on the <xref:System.ServiceModel.Description.ServiceEndpoint> returned from the <xref:System.ServiceModel.ChannelFactory.Endpoint%2A> property prior to the creation of the channel object.</span></span>  
  
 [!code-csharp[ChannelFactoryBehaviors#10](../../../samples/snippets/csharp/VS_Snippets_CFX/channelfactorybehaviors/cs/client.cs#10)]
 [!code-vb[ChannelFactoryBehaviors#10](../../../samples/snippets/visualbasic/VS_Snippets_CFX/channelfactorybehaviors/vb/client.vb#10)]  
  
## <a name="see-also"></a><span data-ttu-id="40840-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="40840-115">See Also</span></span>  
 [<span data-ttu-id="40840-116">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="40840-116">\<behaviors></span></span>](../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)
