---
title: Provedor de função e associação
ms.date: 03/30/2017
ms.assetid: 0d11a31c-e75f-4fcf-9cf4-b7f26e056bcd
ms.openlocfilehash: 94808fbb3fae1714f63a4682dfe1096ca314985c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33506682"
---
# <a name="membership-and-role-provider"></a><span data-ttu-id="2ec33-102">Provedor de função e associação</span><span class="sxs-lookup"><span data-stu-id="2ec33-102">Membership and Role Provider</span></span>
<span data-ttu-id="2ec33-103">O provedor de função e associação de exemplo demonstra como um serviço pode usar o [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] provedores de associação e funções para autenticar e autorizar clientes.</span><span class="sxs-lookup"><span data-stu-id="2ec33-103">The Membership and Role Provider sample demonstrates how a service can use the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] membership and role providers to authenticate and authorize clients.</span></span>  
  
 <span data-ttu-id="2ec33-104">Neste exemplo, o cliente é um aplicativo de console (.exe) e o serviço é hospedado por serviços de informações da Internet (IIS).</span><span class="sxs-lookup"><span data-stu-id="2ec33-104">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2ec33-105">As instruções de procedimento e a compilação de configuração para este exemplo estão localizadas no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="2ec33-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="2ec33-106">O exemplo demonstra como:</span><span class="sxs-lookup"><span data-stu-id="2ec33-106">The sample demonstrates how:</span></span>  
  
-   <span data-ttu-id="2ec33-107">Um cliente pode autenticar usando a combinação da senha do nome de usuário.</span><span class="sxs-lookup"><span data-stu-id="2ec33-107">A client can authenticate by using the username-password combination.</span></span>  
  
-   <span data-ttu-id="2ec33-108">O servidor pode validar as credenciais do cliente em relação a [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] provedor de associação.</span><span class="sxs-lookup"><span data-stu-id="2ec33-108">The server can validate the client credentials against the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] membership provider.</span></span>  
  
-   <span data-ttu-id="2ec33-109">O servidor pode ser autenticado usando o certificado do servidor x. 509.</span><span class="sxs-lookup"><span data-stu-id="2ec33-109">The server can be authenticated by using the server's X.509 certificate.</span></span>  
  
-   <span data-ttu-id="2ec33-110">O servidor pode mapear o cliente autenticado a uma função usando o [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] provedor de função.</span><span class="sxs-lookup"><span data-stu-id="2ec33-110">The server can map the authenticated client to a role by using the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] role provider.</span></span>  
  
