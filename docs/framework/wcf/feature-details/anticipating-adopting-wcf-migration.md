---
title: 'Antecipando a adoção do Windows Communication Foundation: facilitando a migração futura'
ms.date: 03/30/2017
ms.assetid: f49664d9-e9e0-425c-a259-93f0a569d01b
ms.openlocfilehash: 995bdaaaba96bf8697ea75c1f1a17fa8e51ec2d5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185468"
---
# <a name="anticipating-adopting-the-windows-communication-foundation-easing-future-migration"></a><span data-ttu-id="02a57-102">Antecipando a adoção do Windows Communication Foundation: facilitando a migração futura</span><span class="sxs-lookup"><span data-stu-id="02a57-102">Anticipating Adopting the Windows Communication Foundation: Easing Future Migration</span></span>
<span data-ttu-id="02a57-103">Para garantir uma migração futura mais fácil de novos aplicativos de ASP.NET para o WCF, siga as recomendações anteriores, bem como as seguintes recomendações.</span><span class="sxs-lookup"><span data-stu-id="02a57-103">To ensure an easier future migration of new ASP.NET applications to WCF, follow the preceding recommendations as well as the following recommendations.</span></span>  
  
## <a name="protocols"></a><span data-ttu-id="02a57-104">Protocolos</span><span class="sxs-lookup"><span data-stu-id="02a57-104">Protocols</span></span>  
 <span data-ttu-id="02a57-105">Desativar o suporte do ASP.NET 2.0 para o SOAP 1.2:</span><span class="sxs-lookup"><span data-stu-id="02a57-105">Disable ASP.NET 2.0’s support for SOAP 1.2:</span></span>  
  
```xml  
<configuration>  
     <system.web>  
      <webServices >  
          <protocols>  
           <remove name="HttpSoap12"/>  
          </protocols>
      </webServices>  
     </system.web>
</configuration>  
```  
  
 <span data-ttu-id="02a57-106">Fazer isso é aconselhável porque o WCF requer mensagens em conformidade com diferentes protocolos, como SOAP 1.1 e SOAP 1.2, para usar diferentes pontos finais.</span><span class="sxs-lookup"><span data-stu-id="02a57-106">Doing so is advisable because WCF requires messages conforming to different protocols, like SOAP 1.1 and SOAP 1.2, to go by using different endpoints.</span></span> <span data-ttu-id="02a57-107">Se um serviço web ASP.NET 2.0 for configurado para suportar tanto o SOAP 1.1 quanto o SOAP 1.2, que é a configuração padrão, então ele não poderá ser migrado para um único ponto final wcf no endereço original que certamente seria compatível com todos os ASP.NET Web os clientes existentes do serviço.</span><span class="sxs-lookup"><span data-stu-id="02a57-107">If an ASP.NET 2.0 Web service is configured to support both SOAP 1.1 and SOAP 1.2, which is the default configuration, then it cannot be migrated forward to a single WCF endpoint at the original address that would be certainly be compatible with all of the ASP.NET Web service’s existing clients.</span></span> <span data-ttu-id="02a57-108">Também a escolha do SOAP 1.2 em vez do 1.1 restringirá mais severamente a clientela do serviço.</span><span class="sxs-lookup"><span data-stu-id="02a57-108">Also choosing SOAP 1.2 instead of 1.1 will more severely restrict the clientele of the service.</span></span>  
  
