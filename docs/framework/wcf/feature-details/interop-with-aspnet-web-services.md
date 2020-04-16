---
title: Interoperabilidade com serviços Web do ASP.NET
ms.date: 03/30/2017
ms.assetid: 622422f8-6651-442f-b8be-e654a4aabcac
ms.openlocfilehash: 41810d8044e4b7ff3193950a914edbf1e61cffb1
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81464085"
---
# <a name="interoperability-with-aspnet-web-services"></a><span data-ttu-id="b63cc-102">Interoperabilidade com serviços Web do ASP.NET</span><span class="sxs-lookup"><span data-stu-id="b63cc-102">Interoperability with ASP.NET Web Services</span></span>
<span data-ttu-id="b63cc-103">A interoperabilidade entre ASP.NET serviços web e serviços Web da Windows Communication Foundation (WCF) pode ser alcançada garantindo que os serviços implementados usando ambas as tecnologias estejam em conformidade com a especificação ws-i perfil básico 1.1.</span><span class="sxs-lookup"><span data-stu-id="b63cc-103">Interoperability between ASP.NET Web services and Windows Communication Foundation (WCF) Web services can be achieved by ensuring that services implemented using both technologies conform to the WS-I Basic Profile 1.1 specification.</span></span> <span data-ttu-id="b63cc-104">ASP.NET serviços web que estejam em conformidade com o Perfil Básico WS-I 1.1 são <xref:System.ServiceModel.BasicHttpBinding>interoperáveis com os clientes WCF usando a vinculação fornecida pelo sistema WCF, .</span><span class="sxs-lookup"><span data-stu-id="b63cc-104">ASP.NET Web services that conform to WS-I Basic Profile 1.1 are interoperable with WCF clients by using WCF system-provided binding, <xref:System.ServiceModel.BasicHttpBinding>.</span></span>  
  
 <span data-ttu-id="b63cc-105">Use ASP.NET opção 2.0 <xref:System.Web.Services.WebService> <xref:System.Web.Services.WebMethodAttribute> de adicionar e atributos a uma interface em vez de uma classe, e escrever uma classe para implementar a interface, como mostrado no código de amostra a seguir.</span><span class="sxs-lookup"><span data-stu-id="b63cc-105">Use ASP.NET 2.0 option of adding the <xref:System.Web.Services.WebService> and <xref:System.Web.Services.WebMethodAttribute> attributes to an interface rather than to a class, and writing a class to implement the interface, as shown in the following sample code.</span></span>  
  
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
  
 <span data-ttu-id="b63cc-106">O uso dessa opção é preferível, pois a interface com o atributo <xref:System.Web.Services.WebService> constitui um contrato para as operações realizadas pelo serviço que pode ser reutilizado com várias classes que possam implementar esse mesmo contrato de diferentes formas.</span><span class="sxs-lookup"><span data-stu-id="b63cc-106">Using this option is preferred, because the interface with the <xref:System.Web.Services.WebService> attribute constitutes a contract for the operations performed by the service that can be reused with various classes that might implement that same contract in different ways.</span></span>  
  
 <span data-ttu-id="b63cc-107">Evite usar <xref:System.Web.Services.Protocols.SoapDocumentServiceAttribute> o atributo para ter mensagens roteadas para métodos com base no `SOAPAction` nome totalmente qualificado do elemento corpo da mensagem SOAP em vez do cabeçalho HTTP.</span><span class="sxs-lookup"><span data-stu-id="b63cc-107">Avoid using the <xref:System.Web.Services.Protocols.SoapDocumentServiceAttribute> attribute to have messages routed to methods based on the fully-qualified name of the body element of the SOAP message rather than the `SOAPAction` HTTP header.</span></span> <span data-ttu-id="b63cc-108">O WCF `SOAPAction` usa o cabeçalho HTTP para direcionar mensagens.</span><span class="sxs-lookup"><span data-stu-id="b63cc-108">WCF uses the `SOAPAction` HTTP header for routing messages.</span></span>  
  
 <span data-ttu-id="b63cc-109">O XML <xref:System.Xml.Serialization.XmlSerializer> no qual serializa um tipo por padrão é semanticamente <xref:System.Runtime.Serialization.DataContractSerializer> idêntico ao XML no qual o serializa um tipo, desde que o namespace para o XML seja explicitamente definido.</span><span class="sxs-lookup"><span data-stu-id="b63cc-109">The XML into which <xref:System.Xml.Serialization.XmlSerializer> serializes a type by default is semantically identical to the XML into which the <xref:System.Runtime.Serialization.DataContractSerializer> serializes a type, provided the namespace for the XML is explicitly defined.</span></span> <span data-ttu-id="b63cc-110">Ao definir um tipo de dados para uso com os serviços ASP.NETWeb na expectativa de adotar o WCF, faça o seguinte:</span><span class="sxs-lookup"><span data-stu-id="b63cc-110">When defining a data type for use with ASP.NETWeb services in anticipation of adopting WCF, do the following:</span></span>  
  
