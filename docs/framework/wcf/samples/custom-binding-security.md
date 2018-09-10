---
title: Segurança de associação personalizada
ms.date: 03/30/2017
ms.assetid: a6383dff-4308-46d2-bc6d-acd4e18b4b8d
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 61e8be6f7f621340a684bff69ec5c9d64ab36c61
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43876009"
---
# <a name="custom-binding-security"></a>Segurança de associação personalizada
Este exemplo demonstra como configurar a segurança por meio de uma associação personalizada. Ele mostra como usar uma ligação personalizada para habilitar a segurança em nível de mensagem junto com um transporte seguro. Isso é útil quando um transporte seguro é necessária para transmitir as mensagens entre o cliente e o serviço e ao mesmo tempo as mensagens devem ser seguras no nível da mensagem. Essa configuração não é suportada por associações fornecidas pelo sistema.  
  
 Esse exemplo consiste em um programa de console de cliente (EXE) e um programa de console de serviço (EXE). O serviço implementa um contrato duplex. O contrato é definido o `ICalculatorDuplex` interface, que expõe operações matemáticas (Adicionar, subtrair, multiplicar e dividir). O `ICalculatorDuplex` interface permite que o cliente a executar operações matemáticas, calculando um resultado em execução em uma sessão. De forma independente, o serviço pode retornar resultados no `ICalculatorDuplexCallback` interface. Um contrato duplex requer uma sessão, porque um contexto deve ser estabelecido para correlacionar o conjunto de mensagens sendo enviadas entre o cliente e o serviço. Uma associação personalizada é definida que dá suporte à comunicação duplex e é seguro.  
  
> [!NOTE]
>  As instruções de procedimento e compilação de configuração para este exemplo estão localizadas no final deste tópico.  
  
 A configuração de serviço define uma associação personalizada que dá suporte ao seguinte:  
  
-   Comunicação TCP protegida usando o protocolo TLS/SSL.  
  
-   Segurança de mensagem do Windows.  
  
 A configuração de associação personalizado permite que o transporte seguro, permitindo simultaneamente a segurança de nível de mensagem. A ordenação dos elementos de associação é importante definir uma ligação personalizada, porque cada um representa uma camada da pilha de canal (consulte [ligações personalizadas](../../../../docs/framework/wcf/extending/custom-bindings.md)). A associação personalizada é definida nos arquivos de configuração de cliente e o serviço, conforme mostrado no seguinte exemplo de configuração.  
  
```xml  
<bindings>  
  <!-- Configure a custom binding. -->  
  <customBinding>  
    <binding name="Binding1">  
      <security authenticationMode="SecureConversation"  
                 requireSecurityContextCancellation="true">  
      </security>  
      <textMessageEncoding messageVersion="Soap12WSAddressing10" writeEncoding="utf-8"/>  
      <sslStreamSecurity requireClientCertificate="false"/>  
      <tcpTransport/>  
    </binding>  
  </customBinding>  
</bindings>  
```  
  
 A associação personalizada usa um certificado de serviço para autenticar o serviço no nível de transporte e proteger as mensagens durante a transmissão entre cliente e serviço. Isso é feito usando o `sslStreamSecurity` elemento de associação. O certificado do serviço é configurado usando um comportamento de serviço, conforme mostrado no seguinte exemplo de configuração.  
  
```xml  
<behaviors>  
    <serviceBehaviors>  
    <behavior name="CalculatorServiceBehavior">  
        <serviceMetadata />  
        <serviceDebug includeExceptionDetailInFaults="False" />  
        <serviceCredentials>  
        <serviceCertificate findValue="localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectName"/>  
        </serviceCredentials>  
    </behavior>  
    </serviceBehaviors>  
</behaviors>  
```  
  
 Além disso, a associação personalizada usa segurança de mensagem com o tipo de credencial do Windows - esse é o tipo de credencial padrão. Isso é feito usando o `security` elemento de associação. Cliente e o serviço são autenticados usando a segurança de nível de mensagem se o mecanismo de autenticação Kerberos está disponível. Isso ocorre se a amostra for executada no ambiente do Active Directory. Se o mecanismo de autenticação Kerberos não estiver disponível, a autenticação NTLM é usada. NTLM autentica o cliente para o serviço, mas não autentica o serviço ao cliente. O `security` elemento de associação está configurado para usar `SecureConversation``authenticationType`, que resulta na criação de uma sessão de segurança no cliente e o serviço. Isso é necessário para habilitar o contrato do serviço duplex trabalhar.  
  
 Quando você executar o exemplo, as respostas e solicitações de operação são exibidas na janela do console do cliente. Pressione ENTER na janela do cliente para desligar o cliente.  
  
