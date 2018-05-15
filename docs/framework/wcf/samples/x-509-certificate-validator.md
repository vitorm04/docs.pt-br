---
title: Validador de certificado X.509
ms.date: 03/30/2017
ms.assetid: 3b042379-02c4-4395-b927-e57c842fd3e0
ms.openlocfilehash: 3d9aa14af3ded11bcd373f38656763036e83b0bf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="x509-certificate-validator"></a><span data-ttu-id="815db-102">Validador de certificado X.509</span><span class="sxs-lookup"><span data-stu-id="815db-102">X.509 Certificate Validator</span></span>
<span data-ttu-id="815db-103">Este exemplo demonstra como implementar um validador personalizado de certificado x. 509.</span><span class="sxs-lookup"><span data-stu-id="815db-103">This sample demonstrates how to implement a custom X.509 Certificate Validator.</span></span> <span data-ttu-id="815db-104">Isso é útil em casos em que nenhum dos modos de validação do certificado x. 509 internos é adequado para os requisitos do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="815db-104">This is useful in cases where none of the built-in X.509 Certificate Validation modes is appropriate for the requirements of the application.</span></span> <span data-ttu-id="815db-105">Este exemplo mostra um serviço que tenha um validador personalizado que aceita os certificados emitidos por conta própria.</span><span class="sxs-lookup"><span data-stu-id="815db-105">This sample shows a service that has a custom validator that accepts self-issued certificates.</span></span> <span data-ttu-id="815db-106">O cliente usa esse certificado para autenticar no serviço.</span><span class="sxs-lookup"><span data-stu-id="815db-106">The client uses such a certificate to authenticate to the service.</span></span>  
  
 <span data-ttu-id="815db-107">Observação: como qualquer pessoa pode construir um certificado emitido o validador personalizado usado pelo serviço é menos seguro do que o comportamento padrão fornecido pelo ChainTrust X509CertificateValidationMode.</span><span class="sxs-lookup"><span data-stu-id="815db-107">Note: As anyone can construct a self-issued certificate the custom validator used by the service is less secure than the default behavior provided by the ChainTrust X509CertificateValidationMode.</span></span> <span data-ttu-id="815db-108">As implicações de segurança, isso devem ser consideradas cuidadosamente antes de usar essa lógica de validação no código de produção.</span><span class="sxs-lookup"><span data-stu-id="815db-108">The security implications of this should be carefully considered before using this validation logic in production code.</span></span>  
  
 <span data-ttu-id="815db-109">Em resumo Este exemplo demonstra como:</span><span class="sxs-lookup"><span data-stu-id="815db-109">In summary this sample demonstrates how:</span></span>  
  
-   <span data-ttu-id="815db-110">O cliente pode ser autenticado usando um certificado x. 509.</span><span class="sxs-lookup"><span data-stu-id="815db-110">The client can be authenticated using an X.509 certificate.</span></span>  
  
-   <span data-ttu-id="815db-111">O servidor valida as credenciais do cliente em relação a um X509CertificateValidator personalizado.</span><span class="sxs-lookup"><span data-stu-id="815db-111">The server validates the client credentials against a custom X509CertificateValidator.</span></span>  
  
-   <span data-ttu-id="815db-112">O servidor é autenticado usando o certificado do servidor x. 509.</span><span class="sxs-lookup"><span data-stu-id="815db-112">The server is authenticated using the server's X.509 certificate.</span></span>  
  
 <span data-ttu-id="815db-113">O serviço expõe um ponto de extremidade de comunicação com o serviço, definido usando o arquivo de configuração App. config. O ponto de extremidade consiste em um endereço, uma ligação e um contrato.</span><span class="sxs-lookup"><span data-stu-id="815db-113">The service exposes a single endpoint for communicating with the service, defined using the configuration file App.config. The endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="815db-114">A associação está configurada com um padrão `wsHttpBinding` que foi padronizado para usar `WSSecurity` e autenticação de certificado de cliente.</span><span class="sxs-lookup"><span data-stu-id="815db-114">The binding is configured with a standard `wsHttpBinding` that defaults to using `WSSecurity` and client certificate authentication.</span></span> <span data-ttu-id="815db-115">O comportamento de serviço Especifica o modo personalizado para validar os certificados x. 509 de cliente junto com o tipo de classe do validador.</span><span class="sxs-lookup"><span data-stu-id="815db-115">The service behavior specifies the Custom mode for validating client X.509 certificates along with the type of the validator class.</span></span> <span data-ttu-id="815db-116">O comportamento também especifica o certificado do servidor usando o elemento serviceCertificate.</span><span class="sxs-lookup"><span data-stu-id="815db-116">The behavior also specifies the server certificate using the serviceCertificate element.</span></span> <span data-ttu-id="815db-117">O certificado do servidor deve conter o mesmo valor para o `SubjectName` como o `findValue` no [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md).</span><span class="sxs-lookup"><span data-stu-id="815db-117">The server certificate has to contain the same value for the `SubjectName` as the `findValue` in the [\<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md).</span></span>  
  
