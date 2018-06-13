---
title: 'Antecipando a adoção do Windows Communication Foundation: facilitando a migração futura'
ms.date: 03/30/2017
ms.assetid: f49664d9-e9e0-425c-a259-93f0a569d01b
ms.openlocfilehash: aeafc164d16d9dc60ad0b3012da292e9b0bb38b3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33490039"
---
# <a name="anticipating-adopting-the-windows-communication-foundation-easing-future-migration"></a><span data-ttu-id="655d2-102">Antecipando a adoção do Windows Communication Foundation: facilitando a migração futura</span><span class="sxs-lookup"><span data-stu-id="655d2-102">Anticipating Adopting the Windows Communication Foundation: Easing Future Migration</span></span>
<span data-ttu-id="655d2-103">Para garantir uma migração futura mais fácil de novos aplicativos ASP.NET para o WCF, siga as recomendações acima, bem como as recomendações a seguir.</span><span class="sxs-lookup"><span data-stu-id="655d2-103">To ensure an easier future migration of new ASP.NET applications to WCF, follow the preceding recommendations as well as the following recommendations.</span></span>  
  
## <a name="protocols"></a><span data-ttu-id="655d2-104">Protocolos</span><span class="sxs-lookup"><span data-stu-id="655d2-104">Protocols</span></span>  
 <span data-ttu-id="655d2-105">Desabilite o suporte para SOAP 1.2 do ASP.NET 2.0:</span><span class="sxs-lookup"><span data-stu-id="655d2-105">Disable ASP.NET 2.0’s support for SOAP 1.2:</span></span>  
  
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
  
 <span data-ttu-id="655d2-106">Isso é recomendável porque o WCF exige mensagens em conformidade com os protocolos diferentes, como SOAP 1.1 e SOAP 1.2, usando diferentes pontos de extremidade.</span><span class="sxs-lookup"><span data-stu-id="655d2-106">Doing so is advisable because WCF requires messages conforming to different protocols, like SOAP 1.1 and SOAP 1.2, to go by using different endpoints.</span></span> <span data-ttu-id="655d2-107">Se uma Web do ASP.NET 2.0 serviço está configurado para dar suporte a SOAP 1.1 e SOAP 1.2, que é a configuração padrão, em seguida, ele não pode ser migrado direta para um único ponto de extremidade do WCF no endereço original que seria certamente ser compatível com todos os Web do ASP.NET clientes existentes do serviço.</span><span class="sxs-lookup"><span data-stu-id="655d2-107">If an ASP.NET 2.0 Web service is configured to support both SOAP 1.1 and SOAP 1.2, which is the default configuration, then it cannot be migrated forward to a single WCF endpoint at the original address that would be certainly be compatible with all of the ASP.NET Web service’s existing clients.</span></span> <span data-ttu-id="655d2-108">Escolher também SOAP 1.2 em vez de 1.1 mais severos restringirá clientele do serviço.</span><span class="sxs-lookup"><span data-stu-id="655d2-108">Also choosing SOAP 1.2 instead of 1.1 will more severely restrict the clientele of the service.</span></span>  
  
