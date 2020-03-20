---
title: Segurança de mensagem através do enfileiramento de mensagem
ms.date: 03/30/2017
ms.assetid: 329aea9c-fa80-45c0-b2b9-e37fd7b85b38
ms.openlocfilehash: 2048b27f15787c70abda65ae582849276469c763
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144429"
---
# <a name="message-security-over-message-queuing"></a>Segurança de mensagem através do enfileiramento de mensagem
Esta amostra demonstra como implementar um aplicativo que usa o WS-Security com autenticação de certificado X.509v3 para o cliente e requer autenticação do servidor usando o certificado X.509v3 do servidor sobre o MSMQ. A segurança das mensagens às vezes é mais desejável para garantir que as mensagens na loja MSMQ permaneçam criptografadas e que o aplicativo possa executar sua própria autenticação da mensagem.

 Esta amostra é baseada na amostra [de ligação MSMQ transacionada.](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md) As mensagens são criptografadas e assinadas.

### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo

1. Certifique-se de que você tenha realizado o [procedimento de configuração única para as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).

2. Se o serviço for executado primeiro, ele verificará se a fila está presente. Se a fila não estiver presente, o serviço criará uma. Você pode executar o serviço primeiro para criar a fila, ou você pode criar um através do MSMQ Queue Manager. Siga estas etapas para criar uma fila no Windows 2008.

    1. Gerente de servidor aberto no Visual Studio 2012.

    2. Expanda a guia **Recursos.**

    3. Clique com o botão direito do mouse em Filas de **mensagens privadas**e selecione **Nova** **fila privada**.

    4. Verifique a **caixa transacional.**

    5. Digite `ServiceModelSamplesTransacted` como o nome da nova fila.

3. Para construir a edição C# ou Visual Basic .NET da solução, siga as instruções em [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).

### <a name="to-run-the-sample-on-the-same-computer"></a>Para executar a amostra no mesmo computador

1. Certifique-se de que o caminho inclui a pasta que contém Makecert.exe e FindPrivateKey.exe.

2. Executar Setup.bat da pasta de instalação de amostra. Isso instala todos os certificados necessários para a execução da amostra.

    > [!NOTE]
    > Certifique-se de remover os certificados executando Cleanup.bat quando terminar com a amostra. Outras amostras de segurança usam os mesmos certificados.  
  
3. Launch Service.exe from \service\bin.  
  
4. Inicie client.exe a partir de \client\bin. A atividade do cliente é exibida no aplicativo do console cliente.  
  
