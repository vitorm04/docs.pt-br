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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9509cb2c6478cf82cebd696ab92cd69a7e5b4097
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="custom-token"></a>Token personalizado
Este exemplo demonstra como adicionar uma implementação personalizada de token em um [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] aplicativo. O exemplo usa um `CreditCardToken` para passar com segurança informações sobre cartões de crédito de cliente para o serviço. O token é passado no cabeçalho da mensagem WS-Security e é assinado e criptografado usando o elemento de associação de segurança simétrica junto com o corpo da mensagem e outros cabeçalhos de mensagem. Isso é útil em casos em que os tokens internos não são suficientes. Este exemplo demonstra como fornecer um token de segurança personalizada para um serviço em vez de usar um dos tokens internos. O serviço implementa um contrato que define um padrão de comunicação de solicitação-resposta.  
  
> [!NOTE]
>  As instruções de procedimento e a compilação de configuração para este exemplo estão localizadas no final deste tópico.  
  
 Para resumir, este exemplo demonstra o seguinte:  
  
-   Como um cliente pode passar um token de segurança personalizada para um serviço.  
  
-   Como o serviço pode consumir e validar um token de segurança personalizada.  
  
-   Como o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] código de serviço pode obter as informações sobre tokens de segurança recebido, incluindo o token de segurança personalizada.  
  
-   Como o certificado do servidor x. 509 é usado para proteger a chave simétrica usada para assinatura e criptografia de mensagem.  
  
## <a name="client-authentication-using-a-custom-security-token"></a>Autenticação de cliente usando um Token de segurança personalizado  
 O serviço expõe um ponto de extremidade é criado por meio de programação usando `BindingHelper` e `EchoServiceHost` classes. O ponto de extremidade consiste em um endereço, uma ligação e um contrato. A associação está configurada com uma associação personalizada usando `SymmetricSecurityBindingElement` e `HttpTransportBindingElement`. Este exemplo define o `SymmetricSecurityBindingElement` para usar o certificado x. 509 de um serviço para proteger a chave simétrica durante a transmissão e passar um personalizado `CreditCardToken` em um cabeçalho de mensagem do WS-Security como um token de segurança assinado e criptografado. O comportamento Especifica as credenciais de serviço a ser usado para autenticação de cliente e também informações sobre o certificado x. 509 de serviço.  
  
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
  
 Para consumir um cartão de crédito token na mensagem, o exemplo usa as credenciais de serviço personalizado para fornecer essa funcionalidade. A classe de credenciais de serviço está localizada no `CreditCardServiceCredentials` classe e é adicionado para as coleções de comportamentos do host do serviço no `EchoServiceHost.InitializeRuntime` método.  
  
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
  
 O ponto de extremidade do cliente é configurado de maneira semelhante, como o ponto de extremidade de serviço. O cliente usa o mesmo `BindingHelper` classe para criar uma associação. O restante do programa de instalação está localizado no `Client` classe. O cliente também define informações para ser contida no `CreditCardToken` e informações sobre o certificado x. 509 de serviço no código do programa de instalação adicionando um `CreditCardClientCredentials` instância com os dados apropriados para a coleção de comportamentos de ponto de extremidade do cliente. O exemplo usa o certificado x. 509 com o nome da entidade definida como `CN=localhost` como o certificado de serviço.  
  
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
  
## <a name="custom-security-token-implementation"></a>Implementação de Token de segurança personalizada  
 Para habilitar um token de segurança personalizada no [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], criar uma representação de objeto do token de segurança personalizada. O exemplo tem essa representação no `CreditCardToken` classe. A representação de objeto é responsável por manter todas as informações de token de segurança relevantes e para fornecer uma lista de chaves de segurança contidas no token de segurança. Nesse caso, o token de segurança do cartão de crédito não contém nenhuma chave de segurança.  
  
 A próxima seção descreve o que deve ser feito para permitir que um token personalizado para serem transmitidos eletronicamente e consumido por um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ponto de extremidade.  
  
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
  
