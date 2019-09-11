---
title: Token personalizado
ms.date: 03/30/2017
ms.assetid: e7fd8b38-c370-454f-ba3e-19759019f03d
ms.openlocfilehash: c3c6cfd9d1742f7e839d7b40220792ba455d7673
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855513"
---
# <a name="custom-token"></a><span data-ttu-id="e4c15-102">Token personalizado</span><span class="sxs-lookup"><span data-stu-id="e4c15-102">Custom Token</span></span>

<span data-ttu-id="e4c15-103">Este exemplo demonstra como adicionar uma implementação de token personalizada a um aplicativo Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="e4c15-103">This sample demonstrates how to add a custom token implementation into a Windows Communication Foundation (WCF) application.</span></span> <span data-ttu-id="e4c15-104">O exemplo usa um `CreditCardToken` para transmitir informações com segurança sobre cartões de crédito do cliente para o serviço.</span><span class="sxs-lookup"><span data-stu-id="e4c15-104">The example uses a `CreditCardToken` to securely pass information about client credit cards to the service.</span></span> <span data-ttu-id="e4c15-105">O token é passado no cabeçalho da mensagem WS-Security e é assinado e criptografado usando o elemento de ligação de segurança simétrica junto com o corpo da mensagem e outros cabeçalhos de mensagem.</span><span class="sxs-lookup"><span data-stu-id="e4c15-105">The token is passed in the WS-Security message header and is signed and encrypted using the symmetric security binding element along with message body and other message headers.</span></span> <span data-ttu-id="e4c15-106">Isso é útil em casos em que os tokens internos não são suficientes.</span><span class="sxs-lookup"><span data-stu-id="e4c15-106">This is useful in cases where the built-in tokens are not sufficient.</span></span> <span data-ttu-id="e4c15-107">Este exemplo demonstra como fornecer um token de segurança personalizado para um serviço em vez de usar um dos tokens internos.</span><span class="sxs-lookup"><span data-stu-id="e4c15-107">This sample demonstrates how to provide a custom security token to a service instead of using one of the built-in tokens.</span></span> <span data-ttu-id="e4c15-108">O serviço implementa um contrato que define um padrão de comunicação de solicitação-resposta.</span><span class="sxs-lookup"><span data-stu-id="e4c15-108">The service implements a contract that defines a request-reply communication pattern.</span></span>

> [!NOTE]
> <span data-ttu-id="e4c15-109">O procedimento de instalação e as instruções de Build para este exemplo estão localizados no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="e4c15-109">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

 <span data-ttu-id="e4c15-110">Para resumir, este exemplo demonstra o seguinte:</span><span class="sxs-lookup"><span data-stu-id="e4c15-110">To summarize, this sample demonstrates the following:</span></span>

- <span data-ttu-id="e4c15-111">Como um cliente pode passar um token de segurança personalizado para um serviço.</span><span class="sxs-lookup"><span data-stu-id="e4c15-111">How a client can pass a custom security token to a service.</span></span>

- <span data-ttu-id="e4c15-112">Como o serviço pode consumir e validar um token de segurança personalizado.</span><span class="sxs-lookup"><span data-stu-id="e4c15-112">How the service can consume and validate a custom security token.</span></span>

- <span data-ttu-id="e4c15-113">Como o código do serviço WCF pode obter as informações sobre tokens de segurança recebidos, incluindo o token de segurança personalizado.</span><span class="sxs-lookup"><span data-stu-id="e4c15-113">How the WCF service code can obtain the information about received security tokens including the custom security token.</span></span>

- <span data-ttu-id="e4c15-114">Como o certificado X. 509 do servidor é usado para proteger a chave simétrica usada para criptografia e assinatura de mensagens.</span><span class="sxs-lookup"><span data-stu-id="e4c15-114">How the server's X.509 certificate is used to protect the symmetric key used for message encryption and signature.</span></span>

