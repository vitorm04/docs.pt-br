---
title: Token personalizado
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e7fd8b38-c370-454f-ba3e-19759019f03d
caps.latest.revision: "28"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 19593e61cc640068ac7c90a6abbd6ea0d6a3ff08
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="custom-token"></a><span data-ttu-id="eea21-102">Token personalizado</span><span class="sxs-lookup"><span data-stu-id="eea21-102">Custom Token</span></span>
<span data-ttu-id="eea21-103">Este exemplo demonstra como adicionar uma implementação personalizada de token em um [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] aplicativo.</span><span class="sxs-lookup"><span data-stu-id="eea21-103">This sample demonstrates how to add a custom token implementation into a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] application.</span></span> <span data-ttu-id="eea21-104">O exemplo usa um `CreditCardToken` para passar com segurança informações sobre cartões de crédito de cliente para o serviço.</span><span class="sxs-lookup"><span data-stu-id="eea21-104">The example uses a `CreditCardToken` to securely pass information about client credit cards to the service.</span></span> <span data-ttu-id="eea21-105">O token é passado no cabeçalho da mensagem WS-Security e é assinado e criptografado usando o elemento de associação de segurança simétrica junto com o corpo da mensagem e outros cabeçalhos de mensagem.</span><span class="sxs-lookup"><span data-stu-id="eea21-105">The token is passed in the WS-Security message header and is signed and encrypted using the symmetric security binding element along with message body and other message headers.</span></span> <span data-ttu-id="eea21-106">Isso é útil em casos em que os tokens internos não são suficientes.</span><span class="sxs-lookup"><span data-stu-id="eea21-106">This is useful in cases where the built-in tokens are not sufficient.</span></span> <span data-ttu-id="eea21-107">Este exemplo demonstra como fornecer um token de segurança personalizada para um serviço em vez de usar um dos tokens internos.</span><span class="sxs-lookup"><span data-stu-id="eea21-107">This sample demonstrates how to provide a custom security token to a service instead of using one of the built-in tokens.</span></span> <span data-ttu-id="eea21-108">O serviço implementa um contrato que define um padrão de comunicação de solicitação-resposta.</span><span class="sxs-lookup"><span data-stu-id="eea21-108">The service implements a contract that defines a request-reply communication pattern.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="eea21-109">As instruções de procedimento e a compilação de configuração para este exemplo estão localizadas no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="eea21-109">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="eea21-110">Para resumir, este exemplo demonstra o seguinte:</span><span class="sxs-lookup"><span data-stu-id="eea21-110">To summarize, this sample demonstrates the following:</span></span>  
  
-   <span data-ttu-id="eea21-111">Como um cliente pode passar um token de segurança personalizada para um serviço.</span><span class="sxs-lookup"><span data-stu-id="eea21-111">How a client can pass a custom security token to a service.</span></span>  
  
-   <span data-ttu-id="eea21-112">Como o serviço pode consumir e validar um token de segurança personalizada.</span><span class="sxs-lookup"><span data-stu-id="eea21-112">How the service can consume and validate a custom security token.</span></span>  
  
-   <span data-ttu-id="eea21-113">Como o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] código de serviço pode obter as informações sobre tokens de segurança recebido, incluindo o token de segurança personalizada.</span><span class="sxs-lookup"><span data-stu-id="eea21-113">How the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service code can obtain the information about received security tokens including the custom security token.</span></span>  
  
-   <span data-ttu-id="eea21-114">Como o certificado do servidor x. 509 é usado para proteger a chave simétrica usada para assinatura e criptografia de mensagem.</span><span class="sxs-lookup"><span data-stu-id="eea21-114">How the server's X.509 certificate is used to protect the symmetric key used for message encryption and signature.</span></span>  
  
## <a name="client-authentication-using-a-custom-security-token"></a><span data-ttu-id="eea21-115">Autenticação de cliente usando um Token de segurança personalizado</span><span class="sxs-lookup"><span data-stu-id="eea21-115">Client Authentication Using a Custom Security Token</span></span>  
 <span data-ttu-id="eea21-116">O serviço expõe um ponto de extremidade é criado por meio de programação usando `BindingHelper` e `EchoServiceHost` classes.</span><span class="sxs-lookup"><span data-stu-id="eea21-116">The service exposes a single endpoint that is programmatically created using `BindingHelper` and `EchoServiceHost` classes.</span></span> <span data-ttu-id="eea21-117">O ponto de extremidade consiste em um endereço, uma ligação e um contrato.</span><span class="sxs-lookup"><span data-stu-id="eea21-117">The endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="eea21-118">A associação está configurada com uma associação personalizada usando `SymmetricSecurityBindingElement` e `HttpTransportBindingElement`.</span><span class="sxs-lookup"><span data-stu-id="eea21-118">The binding is configured with a custom binding using `SymmetricSecurityBindingElement` and `HttpTransportBindingElement`.</span></span> <span data-ttu-id="eea21-119">Este exemplo define o `SymmetricSecurityBindingElement` para usar o certificado x. 509 de um serviço para proteger a chave simétrica durante a transmissão e passar um personalizado `CreditCardToken` em um cabeçalho de mensagem do WS-Security como um token de segurança assinado e criptografado.</span><span class="sxs-lookup"><span data-stu-id="eea21-119">This sample sets the `SymmetricSecurityBindingElement` to use a service's X.509 certificate to protect the symmetric key during transmission and to pass a custom `CreditCardToken` in a WS-Security message header as a signed and encrypted security token.</span></span> <span data-ttu-id="eea21-120">O comportamento Especifica as credenciais de serviço a ser usado para autenticação de cliente e também informações sobre o certificado x. 509 de serviço.</span><span class="sxs-lookup"><span data-stu-id="eea21-120">The behavior specifies the service credentials that are to be used for client authentication and also information about the service X.509 certificate.</span></span>  
  
