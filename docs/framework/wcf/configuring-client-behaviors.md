---
title: Configurando comportamentos do cliente
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: df5b32fa-e73b-4e8e-b66f-357c748e0173
ms.openlocfilehash: 83fdc77bd17115f9952f2ca6c494ed0eb873cd9c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61608769"
---
# <a name="configuring-client-behaviors"></a><span data-ttu-id="e7ed7-102">Configurando comportamentos do cliente</span><span class="sxs-lookup"><span data-stu-id="e7ed7-102">Configuring Client Behaviors</span></span>
<span data-ttu-id="e7ed7-103">Windows Communication Foundation (WCF) configura a comportamentos de duas maneiras: referindo-se às configurações de comportamento – que são definidas no `<behavior>` seção de um arquivo de configuração de aplicativo do cliente – ou programaticamente na chamada aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e7ed7-103">Windows Communication Foundation (WCF) configures behaviors in two ways: either by referring to behavior configurations -- which are defined in the `<behavior>` section of a client application configuration file – or programmatically in the calling application.</span></span> <span data-ttu-id="e7ed7-104">Este tópico descreve as duas abordagens.</span><span class="sxs-lookup"><span data-stu-id="e7ed7-104">This topic describes both approaches.</span></span>  
  
 <span data-ttu-id="e7ed7-105">Ao usar um arquivo de configuração, a configuração de comportamento é uma coleção nomeada de definições de configuração.</span><span class="sxs-lookup"><span data-stu-id="e7ed7-105">When using a configuration file, behavior configuration is a named collection of configuration settings.</span></span> <span data-ttu-id="e7ed7-106">O nome de cada configuração de comportamento deve ser exclusivo.</span><span class="sxs-lookup"><span data-stu-id="e7ed7-106">The name of each behavior configuration must be unique.</span></span> <span data-ttu-id="e7ed7-107">Essa cadeia é usada a `behaviorConfiguration` atributo de uma configuração de ponto de extremidade para vincular o ponto de extremidade para o comportamento.</span><span class="sxs-lookup"><span data-stu-id="e7ed7-107">This string is used in the `behaviorConfiguration` attribute of an endpoint configuration to link the endpoint to the behavior.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e7ed7-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e7ed7-108">Example</span></span>  
 <span data-ttu-id="e7ed7-109">O código de configuração a seguir define um comportamento chamado `myBehavior`.</span><span class="sxs-lookup"><span data-stu-id="e7ed7-109">The following configuration code defines a behavior called `myBehavior`.</span></span> <span data-ttu-id="e7ed7-110">O ponto de extremidade do cliente faz referência a esse comportamento no `behaviorConfiguration` atributo.</span><span class="sxs-lookup"><span data-stu-id="e7ed7-110">The client endpoint references this behavior in the `behaviorConfiguration` attribute.</span></span>  
  
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
  
## <a name="using-behaviors-programmatically"></a><span data-ttu-id="e7ed7-111">Usando comportamentos de forma programática</span><span class="sxs-lookup"><span data-stu-id="e7ed7-111">Using Behaviors Programmatically</span></span>  
 <span data-ttu-id="e7ed7-112">Você também pode configurar ou inserir comportamentos de forma programática, localizando apropriado `Behaviors` propriedade no objeto de cliente do Windows Communication Foundation (WCF) ou no objeto de fábrica de canal cliente antes da abertura do cliente.</span><span class="sxs-lookup"><span data-stu-id="e7ed7-112">You can also configure or insert behaviors programmatically by locating the appropriate `Behaviors` property on the Windows Communication Foundation (WCF) client object or on the client channel factory object prior to opening the client.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e7ed7-113">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e7ed7-113">Example</span></span>  
 <span data-ttu-id="e7ed7-114">O exemplo de código a seguir mostra como inserir programaticamente um comportamento, acessando o <xref:System.ServiceModel.Description.ServiceEndpoint.Behaviors%2A> propriedade no <xref:System.ServiceModel.Description.ServiceEndpoint> retornados do <xref:System.ServiceModel.ChannelFactory.Endpoint%2A> propriedade antes da criação do objeto de canal.</span><span class="sxs-lookup"><span data-stu-id="e7ed7-114">The following code example shows how to programmatically insert a behavior by accessing the <xref:System.ServiceModel.Description.ServiceEndpoint.Behaviors%2A> property on the <xref:System.ServiceModel.Description.ServiceEndpoint> returned from the <xref:System.ServiceModel.ChannelFactory.Endpoint%2A> property prior to the creation of the channel object.</span></span>  
  
 [!code-csharp[ChannelFactoryBehaviors#10](../../../samples/snippets/csharp/VS_Snippets_CFX/channelfactorybehaviors/cs/client.cs#10)]
 [!code-vb[ChannelFactoryBehaviors#10](../../../samples/snippets/visualbasic/VS_Snippets_CFX/channelfactorybehaviors/vb/client.vb#10)]  
  
## <a name="see-also"></a><span data-ttu-id="e7ed7-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e7ed7-115">See also</span></span>

- [<span data-ttu-id="e7ed7-116">\<behaviors></span><span class="sxs-lookup"><span data-stu-id="e7ed7-116">\<behaviors></span></span>](../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)
