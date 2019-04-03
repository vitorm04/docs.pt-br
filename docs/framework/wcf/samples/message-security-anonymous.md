---
title: Segurança de mensagem anônima
ms.date: 03/30/2017
helpviewer_keywords:
- WS Security
ms.assetid: c321cbf9-8c05-4cce-b5a5-4bf7b230ee03
ms.openlocfilehash: 534061e203c2efb0b81e5a1d1c720097a08ce15a
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58843663"
---
# <a name="message-security-anonymous"></a>Segurança de mensagem anônima
O exemplo de segurança de mensagem anônimo demonstra como implementar um aplicativo do Windows Communication Foundation (WCF) que usa a segurança de nível de mensagem sem autenticação de cliente, mas que requer autenticação de servidor usando o X.509 do servidor certificado. Todas as mensagens de aplicativo entre o cliente e servidor assinadas e criptografadas. Este exemplo se baseia a [WSHttpBinding](../../../../docs/framework/wcf/samples/wshttpbinding.md) exemplo. Esse exemplo consiste em um programa de console de cliente (.exe) e uma biblioteca de serviço (. dll) hospedado pelo Internet Information Services (IIS). O serviço implementa um contrato que define um padrão de comunicação de solicitação-resposta.

> [!NOTE]
>  As instruções de procedimento e compilação de configuração para este exemplo estão localizadas no final deste tópico.

 Este exemplo adiciona uma nova operação para a interface de calculadora retorna `True` se o cliente não foi autenticado.

```csharp
public class CalculatorService : ICalculator
{
    public bool IsCallerAnonymous()
    {
        // ServiceSecurityContext.IsAnonymous returns true if the caller is not authenticated.
        return ServiceSecurityContext.Current.IsAnonymous;
    }
    ...
}
```

 O serviço expõe um ponto de extremidade para se comunicar com o serviço, definido usando um arquivo de configuração (Web. config). O ponto de extremidade consiste em um endereço, uma ligação e um contrato. A associação está configurada com um `wsHttpBinding` associação. O modo de segurança padrão para o `wsHttpBinding` associação é `Message`. O `clientCredentialType` atributo é definido como `None`.

```xml
<system.serviceModel>

  <protocolMapping>
    <add scheme="http" binding="wsHttpBinding" />
  </protocolMapping>

  <bindings>
    <wsHttpBinding>
     <!-- This configuration defines the security mode as Message and -->
     <!-- the clientCredentialType as None. This mode provides -->
     <!-- server authentication only using the service certificate. -->

     <binding>
       <security mode="Message">
         <message clientCredentialType="None" />
       </security>
     </binding>
    </wsHttpBinding>
  </bindings>
  ...
</system.serviceModel>
```

 As credenciais a serem usadas para autenticação de serviço são especificadas na [ \<comportamento >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md). O certificado do servidor deve conter o mesmo valor para o `SubjectName` como o valor especificado para o `findValue` atributo conforme mostrado no código de exemplo a seguir.

```xml
<behaviors>
  <serviceBehaviors>
    <behavior>
      <!--
    The serviceCredentials behavior allows you to define a service certificate.
    A service certificate is used by a client to authenticate the service and provide message protection.
    This configuration references the "localhost" certificate installed during the setup instructions.
    -->
      <serviceCredentials>
        <serviceCertificate findValue="localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectName" />
      </serviceCredentials>
      <serviceMetadata httpGetEnabled="True"/>
      <serviceDebug includeExceptionDetailInFaults="False" />
    </behavior>
  </serviceBehaviors>
</behaviors>
```

 A configuração do ponto de extremidade cliente consiste em um endereço absoluto para o ponto de extremidade de serviço, a associação e o contrato. O modo de segurança do cliente para o `wsHttpBinding` associação é `Message`. O `clientCredentialType` atributo é definido como `None`.