## <a name="getting-the-custom-credit-card-token-to-and-from-the-message"></a>Obtendo o cartão de crédito Token de e para a mensagem  
 Serializadores de token de segurança em [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] são responsáveis por criar uma representação de objeto dos tokens de segurança do XML da mensagem e criar um formulário XML dos tokens de segurança. Eles também são responsáveis por outros recursos, como leitura e gravação de identificadores de chave apontando para tokens de segurança, mas este exemplo usa somente segurança token funcionalidades relacionadas. Para habilitar um personalizado token você deve implementar seu próprio serializador de token de segurança. Este exemplo usa o `CreditCardSecurityTokenSerializer` classe para essa finalidade.  
  
 Sobre o serviço, o serializador personalizado lê o formulário XML do token personalizado e cria a representação de objeto de token personalizado dele.  
  
 No cliente, o `CreditCardSecurityTokenSerializer` classe grava as informações contidas na representação de objeto de token de segurança para o gravador de XML.  
  
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
  
## <a name="how-token-provider-and-token-authenticator-classes-are-created"></a>Como o provedor de Token e Classes do autenticador de Token são criados  
 As credenciais de cliente e de serviço serão responsáveis por fornecer a instância do Gerenciador de token de segurança. A instância do Gerenciador de token de segurança é usada para obter os provedores de token, autenticadores de token e serializadores de token.  
  
 O provedor de token cria uma representação de objeto do token com base nas informações contidas nas credenciais do cliente ou serviço. A representação de objeto de token é gravada para a mensagem usando o serializador de token (discutido na seção anterior).  
  
 O autenticador de token valida os tokens que chegam na mensagem. A entrada representação de objeto de token é criada pelo serializador de token. Essa representação de objeto é então passada para o autenticador de token para validação. Depois que o token é validado com êxito, o autenticador de token retorna uma coleção de `IAuthorizationPolicy` objetos que representam as informações contidas no token. Essas informações são usadas durante o processamento da mensagem para decisões de autorização de executar e fornecer declarações para o aplicativo. Neste exemplo, o autenticador de token de cartão de crédito usa `CreditCardTokenAuthorizationPolicy` para essa finalidade.  
  
 O serializador de token é responsável por obter a representação de objeto do token para e da transmissão. Isso é discutido na seção anterior.  
  
 Neste exemplo, usamos um provedor de token somente no cliente e um autenticador de token apenas no serviço, porque você deseja transmitir um token de cartão de crédito somente na direção serviço do cliente.  
  
 A funcionalidade no cliente está localizada no `CreditCardClientCrendentials`, `CreditCardClientCredentialsSecurityTokenManager` e `CreditCardTokenProvider` classes.  
  
 Sobre o serviço, a funcionalidade reside no `CreditCardServiceCredentials`, `CreditCardServiceCredentialsSecurityTokenManager`, `CreditCardTokenAuthenticator` e `CreditCardTokenAuthorizationPolicy` classes.  
  
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
  
## <a name="displaying-the-callers-information"></a>Exibindo informações os chamadores  
 Para exibir informações do chamador, use o `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` conforme mostrado no código de exemplo a seguir. O `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` contém declarações de autorização associadas ao chamador atual. As declarações são fornecidas pelo `CreditCardToken` classe em seu `AuthorizationPolicies` coleção.  
  
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
  
 Quando você executar o exemplo, as respostas e solicitações de operação são exibidas na janela do console do cliente. Pressione ENTER na janela do cliente para desligar o cliente.  
  
## <a name="setup-batch-file"></a>Arquivo de lote  
 Arquivo em lotes bat incluído com este exemplo permite que você configure o servidor com certificados relevantes para executar o aplicativo hospedado no IIS que exige a segurança baseada em certificado do servidor. Esse arquivo em lotes deve ser modificado para funcionar entre computadores ou para trabalhar em um caso não hospedado.  
  
 O exemplo a seguir fornece uma visão geral das seções diferentes dos arquivos de lote para que eles podem ser modificados para executar a configuração apropriada.  
  
-   Criando o certificado do servidor:  
  
     As seguintes linhas do `Setup.bat` arquivo em lotes criar o certificado do servidor a ser usado. O `%SERVER_NAME%` variável Especifica o nome do servidor. Altere essa variável para especificar seu próprio nome de servidor. O padrão, esse arquivo em lotes é localhost. Se você alterar o `%SERVER_NAME%` variável, você deve percorrer os arquivos Client.cs e Service.cs e substitua todas as instâncias do host local com o nome do servidor que você usa no script bat.  
  
     O certificado é armazenado no repositório My (pessoal) sob o `LocalMachine` local do repositório. O certificado é armazenado no repositório de LocalMachine para os serviços hospedados no IIS. Para serviços de hospedagem interna, você deve modificar o arquivo em lotes para armazenar o certificado de cliente no local de armazenamento CurrentUser, substituindo a cadeia de caracteres LocalMachine por CurrentUser.  
  
    ```  
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
-   Instalando o certificado do servidor no repositório de certificados confiáveis do cliente:  
  
     Armazenam as linhas a seguir na cópia de arquivo de lote o certificado do servidor bat para as pessoas confiáveis do cliente. Esta etapa é necessária porque os certificados gerados pela Makecert.exe não são implicitamente confiáveis pelo sistema do cliente. Se você já tiver um certificado que está enraizado em um certificado de raiz confiável do cliente — por exemplo, um certificado da Microsoft emitido — essa etapa de preenchimento do repositório de certificados de cliente com o certificado do servidor não é necessária.  
  
    ```  
    echo ************  
    echo copying server cert to client's TrustedPeople store  
    echo ************  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
