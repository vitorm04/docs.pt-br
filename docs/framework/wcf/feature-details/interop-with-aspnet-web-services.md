---
title: Interoperabilidade com serviços Web do ASP.NET
ms.date: 03/30/2017
ms.assetid: 622422f8-6651-442f-b8be-e654a4aabcac
ms.openlocfilehash: 59ee6412cde152588e8007fe530cc8e5708410e5
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991525"
---
# <a name="interoperability-with-aspnet-web-services"></a><span data-ttu-id="5047b-102">Interoperabilidade com serviços Web do ASP.NET</span><span class="sxs-lookup"><span data-stu-id="5047b-102">Interoperability with ASP.NET Web Services</span></span>
<span data-ttu-id="5047b-103">A interoperabilidade entre ASP.NET Web Services e serviços Web Windows Communication Foundation (WCF) pode ser obtida garantindo que os serviços implementados usando ambas as tecnologias estejam em conformidade com a especificação WS-I Basic Profile 1,1.</span><span class="sxs-lookup"><span data-stu-id="5047b-103">Interoperability between ASP.NET Web services and Windows Communication Foundation (WCF) Web services can be achieved by ensuring that services implemented using both technologies conform to the WS-I Basic Profile 1.1 specification.</span></span> <span data-ttu-id="5047b-104">Os serviços Web do ASP.NET que estão em conformidade com o WS-I Basic Profile 1,1 são interoperáveis com clientes WCF usando a <xref:System.ServiceModel.BasicHttpBinding>Associação fornecida pelo sistema do WCF,.</span><span class="sxs-lookup"><span data-stu-id="5047b-104">ASP.NET Web services that conform to WS-I Basic Profile 1.1 are interoperable with WCF clients by using WCF system-provided binding, <xref:System.ServiceModel.BasicHttpBinding>.</span></span>  
  
 <span data-ttu-id="5047b-105">Use a opção ASP.NET 2,0 de adicionar <xref:System.Web.Services.WebService> os <xref:System.Web.Services.WebMethodAttribute> atributos e a uma interface, em vez de uma classe, e escrever uma classe para implementar a interface, conforme mostrado no código de exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="5047b-105">Use ASP.NET 2.0 option of adding the <xref:System.Web.Services.WebService> and <xref:System.Web.Services.WebMethodAttribute> attributes to an interface rather than to a class, and writing a class to implement the interface, as shown in the following sample code.</span></span>  
  
```csharp
[WebService]  
public interface IEcho  
{  
    [WebMethod]  
    string Echo(string input);  
}  
  
public class Service : IEcho  
{  
  
   public string Echo(string input)  
   {  
        return input;  
    }  
}  
```  
  
 <span data-ttu-id="5047b-106">Usar essa opção é preferencial, pois a interface com o <xref:System.Web.Services.WebService> atributo constitui um contrato para as operações executadas pelo serviço que podem ser reutilizadas com várias classes que podem implementar esse mesmo contrato de maneiras diferentes.</span><span class="sxs-lookup"><span data-stu-id="5047b-106">Using this option is preferred, because the interface with the <xref:System.Web.Services.WebService> attribute constitutes a contract for the operations performed by the service that can be reused with various classes that might implement that same contract in different ways.</span></span>  
  
 <span data-ttu-id="5047b-107">Evite usar o <xref:System.Web.Services.Protocols.SoapDocumentServiceAttribute> atributo para que as mensagens sejam roteadas para métodos com base no nome totalmente qualificado do elemento body da mensagem SOAP, e não `SOAPAction` no cabeçalho http.</span><span class="sxs-lookup"><span data-stu-id="5047b-107">Avoid using the <xref:System.Web.Services.Protocols.SoapDocumentServiceAttribute> attribute to have messages routed to methods based on the fully-qualified name of the body element of the SOAP message rather than the `SOAPAction` HTTP header.</span></span> <span data-ttu-id="5047b-108">O WCF usa `SOAPAction` o cabeçalho HTTP para rotear mensagens.</span><span class="sxs-lookup"><span data-stu-id="5047b-108">WCF uses the `SOAPAction` HTTP header for routing messages.</span></span>  
  
 <span data-ttu-id="5047b-109">O XML no qual <xref:System.Xml.Serialization.XmlSerializer> serializa um tipo por padrão é semanticamente idêntico ao XML no qual o <xref:System.Runtime.Serialization.DataContractSerializer> serializa um tipo, desde que o namespace para o XML seja definido explicitamente.</span><span class="sxs-lookup"><span data-stu-id="5047b-109">The XML into which <xref:System.Xml.Serialization.XmlSerializer> serializes a type by default is semantically identical to the XML into which the <xref:System.Runtime.Serialization.DataContractSerializer> serializes a type, provided the namespace for the XML is explicitly defined.</span></span> <span data-ttu-id="5047b-110">Ao definir um tipo de dados para uso com os serviços ASP. NETWeb em antecipação de adoção do WCF, faça o seguinte:</span><span class="sxs-lookup"><span data-stu-id="5047b-110">When defining a data type for use with ASP.NETWeb services in anticipation of adopting WCF, do the following:</span></span>  
  