```xml  
  <system.serviceModel>  
    <services>  
      <service name="Microsoft.ServiceModel.Samples.CalculatorService"  
               behaviorConfiguration="CalculatorServiceBehavior">  
        <!-- use host/baseAddresses to configure base address -->  
        <!-- provided by host -->  
        <host>  
          <baseAddresses>  
            <add baseAddress =  
                "http://localhost:8001/servicemodelsamples/service" />  
          </baseAddresses>  
        </host>  
        <!-- use base address specified above, provide one endpoint -->  
        <endpoint address="certificate"  
               binding="wsHttpBinding"  
               bindingConfiguration="Binding"   
               contract="Microsoft.ServiceModel.Samples.ICalculator" />  
      </service>  
    </services>  
    <bindings>  
      <wsHttpBinding>  
        <!-- X509 certificate binding -->  
        <binding name="Binding">  
          <security mode="Message">  
            <message clientCredentialType="Certificate" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="CalculatorServiceBehavior">  
          <serviceDebug includeExceptionDetailInFaults ="true"/>  
          <serviceCredentials>  
            <!--The serviceCredentials behavior allows one -->  
            <!-- to specify authentication constraints on -->  
            <!-- client certificates. -->  
            <clientCertificate>  
              <!-- Setting the certificateValidationMode to -->  
              <!-- Custom means that if the custom -->  
              <!-- X509CertificateValidator does NOT throw -->  
              <!-- an exception, then the provided certificate -- >  
              <!-- will be trusted without performing any -->  
              <!-- validation beyond that performed by the custom-->  
              <!-- validator. The security implications of this -->  
              <!-- setting should be carefully considered before -->  
              <!-- using Custom in production code. -->  
              <authentication   
                 certificateValidationMode="Custom"   
                 customCertificateValidatorType =  
"Microsoft.ServiceModel.Samples.CustomX509CertificateValidator, service" />  
            </clientCertificate>  
            <!-- The serviceCredentials behavior allows one to -- >  
            <!--define a service certificate. -->  
            <!--A service certificate is used by a client to  -->  
            <!--authenticate the service and provide message  -->  
            <!--protection. This configuration references the  -->  
            <!--"localhost" certificate installed during the setup  -->  
            <!--instructions. -->  
            <serviceCertificate findValue="localhost"   
                 storeLocation="LocalMachine"   
                 storeName="My" x509FindType="FindBySubjectName" />  
          </serviceCredentials>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
      </system.serviceModel>  
```  
  
 <span data-ttu-id="815db-118">A configuração do ponto de extremidade cliente consiste em um nome de configuração, um endereço absoluto para o ponto de extremidade de serviço, a associação e o contrato.</span><span class="sxs-lookup"><span data-stu-id="815db-118">The client endpoint configuration consists of a configuration name, an absolute address for the service endpoint, the binding, and the contract.</span></span> <span data-ttu-id="815db-119">A ligação do cliente é configurado com o modo apropriado e a mensagem `clientCredentialType`.</span><span class="sxs-lookup"><span data-stu-id="815db-119">The client binding is configured with the appropriate mode and message `clientCredentialType`.</span></span>  
  
