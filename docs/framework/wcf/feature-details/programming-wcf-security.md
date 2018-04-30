---
title: Programação de segurança do WCF
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- message security [WCF], programming overview
ms.assetid: 739ec222-4eda-4cc9-a470-67e64a7a3f10
caps.latest.revision: 25
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload:
- dotnet
ms.openlocfilehash: 63f5c2c61a374b92b018419c83c9429e6ad796d8
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/30/2018
---
# <a name="programming-wcf-security"></a>Programação de segurança do WCF
Este tópico descreve as tarefas de programação fundamentais usadas para criar um site seguro [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] aplicativo. Este tópico aborda somente autenticação, confidencialidade e integridade, coletivamente conhecido como *transferir segurança*. Este tópico não abrange a autorização (o controle de acesso aos recursos ou serviços); Para obter informações sobre autorização, consulte [autorização](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md).  
  
> [!NOTE]
>  Para obter uma introdução valiosa para conceitos de segurança, especialmente em relação ao [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], consulte o conjunto de padrões e práticas recomendadas tutoriais no MSDN em [cenários, padrões e diretrizes de implementação para aprimoramentos de WSE (Web Services) 3.0](http://go.microsoft.com/fwlink/?LinkID=88250).  
  
 Programação [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] é baseada em três etapas de configuração a seguir: o modo de segurança, um tipo de credencial de cliente e os valores de credencial. Você pode executar essas etapas por meio de código ou de configuração.  
  
## <a name="setting-the-security-mode"></a>Configurando o modo de segurança  
 A seguir explica as etapas gerais para programação com o modo de segurança no [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]:  
  
1.  Selecione uma das associações predefinidas adequadas aos seus requisitos de aplicativo. Para obter uma lista das opções de associação, consulte [System-Provided associações](../../../../docs/framework/wcf/system-provided-bindings.md). Por padrão, quase todas as associações tem segurança habilitada. A única exceção é o <xref:System.ServiceModel.BasicHttpBinding> classe (usando a configuração, o [ \<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)).  
  
     A associação que você seleciona determina o transporte. Por exemplo, <xref:System.ServiceModel.WSHttpBinding> usa HTTP como o transporte; <xref:System.ServiceModel.NetTcpBinding> usa o TCP.  
  
2.  Selecione um dos modos de segurança para a associação. Observe que a associação que você seleciona determina as opções de modo disponível. Por exemplo, o <xref:System.ServiceModel.WSDualHttpBinding> não permite que a segurança de transporte (não é uma opção). Da mesma forma, não o <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> nem o <xref:System.ServiceModel.NetNamedPipeBinding> permite que a segurança de mensagem.  
  
     Você tem três opções:  
  
    1.  `Transport`  
  
         Segurança de transporte depende do mecanismo que usa a associação selecionada. Por exemplo, se você estiver usando `WSHttpBinding` , em seguida, o mecanismo de segurança é o protocolo (SSL) (também o mecanismo para o protocolo HTTPS). Em geral, a vantagem principal de segurança de transporte é que ele oferece uma taxa de transferência não importa qual transporte você está usando. No entanto, ele tem duas limitações: A primeira é que o mecanismo de transporte determina o tipo de credencial usado para autenticar um usuário. Isso é uma desvantagem somente se um serviço precisa interoperar com outros serviços que exigem tipos diferentes de credenciais. A segunda é que, como a segurança não é aplicada no nível da mensagem, a segurança é implementada em uma maneira de salto por salto em vez de ponta a ponta. Essa última limitação é um problema apenas se o caminho de mensagem entre cliente e serviço inclui intermediários. Para obter mais informações sobre qual transporte deve ser usado, consulte [selecionando um transporte](../../../../docs/framework/wcf/feature-details/choosing-a-transport.md). Para obter mais informações sobre como usar a segurança de transporte, consulte [visão geral de segurança de transporte](../../../../docs/framework/wcf/feature-details/transport-security-overview.md).  
  
    2.  `Message`  
  
         Segurança de mensagem significa que cada mensagem inclui os cabeçalhos necessários e seguro de dados para manter a mensagem. Como a composição dos cabeçalhos varia, você pode incluir qualquer número de credenciais. Isso é um fator importante, se você está interoperando com outros serviços que exigem um tipo de credencial específico que não pode fornecer um mecanismo de transporte, ou se a mensagem deve ser usada com mais de um serviço, em que cada serviço exige um tipo de credencial diferente.  
  
         Para obter mais informações, consulte [segurança de mensagem](../../../../docs/framework/wcf/feature-details/message-security-in-wcf.md).  
  
    3.  `TransportWithMessageCredential`  
  
         Essa opção usa a camada de transporte para proteger a transferência de mensagem, enquanto cada mensagem inclui as credenciais avançadas necessário outros serviços. Ele combina a vantagem de desempenho de segurança de transporte com a vantagem de rich credenciais de segurança de mensagem. Isso está disponível com as seguintes associações: <xref:System.ServiceModel.BasicHttpBinding>, <xref:System.ServiceModel.WSFederationHttpBinding>, <xref:System.ServiceModel.NetPeerTcpBinding>, e <xref:System.ServiceModel.WSHttpBinding>.  
  
3.  Se você decidir usar a segurança de transporte HTTP (em outras palavras, HTTPS), você também deve configurar o host com um certificado SSL e habilitar o SSL em uma porta. Para obter mais informações, consulte [segurança de transporte HTTP](../../../../docs/framework/wcf/feature-details/http-transport-security.md).  
  
4.  Se você estiver usando o <xref:System.ServiceModel.WSHttpBinding> e não é necessário estabelecer uma sessão segura, defina o <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> propriedade `false`.  
  
     Uma sessão segura ocorre quando um cliente e o serviço criam um canal usando uma chave simétrica (cliente e servidor para usar a mesma chave para o comprimento de uma conversa, até que a caixa de diálogo é fechada).  
  
## <a name="setting-the-client-credential-type"></a>Definir o tipo de credencial de cliente  
 Selecione um tipo de credencial de cliente conforme apropriado. Para obter mais informações, consulte [selecionando um tipo de credencial](../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md). Os seguintes tipos de credencial de cliente estão disponíveis:  
  
-   `Windows`  
  
-   `Certificate`  
  
-   `Digest`  
  
-   `Basic`  
  
-   `UserName`  
  
-   `NTLM`  
  
-   `IssuedToken`  
  
 Dependendo de como você define o modo, você deve definir o tipo de credencial. Por exemplo, se você tiver selecionado o `wsHttpBinding`e tiver definido o modo de "Mensagem", em seguida, você também pode definir o `clientCredentialType` atributo do elemento de mensagem para um dos seguintes valores: `None`, `Windows`, `UserName`, `Certificate` , e `IssuedToken`, conforme mostrado no exemplo de configuração a seguir.  
  
```xml  
<system.serviceModel>  
<bindings>  
  <wsHttpBinding>  
    <binding name="myBinding">  
      <security mode="Message"/>  
      <message clientCredentialType="Windows"/>  
    </binding>  
</bindings>  
</system.serviceModel>  
```  
  
 Ou no código:  
  
 [!code-csharp[c_WsHttpService#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wshttpservice/cs/source.cs#1)]
 [!code-vb[c_WsHttpService#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wshttpservice/vb/source.vb#1)]  
  
## <a name="setting-service-credential-values"></a>Valores de credencial de serviço de configuração  
 Quando você seleciona um tipo de credencial de cliente, você deve definir as credenciais reais para o serviço e o cliente para usar. No serviço, as credenciais são definidas usando o <xref:System.ServiceModel.Description.ServiceCredentials> classe e retornado pelo <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> propriedade o <xref:System.ServiceModel.ServiceHostBase> classe. A associação em uso indica o tipo de credencial de serviço, o modo de segurança escolhido e o tipo da credencial do cliente. O código a seguir define um certificado para uma credencial de serviço.  
  
 [!code-csharp[c_tcpService#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_tcpservice/cs/source.cs#3)]
 [!code-vb[c_tcpService#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_tcpservice/vb/source.vb#3)]  
  
## <a name="setting-client-credential-values"></a>Definindo valores de credencial de cliente  
 No cliente, definir valores de credencial de cliente usando o <xref:System.ServiceModel.Description.ClientCredentials> classe e retornado pelo <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> propriedade o <xref:System.ServiceModel.ClientBase%601> classe. O código a seguir define um certificado como uma credencial em um cliente usando o protocolo TCP.  
  
 [!code-csharp[c_TcpClient#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_tcpclient/cs/source.cs#1)]
 [!code-vb[c_TcpClient#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_tcpclient/vb/source.vb#1)]  
  
## <a name="see-also"></a>Consulte também  
 [Programação básica do WCF](../../../../docs/framework/wcf/basic-wcf-programming.md)  
 [Cenários comuns de segurança](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md)