5. Se o cliente e o serviço não forem capazes de se comunicar, consulte [Dicas de solução de problemas para amostras wcf](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
### <a name="to-run-the-sample-across-computers"></a>Para executar a amostra através de computadores  
  
1. Copie os arquivos Setup.bat, Cleanup.bat e ImportClientCert.bat para o computador de serviço.  
  
2. Crie um diretório no computador cliente para os binários do cliente.  
  
3. Copie os arquivos do programa cliente para o diretório do cliente no computador cliente. Copie também os arquivos Setup.bat, Cleanup.bat e ImportServiceCert.bat para o cliente.  
  
4. No servidor, `setup.bat service`execute. A `setup.bat` execução com o `service` argumento cria um certificado de serviço com o nome de domínio totalmente qualificado do computador e exporta o certificado de serviço para um arquivo chamado Service.cer.  
  
5. Editar o service.exe.config do serviço para refletir `findValue` o novo nome do certificado (no atributo no [ \<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)), que é o mesmo que o nome de domínio totalmente qualificado do computador.  
  
6. Copie o arquivo Service.cer do diretório de serviço para o diretório do cliente no computador cliente.  
  
7. No cliente, `setup.bat client`corra. A `setup.bat` execução com o `client` argumento cria um certificado de cliente chamado client.com e exporta o certificado do cliente para um arquivo chamado Client.cer.  
  
8. No arquivo Client.exe.config no computador do cliente, altere o valor do endereço do ponto final para corresponder ao novo endereço do seu serviço. Faça isso substituindo o localhost pelo nome de domínio totalmente qualificado do servidor.  Você também deve alterar o nome do certificado do serviço para ser o mesmo `findValue` que o `defaultCertificate` nome `serviceCertificate` `clientCredentials`de domínio totalmente qualificado do computador de serviço (no atributo no elemento de under ).  
  
9. Copie o arquivo Client.cer do diretório do cliente para o diretório de serviço situado no servidor.  
  
10. No cliente, `ImportServiceCert.bat`corra. Isso importa o certificado de serviço do arquivo Service.cer para a loja CurrentUser - TrustedPeople.  
  
11. No servidor, `ImportClientCert.bat`execute , Isso importa o certificado do cliente do arquivo Client.cer para a loja LocalMachine - TrustedPeople.  
  
12. No computador de serviço, inicie Service.exe a partir do prompt de comando.  
  
13. No computador do cliente, inicie client.exe a partir do prompt de comando. Se o cliente e o serviço não forem capazes de se comunicar, consulte [Dicas de solução de problemas para amostras wcf](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
### <a name="to-clean-up-after-the-sample"></a>Para limpar depois da amostra  
  
- Executar Cleanup.bat na pasta amostras depois de terminar de executar a amostra.  
  
    > [!NOTE]
    > Este script não remove certificados de serviço em um cliente ao executar essa amostra em computadores. Se você tiver executado amostras de WCF (Windows Communication Foundation, fundação de comunicação do Windows) que usam certificados em computadores, certifique-se de limpar os certificados de serviço que foram instalados na loja CurrentUser - TrustedPeople. Para isso, use o `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` seguinte comando: Por exemplo: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.

## <a name="requirements"></a>Requisitos
 Esta amostra requer que o MSMQ esteja instalado e em execução.

## <a name="demonstrates"></a>Demonstra
 O cliente criptografa a mensagem usando a chave pública do serviço e assina a mensagem usando seu próprio certificado. O serviço de leitura da mensagem da fila autentica o certificado do cliente com o certificado em sua loja de pessoas confiáveis. Em seguida, descriptografa a mensagem e envia a mensagem para a operação do serviço.

 Como a mensagem da Windows Communication Foundation (WCF) é transportada como uma carga no corpo da mensagem MSMQ, o corpo permanece criptografado na loja MSMQ. Isso protege a mensagem da divulgação indesejada da mensagem. Observe que o próprio MSMQ não está ciente se a mensagem que está carregando é criptografada.

 A amostra demonstra como a autenticação mútua no nível da mensagem pode ser usada com o MSMQ. Os certificados são trocados fora de banda. Esse é sempre o caso do aplicativo enfileirado porque o serviço e o cliente não têm que estar funcionando ao mesmo tempo.

## <a name="description"></a>Descrição
 O cliente amostra e o código de serviço são os mesmos da amostra [de vinculação MSMQ transacionada](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md) com uma diferença. O contrato de operação é anotado com nível de proteção, o que sugere que a mensagem deve ser assinada e criptografada.

```csharp
// Define a service contract.
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]
public interface IOrderProcessor
{
    [OperationContract(IsOneWay = true, ProtectionLevel=ProtectionLevel.EncryptAndSign)]
    void SubmitPurchaseOrder(PurchaseOrder po);
}
```

 Para garantir que a mensagem seja protegida usando o token necessário para identificar o serviço e o cliente, o App.config contém informações de credenciais.

 A configuração do cliente especifica o certificado de serviço para autenticar o serviço. Ele usa sua loja LocalMachine como a loja confiável para confiar na validade do serviço. Ele também especifica o certificado de cliente anexado com a mensagem para autenticação de serviço do cliente.

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

 Observe que o modo de segurança está definido como Mensagem e o ClientCredentialType está definido como Certificado.

 A configuração do serviço inclui um comportamento de serviço que especifica as credenciais do serviço que são usadas quando o cliente autentica o serviço. O nome do assunto do `findValue` certificado do servidor é especificado no atributo no [ \<serviceCredentials>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md).

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

 A amostra demonstra o controle da autenticação usando a configuração e como obter a identidade do chamador a partir do contexto de segurança, conforme mostrado no seguinte código de amostra:

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

 Quando executado, o código de serviço exibe a identificação do cliente. A seguir está uma saída de amostra do código de serviço:

```console
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

- Criando o certificado do cliente.

     A linha a seguir no arquivo de lote cria o certificado do cliente. O nome do cliente especificado é usado no nome do assunto do certificado criado. O certificado é `My` armazenado `CurrentUser` na loja no local da loja.

    ```bat
    echo ************
    echo making client cert
    echo ************
    makecert.exe -sr CurrentUser -ss MY -a sha1 -n CN=%CLIENT_NAME% -sky exchange -pe
    ```

- Instalando o certificado de cliente na loja de certificados confiáveis do servidor.

     A linha a seguir no arquivo em lote copia o certificado do cliente na loja TrustedPeople do servidor para que o servidor possa tomar as decisões de confiança ou não confiáveis relevantes. Para que um certificado instalado na loja TrustedPeople seja confiável por um serviço wcf da Windows `PeerOrChainTrust` `PeerTrust` Communication Foundation (Windows Communication Foundation), o modo de validação do certificado do cliente deve ser definido ou valorizado. Consulte a amostra de configuração de serviço anterior para saber como isso pode ser feito usando um arquivo de configuração.

    ```bat
    echo ************
    echo copying client cert to server's LocalMachine store
    echo ************
    certmgr.exe -add -r CurrentUser -s My -c -n %CLIENT_NAME% -r LocalMachine -s TrustedPeople
    ```

- Criando o certificado do servidor.

     As seguintes linhas do arquivo setup.bat batch criam o certificado de servidor a ser usado:

    ```bat
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
    ```

     A variável %SERVER_NAME% especifica o nome do servidor. O certificado é armazenado na loja LocalMachine. Se o arquivo de lote de configuração for `setup.bat service`executado com um argumento de serviço (como, ) o %SERVER_NAME% contém o nome de domínio totalmente qualificado do computador. Caso contrário, ele é padrão para host local

- Instalando o certificado do servidor na loja de certificados confiáveis do cliente.

     A linha a seguir copia o certificado do servidor na loja de pessoas confiáveis do cliente. Essa etapa é necessária porque os certificados gerados pelo Makecert.exe não são implicitamente confiáveis pelo sistema cliente. Se você já tiver um certificado enraizado em um certificado raiz confiável do cliente — por exemplo, um certificado emitido pela Microsoft — essa etapa de povoar a loja de certificados do cliente com o certificado do servidor não é necessária.

    ```console
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
    ```

    > [!NOTE]
    > Se você estiver usando uma edição em inglês não-americana do Microsoft Windows, você deve editar o arquivo Setup.bat e substituir o nome da conta "NT AUTHORITY\NETWORK SERVICE" pelo seu equivalente regional.

> [!IMPORTANT]
> Os exemplos podem mais ser instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation). Este exemplo está localizado no seguinte diretório.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\MessageSecurity`  