```xml  
<system.serviceModel>  
    <client>  
      <!-- X509 certificate based endpoint -->  
      <endpoint name="Certificate"  
        address=  
        "http://localhost:8001/servicemodelsamples/service/certificate"   
                binding="wsHttpBinding"   
                bindingConfiguration="Binding"   
                behaviorConfiguration="ClientCertificateBehavior"  
                contract="Microsoft.ServiceModel.Samples.ICalculator">  
      </endpoint>  
    </client>  
    <bindings>  
        <wsHttpBinding>  
            <!-- X509 certificate binding -->  
            <binding name="Binding">  
                <security mode="Message">  
                    <message clientCredentialType="Certificate" />  
               </security>  
            </binding>  
       </wsHttpBinding>  
    </bindings>  
    <behaviors>  
      <endpointBehaviors>  
        <behavior name="ClientCertificateBehavior">  
          <clientCredentials>  
            <serviceCertificate>  
              <!-- Setting the certificateValidationMode to -->  
              <!-- PeerOrChainTrust means that if the certificate -->  
              <!-- is in the user's Trusted People store, then it -->  
              <!-- is trusted without performing a validation of -->  
              <!-- the certificate's issuer chain. -->  
              <!-- This setting is used here for convenience so -->  
              <!-- that the sample can be run without having to -->  
              <!-- have certificates issued by a certification -->  
              <!-- authority (CA). This setting is less secure -->  
              <!-- than the default, ChainTrust. The security -->  
              <!-- implications of this setting should be -->  
              <!-- carefully considered before using -->  
              <!-- PeerOrChainTrust in production code.-->  
              <authentication   
                  certificateValidationMode="PeerOrChainTrust" />  
            </serviceCertificate>  
          </clientCredentials>  
        </behavior>  
      </endpointBehaviors>  
    </behaviors>  
  </system.serviceModel>  
```  
  
 <span data-ttu-id="815db-120">A implementação de cliente define o certificado de cliente para usar.</span><span class="sxs-lookup"><span data-stu-id="815db-120">The client implementation sets the client certificate to use.</span></span>  
  
```  
// Create a client with Certificate endpoint configuration  
CalculatorClient client = new CalculatorClient("Certificate");  
try  
{  
    client.ClientCredentials.ClientCertificate.SetCertificate(StoreLocation.CurrentUser, StoreName.My, X509FindType.FindBySubjectName, "test1");  
  
    // Call the Add service operation.  
    double value1 = 100.00D;  
    double value2 = 15.99D;  
    double result = client.Add(value1, value2);  
    Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);  
  
    // Call the Subtract service operation.  
    value1 = 145.00D;  
    value2 = 76.54D;  
    result = client.Subtract(value1, value2);  
    Console.WriteLine("Subtract({0},{1}) = {2}", value1, value2, result);  
  
    // Call the Multiply service operation.  
    value1 = 9.00D;  
    value2 = 81.25D;  
    result = client.Multiply(value1, value2);  
    Console.WriteLine("Multiply({0},{1}) = {2}", value1, value2, result);  
  
    // Call the Divide service operation.  
    value1 = 22.00D;  
    value2 = 7.00D;  
    result = client.Divide(value1, value2);  
    Console.WriteLine("Divide({0},{1}) = {2}", value1, value2, result);  
    client.Close();  
}  
catch (TimeoutException e)  
{  
    Console.WriteLine("Call timed out : {0}", e.Message);  
    client.Abort();  
}  
catch (CommunicationException e)  
{  
    Console.WriteLine("Call failed : {0}", e.Message);  
    client.Abort();  
}  
catch (Exception e)  
{  
    Console.WriteLine("Call failed : {0}", e.Message);  
    client.Abort();  
}  
```  
  
 <span data-ttu-id="815db-121">Este exemplo usa um X509CertificateValidator personalizado para validar certificados.</span><span class="sxs-lookup"><span data-stu-id="815db-121">This sample uses a custom X509CertificateValidator to validate certificates.</span></span> <span data-ttu-id="815db-122">O exemplo implementa CustomX509CertificateValidator, derivada de <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span><span class="sxs-lookup"><span data-stu-id="815db-122">The sample implements CustomX509CertificateValidator, derived from <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span></span> <span data-ttu-id="815db-123">Consulte a documentação <xref:System.IdentityModel.Selectors.X509CertificateValidator> para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="815db-123">See documentation about <xref:System.IdentityModel.Selectors.X509CertificateValidator> for more information.</span></span> <span data-ttu-id="815db-124">Este exemplo de validador personalizado específico implementa o método Validate para aceitar qualquer certificado x. 509 que é emitido por conta própria como mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="815db-124">This particular custom validator sample implements the Validate method to accept any X.509 certificate that is self-issued as shown in the following code.</span></span>  
  
