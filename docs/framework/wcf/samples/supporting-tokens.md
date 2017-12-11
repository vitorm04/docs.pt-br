---
title: Tokens com suporte
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 65a8905d-92cc-4ab0-b6ed-1f710e40784e
caps.latest.revision: "29"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ab728751a01d16c6b3d2d14de4dd09c2d2b0a17a
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="supporting-tokens"></a><span data-ttu-id="af784-102">Tokens com suporte</span><span class="sxs-lookup"><span data-stu-id="af784-102">Supporting Tokens</span></span>
<span data-ttu-id="af784-103">O suporte a Tokens demonstra como adicionar tokens adicionais para uma mensagem que usa o WS-Security.</span><span class="sxs-lookup"><span data-stu-id="af784-103">The Supporting Tokens sample demonstrates how to add additional tokens to a message that uses WS-Security.</span></span> <span data-ttu-id="af784-104">O exemplo adiciona um token de segurança binário x. 509 além de um token de segurança do nome de usuário.</span><span class="sxs-lookup"><span data-stu-id="af784-104">The example adds an X.509 binary security token in addition to a username security token.</span></span> <span data-ttu-id="af784-105">O token é passado em um cabeçalho de mensagem do WS-Security do cliente para o serviço e a parte da mensagem está assinado com a chave privada associada com o token de segurança x. 509 para provar a posse do certificado x. 509 para o receptor.</span><span class="sxs-lookup"><span data-stu-id="af784-105">The token is passed in a WS-Security message header from the client to the service and part of the message is signed with the private key associated with the X.509 security token to prove the possession of the X.509 certificate to the receiver.</span></span> <span data-ttu-id="af784-106">Isso é útil no caso, quando há uma necessidade de ter várias declarações associadas a uma mensagem para autenticar ou autorizar o remetente.</span><span class="sxs-lookup"><span data-stu-id="af784-106">This is useful in the case when there is a requirement to have multiple claims associated with a message to authenticate or authorize the sender.</span></span> <span data-ttu-id="af784-107">O serviço implementa um contrato que define um padrão de comunicação de solicitação-resposta.</span><span class="sxs-lookup"><span data-stu-id="af784-107">The service implements a contract that defines a request-reply communication pattern.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="af784-108">Demonstra</span><span class="sxs-lookup"><span data-stu-id="af784-108">Demonstrates</span></span>  
 <span data-ttu-id="af784-109">O exemplo demonstra:</span><span class="sxs-lookup"><span data-stu-id="af784-109">The sample demonstrates:</span></span>  
  
-   <span data-ttu-id="af784-110">Como um cliente pode passar tokens de segurança adicionais para um serviço.</span><span class="sxs-lookup"><span data-stu-id="af784-110">How a client can pass additional security tokens to a service.</span></span>  
  
-   <span data-ttu-id="af784-111">Como o servidor possa acessar as declarações associadas com os tokens de segurança adicional.</span><span class="sxs-lookup"><span data-stu-id="af784-111">How the server can access claims associated with additional security tokens.</span></span>  
  
-   <span data-ttu-id="af784-112">Como o certificado do servidor x. 509 é usado para proteger a chave simétrica usada para assinatura e criptografia de mensagem.</span><span class="sxs-lookup"><span data-stu-id="af784-112">How the server's X.509 certificate is used to protect the symmetric key used for message encryption and signature.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="af784-113">As instruções de procedimento e a compilação de configuração para este exemplo estão localizadas no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="af784-113">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
## <a name="client-authenticates-with-username-token-and-supporting-x509-security-token"></a><span data-ttu-id="af784-114">Cliente autentica com o Token de nome de usuário e o Token de segurança x. 509 de suporte</span><span class="sxs-lookup"><span data-stu-id="af784-114">Client Authenticates with Username Token and Supporting X.509 Security Token</span></span>  
 <span data-ttu-id="af784-115">O serviço expõe um ponto de extremidade de comunicação que é criado por meio de programação usando o `BindingHelper` e `EchoServiceHost` classes.</span><span class="sxs-lookup"><span data-stu-id="af784-115">The service exposes a single endpoint for communicating that is programmatically created using the `BindingHelper` and `EchoServiceHost` classes.</span></span> <span data-ttu-id="af784-116">O ponto de extremidade consiste em um endereço, uma ligação e um contrato.</span><span class="sxs-lookup"><span data-stu-id="af784-116">The endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="af784-117">A associação está configurada com uma associação personalizada usando `SymmetricSecurityBindingElement` e `HttpTransportBindingElement`.</span><span class="sxs-lookup"><span data-stu-id="af784-117">The binding is configured with a custom binding using `SymmetricSecurityBindingElement` and `HttpTransportBindingElement`.</span></span> <span data-ttu-id="af784-118">Este exemplo define o `SymmetricSecurityBindingElement` para usar um certificado x. 509 de serviço para proteger a chave simétrica durante a transmissão e passar uma `UserNameToken` juntamente com o suporte `X509SecurityToken` em um cabeçalho de mensagem do WS-Security.</span><span class="sxs-lookup"><span data-stu-id="af784-118">This sample sets the `SymmetricSecurityBindingElement` to use a service X.509 certificate to protect the symmetric key during transmission and to pass a `UserNameToken` along with the supporting `X509SecurityToken` in a WS-Security message header.</span></span> <span data-ttu-id="af784-119">A chave simétrica é usada para criptografar o corpo da mensagem e o token de segurança do nome de usuário.</span><span class="sxs-lookup"><span data-stu-id="af784-119">The symmetric key is used to encrypt the message body and the username security token.</span></span> <span data-ttu-id="af784-120">O token de suporte é passado como um token de segurança binário adicionais no cabeçalho da mensagem WS-Security.</span><span class="sxs-lookup"><span data-stu-id="af784-120">The supporting token is passed as an additional binary security token in the WS-Security message header.</span></span> <span data-ttu-id="af784-121">A autenticidade do token de suporte é comprovada inscrevendo-se parte da mensagem com a chave privada associada com a segurança x. 509 suporte token.</span><span class="sxs-lookup"><span data-stu-id="af784-121">The authenticity of the supporting token is proved by signing part of the message with the private key associated with the supporting X.509 security token.</span></span>  
  
