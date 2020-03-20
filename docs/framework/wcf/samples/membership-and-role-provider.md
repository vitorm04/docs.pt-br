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
# <a name="membership-and-role-provider"></a><span data-ttu-id="5d653-102">Provedor de função e associação</span><span class="sxs-lookup"><span data-stu-id="5d653-102">Membership and Role Provider</span></span>
<span data-ttu-id="5d653-103">A amostra de Associação e Provedor de Papéis demonstra como um serviço pode usar a ASP.NET membros e provedores de papéis para autenticar e autorizar clientes.</span><span class="sxs-lookup"><span data-stu-id="5d653-103">The Membership and Role Provider sample demonstrates how a service can use the ASP.NET membership and role providers to authenticate and authorize clients.</span></span>  
  
 <span data-ttu-id="5d653-104">Nesta amostra, o cliente é um aplicativo de console (.exe) e o serviço é hospedado pelo Internet Information Services (IIS).</span><span class="sxs-lookup"><span data-stu-id="5d653-104">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5d653-105">O procedimento de configuração e as instruções de construção desta amostra estão localizados no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="5d653-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="5d653-106">A amostra demonstra como:</span><span class="sxs-lookup"><span data-stu-id="5d653-106">The sample demonstrates how:</span></span>  
  
- <span data-ttu-id="5d653-107">Um cliente pode autenticar usando a combinação nome de usuário-senha.</span><span class="sxs-lookup"><span data-stu-id="5d653-107">A client can authenticate by using the username-password combination.</span></span>  
  
- <span data-ttu-id="5d653-108">O servidor pode validar as credenciais do cliente em relação ao provedor de membros ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="5d653-108">The server can validate the client credentials against the ASP.NET membership provider.</span></span>  
  
- <span data-ttu-id="5d653-109">O servidor pode ser autenticado usando o certificado X.509 do servidor.</span><span class="sxs-lookup"><span data-stu-id="5d653-109">The server can be authenticated by using the server's X.509 certificate.</span></span>  
  
- <span data-ttu-id="5d653-110">O servidor pode mapear o cliente autenticado para uma função usando o provedor de ASP.NET função.</span><span class="sxs-lookup"><span data-stu-id="5d653-110">The server can map the authenticated client to a role by using the ASP.NET role provider.</span></span>  
  
