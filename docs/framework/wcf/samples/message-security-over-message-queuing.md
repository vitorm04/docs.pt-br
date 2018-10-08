---
title: Segurança de mensagem através do enfileiramento de mensagem
ms.date: 03/30/2017
ms.assetid: 329aea9c-fa80-45c0-b2b9-e37fd7b85b38
author: BrucePerlerMS
ms.openlocfilehash: 4578f93759379fabe258f6a70e38a9c5d46433dc
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/08/2018
ms.locfileid: "48850831"
---
# <a name="message-security-over-message-queuing"></a>Segurança de mensagem através do enfileiramento de mensagem
Este exemplo demonstra como implementar um aplicativo que usa WS-Security com autenticação de certificado X.509v3 para o cliente e requer autenticação de servidor usando o certificado X.509v3 do servidor em relação ao MSMQ. Mensagem de segurança, às vezes, é mais desejável para garantir que as mensagens no armazenamento de MSMQ permanecem criptografadas e o aplicativo pode executar sua própria autenticação da mensagem.

 Este exemplo se baseia a [transacionada de associação de MSMQ](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md) exemplo. As mensagens são criptografadas e assinadas.

### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo

1.  Certifique-se de que você tenha executado o [procedimento de configuração de uso único para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).

2.  Se o serviço é executado primeiro, ele verificará para garantir que a fila está presente. Se a fila não estiver presente, o serviço criará um. Você pode executar o serviço pela primeira vez para criar a fila, ou você pode criar um por meio do Gerenciador de fila MSMQ. Siga estas etapas para criar uma fila no Windows 2008.

    1.  Abra o Gerenciador de servidores no Visual Studio 2012.

    2.  Expanda o **recursos** guia.

    3.  Clique com botão direito **filas de mensagens privadas**e selecione **New**, **fila particular**.

    4.  Verifique as **transacional** caixa.

    5.  Insira `ServiceModelSamplesTransacted` como o nome da nova fila.

3.  Para compilar a edição em C# ou Visual Basic .NET da solução, siga as instruções em [compilando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).

### <a name="to-run-the-sample-on-the-same-computer"></a>Para executar o exemplo no mesmo computador

1.  Certifique-se de que o caminho inclui a pasta que contém Makecert.exe e FindPrivateKey.exe.

2.  Execute Setup. bat da pasta de instalação de exemplo. Essa opção instala todos os certificados necessários para executar o exemplo.

    > [!NOTE]
    >  Certifique-se de que você remova os certificados com a execução CleanUp quando você terminar com o exemplo. Outros exemplos de segurança usam os mesmos certificados.  
  
3.  Inicie o Service.exe no \service\bin.  
  
4.  Inicie o Client.exe no \client\bin. Atividade do cliente é exibida no aplicativo de console do cliente.  
  
5.  Se o cliente e o serviço não for capazes de se comunicar, consulte [dicas de solução de problemas](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).  
  
### <a name="to-run-the-sample-across-computers"></a>Para executar o exemplo em computadores  
  
1.  Copie os arquivos Setup. bat, CleanUp e ImportClientCert.bat no computador de serviço.  
  
2.  Crie um diretório no computador cliente para os binários do cliente.  
  
3.  Copie os arquivos de programa do cliente para o diretório do cliente no computador cliente. Também copie os arquivos Setup. bat, CleanUp e ImportServiceCert.bat ao cliente.  
  
4.  No servidor, execute `setup.bat service`. Executando `setup.bat` com o `service` argumento cria um certificado de serviço com o nome de domínio totalmente qualificado do computador e exporta o certificado de serviço para um arquivo chamado Service.cer.  
  
