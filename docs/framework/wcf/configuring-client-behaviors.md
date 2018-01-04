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
# <a name="configuring-client-behaviors"></a>Configurando comportamentos do cliente
[!INCLUDE[indigo1](../../../includes/indigo1-md.md)]configura os comportamentos de duas maneiras: referindo-se às configurações de comportamento – que são definidas no `<behavior>` seção de um arquivo de configuração do aplicativo de cliente – ou por meio de programação do aplicativo de chamada. Este tópico descreve as duas abordagens.  
  
 Ao usar um arquivo de configuração, a configuração de comportamento é uma coleção nomeada de definições de configuração. O nome de cada configuração de comportamento deve ser exclusivo. Essa cadeia de caracteres é usada no `behaviorConfiguration` atributo de uma configuração de ponto de extremidade para vincular o ponto de extremidade para o comportamento.  
  
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
  
## <a name="using-behaviors-programmatically"></a>Usando comportamentos programaticamente  
 Você também pode configurar ou inserir comportamentos programaticamente Localizando apropriada `Behaviors` propriedade o [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] objeto de cliente ou o objeto de fábrica de canal do cliente antes da abertura do cliente.  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir mostra como inserir programaticamente um comportamento acessando o <xref:System.ServiceModel.Description.ServiceEndpoint.Behaviors%2A> propriedade o <xref:System.ServiceModel.Description.ServiceEndpoint> retornado do <xref:System.ServiceModel.ChannelFactory.Endpoint%2A> propriedade antes da criação do objeto do canal.  
  
 [!code-csharp[ChannelFactoryBehaviors#10](../../../samples/snippets/csharp/VS_Snippets_CFX/channelfactorybehaviors/cs/client.cs#10)]
 [!code-vb[ChannelFactoryBehaviors#10](../../../samples/snippets/visualbasic/VS_Snippets_CFX/channelfactorybehaviors/vb/client.vb#10)]  
  
## <a name="see-also"></a>Consulte também  
 [\<comportamentos >](../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)