```xml
<system.serviceModel>
  <client>
    <endpoint name=""
             address="http://localhost/servicemodelsamples/service.svc"
             binding="wsHttpBinding"
             behaviorConfiguration="ClientCredentialsBehavior"
             bindingConfiguration="Binding1"
             contract="Microsoft.ServiceModel.Samples.ICalculator" />
  </client>

  <bindings>
    <wsHttpBinding>
      <!--This configuration defines the security mode as -->
      <!--Message and the clientCredentialType as None. -->
      <binding name="Binding1">
        <security mode = "Message">
          <message clientCredentialType="None"/>
        </security>
      </binding>
    </wsHttpBinding>
  </bindings>
  ...
</system.serviceModel>
```

 O exemplo define o <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CertificateValidationMode%2A> para <xref:System.ServiceModel.Security.X509CertificateValidationMode.PeerOrChainTrust> para autenticar o certificado do serviço. Isso é feito no arquivo de App. config do cliente no `behaviors` seção. Isso significa que se o certificado estiver no armazenamento de pessoas confiáveis do usuário, em seguida, ele é confiável sem executar uma validação de cadeia de emissores do certificado. Essa configuração é usada aqui para sua conveniência para que o exemplo pode ser executado sem a necessidade de certificados emitidos por uma autoridade de certificação (CA). Essa configuração é menos segura do que o padrão, ChainTrust. As implicações de segurança dessa configuração devem ser consideradas com cuidado antes de usar `PeerOrChainTrust` no código de produção.

 A implementação do cliente adiciona uma chamada para o `IsCallerAnonymous` método e, caso contrário, não será diferente do [WSHttpBinding](../../../../docs/framework/wcf/samples/wshttpbinding.md) exemplo.

```csharp
// Create a client with a client endpoint configuration.
CalculatorClient client = new CalculatorClient();

// Call the GetCallerIdentity operation.
Console.WriteLine("IsCallerAnonymous returned: {0}", client.IsCallerAnonymous());

// Call the Add service operation.
double value1 = 100.00D;
double value2 = 15.99D;
double result = client.Add(value1, value2);
Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);

...

//Closing the client gracefully closes the connection and cleans up resources.
client.Close();

Console.WriteLine();
Console.WriteLine("Press <ENTER> to terminate client.");
Console.ReadLine();
```

 Quando você executar o exemplo, as respostas e solicitações de operação são exibidas na janela do console de cliente. Pressione ENTER na janela do cliente para desligar o cliente.

```
IsCallerAnonymous returned: True
Add(100,15.99) = 115.99
Subtract(145,76.54) = 68.46
Multiply(9,81.25) = 731.25
Divide(22,7) = 3.14285714285714
Press <ENTER> to terminate client.
```

 O arquivo em lotes de Setup. bat incluído no exemplo de segurança de mensagem anônima permite que você configure o servidor com um certificado apropriado para executar um aplicativo hospedado que exige a segurança baseada em certificado. O arquivo em lotes pode ser executado em dois modos. Para executar o arquivo em lote no modo único computador, digite `setup.bat` na linha de comando. Para executá-lo no modo de serviço, digite `setup.bat service`. Use este modo, ao executar a amostra entre computadores. Consulte o procedimento de instalação no final deste tópico para obter detalhes.

 O exemplo a seguir fornece uma visão geral das diferentes seções dos arquivos de lote:

-   Criando o certificado do servidor.

     As seguintes linhas do arquivo em lotes bat criam o certificado do servidor a ser usado.

    ```bat
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
    ```

     A variável % SERVER_NAME % Especifica o nome do servidor. O certificado é armazenado no repositório de LocalMachine. Se o arquivo de lote é executado com um argumento de serviço (como `setup.bat service`) % % SERVER_NAME contém o nome de domínio totalmente qualificado do computador. Caso contrário, o padrão é localhost.

-   Instalando o certificado do servidor no repositório de certificados confiáveis do cliente.

     A linha a seguir copia o certificado do servidor para o repositório de pessoas confiáveis do cliente. Esta etapa é necessária porque certificados gerados pelo Makecert.exe não são implicitamente confiáveis pelo sistema do cliente. Se você já tiver um certificado que está enraizado em um certificado de raiz confiável do cliente — por exemplo, um certificado emitido Microsoft — essa etapa de preencher o repositório de certificados de cliente com o certificado do servidor não é necessária.

    ```
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
    ```

-   Concedendo permissões de chave privada do certificado.

     As seguintes linhas no arquivo em lotes bat Verifique o certificado de servidor armazenado no repositório de LocalMachine acessível para o [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] conta de processo de trabalho.

    ```bat
    echo ************
    echo setting privileges on server certificates
    echo ************
    for /F "delims=" %%i in ('"%MSSDK%\bin\FindPrivateKey.exe" My LocalMachine -n CN^=%SERVER_NAME% -a') do set PRIVATE_KEY_FILE=%%i set WP_ACCOUNT=NT AUTHORITY\NETWORK SERVICE
    (ver | findstr "5.1") && set WP_ACCOUNT=%COMPUTERNAME%\ASPNET
    echo Y|cacls.exe "%PRIVATE_KEY_FILE%" /E /G "%WP_ACCOUNT%":R
    iisreset
    ```

