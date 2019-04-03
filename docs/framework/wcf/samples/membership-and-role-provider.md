---
title: Provedor de função e associação
ms.date: 03/30/2017
ms.assetid: 0d11a31c-e75f-4fcf-9cf4-b7f26e056bcd
ms.openlocfilehash: eb2c8a5bbe10d91a29ed040e89163279434c8f8f
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58839750"
---
# <a name="membership-and-role-provider"></a>Provedor de função e associação
O provedor de função e associação que demonstra como um serviço pode usar o [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] provedores de associação e funções para autenticar e autorizar clientes.  
  
 Neste exemplo, o cliente é um aplicativo de console (.exe) e o serviço é hospedado pelo Internet Information Services (IIS).  
  
> [!NOTE]
>  As instruções de procedimento e compilação de configuração para este exemplo estão localizadas no final deste tópico.  
  
 O exemplo demonstra como:  
  
-   Um cliente pode autenticar usando a combinação da senha do nome de usuário.  
  
-   O servidor pode validar as credenciais do cliente em relação a [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] provedor de associação.  
  
-   O servidor pode ser autenticado usando o certificado do servidor x. 509.  
  
-   O servidor pode mapear o cliente autenticado a uma função usando o [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] provedor de função.  
  
-   O servidor pode usar o `PrincipalPermissionAttribute` para controlar o acesso a determinados métodos que são expostos pelo serviço.  
  
 Os provedores de associação e funções são configurados para usar um armazenamento de apoio do SQL Server. Uma cadeia de caracteres de conexão e várias opções são especificadas no arquivo de configuração de serviço. O provedor de associação é dado o nome `SqlMembershipProvider` enquanto o provedor de função recebe o nome `SqlRoleProvider`.  
  
```xml  
<!-- Set the connection string for SQL Server -->  
<connectionStrings>  
  <add name="SqlConn"   
       connectionString="Data Source=localhost;Integrated Security=SSPI;Initial Catalog=aspnetdb;" />  
</connectionStrings>  
  
<system.web>  
  <!-- Configure the Sql Membership Provider -->  
  <membership defaultProvider="SqlMembershipProvider" userIsOnlineTimeWindow="15">  
    <providers>  
      <clear />  
      <add   
        name="SqlMembershipProvider"   
        type="System.Web.Security.SqlMembershipProvider"   
        connectionStringName="SqlConn"  
        applicationName="MembershipAndRoleProviderSample"  
        enablePasswordRetrieval="false"  
        enablePasswordReset="false"  
        requiresQuestionAndAnswer="false"  
        requiresUniqueEmail="true"  
        passwordFormat="Hashed" />  
    </providers>  
  </membership>  
  
  <!-- Configure the Sql Role Provider -->  
  <roleManager enabled ="true"   
               defaultProvider ="SqlRoleProvider" >  
    <providers>  
      <add name ="SqlRoleProvider"   
           type="System.Web.Security.SqlRoleProvider"   
           connectionStringName="SqlConn"   
           applicationName="MembershipAndRoleProviderSample"/>  
    </providers>  
  </roleManager>  
</system.web>  
```  
  
 O serviço expõe um ponto de extremidade para se comunicar com o serviço, que é definido usando o arquivo de configuração Web. config. O ponto de extremidade consiste em um endereço, uma ligação e um contrato. A associação está configurada com um padrão `wsHttpBinding`, cujo padrão é usando a autenticação do Windows. Este exemplo define o padrão `wsHttpBinding` para usar a autenticação de nome de usuário. O comportamento Especifica que o certificado do servidor deve ser usado para autenticação de serviço. O certificado do servidor deve conter o mesmo valor para o `SubjectName` como o `findValue` atributo na [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) elemento de configuração. Além disso, o comportamento Especifica que a autenticação de senha do nome de usuário pares é executada pela [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] provedor de associação e o mapeamento de função é executada pelo [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] provedor de função, especificando os nomes definidos para os dois provedores.  
  