```  
public static Binding CreateMultiFactorAuthenticationBinding()  
{  
    HttpTransportBindingElement httpTransport = new HttpTransportBindingElement();  
  
    // the message security binding element will be configured to require 2 tokens:  
    // 1) A username-password encrypted with the service token  
    // 2) A client certificate used to sign the message  
  
    // Instantiate a binding element that will require the username/password token in the message (encrypted with the server cert)  
    SymmetricSecurityBindingElement messageSecurity = SecurityBindingElement.CreateUserNameForCertificateBindingElement();  
  
    // Create supporting token parameters for the client X509 certificate.  
    X509SecurityTokenParameters clientX509SupportingTokenParameters = new X509SecurityTokenParameters();  
    // Specify that the supporting token is passed in message send by the client to the service  
    clientX509SupportingTokenParameters.InclusionMode = SecurityTokenInclusionMode.AlwaysToRecipient;  
    // Turn off derived keys  
    clientX509SupportingTokenParameters.RequireDerivedKeys = false;  
    // Augment the binding element to require the client's X509 certificate as an endorsing token in the message  
    messageSecurity.EndpointSupportingTokenParameters.Endorsing.Add(clientX509SupportingTokenParameters);  
  
    // Create a CustomBinding based on the constructed security binding element.  
    return new CustomBinding(messageSecurity, httpTransport);  
}  
```  
  
 <span data-ttu-id="af784-122">O comportamento Especifica as credenciais de serviço a ser usado para autenticação de cliente e também informações sobre o certificado x. 509 de serviço.</span><span class="sxs-lookup"><span data-stu-id="af784-122">The behavior specifies the service credentials that are to be used for client authentication and also information about the service X.509 certificate.</span></span> <span data-ttu-id="af784-123">O exemplo usa `CN=localhost` como um nome de assunto no certificado x. 509 de serviço.</span><span class="sxs-lookup"><span data-stu-id="af784-123">The sample uses `CN=localhost` as a subject name in the service X.509 certificate.</span></span>  
  
```  
override protected void InitializeRuntime()  
{  
    // Extract the ServiceCredentials behavior or create one.  
    ServiceCredentials serviceCredentials =   
        this.Description.Behaviors.Find<ServiceCredentials>();  
    if (serviceCredentials == null)  
    {  
        serviceCredentials = new ServiceCredentials();  
        this.Description.Behaviors.Add(serviceCredentials);  
    }  
  
    // Set the service certificate  
    serviceCredentials.ServiceCertificate.SetCertificate(  
                                       "CN=localhost");  
  
/*  
Setting the CertificateValidationMode to PeerOrChainTrust means that if the certificate is in the Trusted People store, then it will be trusted without performing a validation of the certificate's issuer chain. This setting is used here for convenience so that the sample can be run without having to have certificates issued by a certification authority (CA).  
This setting is less secure than the default, ChainTrust. The security implications of this setting should be carefully considered before using PeerOrChainTrust in production code.  
*/  
    serviceCredentials.ClientCertificate.Authentication.CertificateValidationMode = X509CertificateValidationMode.PeerOrChainTrust;  
  
    // Create the custom binding and add an endpoint to the service.  
    Binding multipleTokensBinding =  
         BindingHelper.CreateMultiFactorAuthenticationBinding();  
    this.AddServiceEndpoint(typeof(IEchoService),   
                          multipleTokensBinding, string.Empty);  
    base.InitializeRuntime();  
}  
```  
  
 <span data-ttu-id="af784-124">Código de serviço:</span><span class="sxs-lookup"><span data-stu-id="af784-124">Service code:</span></span>  
  
