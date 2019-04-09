---
title: Interoperabilidade com serviços Web do ASP.NET
ms.date: 03/30/2017
ms.assetid: 622422f8-6651-442f-b8be-e654a4aabcac
ms.openlocfilehash: c6fec1d520cd251473d8840b7b1afe879002a04c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59108570"
---
# <a name="interoperability-with-aspnet-web-services"></a><span data-ttu-id="c7daa-102">Interoperabilidade com serviços Web do ASP.NET</span><span class="sxs-lookup"><span data-stu-id="c7daa-102">Interoperability with ASP.NET Web Services</span></span>
<span data-ttu-id="c7daa-103">Interoperabilidade entre [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] serviços da Web e serviços da Web do Windows Communication Foundation (WCF) podem ser obtidos, garantindo que os serviços implementados usando ambas as tecnologias em conformidade com o WS-I Basic Profile 1.1 especificação.</span><span class="sxs-lookup"><span data-stu-id="c7daa-103">Interoperability between [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Web services and Windows Communication Foundation (WCF) Web services can be achieved by ensuring that services implemented using both technologies conform to the WS-I Basic Profile 1.1 specification.</span></span> [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] <span data-ttu-id="c7daa-104">Serviços Web que estão em conformidade com WS-I Basic Profile 1.1 são interoperáveis com clientes do WCF usando a associação WCF fornecida pelo sistema, <xref:System.ServiceModel.BasicHttpBinding>.</span><span class="sxs-lookup"><span data-stu-id="c7daa-104">Web services that conform to WS-I Basic Profile 1.1 are interoperable with WCF clients by using WCF system-provided binding, <xref:System.ServiceModel.BasicHttpBinding>.</span></span>  
  
 <span data-ttu-id="c7daa-105">Use [!INCLUDE[vstecasplong](../../../../includes/vstecasplong-md.md)] opção de adicionar a <xref:System.Web.Services.WebService> e <xref:System.Web.Services.WebMethodAttribute> atributos para uma interface em vez de uma classe e escrevendo uma classe para implementar a interface, conforme mostrado no código de exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="c7daa-105">Use [!INCLUDE[vstecasplong](../../../../includes/vstecasplong-md.md)] option of adding the <xref:System.Web.Services.WebService> and <xref:System.Web.Services.WebMethodAttribute> attributes to an interface rather than to a class, and writing a class to implement the interface, as shown in the following sample code.</span></span>  
  
```  
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
  
 <span data-ttu-id="c7daa-106">O uso dessa opção é preferível, pois a interface com o <xref:System.Web.Services.WebService> atributo constitui um contrato para as operações executadas pelo serviço que pode ser reutilizado com várias classes que podem implementar o mesmo contrato de maneiras diferentes.</span><span class="sxs-lookup"><span data-stu-id="c7daa-106">Using this option is preferred, because the interface with the <xref:System.Web.Services.WebService> attribute constitutes a contract for the operations performed by the service that can be reused with various classes that might implement that same contract in different ways.</span></span>  
  
 <span data-ttu-id="c7daa-107">Evite usar o <xref:System.Web.Services.Protocols.SoapDocumentServiceAttribute> atributo para que as mensagens roteadas para métodos com base no nome totalmente qualificado do elemento de corpo da mensagem SOAP em vez de `SOAPAction` cabeçalho HTTP.</span><span class="sxs-lookup"><span data-stu-id="c7daa-107">Avoid using the <xref:System.Web.Services.Protocols.SoapDocumentServiceAttribute> attribute to have messages routed to methods based on the fully-qualified name of the body element of the SOAP message rather than the `SOAPAction` HTTP header.</span></span> <span data-ttu-id="c7daa-108">O WCF usa o `SOAPAction` cabeçalho HTTP de roteamento de mensagens.</span><span class="sxs-lookup"><span data-stu-id="c7daa-108">WCF uses the `SOAPAction` HTTP header for routing messages.</span></span>  
  
 <span data-ttu-id="c7daa-109">O XML no qual <xref:System.Xml.Serialization.XmlSerializer> serializa um tipo por padrão é semanticamente idêntico ao XML em que o <xref:System.Runtime.Serialization.DataContractSerializer> serializa um tipo, desde que o namespace para o XML seja explicitamente definido.</span><span class="sxs-lookup"><span data-stu-id="c7daa-109">The XML into which <xref:System.Xml.Serialization.XmlSerializer> serializes a type by default is semantically identical to the XML into which the <xref:System.Runtime.Serialization.DataContractSerializer> serializes a type, provided the namespace for the XML is explicitly defined.</span></span> <span data-ttu-id="c7daa-110">Ao definir um tipo de dados para uso com [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]serviços em antecipação a adoção do WCF Web, faça o seguinte:</span><span class="sxs-lookup"><span data-stu-id="c7daa-110">When defining a data type for use with [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]Web services in anticipation of adopting WCF, do the following:</span></span>  
  
-   <span data-ttu-id="c7daa-111">Defina o tipo usando classes do .NET Framework em vez de esquema XML.</span><span class="sxs-lookup"><span data-stu-id="c7daa-111">Define the type using .NET Framework classes rather than XML Schema.</span></span>  
  
-   <span data-ttu-id="c7daa-112">Adicione somente as <xref:System.SerializableAttribute> e o <xref:System.Xml.Serialization.XmlRootAttribute> à classe, usando o último para definir explicitamente o namespace para o tipo.</span><span class="sxs-lookup"><span data-stu-id="c7daa-112">Add only the <xref:System.SerializableAttribute> and the <xref:System.Xml.Serialization.XmlRootAttribute> to the class, using the latter to explicitly define the namespace for the type.</span></span> <span data-ttu-id="c7daa-113">Não adicione atributos adicionais do <xref:System.Xml.Serialization> namespace para controlar como a classe do .NET Framework deve ser convertido em XML.</span><span class="sxs-lookup"><span data-stu-id="c7daa-113">Do not add additional attributes from the <xref:System.Xml.Serialization> namespace to control how the .NET Framework class is to be translated into XML.</span></span>  
  
-   <span data-ttu-id="c7daa-114">Ao adotar essa abordagem, você deve ser capaz de fazer mais tarde as classes do .NET em contratos de dados com a adição do <xref:System.Runtime.Serialization.DataContractAttribute> e <xref:System.Runtime.Serialization.DataMemberAttribute> sem alterar significativamente o XML no qual as classes são serializadas para transmissão.</span><span class="sxs-lookup"><span data-stu-id="c7daa-114">By adopting this approach, you should be able to later make the .NET classes into data contracts with the addition of the <xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> without significantly altering the XML into which the classes are serialized for transmission.</span></span> <span data-ttu-id="c7daa-115">Os tipos usados em mensagens por [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] serviços Web podem ser processados como contratos de dados por aplicativos do WCF, gerando, entre outros benefícios, melhor desempenho em aplicativos do WCF.</span><span class="sxs-lookup"><span data-stu-id="c7daa-115">The types used in messages by [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Web services can be processed as data contracts by WCF applications, yielding, among other benefits, better performance in WCF applications.</span></span>  
  
 <span data-ttu-id="c7daa-116">Evite usar as opções de autenticação fornecidas pelo Internet Information Services (IIS).</span><span class="sxs-lookup"><span data-stu-id="c7daa-116">Avoid using the authentication options provided by Internet Information Services (IIS).</span></span> <span data-ttu-id="c7daa-117">Clientes do WCF não oferecem suporte a isso.</span><span class="sxs-lookup"><span data-stu-id="c7daa-117">WCF clients do not support them.</span></span> <span data-ttu-id="c7daa-118">Se um serviço deve ser protegido, use as opções fornecidas pelo WCF, porque essas opções são robustas e se baseiam nos protocolos padrão.</span><span class="sxs-lookup"><span data-stu-id="c7daa-118">If a service must be secured, use the options provided by WCF, because these options are robust and are based on standard protocols.</span></span>  
  
## <a name="performance-impact-caused-by-loading-the-servicemodel-httpmodule"></a><span data-ttu-id="c7daa-119">Impacto no desempenho causado por carregar o ServiceModel HttpModule</span><span class="sxs-lookup"><span data-stu-id="c7daa-119">Performance impact caused by loading the ServiceModel HttpModule</span></span>  
 <span data-ttu-id="c7daa-120">No .NET Framework 3.0, o WCF `HttpModule` foi instalado na raiz do arquivo Web. config, de modo que todos os aplicativos ASP.NET foi habilitado do WCF.</span><span class="sxs-lookup"><span data-stu-id="c7daa-120">In the .NET Framework 3.0, the WCF `HttpModule` was installed in the root Web.config file such that every ASP.NET application was WCF enabled.</span></span> <span data-ttu-id="c7daa-121">Isso pode afetar o desempenho, portanto, você pode remover `ServiceModel` para o arquivo Web. config, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="c7daa-121">This might affect performance, so you can remove `ServiceModel` for the Web.config file as shown in the following example.</span></span>  
  
```xml  
<httpModules>  
    <remove name="ServiceModel" />  
<httpModules/>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c7daa-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c7daa-122">See also</span></span>

- [<span data-ttu-id="c7daa-123">Como: configurar um serviço do WCF para interoperar com os clientes de serviço Web do ASP.NET</span><span class="sxs-lookup"><span data-stu-id="c7daa-123">How to: Configure WCF Service to Interoperate with ASP.NET Web Service Clients</span></span>](../../../../docs/framework/wcf/feature-details/config-wcf-service-with-aspnet-web-service.md)