```  
public class CustomX509CertificateValidator : X509CertificateValidator  
{  
  public override void Validate ( X509Certificate2 certificate )  
  {  
   // Only accept self-issued certificates  
   if (certificate.Subject != certificate.Issuer)  
     throw new Exception("Certificate is not self-issued");  
   }  
}  
```  
  
 <span data-ttu-id="815db-125">Depois que o validador é implementado no código de serviço, o host de serviço deve ser informado sobre a instância de validação a ser usado.</span><span class="sxs-lookup"><span data-stu-id="815db-125">Once the validator is implemented in service code, the service host must be informed about the validator instance to use.</span></span> <span data-ttu-id="815db-126">Isso é feito usando o código a seguir.</span><span class="sxs-lookup"><span data-stu-id="815db-126">This is done using the following code.</span></span>  
  
```  
serviceHost.Credentials.ClientCertificate.Authentication.CertificateValidationMode = X509CertificateValidationMode.Custom;  
serviceHost.Credentials.ClientCertificate.Authentication.CustomCertificateValidator = new CustomX509CertificateValidator();  
```  
  
 <span data-ttu-id="815db-127">Ou você pode fazer a mesma coisa na configuração da seguinte maneira.</span><span class="sxs-lookup"><span data-stu-id="815db-127">Or you can do the same thing in configuration as follows.</span></span>  
  
```xml  
<behaviors>  
    <serviceBehaviors>  
     <behavior name="CalculatorServiceBehavior">  
       ...  
   <serviceCredentials>  
    <!--The serviceCredentials behavior allows one to specify -->   
    <!--authentication constraints on client certificates.-->  
    <clientCertificate>  
    <!-- Setting the certificateValidationMode to Custom means -->   
    <!--that if the custom X509CertificateValidator does NOT -->   
    <!--throw an exception, then the provided certificate will-- >   
    <!-- be trusted without performing any validation beyond that-- >  
    <!-- performed by the custom validator. The security -- >   
    <!--implications of this setting should be carefully -- >  
    <!--considered before using Custom in production code. -->  
    <authentication certificateValidationMode="Custom"  
       customCertificateValidatorType =  
"Microsoft.ServiceModel.Samples. CustomX509CertificateValidator, service" />  
   </clientCertificate>  
   ...  
  </behavior>  
 </serviceBehaviors>  
</behaviors>  
```  
  
 <span data-ttu-id="815db-128">Quando você executar o exemplo, as respostas e solicitações de operação são exibidas na janela do console do cliente.</span><span class="sxs-lookup"><span data-stu-id="815db-128">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="815db-129">O cliente deve chamar com êxito todos os métodos.</span><span class="sxs-lookup"><span data-stu-id="815db-129">The client should successfully call all the methods.</span></span> <span data-ttu-id="815db-130">Pressione ENTER na janela do cliente para desligar o cliente.</span><span class="sxs-lookup"><span data-stu-id="815db-130">Press ENTER in the client window to shut down the client.</span></span>  
  
## <a name="setup-batch-file"></a><span data-ttu-id="815db-131">Arquivo de lote</span><span class="sxs-lookup"><span data-stu-id="815db-131">Setup Batch File</span></span>  
 <span data-ttu-id="815db-132">Arquivo em lotes bat incluído com este exemplo permite que você configure o servidor com certificados relevantes para executar um aplicativo auto-hospedado que exige a segurança baseada em certificado do servidor.</span><span class="sxs-lookup"><span data-stu-id="815db-132">The Setup.bat batch file included with this sample allows you to configure the server with relevant certificates to run a self-hosted application that requires server certificate-based security.</span></span> <span data-ttu-id="815db-133">Esse arquivo em lotes deve ser modificado para funcionar entre computadores ou para trabalhar em um caso não hospedado.</span><span class="sxs-lookup"><span data-stu-id="815db-133">This batch file must be modified to work across computers or to work in a non-hosted case.</span></span>  
  
 <span data-ttu-id="815db-134">O exemplo a seguir fornece uma visão geral das seções diferentes dos arquivos de lote para que eles podem ser modificados para executar a configuração apropriada:</span><span class="sxs-lookup"><span data-stu-id="815db-134">The following provides a brief overview of the different sections of the batch files so that they can be modified to run in the appropriate configuration:</span></span>  
  