```xml  
<system.serviceModel>  
  
  <protocolMapping>  
    <add scheme="http" binding="wsHttpBinding" />  
  </protocolMapping>  
  
  <bindings>  
    <wsHttpBinding>  
      <!-- Set up a binding that uses Username as the client credential type -->  
      <binding>  
        <security mode ="Message">  
          <message clientCredentialType ="UserName"/>  
        </security>  
      </binding>  
    </wsHttpBinding>  
  </bindings>  
  
  <behaviors>  
    <serviceBehaviors>  
      <behavior>  
        <!-- Configure role based authorization to use the Role Provider -->  
        <serviceAuthorization principalPermissionMode ="UseAspNetRoles"  
                              roleProviderName ="SqlRoleProvider" />  
        <serviceCredentials>  
          <!-- Configure user name authentication to use the Membership Provider -->  
          <userNameAuthentication userNamePasswordValidationMode ="MembershipProvider"   
                                  membershipProviderName ="SqlMembershipProvider"/>  
          <!-- Configure the service certificate -->  
          <serviceCertificate storeLocation ="LocalMachine"   
                              storeName ="My"   
                              x509FindType ="FindBySubjectName"  
                              findValue ="localhost" />  
        </serviceCredentials>  
        <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->  
        <serviceDebug includeExceptionDetailInFaults="false" />  
        <serviceMetadata httpGetEnabled="true"/>  
      </behavior>  
    </serviceBehaviors>  
  </behaviors>  
</system.serviceModel>  
```  
  
 Quando você executar o exemplo, o cliente chama as várias operações de serviço em três diferentes contas de usuário: Charlie, Bob e Alice. As respostas e solicitações de operação são exibidas na janela do console de cliente. Todas as quatro chamadas feitas como usuário "Alice" deve ser bem-sucedida. O usuário "Bob" obterá um erro de acesso negado ao tentar chamar o método de divisão. O usuário "Charlie" obterá um erro de acesso negado ao tentar chamar o método Multiply. Pressione ENTER na janela do cliente para desligar o cliente.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1.  Para compilar a edição em C# ou Visual Basic .NET da solução, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