- <span data-ttu-id="b63cc-111">Defina o tipo usando classes .NET Framework em vez de XML Schema.</span><span class="sxs-lookup"><span data-stu-id="b63cc-111">Define the type using .NET Framework classes rather than XML Schema.</span></span>  
  
- <span data-ttu-id="b63cc-112">Adicione apenas <xref:System.SerializableAttribute> o <xref:System.Xml.Serialization.XmlRootAttribute> e a classe, usando este último para definir explicitamente o namespace para o tipo.</span><span class="sxs-lookup"><span data-stu-id="b63cc-112">Add only the <xref:System.SerializableAttribute> and the <xref:System.Xml.Serialization.XmlRootAttribute> to the class, using the latter to explicitly define the namespace for the type.</span></span> <span data-ttu-id="b63cc-113">Não adicione atributos <xref:System.Xml.Serialization> adicionais do namespace para controlar como a classe .NET Framework deve ser traduzida em XML.</span><span class="sxs-lookup"><span data-stu-id="b63cc-113">Do not add additional attributes from the <xref:System.Xml.Serialization> namespace to control how the .NET Framework class is to be translated into XML.</span></span>  
  
- <span data-ttu-id="b63cc-114">Ao adotar essa abordagem, você deve ser capaz de posteriormente transformar <xref:System.Runtime.Serialization.DataContractAttribute> as <xref:System.Runtime.Serialization.DataMemberAttribute> classes .NET em contratos de dados com a adição do e sem alterar significativamente o XML no qual as classes são serializadas para transmissão.</span><span class="sxs-lookup"><span data-stu-id="b63cc-114">By adopting this approach, you should be able to later make the .NET classes into data contracts with the addition of the <xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> without significantly altering the XML into which the classes are serialized for transmission.</span></span> <span data-ttu-id="b63cc-115">Os tipos usados em mensagens por ASP.NET serviços Web podem ser processados como contratos de dados por aplicativos WCF, gerando, entre outros benefícios, melhor desempenho em aplicações WCF.</span><span class="sxs-lookup"><span data-stu-id="b63cc-115">The types used in messages by ASP.NET Web services can be processed as data contracts by WCF applications, yielding, among other benefits, better performance in WCF applications.</span></span>  
  
 <span data-ttu-id="b63cc-116">Evite usar as opções de autenticação fornecidas pelos Serviços de Informação da Internet (IIS).</span><span class="sxs-lookup"><span data-stu-id="b63cc-116">Avoid using the authentication options provided by Internet Information Services (IIS).</span></span> <span data-ttu-id="b63cc-117">Os clientes WCF não os suportam.</span><span class="sxs-lookup"><span data-stu-id="b63cc-117">WCF clients do not support them.</span></span> <span data-ttu-id="b63cc-118">Se um serviço deve ser seguro, use as opções fornecidas pelo WCF, pois essas opções são robustas e são baseadas em protocolos padrão.</span><span class="sxs-lookup"><span data-stu-id="b63cc-118">If a service must be secured, use the options provided by WCF, because these options are robust and are based on standard protocols.</span></span>  
  
## <a name="performance-impact-caused-by-loading-the-servicemodel-httpmodule"></a><span data-ttu-id="b63cc-119">Impacto de desempenho causado pelo carregamento do ServiceModel HttpModule</span><span class="sxs-lookup"><span data-stu-id="b63cc-119">Performance impact caused by loading the ServiceModel HttpModule</span></span>  
 <span data-ttu-id="b63cc-120">No .NET Framework 3.0, `HttpModule` o WCF foi instalado no arquivo web.config raiz, de tal forma que cada ASP.NET aplicativo estava habilitado para WCF.</span><span class="sxs-lookup"><span data-stu-id="b63cc-120">In the .NET Framework 3.0, the WCF `HttpModule` was installed in the root Web.config file such that every ASP.NET application was WCF enabled.</span></span> <span data-ttu-id="b63cc-121">Isso pode afetar o desempenho, `ServiceModel` para que você possa remover para o arquivo Web.config como mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="b63cc-121">This might affect performance, so you can remove `ServiceModel` for the Web.config file as shown in the following example.</span></span>  
  
```xml  
<httpModules>  
    <remove name="ServiceModel" />  
</httpModules>
```  
  
## <a name="see-also"></a><span data-ttu-id="b63cc-122">Confira também</span><span class="sxs-lookup"><span data-stu-id="b63cc-122">See also</span></span>

- [<span data-ttu-id="b63cc-123">Como configurar um serviço do WCF para interoperar com os clientes de serviço Web do ASP.NET</span><span class="sxs-lookup"><span data-stu-id="b63cc-123">How to: Configure WCF Service to Interoperate with ASP.NET Web Service Clients</span></span>](../../../../docs/framework/wcf/feature-details/config-wcf-service-with-aspnet-web-service.md)