-   <span data-ttu-id="815db-135">Criando o certificado do servidor:</span><span class="sxs-lookup"><span data-stu-id="815db-135">Creating the server certificate:</span></span>  
  
     <span data-ttu-id="815db-136">As seguintes linhas do arquivo em lotes bat criam o certificado do servidor a ser usado.</span><span class="sxs-lookup"><span data-stu-id="815db-136">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span> <span data-ttu-id="815db-137">A variável % SERVER_NAME % Especifica o nome do servidor.</span><span class="sxs-lookup"><span data-stu-id="815db-137">The %SERVER_NAME% variable specifies the server name.</span></span> <span data-ttu-id="815db-138">Altere essa variável para especificar seu próprio nome de servidor.</span><span class="sxs-lookup"><span data-stu-id="815db-138">Change this variable to specify your own server name.</span></span> <span data-ttu-id="815db-139">O valor padrão é localhost.</span><span class="sxs-lookup"><span data-stu-id="815db-139">The default value is localhost.</span></span>  
  
    ```  
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
-   <span data-ttu-id="815db-140">Instalando o certificado do servidor no repositório de certificados confiáveis do cliente:</span><span class="sxs-lookup"><span data-stu-id="815db-140">Installing the server certificate into client's trusted certificate store:</span></span>  
  
     <span data-ttu-id="815db-141">Armazenam as linhas a seguir na cópia de arquivo de lote o certificado do servidor bat para as pessoas confiáveis do cliente.</span><span class="sxs-lookup"><span data-stu-id="815db-141">The following lines in the Setup.bat batch file copy the server certificate into the client trusted people store.</span></span> <span data-ttu-id="815db-142">Esta etapa é necessária porque os certificados gerados pela Makecert.exe não são implicitamente confiáveis pelo sistema do cliente.</span><span class="sxs-lookup"><span data-stu-id="815db-142">This step is required since certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="815db-143">Se você já tiver um certificado que está enraizado em um certificado de raiz confiável do cliente — por exemplo, um certificado da Microsoft emitido — essa etapa de preenchimento do repositório de certificados de cliente com o certificado do servidor não é necessária.</span><span class="sxs-lookup"><span data-stu-id="815db-143">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>  
  
    ```  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
-   <span data-ttu-id="815db-144">Criando o certificado de cliente:</span><span class="sxs-lookup"><span data-stu-id="815db-144">Creating the client certificate:</span></span>  
  
     <span data-ttu-id="815db-145">As seguintes linhas do arquivo em lotes bat criam o certificado de cliente a ser usado.</span><span class="sxs-lookup"><span data-stu-id="815db-145">The following lines from the Setup.bat batch file create the client certificate to be used.</span></span> <span data-ttu-id="815db-146">A variável % nome_do_usuário % Especifica o nome do cliente.</span><span class="sxs-lookup"><span data-stu-id="815db-146">The %USER_NAME% variable specifies the client name.</span></span> <span data-ttu-id="815db-147">Esse valor é definido como "test1" porque esse é o nome que o código do cliente procura.</span><span class="sxs-lookup"><span data-stu-id="815db-147">This value is set to "test1" because this is the name the client code looks for.</span></span> <span data-ttu-id="815db-148">Se você alterar o valor de % username %, você deve alterar o valor correspondente no arquivo de origem Client.cs e recriar o cliente.</span><span class="sxs-lookup"><span data-stu-id="815db-148">If you change the value of %USER_NAME% you must change the corresponding value in the Client.cs source file and rebuild the client.</span></span>  
  
     <span data-ttu-id="815db-149">O certificado é armazenado no repositório My (pessoal) no local de armazenamento CurrentUser.</span><span class="sxs-lookup"><span data-stu-id="815db-149">The certificate is stored in My (Personal) store under the CurrentUser store location.</span></span>  
  
    ```  
    echo ************  
    echo Client cert setup starting  
    echo %USER_NAME%  
    echo ************  
    echo making client cert  
    echo ************  
    makecert.exe -sr CurrentUser -ss MY -a sha1 -n CN=%USER_NAME% -sky exchange -pe  
    ```  
  
