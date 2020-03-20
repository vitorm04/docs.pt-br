---
title: Provedor de função e associação
ms.date: 03/30/2017
ms.assetid: 0d11a31c-e75f-4fcf-9cf4-b7f26e056bcd
ms.openlocfilehash: 117be783c2d4a72ff9d1c4509566274b1043a43d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144455"
---
# <a name="membership-and-role-provider"></a>Provedor de função e associação
A amostra de Associação e Provedor de Papéis demonstra como um serviço pode usar a ASP.NET membros e provedores de papéis para autenticar e autorizar clientes.  
  
 Nesta amostra, o cliente é um aplicativo de console (.exe) e o serviço é hospedado pelo Internet Information Services (IIS).  
  
> [!NOTE]
> O procedimento de configuração e as instruções de construção desta amostra estão localizados no final deste tópico.  
  
 A amostra demonstra como:  
  
- Um cliente pode autenticar usando a combinação nome de usuário-senha.  
  
- O servidor pode validar as credenciais do cliente em relação ao provedor de membros ASP.NET.  
  
- O servidor pode ser autenticado usando o certificado X.509 do servidor.  
  
- O servidor pode mapear o cliente autenticado para uma função usando o provedor de ASP.NET função.  
  
- O servidor pode `PrincipalPermissionAttribute` usar o para controlar o acesso a determinados métodos que são expostos pelo serviço.  
  
 Os provedores de adesão e função são configurados para usar uma loja apoiada pelo SQL Server. Uma seqüência de conexões e várias opções são especificadas no arquivo de configuração do serviço. O provedor de adesão recebe o `SqlMembershipProvider` nome `SqlRoleProvider`enquanto o provedor de função recebe o nome .  
  
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
  
 O serviço expõe um único ponto final para se comunicar com o serviço, que é definido usando o arquivo de configuração Web.config. O ponto final consiste em um endereço, um vinculativo e um contrato. A vinculação é configurada com um padrão `wsHttpBinding`, que é padrão para usar a autenticação do Windows. Esta amostra define `wsHttpBinding` o padrão para usar autenticação de nome de usuário. O comportamento especifica que o certificado do servidor deve ser usado para autenticação de serviço. O certificado de servidor deve `SubjectName` conter `findValue` o mesmo valor para o atributo no [ \<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) elemento de configuração. Além disso, o comportamento especifica que a autenticação de pares de nome de usuário-senha é realizada pelo provedor de membros ASP.NET e o mapeamento de função é realizado pelo provedor de função ASP.NET, especificando os nomes definidos para os dois provedores.  
  
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
  
 Quando você executa a amostra, o cliente liga para as várias operações de serviço em três diferentes contas de usuário: Alice, Bob e Charlie. As solicitações e respostas da operação são exibidas na janela do console do cliente. Todas as quatro chamadas feitas como usuário "Alice" devem ter sucesso. O usuário "Bob" deve ter um erro de acesso negado ao tentar chamar o método Dividir. O usuário "Charlie" deve ter um erro de acesso negado ao tentar chamar o método Multiply. Pressione ENTER na janela do cliente para desligar o cliente.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1. Para construir a edição C# ou Visual Basic .NET da solução, siga as instruções em [Executar as Amostras da Fundação de Comunicação do Windows](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
