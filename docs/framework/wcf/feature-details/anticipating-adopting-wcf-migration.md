---
title: 'Antecipar a adoção do Windows Communication Foundation: facilitar a migração futura'
ms.date: 03/30/2017
ms.assetid: f49664d9-e9e0-425c-a259-93f0a569d01b
ms.openlocfilehash: 4492626c2cb0958f8aa79fa2b511d9aa9e90b16a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61769506"
---
# <a name="anticipating-adopting-the-windows-communication-foundation-easing-future-migration"></a><span data-ttu-id="a1e6e-102">Antecipar a adoção do Windows Communication Foundation: facilitar a migração futura</span><span class="sxs-lookup"><span data-stu-id="a1e6e-102">Anticipating Adopting the Windows Communication Foundation: Easing Future Migration</span></span>
<span data-ttu-id="a1e6e-103">Para garantir uma migração mais fácil futuras de novos aplicativos ASP.NET ao WCF, siga as recomendações acima, bem como as recomendações a seguir.</span><span class="sxs-lookup"><span data-stu-id="a1e6e-103">To ensure an easier future migration of new ASP.NET applications to WCF, follow the preceding recommendations as well as the following recommendations.</span></span>  
  
## <a name="protocols"></a><span data-ttu-id="a1e6e-104">Protocolos</span><span class="sxs-lookup"><span data-stu-id="a1e6e-104">Protocols</span></span>  
 <span data-ttu-id="a1e6e-105">Desabilite o suporte do ASP.NET 2.0 para SOAP 1.2:</span><span class="sxs-lookup"><span data-stu-id="a1e6e-105">Disable ASP.NET 2.0’s support for SOAP 1.2:</span></span>  
  
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
  
 <span data-ttu-id="a1e6e-106">É aconselhável fazer isso, porque o WCF exige que as mensagens em conformidade com protocolos diferentes, como SOAP 1.1 e SOAP 1.2, acesse usando pontos de extremidade diferentes.</span><span class="sxs-lookup"><span data-stu-id="a1e6e-106">Doing so is advisable because WCF requires messages conforming to different protocols, like SOAP 1.1 and SOAP 1.2, to go by using different endpoints.</span></span> <span data-ttu-id="a1e6e-107">Se um ASP.NET 2.0 da Web serviço está configurado para dar suporte a SOAP 1.1 e SOAP 1.2, que é a configuração padrão, em seguida, ele não pode ser migrado direta para um único ponto de extremidade do WCF no endereço original que seria certamente seja compatível com todos os Web do ASP.NET clientes existentes do serviço.</span><span class="sxs-lookup"><span data-stu-id="a1e6e-107">If an ASP.NET 2.0 Web service is configured to support both SOAP 1.1 and SOAP 1.2, which is the default configuration, then it cannot be migrated forward to a single WCF endpoint at the original address that would be certainly be compatible with all of the ASP.NET Web service’s existing clients.</span></span> <span data-ttu-id="a1e6e-108">Também escolher SOAP 1.2 em vez de 1.1 mais seriamente restringirá o clientele do serviço.</span><span class="sxs-lookup"><span data-stu-id="a1e6e-108">Also choosing SOAP 1.2 instead of 1.1 will more severely restrict the clientele of the service.</span></span>  
  
