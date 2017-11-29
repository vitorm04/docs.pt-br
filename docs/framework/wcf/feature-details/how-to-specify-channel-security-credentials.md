---
title: "Como especificar credenciais de segurança de canal"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f8e03f47-9c4f-4dd5-8f85-429e6d876119
caps.latest.revision: "18"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 2a1b2ba0ab49ebf470c0245f0827f82e1fe20ce8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-specify-channel-security-credentials"></a>Como especificar credenciais de segurança de canal
O [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Moniker de serviço permite que aplicativos de COM chamar [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviços. A maioria dos [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] services requer que o cliente especificar credenciais para autenticação e autorização. Ao chamar um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviço um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] cliente, você pode especificar essas credenciais no código gerenciado ou em um arquivo de configuração do aplicativo. Ao chamar um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviço de um aplicativo COM, você pode usar o <xref:System.ServiceModel.ComIntegration.IChannelCredentials> interface para especificar as credenciais. Este tópico ilustrará várias maneiras de especificar credenciais usando o <xref:System.ServiceModel.ComIntegration.IChannelCredentials> interface.  
  
> [!NOTE]
>  <xref:System.ServiceModel.ComIntegration.IChannelCredentials>é uma interface baseada em IDispatch e você não terá a funcionalidade do IntelliSense no ambiente do Visual Studio.  
  
 Este artigo usará o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviço definido no [exemplo de segurança de mensagem](../../../../docs/framework/wcf/samples/message-security-sample.md).  
  
### <a name="to-specify-a-client-certificate"></a>Para especificar um certificado de cliente  
  
1.  Execute o arquivo bat no diretório de segurança de mensagem para criar e instalar os certificados de teste necessário.  
  
2.  Abra o projeto de segurança de mensagem.  
  
3.  Adicionar `[ServiceBehavior(Namespace=``http://Microsoft.ServiceModel.Samples``)]` para o `ICalculator` definição de interface.  
  
4.  Adicionar `bindingNamespace=``http://Microsoft.ServiceModel.Samples` à marca de ponto de extremidade no App. config para o serviço.  
  
5.  Criar o exemplo de segurança de mensagem e executar Service.exe. Use o Internet Explorer e navegue até o URI do serviço (ServiceModelSamples/http://localhost:8000/serviço) para garantir que o serviço está funcionando.  
  
6.  Abra o Visual Basic 6.0 e crie um novo arquivo .exe padrão. Adicione um botão ao formulário e clique duas vezes no botão para adicionar o código a seguir para o manipulador de cliques:  
  
    ```  
        monString = "service:mexAddress=http://localhost:8000/ServiceModelSamples/Service?wsdl"  
        monString = monString + ", address=http://localhost:8000/ServiceModelSamples/Service"  
        monString = monString + ", contract=ICalculator, contractNamespace=http://Microsoft.ServiceModel.Samples"  
        monString = monString + ", binding=BasicHttpBinding_ICalculator, bindingNamespace=http://Microsoft.ServiceModel.Samples"  
  
        Set monikerProxy = GetObject(monString)  
  
        'Set the Service Certificate.  
     monikerProxy.ChannelCredentials.SetServiceCertificateAuthentication "CurrentUser", "NoCheck", "PeerOrChainTrust"  
    monikerProxy.ChannelCredentials.SetDefaultServiceCertificateFromStore "CurrentUser", "TrustedPeople", "FindBySubjectName", "localhost"  
  
        'Set the Client Certificate.  
        monikerProxy.ChannelCredentials.SetClientCertificateFromStoreByName "CN=client.com", "CurrentUser", "My"  
        MsgBox monikerProxy.Add(3, 4)  
    ```  
  
7.  Execute o aplicativo do Visual Basic e verificar os resultados.  
  
     O aplicativo do Visual Basic exibirá uma caixa de mensagem com o resultado de chamar o método Add (3, 4). <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetClientCertificateFromFile%28System.String%2CSystem.String%2CSystem.String%29>ou <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetClientCertificateFromStoreByName%28System.String%2CSystem.String%2CSystem.String%29> também pode ser usado no lugar de <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetClientCertificateFromStore%28System.String%2CSystem.String%2CSystem.String%2CSystem.Object%29> para definir o certificado de cliente:  
  
    ```  
    monikerProxy.ChannelCredentials.SetClientCertificateFromFile "C:\MyClientCert.pfx", "password", "DefaultKeySet"  
    ```  
  
> [!NOTE]
>  Para esta chamada funcionar, o certificado de cliente precisa ser confiável no computador que cliente está em execução no.  
  
> [!NOTE]
>  Se o identificador de origem está malformado ou se o serviço está indisponível, a chamada para `GetObject` retornará um erro dizendo "Sintaxe inválida". Se você receber esse erro, verifique se você estiver usando o identificador de origem está correto e o serviço está disponível.  
  
### <a name="to-specify-user-name-and-password"></a>Para especificar o nome de usuário e senha  
  
1.  Modificar o arquivo App. config do serviço para usar o `wsHttpBinding`. Isso é necessário para a validação de nome e a senha do usuário:  
  
  
  
2.  Definir o `clientCredentialType` para o nome de usuário:  
  
  
  
3.  Abra o Visual Basic 6.0 e crie um novo arquivo .exe padrão. Adicione um botão ao formulário e clique duas vezes no botão para adicionar o código a seguir para o manipulador de cliques:  
  
    ```  
    monString = "service:mexAddress=http://localhost:8000/ServiceModelSamples/Service?wsdl"  
    monString = monString + ", address=http://localhost:8000/ServiceModelSamples/Service"  
    monString = monString + ", contract=ICalculator, contractNamespace=http://Microsoft.ServiceModel.Samples"  
    monString = monString + ", binding=WSHttpBinding_ICalculator, bindingNamespace=http://Microsoft.ServiceModel.Samples"  
  
    Set monikerProxy = GetObject(monString)  
  
    monikerProxy.ChannelCredentials.SetServiceCertificateAuthentication "CurrentUser", "NoCheck", "PeerOrChainTrust"  
    monikerProxy.ChannelCredentials.SetUserNameCredential "username", "password"  
  
    MsgBox monikerProxy.Add(3, 4)  
    ```  
  
4.  Execute o aplicativo do Visual Basic e verificar os resultados. O aplicativo do Visual Basic exibirá uma caixa de mensagem com o resultado de chamar o método Add (3, 4).  
  
    > [!NOTE]
    >  A associação especificada no apelido serviço neste exemplo foi alterada para WSHttpBinding_ICalculator. Observe também que você deve fornecer um nome de usuário válido e uma senha na chamada para <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetUserNameCredential%28System.String%2CSystem.String%29>.  
  
### <a name="to-specify-windows-credentials"></a>Para especificar as credenciais do Windows  
  
1.  Definir `clientCredentialType` para Windows no arquivo App. config do serviço:  
  
  
  
2.  Abra o Visual Basic 6.0 e crie um novo arquivo .exe padrão. Adicione um botão ao formulário e clique duas vezes no botão para adicionar o código a seguir para o manipulador de cliques:  
  
    ```  
    monString = "service:mexAddress=http://localhost:8000/ServiceModelSamples/Service?wsdl"  
    monString = monString + ", address=http://localhost:8000/ServiceModelSamples/Service"  
    monString = monString + ", contract=ICalculator, contractNamespace=http://Microsoft.ServiceModel.Samples"  
    monString = monString + ", binding=WSHttpBinding_ICalculator, bindingNamespace=http://Microsoft.ServiceModel.Samples"  
    monString = monString + ", upnidentity=domain\userID"  
  
    Set monikerProxy = GetObject(monString)  
     monikerProxy.ChannelCredentials.SetWindowsCredential "domain", "userID", "password", 1, True  
  
    MsgBox monikerProxy.Add(3, 4)  
    ```  
  
3.  Execute o aplicativo do Visual Basic e verificar os resultados. O aplicativo do Visual Basic exibirá uma caixa de mensagem com o resultado de chamar o método Add (3, 4).  
  
    > [!NOTE]
    >  Você deve substituir "domínio", "userID" e "password" com os valores válidos.  
  
### <a name="to-specify-an-issue-token"></a>Para especificar um token de problema  
  
1.  Emitir tokens são usados apenas para aplicativos que usam segurança federada. Para obter mais informações sobre segurança federada, consulte [federação e Tokens emitidos](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md) e [federação exemplo](../../../../docs/framework/wcf/samples/federation-sample.md).  
  
     O seguinte exemplo de código do Visual Basic mostra como chamar o <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetIssuedToken%28System.String%2CSystem.String%2CSystem.String%29> método:  
  
    ```  
        monString = "service:mexAddress=http://localhost:8000/ServiceModelSamples/Service?wsdl"  
        monString = monString + ", address=http://localhost:8000/SomeService/Service"  
        monString = monString + ", contract=ICalculator, contractNamespace=http://SomeService.Samples"  
        monString = monString + ", binding=WSHttpBinding_ISomeContract, bindingNamespace=http://SomeService.Samples"  
  
        Set monikerProxy = GetObject(monString)  
    monikerProxy.SetIssuedToken("http://somemachine/sts", "bindingType", "binding")  
    ```  
  
     Para obter mais informações sobre os parâmetros para este método, consulte <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetIssuedToken%28System.String%2CSystem.String%2CSystem.String%29>.  
  
## <a name="see-also"></a>Consulte também  
 [Federação](../../../../docs/framework/wcf/feature-details/federation.md)  
 [Como: configurar as credenciais em um serviço de Federação](../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)  
 [Como: criar um cliente federado](../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)  
 [Segurança de mensagem](../../../../docs/framework/wcf/feature-details/message-security-in-wcf.md)  
 [Associações e segurança](../../../../docs/framework/wcf/feature-details/bindings-and-security.md)