2. Certifique-se de que você configurou o [banco de dados de serviços de aplicativos ASP.NET](https://go.microsoft.com/fwlink/?LinkId=94997).  
  
    > [!NOTE]
    > Se você estiver executando o SQL Server Express Edition, o nome do servidor é .\SQLEXPRESS. Este servidor deve ser usado ao configurar o banco de dados de serviços de aplicativos ASP.NET, bem como na seqüência de conexões Web.config.  
  
    > [!NOTE]
    > A conta ASP.NET do processo do trabalhador deve ter permissões no banco de dados que é criado nesta etapa. Use o utilitário sqlcmd ou o SQL Server Management Studio para fazer isso.  
  
3. Para executar a amostra em uma configuração de computador único ou cruzado, use as seguintes instruções.  
  
### <a name="to-run-the-sample-on-the-same-computer"></a>Para executar a amostra no mesmo computador  
  
1. Certifique-se de que o caminho inclui a pasta onde o Makecert.exe está localizado.  
  
2. Executar setup.bat a partir da pasta de instalação de amostra em um prompt de comando do desenvolvedor para visual studio executado com privilégios de administrador. Isso instala os certificados de serviço necessários para executar a amostra.  
  
3. Inicie client.exe a partir de \client\bin. A atividade do cliente é exibida no aplicativo do console cliente.  
  
4. Se o cliente e o serviço não forem capazes de se comunicar, consulte [Dicas de solução de problemas para amostras wcf](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
### <a name="to-run-the-sample-across-computers"></a>Para executar a amostra através de computadores  
  
1. Crie um diretório no computador de serviço. Crie um aplicativo virtual chamado servicemodelsamples para este diretório usando a ferramenta de gerenciamento de Serviços de Informação da Internet (IIS).  
  
2. Copie os arquivos do programa de serviço de \inetpub\wwwroot\servicemodelsamples para o diretório virtual no computador de serviço. Certifique-se de copiar os arquivos no subdiretório \bin. Copie também os arquivos Setup.bat, GetComputerName.vbs e Cleanup.bat para o computador de serviço.  
  
3. Crie um diretório no computador cliente para os binários do cliente.  
  
4. Copie os arquivos do programa cliente para o diretório do cliente no computador cliente. Copie também os arquivos Setup.bat, Cleanup.bat e ImportServiceCert.bat para o cliente.  
  
5. No servidor, abra um Prompt de Comando de Desenvolvedor `setup.bat service`para o Visual Studio com privilégios administrativos e execute . A `setup.bat` execução com o `service` argumento cria um certificado de serviço com o nome de domínio totalmente qualificado do computador e exporta o certificado de serviço para um arquivo chamado Service.cer.  
  
6. Editar Web.config para refletir o novo `findValue` nome do certificado (no atributo no [ \<serviceCertificate>), ](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)que é o mesmo que o nome de domínio totalmente qualificado do computador.  
  
7. Copie o arquivo Service.cer do diretório de serviço para o diretório do cliente no computador cliente.  
  
8. No arquivo Client.exe.config no computador do cliente, altere o valor do endereço do ponto final para corresponder ao novo endereço do seu serviço.  
  
9. No cliente, abra um Prompt de Comando de Desenvolvedor para o Visual Studio com privilégios administrativos e execute ImportServiceCert.bat. Isso importa o certificado de serviço do arquivo Service.cer para a loja CurrentUser - TrustedPeople.  
  
10. No computador do cliente, inicie client.exe a partir de um prompt de comando. Se o cliente e o serviço não forem capazes de se comunicar, consulte [Dicas de solução de problemas para amostras wcf](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
### <a name="to-clean-up-after-the-sample"></a>Para limpar depois da amostra  
  
- Executar Cleanup.bat na pasta amostras depois de terminar de executar a amostra.  
  
> [!NOTE]
> Este script não remove certificados de serviço em um cliente ao executar essa amostra em computadores. Se você tiver executado amostras de WCF (Windows Communication Foundation, fundação de comunicação do Windows) que usam certificados em computadores, certifique-se de limpar os certificados de serviço que foram instalados na loja CurrentUser - TrustedPeople. Para isso, use o `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` seguinte comando: Por exemplo: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.  
  
## <a name="the-setup-batch-file"></a>O arquivo de lote de configuração  
 O arquivo de lote Setup.bat incluído nesta amostra permite configurar o servidor com certificados relevantes para executar um aplicativo auto-hospedado que requer segurança baseada em certificados de servidor. Este arquivo em lote deve ser modificado para funcionar em computadores ou para funcionar em um caso não hospedado.  
  
 O seguinte fornece uma breve visão geral das diferentes seções dos arquivos em lote para que eles possam ser modificados para serem executados na configuração apropriada.  
  
- Criando o certificado do servidor.  
  
     As seguintes linhas do arquivo setup.bat batch criam o certificado de servidor a ser usado. A variável %SERVER_NAME% especifica o nome do servidor. Altere essa variável para especificar o nome do seu próprio servidor. Este arquivo de lote é padrão para host local.  
  
     O certificado é armazenado na minha loja (pessoal) a localização da loja LocalMachine.  
  
    ```console
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
- Instalando o certificado do servidor na loja de certificados confiáveis do cliente.  
  
     As seguintes linhas no arquivo de lote Setup.bat copiam o certificado do servidor na loja de pessoas confiáveis do cliente. Essa etapa é necessária porque os certificados gerados pelo Makecert.exe não são implicitamente confiáveis pelo sistema cliente. Se você já tiver um certificado enraizado em um certificado raiz confiável do cliente — por exemplo, um certificado emitido pela Microsoft — essa etapa de povoar a loja de certificados do cliente com o certificado do servidor não é necessária.  
  
    ```bat  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