```  
public static class BindingHelper  
{  
    public static Binding CreateCreditCardBinding()  
    {  
        HttpTransportBindingElement httpTransport = new HttpTransportBindingElement();  
  
        // The message security binding element will be configured to require a credit card.  
        // The token that is encrypted with the service's certificate.   
        SymmetricSecurityBindingElement messageSecurity = new SymmetricSecurityBindingElement();  
        messageSecurity.EndpointSupportingTokenParameters.SignedEncrypted.Add(new CreditCardTokenParameters());  
        X509SecurityTokenParameters x509ProtectionParameters = new X509SecurityTokenParameters();  
        x509ProtectionParameters.InclusionMode = SecurityTokenInclusionMode.Never;  
        messageSecurity.ProtectionTokenParameters = x509ProtectionParameters;  
        return new CustomBinding(messageSecurity, httpTransport);  
    }  
}  
```  
  
 <span data-ttu-id="eea21-121">Para consumir um cartão de crédito token na mensagem, o exemplo usa as credenciais de serviço personalizado para fornecer essa funcionalidade.</span><span class="sxs-lookup"><span data-stu-id="eea21-121">To consume a credit card token in the message, the sample uses custom service credentials to provide this functionality.</span></span> <span data-ttu-id="eea21-122">A classe de credenciais de serviço está localizada no `CreditCardServiceCredentials` classe e é adicionado para as coleções de comportamentos do host do serviço no `EchoServiceHost.InitializeRuntime` método.</span><span class="sxs-lookup"><span data-stu-id="eea21-122">The service credentials class is located in the `CreditCardServiceCredentials` class and is added to the behaviors collections of the service host in the `EchoServiceHost.InitializeRuntime` method.</span></span>  
  
```  
class EchoServiceHost : ServiceHost  
{  
    string creditCardFile;  
  
    public EchoServiceHost(parameters Uri[] addresses)  
        : base(typeof(EchoService), addresses)  
    {  
        creditCardFile = ConfigurationManager.AppSettings["creditCardFile"];  
        if (string.IsNullOrEmpty(creditCardFile))  
        {  
            throw new ConfigurationErrorsException("creditCardFile not specified in service config");  
        }  
  
        creditCardFile = String.Format("{0}\\{1}", System.Web.Hosting.HostingEnvironment.ApplicationPhysicalPath, creditCardFile);  
  
    }  
  
    override protected void InitializeRuntime()  
    {  
        // Create a credit card service credentials and add it to the behaviors.  
        CreditCardServiceCredentials serviceCredentials = new CreditCardServiceCredentials(this.creditCardFile);  
        serviceCredentials.ServiceCertificate.SetCertificate("CN=localhost", StoreLocation.LocalMachine, StoreName.My);  
        this.Description.Behaviors.Remove((typeof(ServiceCredentials)));  
        this.Description.Behaviors.Add(serviceCredentials);  
  
        // Register a credit card binding for the endpoint.  
        Binding creditCardBinding = BindingHelper.CreateCreditCardBinding();  
        this.AddServiceEndpoint(typeof(IEchoService), creditCardBinding, string.Empty);  
  
        base.InitializeRuntime();  
    }  
}  
```  
  
 <span data-ttu-id="eea21-123">O ponto de extremidade do cliente é configurado de maneira semelhante, como o ponto de extremidade de serviço.</span><span class="sxs-lookup"><span data-stu-id="eea21-123">The client endpoint is configured in a similar manner as the service endpoint.</span></span> <span data-ttu-id="eea21-124">O cliente usa o mesmo `BindingHelper` classe para criar uma associação.</span><span class="sxs-lookup"><span data-stu-id="eea21-124">The client uses the same `BindingHelper` class to create a binding.</span></span> <span data-ttu-id="eea21-125">O restante do programa de instalação está localizado no `Client` classe.</span><span class="sxs-lookup"><span data-stu-id="eea21-125">The rest of the setup is located in the `Client` class.</span></span> <span data-ttu-id="eea21-126">O cliente também define informações para ser contida no `CreditCardToken` e informações sobre o certificado x. 509 de serviço no código do programa de instalação adicionando um `CreditCardClientCredentials` instância com os dados apropriados para a coleção de comportamentos de ponto de extremidade do cliente.</span><span class="sxs-lookup"><span data-stu-id="eea21-126">The client also sets information to be contained in the `CreditCardToken` and information about the service X.509 certificate in the setup code by adding a `CreditCardClientCredentials` instance with the proper data to the client endpoint behaviors collection.</span></span> <span data-ttu-id="eea21-127">O exemplo usa o certificado x. 509 com o nome da entidade definida como `CN=localhost` como o certificado de serviço.</span><span class="sxs-lookup"><span data-stu-id="eea21-127">The sample uses X.509 certificate with subject name set to `CN=localhost` as the service certificate.</span></span>  
  
```  
Binding creditCardBinding = BindingHelper.CreateCreditCardBinding();  
EndpointAddress serviceAddress = new EndpointAddress("http://localhost/servicemodelsamples/service.svc");  
  
// Create a client with given client endpoint configuration  
channelFactory =   
new ChannelFactory<IEchoService>(creditCardBinding, serviceAddress);  
  
// configure the credit card credentials on the channel factory   
CreditCardClientCredentials credentials =   
      new CreditCardClientCredentials(  
      new CreditCardInfo(creditCardNumber, issuer, expirationTime));  
// configure the service certificate on the credentials  
credentials.ServiceCertificate.SetDefaultCertificate(  
      "CN=localhost", StoreLocation.LocalMachine, StoreName.My);  
  
// replace ClientCredentials with CreditCardClientCredentials  
channelFactory.Endpoint.Behaviors.Remove(typeof(ClientCredentials));  
channelFactory.Endpoint.Behaviors.Add(credentials);  
  
client = channelFactory.CreateChannel();  
  
Console.WriteLine("Echo service returned: {0}", client.Echo());  
  
((IChannel)client).Close();  
channelFactory.Close();  
```  
  
## <a name="custom-security-token-implementation"></a><span data-ttu-id="eea21-128">Implementação de Token de segurança personalizada</span><span class="sxs-lookup"><span data-stu-id="eea21-128">Custom Security Token Implementation</span></span>  
 <span data-ttu-id="eea21-129">Para habilitar um token de segurança personalizada no [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], criar uma representação de objeto do token de segurança personalizada.</span><span class="sxs-lookup"><span data-stu-id="eea21-129">To enable a custom security token in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], create an object representation of the custom security token.</span></span> <span data-ttu-id="eea21-130">O exemplo tem essa representação no `CreditCardToken` classe.</span><span class="sxs-lookup"><span data-stu-id="eea21-130">The sample has this representation in the `CreditCardToken` class.</span></span> <span data-ttu-id="eea21-131">A representação de objeto é responsável por manter todas as informações de token de segurança relevantes e para fornecer uma lista de chaves de segurança contidas no token de segurança.</span><span class="sxs-lookup"><span data-stu-id="eea21-131">The object representation is responsible for holding all relevant security token information and to provide a list of security keys contained in the security token.</span></span> <span data-ttu-id="eea21-132">Nesse caso, o token de segurança do cartão de crédito não contém nenhuma chave de segurança.</span><span class="sxs-lookup"><span data-stu-id="eea21-132">In this case, the credit card security token does not contain any security key.</span></span>  
  
 <span data-ttu-id="eea21-133">A próxima seção descreve o que deve ser feito para permitir que um token personalizado para serem transmitidos eletronicamente e consumido por um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="eea21-133">The next section describes what must be done to enable a custom token to be transmitted over the wire and consumed by a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] endpoint.</span></span>  
  