5.  Editar service.exe.config do serviço para refletir o novo nome do certificado (na `findValue` de atributo na [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) que é o mesmo que o nome de domínio totalmente qualificado do computador.  
  
6.  Copie o arquivo de Service.cer do diretório de serviço para o diretório do cliente no computador cliente.  
  
7.  No cliente, execute `setup.bat client`. Executando `setup.bat` com o `client` argumento cria um certificado de cliente chamado client.com e exporta o certificado de cliente para um arquivo chamado da CER.  
  
8.  No arquivo Client.exe.config no computador cliente, altere o valor do endereço do ponto de extremidade para coincidir com o novo endereço do seu serviço. Fazer isso, substitua localhost pelo nome de domínio totalmente qualificado do servidor.  Você também deve alterar o nome do certificado do serviço para ser o mesmo que o nome de domínio totalmente qualificado do computador do serviço (na `findValue` de atributo na `defaultCertificate` elemento de `serviceCertificate` em `clientCredentials`).  
  
9. Copie o arquivo de Client. cer do diretório do cliente para o diretório de serviço no servidor.  
  
10. No cliente, execute `ImportServiceCert.bat`. Isso importa o certificado de serviço do arquivo Service.cer para CurrentUser - TrustedPeople store.  
  
11. No servidor, execute `ImportClientCert.bat`, isso importa o certificado de cliente do arquivo CER para o repositório de LocalMachine - TrustedPeople.  
  
12. No computador do serviço, inicie Service.exe do prompt de comando.  
  
13. No computador cliente, inicie Client.exe do prompt de comando. Se o cliente e o serviço não for capazes de se comunicar, consulte [dicas de solução de problemas](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).  
  
### <a name="to-clean-up-after-the-sample"></a>Para limpar após a amostra  
  
-   Execute CleanUp na pasta exemplos depois de concluir a execução do exemplo.  
  
    > [!NOTE]
    >  Esse script não remove os certificados de serviço em um cliente ao executar este exemplo entre computadores. Se você executou os exemplos do Windows Communication Foundation (WCF) que usam certificados em computadores, certifique-se de limpar os certificados de serviço que foram instalados no CurrentUser - TrustedPeople store. Para fazer isso, use o seguinte comando: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` por exemplo: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.

## <a name="requirements"></a>Requisitos
 Este exemplo requer que o MSMQ está instalado e em execução.

## <a name="demonstrates"></a>Demonstra
 O cliente criptografa a mensagem usando a chave pública do serviço e assina a mensagem usando seu próprio certificado. O serviço de ler a mensagem da fila autentica o certificado do cliente com o certificado em seu repositório de pessoas confiáveis. Em seguida, ele descriptografa a mensagem e expede a mensagem para a operação de serviço.

 Porque a mensagem do Windows Communication Foundation (WCF) é executada como um conteúdo no corpo da mensagem do MSMQ, o corpo permanece criptografado no armazenamento do MSMQ. Isso protege a mensagem da divulgação indesejada de mensagem. Observe que o MSMQ em si não está ciente se a mensagem que ele esteja carregando é criptografada.

 O exemplo demonstra a autenticação mútua como a mensagem de nível pode ser usado com o MSMQ. Os certificados são troca fora de banda. Isso é sempre o caso com o aplicativo em fila porque o serviço e o cliente não precisam estar em execução ao mesmo tempo.

## <a name="description"></a>Descrição
 O código de cliente e o serviço de exemplo são os mesmos que o [associação de MSMQ transacionado](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md) exemplo com uma diferença. O contrato de operação é anotado com o nível de proteção, o que sugere que a mensagem deve ser assinada e criptografada.

```csharp
// Define a service contract.
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]
public interface IOrderProcessor
{
    [OperationContract(IsOneWay = true, ProtectionLevel=ProtectionLevel.EncryptAndSign)]
    void SubmitPurchaseOrder(PurchaseOrder po);
}
```

 Para garantir que a mensagem é protegida usando o token necessário para identificar o serviço e o cliente, o App. config contém informações de credenciais.

 A configuração de cliente especifica o certificado de serviço para autenticar o serviço. Ele usa seu armazenamento LocalMachine como o armazenamento confiável contar com a validade do serviço. Ela também especifica o certificado do cliente que está associado com a mensagem para a autenticação de serviço do cliente.

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>

  <system.serviceModel>

    <client>
      <!-- Define NetMsmqEndpoint -->
      <endpoint address="net.msmq://localhost/private/ServiceModelSamplesMessageSecurity"
                binding="netMsmqBinding"
                bindingConfiguration="messageSecurityBinding"
                contract="Microsoft.ServiceModel.Samples.IOrderProcessor"
                behaviorConfiguration="ClientCertificateBehavior" />
    </client>

    <bindings>
        <netMsmqBinding>
            <binding name="messageSecurityBinding">
                <security mode="Message">
                    <message clientCredentialType="Certificate"/>
                </security>
            </binding>
        </netMsmqBinding>
    </bindings>

    <behaviors>
      <endpointBehaviors>
        <behavior name="ClientCertificateBehavior">
          <!--
        The clientCredentials behavior allows one to define a certificate to present to a service.
        A certificate is used by a client to authenticate itself to the service and provide message integrity.
        This configuration references the "client.com" certificate installed during the setup instructions.
        -->
          <clientCredentials>
            <clientCertificate findValue="client.com" storeLocation="CurrentUser" storeName="My" x509FindType="FindBySubjectName" />
            <serviceCertificate>
                <defaultCertificate findValue="localhost" storeLocation="CurrentUser" storeName="TrustedPeople" x509FindType="FindBySubjectName"/>
              <!--
            Setting the certificateValidationMode to PeerOrChainTrust means that if the certificate
            is in the user's Trusted People store, then it is trusted without performing a
            validation of the certificate's issuer chain. This setting is used here for convenience so that the
            sample can be run without having to have certificates issued by a certification authority (CA).
            This setting is less secure than the default, ChainTrust. The security implications of this
            setting should be carefully considered before using PeerOrChainTrust in production code.
            -->
              <authentication certificateValidationMode="PeerOrChainTrust" />
            </serviceCertificate>
          </clientCredentials>
        </behavior>
      </endpointBehaviors>
    </behaviors>

  </system.serviceModel>
</configuration>
```

 Observe que o modo de segurança é definido como mensagem e ClientCredentialType está definida como Certificate.

 A configuração de serviço inclui um comportamento de serviço que especifica as credenciais do serviço que são usadas quando o cliente autentica o serviço. O nome de assunto do certificado de servidor é especificado na `findValue` de atributo em de [ \<serviceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md).

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>

  <appSettings>
    <!-- Use appSetting to configure MSMQ queue name. -->
    <add key="queueName" value=".\private$\ServiceModelSamplesMessageSecurity" />
  </appSettings>

  <system.serviceModel>
    <services>
      <service
          name="Microsoft.ServiceModel.Samples.OrderProcessorService"
          behaviorConfiguration="PurchaseOrderServiceBehavior">
        <host>
          <baseAddresses>
            <add baseAddress="http://localhost:8000/ServiceModelSamples/service"/>
          </baseAddresses>
        </host>
        <!-- Define NetMsmqEndpoint -->
        <endpoint address="net.msmq://localhost/private/ServiceModelSamplesMessageSecurity"
                  binding="netMsmqBinding"
                  bindingConfiguration="messageSecurityBinding"
                  contract="Microsoft.ServiceModel.Samples.IOrderProcessor" />
        <!-- The mex endpoint is exposed at http://localhost:8000/ServiceModelSamples/service/mex. -->
        <endpoint address="mex"
                  binding="mexHttpBinding"
                  contract="IMetadataExchange" />
      </service>
    </services>

    <bindings>
        <netMsmqBinding>
            <binding name="messageSecurityBinding">
                <security mode="Message">
                    <message clientCredentialType="Certificate" />
                </security>
            </binding>
        </netMsmqBinding>
    </bindings>

    <behaviors>
      <serviceBehaviors>
        <behavior name="PurchaseOrderServiceBehavior">
          <serviceMetadata httpGetEnabled="True"/>
          <!--
               The serviceCredentials behavior allows one to define a service certificate.
               A service certificate is used by the service to authenticate itself to its clients and to provide message protection.
               This configuration references the "localhost" certificate installed during the setup instructions.
          -->
          <serviceCredentials>
            <serviceCertificate findValue="localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectName" />
            <clientCertificate>
                <certificate findValue="client.com" storeLocation="LocalMachine" storeName="TrustedPeople" x509FindType="FindBySubjectName"/>
              <!--
            Setting the certificateValidationMode to PeerOrChainTrust means that if the certificate
            is in the user's Trusted People store, then it is trusted without performing a
            validation of the certificate's issuer chain. This setting is used here for convenience so that the
            sample can be run without having to have certificates issued by a certification authority (CA).
            This setting is less secure than the default, ChainTrust. The security implications of this
            setting should be carefully considered before using PeerOrChainTrust in production code.
            -->
              <authentication certificateValidationMode="PeerOrChainTrust" />
            </clientCertificate>
          </serviceCredentials>
        </behavior>
      </serviceBehaviors>
    </behaviors>

  </system.serviceModel>

