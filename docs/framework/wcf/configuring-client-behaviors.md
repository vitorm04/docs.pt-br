---
title: Configurando comportamentos do cliente
description: 'Saiba mais sobre as duas maneiras pelas quais o WCF configura comportamentos: no arquivo de configuração do aplicativo ou programaticamente do aplicativo de chamada.'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: df5b32fa-e73b-4e8e-b66f-357c748e0173
ms.openlocfilehash: 4b83862221cf249455478c3ade159a3101062f3e
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85245434"
---
# <a name="configuring-client-behaviors"></a><span data-ttu-id="4ccbf-103">Configurando comportamentos do cliente</span><span class="sxs-lookup"><span data-stu-id="4ccbf-103">Configuring Client Behaviors</span></span>
<span data-ttu-id="4ccbf-104">O Windows Communication Foundation (WCF) configura comportamentos de duas maneiras: seja referindo-se a configurações de comportamento, que são definidas na `<behavior>` seção de um arquivo de configuração de aplicativo cliente – ou programaticamente no aplicativo de chamada.</span><span class="sxs-lookup"><span data-stu-id="4ccbf-104">Windows Communication Foundation (WCF) configures behaviors in two ways: either by referring to behavior configurations -- which are defined in the `<behavior>` section of a client application configuration file – or programmatically in the calling application.</span></span> <span data-ttu-id="4ccbf-105">Este tópico descreve as duas abordagens.</span><span class="sxs-lookup"><span data-stu-id="4ccbf-105">This topic describes both approaches.</span></span>  
  
 <span data-ttu-id="4ccbf-106">Ao usar um arquivo de configuração, a configuração de comportamento é uma coleção nomeada de definições de configuração.</span><span class="sxs-lookup"><span data-stu-id="4ccbf-106">When using a configuration file, behavior configuration is a named collection of configuration settings.</span></span> <span data-ttu-id="4ccbf-107">O nome de cada configuração de comportamento deve ser exclusivo.</span><span class="sxs-lookup"><span data-stu-id="4ccbf-107">The name of each behavior configuration must be unique.</span></span> <span data-ttu-id="4ccbf-108">Essa cadeia de caracteres é usada no `behaviorConfiguration` atributo de uma configuração de ponto de extremidade para vincular o ponto de extremidade ao comportamento.</span><span class="sxs-lookup"><span data-stu-id="4ccbf-108">This string is used in the `behaviorConfiguration` attribute of an endpoint configuration to link the endpoint to the behavior.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4ccbf-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4ccbf-109">Example</span></span>  
 <span data-ttu-id="4ccbf-110">O código de configuração a seguir define um comportamento chamado `myBehavior` .</span><span class="sxs-lookup"><span data-stu-id="4ccbf-110">The following configuration code defines a behavior called `myBehavior`.</span></span> <span data-ttu-id="4ccbf-111">O ponto de extremidade do cliente faz referência a esse comportamento no `behaviorConfiguration` atributo.</span><span class="sxs-lookup"><span data-stu-id="4ccbf-111">The client endpoint references this behavior in the `behaviorConfiguration` attribute.</span></span>  
  
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
  
## <a name="using-behaviors-programmatically"></a><span data-ttu-id="4ccbf-112">Usando comportamentos programaticamente</span><span class="sxs-lookup"><span data-stu-id="4ccbf-112">Using Behaviors Programmatically</span></span>  
 <span data-ttu-id="4ccbf-113">Você também pode configurar ou inserir comportamentos programaticamente, localizando a `Behaviors` propriedade apropriada no objeto de cliente Windows Communication Foundation (WCF) ou no objeto de fábrica de canais do cliente antes de abrir o cliente.</span><span class="sxs-lookup"><span data-stu-id="4ccbf-113">You can also configure or insert behaviors programmatically by locating the appropriate `Behaviors` property on the Windows Communication Foundation (WCF) client object or on the client channel factory object prior to opening the client.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4ccbf-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4ccbf-114">Example</span></span>  
 <span data-ttu-id="4ccbf-115">O exemplo de código a seguir mostra como inserir programaticamente um comportamento acessando a <xref:System.ServiceModel.Description.ServiceEndpoint.Behaviors%2A> propriedade no <xref:System.ServiceModel.Description.ServiceEndpoint> retornado da <xref:System.ServiceModel.ChannelFactory.Endpoint%2A> propriedade antes da criação do objeto de canal.</span><span class="sxs-lookup"><span data-stu-id="4ccbf-115">The following code example shows how to programmatically insert a behavior by accessing the <xref:System.ServiceModel.Description.ServiceEndpoint.Behaviors%2A> property on the <xref:System.ServiceModel.Description.ServiceEndpoint> returned from the <xref:System.ServiceModel.ChannelFactory.Endpoint%2A> property prior to the creation of the channel object.</span></span>  
  
 [!code-csharp[ChannelFactoryBehaviors#10](../../../samples/snippets/csharp/VS_Snippets_CFX/channelfactorybehaviors/cs/client.cs#10)]
 [!code-vb[ChannelFactoryBehaviors#10](../../../samples/snippets/visualbasic/VS_Snippets_CFX/channelfactorybehaviors/vb/client.vb#10)]  
  
## <a name="see-also"></a><span data-ttu-id="4ccbf-116">Confira também</span><span class="sxs-lookup"><span data-stu-id="4ccbf-116">See also</span></span>

- [\<behaviors>](../configure-apps/file-schema/wcf/behaviors.md)
