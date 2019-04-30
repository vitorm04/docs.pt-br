---
title: Interoperabilidade com serviços Web do ASP.NET
ms.date: 03/30/2017
ms.assetid: 622422f8-6651-442f-b8be-e654a4aabcac
ms.openlocfilehash: c6fec1d520cd251473d8840b7b1afe879002a04c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61972556"
---
# <a name="interoperability-with-aspnet-web-services"></a>Interoperabilidade com serviços Web do ASP.NET
Interoperabilidade entre [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] serviços da Web e serviços da Web do Windows Communication Foundation (WCF) podem ser obtidos, garantindo que os serviços implementados usando ambas as tecnologias em conformidade com o WS-I Basic Profile 1.1 especificação. [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Serviços Web que estão em conformidade com WS-I Basic Profile 1.1 são interoperáveis com clientes do WCF usando a associação WCF fornecida pelo sistema, <xref:System.ServiceModel.BasicHttpBinding>.  
  
 Use [!INCLUDE[vstecasplong](../../../../includes/vstecasplong-md.md)] opção de adicionar a <xref:System.Web.Services.WebService> e <xref:System.Web.Services.WebMethodAttribute> atributos para uma interface em vez de uma classe e escrevendo uma classe para implementar a interface, conforme mostrado no código de exemplo a seguir.  
  
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
  
 O uso dessa opção é preferível, pois a interface com o <xref:System.Web.Services.WebService> atributo constitui um contrato para as operações executadas pelo serviço que pode ser reutilizado com várias classes que podem implementar o mesmo contrato de maneiras diferentes.  
  
 Evite usar o <xref:System.Web.Services.Protocols.SoapDocumentServiceAttribute> atributo para que as mensagens roteadas para métodos com base no nome totalmente qualificado do elemento de corpo da mensagem SOAP em vez de `SOAPAction` cabeçalho HTTP. O WCF usa o `SOAPAction` cabeçalho HTTP de roteamento de mensagens.  
  
 O XML no qual <xref:System.Xml.Serialization.XmlSerializer> serializa um tipo por padrão é semanticamente idêntico ao XML em que o <xref:System.Runtime.Serialization.DataContractSerializer> serializa um tipo, desde que o namespace para o XML seja explicitamente definido. Ao definir um tipo de dados para uso com [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]serviços em antecipação a adoção do WCF Web, faça o seguinte:  
  
- Defina o tipo usando classes do .NET Framework em vez de esquema XML.  
  
- Adicione somente as <xref:System.SerializableAttribute> e o <xref:System.Xml.Serialization.XmlRootAttribute> à classe, usando o último para definir explicitamente o namespace para o tipo. Não adicione atributos adicionais do <xref:System.Xml.Serialization> namespace para controlar como a classe do .NET Framework deve ser convertido em XML.  
  
- Ao adotar essa abordagem, você deve ser capaz de fazer mais tarde as classes do .NET em contratos de dados com a adição do <xref:System.Runtime.Serialization.DataContractAttribute> e <xref:System.Runtime.Serialization.DataMemberAttribute> sem alterar significativamente o XML no qual as classes são serializadas para transmissão. Os tipos usados em mensagens por [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] serviços Web podem ser processados como contratos de dados por aplicativos do WCF, gerando, entre outros benefícios, melhor desempenho em aplicativos do WCF.  
  
 Evite usar as opções de autenticação fornecidas pelo Internet Information Services (IIS). Clientes do WCF não oferecem suporte a isso. Se um serviço deve ser protegido, use as opções fornecidas pelo WCF, porque essas opções são robustas e se baseiam nos protocolos padrão.  
  
## <a name="performance-impact-caused-by-loading-the-servicemodel-httpmodule"></a>Impacto no desempenho causado por carregar o ServiceModel HttpModule  
 No .NET Framework 3.0, o WCF `HttpModule` foi instalado na raiz do arquivo Web. config, de modo que todos os aplicativos ASP.NET foi habilitado do WCF. Isso pode afetar o desempenho, portanto, você pode remover `ServiceModel` para o arquivo Web. config, conforme mostrado no exemplo a seguir.  
  
```xml  
<httpModules>  
    <remove name="ServiceModel" />  
<httpModules/>  
```  
  
## <a name="see-also"></a>Consulte também

- [Como: Configurar o serviço do WCF para interoperar com clientes de serviço Web do ASP.NET](../../../../docs/framework/wcf/feature-details/config-wcf-service-with-aspnet-web-service.md)