</configuration>
```

 O exemplo demonstra o controle de autenticação usando a configuração e como obter a identidade do chamador do contexto de segurança, conforme mostrado no código de exemplo a seguir:

```csharp
// Service class which implements the service contract.
// Added code to write output to the console window.
public class OrderProcessorService : IOrderProcessor
{
    private string GetCallerIdentity()
    {
        // The client certificate is not mapped to a Windows identity by default.
        // ServiceSecurityContext.PrimaryIdentity is populated based on the information
        // in the certificate that the client used to authenticate itself to the service.
        return ServiceSecurityContext.Current.PrimaryIdentity.Name;
    }

    [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]
    public void SubmitPurchaseOrder(PurchaseOrder po)
    {
        Console.WriteLine("Client's Identity {0} ", GetCallerIdentity());
        Orders.Add(po);
        Console.WriteLine("Processing {0} ", po);
    }
  //…
}
```

 Quando executado, o código de serviço exibe a identificação de cliente. Este é um exemplo de saída do código de serviço:

```
The service is ready.
Press <ENTER> to terminate service.

Client's Identity CN=client.com; ECA6629A3C695D01832D77EEE836E04891DE9D3C
Processing Purchase Order: 6536e097-da96-4773-9da3-77bab4345b5d
        Customer: somecustomer.com
        OrderDetails
                Order LineItem: 54 of Blue Widget @unit price: $29.99
                Order LineItem: 890 of Red Widget @unit price: $45.89
        Total cost of this order: $42461.56
        Order status: Pending
