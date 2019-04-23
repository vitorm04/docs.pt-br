---
title: Configurando comportamentos do cliente
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: df5b32fa-e73b-4e8e-b66f-357c748e0173
ms.openlocfilehash: 83fdc77bd17115f9952f2ca6c494ed0eb873cd9c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59193649"
---
# <a name="configuring-client-behaviors"></a>Configurando comportamentos do cliente
Windows Communication Foundation (WCF) configura a comportamentos de duas maneiras: referindo-se às configurações de comportamento – que são definidas no `<behavior>` seção de um arquivo de configuração de aplicativo do cliente – ou programaticamente na chamada aplicativo. Este tópico descreve as duas abordagens.  
  
 Ao usar um arquivo de configuração, a configuração de comportamento é uma coleção nomeada de definições de configuração. O nome de cada configuração de comportamento deve ser exclusivo. Essa cadeia é usada a `behaviorConfiguration` atributo de uma configuração de ponto de extremidade para vincular o ponto de extremidade para o comportamento.  
  
## <a name="example"></a>Exemplo  
 O código de configuração a seguir define um comportamento chamado `myBehavior`. O ponto de extremidade do cliente faz referência a esse comportamento no `behaviorConfiguration` atributo.  
  
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
  
## <a name="using-behaviors-programmatically"></a>Usando comportamentos de forma programática  
 Você também pode configurar ou inserir comportamentos de forma programática, localizando apropriado `Behaviors` propriedade no objeto de cliente do Windows Communication Foundation (WCF) ou no objeto de fábrica de canal cliente antes da abertura do cliente.  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir mostra como inserir programaticamente um comportamento, acessando o <xref:System.ServiceModel.Description.ServiceEndpoint.Behaviors%2A> propriedade no <xref:System.ServiceModel.Description.ServiceEndpoint> retornados do <xref:System.ServiceModel.ChannelFactory.Endpoint%2A> propriedade antes da criação do objeto de canal.  
  
 [!code-csharp[ChannelFactoryBehaviors#10](../../../samples/snippets/csharp/VS_Snippets_CFX/channelfactorybehaviors/cs/client.cs#10)]
 [!code-vb[ChannelFactoryBehaviors#10](../../../samples/snippets/visualbasic/VS_Snippets_CFX/channelfactorybehaviors/vb/client.vb#10)]  
  
## <a name="see-also"></a>Consulte também

- [\<behaviors>](../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)