```  
class CreditCardToken : SecurityToken  
{  
    CreditCardInfo cardInfo;  
    DateTime effectiveTime = DateTime.UtcNow;  
    string id;  
    ReadOnlyCollection<SecurityKey> securityKeys;  
  
    public CreditCardToken(CreditCardInfo cardInfo) : this(cardInfo, Guid.NewGuid().ToString()) { }  
  
    public CreditCardToken(CreditCardInfo cardInfo, string id)  
    {  
        if (cardInfo == null)  
            throw new ArgumentNullException("cardInfo");  
  
        if (id == null)  
            throw new ArgumentNullException("id");  
  
        this.cardInfo = cardInfo;  
        this.id = id;  
  
        // The credit card token is not capable of any cryptography.  
        this.securityKeys = new ReadOnlyCollection<SecurityKey>(new List<SecurityKey>());  
    }  
  
    public CreditCardInfo CardInfo { get { return this.cardInfo; } }  
  
    public override ReadOnlyCollection<SecurityKey> SecurityKeys { get { return this.securityKeys; } }  
  
    public override DateTime ValidFrom { get { return this.effectiveTime; } }  
    public override DateTime ValidTo { get { return this.cardInfo.ExpirationDate; } }  
    public override string Id { get { return this.id; } }  
}  
```  
  
## <a name="getting-the-custom-credit-card-token-to-and-from-the-message"></a><span data-ttu-id="eea21-134">Obtendo o cartão de crédito Token de e para a mensagem</span><span class="sxs-lookup"><span data-stu-id="eea21-134">Getting the Custom Credit Card Token to and from the Message</span></span>  
 <span data-ttu-id="eea21-135">Serializadores de token de segurança em [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] são responsáveis por criar uma representação de objeto dos tokens de segurança do XML da mensagem e criar um formulário XML dos tokens de segurança.</span><span class="sxs-lookup"><span data-stu-id="eea21-135">Security token serializers in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] are responsible for creating an object representation of security tokens from the XML in the message and creating a XML form of the security tokens.</span></span> <span data-ttu-id="eea21-136">Eles também são responsáveis por outros recursos, como leitura e gravação de identificadores de chave apontando para tokens de segurança, mas este exemplo usa somente segurança token funcionalidades relacionadas.</span><span class="sxs-lookup"><span data-stu-id="eea21-136">They are also responsible for other functionality such as reading and writing key identifiers pointing to security tokens, but this example uses only security token-related functionality.</span></span> <span data-ttu-id="eea21-137">Para habilitar um personalizado token você deve implementar seu próprio serializador de token de segurança.</span><span class="sxs-lookup"><span data-stu-id="eea21-137">To enable a custom token you must implement your own security token serializer.</span></span> <span data-ttu-id="eea21-138">Este exemplo usa o `CreditCardSecurityTokenSerializer` classe para essa finalidade.</span><span class="sxs-lookup"><span data-stu-id="eea21-138">This sample uses the `CreditCardSecurityTokenSerializer` class for this purpose.</span></span>  
  
 <span data-ttu-id="eea21-139">Sobre o serviço, o serializador personalizado lê o formulário XML do token personalizado e cria a representação de objeto de token personalizado dele.</span><span class="sxs-lookup"><span data-stu-id="eea21-139">On the service, the custom serializer reads the XML form of the custom token and creates the custom token object representation from it.</span></span>  
  
 <span data-ttu-id="eea21-140">No cliente, o `CreditCardSecurityTokenSerializer` classe grava as informações contidas na representação de objeto de token de segurança para o gravador de XML.</span><span class="sxs-lookup"><span data-stu-id="eea21-140">On the client, the `CreditCardSecurityTokenSerializer` class writes the information contained in the security token object representation into the XML writer.</span></span>  
  
```  
public class CreditCardSecurityTokenSerializer : WSSecurityTokenSerializer  
{  
    public CreditCardSecurityTokenSerializer(SecurityTokenVersion version) : base() { }  
  
    protected override bool CanReadTokenCore(XmlReader reader)  
    {  
        XmlDictionaryReader localReader = XmlDictionaryReader.CreateDictionaryReader(reader);  
  
        if (reader == null) throw new ArgumentNullException("reader");  
  
        if (reader.IsStartElement(Constants.CreditCardTokenName, Constants.CreditCardTokenNamespace))  
            return true;  
  
        return base.CanReadTokenCore(reader);  
    }  
  
    protected override SecurityToken ReadTokenCore(XmlReader reader, SecurityTokenResolver tokenResolver)  
    {  
        if (reader == null) throw new ArgumentNullException("reader");  
  
        if (reader.IsStartElement(Constants.CreditCardTokenName, Constants.CreditCardTokenNamespace))  
        {  
            string id = reader.GetAttribute(Constants.Id, Constants.WsUtilityNamespace);  
  
            reader.ReadStartElement();  
  
            // Read the credit card number.  
            string creditCardNumber = reader.ReadElementString(Constants.CreditCardNumberElementName, Constants.CreditCardTokenNamespace);  
  
            // Read the expiration date.  
            string expirationTimeString = reader.ReadElementString(Constants.CreditCardExpirationElementName, Constants.CreditCardTokenNamespace);  
            DateTime expirationTime = XmlConvert.ToDateTime(expirationTimeString, XmlDateTimeSerializationMode.Utc);  
  
            // Read the issuer of the credit card.  
            string creditCardIssuer = reader.ReadElementString(Constants.CreditCardIssuerElementName, Constants.CreditCardTokenNamespace);  
            reader.ReadEndElement();  
  
            CreditCardInfo cardInfo = new CreditCardInfo(creditCardNumber, creditCardIssuer, expirationTime);  
  
            return new CreditCardToken(cardInfo, id);  
        }  
        else  
        {  
            return WSSecurityTokenSerializer.DefaultInstance.ReadToken(reader, tokenResolver);  
        }  
    }  
  
    protected override bool CanWriteTokenCore(SecurityToken token)  
    {  
        if (token is CreditCardToken)  
            return true;  
  
        else  
            return base.CanWriteTokenCore(token);  
    }  
  
    protected override void WriteTokenCore(XmlWriter writer, SecurityToken token)  
    {  
        if (writer == null) { throw new ArgumentNullException("writer"); }  
        if (token == null) { throw new ArgumentNullException("token"); }  
  
        CreditCardToken c = token as CreditCardToken;  
        if (c != null)  
        {  
            writer.WriteStartElement(Constants.CreditCardTokenPrefix, Constants.CreditCardTokenName, Constants.CreditCardTokenNamespace);  
            writer.WriteAttributeString(Constants.WsUtilityPrefix, Constants.Id, Constants.WsUtilityNamespace, token.Id);  
            writer.WriteElementString(Constants.CreditCardNumberElementName, Constants.CreditCardTokenNamespace, c.CardInfo.CardNumber);  
            writer.WriteElementString(Constants.CreditCardExpirationElementName, Constants.CreditCardTokenNamespace, XmlConvert.ToString(c.CardInfo.ExpirationDate, XmlDateTimeSerializationMode.Utc));  
            writer.WriteElementString(Constants.CreditCardIssuerElementName, Constants.CreditCardTokenNamespace, c.CardInfo.CardIssuer);  
            writer.WriteEndElement();  
            writer.Flush();  
        }  
        else  
        {  
            base.WriteTokenCore(writer, token);  
        }  
    }  
}  
```  
  