```  
[ServiceBehavior(IncludeExceptionDetailInFaults = true)]  
public class EchoService : IEchoService  
{  
    public string Echo()  
    {  
        string userName;  
        string certificateSubjectName;  
        GetCallerIdentities(  
            OperationContext.Current.ServiceSecurityContext,   
            out userName,   
            out certificateSubjectName);  
            return String.Format("Hello {0}, {1}",   
                    userName, certificateSubjectName);  
    }  
  
    public void Dispose()  
    {  
    }  
  
    bool TryGetClaimValue<TClaimResource>(ClaimSet claimSet,   
            string claimType, out TClaimResource resourceValue)  
            where TClaimResource : class  
    {  
        resourceValue = default(TClaimResource);  
        IEnumerable<Claim> matchingClaims =   
            claimSet.FindClaims(claimType, Rights.PossessProperty);  
        if(matchingClaims == null)  
            return false;  
        IEnumerator<Claim> enumerator = matchingClaims.GetEnumerator();  
        if (enumerator.MoveNext())  
        {  
            resourceValue =   
              (enumerator.Current.Resource == null) ? null :   
              (enumerator.Current.Resource as TClaimResource);  
            return true;  
        }  
        else  
        {  
            return false;  
        }  
    }  
  
    // Returns the username and certificate subject name provided by   
    //the client  
    void GetCallerIdentities(ServiceSecurityContext   
        callerSecurityContext,   
        out string userName, out string certificateSubjectName)  
    {  
        userName = null;  
        certificateSubjectName = null;  
  
       // Look in all the claimsets in the authorization context  
       foreach (ClaimSet claimSet in   
               callerSecurityContext.AuthorizationContext.ClaimSets)  
       {  
            if (claimSet is WindowsClaimSet)  
            {  
                // Try to find a Name claim. This will have been   
                // generated from the windows username.  
                string tmpName;  
                if (TryGetClaimValue<string>(claimSet, ClaimTypes.Name,   
                                                      out tmpName))  
                {  
                    userName = tmpName;  
                }  
            }  
            else if (claimSet is X509CertificateClaimSet)  
            {  
                // Try to find an X500DisinguishedName claim. This will   
                // have been generated from the client certificate.  
                X500DistinguishedName tmpDistinguishedName;  
                if (TryGetClaimValue<X500DistinguishedName>(claimSet,   
                               ClaimTypes.X500DistinguishedName,   
                               out tmpDistinguishedName))  
                {  
                    certificateSubjectName = tmpDistinguishedName.Name;  
                }  
            }  
        }  
    }  
}   
```  
  
 <span data-ttu-id="af784-125">O ponto de extremidade do cliente é configurado de maneira semelhante para o ponto de extremidade de serviço.</span><span class="sxs-lookup"><span data-stu-id="af784-125">The client endpoint is configured in a similar way to the service endpoint.</span></span> <span data-ttu-id="af784-126">O cliente usa o mesmo `BindingHelper` classe para criar uma associação.</span><span class="sxs-lookup"><span data-stu-id="af784-126">The client uses the same `BindingHelper` class to create a binding.</span></span> <span data-ttu-id="af784-127">O restante do programa de instalação está localizado em `Client` classe.</span><span class="sxs-lookup"><span data-stu-id="af784-127">The rest of the setup is located in `Client` class.</span></span> <span data-ttu-id="af784-128">O cliente define as informações sobre o token de segurança do nome de usuário, o token de segurança x. 509 suporte e informações sobre o certificado x. 509 de serviço no código do programa de instalação para a coleção de comportamentos de ponto de extremidade do cliente.</span><span class="sxs-lookup"><span data-stu-id="af784-128">The client sets information about the user name security token, the supporting X.509 security token and information about the service X.509 certificate in the setup code to the client endpoint behaviors collection.</span></span>  
  
```  
 static void Main()  
 {  
     // Create the custom binding and an endpoint address for   
     // the service.  
     Binding multipleTokensBinding =   
         BindingHelper.CreateMultiFactorAuthenticationBinding();  
         EndpointAddress serviceAddress = new EndpointAddress(  
         "http://localhost/servicemodelsamples/service.svc");  
       ChannelFactory<IEchoService> channelFactory = null;  
       IEchoService client = null;  
  
       Console.WriteLine("Username authentication required.");  
       Console.WriteLine(  
         "Provide a valid machine or domain account. [domain\\user]");  
       Console.WriteLine("   Enter username:");  
       string username = Console.ReadLine();  
       Console.WriteLine("   Enter password:");  
       string password = "";  
       ConsoleKeyInfo info = Console.ReadKey(true);  
       while (info.Key != ConsoleKey.Enter)  
       {  
           if (info.Key != ConsoleKey.Backspace)  
           {  
               if (info.KeyChar != '\0')  
               {  
                   password += info.KeyChar;  
                }  
                info = Console.ReadKey(true);  
            }  
            else if (info.Key == ConsoleKey.Backspace)  
            {  
                if (password != "")  
                {  
                    password =   
                       password.Substring(0, password.Length - 1);  
                }  
                info = Console.ReadKey(true);  
            }  
         }  
         for (int i = 0; i < password.Length; i++)  
            Console.Write("*");  
         Console.WriteLine();  
         try  
         {  
           // Create a proxy with the previously create binding and   
           // endpoint address  
              channelFactory =   
                 new ChannelFactory<IEchoService>(  
                     multipleTokensBinding, serviceAddress);  
           // configure the username credentials, the client   
           // certificate and the server certificate on the channel   
           // factory   
           channelFactory.Credentials.UserName.UserName = username;  
           channelFactory.Credentials.UserName.Password = password;  
           channelFactory.Credentials.ClientCertificate.SetCertificate(  
           "CN=client.com", StoreLocation.CurrentUser, StoreName.My);  
              channelFactory.Credentials.ServiceCertificate.SetDefaultCertificate(  
           "CN=localhost", StoreLocation.LocalMachine, StoreName.My);  
           client = channelFactory.CreateChannel();  
           Console.WriteLine("Echo service returned: {0}",   
                                           client.Echo());  
  
           ((IChannel)client).Close();  
           channelFactory.Close();  
        }  
        catch (CommunicationException e)  
        {  
         Abort((IChannel)client, channelFactory);  
         // if there is a fault then print it out  
         FaultException fe = null;  
         Exception tmp = e;  
         while (tmp != null)  
         {  
            fe = tmp as FaultException;  
            if (fe != null)  
            {  
                break;  
            }  
            tmp = tmp.InnerException;  
        }  
        if (fe != null)  
        {  
           Console.WriteLine("The server sent back a fault: {0}",   
         fe.CreateMessageFault().Reason.GetMatchingTranslation().Text);  
        }  
        else  
        {  
         Console.WriteLine("The request failed with exception: {0}",e);  
        }  
    }  
    catch (TimeoutException)  
    {  
        Abort((IChannel)client, channelFactory);  
        Console.WriteLine("The request timed out");  
    }  
    catch (Exception e)  
    {  
         Abort((IChannel)client, channelFactory);  
          Console.WriteLine(  
          "The request failed with unexpected exception: {0}", e);  
    }  
    Console.WriteLine();  
    Console.WriteLine("Press <ENTER> to terminate client.");  
    Console.ReadLine();  
}  
```  
  