```  
Press <ENTER> to terminate client.  
Result(100)  
Result(50)  
Result(882.5)  
Result(441.25)  
Equation(0 + 100 - 50 * 17.65 / 2 = 441.25)  
```  
  
 Quando você executar o exemplo, você ver as mensagens retornadas ao cliente sobre a interface de retorno de chamada enviada do serviço. Cada resultado intermediário é exibido, seguido por toda a equação após a conclusão de todas as operações. Pressione ENTER para desligar o cliente.  
  
 O arquivo Setup. bat incluído permite que você configure o cliente e servidor com o certificado de serviço relevante para executar um aplicativo hospedado que exige a segurança baseada em certificado. Esse arquivo em lotes deve ser modificado para funcionar entre computadores ou para trabalhar em um caso de não hospedados.  
  
 O exemplo a seguir fornece uma visão geral das diferentes seções dos arquivos de lote que se aplicam a este exemplo, para que eles podem ser modificados para executar a configuração apropriada:  
  
-   Criando o certificado do servidor.  
  
     As seguintes linhas do arquivo Setup. bat de criam o certificado do servidor a ser usado. O `%SERVER_NAME%` variável Especifica o nome do servidor. Altere essa variável para especificar seu próprio nome de servidor. Esse arquivo em lotes padrão é o nome do servidor ao localhost.  
  
     O certificado é armazenado no repositório CurrentUser para os serviços hospedados na Web.  
  
    ```bat
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
-   Instalando o certificado do servidor no repositório de certificados confiáveis do cliente.  
  
     As seguintes linhas na cópia do arquivo Setup. bat o certificado do servidor as pessoas confiáveis do cliente ao repositório. Esta etapa é necessária porque certificados gerados pelo Makecert.exe não são implicitamente confiáveis pelo sistema do cliente. Se você já tiver um certificado que está enraizado em um certificado de raiz confiável do cliente — por exemplo, um certificado emitido Microsoft — essa etapa de preencher o repositório de certificados de cliente com o certificado do servidor não é necessária.  
  
    ```  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
    > [!NOTE]
    >  O arquivo em lotes de Setup. bat foi projetado para ser executado a partir de um Visual Studio 2010 Prompt de comando. Ele requer que a variável de ambiente MSSDK apontar para o diretório onde o SDK está instalado. Essa variável de ambiente é definido automaticamente dentro de um Visual Studio 2010 Prompt de comando.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1.  Certifique-se de que você tenha executado o [procedimento de configuração de uso único para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Para compilar a edição em C# ou Visual Basic .NET da solução, siga as instruções em [compilando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
### <a name="to-run-the-sample-on-the-same-computer"></a>Para executar o exemplo no mesmo computador  
  
1.  Abra uma janela de Prompt de comando do Visual Studio com privilégios de administrador e execute Setup. bat da pasta de instalação de exemplo. Essa opção instala todos os certificados necessários para executar o exemplo.  
  
    > [!NOTE]
    >  O arquivo em lotes de Setup. bat foi projetado para ser executado a partir um [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] Prompt de comando. A variável de ambiente PATH definido dentro de [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] Prompt de comando aponta para o diretório que contém executáveis exigido pelo script de Setup. bat.  
  
2.  Inicie o Service.exe no \service\bin.  
  
3.  Inicie o Client.exe no \Client\Bin. Atividade do cliente é exibida no aplicativo de console do cliente.  
  
4.  Se o cliente e o serviço não for capazes de se comunicar, consulte [dicas de solução de problemas](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).  
  
### <a name="to-run-the-sample-across-computers"></a>Para executar o exemplo em computadores  
  
1.  No computador do serviço:  
  
    1.  Crie um diretório virtual chamado servicemodelsamples no computador do serviço.  
  
    2.  Copie os arquivos de programa do serviço de \inetpub\wwwroot\servicemodelsamples para o diretório virtual no computador do serviço. Certifique-se de que você copiar os arquivos no subdiretório \bin.  
  
    3.  Copie os arquivos Setup. bat e Cleanup no computador de serviço.  
  
    4.  Execute o seguinte comando em um prompt de comando do Visual Studio é aberto com privilégios de administrador: `Setup.bat service`. Isso cria o certificado de serviço com o nome da entidade que corresponde ao nome do computador em que o arquivo em lotes foi executado em.  
  
        > [!NOTE]
        >  O arquivo em lotes de Setup. bat foi projetado para ser executado a partir de um Visual Studio 2010 Prompt de comando. Ele requer que a variável de ambiente path apontar para o diretório onde o SDK está instalado. Essa variável de ambiente é definido automaticamente dentro de um Visual Studio 2010 Prompt de comando.  
  
    5.  Alterar o [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) dentro do arquivo Service.exe.config para refletir o nome da entidade do certificado gerado na etapa anterior.  
  
    6.  Execute Service.exe em um prompt de comando.  
  
2.  No computador cliente:  
  
    1.  Copie os arquivos de programa do cliente da pasta \client\bin\ no computador cliente. Copie também o arquivo de CleanUp.  
  
    2.  Execute CleanUp para remover todos os certificados antigos de amostras anteriores.  
  
    3.  Exportar o certificado do serviço abrindo um prompt de comando do Visual Studio com privilégios administrativos e executando o seguinte comando no computador do serviço (substitua `%SERVER_NAME%` com o nome totalmente qualificado do computador onde o serviço está em execução):  
  
        ```  
        certmgr -put -r LocalMachine -s My -c -n %SERVER_NAME% %SERVER_NAME%.cer  
        ```  
  
    4.  Copie %SERVER_NAME%.cer para o computador cliente (substitua % SERVER_NAME % com o nome totalmente qualificado do computador onde o serviço está em execução).  
  
    5.  Importar o certificado do serviço abrindo um prompt de comando do Visual Studio com privilégios administrativos e executando o seguinte comando no computador cliente (substitua % SERVER_NAME % com o nome totalmente qualificado do computador onde o serviço está em execução):  
  
        ```  
        certmgr.exe -add -c %SERVER_NAME%.cer -s -r CurrentUser TrustedPeople  
        ```  
  
         Etapas de c, d e e não são necessárias se o certificado é emitido por um emissor confiável.  
  
    6.  Modifique o arquivo do cliente App. config da seguinte maneira:  
  
        ```xml  
        <client>  
            <endpoint name="default"  
                address="net.tcp://ReplaceThisWithServiceMachineName:8000/ServiceModelSamples/Service"   
                binding="customBinding"   
                bindingConfiguration="Binding1"   
                contract="Microsoft.ServiceModel.Samples.ICalculatorDuplex"  
        behaviorConfiguration="CalculatorClientBehavior" />  
        </client>  
        ```  
  
    7.  Se o serviço for executado sob uma conta que não seja o NetworkService ou LocalSystem em um ambiente de domínio, você talvez precise modificar a identidade do ponto de extremidade para o ponto de extremidade de serviço dentro do arquivo de App. config do cliente para definir o UPN ou o SPN com base em apropriado na conta que é usado para executar o serviço. Para obter mais informações sobre a identidade do ponto de extremidade, consulte a [identidade de serviço e autenticação](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md) tópico.  
  
    8.  Execute Client.exe em um prompt de comando.  
  
### <a name="to-clean-up-after-the-sample"></a>Para limpar após a amostra  
  
-   Execute CleanUp na pasta exemplos depois de concluir a execução do exemplo.  
  
## <a name="see-also"></a>Consulte também