> [!NOTE]
>  Se você estiver usando um fora dos EUA Edição em inglês do Windows, você deve editar o arquivo Setup. bat e substitua o `NT AUTHORITY\NETWORK SERVICE` nome da conta com seu equivalente regional.

### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo

1.  Certifique-se de que você tenha executado o [procedimento de configuração de uso único para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).

2.  Para compilar a edição em C# ou Visual Basic .NET da solução, siga as instruções em [compilando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).

### <a name="to-run-the-sample-on-the-same-computer"></a>Para executar o exemplo no mesmo computador

1.  Certifique-se de que o caminho inclui a pasta onde Makecert.exe e FindPrivateKey.exe estão localizados.

2.  Execute Setup. bat da pasta de instalação de exemplo em um Prompt de comando do desenvolvedor para Visual Studio executar com privilégios de administrador. Essa opção instala todos os certificados necessários para executar o exemplo.

    > [!NOTE]
    > O arquivo de lote é criado para ser executado de um Prompt de comando do desenvolvedor para Visual Studio. Ele requer que a variável de ambiente path apontar para o diretório onde o SDK está instalado. Essa variável de ambiente é definido automaticamente dentro de um Prompt de comando do desenvolvedor para Visual Studio.  
  
3.  Verificar o acesso ao serviço usando um navegador, inserindo o endereço `http://localhost/servicemodelsamples/service.svc`.  
  
4.  Inicie o Client.exe no \client\bin. Atividade do cliente é exibida no aplicativo de console do cliente.  
  
5.  Se o cliente e o serviço não for capazes de se comunicar, consulte [dicas de solução de problemas para obter exemplos de WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
### <a name="to-run-the-sample-across-computers"></a>Para executar o exemplo em computadores  
  
1.  Crie um diretório no computador do serviço. Crie um aplicativo virtual denominado servicemodelsamples para este diretório usando a ferramenta de gerenciamento de serviços de informações da Internet (IIS).  
  
2.  Copie os arquivos de programa do serviço de \inetpub\wwwroot\servicemodelsamples para o diretório virtual no computador do serviço. Certifique-se de que você copiar os arquivos no subdiretório \bin. Também copie os arquivos Setup. bat e Cleanup para o computador do serviço.  
  
3.  Crie um diretório no computador cliente para os binários do cliente.  
  
4.  Copie os arquivos de programa do cliente para o diretório do cliente no computador cliente. Também copie os arquivos Setup. bat, CleanUp e ImportServiceCert.bat ao cliente.  
  
5.  No servidor, execute `setup.bat service` em um Prompt de comando do desenvolvedor para Visual Studio é aberto com privilégios de administrador. Executando `setup.bat` com o `service` argumento cria um certificado de serviço com o nome de domínio totalmente qualificado do computador e exporta o certificado de serviço para um arquivo chamado Service.cer.  
  
6.  Editar o Web. config para refletir o novo nome do certificado (na `findValue` de atributo no [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)), que é igual ao nome de domínio totalmente qualificado do computador.  
  
7.  Copie o arquivo de Service.cer do diretório de serviço para o diretório do cliente no computador cliente.  
  
8.  No arquivo Client.exe.config no computador cliente, altere o valor do endereço do ponto de extremidade para coincidir com o novo endereço do seu serviço.  
  
9. No cliente, execute ImportServiceCert.bat em um Prompt de comando do desenvolvedor para Visual Studio aberto com privilégios de administrador. Isso importa o certificado de serviço do arquivo Service.cer para CurrentUser - TrustedPeople store.  
  
10. No computador cliente, inicie Client.exe em um prompt de comando. Se o cliente e o serviço não for capazes de se comunicar, consulte [dicas de solução de problemas para obter exemplos de WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
### <a name="to-clean-up-after-the-sample"></a>Para limpar após a amostra  
  
-   Execute CleanUp na pasta exemplos depois de concluir a execução do exemplo.  
  
> [!NOTE]
>  Esse script não remove os certificados de serviço em um cliente ao executar este exemplo entre computadores. Se você executou os exemplos do Windows Communication Foundation (WCF) que usam certificados em computadores, certifique-se de limpar os certificados de serviço que foram instalados no CurrentUser - TrustedPeople store. Para fazer isso, use o seguinte comando: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` Por exemplo: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com.`