- <span data-ttu-id="5047b-111">Defina o tipo usando .NET Framework classes em vez de esquema XML.</span><span class="sxs-lookup"><span data-stu-id="5047b-111">Define the type using .NET Framework classes rather than XML Schema.</span></span>  
  
- <span data-ttu-id="5047b-112">Adicione somente o <xref:System.SerializableAttribute> e o <xref:System.Xml.Serialization.XmlRootAttribute> à classe, usando o último para definir explicitamente o namespace para o tipo.</span><span class="sxs-lookup"><span data-stu-id="5047b-112">Add only the <xref:System.SerializableAttribute> and the <xref:System.Xml.Serialization.XmlRootAttribute> to the class, using the latter to explicitly define the namespace for the type.</span></span> <span data-ttu-id="5047b-113">Não adicione atributos adicionais do <xref:System.Xml.Serialization> namespace para controlar como a classe de .NET Framework deve ser convertida em XML.</span><span class="sxs-lookup"><span data-stu-id="5047b-113">Do not add additional attributes from the <xref:System.Xml.Serialization> namespace to control how the .NET Framework class is to be translated into XML.</span></span>  
  
- <span data-ttu-id="5047b-114">Ao adotar essa abordagem, você deve ser capaz de fazer as classes .net em contratos de dados com a adição de <xref:System.Runtime.Serialization.DataContractAttribute> e <xref:System.Runtime.Serialization.DataMemberAttribute> sem alterar significativamente o XML no qual as classes são serializadas para transmissão.</span><span class="sxs-lookup"><span data-stu-id="5047b-114">By adopting this approach, you should be able to later make the .NET classes into data contracts with the addition of the <xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> without significantly altering the XML into which the classes are serialized for transmission.</span></span> <span data-ttu-id="5047b-115">Os tipos usados em mensagens por ASP.NET Web Services podem ser processados como contratos de dados por aplicativos WCF, produzindo, entre outros benefícios, melhor desempenho em aplicativos WCF.</span><span class="sxs-lookup"><span data-stu-id="5047b-115">The types used in messages by ASP.NET Web services can be processed as data contracts by WCF applications, yielding, among other benefits, better performance in WCF applications.</span></span>  
  
 <span data-ttu-id="5047b-116">Evite usar as opções de autenticação fornecidas pelo Serviços de Informações da Internet (IIS).</span><span class="sxs-lookup"><span data-stu-id="5047b-116">Avoid using the authentication options provided by Internet Information Services (IIS).</span></span> <span data-ttu-id="5047b-117">Os clientes WCF não dão suporte a eles.</span><span class="sxs-lookup"><span data-stu-id="5047b-117">WCF clients do not support them.</span></span> <span data-ttu-id="5047b-118">Se um serviço precisar ser protegido, use as opções fornecidas pelo WCF, pois essas opções são robustas e são baseadas em protocolos padrão.</span><span class="sxs-lookup"><span data-stu-id="5047b-118">If a service must be secured, use the options provided by WCF, because these options are robust and are based on standard protocols.</span></span>  
  
## <a name="performance-impact-caused-by-loading-the-servicemodel-httpmodule"></a><span data-ttu-id="5047b-119">Impacto no desempenho causado pelo carregamento do ServiceModel HttpModule</span><span class="sxs-lookup"><span data-stu-id="5047b-119">Performance impact caused by loading the ServiceModel HttpModule</span></span>  
 <span data-ttu-id="5047b-120">No .NET Framework 3,0, o WCF `HttpModule` foi instalado no arquivo Web. config raiz, de modo que todos os aplicativos ASP.net eram habilitados para WCF.</span><span class="sxs-lookup"><span data-stu-id="5047b-120">In the .NET Framework 3.0, the WCF `HttpModule` was installed in the root Web.config file such that every ASP.NET application was WCF enabled.</span></span> <span data-ttu-id="5047b-121">Isso pode afetar o desempenho para que você possa `ServiceModel` remover o arquivo Web. config, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="5047b-121">This might affect performance, so you can remove `ServiceModel` for the Web.config file as shown in the following example.</span></span>  
  
```xml  
<httpModules>  
    <remove name="ServiceModel" />  
<httpModules/>  
```  
  
## <a name="see-also"></a><span data-ttu-id="5047b-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5047b-122">See also</span></span>

- [<span data-ttu-id="5047b-123">Como: Configurar o serviço WCF para interoperar com clientes de serviço Web ASP.NET</span><span class="sxs-lookup"><span data-stu-id="5047b-123">How to: Configure WCF Service to Interoperate with ASP.NET Web Service Clients</span></span>](../../../../docs/framework/wcf/feature-details/config-wcf-service-with-aspnet-web-service.md)