## <a name="service-development"></a><span data-ttu-id="02a57-109">Desenvolvimento do serviço</span><span class="sxs-lookup"><span data-stu-id="02a57-109">Service Development</span></span>  
 <span data-ttu-id="02a57-110">O WCF permite que você defina contratos de serviço aplicando-o <xref:System.ServiceModel.ServiceContractAttribute> em interfaces ou em classes.</span><span class="sxs-lookup"><span data-stu-id="02a57-110">WCF allows you to define service contracts by applying the <xref:System.ServiceModel.ServiceContractAttribute> either to interfaces or to classes.</span></span> <span data-ttu-id="02a57-111">Recomenda-se aplicar o atributo a uma interface e não a uma classe, pois fazê-lo cria uma definição de um contrato que pode ser implementado várias vezes por qualquer número de classes.</span><span class="sxs-lookup"><span data-stu-id="02a57-111">It is recommended to apply the attribute to an interface rather than to a class, because doing so creates a definition of a contract that can be variously implemented by any number of classes.</span></span> <span data-ttu-id="02a57-112">ASP.NET 2.0 suporta a opção <xref:System.Web.Services.WebService> de aplicar o atributo em interfaces e classes.</span><span class="sxs-lookup"><span data-stu-id="02a57-112">ASP.NET 2.0 supports the option of applying the <xref:System.Web.Services.WebService> attribute to interfaces as well as classes.</span></span> <span data-ttu-id="02a57-113">No entanto, como mencionado já, há um defeito no ASP.NET 2.0, pelo qual o parâmetro Namespace do atributo <xref:System.Web.Services.WebService> não tem efeito quando esse atributo é aplicado a uma interface em vez de uma classe.</span><span class="sxs-lookup"><span data-stu-id="02a57-113">However, as mentioned already, there is a defect in ASP.NET 2.0, by which the Namespace parameter of the <xref:System.Web.Services.WebService> attribute has no effect when that attribute is applied to an interface rather than a class.</span></span> <span data-ttu-id="02a57-114">Uma vez que é geralmente aconselhável modificar o namespace `http://tempuri.org`de um serviço a partir <xref:System.Web.Services.WebService> do valor padrão, usando o parâmetro <xref:System.ServiceModel.ServiceContractAttribute> Namespace do atributo, deve-se continuar definindo ASP.NET Web Services aplicando o atributo tanto em interfaces quanto em classes.</span><span class="sxs-lookup"><span data-stu-id="02a57-114">Since it is generally advisable to modify the namespace of a service from the default value, `http://tempuri.org`, using the Namespace parameter of the <xref:System.Web.Services.WebService> attribute, one should continue defining ASP.NET Web Services by applying the <xref:System.ServiceModel.ServiceContractAttribute> attribute either to interfaces or to classes.</span></span>  
  
- <span data-ttu-id="02a57-115">Tenha o menor código possível nos métodos pelos quais essas interfaces são definidas.</span><span class="sxs-lookup"><span data-stu-id="02a57-115">Have as little code as possible in the methods by which those interfaces are defined.</span></span> <span data-ttu-id="02a57-116">Que delegem seu trabalho para outras classes.</span><span class="sxs-lookup"><span data-stu-id="02a57-116">Have them delegate their work to other classes.</span></span> <span data-ttu-id="02a57-117">Novos tipos de serviço sufem, então, também poderiam delegar seu trabalho substantivo para essas classes.</span><span class="sxs-lookup"><span data-stu-id="02a57-117">New WCF service types could then also delegate their substantive work to those classes.</span></span>  
  
- <span data-ttu-id="02a57-118">Fornecer nomes explícitos para as `MessageName` operações de <xref:System.Web.Services.WebMethodAttribute>um serviço usando o parâmetro do .</span><span class="sxs-lookup"><span data-stu-id="02a57-118">Provide explicit names for the operations of a service using the `MessageName` parameter of the <xref:System.Web.Services.WebMethodAttribute>.</span></span>  
  
    ```csharp  
    [WebMethod(MessageName="ExplicitName")]  
    string Echo(string input);  
    ```  
  
     <span data-ttu-id="02a57-119">Fazer isso é importante, pois os nomes padrão para operações em ASP.NET são diferentes dos nomes padrão fornecidos pelo WCF.</span><span class="sxs-lookup"><span data-stu-id="02a57-119">Doing so is important, because the default names for operations in ASP.NET are different from the default names supplied by WCF.</span></span> <span data-ttu-id="02a57-120">Ao fornecer nomes explícitos, você evita confiar nos padrões.</span><span class="sxs-lookup"><span data-stu-id="02a57-120">By providing explicit names, you avoid relying on the default ones.</span></span>  
  
- <span data-ttu-id="02a57-121">Não implemente ASP.NET operações de serviço web com métodos polimórficos, pois o WCF não suporta operações de implementação com métodos polimórficos.</span><span class="sxs-lookup"><span data-stu-id="02a57-121">Do not implement ASP.NET Web service operations with polymorphic methods, because WCF does not support implementing operations with polymorphic methods.</span></span>  
  
