---
title: "Interoperabilidade com serviços Web do ASP.NET"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 622422f8-6651-442f-b8be-e654a4aabcac
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ef174f457114003e5b2783b50040424d9a96945c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="interoperability-with-aspnet-web-services"></a>Interoperabilidade com serviços Web do ASP.NET
Interoperabilidade entre [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] serviços Web e [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] serviços Web podem ser obtidos, garantindo que implementada usando as duas tecnologias de serviços estão em conformidade com o WS-I Basic Profile 1.1 especificação. [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]Serviços Web que está de acordo com WS-I Basic Profile 1.1 são interoperáveis com [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] clientes usando [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] associação fornecida pelo sistema, <xref:System.ServiceModel.BasicHttpBinding>.  
  
 Use [!INCLUDE[vstecasplong](../../../../includes/vstecasplong-md.md)] opção de adicionar o <xref:System.Web.Services.WebService> e <xref:System.Web.Services.WebMethodAttribute> atributos a uma interface em vez de uma classe e escrevendo uma classe para implementar a interface, conforme mostrado no código de exemplo a seguir.  
  
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
  
 O uso dessa opção é o preferencial, porque a interface com o <xref:System.Web.Services.WebService> atributo constitui um contrato para as operações executadas pelo serviço que pode ser reutilizado com várias classes que podem implementar esse mesmo contrato de maneiras diferentes.  
  
 Evite usar o <xref:System.Web.Services.Protocols.SoapDocumentServiceAttribute> atributo para que as mensagens roteadas para os métodos com base no nome totalmente qualificado do elemento de corpo da mensagem SOAP, em vez do `SOAPAction` cabeçalho HTTP. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]usa o `SOAPAction` cabeçalho HTTP para roteamento de mensagens.  
  
 O XML no qual <xref:System.Xml.Serialization.XmlSerializer> serializa um tipo por padrão é semanticamente idêntico ao XML no qual o <xref:System.Runtime.Serialization.DataContractSerializer> serializa um tipo, fornecido o namespace para o XML é definido explicitamente. Ao definir um tipo de dados para uso com [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]Web services antecipadamente adotando [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], faça o seguinte:  
  
-   Defina o tipo usando classes do .NET Framework em vez de esquema XML.  
  
-   Adicione somente o <xref:System.SerializableAttribute> e <xref:System.Xml.Serialization.XmlRootAttribute> para a classe usando o último definir explicitamente o namespace para o tipo. Não adicione atributos adicionais do <xref:System.Xml.Serialization> namespace para controlar como a classe do .NET Framework é para ser convertido em XML.  
  
-   Ao adotar essa abordagem, você deve ser capaz de fazer mais tarde as classes do .NET em contratos de dados com a adição do <xref:System.Runtime.Serialization.DataContractAttribute> e <xref:System.Runtime.Serialization.DataMemberAttribute> sem alterar significativamente o XML no qual as classes são serializadas para transmissão. Os tipos usados em mensagens por [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] serviços Web podem ser processados como contratos de dados por [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplicativos, gerando, entre outros benefícios, melhor desempenho em [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplicativos.  
  
 Evite usar as opções de autenticação fornecidas pelo Internet Information Services (IIS). [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]os clientes não dão suporte a eles. Se um serviço deve ser protegido, use as opções fornecidas por [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], porque essas opções são robustas e baseadas em protocolos padrão.  
  
## <a name="performance-impact-caused-by-loading-the-servicemodel-httpmodule"></a>Impacto no desempenho causado ao carregar o ServiceModel HttpModule  
 O .NET Framework 3.0, o WCF `HttpModule` foi instalado na raiz do arquivo Web. config, de modo que todos os aplicativos ASP.NET foi WCF habilitado. Isso pode afetar o desempenho, portanto você pode remover `ServiceModel` para o arquivo Web. config, conforme mostrado no exemplo a seguir.  
  
```xml  
<httpModules>  
    <remove name="ServiceModel" />  
<httpModules/>  
```  
  
## <a name="see-also"></a>Consulte também  
 [Como configurar o serviço do WCF para interoperar com clientes de serviço Web do ASP.NET](../../../../docs/framework/wcf/feature-details/config-wcf-service-with-aspnet-web-service.md)