-   <span data-ttu-id="815db-150">Instalando o certificado de cliente no repositório de certificados confiáveis do servidor:</span><span class="sxs-lookup"><span data-stu-id="815db-150">Installing the client certificate into server's trusted certificate store:</span></span>  
  
     <span data-ttu-id="815db-151">As seguintes linhas no arquivo em lotes bat copie o certificado do cliente para o armazenamento de pessoas confiáveis.</span><span class="sxs-lookup"><span data-stu-id="815db-151">The following lines in the Setup.bat batch file copy the client certificate into the trusted people store.</span></span> <span data-ttu-id="815db-152">Esta etapa é necessária porque os certificados gerados pela Makecert.exe não são implicitamente confiáveis pelo sistema do servidor.</span><span class="sxs-lookup"><span data-stu-id="815db-152">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the server system.</span></span> <span data-ttu-id="815db-153">Se você já tiver um certificado que está enraizado em um certificado raiz confiável — por exemplo, um certificado da Microsoft emitido — essa etapa de preenchimento do repositório de certificados do servidor com o certificado de cliente não é necessária.</span><span class="sxs-lookup"><span data-stu-id="815db-153">If you already have a certificate that is rooted in a trusted root certificate—for example, a Microsoft issued certificate—this step of populating the server certificate store with the client certificate is not required.</span></span>  
  
    ```  
    certmgr.exe -add -r CurrentUser -s My -c -n %USER_NAME% -r LocalMachine -s TrustedPeople  
    ```  
  
#### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="815db-154">Para configurar e criar o exemplo</span><span class="sxs-lookup"><span data-stu-id="815db-154">To set up and build the sample</span></span>  
  