## <a name="client-authentication-using-a-custom-security-token"></a><span data-ttu-id="e4c15-115">Autenticação de cliente usando um token de segurança personalizado</span><span class="sxs-lookup"><span data-stu-id="e4c15-115">Client Authentication Using a Custom Security Token</span></span>

 <span data-ttu-id="e4c15-116">O serviço expõe um único ponto de extremidade que é criado `BindingHelper` programaticamente usando classes e `EchoServiceHost` .</span><span class="sxs-lookup"><span data-stu-id="e4c15-116">The service exposes a single endpoint that is programmatically created using `BindingHelper` and `EchoServiceHost` classes.</span></span> <span data-ttu-id="e4c15-117">O ponto de extremidade consiste em um endereço, uma associação e um contrato.</span><span class="sxs-lookup"><span data-stu-id="e4c15-117">The endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="e4c15-118">A associação é configurada com uma associação `SymmetricSecurityBindingElement` personalizada `HttpTransportBindingElement`usando e.</span><span class="sxs-lookup"><span data-stu-id="e4c15-118">The binding is configured with a custom binding using `SymmetricSecurityBindingElement` and `HttpTransportBindingElement`.</span></span> <span data-ttu-id="e4c15-119">Este exemplo define o `SymmetricSecurityBindingElement` para usar o certificado X. 509 de um serviço para proteger a chave simétrica durante a transmissão e passar um `CreditCardToken` personalizado em um cabeçalho de mensagem do WS-Security como um token de segurança assinado e criptografado.</span><span class="sxs-lookup"><span data-stu-id="e4c15-119">This sample sets the `SymmetricSecurityBindingElement` to use a service's X.509 certificate to protect the symmetric key during transmission and to pass a custom `CreditCardToken` in a WS-Security message header as a signed and encrypted security token.</span></span> <span data-ttu-id="e4c15-120">O comportamento especifica as credenciais de serviço que devem ser usadas para autenticação de cliente e também informações sobre o certificado X. 509 do serviço.</span><span class="sxs-lookup"><span data-stu-id="e4c15-120">The behavior specifies the service credentials that are to be used for client authentication and also information about the service X.509 certificate.</span></span>

```csharp
public static class BindingHelper
{
    public static Binding CreateCreditCardBinding()
    {
        var httpTransport = new HttpTransportBindingElement();

        // The message security binding element will be configured to require a credit card.
        // The token that is encrypted with the service's certificate.
        var messageSecurity = new SymmetricSecurityBindingElement();
        messageSecurity.EndpointSupportingTokenParameters.SignedEncrypted.Add(new CreditCardTokenParameters());
        X509SecurityTokenParameters x509ProtectionParameters = new X509SecurityTokenParameters();
        x509ProtectionParameters.InclusionMode = SecurityTokenInclusionMode.Never;
        messageSecurity.ProtectionTokenParameters = x509ProtectionParameters;
        return new CustomBinding(messageSecurity, httpTransport);
    }
}
```

 <span data-ttu-id="e4c15-121">Para consumir um token de cartão de crédito na mensagem, o exemplo usa credenciais de serviço personalizadas para fornecer essa funcionalidade.</span><span class="sxs-lookup"><span data-stu-id="e4c15-121">To consume a credit card token in the message, the sample uses custom service credentials to provide this functionality.</span></span> <span data-ttu-id="e4c15-122">A classe de credenciais de serviço está localizada `CreditCardServiceCredentials` na classe e é adicionada às coleções de comportamentos do host de serviço `EchoServiceHost.InitializeRuntime` no método.</span><span class="sxs-lookup"><span data-stu-id="e4c15-122">The service credentials class is located in the `CreditCardServiceCredentials` class and is added to the behaviors collections of the service host in the `EchoServiceHost.InitializeRuntime` method.</span></span>

```csharp
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

 <span data-ttu-id="e4c15-123">O ponto de extremidade do cliente é configurado de maneira semelhante ao ponto de extremidade de serviço.</span><span class="sxs-lookup"><span data-stu-id="e4c15-123">The client endpoint is configured in a similar manner as the service endpoint.</span></span> <span data-ttu-id="e4c15-124">O cliente usa a mesma `BindingHelper` classe para criar uma associação.</span><span class="sxs-lookup"><span data-stu-id="e4c15-124">The client uses the same `BindingHelper` class to create a binding.</span></span> <span data-ttu-id="e4c15-125">O restante da instalação está localizado na `Client` classe.</span><span class="sxs-lookup"><span data-stu-id="e4c15-125">The rest of the setup is located in the `Client` class.</span></span> <span data-ttu-id="e4c15-126">O cliente também define as informações a serem contidas `CreditCardToken` no e no certificado X. 509 no código de instalação, adicionando uma `CreditCardClientCredentials` instância com os dados apropriados à coleção de comportamentos de ponto de extremidade do cliente.</span><span class="sxs-lookup"><span data-stu-id="e4c15-126">The client also sets information to be contained in the `CreditCardToken` and information about the service X.509 certificate in the setup code by adding a `CreditCardClientCredentials` instance with the proper data to the client endpoint behaviors collection.</span></span> <span data-ttu-id="e4c15-127">O exemplo usa o certificado X. 509 com o nome da `CN=localhost` entidade definido como o certificado de serviço.</span><span class="sxs-lookup"><span data-stu-id="e4c15-127">The sample uses X.509 certificate with subject name set to `CN=localhost` as the service certificate.</span></span>

```csharp
Binding creditCardBinding = BindingHelper.CreateCreditCardBinding();
var serviceAddress = new EndpointAddress("http://localhost/servicemodelsamples/service.svc");

// Create a client with given client endpoint configuration.
channelFactory = new ChannelFactory<IEchoService>(creditCardBinding, serviceAddress);

// Configure the credit card credentials on the channel factory.
var credentials =
      new CreditCardClientCredentials(
      new CreditCardInfo(creditCardNumber, issuer, expirationTime));