## <a name="how-token-provider-and-token-authenticator-classes-are-created"></a><span data-ttu-id="eea21-141">Como o provedor de Token e Classes do autenticador de Token são criados</span><span class="sxs-lookup"><span data-stu-id="eea21-141">How Token Provider and Token Authenticator Classes are Created</span></span>  
 <span data-ttu-id="eea21-142">As credenciais de cliente e de serviço serão responsáveis por fornecer a instância do Gerenciador de token de segurança.</span><span class="sxs-lookup"><span data-stu-id="eea21-142">Client and service credentials are responsible for providing the security token manager instance.</span></span> <span data-ttu-id="eea21-143">A instância do Gerenciador de token de segurança é usada para obter os provedores de token, autenticadores de token e serializadores de token.</span><span class="sxs-lookup"><span data-stu-id="eea21-143">The security token manager instance is used to get token providers, token authenticators and token serializers.</span></span>  
  
 <span data-ttu-id="eea21-144">O provedor de token cria uma representação de objeto do token com base nas informações contidas nas credenciais do cliente ou serviço.</span><span class="sxs-lookup"><span data-stu-id="eea21-144">The token provider creates an object representation of the token based on the information contained in the client or service credentials.</span></span> <span data-ttu-id="eea21-145">A representação de objeto de token é gravada para a mensagem usando o serializador de token (discutido na seção anterior).</span><span class="sxs-lookup"><span data-stu-id="eea21-145">The token object representation is then written to the message using the token serializer (discussed in the previous section).</span></span>  
  
 <span data-ttu-id="eea21-146">O autenticador de token valida os tokens que chegam na mensagem.</span><span class="sxs-lookup"><span data-stu-id="eea21-146">The token authenticator validates tokens that arrive in the message.</span></span> <span data-ttu-id="eea21-147">A entrada representação de objeto de token é criada pelo serializador de token.</span><span class="sxs-lookup"><span data-stu-id="eea21-147">The incoming token object representation is created by the token serializer.</span></span> <span data-ttu-id="eea21-148">Essa representação de objeto é então passada para o autenticador de token para validação.</span><span class="sxs-lookup"><span data-stu-id="eea21-148">This object representation is then passed to the token authenticator for validation.</span></span> <span data-ttu-id="eea21-149">Depois que o token é validado com êxito, o autenticador de token retorna uma coleção de `IAuthorizationPolicy` objetos que representam as informações contidas no token.</span><span class="sxs-lookup"><span data-stu-id="eea21-149">After the token is successfully validated, the token authenticator returns a collection of `IAuthorizationPolicy` objects that represent the information contained in the token.</span></span> <span data-ttu-id="eea21-150">Essas informações são usadas durante o processamento da mensagem para decisões de autorização de executar e fornecer declarações para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="eea21-150">This information is used later during the message processing to perform authorization decisions and to provide claims for the application.</span></span> <span data-ttu-id="eea21-151">Neste exemplo, o autenticador de token de cartão de crédito usa `CreditCardTokenAuthorizationPolicy` para essa finalidade.</span><span class="sxs-lookup"><span data-stu-id="eea21-151">In this example, the credit card token authenticator uses `CreditCardTokenAuthorizationPolicy` for this purpose.</span></span>  
  
 <span data-ttu-id="eea21-152">O serializador de token é responsável por obter a representação de objeto do token para e da transmissão.</span><span class="sxs-lookup"><span data-stu-id="eea21-152">The token serializer is responsible for getting the object representation of the token to and from the wire.</span></span> <span data-ttu-id="eea21-153">Isso é discutido na seção anterior.</span><span class="sxs-lookup"><span data-stu-id="eea21-153">This is discussed in the previous section.</span></span>  
  
 <span data-ttu-id="eea21-154">Neste exemplo, usamos um provedor de token somente no cliente e um autenticador de token apenas no serviço, porque você deseja transmitir um token de cartão de crédito somente na direção serviço do cliente.</span><span class="sxs-lookup"><span data-stu-id="eea21-154">In this sample, we use a token provider only on the client and a token authenticator only on the service, because we want to transmit a credit card token only in the client-to-service direction.</span></span>  
  
 <span data-ttu-id="eea21-155">A funcionalidade no cliente está localizada no `CreditCardClientCrendentials`, `CreditCardClientCredentialsSecurityTokenManager` e `CreditCardTokenProvider` classes.</span><span class="sxs-lookup"><span data-stu-id="eea21-155">The functionality on the client is located in the `CreditCardClientCrendentials`, `CreditCardClientCredentialsSecurityTokenManager` and `CreditCardTokenProvider` classes.</span></span>  
  
 <span data-ttu-id="eea21-156">Sobre o serviço, a funcionalidade reside no `CreditCardServiceCredentials`, `CreditCardServiceCredentialsSecurityTokenManager`, `CreditCardTokenAuthenticator` e `CreditCardTokenAuthorizationPolicy` classes.</span><span class="sxs-lookup"><span data-stu-id="eea21-156">On the service, the functionality resides in the `CreditCardServiceCredentials`, `CreditCardServiceCredentialsSecurityTokenManager`, `CreditCardTokenAuthenticator` and `CreditCardTokenAuthorizationPolicy` classes.</span></span>  
  