- <span data-ttu-id="5d653-111">O servidor pode `PrincipalPermissionAttribute` usar o para controlar o acesso a determinados métodos que são expostos pelo serviço.</span><span class="sxs-lookup"><span data-stu-id="5d653-111">The server can use the `PrincipalPermissionAttribute` to control access to certain methods that are exposed by the service.</span></span>  
  
 <span data-ttu-id="5d653-112">Os provedores de adesão e função são configurados para usar uma loja apoiada pelo SQL Server.</span><span class="sxs-lookup"><span data-stu-id="5d653-112">The membership and role providers are configured to use a store backed by SQL Server.</span></span> <span data-ttu-id="5d653-113">Uma seqüência de conexões e várias opções são especificadas no arquivo de configuração do serviço.</span><span class="sxs-lookup"><span data-stu-id="5d653-113">A connection string and various options are specified in the service configuration file.</span></span> <span data-ttu-id="5d653-114">O provedor de adesão recebe o `SqlMembershipProvider` nome `SqlRoleProvider`enquanto o provedor de função recebe o nome .</span><span class="sxs-lookup"><span data-stu-id="5d653-114">The membership provider is given the name `SqlMembershipProvider` while the role provider is given the name `SqlRoleProvider`.</span></span>  
  
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
  
 <span data-ttu-id="5d653-115">O serviço expõe um único ponto final para se comunicar com o serviço, que é definido usando o arquivo de configuração Web.config.</span><span class="sxs-lookup"><span data-stu-id="5d653-115">The service exposes a single endpoint for communicating with the service, which is defined by using the Web.config configuration file.</span></span> <span data-ttu-id="5d653-116">O ponto final consiste em um endereço, um vinculativo e um contrato.</span><span class="sxs-lookup"><span data-stu-id="5d653-116">The endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="5d653-117">A vinculação é configurada com um padrão `wsHttpBinding`, que é padrão para usar a autenticação do Windows.</span><span class="sxs-lookup"><span data-stu-id="5d653-117">The binding is configured with a standard `wsHttpBinding`, which defaults to using Windows authentication.</span></span> <span data-ttu-id="5d653-118">Esta amostra define `wsHttpBinding` o padrão para usar autenticação de nome de usuário.</span><span class="sxs-lookup"><span data-stu-id="5d653-118">This sample sets the standard `wsHttpBinding` to use username authentication.</span></span> <span data-ttu-id="5d653-119">O comportamento especifica que o certificado do servidor deve ser usado para autenticação de serviço.</span><span class="sxs-lookup"><span data-stu-id="5d653-119">The behavior specifies that the server certificate is to be used for service authentication.</span></span> <span data-ttu-id="5d653-120">O certificado de servidor deve `SubjectName` conter `findValue` o mesmo valor para o atributo no [ \<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) elemento de configuração.</span><span class="sxs-lookup"><span data-stu-id="5d653-120">The server certificate must contain the same value for the `SubjectName` as the `findValue` attribute in the [\<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) configuration element.</span></span> <span data-ttu-id="5d653-121">Além disso, o comportamento especifica que a autenticação de pares de nome de usuário-senha é realizada pelo provedor de membros ASP.NET e o mapeamento de função é realizado pelo provedor de função ASP.NET, especificando os nomes definidos para os dois provedores.</span><span class="sxs-lookup"><span data-stu-id="5d653-121">In addition the behavior specifies that authentication of username-password pairs is performed by the ASP.NET membership provider and role mapping is performed by the ASP.NET role provider by specifying the names defined for the two providers.</span></span>  
  
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
  
 <span data-ttu-id="5d653-122">Quando você executa a amostra, o cliente liga para as várias operações de serviço em três diferentes contas de usuário: Alice, Bob e Charlie.</span><span class="sxs-lookup"><span data-stu-id="5d653-122">When you run the sample, the client calls the various service operations under three different user accounts: Alice, Bob, and Charlie.</span></span> <span data-ttu-id="5d653-123">As solicitações e respostas da operação são exibidas na janela do console do cliente.</span><span class="sxs-lookup"><span data-stu-id="5d653-123">The operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="5d653-124">Todas as quatro chamadas feitas como usuário "Alice" devem ter sucesso.</span><span class="sxs-lookup"><span data-stu-id="5d653-124">All four calls made as user "Alice" should succeed.</span></span> <span data-ttu-id="5d653-125">O usuário "Bob" deve ter um erro de acesso negado ao tentar chamar o método Dividir.</span><span class="sxs-lookup"><span data-stu-id="5d653-125">User "Bob" should get an access denied error when trying to call the Divide method.</span></span> <span data-ttu-id="5d653-126">O usuário "Charlie" deve ter um erro de acesso negado ao tentar chamar o método Multiply.</span><span class="sxs-lookup"><span data-stu-id="5d653-126">User "Charlie" should get an access denied error when trying to call the Multiply method.</span></span> <span data-ttu-id="5d653-127">Pressione ENTER na janela do cliente para desligar o cliente.</span><span class="sxs-lookup"><span data-stu-id="5d653-127">Press ENTER in the client window to shut down the client.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="5d653-128">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="5d653-128">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="5d653-129">Para construir a edição C# ou Visual Basic .NET da solução, siga as instruções em [Executar as Amostras da Fundação de Comunicação do Windows](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="5d653-129">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
