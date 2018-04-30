---
title: Segurança de associação personalizada
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a6383dff-4308-46d2-bc6d-acd4e18b4b8d
caps.latest.revision: 30
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload:
- dotnet
ms.openlocfilehash: 4774e4ed6c5afc6e9c4af50e0663ffe8c0964b7f
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/27/2018
---
# <a name="custom-binding-security"></a>Segurança de associação personalizada
Este exemplo demonstra como configurar a segurança por meio de uma associação personalizada. Ele mostra como usar uma associação personalizada para habilitar a segurança em nível de mensagem junto com um transporte seguro. Isso é útil quando um transporte seguro é necessária para transmitir mensagens entre cliente e serviço e simultaneamente as mensagens devem ser seguras no nível de mensagem. Essa configuração não é suportada por associações fornecidas pelo sistema.  
  
 Este exemplo consiste em um programa de console de cliente (EXE) e um programa de console de serviço (EXE). O serviço implementa um contrato duplex. O contrato é definido pelo `ICalculatorDuplex` interface, que expõe operações matemáticas (Adicionar, subtrair, multiplicar e dividir). O `ICalculatorDuplex` interface permite que o cliente executar operações matemáticas, calcular um resultado em execução em uma sessão. Independentemente, o serviço pode retornar resultados no `ICalculatorDuplexCallback` interface. Um contrato duplex requer uma sessão, porque um contexto deve ser estabelecido para correlacionar o conjunto de mensagens sendo enviadas entre o cliente e o serviço. Uma associação personalizada é definida que oferece suporte à comunicação duplex e seguro.  
  
> [!NOTE]
>  As instruções de procedimento e a compilação de configuração para este exemplo estão localizadas no final deste tópico.  
  
 A configuração do serviço define uma associação personalizada que suporta o seguinte:  
  
-   Comunicação TCP protegida usando o protocolo TLS/SSL.  
  
-   Segurança de mensagem do Windows.  
  
 A configuração de associação personalizada permite que o transporte seguro, simultaneamente, permitindo a segurança no nível de mensagem. A ordenação dos elementos de associação é importante definir uma associação personalizada, como cada uma representa uma camada da pilha de canal (consulte [associações personalizadas](../../../../docs/framework/wcf/extending/custom-bindings.md)). A associação personalizada é definida nos arquivos de configuração do cliente e de serviço, conforme mostrado no exemplo de configuração.  
  
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
  
 A associação personalizada usa um certificado de serviço para autenticar o serviço no nível do transporte e proteger as mensagens durante a transmissão entre cliente e serviço. Isso é feito usando o `sslStreamSecurity` elemento de associação. Certificado do serviço é configurado usando um comportamento de serviço, conforme mostrado no exemplo de configuração.  
  
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
  
 Além disso, a associação personalizada usa segurança de mensagem com o tipo de credencial do Windows - esse é o tipo de credencial padrão. Isso é feito usando o `security` elemento de associação. Cliente e serviço são autenticados usando a segurança de nível de mensagem se o mecanismo de autenticação Kerberos está disponível. Isso ocorre se o exemplo é executado no ambiente do Active Directory. Se o mecanismo de autenticação Kerberos não estiver disponível, a autenticação NTLM é usada. NTLM autentica o cliente para o serviço, mas não autenticar o serviço ao cliente. O `security` elemento de associação está configurado para usar `SecureConversation``authenticationType`, que resulta na criação de uma sessão de segurança no cliente e o serviço. Isso é necessário para habilitar o contrato do serviço duplex trabalhar.  
  
 Quando você executar o exemplo, as respostas e solicitações de operação são exibidas na janela do console do cliente. Pressione ENTER na janela do cliente para desligar o cliente.  
  
```  
Press <ENTER> to terminate client.  
Result(100)  
Result(50)  
Result(882.5)  
Result(441.25)  
Equation(0 + 100 - 50 * 17.65 / 2 = 441.25)  
```  
  
 Quando você executar o exemplo, você ver as mensagens retornadas ao cliente sobre a interface de retorno de chamada enviada do serviço. Cada resultado intermediário é exibido, seguido por toda a equação após a conclusão de todas as operações. Pressione ENTER para fechar o cliente.  
  
 O arquivo bat incluído permite que você configure o cliente e o servidor com o certificado de serviço relevantes para executar um aplicativo hospedado que exige a segurança baseada em certificado. Esse arquivo em lotes deve ser modificado para funcionar entre computadores ou para trabalhar em um caso não hospedado.  
  
 O exemplo a seguir fornece uma visão geral das seções diferentes dos arquivos de lote que se aplicam a este exemplo, para que eles podem ser modificados para executar a configuração apropriada:  
  