## <a name="service-development"></a><span data-ttu-id="a1e6e-109">Desenvolvimento do serviço</span><span class="sxs-lookup"><span data-stu-id="a1e6e-109">Service Development</span></span>  
 <span data-ttu-id="a1e6e-110">O WCF permite que você definir contratos de serviço por meio da aplicação de <xref:System.ServiceModel.ServiceContractAttribute> interfaces ou classes.</span><span class="sxs-lookup"><span data-stu-id="a1e6e-110">WCF allows you to define service contracts by applying the <xref:System.ServiceModel.ServiceContractAttribute> either to interfaces or to classes.</span></span> <span data-ttu-id="a1e6e-111">É recomendável aplicar o atributo a uma interface em vez de uma classe, porque fazer isso cria uma definição de um contrato que pode ser chamado implementada por qualquer número de classes.</span><span class="sxs-lookup"><span data-stu-id="a1e6e-111">It is recommended to apply the attribute to an interface rather than to a class, because doing so creates a definition of a contract that can be variously implemented by any number of classes.</span></span> <span data-ttu-id="a1e6e-112">O ASP.NET 2.0 oferece suporte a opção de aplicar o <xref:System.Web.Services.WebService> para interfaces, bem como classes de atributo.</span><span class="sxs-lookup"><span data-stu-id="a1e6e-112">ASP.NET 2.0 supports the option of applying the <xref:System.Web.Services.WebService> attribute to interfaces as well as classes.</span></span> <span data-ttu-id="a1e6e-113">No entanto, como já mencionado, há um defeito no ASP.NET 2.0, pelo qual o parâmetro de Namespace do <xref:System.Web.Services.WebService> atributo não tem nenhum efeito quando esse atributo é aplicado a uma interface em vez de uma classe.</span><span class="sxs-lookup"><span data-stu-id="a1e6e-113">However, as mentioned already, there is a defect in ASP.NET 2.0, by which the Namespace parameter of the <xref:System.Web.Services.WebService> attribute has no effect when that attribute is applied to an interface rather than a class.</span></span> <span data-ttu-id="a1e6e-114">Já que geralmente é aconselhável para modificar o namespace do valor padrão, um serviço `http://tempuri.org`, usando o parâmetro de Namespace do <xref:System.Web.Services.WebService> atributo, um deve continuar definindo serviços Web do ASP.NET por meio da aplicação a <xref:System.ServiceModel.ServiceContractAttribute> atributo para interfaces ou classes.</span><span class="sxs-lookup"><span data-stu-id="a1e6e-114">Since it is generally advisable to modify the namespace of a service from the default value, `http://tempuri.org`, using the Namespace parameter of the <xref:System.Web.Services.WebService> attribute, one should continue defining ASP.NET Web Services by applying the <xref:System.ServiceModel.ServiceContractAttribute> attribute either to interfaces or to classes.</span></span>  
  
- <span data-ttu-id="a1e6e-115">Ter tão pouco de código possível nos métodos pelos quais essas interfaces são definidas.</span><span class="sxs-lookup"><span data-stu-id="a1e6e-115">Have as little code as possible in the methods by which those interfaces are defined.</span></span> <span data-ttu-id="a1e6e-116">Peça para delegar suas tarefas a outras classes.</span><span class="sxs-lookup"><span data-stu-id="a1e6e-116">Have them delegate their work to other classes.</span></span> <span data-ttu-id="a1e6e-117">Novos tipos de serviço do WCF, em seguida, também podem delegar seu trabalho substancial para essas classes.</span><span class="sxs-lookup"><span data-stu-id="a1e6e-117">New WCF service types could then also delegate their substantive work to those classes.</span></span>  
  
- <span data-ttu-id="a1e6e-118">Fornecer nomes explícitos para as operações de um serviço usando o `MessageName` parâmetro do <xref:System.Web.Services.WebMethodAttribute>.</span><span class="sxs-lookup"><span data-stu-id="a1e6e-118">Provide explicit names for the operations of a service using the `MessageName` parameter of the <xref:System.Web.Services.WebMethodAttribute>.</span></span>  
  
    ```csharp  
    [WebMethod(MessageName="ExplicitName")]  
    string Echo(string input);  
    ```  
  
     <span data-ttu-id="a1e6e-119">Isso é importante, porque os nomes padrão para operações no ASP.NET são diferentes dos nomes padrão fornecidos pelo WCF.</span><span class="sxs-lookup"><span data-stu-id="a1e6e-119">Doing so is important, because the default names for operations in ASP.NET are different from the default names supplied by WCF.</span></span> <span data-ttu-id="a1e6e-120">Fornecendo nomes explícitos, você evite contar com os valores padrão.</span><span class="sxs-lookup"><span data-stu-id="a1e6e-120">By providing explicit names, you avoid relying on the default ones.</span></span>  
  