// Configure the service certificate on the credentials.
credentials.ServiceCertificate.SetDefaultCertificate(
      "CN=localhost", StoreLocation.LocalMachine, StoreName.My);

// Replace ClientCredentials with CreditCardClientCredentials.
channelFactory.Endpoint.Behaviors.Remove(typeof(ClientCredentials));
channelFactory.Endpoint.Behaviors.Add(credentials);

client = channelFactory.CreateChannel();

Console.WriteLine($"Echo service returned: {client.Echo()}");

((IChannel)client).Close();
channelFactory.Close();
```

## <a name="custom-security-token-implementation"></a><span data-ttu-id="e4c15-128">Implementação do token de segurança personalizado</span><span class="sxs-lookup"><span data-stu-id="e4c15-128">Custom Security Token Implementation</span></span>

 <span data-ttu-id="e4c15-129">Para habilitar um token de segurança personalizado no WCF, crie uma representação de objeto do token de segurança personalizado.</span><span class="sxs-lookup"><span data-stu-id="e4c15-129">To enable a custom security token in WCF, create an object representation of the custom security token.</span></span> <span data-ttu-id="e4c15-130">O exemplo tem essa representação na `CreditCardToken` classe.</span><span class="sxs-lookup"><span data-stu-id="e4c15-130">The sample has this representation in the `CreditCardToken` class.</span></span> <span data-ttu-id="e4c15-131">A representação do objeto é responsável por manter todas as informações de token de segurança relevantes e fornecer uma lista de chaves de segurança contidas no token de segurança.</span><span class="sxs-lookup"><span data-stu-id="e4c15-131">The object representation is responsible for holding all relevant security token information and to provide a list of security keys contained in the security token.</span></span> <span data-ttu-id="e4c15-132">Nesse caso, o token de segurança do cartão de crédito não contém nenhuma chave de segurança.</span><span class="sxs-lookup"><span data-stu-id="e4c15-132">In this case, the credit card security token does not contain any security key.</span></span>

 <span data-ttu-id="e4c15-133">A próxima seção descreve o que deve ser feito para permitir que um token personalizado seja transmitido pela rede e consumido por um ponto de extremidade do WCF.</span><span class="sxs-lookup"><span data-stu-id="e4c15-133">The next section describes what must be done to enable a custom token to be transmitted over the wire and consumed by a WCF endpoint.</span></span>

```csharp
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
            throw new ArgumentNullException(nameof(cardInfo));

        if (id == null)
            throw new ArgumentNullException(nameof(id));

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

## <a name="getting-the-custom-credit-card-token-to-and-from-the-message"></a><span data-ttu-id="e4c15-134">Obtendo o token do cartão de crédito personalizado de e para a mensagem</span><span class="sxs-lookup"><span data-stu-id="e4c15-134">Getting the Custom Credit Card Token to and from the Message</span></span>

 <span data-ttu-id="e4c15-135">Os serializadores de token de segurança no WCF são responsáveis por criar uma representação de objeto de tokens de segurança do XML na mensagem e criar um formulário XML dos tokens de segurança.</span><span class="sxs-lookup"><span data-stu-id="e4c15-135">Security token serializers in WCF are responsible for creating an object representation of security tokens from the XML in the message and creating a XML form of the security tokens.</span></span> <span data-ttu-id="e4c15-136">Eles também são responsáveis por outras funcionalidades, como leitura e gravação de identificadores de chave que apontam para tokens de segurança, mas este exemplo usa apenas a funcionalidade relacionada ao token de segurança.</span><span class="sxs-lookup"><span data-stu-id="e4c15-136">They are also responsible for other functionality such as reading and writing key identifiers pointing to security tokens, but this example uses only security token-related functionality.</span></span> <span data-ttu-id="e4c15-137">Para habilitar um token personalizado, você deve implementar seu próprio serializador de token de segurança.</span><span class="sxs-lookup"><span data-stu-id="e4c15-137">To enable a custom token you must implement your own security token serializer.</span></span> <span data-ttu-id="e4c15-138">Este exemplo usa a `CreditCardSecurityTokenSerializer` classe para essa finalidade.</span><span class="sxs-lookup"><span data-stu-id="e4c15-138">This sample uses the `CreditCardSecurityTokenSerializer` class for this purpose.</span></span>

 <span data-ttu-id="e4c15-139">No serviço, o serializador personalizado lê o formulário XML do token personalizado e cria a representação de objeto de token personalizado a partir dele.</span><span class="sxs-lookup"><span data-stu-id="e4c15-139">On the service, the custom serializer reads the XML form of the custom token and creates the custom token object representation from it.</span></span>

 <span data-ttu-id="e4c15-140">No cliente, a `CreditCardSecurityTokenSerializer` classe grava as informações contidas na representação do objeto de token de segurança no gravador de XML.</span><span class="sxs-lookup"><span data-stu-id="e4c15-140">On the client, the `CreditCardSecurityTokenSerializer` class writes the information contained in the security token object representation into the XML writer.</span></span>