1.  <span data-ttu-id="815db-155">Para criar a solução, siga as instruções em [compilar os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="815db-155">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
2.  <span data-ttu-id="815db-156">Para executar o exemplo em um único - ou entre-computerconfiguration, use as instruções a seguir.</span><span class="sxs-lookup"><span data-stu-id="815db-156">To run the sample in a single- or cross-computerconfiguration, use the following instructions.</span></span>  
  
#### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="815db-157">Para executar o exemplo no mesmo computador</span><span class="sxs-lookup"><span data-stu-id="815db-157">To run the sample on the same computer</span></span>  
  
1.  <span data-ttu-id="815db-158">Execute bat da pasta de instalação de exemplo dentro de um [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] prompt de comando aberto com privilégios de administrador.</span><span class="sxs-lookup"><span data-stu-id="815db-158">Run Setup.bat from the sample install folder inside a [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] command prompt opened with administrator privileges.</span></span> <span data-ttu-id="815db-159">Isso instala todos os certificados necessários para executar o exemplo.</span><span class="sxs-lookup"><span data-stu-id="815db-159">This installs all the certificates required for running the sample.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="815db-160">O arquivo em lotes bat é projetado para ser executado de um [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] Prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="815db-160">The Setup.bat batch file is designed to be run from a [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] Command Prompt.</span></span> <span data-ttu-id="815db-161">Definir a variável de ambiente PATH dentro de [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] Prompt de comando aponta para o diretório que contém os executáveis exigido pelo script bat.</span><span class="sxs-lookup"><span data-stu-id="815db-161">The PATH environment variable set within the [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] Command Prompt points to the directory that contains executables required by the Setup.bat script.</span></span>  
  
2.  <span data-ttu-id="815db-162">Inicie Service.exe de service\bin.</span><span class="sxs-lookup"><span data-stu-id="815db-162">Launch Service.exe from service\bin.</span></span>  
  
3.  <span data-ttu-id="815db-163">Inicie Client.exe de \Client\Bin.</span><span class="sxs-lookup"><span data-stu-id="815db-163">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="815db-164">Atividade do cliente é exibida no aplicativo de console do cliente.</span><span class="sxs-lookup"><span data-stu-id="815db-164">Client activity is displayed on the client console application.</span></span>  
  
4.  <span data-ttu-id="815db-165">Se o cliente e o serviço não for capazes de se comunicar, consulte [dicas de solução de problemas](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span><span class="sxs-lookup"><span data-stu-id="815db-165">If the client and service are not able to communicate, see [Troubleshooting Tips](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
#### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="815db-166">Para executar o exemplo em computadores</span><span class="sxs-lookup"><span data-stu-id="815db-166">To run the sample across computers</span></span>  
  
1.  <span data-ttu-id="815db-167">Crie um diretório no computador de serviço.</span><span class="sxs-lookup"><span data-stu-id="815db-167">Create a directory on the service computer.</span></span>  
  
2.  <span data-ttu-id="815db-168">Copie os arquivos de programa do serviço de \service\bin para o diretório virtual no computador de serviço.</span><span class="sxs-lookup"><span data-stu-id="815db-168">Copy the service program files from \service\bin to the virtual directory on the service computer.</span></span> <span data-ttu-id="815db-169">Também copie os arquivos bat, Cleanup.bat, GetComputerName.vbs e ImportClientCert.bat para o computador do serviço.</span><span class="sxs-lookup"><span data-stu-id="815db-169">Also copy the Setup.bat, Cleanup.bat, GetComputerName.vbs and ImportClientCert.bat files to the service computer.</span></span>  
  
3.  <span data-ttu-id="815db-170">Crie um diretório em que o cliente computerfor os binários do cliente.</span><span class="sxs-lookup"><span data-stu-id="815db-170">Create a directory on the client computerfor the client binaries.</span></span>  
  
4.  <span data-ttu-id="815db-171">Copie os arquivos de programa do cliente para o diretório de cliente no computador cliente.</span><span class="sxs-lookup"><span data-stu-id="815db-171">Copy the client program files to the client directory on the client computer.</span></span> <span data-ttu-id="815db-172">Também copie os arquivos. bat, Cleanup.bat e ImportServiceCert.bat ao cliente.</span><span class="sxs-lookup"><span data-stu-id="815db-172">Also copy the Setup.bat, Cleanup.bat, and ImportServiceCert.bat files to the client.</span></span>  
  
5.  <span data-ttu-id="815db-173">No servidor, execute `setup.bat service` em um prompt de comando do Visual Studio aberto com privilégios de administrador.</span><span class="sxs-lookup"><span data-stu-id="815db-173">On the server, run `setup.bat service` in a Visual Studio command prompt opened with administrator privileges.</span></span> <span data-ttu-id="815db-174">Executando `setup.bat` com o `service` argumento cria um certificado de serviço com o nome de domínio totalmente qualificado do computerand exporta o certificado de serviço em um arquivo chamado Service.cer.</span><span class="sxs-lookup"><span data-stu-id="815db-174">Running `setup.bat` with the `service` argument creates a service certificate with the fully-qualified domain name of the computerand exports the service certificate to a file named Service.cer.</span></span>  
  
6.  <span data-ttu-id="815db-175">Editar Service.exe.config para refletir o novo nome de certificado (no `findValue` atributo o [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) que é o mesmo que o nome de domínio totalmente qualificado do computador.</span><span class="sxs-lookup"><span data-stu-id="815db-175">Edit Service.exe.config to reflect the new certificate name (in the `findValue` attribute in the [\<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) which is the same as the fully-qualified domain name of the computer.</span></span> <span data-ttu-id="815db-176">Também alterar o nome do computador no \<serviço > /\<baseAddresses > elemento de localhost como o nome totalmente qualificado do computador de serviço.</span><span class="sxs-lookup"><span data-stu-id="815db-176">Also change the computer name in the \<service>/\<baseAddresses> element from localhost to fully qualified name of your service computer.</span></span>  
  
7.  <span data-ttu-id="815db-177">Copie o arquivo de Service.cer do diretório de serviço para o diretório do cliente no computador cliente.</span><span class="sxs-lookup"><span data-stu-id="815db-177">Copy the Service.cer file from the service directory to the client directory on the client computer.</span></span>  
  
8.  <span data-ttu-id="815db-178">No cliente, execute `setup.bat client` em um prompt de comando do Visual Studio aberto com privilégios de administrador.</span><span class="sxs-lookup"><span data-stu-id="815db-178">On the client, run `setup.bat client` in a Visual Studio command prompt opened with administrator privileges.</span></span> <span data-ttu-id="815db-179">Executando `setup.bat` com o `client` argumento cria um certificado de cliente chamado client.com e exporta o certificado de cliente para um arquivo chamado cer.</span><span class="sxs-lookup"><span data-stu-id="815db-179">Running `setup.bat` with the `client` argument creates a client certificate named client.com and exports the client certificate to a file named Client.cer.</span></span>  
  
9. <span data-ttu-id="815db-180">No arquivo Client.exe.config no computador cliente, altere o valor do endereço do ponto de extremidade para coincidir com o novo endereço do seu serviço.</span><span class="sxs-lookup"><span data-stu-id="815db-180">In the Client.exe.config file on the client computer, change the address value of the endpoint to match the new address of your service.</span></span> <span data-ttu-id="815db-181">Faça isso substituindo localhost com o nome de domínio totalmente qualificado do servidor.</span><span class="sxs-lookup"><span data-stu-id="815db-181">Do this by replacing localhost with the fully-qualified domain name of the server.</span></span>  
  
10. <span data-ttu-id="815db-182">Copie o arquivo CER do diretório do cliente para o diretório de serviço no servidor.</span><span class="sxs-lookup"><span data-stu-id="815db-182">Copy the Client.cer file from the client directory to the service directory on the server.</span></span>  
  
11. <span data-ttu-id="815db-183">No cliente, execute ImportServiceCert.bat em um prompt de comando do Visual Studio aberto com privilégios de administrador.</span><span class="sxs-lookup"><span data-stu-id="815db-183">On the client, run ImportServiceCert.bat in a Visual Studio command prompt opened with administrator privileges.</span></span> <span data-ttu-id="815db-184">Isso importa o certificado de serviço do arquivo Service.cer para CurrentUser - TrustedPeople repositório.</span><span class="sxs-lookup"><span data-stu-id="815db-184">This imports the service certificate from the Service.cer file into the CurrentUser - TrustedPeople store.</span></span>  
  
12. <span data-ttu-id="815db-185">No servidor, execute ImportClientCert.bat em um prompt de comando do Visual Studio aberto com privilégios de administrador.</span><span class="sxs-lookup"><span data-stu-id="815db-185">On the server, run ImportClientCert.bat in a Visual Studio command prompt opened with administrator privileges.</span></span> <span data-ttu-id="815db-186">Isso importa o certificado de cliente do arquivo CER para o repositório de LocalMachine - TrustedPeople.</span><span class="sxs-lookup"><span data-stu-id="815db-186">This imports the client certificate from the Client.cer file into the LocalMachine - TrustedPeople store.</span></span>  
  
13. <span data-ttu-id="815db-187">No computador do servidor, inicie Service.exe da janela de prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="815db-187">On the server computer, launch Service.exe from the command prompt window.</span></span>  
  
14. <span data-ttu-id="815db-188">No computador cliente, inicie o Client.exe em uma janela de prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="815db-188">On the client computer, launch Client.exe from a command prompt window.</span></span> <span data-ttu-id="815db-189">Se o cliente e o serviço não for capazes de se comunicar, consulte [dicas de solução de problemas](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span><span class="sxs-lookup"><span data-stu-id="815db-189">If the client and service are not able to communicate, see [Troubleshooting Tips](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
#### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="815db-190">A limpeza após a amostra</span><span class="sxs-lookup"><span data-stu-id="815db-190">To clean up after the sample</span></span>  
  
1.  <span data-ttu-id="815db-191">Execute Cleanup.bat na pasta exemplos depois de terminar a execução do exemplo.</span><span class="sxs-lookup"><span data-stu-id="815db-191">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span> <span data-ttu-id="815db-192">Isso remove os certificados de servidor e cliente do repositório de certificados.</span><span class="sxs-lookup"><span data-stu-id="815db-192">This removes the server and client certificates from the certificate store.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="815db-193">Esse script não remove os certificados de serviço em um cliente ao executar este exemplo entre computadores.</span><span class="sxs-lookup"><span data-stu-id="815db-193">This script does not remove service certificates on a client when running this sample across computers.</span></span> <span data-ttu-id="815db-194">Se você executou os exemplos do Windows Communication Foundation (WCF) que usam certificados em computadores, certifique-se de limpar os certificados de serviço que foram instalados em CurrentUser - TrustedPeople repositório.</span><span class="sxs-lookup"><span data-stu-id="815db-194">If you have run Windows Communication Foundation (WCF) samples that use certificates across computers, be sure to clear the service certificates that have been installed in the CurrentUser - TrustedPeople store.</span></span> <span data-ttu-id="815db-195">Para fazer isso, use o seguinte comando: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` por exemplo: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span><span class="sxs-lookup"><span data-stu-id="815db-195">To do this, use the following command: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` For example: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="815db-196">Consulte também</span><span class="sxs-lookup"><span data-stu-id="815db-196">See Also</span></span>