-   <span data-ttu-id="2ec33-111">O servidor pode usar o `PrincipalPermissionAttribute` para controlar o acesso a determinados métodos que são expostos pelo serviço.</span><span class="sxs-lookup"><span data-stu-id="2ec33-111">The server can use the `PrincipalPermissionAttribute` to control access to certain methods that are exposed by the service.</span></span>  
  
 <span data-ttu-id="2ec33-112">Os provedores de associação e funções estão configurados para usar um repositório de backup feito pelo SQL Server.</span><span class="sxs-lookup"><span data-stu-id="2ec33-112">The membership and role providers are configured to use a store backed by SQL Server.</span></span> <span data-ttu-id="2ec33-113">Uma cadeia de caracteres de conexão e as várias opções são especificadas no arquivo de configuração de serviço.</span><span class="sxs-lookup"><span data-stu-id="2ec33-113">A connection string and various options are specified in the service configuration file.</span></span> <span data-ttu-id="2ec33-114">O provedor de associação é fornecido o nome `SqlMembershipProvider` enquanto o provedor de função recebe o nome `SqlRoleProvider`.</span><span class="sxs-lookup"><span data-stu-id="2ec33-114">The membership provider is given the name `SqlMembershipProvider` while the role provider is given the name `SqlRoleProvider`.</span></span>  
  
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
  
 <span data-ttu-id="2ec33-115">O serviço expõe um ponto de extremidade de comunicação com o serviço, que é definido usando o arquivo de configuração Web. config.</span><span class="sxs-lookup"><span data-stu-id="2ec33-115">The service exposes a single endpoint for communicating with the service, which is defined by using the Web.config configuration file.</span></span> <span data-ttu-id="2ec33-116">O ponto de extremidade consiste em um endereço, uma ligação e um contrato.</span><span class="sxs-lookup"><span data-stu-id="2ec33-116">The endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="2ec33-117">A associação está configurada com um padrão `wsHttpBinding`, que assume como padrão usando a autenticação do Windows.</span><span class="sxs-lookup"><span data-stu-id="2ec33-117">The binding is configured with a standard `wsHttpBinding`, which defaults to using Windows authentication.</span></span> <span data-ttu-id="2ec33-118">Este exemplo define o padrão de `wsHttpBinding` para usar a autenticação de nome de usuário.</span><span class="sxs-lookup"><span data-stu-id="2ec33-118">This sample sets the standard `wsHttpBinding` to use username authentication.</span></span> <span data-ttu-id="2ec33-119">O comportamento Especifica que o certificado do servidor a ser usado para autenticação do serviço.</span><span class="sxs-lookup"><span data-stu-id="2ec33-119">The behavior specifies that the server certificate is to be used for service authentication.</span></span> <span data-ttu-id="2ec33-120">O certificado do servidor deve conter o mesmo valor para o `SubjectName` como o `findValue` atributo o [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) elemento de configuração.</span><span class="sxs-lookup"><span data-stu-id="2ec33-120">The server certificate must contain the same value for the `SubjectName` as the `findValue` attribute in the [\<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) configuration element.</span></span> <span data-ttu-id="2ec33-121">Além disso, o comportamento Especifica que a autenticação de senha do nome de usuário pares é executada pelo [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] provedor de associação e mapeamento de função é realizada pelo [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] provedor de função, especificando os nomes definidos para os dois provedores.</span><span class="sxs-lookup"><span data-stu-id="2ec33-121">In addition the behavior specifies that authentication of username-password pairs is performed by the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] membership provider and role mapping is performed by the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] role provider by specifying the names defined for the two providers.</span></span>  
  
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
  
 <span data-ttu-id="2ec33-122">Quando você executar o exemplo, o cliente chama as várias operações de serviço em três diferentes contas de usuário: Alice e Bob Charlie.</span><span class="sxs-lookup"><span data-stu-id="2ec33-122">When you run the sample, the client calls the various service operations under three different user accounts: Alice, Bob, and Charlie.</span></span> <span data-ttu-id="2ec33-123">As respostas e solicitações de operação são exibidas na janela do console do cliente.</span><span class="sxs-lookup"><span data-stu-id="2ec33-123">The operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="2ec33-124">Todas as quatro chamadas feitas como usuário "Alice" deve ter êxito.</span><span class="sxs-lookup"><span data-stu-id="2ec33-124">All four calls made as user "Alice" should succeed.</span></span> <span data-ttu-id="2ec33-125">O usuário "Bob" deve obter um erro de acesso negado ao tentar chamar o método de divisão.</span><span class="sxs-lookup"><span data-stu-id="2ec33-125">User "Bob" should get an access denied error when trying to call the Divide method.</span></span> <span data-ttu-id="2ec33-126">O usuário "Charlie" deve receber um erro de acesso negado ao tentar chamar o método Multiply.</span><span class="sxs-lookup"><span data-stu-id="2ec33-126">User "Charlie" should get an access denied error when trying to call the Multiply method.</span></span> <span data-ttu-id="2ec33-127">Pressione ENTER na janela do cliente para desligar o cliente.</span><span class="sxs-lookup"><span data-stu-id="2ec33-127">Press ENTER in the client window to shut down the client.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="2ec33-128">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="2ec33-128">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="2ec33-129">Para compilar o c# ou Visual Basic .NET edição da solução, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="2ec33-129">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