```csharp
public class CreditCardSecurityTokenSerializer : WSSecurityTokenSerializer
{
    public CreditCardSecurityTokenSerializer(SecurityTokenVersion version) : base() { }

    protected override bool CanReadTokenCore(XmlReader reader)
    {
        XmlDictionaryReader localReader = XmlDictionaryReader.CreateDictionaryReader(reader);

        if (reader == null)
            throw new ArgumentNullException(nameof(reader));

        if (reader.IsStartElement(Constants.CreditCardTokenName, Constants.CreditCardTokenNamespace))
            return true;

        return base.CanReadTokenCore(reader);
    }

    protected override SecurityToken ReadTokenCore(XmlReader reader, SecurityTokenResolver tokenResolver)
    {
        if (reader == null)
            throw new ArgumentNullException(nameof(reader));

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

            var cardInfo = new CreditCardInfo(creditCardNumber, creditCardIssuer, expirationTime);

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
        return base.CanWriteTokenCore(token);
    }

    protected override void WriteTokenCore(XmlWriter writer, SecurityToken token)
    {
        if (writer == null)
            throw new ArgumentNullException(nameof(writer));
        if (token == null)
            throw new ArgumentNullException(nameof(token));

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

## <a name="how-token-provider-and-token-authenticator-classes-are-created"></a><span data-ttu-id="e4c15-141">Como as classes do provedor de token e do autenticador de token são criadas</span><span class="sxs-lookup"><span data-stu-id="e4c15-141">How Token Provider and Token Authenticator Classes are Created</span></span>

 <span data-ttu-id="e4c15-142">As credenciais de cliente e serviço são responsáveis por fornecer a instância do Gerenciador de token de segurança.</span><span class="sxs-lookup"><span data-stu-id="e4c15-142">Client and service credentials are responsible for providing the security token manager instance.</span></span> <span data-ttu-id="e4c15-143">A instância do Gerenciador de token de segurança é usada para obter provedores de token, autenticadores de token e serializadores de token.</span><span class="sxs-lookup"><span data-stu-id="e4c15-143">The security token manager instance is used to get token providers, token authenticators and token serializers.</span></span>

 <span data-ttu-id="e4c15-144">O provedor de token cria uma representação de objeto do token com base nas informações contidas nas credenciais do cliente ou do serviço.</span><span class="sxs-lookup"><span data-stu-id="e4c15-144">The token provider creates an object representation of the token based on the information contained in the client or service credentials.</span></span> <span data-ttu-id="e4c15-145">A representação do objeto token é gravada na mensagem usando o serializador de token (abordado na seção anterior).</span><span class="sxs-lookup"><span data-stu-id="e4c15-145">The token object representation is then written to the message using the token serializer (discussed in the previous section).</span></span>

 <span data-ttu-id="e4c15-146">O autenticador de token valida os tokens que chegam na mensagem.</span><span class="sxs-lookup"><span data-stu-id="e4c15-146">The token authenticator validates tokens that arrive in the message.</span></span> <span data-ttu-id="e4c15-147">A representação de objeto de token de entrada é criada pelo serializador de token.</span><span class="sxs-lookup"><span data-stu-id="e4c15-147">The incoming token object representation is created by the token serializer.</span></span> <span data-ttu-id="e4c15-148">Essa representação de objeto é passada para o autenticador de token para validação.</span><span class="sxs-lookup"><span data-stu-id="e4c15-148">This object representation is then passed to the token authenticator for validation.</span></span> <span data-ttu-id="e4c15-149">Depois que o token é validado com êxito, o autenticador de token `IAuthorizationPolicy` retorna uma coleção de objetos que representam as informações contidas no token.</span><span class="sxs-lookup"><span data-stu-id="e4c15-149">After the token is successfully validated, the token authenticator returns a collection of `IAuthorizationPolicy` objects that represent the information contained in the token.</span></span> <span data-ttu-id="e4c15-150">Essas informações são usadas posteriormente durante o processamento de mensagens para executar decisões de autorização e para fornecer declarações para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e4c15-150">This information is used later during the message processing to perform authorization decisions and to provide claims for the application.</span></span> <span data-ttu-id="e4c15-151">Neste exemplo, o autenticador de token de cartão `CreditCardTokenAuthorizationPolicy` de crédito usa para essa finalidade.</span><span class="sxs-lookup"><span data-stu-id="e4c15-151">In this example, the credit card token authenticator uses `CreditCardTokenAuthorizationPolicy` for this purpose.</span></span>

 <span data-ttu-id="e4c15-152">O serializador de token é responsável por obter a representação do objeto do token de e para a conexão.</span><span class="sxs-lookup"><span data-stu-id="e4c15-152">The token serializer is responsible for getting the object representation of the token to and from the wire.</span></span> <span data-ttu-id="e4c15-153">Isso é abordado na seção anterior.</span><span class="sxs-lookup"><span data-stu-id="e4c15-153">This is discussed in the previous section.</span></span>

 <span data-ttu-id="e4c15-154">Neste exemplo, usamos um provedor de token somente no cliente e um autenticador de token somente no serviço, pois queremos transmitir um token de cartão de crédito somente na direção do cliente para o serviço.</span><span class="sxs-lookup"><span data-stu-id="e4c15-154">In this sample, we use a token provider only on the client and a token authenticator only on the service, because we want to transmit a credit card token only in the client-to-service direction.</span></span>

 <span data-ttu-id="e4c15-155">A funcionalidade no cliente está localizada nas `CreditCardClientCredentials` `CreditCardClientCredentialsSecurityTokenManager` classes e `CreditCardTokenProvider` .</span><span class="sxs-lookup"><span data-stu-id="e4c15-155">The functionality on the client is located in the `CreditCardClientCredentials`, `CreditCardClientCredentialsSecurityTokenManager` and `CreditCardTokenProvider` classes.</span></span>

 <span data-ttu-id="e4c15-156">No serviço, a funcionalidade `CreditCardServiceCredentials`reside nas classes `CreditCardTokenAuthenticator` , `CreditCardServiceCredentialsSecurityTokenManager`e `CreditCardTokenAuthorizationPolicy` .</span><span class="sxs-lookup"><span data-stu-id="e4c15-156">On the service, the functionality resides in the `CreditCardServiceCredentials`, `CreditCardServiceCredentialsSecurityTokenManager`, `CreditCardTokenAuthenticator` and `CreditCardTokenAuthorizationPolicy` classes.</span></span>

```csharp
    public class CreditCardClientCredentials : ClientCredentials
    {
        CreditCardInfo creditCardInfo;

        public CreditCardClientCredentials(CreditCardInfo creditCardInfo)
            : base()
        {
            if (creditCardInfo == null)
                throw new ArgumentNullException(nameof(creditCardInfo));

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
            // Handle this token for Custom.
            if (tokenRequirement.TokenType == Constants.CreditCardTokenType)
                return new CreditCardTokenProvider(this.creditCardClientCredentials.CreditCardInfo);
            // Return server cert.
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
                throw new ArgumentNullException(nameof(creditCardInfo));

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
                throw new ArgumentNullException(nameof(creditCardFile));

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
                throw new SecurityTokenValidationException("The credit card has expired.");
            if (!IsCardNumberAndExpirationValid(creditCardToken.CardInfo))
                throw new SecurityTokenValidationException("Unknown or invalid credit card.");

            // the credit card token has only 1 claim - the card number. The issuer for the claim is the
            // credit card issuer

            var cardIssuerClaimSet = new DefaultClaimSet(new Claim(ClaimTypes.Name, creditCardToken.CardInfo.CardIssuer, Rights.PossessProperty));
            var cardClaimSet = new DefaultClaimSet(cardIssuerClaimSet, new Claim(Constants.CreditCardNumberClaim, creditCardToken.CardInfo.CardNumber, Rights.PossessProperty));
            var policies = new List<IAuthorizationPolicy>(1);
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
                using (var myStreamReader = new StreamReader(this.creditCardsFile))
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
                throw new ArgumentNullException(nameof(issuedClaims));
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

## <a name="displaying-the-callers-information"></a><span data-ttu-id="e4c15-157">Exibindo as informações dos chamadores</span><span class="sxs-lookup"><span data-stu-id="e4c15-157">Displaying the Callers' Information</span></span>

 <span data-ttu-id="e4c15-158">Para exibir as informações do chamador, use o `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` conforme mostrado no código de exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="e4c15-158">To display the caller's information, use the `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` as shown in the following sample code.</span></span> <span data-ttu-id="e4c15-159">O `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` contém declarações de autorização associadas ao chamador atual.</span><span class="sxs-lookup"><span data-stu-id="e4c15-159">The `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` contains authorization claims associated with the current caller.</span></span> <span data-ttu-id="e4c15-160">As declarações são fornecidas pela `CreditCardToken` classe em sua `AuthorizationPolicies` coleção.</span><span class="sxs-lookup"><span data-stu-id="e4c15-160">The claims are supplied by the `CreditCardToken` class in its `AuthorizationPolicies` collection.</span></span>

```csharp
bool TryGetStringClaimValue(ClaimSet claimSet, string claimType, out string claimValue)
{
    claimValue = null;
    IEnumerable<Claim> matchingClaims = claimSet.FindClaims(claimType, Rights.PossessProperty);
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
                 return $"Credit card '{creditCardNumber}' issued by '{issuer}'";
        }
    }
    return "Credit card is not known";
}
```

 <span data-ttu-id="e4c15-161">Quando você executa o exemplo, as solicitações de operação e as respostas são exibidas na janela do console do cliente.</span><span class="sxs-lookup"><span data-stu-id="e4c15-161">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="e4c15-162">Pressione ENTER na janela do cliente para desligar o cliente.</span><span class="sxs-lookup"><span data-stu-id="e4c15-162">Press ENTER in the client window to shut down the client.</span></span>

## <a name="setup-batch-file"></a><span data-ttu-id="e4c15-163">Arquivo em lotes de instalação</span><span class="sxs-lookup"><span data-stu-id="e4c15-163">Setup Batch File</span></span>

 <span data-ttu-id="e4c15-164">O arquivo em lotes setup. bat incluído com este exemplo permite que você configure o servidor com certificados relevantes para executar o aplicativo hospedado pelo IIS que requer segurança baseada em certificado do servidor.</span><span class="sxs-lookup"><span data-stu-id="e4c15-164">The Setup.bat batch file included with this sample allows you to configure the server with relevant certificates to run the IIS-hosted application that requires server certificate-based security.</span></span> <span data-ttu-id="e4c15-165">Esse arquivo em lotes deve ser modificado para funcionar em computadores ou para funcionar em um caso não hospedado.</span><span class="sxs-lookup"><span data-stu-id="e4c15-165">This batch file must be modified to work across computers or to work in a non-hosted case.</span></span>

 <span data-ttu-id="e4c15-166">Veja a seguir uma breve visão geral das diferentes seções dos arquivos em lotes para que eles possam ser modificados para serem executados na configuração apropriada.</span><span class="sxs-lookup"><span data-stu-id="e4c15-166">The following provides a brief overview of the different sections of the batch files so that they can be modified to run in the appropriate configuration.</span></span>

- <span data-ttu-id="e4c15-167">Criando o certificado do servidor:</span><span class="sxs-lookup"><span data-stu-id="e4c15-167">Creating the server certificate:</span></span>

     <span data-ttu-id="e4c15-168">As linhas a seguir do `Setup.bat` arquivo em lotes criam o certificado do servidor a ser usado.</span><span class="sxs-lookup"><span data-stu-id="e4c15-168">The following lines from the `Setup.bat` batch file create the server certificate to be used.</span></span> <span data-ttu-id="e4c15-169">A `%SERVER_NAME%` variável especifica o nome do servidor.</span><span class="sxs-lookup"><span data-stu-id="e4c15-169">The `%SERVER_NAME%` variable specifies the server name.</span></span> <span data-ttu-id="e4c15-170">Altere essa variável para especificar seu próprio nome de servidor.</span><span class="sxs-lookup"><span data-stu-id="e4c15-170">Change this variable to specify your own server name.</span></span> <span data-ttu-id="e4c15-171">O padrão neste arquivo em lotes é localhost.</span><span class="sxs-lookup"><span data-stu-id="e4c15-171">The default in this batch file is localhost.</span></span> <span data-ttu-id="e4c15-172">Se você alterar a `%SERVER_NAME%` variável, deverá percorrer os arquivos Client.cs e Service.cs e substituir todas as instâncias do localhost pelo nome do servidor que você usa no script setup. bat.</span><span class="sxs-lookup"><span data-stu-id="e4c15-172">If you change the `%SERVER_NAME%` variable, you must go through the Client.cs and Service.cs files and replace all instances of localhost with the server name that you use in the Setup.bat script.</span></span>

     <span data-ttu-id="e4c15-173">O certificado é armazenado no meu repositório (pessoal) no local `LocalMachine` do repositório.</span><span class="sxs-lookup"><span data-stu-id="e4c15-173">The certificate is stored in My (Personal) store under the `LocalMachine` store location.</span></span> <span data-ttu-id="e4c15-174">O certificado é armazenado no armazenamento LocalMachine para os serviços hospedados pelo IIS.</span><span class="sxs-lookup"><span data-stu-id="e4c15-174">The certificate is stored in the LocalMachine store for the IIS-hosted services.</span></span> <span data-ttu-id="e4c15-175">Para serviços hospedados internamente, você deve modificar o arquivo em lotes para armazenar o certificado do cliente no local do repositório CurrentUser, substituindo a cadeia de caracteres LocalMachine por CurrentUser.</span><span class="sxs-lookup"><span data-stu-id="e4c15-175">For self-hosted services, you should modify the batch file to store the client certificate in the CurrentUser store location by replacing the string LocalMachine with CurrentUser.</span></span>

    ```
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
    ```

- <span data-ttu-id="e4c15-176">Instalando o certificado do servidor no repositório de certificados confiáveis do cliente:</span><span class="sxs-lookup"><span data-stu-id="e4c15-176">Installing the server certificate into client's trusted certificate store:</span></span>

     <span data-ttu-id="e4c15-177">As linhas a seguir no arquivo em lotes setup. bat copiam o certificado do servidor no repositório de pessoas confiáveis do cliente.</span><span class="sxs-lookup"><span data-stu-id="e4c15-177">The following lines in the Setup.bat batch file copy the server certificate into the client trusted people store.</span></span> <span data-ttu-id="e4c15-178">Essa etapa é necessária porque os certificados gerados pelo MakeCert. exe não são implicitamente confiáveis pelo sistema cliente.</span><span class="sxs-lookup"><span data-stu-id="e4c15-178">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="e4c15-179">Se você já tiver um certificado com raiz em um certificado raiz confiável do cliente — por exemplo, um certificado emitido pela Microsoft — esta etapa de popular o repositório de certificados do cliente com o certificado do servidor não será necessária.</span><span class="sxs-lookup"><span data-stu-id="e4c15-179">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>

    ```
    echo ************
    echo copying server cert to client's TrustedPeople store
    echo ************
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
    ```

- <span data-ttu-id="e4c15-180">Para habilitar o acesso à chave privada do certificado do serviço hospedado pelo IIS, a conta de usuário sob a qual o processo hospedado pelo IIS está em execução deve receber as permissões apropriadas para a chave privada.</span><span class="sxs-lookup"><span data-stu-id="e4c15-180">To enable access to the certificate private key from the IIS-hosted service, the user account under which the IIS-hosted process is running must be granted appropriate permissions for the private key.</span></span> <span data-ttu-id="e4c15-181">Isso é feito pelas últimas etapas do script setup. bat.</span><span class="sxs-lookup"><span data-stu-id="e4c15-181">This is accomplished by last steps in the Setup.bat script.</span></span>

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
> <span data-ttu-id="e4c15-182">O arquivo em lotes setup. bat foi projetado para ser executado em um prompt de comando do Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="e4c15-182">The Setup.bat batch file is designed to be run from a Visual Studio 2012 Command Prompt.</span></span> <span data-ttu-id="e4c15-183">A variável de ambiente PATH definida no prompt de comando do Visual Studio 2012 aponta para o diretório que contém os executáveis exigidos pelo script setup. bat.</span><span class="sxs-lookup"><span data-stu-id="e4c15-183">The PATH environment variable set within the Visual Studio 2012 Command Prompt points to the directory that contains executables required by the Setup.bat script.</span></span>

#### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="e4c15-184">Para configurar e compilar o exemplo</span><span class="sxs-lookup"><span data-stu-id="e4c15-184">To set up and build the sample</span></span>

1. <span data-ttu-id="e4c15-185">Verifique se você executou o [procedimento de configuração única para os exemplos de Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e4c15-185">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="e4c15-186">Para compilar a solução, siga as instruções em [criando os exemplos de Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e4c15-186">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

#### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="e4c15-187">Para executar o exemplo no mesmo computador</span><span class="sxs-lookup"><span data-stu-id="e4c15-187">To run the sample on the same computer</span></span>

1. <span data-ttu-id="e4c15-188">Abra uma janela do prompt de comando do Visual Studio 2012 com privilégios de administrador e execute Setup. bat na pasta de instalação de exemplo.</span><span class="sxs-lookup"><span data-stu-id="e4c15-188">Open a Visual Studio 2012 Command Prompt window with administrator privileges and run Setup.bat from the sample install folder.</span></span> <span data-ttu-id="e4c15-189">Isso instala todos os certificados necessários para executar o exemplo. Certifique-se de que o caminho inclui a pasta onde o MakeCert. exe está localizado.</span><span class="sxs-lookup"><span data-stu-id="e4c15-189">This installs all the certificates required for running the sample.Make sure that the path includes the folder where Makecert.exe is located.</span></span>

> [!NOTE]
> <span data-ttu-id="e4c15-190">Certifique-se de remover os certificados executando Cleanup. bat quando terminar com o exemplo.</span><span class="sxs-lookup"><span data-stu-id="e4c15-190">Be sure to remove the certificates by running Cleanup.bat when finished with the sample.</span></span> <span data-ttu-id="e4c15-191">Outros exemplos de segurança usam os mesmos certificados.</span><span class="sxs-lookup"><span data-stu-id="e4c15-191">Other security samples use the same certificates.</span></span>  
  
1. <span data-ttu-id="e4c15-192">Inicie o Client. exe no diretório client\bin.</span><span class="sxs-lookup"><span data-stu-id="e4c15-192">Launch Client.exe from client\bin directory.</span></span> <span data-ttu-id="e4c15-193">A atividade do cliente é exibida no aplicativo de console do cliente.</span><span class="sxs-lookup"><span data-stu-id="e4c15-193">Client activity is displayed on the client console application.</span></span>  
  
2. <span data-ttu-id="e4c15-194">Se o cliente e o serviço não puderem se comunicar, consulte [dicas de solução de problemas para exemplos do WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="e4c15-194">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
#### <a name="to-run-the-sample-across-computer"></a><span data-ttu-id="e4c15-195">Para executar o exemplo no computador</span><span class="sxs-lookup"><span data-stu-id="e4c15-195">To run the sample across computer</span></span>  
  
1. <span data-ttu-id="e4c15-196">Crie um diretório no computador de serviço para os binários de serviço.</span><span class="sxs-lookup"><span data-stu-id="e4c15-196">Create a directory on the service computer for the service binaries.</span></span>  
  
2. <span data-ttu-id="e4c15-197">Copie os arquivos de programa do serviço para o diretório de serviço no computador do serviço.</span><span class="sxs-lookup"><span data-stu-id="e4c15-197">Copy the service program files into the service directory on the service computer.</span></span> <span data-ttu-id="e4c15-198">Não se esqueça de copiar CreditCardFile. txt; caso contrário, o autenticador de cartão de crédito não poderá validar as informações de cartão de crédito enviadas do cliente.</span><span class="sxs-lookup"><span data-stu-id="e4c15-198">Do not forget to copy CreditCardFile.txt; otherwise the credit card authenticator cannot validate credit card information sent from the client.</span></span> <span data-ttu-id="e4c15-199">Copie também os arquivos Setup. bat e Cleanup. bat para o computador de serviço.</span><span class="sxs-lookup"><span data-stu-id="e4c15-199">Also copy the Setup.bat and Cleanup.bat files to the service computer.</span></span>  
  
3. <span data-ttu-id="e4c15-200">Você deve ter um certificado de servidor com o nome da entidade que contém o nome de domínio totalmente qualificado do computador.</span><span class="sxs-lookup"><span data-stu-id="e4c15-200">You must have a server certificate with the subject name that contains the fully-qualified domain name of the computer.</span></span> <span data-ttu-id="e4c15-201">Você pode criar um usando o setup. bat se alterar a `%SERVER_NAME%` variável para o nome totalmente qualificado do computador em que o serviço está hospedado.</span><span class="sxs-lookup"><span data-stu-id="e4c15-201">You can create one using the Setup.bat if you change the `%SERVER_NAME%` variable to fully-qualified name of the computer where the service is hosted.</span></span> <span data-ttu-id="e4c15-202">Observe que o arquivo setup. bat deve ser executado em um Prompt de Comando do Desenvolvedor para Visual Studio aberto com privilégios de administrador.</span><span class="sxs-lookup"><span data-stu-id="e4c15-202">Note that the Setup.bat file must be run in a Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span>  
  
4. <span data-ttu-id="e4c15-203">Copie o certificado do servidor no repositório CurrentUser-TrustedPeople no cliente.</span><span class="sxs-lookup"><span data-stu-id="e4c15-203">Copy the server certificate into the CurrentUser-TrustedPeople store on the client.</span></span> <span data-ttu-id="e4c15-204">Você deve fazer isso somente se o certificado do servidor não for emitido por um emissor confiável.</span><span class="sxs-lookup"><span data-stu-id="e4c15-204">You must do this only if the server certificate is not issued by a trusted issuer.</span></span>  
  
5. <span data-ttu-id="e4c15-205">No arquivo EchoServiceHost.cs, altere o valor do nome da entidade do certificado para especificar um nome de computador totalmente qualificado em vez de localhost.</span><span class="sxs-lookup"><span data-stu-id="e4c15-205">In the EchoServiceHost.cs file, change the value of the certificate subject name to specify a fully-qualified computer name instead of localhost.</span></span>  
  
6. <span data-ttu-id="e4c15-206">Copie os arquivos de programas do cliente da pasta \client\bin\, na pasta específica do idioma, para o computador cliente.</span><span class="sxs-lookup"><span data-stu-id="e4c15-206">Copy the client program files from the \client\bin\ folder, under the language-specific folder, to the client computer.</span></span>  
  
7. <span data-ttu-id="e4c15-207">No arquivo Client.cs, altere o valor de endereço do ponto de extremidade para corresponder ao novo endereço do serviço.</span><span class="sxs-lookup"><span data-stu-id="e4c15-207">In the Client.cs file, change the address value of the endpoint to match the new address of your service.</span></span>  
  
8. <span data-ttu-id="e4c15-208">No arquivo Client.cs, altere o nome da entidade do certificado X. 509 para corresponder ao nome do computador totalmente qualificado do host remoto, em vez de localhost.</span><span class="sxs-lookup"><span data-stu-id="e4c15-208">In the Client.cs file change the subject name of the service X.509 certificate to match the fully-qualified computer name of the remote host instead of localhost.</span></span>  
  
9. <span data-ttu-id="e4c15-209">No computador cliente, inicie o Client. exe em uma janela de prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="e4c15-209">On the client computer, launch Client.exe from a command prompt window.</span></span>  
  
10. <span data-ttu-id="e4c15-210">Se o cliente e o serviço não puderem se comunicar, consulte [dicas de solução de problemas para exemplos do WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="e4c15-210">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
#### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="e4c15-211">Para limpar após o exemplo</span><span class="sxs-lookup"><span data-stu-id="e4c15-211">To clean up after the sample</span></span>  
  
1. <span data-ttu-id="e4c15-212">Execute o Cleanup. bat na pasta Samples depois de concluir a execução do exemplo.</span><span class="sxs-lookup"><span data-stu-id="e4c15-212">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span>  