## <a name="service-development"></a><span data-ttu-id="655d2-109">Desenvolvimento do serviço</span><span class="sxs-lookup"><span data-stu-id="655d2-109">Service Development</span></span>  
 <span data-ttu-id="655d2-110">WCF permite que você defina os contratos de serviço aplicando o <xref:System.ServiceModel.ServiceContractAttribute> para interfaces ou classes.</span><span class="sxs-lookup"><span data-stu-id="655d2-110">WCF allows you to define service contracts by applying the <xref:System.ServiceModel.ServiceContractAttribute> either to interfaces or to classes.</span></span> <span data-ttu-id="655d2-111">É recomendável aplicar o atributo a uma interface em vez de uma classe, porque fazer isso cria uma definição de um contrato que pode ser implementada diversos por qualquer número de classes.</span><span class="sxs-lookup"><span data-stu-id="655d2-111">It is recommended to apply the attribute to an interface rather than to a class, because doing so creates a definition of a contract that can be variously implemented by any number of classes.</span></span> <span data-ttu-id="655d2-112">ASP.NET 2.0 dá suporte a opção de aplicar o <xref:System.Web.Services.WebService> a interfaces, bem como classes de atributo.</span><span class="sxs-lookup"><span data-stu-id="655d2-112">ASP.NET 2.0 supports the option of applying the <xref:System.Web.Services.WebService> attribute to interfaces as well as classes.</span></span> <span data-ttu-id="655d2-113">No entanto, como já mencionado, há um defeito no ASP.NET 2.0, pelo qual o parâmetro de Namespace do <xref:System.Web.Services.WebService> atributo não tem nenhum efeito quando esse atributo é aplicado a uma interface em vez de uma classe.</span><span class="sxs-lookup"><span data-stu-id="655d2-113">However, as mentioned already, there is a defect in ASP.NET 2.0, by which the Namespace parameter of the <xref:System.Web.Services.WebService> attribute has no effect when that attribute is applied to an interface rather than a class.</span></span> <span data-ttu-id="655d2-114">Como é geralmente é recomendável modificar o espaço para nome de um serviço do valor padrão, http://tempuri.org, usando o parâmetro de Namespace do <xref:System.Web.Services.WebService> atributo, um deve continuar definindo serviços Web ASP.NET, aplicando o <xref:System.ServiceModel.ServiceContractAttribute> atributo para interfaces ou classes.</span><span class="sxs-lookup"><span data-stu-id="655d2-114">Since it is generally advisable to modify the namespace of a service from the default value, http://tempuri.org, using the Namespace parameter of the <xref:System.Web.Services.WebService> attribute, one should continue defining ASP.NET Web Services by applying the <xref:System.ServiceModel.ServiceContractAttribute> attribute either to interfaces or to classes.</span></span>  
  
-   <span data-ttu-id="655d2-115">Ter apenas código possível nos métodos pelos quais as interfaces são definidas.</span><span class="sxs-lookup"><span data-stu-id="655d2-115">Have as little code as possible in the methods by which those interfaces are defined.</span></span> <span data-ttu-id="655d2-116">Tê-los delegar seus trabalhos para outras classes.</span><span class="sxs-lookup"><span data-stu-id="655d2-116">Have them delegate their work to other classes.</span></span> <span data-ttu-id="655d2-117">Novos tipos de serviço do WCF, em seguida, podem também delegar seu trabalho substancial para essas classes.</span><span class="sxs-lookup"><span data-stu-id="655d2-117">New WCF service types could then also delegate their substantive work to those classes.</span></span>  
  
-   <span data-ttu-id="655d2-118">Fornecer nomes explícitos para as operações de um serviço usando o `MessageName` parâmetro o <xref:System.Web.Services.WebMethodAttribute>.</span><span class="sxs-lookup"><span data-stu-id="655d2-118">Provide explicit names for the operations of a service using the `MessageName` parameter of the <xref:System.Web.Services.WebMethodAttribute>.</span></span>  
  
    ```  
    [WebMethod(MessageName="ExplicitName")]  
    string Echo(string input);  
    ```  
  
     <span data-ttu-id="655d2-119">Isso é importante, porque os nomes padrão para operações no ASP.NET são diferentes dos nomes padrão fornecidos pelo WCF.</span><span class="sxs-lookup"><span data-stu-id="655d2-119">Doing so is important, because the default names for operations in ASP.NET are different from the default names supplied by WCF.</span></span> <span data-ttu-id="655d2-120">Fornecendo nomes explícito, você evitar contar com as definições padrão.</span><span class="sxs-lookup"><span data-stu-id="655d2-120">By providing explicit names, you avoid relying on the default ones.</span></span>  
  
