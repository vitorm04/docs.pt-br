---
title: 'Antecipando a adoção do Windows Communication Foundation: facilitando a futura integração'
ms.date: 03/30/2017
ms.assetid: 3028bba8-6355-4ee0-9ecd-c56e614cb474
ms.openlocfilehash: 6392194b3124c999031123225dcc28c8de6171e9
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84576519"
---
# <a name="anticipating-adopting-the-windows-communication-foundation-easing-future-integration"></a><span data-ttu-id="d85ad-102">Antecipando a adoção do Windows Communication Foundation: facilitando a futura integração</span><span class="sxs-lookup"><span data-stu-id="d85ad-102">Anticipating Adopting the Windows Communication Foundation: Easing Future Integration</span></span>
<span data-ttu-id="d85ad-103">Se você usar o ASP.NET hoje e antecipar o uso do WCF no futuro, este tópico fornecerá orientação para garantir que os novos serviços Web do ASP.NET funcionarão bem junto com os aplicativos WCF.</span><span class="sxs-lookup"><span data-stu-id="d85ad-103">If you use ASP.NET today, and anticipate using WCF in the future, this topic provides guidance to ensure that new ASP.NET Web services will work well together with WCF applications.</span></span>  
  
## <a name="general-recommendations"></a><span data-ttu-id="d85ad-104">Recomendações gerais</span><span class="sxs-lookup"><span data-stu-id="d85ad-104">General Recommendations</span></span>  
 <span data-ttu-id="d85ad-105">Adote o ASP.NET 2,0 para novos serviços.</span><span class="sxs-lookup"><span data-stu-id="d85ad-105">Adopt ASP.NET 2.0 for any new services.</span></span> <span data-ttu-id="d85ad-106">Isso dará acesso aos aprimoramentos e aprimoramentos da nova versão.</span><span class="sxs-lookup"><span data-stu-id="d85ad-106">Doing so will provide access to the improvements and enhancements of the new version.</span></span> <span data-ttu-id="d85ad-107">No entanto, ele também permitirá a possibilidade de usar componentes do ASP.NET 2,0 junto com os componentes do WCF no mesmo aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d85ad-107">However, it will also allow for the possibility of using ASP.NET 2.0 components together with WCF components in the same application.</span></span>  
  
## <a name="protocols"></a><span data-ttu-id="d85ad-108">Protocolos</span><span class="sxs-lookup"><span data-stu-id="d85ad-108">Protocols</span></span>  
 <span data-ttu-id="d85ad-109">Use o novo recurso do ASP.NET 2.0 para validar a conformidade com o WS-I Basic Profile 1,1:</span><span class="sxs-lookup"><span data-stu-id="d85ad-109">Use ASP.NET 2.0’s new facility for validating conformity to the WS-I Basic Profile 1.1:</span></span>  
  
```csharp  
[WebService(Namespace = "http://tempuri.org/")]  
[WebServiceBinding(  
     ConformsTo = WsiProfiles.BasicProfile1_1,  
     EmitConformanceClaims=true)]  
public interface IEcho  
```  
  
 <span data-ttu-id="d85ad-110">Os serviços Web do ASP.NET que estão em conformidade com o WS-I Basic Profile 1,1 serão interoperáveis com clientes WCF usando a associação predefinida do WCF, <xref:System.ServiceModel.BasicHttpBinding> .</span><span class="sxs-lookup"><span data-stu-id="d85ad-110">ASP.NET Web services that conform to WS-I Basic Profile 1.1 will be interoperable with WCF clients by using WCF predefined binding, <xref:System.ServiceModel.BasicHttpBinding>.</span></span>  
  
## <a name="service-development"></a><span data-ttu-id="d85ad-111">Desenvolvimento do serviço</span><span class="sxs-lookup"><span data-stu-id="d85ad-111">Service Development</span></span>  
 <span data-ttu-id="d85ad-112">Evite usar o <xref:System.Web.Services.Protocols.SoapDocumentServiceAttribute> atributo para ter mensagens roteadas para métodos com base no nome totalmente qualificado do elemento body da mensagem SOAP em vez do cabeçalho HTTP SoapAction.</span><span class="sxs-lookup"><span data-stu-id="d85ad-112">Avoid using the <xref:System.Web.Services.Protocols.SoapDocumentServiceAttribute> attribute to have messages routed to methods based on the fully-qualified name of the body element of the SOAP message rather than the SOAPAction HTTP header.</span></span> <span data-ttu-id="d85ad-113">O WCF usa o cabeçalho HTTP SOAPaction para mensagens de roteamento.</span><span class="sxs-lookup"><span data-stu-id="d85ad-113">WCF uses the SOAPAction HTTP header for routing messages.</span></span>  
  