- <span data-ttu-id="02a57-122">Use <xref:System.Web.Services.Protocols.SoapDocumentMethodAttribute> o para fornecer valores explícitos para os cabeçalhos SOAPAction HTTP pelos quais as solicitações HTTP serão encaminhadas para métodos.</span><span class="sxs-lookup"><span data-stu-id="02a57-122">Use the <xref:System.Web.Services.Protocols.SoapDocumentMethodAttribute> to provide explicit values for the SOAPAction HTTP headers by which HTTP requests will be routed to methods.</span></span>  
  
    ```csharp  
    [WebMethod]  
    [SoapDocumentMethod(RequestElementName="ExplicitAction")]  
    string Echo(string input);  
    ```  
  
     <span data-ttu-id="02a57-123">Tomar essa abordagem contornará ter que confiar nos valores de SOAPAction padrão usados por ASP.NET e WCF sendo o mesmo.</span><span class="sxs-lookup"><span data-stu-id="02a57-123">Taking this approach will circumvent having to rely on the default SOAPAction values used by ASP.NET and WCF being the same.</span></span>  
  
- <span data-ttu-id="02a57-124">Evite usar extensões SOAP.</span><span class="sxs-lookup"><span data-stu-id="02a57-124">Avoid using SOAP extensions.</span></span> <span data-ttu-id="02a57-125">Se as extensões SOAP forem necessárias, determine se a finalidade para a qual elas estão sendo consideradas é uma característica que já é fornecida pelo WCF.</span><span class="sxs-lookup"><span data-stu-id="02a57-125">If SOAP extensions are required, then determine whether the purpose for which they are being considered is a feature that is already provided by WCF.</span></span> <span data-ttu-id="02a57-126">Se esse for realmente o caso, então reconsidere a escolha de não adotar o WCF imediatamente.</span><span class="sxs-lookup"><span data-stu-id="02a57-126">If that is indeed the case, then reconsider the choice to not adopt WCF right away.</span></span>  
  
## <a name="state-management"></a><span data-ttu-id="02a57-127">Gerenciamento do estado</span><span class="sxs-lookup"><span data-stu-id="02a57-127">State Management</span></span>  
 <span data-ttu-id="02a57-128">Evite ter que manter o estado nos serviços.</span><span class="sxs-lookup"><span data-stu-id="02a57-128">Avoid having to maintain state in services.</span></span> <span data-ttu-id="02a57-129">Não só a manutenção do estado tende a comprometer a escalabilidade de uma aplicação, mas os mecanismos de gestão estatal de ASP.NET e WCF são muito diferentes, embora o WCF apoie os mecanismos ASP.NET no modo de compatibilidade ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="02a57-129">Not only does maintaining state tend to compromise the scalability of an application, but the state management mechanisms of ASP.NET and WCF are very different, although WCF does support the ASP.NET mechanisms in ASP.NET compatibility mode.</span></span>  
  
## <a name="exception-handling"></a><span data-ttu-id="02a57-130">Tratamento de exceção</span><span class="sxs-lookup"><span data-stu-id="02a57-130">Exception Handling</span></span>  
 <span data-ttu-id="02a57-131">Ao projetar as estruturas dos tipos de dados a serem enviados e recebidos por um serviço, também projete estruturas para representar os vários tipos de exceções que podem ocorrer dentro de um serviço que se pode desejar transmitir a um cliente.</span><span class="sxs-lookup"><span data-stu-id="02a57-131">In designing the structures of the data types to be sent and received by a service, also design structures to represent the various types of exceptions that might occur within a service that one might wish to convey to a client.</span></span>  
  
```csharp  
[Serializable]  
[XmlRoot(Namespace="ExplicitNamespace", IsNullable=true)]  
public partial class AnticipatedException
{
    private string anticipatedExceptionInformationField;  

    public string AnticipatedExceptionInformation
    {  
        get {
            return this.anticipatedExceptionInformationField;  
        }  
        set {  
            this.anticipatedExceptionInformationField = value;  
        }  
    }  
}  
```  
  
 <span data-ttu-id="02a57-132">Dê a essas classes a capacidade de serializar-se ao XML:</span><span class="sxs-lookup"><span data-stu-id="02a57-132">Give such classes the ability to serialize themselves to XML:</span></span>  
  