-   <span data-ttu-id="655d2-121">Não implemente a operações do serviço Web do ASP.NET com métodos polimórficos, porque o WCF não oferece suporte a operações de implementação com métodos polimórficos.</span><span class="sxs-lookup"><span data-stu-id="655d2-121">Do not implement ASP.NET Web service operations with polymorphic methods, because WCF does not support implementing operations with polymorphic methods.</span></span>  
  
-   <span data-ttu-id="655d2-122">Use o <xref:System.Web.Services.Protocols.SoapDocumentMethodAttribute> para fornecer valores explícitos para os cabeçalhos HTTP SOAPAction pelo qual HTTP as solicitações serão roteadas para métodos.</span><span class="sxs-lookup"><span data-stu-id="655d2-122">Use the <xref:System.Web.Services.Protocols.SoapDocumentMethodAttribute> to provide explicit values for the SOAPAction HTTP headers by which HTTP requests will be routed to methods.</span></span>  
  
    ```  
    [WebMethod]  
    [SoapDocumentMethod(RequestElementName="ExplicitAction")]  
    string Echo(string input);  
    ```  
  
     <span data-ttu-id="655d2-123">Essa abordagem contornar a depender valores de SOAPAction usados pelo ASP.NET e WCF, sendo o mesmo padrão.</span><span class="sxs-lookup"><span data-stu-id="655d2-123">Taking this approach will circumvent having to rely on the default SOAPAction values used by ASP.NET and WCF being the same.</span></span>  
  
-   <span data-ttu-id="655d2-124">Evite usar extensões SOAP.</span><span class="sxs-lookup"><span data-stu-id="655d2-124">Avoid using SOAP extensions.</span></span> <span data-ttu-id="655d2-125">Se as extensões SOAP forem necessárias, determine se a finalidade para a qual eles são considerados é um recurso que já é fornecido pelo WCF.</span><span class="sxs-lookup"><span data-stu-id="655d2-125">If SOAP extensions are required, then determine whether the purpose for which they are being considered is a feature that is already provided by WCF.</span></span> <span data-ttu-id="655d2-126">Se esse for realmente o caso, reconsidere, em seguida, a opção de não adotar WCF imediatamente.</span><span class="sxs-lookup"><span data-stu-id="655d2-126">If that is indeed the case, then reconsider the choice to not adopt WCF right away.</span></span>  
  
## <a name="state-management"></a><span data-ttu-id="655d2-127">Gerenciamento do estado</span><span class="sxs-lookup"><span data-stu-id="655d2-127">State Management</span></span>  
 <span data-ttu-id="655d2-128">Evite ter que manter o estado nos serviços.</span><span class="sxs-lookup"><span data-stu-id="655d2-128">Avoid having to maintain state in services.</span></span> <span data-ttu-id="655d2-129">Manter o estado tende a comprometer a escalabilidade de um aplicativo e os mecanismos de gerenciamento de estado do ASP.NET e WCF são muito diferentes, embora o WCF dá suporte os mecanismos ASP.NET no modo de compatibilidade do ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="655d2-129">Not only does maintaining state tend to compromise the scalability of an application, but the state management mechanisms of ASP.NET and WCF are very different, although WCF does support the ASP.NET mechanisms in ASP.NET compatibility mode.</span></span>  
  
## <a name="exception-handling"></a><span data-ttu-id="655d2-130">Tratamento de Exceção</span><span class="sxs-lookup"><span data-stu-id="655d2-130">Exception Handling</span></span>  
 <span data-ttu-id="655d2-131">Também ao criar as estruturas dos tipos de dados sejam enviadas e recebidas por um serviço, estruturas de design para representar vários tipos de exceções que podem ocorrer dentro de um serviço que podem ser conveniente transmitir a um cliente.</span><span class="sxs-lookup"><span data-stu-id="655d2-131">In designing the structures of the data types to be sent and received by a service, also design structures to represent the various types of exceptions that might occur within a service that one might wish to convey to a client.</span></span>  
  