## <a name="displaying-callers-information"></a><span data-ttu-id="af784-129">Exibindo informações dos chamadores</span><span class="sxs-lookup"><span data-stu-id="af784-129">Displaying Callers' Information</span></span>  
 <span data-ttu-id="af784-130">Para exibir informações do chamador, você pode usar o `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="af784-130">To display the caller's information, you can use the `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` as shown in the following code.</span></span> <span data-ttu-id="af784-131">O `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` contém declarações de autorização associadas ao chamador atual.</span><span class="sxs-lookup"><span data-stu-id="af784-131">The `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` contains authorization claims associated with the current caller.</span></span> <span data-ttu-id="af784-132">Essas declarações são fornecidas automaticamente pelo [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] para cada token recebido na mensagem.</span><span class="sxs-lookup"><span data-stu-id="af784-132">Those claims are supplied automatically by [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] for every token received in the message.</span></span>  
  
```  
bool TryGetClaimValue<TClaimResource>(ClaimSet claimSet, string   
                         claimType, out TClaimResource resourceValue)  
    where TClaimResource : class  
{  
    resourceValue = default(TClaimResource);  
    IEnumerable<Claim> matchingClaims =   
    claimSet.FindClaims(claimType, Rights.PossessProperty);  
    if (matchingClaims == null)  
          return false;  
    IEnumerator<Claim> enumerator = matchingClaims.GetEnumerator();  
    if (enumerator.MoveNext())  
    {  
        resourceValue = (enumerator.Current.Resource == null) ? null : (enumerator.Current.Resource as TClaimResource);  
        return true;  
    }  
    else  
    {  
         return false;  
    }  
}  
  