```  
    public class CreditCardClientCredentials : ClientCredentials  
    {  
        CreditCardInfo creditCardInfo;  
  
        public CreditCardClientCredentials(CreditCardInfo creditCardInfo)  
            : base()  
        {  
            if (creditCardInfo == null)  
                throw new ArgumentNullException("creditCardInfo");  
  
            this.creditCardInfo = creditCardInfo;  
        }  
  
        public CreditCardInfo CreditCardInfo  
        {  
            get { return this.creditCardInfo; }  
        }  
  
        protected override ClientCredentials CloneCore()  
        {  
            return new CreditCardClientCredentials(this.creditCardInfo);  
        }  
  
        public override SecurityTokenManager CreateSecurityTokenManager()  
        {  
            return new CreditCardClientCredentialsSecurityTokenManager(this);  
        }  
    }  
  
public class CreditCardClientCredentialsSecurityTokenManager : ClientCredentialsSecurityTokenManager  
    {  
        CreditCardClientCredentials creditCardClientCredentials;  
  
        public CreditCardClientCredentialsSecurityTokenManager(CreditCardClientCredentials creditCardClientCredentials)  
            : base (creditCardClientCredentials)  
        {  
            this.creditCardClientCredentials = creditCardClientCredentials;  
        }  
  
        public override SecurityTokenProvider CreateSecurityTokenProvider(SecurityTokenRequirement tokenRequirement)  
        {  
            // handle this token for Custom  
            if (tokenRequirement.TokenType == Constants.CreditCardTokenType)  
                return new CreditCardTokenProvider(this.creditCardClientCredentials.CreditCardInfo);  
            // return server cert  
            else if (tokenRequirement is InitiatorServiceModelSecurityTokenRequirement)  
            {  
                if (tokenRequirement.TokenType == SecurityTokenTypes.X509Certificate)  
                {  
                    return new X509SecurityTokenProvider(creditCardClientCredentials.ServiceCertificate.DefaultCertificate);  
                }  
            }  
  
            return base.CreateSecurityTokenProvider(tokenRequirement);  
        }  
  
        public override SecurityTokenSerializer CreateSecurityTokenSerializer(SecurityTokenVersion version)  
        {  
  
            return new CreditCardSecurityTokenSerializer(version);  
        }  
  
    }  
  
    class CreditCardTokenProvider : SecurityTokenProvider  
    {  
        CreditCardInfo creditCardInfo;  
  
        public CreditCardTokenProvider(CreditCardInfo creditCardInfo) : base()  
        {  
            if (creditCardInfo == null)  
            {  
                throw new ArgumentNullException("creditCardInfo");  
            }  
            this.creditCardInfo = creditCardInfo;  
        }  
  
        protected override SecurityToken GetTokenCore(TimeSpan timeout)  
        {  
            SecurityToken result = new CreditCardToken(this.creditCardInfo);  
            return result;  
        }  
    }  
  
public class CreditCardServiceCredentials : ServiceCredentials  
    {  
        string creditCardFile;  
  
        public CreditCardServiceCredentials(string creditCardFile)  
            : base()  
        {   
            if (creditCardFile == null)  
                throw new ArgumentNullException("creditCardFile");  
  
            this.creditCardFile = creditCardFile;  
        }  
  
        public string CreditCardDataFile  
        {  
            get { return this.creditCardFile; }  
        }  
  
        protected override ServiceCredentials CloneCore()  
        {  
            return new CreditCardServiceCredentials(this.creditCardFile);  
        }  
  
        public override SecurityTokenManager CreateSecurityTokenManager()  
        {  
            return new CreditCardServiceCredentialsSecurityTokenManager(this);  
        }  
    }  
  
public class CreditCardServiceCredentialsSecurityTokenManager : ServiceCredentialsSecurityTokenManager  
{  
        CreditCardServiceCredentials creditCardServiceCredentials;  
  
        public CreditCardServiceCredentialsSecurityTokenManager(CreditCardServiceCredentials creditCardServiceCredentials)  
            : base(creditCardServiceCredentials)  
        {  
            this.creditCardServiceCredentials = creditCardServiceCredentials;  
        }  
  
        public override SecurityTokenAuthenticator CreateSecurityTokenAuthenticator(SecurityTokenRequirement tokenRequirement, out SecurityTokenResolver outOfBandTokenResolver)  
        {  
            if (tokenRequirement.TokenType == Constants.CreditCardTokenType)  
            {  
                outOfBandTokenResolver = null;  
                return new CreditCardTokenAuthenticator(creditCardServiceCredentials.CreditCardDataFile);  
            }  
  
            return base.CreateSecurityTokenAuthenticator(tokenRequirement, out outOfBandTokenResolver);  
        }  
  
        public override SecurityTokenSerializer CreateSecurityTokenSerializer(SecurityTokenVersion version)  
        {  
            return new CreditCardSecurityTokenSerializer(version);  
        }  
    }  
  
    class CreditCardTokenAuthenticator : SecurityTokenAuthenticator  
    {  
        string creditCardsFile;  
        public CreditCardTokenAuthenticator(string creditCardsFile)  
        {  
            this.creditCardsFile = creditCardsFile;  
        }  
  
        protected override bool CanValidateTokenCore(SecurityToken token)  
        {  
            return (token is CreditCardToken);  
        }  
  
        protected override ReadOnlyCollection<IAuthorizationPolicy> ValidateTokenCore(SecurityToken token)  
        {  
            CreditCardToken creditCardToken = token as CreditCardToken;  
  
            if (creditCardToken.CardInfo.ExpirationDate < DateTime.UtcNow)  
                throw new SecurityTokenValidationException("The credit card has expired");  
            if (!IsCardNumberAndExpirationValid(creditCardToken.CardInfo))  
                throw new SecurityTokenValidationException("Unknown or invalid credit card");  
  
            // the credit card token has only 1 claim - the card number. The issuer for the claim is the  
            // credit card issuer  
  
            DefaultClaimSet cardIssuerClaimSet = new DefaultClaimSet(new Claim(ClaimTypes.Name, creditCardToken.CardInfo.CardIssuer, Rights.PossessProperty));  
            DefaultClaimSet cardClaimSet = new DefaultClaimSet(cardIssuerClaimSet, new Claim(Constants.CreditCardNumberClaim, creditCardToken.CardInfo.CardNumber, Rights.PossessProperty));  
            List<IAuthorizationPolicy> policies = new List<IAuthorizationPolicy>(1);  
            policies.Add(new CreditCardTokenAuthorizationPolicy(cardClaimSet));  
            return policies.AsReadOnly();  
        }  
  
        /// <summary>  
        /// Helper method to check if a given credit card entry is present in the User DB  
        /// </summary>  
        private bool IsCardNumberAndExpirationValid(CreditCardInfo cardInfo)  
        {  
            try  
            {  
                using (StreamReader myStreamReader = new StreamReader(this.creditCardsFile))  
                {  
                    string line = "";  
                    while ((line = myStreamReader.ReadLine()) != null)  
                    {  
                        string[] splitEntry = line.Split('#');  
                        if (splitEntry[0] == cardInfo.CardNumber)  
                        {  
                            string expirationDateString = splitEntry[1].Trim();  
                            DateTime expirationDateOnFile = DateTime.Parse(expirationDateString, System.Globalization.DateTimeFormatInfo.InvariantInfo, System.Globalization.DateTimeStyles.AdjustToUniversal);  
                            if (cardInfo.ExpirationDate == expirationDateOnFile)  
                            {  
                                string issuer = splitEntry[2];  
                                return issuer.Equals(cardInfo.CardIssuer, StringComparison.InvariantCultureIgnoreCase);  
                            }  
                            else  
                            {  
                                return false;  
                            }  
                        }  
                    }  
                    return false;  
                }  
            }  
            catch (Exception e)  
            {  
                throw new Exception("BookStoreService: Error while retrieving credit card information from User DB " + e.ToString());  
            }  
        }  
    }  
  
    public class CreditCardTokenAuthorizationPolicy : IAuthorizationPolicy  
    {  
        string id;  
        ClaimSet issuer;  
        IEnumerable<ClaimSet> issuedClaimSets;  
  
        public CreditCardTokenAuthorizationPolicy(ClaimSet issuedClaims)  
        {  
            if (issuedClaims == null)  
                throw new ArgumentNullException("issuedClaims");  
            this.issuer = issuedClaims.Issuer;  
            this.issuedClaimSets = new ClaimSet[] { issuedClaims };  
            this.id = Guid.NewGuid().ToString();  
        }  
  
        public ClaimSet Issuer { get { return this.issuer; } }  
  
        public string Id { get { return this.id; } }  
  
        public bool Evaluate(EvaluationContext context, ref object state)  
        {  
            foreach (ClaimSet issuance in this.issuedClaimSets)  
            {  
                context.AddClaimSet(this, issuance);  
            }  
  
            return true;  
        }  
    }  
```  
  