```  
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
  
 <span data-ttu-id="655d2-132">Permitir que essas classes serializar próprios para XML:</span><span class="sxs-lookup"><span data-stu-id="655d2-132">Give such classes the ability to serialize themselves to XML:</span></span>  
  
```  
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
  
 <span data-ttu-id="655d2-133">As classes, em seguida, podem ser usadas para fornecer os detalhes de geradas explicitamente <xref:System.Web.Services.Protocols.SoapException> instâncias:</span><span class="sxs-lookup"><span data-stu-id="655d2-133">The classes can then be used to provide the details for explicitly thrown <xref:System.Web.Services.Protocols.SoapException> instances:</span></span>  
  
```  
AnctipatedException exception = new AnticipatedException();  
exception.AnticipatedExceptionInformation = "…";  
throw new SoapException(  
     "Fault occurred",  
     SoapException.ClientFaultCode,  
     Context.Request.Url.AbsoluteUri,  
     exception.ToXML());  
```  
  
 <span data-ttu-id="655d2-134">Essas classes de exceção será prontamente reutilizáveis com o WCF<xref:System.ServiceModel.FaultException%601> classe lançar um novo `FaultException<AnticipatedException>(anticipatedException);`</span><span class="sxs-lookup"><span data-stu-id="655d2-134">These exception classes will be readily reusable with the WCF<xref:System.ServiceModel.FaultException%601> class to throw a new `FaultException<AnticipatedException>(anticipatedException);`</span></span>  
  
## <a name="security"></a><span data-ttu-id="655d2-135">Segurança</span><span class="sxs-lookup"><span data-stu-id="655d2-135">Security</span></span>  
 <span data-ttu-id="655d2-136">A seguir estão algumas recomendações de segurança.</span><span class="sxs-lookup"><span data-stu-id="655d2-136">The following are some security recommendations.</span></span>  
  
-   <span data-ttu-id="655d2-137">Evite usar perfis do ASP.NET 2.0, como usá-los restringe o uso do modo de integração de ASP.NET se o serviço foi migrado para o WCF.</span><span class="sxs-lookup"><span data-stu-id="655d2-137">Avoid using ASP.NET 2.0 Profiles, as using them would restrict the use of ASP.NET Integration Mode if the service was migrated to WCF.</span></span>  
  
-   <span data-ttu-id="655d2-138">Evite usar ACLs para controlar o acesso a serviços, como o ASP.NET Web services dá suporte a ACLs usando o Internet Information Services (IIS), o WCF não — porque dependem de serviços Web do ASP.NET no IIS para hospedar e WCF não precisam necessariamente ser hospedado no IIS.</span><span class="sxs-lookup"><span data-stu-id="655d2-138">Avoid using ACLs to control access to services, as ASP.NET Web services supports ACLs using Internet Information Services (IIS), WCF does not—because ASP.NET Web services depend on IIS for hosting, and WCF does not necessarily have to be hosted in IIS.</span></span>  
  
-   <span data-ttu-id="655d2-139">Considere o uso de provedores de função do ASP.NET 2.0 para autorizar o acesso aos recursos de um serviço.</span><span class="sxs-lookup"><span data-stu-id="655d2-139">Do consider using ASP.NET 2.0 Role Providers for authorizing access to the resources of a service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="655d2-140">Consulte também</span><span class="sxs-lookup"><span data-stu-id="655d2-140">See Also</span></span>  
 [<span data-ttu-id="655d2-141">Antecipando a adoção do Windows Communication Foundation: facilitando a futura integração</span><span class="sxs-lookup"><span data-stu-id="655d2-141">Anticipating Adopting the Windows Communication Foundation: Easing Future Integration</span></span>](../../../../docs/framework/wcf/feature-details/anticipating-adopting-the-wcf-easing-future-integration.md)