-   Criando o certificado do servidor.  
  
     As seguintes linhas do arquivo bat criam o certificado do servidor a ser usado. O `%SERVER_NAME%` variável Especifica o nome do servidor. Altere essa variável para especificar seu próprio nome de servidor. Esse arquivo em lote padrão é o nome do servidor com o localhost.  
  
     O certificado é armazenado no repositório de CurrentUser para os serviços Web hospedados.  
  
    ```bat
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
-   Instalando o certificado de servidor no repositório de certificados confiáveis do cliente.  
  
     Armazenam as linhas a seguir na cópia de arquivo bat o certificado do servidor em que as pessoas confiáveis do cliente. Esta etapa é necessária porque os certificados gerados pela Makecert.exe não são implicitamente confiáveis pelo sistema do cliente. Se você já tiver um certificado que está enraizado em um certificado de raiz confiável do cliente — por exemplo, um certificado emitido Microsoft — essa etapa de preenchimento do repositório de certificados de cliente com o certificado do servidor não é necessária.  
  
    ```  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
    > [!NOTE]
    >  O arquivo em lotes bat é projetado para ser executado de um Visual Studio 2010 Prompt de comando. Isso requer que a variável de ambiente MSSDK apontar para o diretório onde o SDK está instalado. Essa variável de ambiente é definida automaticamente dentro de um Visual Studio 2010 Prompt de comando.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1.  Certifique-se de que você executou o [único procedimento de instalação para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Para compilar o c# ou Visual Basic .NET edição da solução, siga as instruções em [compilar os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
### <a name="to-run-the-sample-on-the-same-computer"></a>Para executar o exemplo no mesmo computador  
  
1.  Abra uma janela de Prompt de comando do Visual Studio com privilégios de administrador e execute bat da pasta de instalação do exemplo. Isso instala todos os certificados necessários para executar o exemplo.  
  
    > [!NOTE]
    >  O arquivo em lotes bat é projetado para ser executado de um [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] Prompt de comando. Definir a variável de ambiente PATH dentro de [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] Prompt de comando aponta para o diretório que contém os executáveis exigido pelo script bat.  
  
2.  Inicie Service.exe de \service\bin.  
  
3.  Inicie Client.exe de \Client\Bin. Atividade do cliente é exibida no aplicativo de console do cliente.  
  
4.  Se o cliente e o serviço não for capazes de se comunicar, consulte [dicas de solução de problemas](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).  
  
### <a name="to-run-the-sample-across-computers"></a>Para executar o exemplo em computadores  
  
1.  No computador do serviço:  
  
    1.  Crie um diretório virtual chamado servicemodelsamples no computador de serviço.  
  
    2.  Copie os arquivos de programa do serviço de \inetpub\wwwroot\servicemodelsamples para o diretório virtual no computador de serviço. Certifique-se de que você copiar os arquivos no subdiretório \bin.  
  
    3.  Copie os arquivos. bat e Cleanup.bat para o computador do serviço.  
  
    4.  Execute o seguinte comando em um prompt de comando do Visual Studio é aberto com privilégios de administrador: `Setup.bat service`. Isso cria o certificado de serviço com o nome de entidade correspondente ao nome do computador em que o arquivo em lotes foi executado no.  
  
        > [!NOTE]
        >  O arquivo em lotes bat é projetado para ser executado de um Visual Studio 2010 Prompt de comando. Isso requer que a variável de ambiente path apontar para o diretório onde o SDK está instalado. Essa variável de ambiente é definida automaticamente dentro de um Visual Studio 2010 Prompt de comando.  
  
    5.  Alterar o [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) dentro do arquivo Service.exe.config para refletir o nome da entidade do certificado gerado na etapa anterior.  
  
    6.  Execute Service.exe em um prompt de comando.  
  
2.  No computador cliente:  
  
    1.  Copie os arquivos de programa do cliente da pasta \client\bin\ no computador cliente. Também copie o arquivo Cleanup.bat.  
  
    2.  Execute Cleanup.bat para remover quaisquer certificados antigos de exemplos anteriores.  
  
    3.  Exportar o certificado do serviço de abrindo um prompt de comando do Visual Studio com privilégios administrativos e executando o seguinte comando no computador de serviço (substitua `%SERVER_NAME%` com o nome totalmente qualificado do computador onde o serviço está executando):  
  
        ```  
        certmgr -put -r LocalMachine -s My -c -n %SERVER_NAME% %SERVER_NAME%.cer  
        ```  
  
    4.  Copie %SERVER_NAME%.cer para o computador cliente (substituto SERVER_NAME % com o nome totalmente qualificado do computador onde o serviço está sendo executado).  
  
    5.  Importar o certificado do serviço abrindo um prompt de comando do Visual Studio com privilégios administrativos e executando o seguinte comando no computador cliente (substituto SERVER_NAME % com o nome totalmente qualificado do computador onde o serviço está executando):  
  
        ```  
        certmgr.exe -add -c %SERVER_NAME%.cer -s -r CurrentUser TrustedPeople  
        ```  
  
         Etapas c, d e e não são necessárias se o certificado é emitido por um emissor confiável.  
  
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
  
    7.  Se o serviço é executado sob uma conta que não seja o NetworkService ou LocalSystem em um ambiente de domínio, você talvez precise modificar a identidade do ponto de extremidade para o ponto de extremidade de serviço no arquivo App. config do cliente, para definir o UPN ou o SPN com base em apropriado a conta que é usado para executar o serviço. Para obter mais informações sobre a identidade do ponto de extremidade, consulte o [autenticação e identidade de serviço](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md) tópico.  
  
    8.  Execute Client.exe em um prompt de comando.  
  
### <a name="to-clean-up-after-the-sample"></a>A limpeza após a amostra  
  
-   Execute Cleanup.bat na pasta exemplos depois de terminar de executar o exemplo.  
  
## <a name="see-also"></a>Consulte também