## <a name="displaying-the-callers-information"></a><span data-ttu-id="eea21-157">Exibindo informações os chamadores</span><span class="sxs-lookup"><span data-stu-id="eea21-157">Displaying the Callers' Information</span></span>  
 <span data-ttu-id="eea21-158">Para exibir informações do chamador, use o `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` conforme mostrado no código de exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="eea21-158">To display the caller's information, use the `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` as shown in the following sample code.</span></span> <span data-ttu-id="eea21-159">O `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` contém declarações de autorização associadas ao chamador atual.</span><span class="sxs-lookup"><span data-stu-id="eea21-159">The `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` contains authorization claims associated with the current caller.</span></span> <span data-ttu-id="eea21-160">As declarações são fornecidas pelo `CreditCardToken` classe em seu `AuthorizationPolicies` coleção.</span><span class="sxs-lookup"><span data-stu-id="eea21-160">The claims are supplied by the `CreditCardToken` class in its `AuthorizationPolicies` collection.</span></span>  
  
```  
bool TryGetStringClaimValue(ClaimSet claimSet, string claimType, out string claimValue)  
{  
    claimValue = null;  
    IEnumerable<Claim> matchingClaims = claimSet.FindClaims(claimType,  
        Rights.PossessProperty);  
    if (matchingClaims == null)  
        return false;  
    IEnumerator<Claim> enumerator = matchingClaims.GetEnumerator();  
    enumerator.MoveNext();  
    claimValue = (enumerator.Current.Resource == null) ? null :   
        enumerator.Current.Resource.ToString();  
    return true;  
}  
  
string GetCallerCreditCardNumber()  
{  
     foreach (ClaimSet claimSet in   
         ServiceSecurityContext.Current.AuthorizationContext.ClaimSets)  
     {  
         string creditCardNumber = null;  
         if (TryGetStringClaimValue(claimSet,   
             Constants.CreditCardNumberClaim, out creditCardNumber))  
             {  
                 string issuer;  
                 if (!TryGetStringClaimValue(claimSet.Issuer,  
                        ClaimTypes.Name, out issuer))  
                 {  
                     issuer = "Unknown";  
                 }  
                 return String.Format(  
                   "Credit card '{0}' issued by '{1}'",   
                   creditCardNumber, issuer);  
        }  
    }  
    return "Credit card is not known";  
}  
```  
  
 <span data-ttu-id="eea21-161">Quando você executar o exemplo, as respostas e solicitações de operação são exibidas na janela do console do cliente.</span><span class="sxs-lookup"><span data-stu-id="eea21-161">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="eea21-162">Pressione ENTER na janela do cliente para desligar o cliente.</span><span class="sxs-lookup"><span data-stu-id="eea21-162">Press ENTER in the client window to shut down the client.</span></span>  
  
## <a name="setup-batch-file"></a><span data-ttu-id="eea21-163">Arquivo de lote</span><span class="sxs-lookup"><span data-stu-id="eea21-163">Setup Batch File</span></span>  
 <span data-ttu-id="eea21-164">Arquivo em lotes bat incluído com este exemplo permite que você configure o servidor com certificados relevantes para executar o aplicativo hospedado no IIS que exige a segurança baseada em certificado do servidor.</span><span class="sxs-lookup"><span data-stu-id="eea21-164">The Setup.bat batch file included with this sample allows you to configure the server with relevant certificates to run the IIS-hosted application that requires server certificate-based security.</span></span> <span data-ttu-id="eea21-165">Esse arquivo em lotes deve ser modificado para funcionar entre computadores ou para trabalhar em um caso não hospedado.</span><span class="sxs-lookup"><span data-stu-id="eea21-165">This batch file must be modified to work across computers or to work in a non-hosted case.</span></span>  
  
 <span data-ttu-id="eea21-166">O exemplo a seguir fornece uma visão geral das seções diferentes dos arquivos de lote para que eles podem ser modificados para executar a configuração apropriada.</span><span class="sxs-lookup"><span data-stu-id="eea21-166">The following provides a brief overview of the different sections of the batch files so that they can be modified to run in the appropriate configuration.</span></span>  
  
