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
# <a name="interoperability-with-aspnet-web-services"></a>Interoperabilidade com serviços Web do ASP.NET
A interoperabilidade entre ASP.NET Web Services e serviços Web Windows Communication Foundation (WCF) pode ser obtida garantindo que os serviços implementados usando ambas as tecnologias estejam em conformidade com a especificação WS-I Basic Profile 1,1. Os serviços Web do ASP.NET que estão em conformidade com o WS-I Basic Profile 1,1 são interoperáveis com clientes WCF usando a <xref:System.ServiceModel.BasicHttpBinding>Associação fornecida pelo sistema do WCF,.  
  
 Use a opção ASP.NET 2,0 de adicionar <xref:System.Web.Services.WebService> os <xref:System.Web.Services.WebMethodAttribute> atributos e a uma interface, em vez de uma classe, e escrever uma classe para implementar a interface, conforme mostrado no código de exemplo a seguir.  
  
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
  
 Usar essa opção é preferencial, pois a interface com o <xref:System.Web.Services.WebService> atributo constitui um contrato para as operações executadas pelo serviço que podem ser reutilizadas com várias classes que podem implementar esse mesmo contrato de maneiras diferentes.  
  
 Evite usar o <xref:System.Web.Services.Protocols.SoapDocumentServiceAttribute> atributo para que as mensagens sejam roteadas para métodos com base no nome totalmente qualificado do elemento body da mensagem SOAP, e não `SOAPAction` no cabeçalho http. O WCF usa `SOAPAction` o cabeçalho HTTP para rotear mensagens.  
  
 O XML no qual <xref:System.Xml.Serialization.XmlSerializer> serializa um tipo por padrão é semanticamente idêntico ao XML no qual o <xref:System.Runtime.Serialization.DataContractSerializer> serializa um tipo, desde que o namespace para o XML seja definido explicitamente. Ao definir um tipo de dados para uso com os serviços ASP. NETWeb em antecipação de adoção do WCF, faça o seguinte:  
  
- Defina o tipo usando .NET Framework classes em vez de esquema XML.  
  
- Adicione somente o <xref:System.SerializableAttribute> e o <xref:System.Xml.Serialization.XmlRootAttribute> à classe, usando o último para definir explicitamente o namespace para o tipo. Não adicione atributos adicionais do <xref:System.Xml.Serialization> namespace para controlar como a classe de .NET Framework deve ser convertida em XML.  
  
- Ao adotar essa abordagem, você deve ser capaz de fazer as classes .net em contratos de dados com a adição de <xref:System.Runtime.Serialization.DataContractAttribute> e <xref:System.Runtime.Serialization.DataMemberAttribute> sem alterar significativamente o XML no qual as classes são serializadas para transmissão. Os tipos usados em mensagens por ASP.NET Web Services podem ser processados como contratos de dados por aplicativos WCF, produzindo, entre outros benefícios, melhor desempenho em aplicativos WCF.  
  
 Evite usar as opções de autenticação fornecidas pelo Serviços de Informações da Internet (IIS). Os clientes WCF não dão suporte a eles. Se um serviço precisar ser protegido, use as opções fornecidas pelo WCF, pois essas opções são robustas e são baseadas em protocolos padrão.  
  
## <a name="performance-impact-caused-by-loading-the-servicemodel-httpmodule"></a>Impacto no desempenho causado pelo carregamento do ServiceModel HttpModule  
 No .NET Framework 3,0, o WCF `HttpModule` foi instalado no arquivo Web. config raiz, de modo que todos os aplicativos ASP.net eram habilitados para WCF. Isso pode afetar o desempenho para que você possa `ServiceModel` remover o arquivo Web. config, conforme mostrado no exemplo a seguir.  
  
```xml  
<httpModules>  
    <remove name="ServiceModel" />  
<httpModules/>  
```  
  
## <a name="see-also"></a>Consulte também

- [Como: Configurar o serviço WCF para interoperar com clientes de serviço Web ASP.NET](../../../../docs/framework/wcf/feature-details/config-wcf-service-with-aspnet-web-service.md)