```csharp  
public XmlNode ToXML()  
{  
     XmlSerializer serializer = new XmlSerializer(  
      typeof(AnticipatedException));  
     MemoryStream memoryStream = new MemoryStream();  
     XmlTextWriter writer = new XmlTextWriter(  
     memoryStream, UnicodeEncoding.UTF8);  
     serializer.Serialize(writer, this);  
     XmlDocument document = new XmlDocument();  
     document.LoadXml(new string(  
     UnicodeEncoding.UTF8.GetChars(  
     memoryStream.GetBuffer())).Trim());  
    return document.DocumentElement;  
}  
```  
  
 <span data-ttu-id="02a57-133">As classes podem então ser usadas para <xref:System.Web.Services.Protocols.SoapException> fornecer os detalhes para instâncias explicitamente jogadas:</span><span class="sxs-lookup"><span data-stu-id="02a57-133">The classes can then be used to provide the details for explicitly thrown <xref:System.Web.Services.Protocols.SoapException> instances:</span></span>  
  
```csharp  
AnticipatedException exception = new AnticipatedException();  
exception.AnticipatedExceptionInformation = "…";  
throw new SoapException(  
     "Fault occurred",  
     SoapException.ClientFaultCode,  
     Context.Request.Url.AbsoluteUri,  
     exception.ToXML());  
```  
  
 <span data-ttu-id="02a57-134">Essas classes de exceção serão facilmente utilizáveis com a classe WCF <xref:System.ServiceModel.FaultException%601> para lançar um novo`FaultException<AnticipatedException>(anticipatedException);`</span><span class="sxs-lookup"><span data-stu-id="02a57-134">These exception classes will be readily reusable with the WCF <xref:System.ServiceModel.FaultException%601> class to throw a new `FaultException<AnticipatedException>(anticipatedException);`</span></span>  
  
## <a name="security"></a><span data-ttu-id="02a57-135">Segurança</span><span class="sxs-lookup"><span data-stu-id="02a57-135">Security</span></span>  
 <span data-ttu-id="02a57-136">A seguir, algumas recomendações de segurança.</span><span class="sxs-lookup"><span data-stu-id="02a57-136">The following are some security recommendations.</span></span>  
  
- <span data-ttu-id="02a57-137">Evite usar ASP.NET perfis 2.0, pois usá-los restringiria o uso de ASP.NET Modo de Integração se o serviço fosse migrado para o WCF.</span><span class="sxs-lookup"><span data-stu-id="02a57-137">Avoid using ASP.NET 2.0 Profiles, as using them would restrict the use of ASP.NET Integration Mode if the service was migrated to WCF.</span></span>  
  
- <span data-ttu-id="02a57-138">Evite usar ACLs para controlar o acesso aos serviços, já que ASP.NET serviços da Web suportam ACLs usando Serviços de Informação da Internet (IIS), o WCF não — porque ASP.NET serviços da Web dependem do IIS para hospedagem, e o WCF não precisa necessariamente ser hospedado no IIS.</span><span class="sxs-lookup"><span data-stu-id="02a57-138">Avoid using ACLs to control access to services, as ASP.NET Web services supports ACLs using Internet Information Services (IIS), WCF does not—because ASP.NET Web services depend on IIS for hosting, and WCF does not necessarily have to be hosted in IIS.</span></span>  
  
- <span data-ttu-id="02a57-139">Considere usar ASP.NET Provedores de Papel 2.0 para autorizar o acesso aos recursos de um serviço.</span><span class="sxs-lookup"><span data-stu-id="02a57-139">Do consider using ASP.NET 2.0 Role Providers for authorizing access to the resources of a service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02a57-140">Confira também</span><span class="sxs-lookup"><span data-stu-id="02a57-140">See also</span></span>

- [<span data-ttu-id="02a57-141">Antecipando a adoção do Windows Communication Foundation: facilitando a futura integração</span><span class="sxs-lookup"><span data-stu-id="02a57-141">Anticipating Adopting the Windows Communication Foundation: Easing Future Integration</span></span>](../../../../docs/framework/wcf/feature-details/anticipating-adopting-the-wcf-easing-future-integration.md)