-   <span data-ttu-id="eea21-167">Criando o certificado do servidor:</span><span class="sxs-lookup"><span data-stu-id="eea21-167">Creating the server certificate:</span></span>  
  
     <span data-ttu-id="eea21-168">As seguintes linhas do `Setup.bat` arquivo em lotes criar o certificado do servidor a ser usado.</span><span class="sxs-lookup"><span data-stu-id="eea21-168">The following lines from the `Setup.bat` batch file create the server certificate to be used.</span></span> <span data-ttu-id="eea21-169">O `%SERVER_NAME%` variável Especifica o nome do servidor.</span><span class="sxs-lookup"><span data-stu-id="eea21-169">The `%SERVER_NAME%` variable specifies the server name.</span></span> <span data-ttu-id="eea21-170">Altere essa variável para especificar seu próprio nome de servidor.</span><span class="sxs-lookup"><span data-stu-id="eea21-170">Change this variable to specify your own server name.</span></span> <span data-ttu-id="eea21-171">O padrão, esse arquivo em lotes é localhost.</span><span class="sxs-lookup"><span data-stu-id="eea21-171">The default in this batch file is localhost.</span></span> <span data-ttu-id="eea21-172">Se você alterar o `%SERVER_NAME%` variável, você deve percorrer os arquivos Client.cs e Service.cs e substitua todas as instâncias do host local com o nome do servidor que você usa no script bat.</span><span class="sxs-lookup"><span data-stu-id="eea21-172">If you change the `%SERVER_NAME%` variable, you must go through the Client.cs and Service.cs files and replace all instances of localhost with the server name that you use in the Setup.bat script.</span></span>  
  
     <span data-ttu-id="eea21-173">O certificado é armazenado no repositório My (pessoal) sob o `LocalMachine` local do repositório.</span><span class="sxs-lookup"><span data-stu-id="eea21-173">The certificate is stored in My (Personal) store under the `LocalMachine` store location.</span></span> <span data-ttu-id="eea21-174">O certificado é armazenado no repositório de LocalMachine para os serviços hospedados no IIS.</span><span class="sxs-lookup"><span data-stu-id="eea21-174">The certificate is stored in the LocalMachine store for the IIS-hosted services.</span></span> <span data-ttu-id="eea21-175">Para serviços de hospedagem interna, você deve modificar o arquivo em lotes para armazenar o certificado de cliente no local de armazenamento CurrentUser, substituindo a cadeia de caracteres LocalMachine por CurrentUser.</span><span class="sxs-lookup"><span data-stu-id="eea21-175">For self-hosted services, you should modify the batch file to store the client certificate in the CurrentUser store location by replacing the string LocalMachine with CurrentUser.</span></span>  
  
    ```  
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
-   <span data-ttu-id="eea21-176">Instalando o certificado do servidor no repositório de certificados confiáveis do cliente:</span><span class="sxs-lookup"><span data-stu-id="eea21-176">Installing the server certificate into client's trusted certificate store:</span></span>  
  
     <span data-ttu-id="eea21-177">Armazenam as linhas a seguir na cópia de arquivo de lote o certificado do servidor bat para as pessoas confiáveis do cliente.</span><span class="sxs-lookup"><span data-stu-id="eea21-177">The following lines in the Setup.bat batch file copy the server certificate into the client trusted people store.</span></span> <span data-ttu-id="eea21-178">Esta etapa é necessária porque os certificados gerados pela Makecert.exe não são implicitamente confiáveis pelo sistema do cliente.</span><span class="sxs-lookup"><span data-stu-id="eea21-178">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="eea21-179">Se você já tiver um certificado que está enraizado em um certificado de raiz confiável do cliente — por exemplo, um certificado da Microsoft emitido — essa etapa de preenchimento do repositório de certificados de cliente com o certificado do servidor não é necessária.</span><span class="sxs-lookup"><span data-stu-id="eea21-179">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>  
  
    ```  
    echo ************  
    echo copying server cert to client's TrustedPeople store  
    echo ************  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
-   <span data-ttu-id="eea21-180">Para habilitar o acesso à chave privada de certificado do serviço hospedado no IIS, a conta de usuário sob a qual o processo de hospedados no IIS é executado deve ter permissões apropriadas para a chave privada.</span><span class="sxs-lookup"><span data-stu-id="eea21-180">To enable access to the certificate private key from the IIS-hosted service, the user account under which the IIS-hosted process is running must be granted appropriate permissions for the private key.</span></span> <span data-ttu-id="eea21-181">Isso é feito por último etapas no script bat.</span><span class="sxs-lookup"><span data-stu-id="eea21-181">This is accomplished by last steps in the Setup.bat script.</span></span>  
  
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
  
> [!NOTE]
>  <span data-ttu-id="eea21-182">O arquivo em lotes bat é projetado para ser executado de um [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] Prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="eea21-182">The Setup.bat batch file is designed to be run from a [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] Command Prompt.</span></span> <span data-ttu-id="eea21-183">Definir a variável de ambiente PATH dentro de [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] Prompt de comando aponta para o diretório que contém os executáveis exigido pelo script bat.</span><span class="sxs-lookup"><span data-stu-id="eea21-183">The PATH environment variable set within the [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] Command Prompt points to the directory that contains executables required by the Setup.bat script.</span></span>  
  
#### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="eea21-184">Para configurar e criar o exemplo</span><span class="sxs-lookup"><span data-stu-id="eea21-184">To set up and build the sample</span></span>  
  