## <a name="data-representation"></a><span data-ttu-id="d85ad-114">Representação de dados</span><span class="sxs-lookup"><span data-stu-id="d85ad-114">Data Representation</span></span>  
 <span data-ttu-id="d85ad-115">O XML no qual <xref:System.Xml.Serialization.XmlSerializer> serializa um tipo por padrão é semanticamente idêntico ao XML no qual o <xref:System.Runtime.Serialization.DataContractSerializer> serializa um tipo, desde que o namespace para o XML seja definido explicitamente.</span><span class="sxs-lookup"><span data-stu-id="d85ad-115">The XML into which <xref:System.Xml.Serialization.XmlSerializer> serializes a type by default is semantically identical to the XML into which the <xref:System.Runtime.Serialization.DataContractSerializer> serializes a type, provided the namespace for the XML is explicitly defined.</span></span> <span data-ttu-id="d85ad-116">Ao definir um tipo de dados para uso com serviços Web do ASP.NET em antecipação de adoção do WCF no futuro, faça o seguinte:</span><span class="sxs-lookup"><span data-stu-id="d85ad-116">When defining a data type for use with ASP.NET Web services in anticipation of adopting WCF in the future, do the following:</span></span>  
  
1. <span data-ttu-id="d85ad-117">Defina o tipo usando .NET Framework classes em vez de esquema XML.</span><span class="sxs-lookup"><span data-stu-id="d85ad-117">Define the type using .NET Framework classes rather than XML Schema.</span></span>  
  
2. <span data-ttu-id="d85ad-118">Adicione somente o <xref:System.SerializableAttribute> e o <xref:System.Xml.Serialization.XmlRootAttribute> à classe, usando o último para definir explicitamente o namespace para o tipo.</span><span class="sxs-lookup"><span data-stu-id="d85ad-118">Add only the <xref:System.SerializableAttribute> and the <xref:System.Xml.Serialization.XmlRootAttribute> to the class, using the latter to explicitly define the namespace for the type.</span></span> <span data-ttu-id="d85ad-119">Não adicione atributos adicionais do <xref:System.Xml.Serialization> namespace para controlar como a classe de .NET Framework deve ser convertida em XML.</span><span class="sxs-lookup"><span data-stu-id="d85ad-119">Do no add additional attributes from the <xref:System.Xml.Serialization> namespace to control how the .NET Framework class is to be translated into XML.</span></span>  
  
 <span data-ttu-id="d85ad-120">Ao adotar essa abordagem, você deve ser capaz de fazer as classes .NET em contratos de dados com a adição de <xref:System.Runtime.Serialization.DataContractAttribute> e <xref:System.Runtime.Serialization.DataMemberAttribute> sem alterar significativamente o XML no qual as classes são serializadas para transmissão.</span><span class="sxs-lookup"><span data-stu-id="d85ad-120">By adopting this approach, you should be able to later make the .NET classes into data contracts with the addition of the <xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> without significantly altering the XML into which the classes are serialized for transmission.</span></span> <span data-ttu-id="d85ad-121">Os tipos usados em mensagens por ASP.NET Web Services poderão ser processados como contratos de dados por aplicativos WCF, produzindo, entre outros benefícios, melhor desempenho em aplicativos WCF.</span><span class="sxs-lookup"><span data-stu-id="d85ad-121">The types used in messages by ASP.NET Web services will be able to be processed as data contracts by WCF applications, yielding, amongst other benefits, better performance in WCF applications.</span></span>  
  
## <a name="security"></a><span data-ttu-id="d85ad-122">Segurança</span><span class="sxs-lookup"><span data-stu-id="d85ad-122">Security</span></span>  
 <span data-ttu-id="d85ad-123">Evite usar as opções de autenticação fornecidas pelo Serviços de Informações da Internet (IIS).</span><span class="sxs-lookup"><span data-stu-id="d85ad-123">Avoid using the authentication options provided by Internet Information Services (IIS).</span></span> <span data-ttu-id="d85ad-124">Os clientes WCF não dão suporte a eles.</span><span class="sxs-lookup"><span data-stu-id="d85ad-124">WCF clients do not support them.</span></span> <span data-ttu-id="d85ad-125">Se um serviço precisar ser protegido, use as opções fornecidas pelo WCF, pois essas opções são mais ricas e são baseadas em protocolos padrão.</span><span class="sxs-lookup"><span data-stu-id="d85ad-125">If a service needs to be secured, use the options provided by WCF, because these options are richer and are based on standard protocols.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d85ad-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d85ad-126">See also</span></span>

- [<span data-ttu-id="d85ad-127">Antecipando a adoção do Windows Communication Foundation: facilitando a migração futura</span><span class="sxs-lookup"><span data-stu-id="d85ad-127">Anticipating Adopting the Windows Communication Foundation: Easing Future Migration</span></span>](anticipating-adopting-wcf-migration.md)
