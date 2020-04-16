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
# <a name="interoperability-with-aspnet-web-services"></a>Interoperabilidade com serviços Web do ASP.NET
A interoperabilidade entre ASP.NET serviços web e serviços Web da Windows Communication Foundation (WCF) pode ser alcançada garantindo que os serviços implementados usando ambas as tecnologias estejam em conformidade com a especificação ws-i perfil básico 1.1. ASP.NET serviços web que estejam em conformidade com o Perfil Básico WS-I 1.1 são <xref:System.ServiceModel.BasicHttpBinding>interoperáveis com os clientes WCF usando a vinculação fornecida pelo sistema WCF, .  
  
 Use ASP.NET opção 2.0 <xref:System.Web.Services.WebService> <xref:System.Web.Services.WebMethodAttribute> de adicionar e atributos a uma interface em vez de uma classe, e escrever uma classe para implementar a interface, como mostrado no código de amostra a seguir.  
  
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
  
 O uso dessa opção é preferível, pois a interface com o atributo <xref:System.Web.Services.WebService> constitui um contrato para as operações realizadas pelo serviço que pode ser reutilizado com várias classes que possam implementar esse mesmo contrato de diferentes formas.  
  
 Evite usar <xref:System.Web.Services.Protocols.SoapDocumentServiceAttribute> o atributo para ter mensagens roteadas para métodos com base no `SOAPAction` nome totalmente qualificado do elemento corpo da mensagem SOAP em vez do cabeçalho HTTP. O WCF `SOAPAction` usa o cabeçalho HTTP para direcionar mensagens.  
  
 O XML <xref:System.Xml.Serialization.XmlSerializer> no qual serializa um tipo por padrão é semanticamente <xref:System.Runtime.Serialization.DataContractSerializer> idêntico ao XML no qual o serializa um tipo, desde que o namespace para o XML seja explicitamente definido. Ao definir um tipo de dados para uso com os serviços ASP.NETWeb na expectativa de adotar o WCF, faça o seguinte:  
  
- Defina o tipo usando classes .NET Framework em vez de XML Schema.  
  
- Adicione apenas <xref:System.SerializableAttribute> o <xref:System.Xml.Serialization.XmlRootAttribute> e a classe, usando este último para definir explicitamente o namespace para o tipo. Não adicione atributos <xref:System.Xml.Serialization> adicionais do namespace para controlar como a classe .NET Framework deve ser traduzida em XML.  
  
- Ao adotar essa abordagem, você deve ser capaz de posteriormente transformar <xref:System.Runtime.Serialization.DataContractAttribute> as <xref:System.Runtime.Serialization.DataMemberAttribute> classes .NET em contratos de dados com a adição do e sem alterar significativamente o XML no qual as classes são serializadas para transmissão. Os tipos usados em mensagens por ASP.NET serviços Web podem ser processados como contratos de dados por aplicativos WCF, gerando, entre outros benefícios, melhor desempenho em aplicações WCF.  
  
 Evite usar as opções de autenticação fornecidas pelos Serviços de Informação da Internet (IIS). Os clientes WCF não os suportam. Se um serviço deve ser seguro, use as opções fornecidas pelo WCF, pois essas opções são robustas e são baseadas em protocolos padrão.  
  
## <a name="performance-impact-caused-by-loading-the-servicemodel-httpmodule"></a>Impacto de desempenho causado pelo carregamento do ServiceModel HttpModule  
 No .NET Framework 3.0, `HttpModule` o WCF foi instalado no arquivo web.config raiz, de tal forma que cada ASP.NET aplicativo estava habilitado para WCF. Isso pode afetar o desempenho, `ServiceModel` para que você possa remover para o arquivo Web.config como mostrado no exemplo a seguir.  
  
```xml  
<httpModules>  
    <remove name="ServiceModel" />  
</httpModules>
```  
  
## <a name="see-also"></a>Confira também

- [Como configurar um serviço do WCF para interoperar com os clientes de serviço Web do ASP.NET](../../../../docs/framework/wcf/feature-details/config-wcf-service-with-aspnet-web-service.md)