// Returns the username and certificate subject name provided by the client  
void GetCallerIdentities(ServiceSecurityContext callerSecurityContext, out string userName, out string certificateSubjectName)  
{  
    userName = null;  
    certificateSubjectName = null;  
  
    // Look in all the claimsets in the authorization context  
    foreach (ClaimSet claimSet in   
      callerSecurityContext.AuthorizationContext.ClaimSets)  
    {  
        if (claimSet is WindowsClaimSet)  
        {  
            // Try to find a Name claim. This will have been generated   
            //from the windows username.  
            string tmpName;  
            if (TryGetClaimValue<string>(claimSet, ClaimTypes.Name,   
                                                     out tmpName))  
            {  
                userName = tmpName;  
            }  
        }  
        else if (claimSet is X509CertificateClaimSet)  
         {  
            //Try to find an X500DisinguishedName claim.   
            //This will have been generated from the client   
            //certificate.  
            X500DistinguishedName tmpDistinguishedName;  
            if (TryGetClaimValue<X500DistinguishedName>(claimSet,   
               ClaimTypes.X500DistinguishedName,   
               out tmpDistinguishedName))  
            {  
                    certificateSubjectName = tmpDistinguishedName.Name;  
            }  
        }  
    }  
}  
```  
  
## <a name="running-the-sample"></a><span data-ttu-id="af784-133">Executando o exemplo</span><span class="sxs-lookup"><span data-stu-id="af784-133">Running the Sample</span></span>  
 <span data-ttu-id="af784-134">Quando você executar o exemplo, o cliente primeiro solicita que você forneça o nome de usuário e senha para o token de nome de usuário.</span><span class="sxs-lookup"><span data-stu-id="af784-134">When you run the sample, the client first prompts you to provide user name and password for the user name token.</span></span> <span data-ttu-id="af784-135">Certifique-se fornecer valores corretos para sua conta do sistema, como [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] no serviço mapeia os valores fornecidos no token de nome de usuário para a identidade fornecida pelo sistema.</span><span class="sxs-lookup"><span data-stu-id="af784-135">Be sure to provide correct values for your system account, because [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] on the service maps the values supplied in the user name token into the identity provided by the system.</span></span> <span data-ttu-id="af784-136">Depois disso, o cliente exibe a resposta do serviço.</span><span class="sxs-lookup"><span data-stu-id="af784-136">After that, the client displays the response from the service.</span></span> <span data-ttu-id="af784-137">Pressione ENTER na janela do cliente para desligar o cliente.</span><span class="sxs-lookup"><span data-stu-id="af784-137">Press ENTER in the client window to shut down the client.</span></span>  
  
## <a name="setup-batch-file"></a><span data-ttu-id="af784-138">Arquivo de lote</span><span class="sxs-lookup"><span data-stu-id="af784-138">Setup Batch File</span></span>  
 <span data-ttu-id="af784-139">Arquivo em lotes bat incluído com este exemplo permite que você configure o servidor com certificados relevantes para executar o aplicativo de serviços de informações da Internet (IIS) hospedado que exige a segurança baseada em certificado do servidor.</span><span class="sxs-lookup"><span data-stu-id="af784-139">The Setup.bat batch file included with this sample allows you to configure the server with relevant certificates to run Internet Information Services (IIS) hosted application that requires server certificate-based security.</span></span> <span data-ttu-id="af784-140">Esse arquivo em lotes deve ser modificado para funcionar entre máquinas ou trabalhar em um caso não hospedado.</span><span class="sxs-lookup"><span data-stu-id="af784-140">This batch file must be modified to work across machines or to work in a non-hosted case.</span></span>  
  
 <span data-ttu-id="af784-141">O exemplo a seguir fornece uma visão geral das seções diferentes dos arquivos de lote para que eles podem ser modificados para executar a configuração apropriada.</span><span class="sxs-lookup"><span data-stu-id="af784-141">The following provides a brief overview of the different sections of the batch files so that they can be modified to run in appropriate configuration.</span></span>  
  
### <a name="creating-the-client-certificate"></a><span data-ttu-id="af784-142">Criando o certificado de cliente</span><span class="sxs-lookup"><span data-stu-id="af784-142">Creating the Client Certificate</span></span>  
 <span data-ttu-id="af784-143">As seguintes linhas do arquivo em lotes bat criam o certificado de cliente a ser usado.</span><span class="sxs-lookup"><span data-stu-id="af784-143">The following lines from the Setup.bat batch file create the client certificate to be used.</span></span> <span data-ttu-id="af784-144">O `%CLIENT_NAME%` variável Especifica o assunto do certificado do cliente.</span><span class="sxs-lookup"><span data-stu-id="af784-144">The `%CLIENT_NAME%` variable specifies the subject of the client certificate.</span></span> <span data-ttu-id="af784-145">Este exemplo usa "client.com" como o nome da entidade.</span><span class="sxs-lookup"><span data-stu-id="af784-145">This sample uses "client.com" as the subject name.</span></span>  
  
 <span data-ttu-id="af784-146">O certificado é armazenado no repositório My (pessoal) sob o `CurrentUser` local do repositório.</span><span class="sxs-lookup"><span data-stu-id="af784-146">The certificate is stored in My (Personal) store under the `CurrentUser` store location.</span></span>  
  
```  
echo ************  
echo making client cert  
echo ************  
makecert.exe -sr CurrentUser -ss MY -a sha1 -n CN=%CLIENT_NAME% -sky exchange -pe  
```  
  
### <a name="installing-the-client-certificate-into-the-servers-trusted-store"></a><span data-ttu-id="af784-147">Instalando o certificado de cliente para o armazenamento do servidor confiável</span><span class="sxs-lookup"><span data-stu-id="af784-147">Installing the Client Certificate into the Server's Trusted Store</span></span>  
 <span data-ttu-id="af784-148">A seguinte linha no arquivo em lotes bat copia o certificado de cliente no armazenamento de pessoas confiáveis do servidor.</span><span class="sxs-lookup"><span data-stu-id="af784-148">The following line in the Setup.bat batch file copies the client certificate into the server’s trusted people store.</span></span> <span data-ttu-id="af784-149">Esta etapa é necessária porque certificados gerados pela Makecert.exe não são implicitamente confiáveis do sistema.</span><span class="sxs-lookup"><span data-stu-id="af784-149">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the server’s system.</span></span> <span data-ttu-id="af784-150">Se você já tiver um certificado que está enraizado em um certificado de raiz confiável do cliente — por exemplo, um certificado da Microsoft emitido — essa etapa de preenchimento do repositório de certificados de cliente com o certificado do servidor não é necessária.</span><span class="sxs-lookup"><span data-stu-id="af784-150">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>  
  
```  
echo ************  
echo copying client cert to server's CurrentUserstore  
echo ************  
certmgr.exe -add -r CurrentUser -s My -c -n %CLIENT_NAME% -r LocalMachine -s TrustedPeople  
```  
  
### <a name="creating-the-server-certificate"></a><span data-ttu-id="af784-151">Criando o certificado do servidor</span><span class="sxs-lookup"><span data-stu-id="af784-151">Creating the Server Certificate</span></span>  
 <span data-ttu-id="af784-152">As seguintes linhas do arquivo em lotes bat criam o certificado do servidor a ser usado.</span><span class="sxs-lookup"><span data-stu-id="af784-152">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span> <span data-ttu-id="af784-153">O `%SERVER_NAME%` variável Especifica o nome do servidor.</span><span class="sxs-lookup"><span data-stu-id="af784-153">The `%SERVER_NAME%` variable specifies the server name.</span></span> <span data-ttu-id="af784-154">Altere essa variável para especificar seu próprio nome de servidor.</span><span class="sxs-lookup"><span data-stu-id="af784-154">Change this variable to specify your own server name.</span></span> <span data-ttu-id="af784-155">O padrão, esse arquivo em lotes é localhost.</span><span class="sxs-lookup"><span data-stu-id="af784-155">The default in this batch file is localhost.</span></span>  
  
 <span data-ttu-id="af784-156">O certificado é armazenado no repositório My (pessoal) em um local de repositório LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="af784-156">The certificate is stored in My (Personal) store under the LocalMachine store location.</span></span> <span data-ttu-id="af784-157">O certificado é armazenado no repositório de LocalMachine para os serviços hospedados no IIS.</span><span class="sxs-lookup"><span data-stu-id="af784-157">The certificate is stored in the LocalMachine store for the IIS-hosted services.</span></span> <span data-ttu-id="af784-158">Para serviços de hospedagem interna, você deve modificar o arquivo em lotes para armazenar o certificado do servidor no local de armazenamento CurrentUser, substituindo a cadeia de caracteres LocalMachine por CurrentUser.</span><span class="sxs-lookup"><span data-stu-id="af784-158">For self-hosted services, you should modify the batch file to store the server certificate in the CurrentUser store location by replacing the string LocalMachine with CurrentUser.</span></span>  
  
```  
echo ************  
echo Server cert setup starting  
echo %SERVER_NAME%  
echo ************  
echo making server cert  
echo ************  
makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
```  
  
### <a name="installing-server-certificate-into-clients-trusted-certificate-store"></a><span data-ttu-id="af784-159">Instalar o certificado do servidor no repositório de certificados confiáveis do cliente</span><span class="sxs-lookup"><span data-stu-id="af784-159">Installing Server Certificate into Client's Trusted Certificate Store</span></span>  
 <span data-ttu-id="af784-160">Armazenam as linhas a seguir na cópia de arquivo de lote o certificado do servidor bat para as pessoas confiáveis do cliente.</span><span class="sxs-lookup"><span data-stu-id="af784-160">The following lines in the Setup.bat batch file copy the server certificate into the client trusted people store.</span></span> <span data-ttu-id="af784-161">Esta etapa é necessária porque os certificados gerados pela Makecert.exe não são implicitamente confiáveis pelo sistema do cliente.</span><span class="sxs-lookup"><span data-stu-id="af784-161">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="af784-162">Se você já tiver um certificado que está enraizado em um certificado de raiz confiável do cliente — por exemplo, um certificado da Microsoft emitido — essa etapa de preenchimento do repositório de certificados de cliente com o certificado do servidor não é necessária.</span><span class="sxs-lookup"><span data-stu-id="af784-162">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>  
  
```  
echo ************  
echo copying server cert to client's TrustedPeople store  
echo ************certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
```  
  
### <a name="enabling-access-to-the-certificates-private-key"></a><span data-ttu-id="af784-163">Habilitando o acesso à chave privada de certificado</span><span class="sxs-lookup"><span data-stu-id="af784-163">Enabling Access to the Certificate's Private Key</span></span>  
 <span data-ttu-id="af784-164">Para habilitar o acesso à chave privada de certificado do serviço hospedado no IIS, a conta de usuário sob a qual o processo de hospedados no IIS é executado deve ter permissões apropriadas para a chave privada.</span><span class="sxs-lookup"><span data-stu-id="af784-164">To enable access to the certificate private key from the IIS-hosted service, the user account under which the IIS-hosted process is running must be granted appropriate permissions for the private key.</span></span> <span data-ttu-id="af784-165">Isso é feito por último etapas no script bat.</span><span class="sxs-lookup"><span data-stu-id="af784-165">This is accomplished by last steps in the Setup.bat script.</span></span>  
  
```  
echo ************  
echo setting privileges on server certificates  
echo ************  
for /F "delims=" %%i in ('"%ProgramFiles%\ServiceModelSampleTools\FindPrivateKey.exe" My LocalMachine -n CN^=%SERVER_NAME% -a') do set PRIVATE_KEY_FILE=%%i  
set WP_ACCOUNT=NT AUTHORITY\NETWORK SERVICE  
(ver | findstr /C:"5.1") && set WP_ACCOUNT=%COMPUTERNAME%\ASPNET  
echo Y|cacls.exe "%PRIVATE_KEY_FILE%" /E /G "%WP_ACCOUNT%":R  
iisreset  
```  
  
##### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="af784-166">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="af784-166">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="af784-167">Certifique-se de que você executou o [único procedimento de instalação para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="af784-167">Be sure you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="af784-168">Para criar a solução, siga as instruções em [compilar os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="af784-168">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="af784-169">Para executar o exemplo em uma configuração ou entre computadores, use as instruções a seguir.</span><span class="sxs-lookup"><span data-stu-id="af784-169">To run the sample in a single- or cross-machine configuration, use the following instructions.</span></span>  
  
##### <a name="to-run-the-sample-on-the-same-machine"></a><span data-ttu-id="af784-170">Para executar o exemplo no mesmo computador</span><span class="sxs-lookup"><span data-stu-id="af784-170">To run the sample on the same machine</span></span>  
  
1.  <span data-ttu-id="af784-171">Execute bat da pasta de instalação de exemplo dentro de um [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] prompt de comando executado com privilégios de administrador.</span><span class="sxs-lookup"><span data-stu-id="af784-171">Run Setup.bat from the sample install folder inside a [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] command prompt run with administrator privileges.</span></span> <span data-ttu-id="af784-172">Isso instala todos os certificados necessários para executar o exemplo.</span><span class="sxs-lookup"><span data-stu-id="af784-172">This installs all the certificates required for running the sample.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="af784-173">O arquivo em lotes bat é projetado para ser executado de um [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] Prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="af784-173">The Setup.bat batch file is designed to be run from a [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] Command Prompt.</span></span> <span data-ttu-id="af784-174">Definir a variável de ambiente PATH dentro de [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] Prompt de comando aponta para o diretório que contém os executáveis exigido pelo script bat.</span><span class="sxs-lookup"><span data-stu-id="af784-174">The PATH environment variable set within the [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] Command Prompt points to the directory that contains executables required by the Setup.bat script.</span></span> <span data-ttu-id="af784-175">Certifique-se de remover os certificados executando Cleanup.bat quando terminar com o exemplo.</span><span class="sxs-lookup"><span data-stu-id="af784-175">Be sure to remove the certificates by running Cleanup.bat when finished with the sample.</span></span> <span data-ttu-id="af784-176">Outros exemplos de segurança usam os mesmos certificados.</span><span class="sxs-lookup"><span data-stu-id="af784-176">Other security samples use the same certificates.</span></span>  
  
2.  <span data-ttu-id="af784-177">Inicie Client.exe de \Client\Bin.</span><span class="sxs-lookup"><span data-stu-id="af784-177">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="af784-178">Atividade do cliente é exibida no aplicativo de console do cliente.</span><span class="sxs-lookup"><span data-stu-id="af784-178">Client activity is displayed on the client console application.</span></span>  
  
3.  <span data-ttu-id="af784-179">Se o cliente e o serviço não for capazes de se comunicar, consulte [dicas de solução de problemas](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).</span><span class="sxs-lookup"><span data-stu-id="af784-179">If the client and service are not able to communicate, see [Troubleshooting Tips](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
##### <a name="to-run-the-sample-across-machines"></a><span data-ttu-id="af784-180">Para executar o exemplo em computadores</span><span class="sxs-lookup"><span data-stu-id="af784-180">To run the sample across machines</span></span>  
  
1.  <span data-ttu-id="af784-181">Crie um diretório no computador do serviço.</span><span class="sxs-lookup"><span data-stu-id="af784-181">Create a directory on the service machine.</span></span> <span data-ttu-id="af784-182">Crie um aplicativo virtual denominado servicemodelsamples para este diretório usando a ferramenta de gerenciamento de serviços de informações da Internet (IIS).</span><span class="sxs-lookup"><span data-stu-id="af784-182">Create a virtual application named servicemodelsamples for this directory using the Internet Information Services (IIS) management tool.</span></span>  
  
2.  <span data-ttu-id="af784-183">Copie os arquivos de programa do serviço de \inetpub\wwwroot\servicemodelsamples para o diretório virtual na máquina do serviço.</span><span class="sxs-lookup"><span data-stu-id="af784-183">Copy the service program files from \inetpub\wwwroot\servicemodelsamples to the virtual directory on the service machine.</span></span> <span data-ttu-id="af784-184">Certifique-se de que você copiar os arquivos no subdiretório \bin.</span><span class="sxs-lookup"><span data-stu-id="af784-184">Ensure that you copy the files in the \bin subdirectory.</span></span> <span data-ttu-id="af784-185">Também copie os arquivos. bat, Cleanup.bat e ImportClientCert.bat para a máquina de serviço.</span><span class="sxs-lookup"><span data-stu-id="af784-185">Also copy the Setup.bat, Cleanup.bat, and ImportClientCert.bat files to the service machine.</span></span>  
  
3.  <span data-ttu-id="af784-186">Crie um diretório no computador cliente para os binários do cliente.</span><span class="sxs-lookup"><span data-stu-id="af784-186">Create a directory on the client machine for the client binaries.</span></span>  
  
4.  <span data-ttu-id="af784-187">Copie os arquivos de programa do cliente para o diretório de cliente no computador cliente.</span><span class="sxs-lookup"><span data-stu-id="af784-187">Copy the client program files to the client directory on the client machine.</span></span> <span data-ttu-id="af784-188">Também copie os arquivos. bat, Cleanup.bat e ImportServiceCert.bat ao cliente.</span><span class="sxs-lookup"><span data-stu-id="af784-188">Also copy the Setup.bat, Cleanup.bat, and ImportServiceCert.bat files to the client.</span></span>  
  
5.  <span data-ttu-id="af784-189">No servidor, execute `setup.bat service` em um prompt de comando do Visual Studio aberto com privilégios de administrador.</span><span class="sxs-lookup"><span data-stu-id="af784-189">On the server, run `setup.bat service` in a Visual Studio command prompt opened with administrator privileges.</span></span> <span data-ttu-id="af784-190">Executando `setup.bat` com o `service` argumento cria um certificado de serviço com o nome de domínio totalmente qualificado do computador e exporta o certificado de serviço para um arquivo chamado Service.cer.</span><span class="sxs-lookup"><span data-stu-id="af784-190">Running `setup.bat` with the `service` argument creates a service certificate with the fully-qualified domain name of the machine and exports the service certificate to a file named Service.cer.</span></span>  
  
6.  <span data-ttu-id="af784-191">Editar o Web. config para refletir o novo nome de certificado (no `findValue` atributo o [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) que é o mesmo que o nome de domínio totalmente qualificado da máquina.</span><span class="sxs-lookup"><span data-stu-id="af784-191">Edit Web.config to reflect the new certificate name (in the `findValue` attribute in the [\<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) which is the same as the fully-qualified domain name of the machine.</span></span>  
  
7.  <span data-ttu-id="af784-192">Copie o arquivo de Service.cer do diretório de serviço para o diretório do cliente no computador cliente.</span><span class="sxs-lookup"><span data-stu-id="af784-192">Copy the Service.cer file from the service directory to the client directory on the client machine.</span></span>  
  
8.  <span data-ttu-id="af784-193">No cliente, execute `setup.bat client` em um prompt de comando do Visual Studio aberto com privilégios de administrador.</span><span class="sxs-lookup"><span data-stu-id="af784-193">On the client, run `setup.bat client` in a Visual Studio command prompt opened with administrator privileges.</span></span> <span data-ttu-id="af784-194">Executando `setup.bat` com o `client` argumento cria um certificado de cliente chamado client.com e exporta o certificado de cliente para um arquivo chamado cer.</span><span class="sxs-lookup"><span data-stu-id="af784-194">Running `setup.bat` with the `client` argument creates a client certificate named client.com and exports the client certificate to a file named Client.cer.</span></span>  
  
9. <span data-ttu-id="af784-195">No arquivo Client.exe.config no computador cliente, altere o valor do endereço do ponto de extremidade para coincidir com o novo endereço do seu serviço.</span><span class="sxs-lookup"><span data-stu-id="af784-195">In the Client.exe.config file on the client machine, change the address value of the endpoint to match the new address of your service.</span></span> <span data-ttu-id="af784-196">Faça isso substituindo localhost com o nome de domínio totalmente qualificado do servidor.</span><span class="sxs-lookup"><span data-stu-id="af784-196">Do this by replacing localhost with the fully-qualified domain name of the server.</span></span>  
  
10. <span data-ttu-id="af784-197">Copie o arquivo CER do diretório do cliente para o diretório de serviço no servidor.</span><span class="sxs-lookup"><span data-stu-id="af784-197">Copy the Client.cer file from the client directory to the service directory on the server.</span></span>  
  
11. <span data-ttu-id="af784-198">No cliente, execute ImportServiceCert.bat.</span><span class="sxs-lookup"><span data-stu-id="af784-198">On the client, run ImportServiceCert.bat.</span></span> <span data-ttu-id="af784-199">Isso importa o certificado de serviço do arquivo Service.cer para CurrentUser - TrustedPeople repositório.</span><span class="sxs-lookup"><span data-stu-id="af784-199">This imports the service certificate from the Service.cer file into the CurrentUser - TrustedPeople store.</span></span>  
  
12. <span data-ttu-id="af784-200">No servidor, execute ImportClientCert.bat, isso importa o certificado de cliente do arquivo CER para o repositório de LocalMachine - TrustedPeople.</span><span class="sxs-lookup"><span data-stu-id="af784-200">On the server, run ImportClientCert.bat, This imports the client certificate from the Client.cer file into the LocalMachine - TrustedPeople store.</span></span>  
  
13. <span data-ttu-id="af784-201">No computador cliente, inicie Client.exe em uma janela de prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="af784-201">On the client machine, launch Client.exe from a command prompt window.</span></span> <span data-ttu-id="af784-202">Se o cliente e o serviço não for capazes de se comunicar, consulte [dicas de solução de problemas](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).</span><span class="sxs-lookup"><span data-stu-id="af784-202">If the client and service are not able to communicate, see [Troubleshooting Tips](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
##### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="af784-203">A limpeza após a amostra</span><span class="sxs-lookup"><span data-stu-id="af784-203">To clean up after the sample</span></span>  
  
-   <span data-ttu-id="af784-204">Execute Cleanup.bat na pasta exemplos depois de terminar a execução do exemplo.</span><span class="sxs-lookup"><span data-stu-id="af784-204">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="af784-205">Esse script não remove os certificados de serviço em um cliente ao executar este exemplo entre máquinas.</span><span class="sxs-lookup"><span data-stu-id="af784-205">This script does not remove service certificates on a client when running this sample across machines.</span></span> <span data-ttu-id="af784-206">Se você tiver executado [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] exemplos que usam certificados em computadores, certifique-se de desmarcar os certificados de serviço que foram instalados em CurrentUser - TrustedPeople repositório.</span><span class="sxs-lookup"><span data-stu-id="af784-206">If you have run [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] samples that use certificates across machines, be sure to clear the service certificates that have been installed in the CurrentUser - TrustedPeople store.</span></span> <span data-ttu-id="af784-207">Para fazer isso, use o seguinte comando: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` por exemplo: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span><span class="sxs-lookup"><span data-stu-id="af784-207">To do this, use the following command: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` For example: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af784-208">Consulte também</span><span class="sxs-lookup"><span data-stu-id="af784-208">See Also</span></span>