2.  Certifique-se de que você tenha configurado o [serviços de banco de dados do aplicativo ASP.NET](https://go.microsoft.com/fwlink/?LinkId=94997).  
  
    > [!NOTE]
    >  Se você estiver executando o SQL Server Express Edition, o nome do servidor é. \SQLEXPRESS. Esse servidor deve ser usado ao configurar o [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aplicativo Serviços de banco de dados, bem como a cadeia de caracteres de conexão de Web. config.  
  
    > [!NOTE]
    >  O [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] conta de processo de trabalho deve ter permissões no banco de dados que é criado nesta etapa. Use o utilitário sqlcmd ou o SQL Server Management Studio para fazer isso.  
  
3.  Para executar o exemplo em uma configuração ou entre computadores, use as instruções a seguir.  
  
### <a name="to-run-the-sample-on-the-same-computer"></a>Para executar o exemplo no mesmo computador  
  
1.  Certifique-se de que o caminho inclui a pasta onde se encontra Makecert.exe.  
  
2.  Execute Setup. bat da pasta de instalação de exemplo em um Prompt de comando do desenvolvedor para Visual Studio executar com privilégios de administrador. Isso instala os certificados de serviço necessários para executar o exemplo.  
  
3.  Inicie o Client.exe no \client\bin. Atividade do cliente é exibida no aplicativo de console do cliente.  
  
4.  Se o cliente e o serviço não for capazes de se comunicar, consulte [dicas de solução de problemas para obter exemplos de WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
### <a name="to-run-the-sample-across-computers"></a>Para executar o exemplo em computadores  
  
1.  Crie um diretório no computador do serviço. Crie um aplicativo virtual denominado servicemodelsamples para este diretório usando a ferramenta de gerenciamento de serviços de informações da Internet (IIS).  
  
2.  Copie os arquivos de programa do serviço de \inetpub\wwwroot\servicemodelsamples para o diretório virtual no computador do serviço. Certifique-se de que você copiar os arquivos no subdiretório \bin. Também copie os arquivos Setup. bat, GetComputerName.vbs e Cleanup para o computador do serviço.  
  
3.  Crie um diretório no computador cliente para os binários do cliente.  
  
4.  Copie os arquivos de programa do cliente para o diretório do cliente no computador cliente. Também copie os arquivos Setup. bat, CleanUp e ImportServiceCert.bat ao cliente.  
  
5.  No servidor, abra um Prompt de comando do desenvolvedor para Visual Studio com privilégios administrativos e execute `setup.bat service`. Executando `setup.bat` com o `service` argumento cria um certificado de serviço com o nome de domínio totalmente qualificado do computador e exporta o certificado de serviço para um arquivo chamado Service.cer.  
  
6.  Editar o Web. config para refletir o novo nome do certificado (na `findValue` de atributo no [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)), que é igual ao nome de domínio totalmente qualificado do computador.  
  
7.  Copie o arquivo de Service.cer do diretório de serviço para o diretório do cliente no computador cliente.  
  
8.  No arquivo Client.exe.config no computador cliente, altere o valor do endereço do ponto de extremidade para coincidir com o novo endereço do seu serviço.  
  
9. No cliente, abra um Prompt de comando do desenvolvedor para Visual Studio com privilégios administrativos e execute ImportServiceCert.bat. Isso importa o certificado de serviço do arquivo Service.cer para CurrentUser - TrustedPeople store.  
  
10. No computador cliente, inicie Client.exe em um prompt de comando. Se o cliente e o serviço não for capazes de se comunicar, consulte [dicas de solução de problemas para obter exemplos de WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
### <a name="to-clean-up-after-the-sample"></a>Para limpar após a amostra  
  
-   Execute CleanUp na pasta exemplos depois de concluir a execução do exemplo.  
  
> [!NOTE]
>  Esse script não remove os certificados de serviço em um cliente ao executar este exemplo entre computadores. Se você executou os exemplos do Windows Communication Foundation (WCF) que usam certificados em computadores, certifique-se de limpar os certificados de serviço que foram instalados no CurrentUser - TrustedPeople store. Para fazer isso, use o seguinte comando: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` Por exemplo: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.  
  
## <a name="the-setup-batch-file"></a>O arquivo de lote  
 O arquivo em lotes de Setup. bat incluído com este exemplo permite que você configure o servidor com certificados relevantes para executar um aplicativo hospedado internamente que exige a segurança baseada em certificado do servidor. Esse arquivo em lotes deve ser modificado para funcionar entre computadores ou para trabalhar em um caso de não hospedados.  
  
 O exemplo a seguir fornece uma visão geral das diferentes seções dos arquivos de lote para que eles podem ser modificados para executar a configuração apropriada.  
  
-   Criando o certificado do servidor.  
  
     As seguintes linhas do arquivo em lotes bat criam o certificado do servidor a ser usado. A variável % SERVER_NAME % Especifica o nome do servidor. Altere essa variável para especificar seu próprio nome de servidor. Esse arquivo em lotes padrão é-localhost.  
  
     O certificado é armazenado no repositório My (pessoal) em um local de repositório LocalMachine.  
  
    ```  
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
-   Instalando o certificado do servidor no repositório de certificados confiáveis do cliente.  
  
     As seguintes linhas na cópia de arquivo de lote o certificado do servidor Setup. bat as pessoas confiáveis do cliente ao repositório. Esta etapa é necessária porque certificados gerados pelo Makecert.exe não são implicitamente confiáveis pelo sistema do cliente. Se você já tiver um certificado que está enraizado em um certificado de raiz confiável do cliente — por exemplo, um certificado emitido Microsoft — essa etapa de preencher o repositório de certificados de cliente com o certificado do servidor não é necessária.  
  
    ```  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