- <span data-ttu-id="a1e6e-121">Não implemente operações de serviço Web do ASP.NET com métodos polimórficos, porque o WCF não oferece suporte a operações de implementação com métodos polimórficos.</span><span class="sxs-lookup"><span data-stu-id="a1e6e-121">Do not implement ASP.NET Web service operations with polymorphic methods, because WCF does not support implementing operations with polymorphic methods.</span></span>  
  
- <span data-ttu-id="a1e6e-122">Use o <xref:System.Web.Services.Protocols.SoapDocumentMethodAttribute> para fornecer valores explícitos para os cabeçalhos HTTP SOAPAction pelo qual HTTP solicitações serão roteadas para métodos.</span><span class="sxs-lookup"><span data-stu-id="a1e6e-122">Use the <xref:System.Web.Services.Protocols.SoapDocumentMethodAttribute> to provide explicit values for the SOAPAction HTTP headers by which HTTP requests will be routed to methods.</span></span>  
  
    ```csharp  
    [WebMethod]  
    [SoapDocumentMethod(RequestElementName="ExplicitAction")]  
    string Echo(string input);  
    ```  
  
     <span data-ttu-id="a1e6e-123">Essa abordagem contornarão precisar contar valores SOAPAction usados por ASP.NET e WCF que está sendo o mesmo padrão.</span><span class="sxs-lookup"><span data-stu-id="a1e6e-123">Taking this approach will circumvent having to rely on the default SOAPAction values used by ASP.NET and WCF being the same.</span></span>  
  
- <span data-ttu-id="a1e6e-124">Evite usar extensões SOAP.</span><span class="sxs-lookup"><span data-stu-id="a1e6e-124">Avoid using SOAP extensions.</span></span> <span data-ttu-id="a1e6e-125">Se as extensões SOAP são necessárias, determine se a finalidade para a qual eles são considerados é um recurso que já é fornecido pelo WCF.</span><span class="sxs-lookup"><span data-stu-id="a1e6e-125">If SOAP extensions are required, then determine whether the purpose for which they are being considered is a feature that is already provided by WCF.</span></span> <span data-ttu-id="a1e6e-126">Se esse for realmente o caso, em seguida, Reconsidere a opção de não adotar imediatamente o WCF.</span><span class="sxs-lookup"><span data-stu-id="a1e6e-126">If that is indeed the case, then reconsider the choice to not adopt WCF right away.</span></span>  
  
## <a name="state-management"></a><span data-ttu-id="a1e6e-127">Gerenciamento do estado</span><span class="sxs-lookup"><span data-stu-id="a1e6e-127">State Management</span></span>  
 <span data-ttu-id="a1e6e-128">Evite ter que manter o estado nos serviços.</span><span class="sxs-lookup"><span data-stu-id="a1e6e-128">Avoid having to maintain state in services.</span></span> <span data-ttu-id="a1e6e-129">Não só manter o estado tende a comprometer a escalabilidade de um aplicativo, mas os mecanismos de gerenciamento de estado do ASP.NET e WCF são muito diferentes, embora o WCF oferece suporte os mecanismos ASP.NET no modo de compatibilidade do ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="a1e6e-129">Not only does maintaining state tend to compromise the scalability of an application, but the state management mechanisms of ASP.NET and WCF are very different, although WCF does support the ASP.NET mechanisms in ASP.NET compatibility mode.</span></span>  
  
## <a name="exception-handling"></a><span data-ttu-id="a1e6e-130">Tratamento de Exceção</span><span class="sxs-lookup"><span data-stu-id="a1e6e-130">Exception Handling</span></span>  
 <span data-ttu-id="a1e6e-131">Ao criar as estruturas dos tipos de dados a serem enviadas e recebidas por um serviço, também estruturas de design para representar os vários tipos de exceções que podem ocorrer dentro de um serviço que um podem desejar transmitir para um cliente.</span><span class="sxs-lookup"><span data-stu-id="a1e6e-131">In designing the structures of the data types to be sent and received by a service, also design structures to represent the various types of exceptions that might occur within a service that one might wish to convey to a client.</span></span>  
  