```

## <a name="comments"></a>Comentários

-   Criando o certificado do cliente.

     A seguinte linha no arquivo de lote cria o certificado do cliente. O nome do cliente especificado é usado no nome da entidade do certificado criado. O certificado é armazenado no `My` armazenar cada a `CurrentUser` local do repositório.

    ```bat
    echo ************
    echo making client cert
    echo ************
    makecert.exe -sr CurrentUser -ss MY -a sha1 -n CN=%CLIENT_NAME% -sky exchange -pe
    ```

-   Instalando o certificado do cliente no repositório de certificados confiáveis do servidor.

     A seguinte linha nas cópias do arquivo em lotes que o certificado do cliente em TrustedPeople do servidor armazenar para que o servidor possa fazer a relação de confiança relevante ou decisões de confiança não. Para um certificado instalado no repositório de TrustedPeople ser confiável por um serviço do Windows Communication Foundation (WCF), o modo de validação de certificado do cliente deve ser definido como `PeerOrChainTrust` ou `PeerTrust` valor. Consulte o exemplo de configuração de serviço anterior para saber como isso pode ser feito usando um arquivo de configuração.

    ```bat
    echo ************
    echo copying client cert to server's LocalMachine store
    echo ************
    certmgr.exe -add -r CurrentUser -s My -c -n %CLIENT_NAME% -r LocalMachine -s TrustedPeople
    ```

-   Criando o certificado do servidor.

     As seguintes linhas do arquivo em lotes bat criam o certificado do servidor a ser usado:

    ```bat
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
    ```

     A variável % SERVER_NAME % Especifica o nome do servidor. O certificado é armazenado no repositório de LocalMachine. Se o arquivo de lote é executado com um argumento de serviço (como, `setup.bat service`) % % SERVER_NAME contém o nome de domínio totalmente qualificado do computador. Caso contrário, o padrão é localhost

-   Instalar o certificado do servidor no repositório de certificados confiáveis do cliente.

     A linha a seguir copia o certificado do servidor para o repositório de pessoas confiáveis do cliente. Esta etapa é necessária porque certificados gerados pelo Makecert.exe não são implicitamente confiáveis pelo sistema do cliente. Se você já tiver um certificado que está enraizado em um certificado de raiz confiável do cliente — por exemplo, um certificado emitido Microsoft — essa etapa de preencher o repositório de certificados de cliente com o certificado do servidor não é necessária.

    ```
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
    ```

    > [!NOTE]
    >  Se você estiver usando um fora dos EUA Edição em inglês do Microsoft Windows, você deve editar o Setup. bat de arquivo e substitua o nome da conta "NT AUTHORITY\NETWORK SERVICE" com seu equivalente regional.

> [!IMPORTANT]
>  Os exemplos podem mais ser instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\MessageSecurity`  
  
## <a name="see-also"></a>Consulte também