-   Para habilitar o acesso à chave privada de certificado do serviço hospedado no IIS, a conta de usuário sob a qual o processo de hospedados no IIS é executado deve ter permissões apropriadas para a chave privada. Isso é feito por último etapas no script bat.  
  
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
>  O arquivo em lotes bat é projetado para ser executado de um [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] Prompt de comando. Definir a variável de ambiente PATH dentro de [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] Prompt de comando aponta para o diretório que contém os executáveis exigido pelo script bat.  
  
#### <a name="to-set-up-and-build-the-sample"></a>Para configurar e criar o exemplo  
  
1.  Certifique-se de que você executou o [único procedimento de instalação para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Para criar a solução, siga as instruções em [compilar os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
#### <a name="to-run-the-sample-on-the-same-computer"></a>Para executar o exemplo no mesmo computador  
  
1.  Abra um [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] janela de Prompt de comando com privilégios de administrador e execute bat da pasta de instalação do exemplo. Isso instala todos os certificados necessários para executar o exemplo. Certifique-se de que o caminho inclui a pasta onde Makecert.exe está localizado.  
  
> [!NOTE]
>  Certifique-se de remover os certificados executando Cleanup.bat quando terminar com o exemplo. Outros exemplos de segurança usam os mesmos certificados.  
  
1.  Inicie Client.exe do diretório client\bin. Atividade do cliente é exibida no aplicativo de console do cliente.  
  
2.  Se o cliente e o serviço não for capazes de se comunicar, consulte [dicas de solução de problemas](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).  
  
#### <a name="to-run-the-sample-across-computer"></a>Para executar o exemplo em um computador  
  
1.  Crie um diretório no computador de serviço para os binários de serviço.  
  
2.  Copie os arquivos de programa do serviço para o diretório de serviço no computador de serviço. Não se esqueça de copiar CreditCardFile.txt; Caso contrário, o autenticador do cartão de crédito não é possível validar as informações de cartão de crédito enviadas do cliente. Também copie os arquivos. bat e Cleanup.bat para o computador do serviço.  
  
3.  Você deve ter um certificado de servidor com o nome da entidade que contém o nome de domínio totalmente qualificado do computador. Você pode criar um usando o bat se você alterar o `%SERVER_NAME%` variável para o nome totalmente qualificado do computador onde o serviço está hospedado. Observe que o arquivo bat deve ser executado em um prompt de comando do Visual Studio aberto com privilégios de administrador.  
  
4.  Copie o certificado do servidor para o armazenamento CurrentUser TrustedPeople no cliente. Você deve fazer isso apenas se o certificado do servidor não foi emitido por um emissor confiável.  
  
5.  No arquivo EchoServiceHost.cs, altere o valor do nome do assunto do certificado para especificar um nome de computador totalmente qualificado em vez de localhost.  
  
6.  Copie os arquivos de programa do cliente na pasta \client\bin\, sob a pasta de idioma específico, para o computador cliente.  
  
7.  No arquivo Client.cs, altere o valor do endereço do ponto de extremidade para coincidir com o novo endereço do seu serviço.  
  
8.  No arquivo Client.cs altere o nome da entidade do certificado x. 509 do serviço para corresponder ao nome de computador totalmente qualificado do host remoto em vez de localhost.  
  
9. No computador cliente, inicie o Client.exe em uma janela de prompt de comando.  
  
10. Se o cliente e o serviço não for capazes de se comunicar, consulte [dicas de solução de problemas](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).  
  
#### <a name="to-clean-up-after-the-sample"></a>A limpeza após a amostra  
  
1.  Execute Cleanup.bat na pasta exemplos depois de terminar a execução do exemplo.  
  
## <a name="see-also"></a>Consulte também