2. <span data-ttu-id="5d653-130">Certifique-se de que você configurou o [banco de dados de serviços de aplicativos ASP.NET](https://go.microsoft.com/fwlink/?LinkId=94997).</span><span class="sxs-lookup"><span data-stu-id="5d653-130">Ensure that you have configured the [ASP.NET Application Services Database](https://go.microsoft.com/fwlink/?LinkId=94997).</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="5d653-131">Se você estiver executando o SQL Server Express Edition, o nome do servidor é .\SQLEXPRESS.</span><span class="sxs-lookup"><span data-stu-id="5d653-131">If you are running SQL Server Express Edition, your server name is .\SQLEXPRESS.</span></span> <span data-ttu-id="5d653-132">Este servidor deve ser usado ao configurar o banco de dados de serviços de aplicativos ASP.NET, bem como na seqüência de conexões Web.config.</span><span class="sxs-lookup"><span data-stu-id="5d653-132">This server should be used when configuring the ASP.NET Application Services Database as well as in the Web.config connection string.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="5d653-133">A conta ASP.NET do processo do trabalhador deve ter permissões no banco de dados que é criado nesta etapa.</span><span class="sxs-lookup"><span data-stu-id="5d653-133">The ASP.NET worker process account must have permissions on the database that is created in this step.</span></span> <span data-ttu-id="5d653-134">Use o utilitário sqlcmd ou o SQL Server Management Studio para fazer isso.</span><span class="sxs-lookup"><span data-stu-id="5d653-134">Use the sqlcmd utility or SQL Server Management Studio to do this.</span></span>  
  
3. <span data-ttu-id="5d653-135">Para executar a amostra em uma configuração de computador único ou cruzado, use as seguintes instruções.</span><span class="sxs-lookup"><span data-stu-id="5d653-135">To run the sample in a single- or cross-computer configuration, use the following instructions.</span></span>  
  
### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="5d653-136">Para executar a amostra no mesmo computador</span><span class="sxs-lookup"><span data-stu-id="5d653-136">To run the sample on the same computer</span></span>  
  
1. <span data-ttu-id="5d653-137">Certifique-se de que o caminho inclui a pasta onde o Makecert.exe está localizado.</span><span class="sxs-lookup"><span data-stu-id="5d653-137">Make sure that the path includes the folder where Makecert.exe is located.</span></span>  
  
2. <span data-ttu-id="5d653-138">Executar setup.bat a partir da pasta de instalação de amostra em um prompt de comando do desenvolvedor para visual studio executado com privilégios de administrador.</span><span class="sxs-lookup"><span data-stu-id="5d653-138">Run Setup.bat from the sample install folder in a Developer Command Prompt for Visual Studio run with administrator privileges.</span></span> <span data-ttu-id="5d653-139">Isso instala os certificados de serviço necessários para executar a amostra.</span><span class="sxs-lookup"><span data-stu-id="5d653-139">This installs the service certificates required for running the sample.</span></span>  
  
3. <span data-ttu-id="5d653-140">Inicie client.exe a partir de \client\bin.</span><span class="sxs-lookup"><span data-stu-id="5d653-140">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="5d653-141">A atividade do cliente é exibida no aplicativo do console cliente.</span><span class="sxs-lookup"><span data-stu-id="5d653-141">Client activity is displayed on the client console application.</span></span>  
  
4. <span data-ttu-id="5d653-142">Se o cliente e o serviço não forem capazes de se comunicar, consulte [Dicas de solução de problemas para amostras wcf](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="5d653-142">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="5d653-143">Para executar a amostra através de computadores</span><span class="sxs-lookup"><span data-stu-id="5d653-143">To run the sample across computers</span></span>  
  
1. <span data-ttu-id="5d653-144">Crie um diretório no computador de serviço.</span><span class="sxs-lookup"><span data-stu-id="5d653-144">Create a directory on the service computer.</span></span> <span data-ttu-id="5d653-145">Crie um aplicativo virtual chamado servicemodelsamples para este diretório usando a ferramenta de gerenciamento de Serviços de Informação da Internet (IIS).</span><span class="sxs-lookup"><span data-stu-id="5d653-145">Create a virtual application named servicemodelsamples for this directory by using the Internet Information Services (IIS) management tool.</span></span>  
  
2. <span data-ttu-id="5d653-146">Copie os arquivos do programa de serviço de \inetpub\wwwroot\servicemodelsamples para o diretório virtual no computador de serviço.</span><span class="sxs-lookup"><span data-stu-id="5d653-146">Copy the service program files from \inetpub\wwwroot\servicemodelsamples to the virtual directory on the service computer.</span></span> <span data-ttu-id="5d653-147">Certifique-se de copiar os arquivos no subdiretório \bin.</span><span class="sxs-lookup"><span data-stu-id="5d653-147">Ensure that you copy the files in the \bin subdirectory.</span></span> <span data-ttu-id="5d653-148">Copie também os arquivos Setup.bat, GetComputerName.vbs e Cleanup.bat para o computador de serviço.</span><span class="sxs-lookup"><span data-stu-id="5d653-148">Also copy the Setup.bat, GetComputerName.vbs, and Cleanup.bat files to the service computer.</span></span>  
  
3. <span data-ttu-id="5d653-149">Crie um diretório no computador cliente para os binários do cliente.</span><span class="sxs-lookup"><span data-stu-id="5d653-149">Create a directory on the client computer for the client binaries.</span></span>  
  
4. <span data-ttu-id="5d653-150">Copie os arquivos do programa cliente para o diretório do cliente no computador cliente.</span><span class="sxs-lookup"><span data-stu-id="5d653-150">Copy the client program files to the client directory on the client computer.</span></span> <span data-ttu-id="5d653-151">Copie também os arquivos Setup.bat, Cleanup.bat e ImportServiceCert.bat para o cliente.</span><span class="sxs-lookup"><span data-stu-id="5d653-151">Also copy the Setup.bat, Cleanup.bat, and ImportServiceCert.bat files to the client.</span></span>  
  
5. <span data-ttu-id="5d653-152">No servidor, abra um Prompt de Comando de Desenvolvedor `setup.bat service`para o Visual Studio com privilégios administrativos e execute .</span><span class="sxs-lookup"><span data-stu-id="5d653-152">On the server, open a Developer Command Prompt for Visual Studio with administrative privileges and run `setup.bat service`.</span></span> <span data-ttu-id="5d653-153">A `setup.bat` execução com o `service` argumento cria um certificado de serviço com o nome de domínio totalmente qualificado do computador e exporta o certificado de serviço para um arquivo chamado Service.cer.</span><span class="sxs-lookup"><span data-stu-id="5d653-153">Running `setup.bat` with the `service` argument creates a service certificate with the fully-qualified domain name of the computer and exports the service certificate to a file named Service.cer.</span></span>  
  
6. <span data-ttu-id="5d653-154">Editar Web.config para refletir o novo `findValue` nome do certificado (no atributo no [ \<serviceCertificate>), ](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)que é o mesmo que o nome de domínio totalmente qualificado do computador.</span><span class="sxs-lookup"><span data-stu-id="5d653-154">Edit Web.config to reflect the new certificate name (in the `findValue` attribute in the [\<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)), which is the same as the fully-qualified domain name of the computer.</span></span>  
  
7. <span data-ttu-id="5d653-155">Copie o arquivo Service.cer do diretório de serviço para o diretório do cliente no computador cliente.</span><span class="sxs-lookup"><span data-stu-id="5d653-155">Copy the Service.cer file from the service directory to the client directory on the client computer.</span></span>  
  
8. <span data-ttu-id="5d653-156">No arquivo Client.exe.config no computador do cliente, altere o valor do endereço do ponto final para corresponder ao novo endereço do seu serviço.</span><span class="sxs-lookup"><span data-stu-id="5d653-156">In the Client.exe.config file on the client computer, change the address value of the endpoint to match the new address of your service.</span></span>  
  
9. <span data-ttu-id="5d653-157">No cliente, abra um Prompt de Comando de Desenvolvedor para o Visual Studio com privilégios administrativos e execute ImportServiceCert.bat.</span><span class="sxs-lookup"><span data-stu-id="5d653-157">On the client, open a Developer Command Prompt for Visual Studio with administrative privileges and run ImportServiceCert.bat.</span></span> <span data-ttu-id="5d653-158">Isso importa o certificado de serviço do arquivo Service.cer para a loja CurrentUser - TrustedPeople.</span><span class="sxs-lookup"><span data-stu-id="5d653-158">This imports the service certificate from the Service.cer file into the CurrentUser - TrustedPeople store.</span></span>  
  
10. <span data-ttu-id="5d653-159">No computador do cliente, inicie client.exe a partir de um prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="5d653-159">On the client computer, launch Client.exe from a command prompt.</span></span> <span data-ttu-id="5d653-160">Se o cliente e o serviço não forem capazes de se comunicar, consulte [Dicas de solução de problemas para amostras wcf](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="5d653-160">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="5d653-161">Para limpar depois da amostra</span><span class="sxs-lookup"><span data-stu-id="5d653-161">To clean up after the sample</span></span>  
  
- <span data-ttu-id="5d653-162">Executar Cleanup.bat na pasta amostras depois de terminar de executar a amostra.</span><span class="sxs-lookup"><span data-stu-id="5d653-162">Run Cleanup.bat in the samples folder after you have finished running the sample.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5d653-163">Este script não remove certificados de serviço em um cliente ao executar essa amostra em computadores.</span><span class="sxs-lookup"><span data-stu-id="5d653-163">This script does not remove service certificates on a client when running this sample across computers.</span></span> <span data-ttu-id="5d653-164">Se você tiver executado amostras de WCF (Windows Communication Foundation, fundação de comunicação do Windows) que usam certificados em computadores, certifique-se de limpar os certificados de serviço que foram instalados na loja CurrentUser - TrustedPeople.</span><span class="sxs-lookup"><span data-stu-id="5d653-164">If you have run Windows Communication Foundation (WCF) samples that use certificates across computers, be sure to clear the service certificates that have been installed in the CurrentUser - TrustedPeople store.</span></span> <span data-ttu-id="5d653-165">Para isso, use o `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` seguinte comando: Por exemplo: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span><span class="sxs-lookup"><span data-stu-id="5d653-165">To do this, use the following command: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` For example: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span></span>  
  
## <a name="the-setup-batch-file"></a><span data-ttu-id="5d653-166">O arquivo de lote de configuração</span><span class="sxs-lookup"><span data-stu-id="5d653-166">The Setup Batch File</span></span>  
 <span data-ttu-id="5d653-167">O arquivo de lote Setup.bat incluído nesta amostra permite configurar o servidor com certificados relevantes para executar um aplicativo auto-hospedado que requer segurança baseada em certificados de servidor.</span><span class="sxs-lookup"><span data-stu-id="5d653-167">The Setup.bat batch file included with this sample allows you to configure the server with relevant certificates to run a self-hosted application that requires server certificate-based security.</span></span> <span data-ttu-id="5d653-168">Este arquivo em lote deve ser modificado para funcionar em computadores ou para funcionar em um caso não hospedado.</span><span class="sxs-lookup"><span data-stu-id="5d653-168">This batch file must be modified to work across computers or to work in a non-hosted case.</span></span>  
  
 <span data-ttu-id="5d653-169">O seguinte fornece uma breve visão geral das diferentes seções dos arquivos em lote para que eles possam ser modificados para serem executados na configuração apropriada.</span><span class="sxs-lookup"><span data-stu-id="5d653-169">The following provides a brief overview of the different sections of the batch files so that they can be modified to run in the appropriate configuration.</span></span>  
  
- <span data-ttu-id="5d653-170">Criando o certificado do servidor.</span><span class="sxs-lookup"><span data-stu-id="5d653-170">Creating the server certificate.</span></span>  
  
     <span data-ttu-id="5d653-171">As seguintes linhas do arquivo setup.bat batch criam o certificado de servidor a ser usado.</span><span class="sxs-lookup"><span data-stu-id="5d653-171">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span> <span data-ttu-id="5d653-172">A variável %SERVER_NAME% especifica o nome do servidor.</span><span class="sxs-lookup"><span data-stu-id="5d653-172">The %SERVER_NAME% variable specifies the server name.</span></span> <span data-ttu-id="5d653-173">Altere essa variável para especificar o nome do seu próprio servidor.</span><span class="sxs-lookup"><span data-stu-id="5d653-173">Change this variable to specify your own server name.</span></span> <span data-ttu-id="5d653-174">Este arquivo de lote é padrão para host local.</span><span class="sxs-lookup"><span data-stu-id="5d653-174">This batch file defaults it to localhost.</span></span>  
  
     <span data-ttu-id="5d653-175">O certificado é armazenado na minha loja (pessoal) a localização da loja LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="5d653-175">The certificate is stored in My (Personal) store under the LocalMachine store location.</span></span>  
  
    ```console
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
- <span data-ttu-id="5d653-176">Instalando o certificado do servidor na loja de certificados confiáveis do cliente.</span><span class="sxs-lookup"><span data-stu-id="5d653-176">Installing the server certificate into the client's trusted certificate store.</span></span>  
  
     <span data-ttu-id="5d653-177">As seguintes linhas no arquivo de lote Setup.bat copiam o certificado do servidor na loja de pessoas confiáveis do cliente.</span><span class="sxs-lookup"><span data-stu-id="5d653-177">The following lines in the Setup.bat batch file copy the server certificate into the client trusted people store.</span></span> <span data-ttu-id="5d653-178">Essa etapa é necessária porque os certificados gerados pelo Makecert.exe não são implicitamente confiáveis pelo sistema cliente.</span><span class="sxs-lookup"><span data-stu-id="5d653-178">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="5d653-179">Se você já tiver um certificado enraizado em um certificado raiz confiável do cliente — por exemplo, um certificado emitido pela Microsoft — essa etapa de povoar a loja de certificados do cliente com o certificado do servidor não é necessária.</span><span class="sxs-lookup"><span data-stu-id="5d653-179">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft-issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>  
  
    ```bat  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