2.  <span data-ttu-id="2ec33-130">Certifique-se de que você tenha configurado o [banco de dados de serviços de aplicativo ASP.NET](http://go.microsoft.com/fwlink/?LinkId=94997).</span><span class="sxs-lookup"><span data-stu-id="2ec33-130">Ensure that you have configured the [ASP.NET Application Services Database](http://go.microsoft.com/fwlink/?LinkId=94997).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="2ec33-131">Se você estiver executando o SQL Server Express Edition, é o nome do servidor. \SQLEXPRESS.</span><span class="sxs-lookup"><span data-stu-id="2ec33-131">If you are running SQL Server Express Edition, your server name is .\SQLEXPRESS.</span></span> <span data-ttu-id="2ec33-132">Esse servidor deve ser usado ao configurar o [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aplicativo Serviços de banco de dados, bem como a cadeia de caracteres de conexão do Web. config.</span><span class="sxs-lookup"><span data-stu-id="2ec33-132">This server should be used when configuring the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Application Services Database as well as in the Web.config connection string.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="2ec33-133">O [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] conta de processo do operador deve ter permissões no banco de dados é criado nesta etapa.</span><span class="sxs-lookup"><span data-stu-id="2ec33-133">The [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] worker process account must have permissions on the database that is created in this step.</span></span> <span data-ttu-id="2ec33-134">Use o utilitário sqlcmd ou o SQL Server Management Studio para fazer isso.</span><span class="sxs-lookup"><span data-stu-id="2ec33-134">Use the sqlcmd utility or SQL Server Management Studio to do this.</span></span>  
  
3.  <span data-ttu-id="2ec33-135">Para executar o exemplo em uma configuração ou entre computadores, use as instruções a seguir.</span><span class="sxs-lookup"><span data-stu-id="2ec33-135">To run the sample in a single- or cross-computer configuration, use the following instructions.</span></span>  
  
### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="2ec33-136">Para executar o exemplo no mesmo computador</span><span class="sxs-lookup"><span data-stu-id="2ec33-136">To run the sample on the same computer</span></span>  
  
1.  <span data-ttu-id="2ec33-137">Certifique-se de que o caminho inclui a pasta onde Makecert.exe está localizado.</span><span class="sxs-lookup"><span data-stu-id="2ec33-137">Make sure that the path includes the folder where Makecert.exe is located.</span></span>  
  
2.  <span data-ttu-id="2ec33-138">Execute bat da pasta de instalação de exemplo em um prompt de comando do Visual Studio executar com privilégios de administrador.</span><span class="sxs-lookup"><span data-stu-id="2ec33-138">Run Setup.bat from the sample install folder in a Visual Studio command prompt run with administrator privileges.</span></span> <span data-ttu-id="2ec33-139">Isso instala os certificados de serviço necessários para executar o exemplo.</span><span class="sxs-lookup"><span data-stu-id="2ec33-139">This installs the service certificates required for running the sample.</span></span>  
  
3.  <span data-ttu-id="2ec33-140">Inicie Client.exe de \Client\Bin.</span><span class="sxs-lookup"><span data-stu-id="2ec33-140">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="2ec33-141">Atividade do cliente é exibida no aplicativo de console do cliente.</span><span class="sxs-lookup"><span data-stu-id="2ec33-141">Client activity is displayed on the client console application.</span></span>  
  
4.  <span data-ttu-id="2ec33-142">Se o cliente e o serviço não for capazes de se comunicar, consulte [dicas de solução de problemas](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span><span class="sxs-lookup"><span data-stu-id="2ec33-142">If the client and service are not able to communicate, see [Troubleshooting Tips](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="2ec33-143">Para executar o exemplo em computadores</span><span class="sxs-lookup"><span data-stu-id="2ec33-143">To run the sample across computers</span></span>  
  
1.  <span data-ttu-id="2ec33-144">Crie um diretório no computador de serviço.</span><span class="sxs-lookup"><span data-stu-id="2ec33-144">Create a directory on the service computer.</span></span> <span data-ttu-id="2ec33-145">Crie um aplicativo virtual denominado servicemodelsamples para este diretório usando a ferramenta de gerenciamento de serviços de informações da Internet (IIS).</span><span class="sxs-lookup"><span data-stu-id="2ec33-145">Create a virtual application named servicemodelsamples for this directory by using the Internet Information Services (IIS) management tool.</span></span>  
  
2.  <span data-ttu-id="2ec33-146">Copie os arquivos de programa do serviço de \inetpub\wwwroot\servicemodelsamples para o diretório virtual no computador de serviço.</span><span class="sxs-lookup"><span data-stu-id="2ec33-146">Copy the service program files from \inetpub\wwwroot\servicemodelsamples to the virtual directory on the service computer.</span></span> <span data-ttu-id="2ec33-147">Certifique-se de que você copiar os arquivos no subdiretório \bin.</span><span class="sxs-lookup"><span data-stu-id="2ec33-147">Ensure that you copy the files in the \bin subdirectory.</span></span> <span data-ttu-id="2ec33-148">Também copie os arquivos. bat, GetComputerName.vbs e Cleanup.bat para o computador do serviço.</span><span class="sxs-lookup"><span data-stu-id="2ec33-148">Also copy the Setup.bat, GetComputerName.vbs, and Cleanup.bat files to the service computer.</span></span>  
  
3.  <span data-ttu-id="2ec33-149">Crie um diretório no computador cliente para os binários do cliente.</span><span class="sxs-lookup"><span data-stu-id="2ec33-149">Create a directory on the client computer for the client binaries.</span></span>  
  
4.  <span data-ttu-id="2ec33-150">Copie os arquivos de programa do cliente para o diretório de cliente no computador cliente.</span><span class="sxs-lookup"><span data-stu-id="2ec33-150">Copy the client program files to the client directory on the client computer.</span></span> <span data-ttu-id="2ec33-151">Também copie os arquivos. bat, Cleanup.bat e ImportServiceCert.bat ao cliente.</span><span class="sxs-lookup"><span data-stu-id="2ec33-151">Also copy the Setup.bat, Cleanup.bat, and ImportServiceCert.bat files to the client.</span></span>  
  
5.  <span data-ttu-id="2ec33-152">No servidor, abra um prompt de comando do Visual Studio com privilégios administrativos e execute `setup.bat service`.</span><span class="sxs-lookup"><span data-stu-id="2ec33-152">On the server, open a Visual Studio command prompt with administrative privileges and run `setup.bat service`.</span></span> <span data-ttu-id="2ec33-153">Executando `setup.bat` com o `service` argumento cria um certificado de serviço com o nome de domínio totalmente qualificado do computador e exporta o certificado de serviço para um arquivo chamado Service.cer.</span><span class="sxs-lookup"><span data-stu-id="2ec33-153">Running `setup.bat` with the `service` argument creates a service certificate with the fully-qualified domain name of the computer and exports the service certificate to a file named Service.cer.</span></span>  
  
6.  <span data-ttu-id="2ec33-154">Editar o Web. config para refletir o novo nome de certificado (no `findValue` atributo o [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)), que é o mesmo que o nome de domínio totalmente qualificado do computador.</span><span class="sxs-lookup"><span data-stu-id="2ec33-154">Edit Web.config to reflect the new certificate name (in the `findValue` attribute in the [\<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)), which is the same as the fully-qualified domain name of the computer.</span></span>  
  
7.  <span data-ttu-id="2ec33-155">Copie o arquivo de Service.cer do diretório de serviço para o diretório do cliente no computador cliente.</span><span class="sxs-lookup"><span data-stu-id="2ec33-155">Copy the Service.cer file from the service directory to the client directory on the client computer.</span></span>  
  
8.  <span data-ttu-id="2ec33-156">No arquivo Client.exe.config no computador cliente, altere o valor do endereço do ponto de extremidade para coincidir com o novo endereço do seu serviço.</span><span class="sxs-lookup"><span data-stu-id="2ec33-156">In the Client.exe.config file on the client computer, change the address value of the endpoint to match the new address of your service.</span></span>  
  
9. <span data-ttu-id="2ec33-157">No cliente, abra um prompt de comando do Visual Studio com privilégios administrativos e execute ImportServiceCert.bat.</span><span class="sxs-lookup"><span data-stu-id="2ec33-157">On the client, open a Visual Studio command prompt with administrative privileges and run ImportServiceCert.bat.</span></span> <span data-ttu-id="2ec33-158">Isso importa o certificado de serviço do arquivo Service.cer para CurrentUser - TrustedPeople repositório.</span><span class="sxs-lookup"><span data-stu-id="2ec33-158">This imports the service certificate from the Service.cer file into the CurrentUser - TrustedPeople store.</span></span>  
  
10. <span data-ttu-id="2ec33-159">No computador cliente, inicie o Client.exe em um prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="2ec33-159">On the client computer, launch Client.exe from a command prompt.</span></span> <span data-ttu-id="2ec33-160">Se o cliente e o serviço não for capazes de se comunicar, consulte [dicas de solução de problemas](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span><span class="sxs-lookup"><span data-stu-id="2ec33-160">If the client and service are not able to communicate, see [Troubleshooting Tips](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="2ec33-161">A limpeza após a amostra</span><span class="sxs-lookup"><span data-stu-id="2ec33-161">To clean up after the sample</span></span>  
  
-   <span data-ttu-id="2ec33-162">Execute Cleanup.bat na pasta exemplos depois de terminar de executar o exemplo.</span><span class="sxs-lookup"><span data-stu-id="2ec33-162">Run Cleanup.bat in the samples folder after you have finished running the sample.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2ec33-163">Esse script não remove os certificados de serviço em um cliente ao executar este exemplo entre computadores.</span><span class="sxs-lookup"><span data-stu-id="2ec33-163">This script does not remove service certificates on a client when running this sample across computers.</span></span> <span data-ttu-id="2ec33-164">Se você executou os exemplos do Windows Communication Foundation (WCF) que usam certificados em computadores, certifique-se de limpar os certificados de serviço que foram instalados em CurrentUser - TrustedPeople repositório.</span><span class="sxs-lookup"><span data-stu-id="2ec33-164">If you have run Windows Communication Foundation (WCF) samples that use certificates across computers, be sure to clear the service certificates that have been installed in the CurrentUser - TrustedPeople store.</span></span> <span data-ttu-id="2ec33-165">Para fazer isso, use o seguinte comando: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` por exemplo: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span><span class="sxs-lookup"><span data-stu-id="2ec33-165">To do this, use the following command: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` For example: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span></span>  
  
## <a name="the-setup-batch-file"></a><span data-ttu-id="2ec33-166">O arquivo de lote</span><span class="sxs-lookup"><span data-stu-id="2ec33-166">The Setup Batch File</span></span>  
 <span data-ttu-id="2ec33-167">Arquivo em lotes bat incluído com este exemplo permite que você configure o servidor com certificados relevantes para executar um aplicativo auto-hospedado que exige a segurança baseada em certificado do servidor.</span><span class="sxs-lookup"><span data-stu-id="2ec33-167">The Setup.bat batch file included with this sample allows you to configure the server with relevant certificates to run a self-hosted application that requires server certificate-based security.</span></span> <span data-ttu-id="2ec33-168">Esse arquivo em lotes deve ser modificado para funcionar entre computadores ou para trabalhar em um caso não hospedado.</span><span class="sxs-lookup"><span data-stu-id="2ec33-168">This batch file must be modified to work across computers or to work in a non-hosted case.</span></span>  
  
 <span data-ttu-id="2ec33-169">O exemplo a seguir fornece uma visão geral das seções diferentes dos arquivos de lote para que eles podem ser modificados para executar a configuração apropriada.</span><span class="sxs-lookup"><span data-stu-id="2ec33-169">The following provides a brief overview of the different sections of the batch files so that they can be modified to run in the appropriate configuration.</span></span>  
  
-   <span data-ttu-id="2ec33-170">Criando o certificado do servidor.</span><span class="sxs-lookup"><span data-stu-id="2ec33-170">Creating the server certificate.</span></span>  
  
     <span data-ttu-id="2ec33-171">As seguintes linhas do arquivo em lotes bat criam o certificado do servidor a ser usado.</span><span class="sxs-lookup"><span data-stu-id="2ec33-171">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span> <span data-ttu-id="2ec33-172">A variável % SERVER_NAME % Especifica o nome do servidor.</span><span class="sxs-lookup"><span data-stu-id="2ec33-172">The %SERVER_NAME% variable specifies the server name.</span></span> <span data-ttu-id="2ec33-173">Altere essa variável para especificar seu próprio nome de servidor.</span><span class="sxs-lookup"><span data-stu-id="2ec33-173">Change this variable to specify your own server name.</span></span> <span data-ttu-id="2ec33-174">Esse arquivo em lote padrão é-localhost.</span><span class="sxs-lookup"><span data-stu-id="2ec33-174">This batch file defaults it to localhost.</span></span>  
  
     <span data-ttu-id="2ec33-175">O certificado é armazenado no repositório My (pessoal) em um local de repositório LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="2ec33-175">The certificate is stored in My (Personal) store under the LocalMachine store location.</span></span>  
  
    ```  
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
-   <span data-ttu-id="2ec33-176">Instalando o certificado de servidor no repositório de certificados confiáveis do cliente.</span><span class="sxs-lookup"><span data-stu-id="2ec33-176">Installing the server certificate into the client's trusted certificate store.</span></span>  
  
     <span data-ttu-id="2ec33-177">Armazenam as linhas a seguir na cópia de arquivo de lote o certificado do servidor bat para as pessoas confiáveis do cliente.</span><span class="sxs-lookup"><span data-stu-id="2ec33-177">The following lines in the Setup.bat batch file copy the server certificate into the client trusted people store.</span></span> <span data-ttu-id="2ec33-178">Esta etapa é necessária porque os certificados gerados pela Makecert.exe não são implicitamente confiáveis pelo sistema do cliente.</span><span class="sxs-lookup"><span data-stu-id="2ec33-178">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="2ec33-179">Se você já tiver um certificado que está enraizado em um certificado de raiz confiável do cliente — por exemplo, um certificado emitido Microsoft — essa etapa de preenchimento do repositório de certificados de cliente com o certificado do servidor não é necessária.</span><span class="sxs-lookup"><span data-stu-id="2ec33-179">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft-issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>  
  
    ```  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="2ec33-180">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2ec33-180">See Also</span></span>
