---
title: 'Como: especificar credenciais de segurança de canal'
ms.date: 03/30/2017
ms.assetid: f8e03f47-9c4f-4dd5-8f85-429e6d876119
ms.openlocfilehash: 0bfbb71ade3822b9f504c2f89a41145ce0d435f6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62038864"
---
# <a name="how-to-specify-channel-security-credentials"></a>Como: especificar credenciais de segurança de canal
O Moniker de serviço do Windows Communication Foundation (WCF) permite que aplicativos de COM chamar serviços WCF. A maioria dos serviços WCF requer que o cliente especificar credenciais para autenticação e autorização. Ao chamar um serviço WCF de um cliente WCF, você pode especificar essas credenciais no código gerenciado ou em um arquivo de configuração de aplicativo. Ao chamar um serviço WCF em um aplicativo COM, você pode usar o <xref:System.ServiceModel.ComIntegration.IChannelCredentials> interface para especificar as credenciais. Este tópico será ilustram várias maneiras para especificar as credenciais usando o <xref:System.ServiceModel.ComIntegration.IChannelCredentials> interface.  
  
> [!NOTE]
>  <xref:System.ServiceModel.ComIntegration.IChannelCredentials> é uma interface baseada em IDispatch e você não obterá a funcionalidade do IntelliSense no ambiente do Visual Studio.  
  
 Este artigo usará o serviço WCF definido na [exemplo de segurança de mensagem](../../../../docs/framework/wcf/samples/message-security-sample.md).  
  
### <a name="to-specify-a-client-certificate"></a>Para especificar um certificado de cliente  
  
1. Execute o arquivo Setup. bat no diretório de segurança de mensagem para criar e instalar os certificados de teste necessário.  
  
2. Abra o projeto de segurança de mensagem.  
  
3. Adicione `[ServiceBehavior(Namespace="http://Microsoft.ServiceModel.Samples")]` para o `ICalculator` definição de interface.  
  
4. Adicionar `bindingNamespace="http://Microsoft.ServiceModel.Samples"` à marca de ponto de extremidade em App. config para o serviço.  
  
5. Criar o exemplo de segurança de mensagem e execute Service.exe. Usar o Internet Explorer e navegue até o URI do serviço (http://localhost:8000/ServiceModelSamples/Service) para garantir que o serviço está funcionando.  
  
6. Abra o Visual Basic 6.0 e crie um novo arquivo .exe padrão. Adicione um botão ao formulário e clique duas vezes no botão para adicionar o seguinte código ao manipulador de cliques:  
  
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
  
7. Execute o aplicativo do Visual Basic e verificar os resultados.  
  
     O aplicativo Visual Basic exibe uma caixa de mensagem com o resultado de chamar o método Add (3, 4). <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetClientCertificateFromFile%28System.String%2CSystem.String%2CSystem.String%29> ou <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetClientCertificateFromStoreByName%28System.String%2CSystem.String%2CSystem.String%29> também pode ser usado no lugar de <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetClientCertificateFromStore%28System.String%2CSystem.String%2CSystem.String%2CSystem.Object%29> para definir o certificado do cliente:  
  
    ```  
    monikerProxy.ChannelCredentials.SetClientCertificateFromFile "C:\MyClientCert.pfx", "password", "DefaultKeySet"  
    ```  
  
> [!NOTE]
>  Para essa chamada funcione, o certificado do cliente precisa ser confiável no computador que cliente está em execução no.  
  
> [!NOTE]
>  Se o moniker está mal formado ou se o serviço está indisponível, a chamada para `GetObject` retornará um erro informando que "Sintaxe inválida". Se você receber esse erro, verifique se você estiver usando o identificador de origem está correto e o serviço está disponível.  
  
### <a name="to-specify-user-name-and-password"></a>Para especificar o nome de usuário e senha  
  
1. Modifique o arquivo App. config do serviço para usar o `wsHttpBinding`. Isso é necessário para a validação de nome e a senha do usuário:  

2. Defina o `clientCredentialType` ao nome de usuário:  

3. Abra o Visual Basic 6.0 e crie um novo arquivo .exe padrão. Adicione um botão ao formulário e clique duas vezes no botão para adicionar o seguinte código ao manipulador de cliques:  
  
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
  
4. Execute o aplicativo do Visual Basic e verificar os resultados. O aplicativo Visual Basic exibe uma caixa de mensagem com o resultado de chamar o método Add (3, 4).  
  
    > [!NOTE]
    >  A associação especificada neste exemplo, o moniker de serviço foi alterada para WSHttpBinding_ICalculator. Observe também que você deve fornecer um nome de usuário válido e uma senha na chamada para <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetUserNameCredential%28System.String%2CSystem.String%29>.  
  
### <a name="to-specify-windows-credentials"></a>Para especificar as credenciais do Windows  
  
1. Definir `clientCredentialType` para Windows no arquivo App. config do serviço:  

2. Abra o Visual Basic 6.0 e crie um novo arquivo .exe padrão. Adicione um botão ao formulário e clique duas vezes no botão para adicionar o seguinte código ao manipulador de cliques:  
  
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
  
3. Execute o aplicativo do Visual Basic e verificar os resultados. O aplicativo Visual Basic exibe uma caixa de mensagem com o resultado de chamar o método Add (3, 4).  
  
    > [!NOTE]
    >  Você deve substituir "domínio", "userID" e "senha" pelos valores válidos.  
  
### <a name="to-specify-an-issue-token"></a>Para especificar um token de problema  
  
1. Emitir tokens são usados apenas para aplicativos que usam segurança federada. Para obter mais informações sobre segurança federada, consulte [federação e Tokens emitidos](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md) e [exemplo de Federação](../../../../docs/framework/wcf/samples/federation-sample.md).  
  
     O exemplo de código Visual Basic a seguir ilustra como chamar o <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetIssuedToken%28System.String%2CSystem.String%2CSystem.String%29> método:  
  
    ```  
        monString = "service:mexAddress=http://localhost:8000/ServiceModelSamples/Service?wsdl"  
        monString = monString + ", address=http://localhost:8000/SomeService/Service"  
        monString = monString + ", contract=ICalculator, contractNamespace=http://SomeService.Samples"  
        monString = monString + ", binding=WSHttpBinding_ISomeContract, bindingNamespace=http://SomeService.Samples"  
  
        Set monikerProxy = GetObject(monString)  
    monikerProxy.SetIssuedToken("http://somemachine/sts", "bindingType", "binding")  
    ```  
  
     Para obter mais informações sobre os parâmetros para esse método, consulte <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetIssuedToken%28System.String%2CSystem.String%2CSystem.String%29>.  
  
## <a name="see-also"></a>Consulte também

- [Federação](../../../../docs/framework/wcf/feature-details/federation.md)
- [Como: Configurar credenciais em um serviço de Federação](../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
- [Como: Criar um cliente federado](../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)
- [Segurança de mensagem](../../../../docs/framework/wcf/feature-details/message-security-in-wcf.md)
- [Associações e segurança](../../../../docs/framework/wcf/feature-details/bindings-and-security.md)