```csharp  
[Serializable]  
[XmlRoot(  
     Namespace="ExplicitNamespace", IsNullable=true)]  
    public partial class AnticipatedException {  
  
     private string anticipatedExceptionInformationField;  
  
     public string AnticipatedExceptionInformation {  
      get {  
          return this.anticipatedExceptionInformationField;  
          }  
      set {  
          this.anticipatedExceptionInformationField = value;  
          }  
     }  
}  
```  
  
 <span data-ttu-id="a1e6e-132">Permitem que essas classes se serializam para XML:</span><span class="sxs-lookup"><span data-stu-id="a1e6e-132">Give such classes the ability to serialize themselves to XML:</span></span>  
  
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
  
 <span data-ttu-id="a1e6e-133">As classes, em seguida, podem ser usadas para fornecer os detalhes para geradas explicitamente <xref:System.Web.Services.Protocols.SoapException> instâncias:</span><span class="sxs-lookup"><span data-stu-id="a1e6e-133">The classes can then be used to provide the details for explicitly thrown <xref:System.Web.Services.Protocols.SoapException> instances:</span></span>  
  
```csharp  
AnctipatedException exception = new AnticipatedException();  
exception.AnticipatedExceptionInformation = "…";  
throw new SoapException(  
     "Fault occurred",  
     SoapException.ClientFaultCode,  
     Context.Request.Url.AbsoluteUri,  
     exception.ToXML());  
```  
  
 <span data-ttu-id="a1e6e-134">Essas classes de exceção serão prontamente reutilizáveis com o WCF <xref:System.ServiceModel.FaultException%601> classe lançar um novo `FaultException<AnticipatedException>(anticipatedException);`</span><span class="sxs-lookup"><span data-stu-id="a1e6e-134">These exception classes will be readily reusable with the WCF <xref:System.ServiceModel.FaultException%601> class to throw a new `FaultException<AnticipatedException>(anticipatedException);`</span></span>  
  
## <a name="security"></a><span data-ttu-id="a1e6e-135">Segurança</span><span class="sxs-lookup"><span data-stu-id="a1e6e-135">Security</span></span>  
 <span data-ttu-id="a1e6e-136">A seguir estão algumas recomendações de segurança.</span><span class="sxs-lookup"><span data-stu-id="a1e6e-136">The following are some security recommendations.</span></span>  
  
- <span data-ttu-id="a1e6e-137">Evite usar perfis do ASP.NET 2.0, como usá-los restringiriam o uso do modo de integração do ASP.NET se o serviço foi migrado para o WCF.</span><span class="sxs-lookup"><span data-stu-id="a1e6e-137">Avoid using ASP.NET 2.0 Profiles, as using them would restrict the use of ASP.NET Integration Mode if the service was migrated to WCF.</span></span>  
  
- <span data-ttu-id="a1e6e-138">Evite usar ACLs para controlar o acesso a serviços, como ASP.NET Web services dá suporte a ACLs usando os serviços de informações da Internet (IIS), o WCF não — porque dependem de serviços Web do ASP.NET no IIS para hospedar e WCF não precisa necessariamente ser hospedado no IIS.</span><span class="sxs-lookup"><span data-stu-id="a1e6e-138">Avoid using ACLs to control access to services, as ASP.NET Web services supports ACLs using Internet Information Services (IIS), WCF does not—because ASP.NET Web services depend on IIS for hosting, and WCF does not necessarily have to be hosted in IIS.</span></span>  
  
- <span data-ttu-id="a1e6e-139">Considere o uso de provedores de função do ASP.NET 2.0 para autorizar o acesso aos recursos de um serviço.</span><span class="sxs-lookup"><span data-stu-id="a1e6e-139">Do consider using ASP.NET 2.0 Role Providers for authorizing access to the resources of a service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1e6e-140">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a1e6e-140">See also</span></span>

- [<span data-ttu-id="a1e6e-141">Antecipando a adoção do Windows Communication Foundation: Facilitando a futura integração</span><span class="sxs-lookup"><span data-stu-id="a1e6e-141">Anticipating Adopting the Windows Communication Foundation: Easing Future Integration</span></span>](../../../../docs/framework/wcf/feature-details/anticipating-adopting-the-wcf-easing-future-integration.md)