1.  <span data-ttu-id="eea21-185">Certifique-se de que você executou o [único procedimento de instalação para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="eea21-185">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="eea21-186">Para criar a solução, siga as instruções em [compilar os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="eea21-186">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
#### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="eea21-187">Para executar o exemplo no mesmo computador</span><span class="sxs-lookup"><span data-stu-id="eea21-187">To run the sample on the same computer</span></span>  
  
1.  <span data-ttu-id="eea21-188">Abra um [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] janela de Prompt de comando com privilégios de administrador e execute bat da pasta de instalação do exemplo.</span><span class="sxs-lookup"><span data-stu-id="eea21-188">Open a [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] Command Prompt window with administrator privileges and run Setup.bat from the sample install folder.</span></span> <span data-ttu-id="eea21-189">Isso instala todos os certificados necessários para executar o exemplo. Certifique-se de que o caminho inclui a pasta onde Makecert.exe está localizado.</span><span class="sxs-lookup"><span data-stu-id="eea21-189">This installs all the certificates required for running the sample.Make sure that the path includes the folder where Makecert.exe is located.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="eea21-190">Certifique-se de remover os certificados executando Cleanup.bat quando terminar com o exemplo.</span><span class="sxs-lookup"><span data-stu-id="eea21-190">Be sure to remove the certificates by running Cleanup.bat when finished with the sample.</span></span> <span data-ttu-id="eea21-191">Outros exemplos de segurança usam os mesmos certificados.</span><span class="sxs-lookup"><span data-stu-id="eea21-191">Other security samples use the same certificates.</span></span>  
  
1.  <span data-ttu-id="eea21-192">Inicie Client.exe do diretório client\bin.</span><span class="sxs-lookup"><span data-stu-id="eea21-192">Launch Client.exe from client\bin directory.</span></span> <span data-ttu-id="eea21-193">Atividade do cliente é exibida no aplicativo de console do cliente.</span><span class="sxs-lookup"><span data-stu-id="eea21-193">Client activity is displayed on the client console application.</span></span>  
  
2.  <span data-ttu-id="eea21-194">Se o cliente e o serviço não for capazes de se comunicar, consulte [dicas de solução de problemas](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).</span><span class="sxs-lookup"><span data-stu-id="eea21-194">If the client and service are not able to communicate, see [Troubleshooting Tips](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
#### <a name="to-run-the-sample-across-computer"></a><span data-ttu-id="eea21-195">Para executar o exemplo em um computador</span><span class="sxs-lookup"><span data-stu-id="eea21-195">To run the sample across computer</span></span>  
  
1.  <span data-ttu-id="eea21-196">Crie um diretório no computador de serviço para os binários de serviço.</span><span class="sxs-lookup"><span data-stu-id="eea21-196">Create a directory on the service computer for the service binaries.</span></span>  
  
2.  <span data-ttu-id="eea21-197">Copie os arquivos de programa do serviço para o diretório de serviço no computador de serviço.</span><span class="sxs-lookup"><span data-stu-id="eea21-197">Copy the service program files into the service directory on the service computer.</span></span> <span data-ttu-id="eea21-198">Não se esqueça de copiar CreditCardFile.txt; Caso contrário, o autenticador do cartão de crédito não é possível validar as informações de cartão de crédito enviadas do cliente.</span><span class="sxs-lookup"><span data-stu-id="eea21-198">Do not forget to copy CreditCardFile.txt; otherwise the credit card authenticator cannot validate credit card information sent from the client.</span></span> <span data-ttu-id="eea21-199">Também copie os arquivos. bat e Cleanup.bat para o computador do serviço.</span><span class="sxs-lookup"><span data-stu-id="eea21-199">Also copy the Setup.bat and Cleanup.bat files to the service computer.</span></span>  
  
3.  <span data-ttu-id="eea21-200">Você deve ter um certificado de servidor com o nome da entidade que contém o nome de domínio totalmente qualificado do computador.</span><span class="sxs-lookup"><span data-stu-id="eea21-200">You must have a server certificate with the subject name that contains the fully-qualified domain name of the computer.</span></span> <span data-ttu-id="eea21-201">Você pode criar um usando o bat se você alterar o `%SERVER_NAME%` variável para o nome totalmente qualificado do computador onde o serviço está hospedado.</span><span class="sxs-lookup"><span data-stu-id="eea21-201">You can create one using the Setup.bat if you change the `%SERVER_NAME%` variable to fully-qualified name of the computer where the service is hosted.</span></span> <span data-ttu-id="eea21-202">Observe que o arquivo bat deve ser executado em um prompt de comando do Visual Studio aberto com privilégios de administrador.</span><span class="sxs-lookup"><span data-stu-id="eea21-202">Note that the Setup.bat file must be run in a Visual Studio command prompt opened with administrator privileges.</span></span>  
  
4.  <span data-ttu-id="eea21-203">Copie o certificado do servidor para o armazenamento CurrentUser TrustedPeople no cliente.</span><span class="sxs-lookup"><span data-stu-id="eea21-203">Copy the server certificate into the CurrentUser-TrustedPeople store on the client.</span></span> <span data-ttu-id="eea21-204">Você deve fazer isso apenas se o certificado do servidor não foi emitido por um emissor confiável.</span><span class="sxs-lookup"><span data-stu-id="eea21-204">You must do this only if the server certificate is not issued by a trusted issuer.</span></span>  
  
5.  <span data-ttu-id="eea21-205">No arquivo EchoServiceHost.cs, altere o valor do nome do assunto do certificado para especificar um nome de computador totalmente qualificado em vez de localhost.</span><span class="sxs-lookup"><span data-stu-id="eea21-205">In the EchoServiceHost.cs file, change the value of the certificate subject name to specify a fully-qualified computer name instead of localhost.</span></span>  
  
6.  <span data-ttu-id="eea21-206">Copie os arquivos de programa do cliente na pasta \client\bin\, sob a pasta de idioma específico, para o computador cliente.</span><span class="sxs-lookup"><span data-stu-id="eea21-206">Copy the client program files from the \client\bin\ folder, under the language-specific folder, to the client computer.</span></span>  
  
7.  <span data-ttu-id="eea21-207">No arquivo Client.cs, altere o valor do endereço do ponto de extremidade para coincidir com o novo endereço do seu serviço.</span><span class="sxs-lookup"><span data-stu-id="eea21-207">In the Client.cs file, change the address value of the endpoint to match the new address of your service.</span></span>  
  
8.  <span data-ttu-id="eea21-208">No arquivo Client.cs altere o nome da entidade do certificado x. 509 do serviço para corresponder ao nome de computador totalmente qualificado do host remoto em vez de localhost.</span><span class="sxs-lookup"><span data-stu-id="eea21-208">In the Client.cs file change the subject name of the service X.509 certificate to match the fully-qualified computer name of the remote host instead of localhost.</span></span>  
  
9. <span data-ttu-id="eea21-209">No computador cliente, inicie o Client.exe em uma janela de prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="eea21-209">On the client computer, launch Client.exe from a command prompt window.</span></span>  
  
10. <span data-ttu-id="eea21-210">Se o cliente e o serviço não for capazes de se comunicar, consulte [dicas de solução de problemas](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).</span><span class="sxs-lookup"><span data-stu-id="eea21-210">If the client and service are not able to communicate, see [Troubleshooting Tips](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
#### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="eea21-211">A limpeza após a amostra</span><span class="sxs-lookup"><span data-stu-id="eea21-211">To clean up after the sample</span></span>  
  
1.  <span data-ttu-id="eea21-212">Execute Cleanup.bat na pasta exemplos depois de terminar a execução do exemplo.</span><span class="sxs-lookup"><span data-stu-id="eea21-212">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eea21-213">Consulte também</span><span class="sxs-lookup"><span data-stu-id="eea21-213">See Also</span></span>
