---
title: 'Antecipando a adoção do Windows Communication Foundation: facilitando a migração futura'
ms.date: 03/30/2017
ms.assetid: f49664d9-e9e0-425c-a259-93f0a569d01b
ms.openlocfilehash: aeafc164d16d9dc60ad0b3012da292e9b0bb38b3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="anticipating-adopting-the-windows-communication-foundation-easing-future-migration"></a>Antecipando a adoção do Windows Communication Foundation: facilitando a migração futura
Para garantir uma migração futura mais fácil de novos aplicativos ASP.NET para o WCF, siga as recomendações acima, bem como as recomendações a seguir.  
  
## <a name="protocols"></a>Protocolos  
 Desabilite o suporte para SOAP 1.2 do ASP.NET 2.0:  
  
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
  
 Isso é recomendável porque o WCF exige mensagens em conformidade com os protocolos diferentes, como SOAP 1.1 e SOAP 1.2, usando diferentes pontos de extremidade. Se uma Web do ASP.NET 2.0 serviço está configurado para dar suporte a SOAP 1.1 e SOAP 1.2, que é a configuração padrão, em seguida, ele não pode ser migrado direta para um único ponto de extremidade do WCF no endereço original que seria certamente ser compatível com todos os Web do ASP.NET clientes existentes do serviço. Escolher também SOAP 1.2 em vez de 1.1 mais severos restringirá clientele do serviço.  
  
## <a name="service-development"></a>Desenvolvimento do serviço  
 WCF permite que você defina os contratos de serviço aplicando o <xref:System.ServiceModel.ServiceContractAttribute> para interfaces ou classes. É recomendável aplicar o atributo a uma interface em vez de uma classe, porque fazer isso cria uma definição de um contrato que pode ser implementada diversos por qualquer número de classes. ASP.NET 2.0 dá suporte a opção de aplicar o <xref:System.Web.Services.WebService> a interfaces, bem como classes de atributo. No entanto, como já mencionado, há um defeito no ASP.NET 2.0, pelo qual o parâmetro de Namespace do <xref:System.Web.Services.WebService> atributo não tem nenhum efeito quando esse atributo é aplicado a uma interface em vez de uma classe. Como é geralmente é recomendável modificar o espaço para nome de um serviço do valor padrão, http://tempuri.org, usando o parâmetro de Namespace do <xref:System.Web.Services.WebService> atributo, um deve continuar definindo serviços Web ASP.NET, aplicando o <xref:System.ServiceModel.ServiceContractAttribute> atributo para interfaces ou classes.  
  
-   Ter apenas código possível nos métodos pelos quais as interfaces são definidas. Tê-los delegar seus trabalhos para outras classes. Novos tipos de serviço do WCF, em seguida, podem também delegar seu trabalho substancial para essas classes.  
  
-   Fornecer nomes explícitos para as operações de um serviço usando o `MessageName` parâmetro o <xref:System.Web.Services.WebMethodAttribute>.  
  
    ```  
    [WebMethod(MessageName="ExplicitName")]  
    string Echo(string input);  
    ```  
  
     Isso é importante, porque os nomes padrão para operações no ASP.NET são diferentes dos nomes padrão fornecidos pelo WCF. Fornecendo nomes explícito, você evitar contar com as definições padrão.  
  
-   Não implemente a operações do serviço Web do ASP.NET com métodos polimórficos, porque o WCF não oferece suporte a operações de implementação com métodos polimórficos.  
  
-   Use o <xref:System.Web.Services.Protocols.SoapDocumentMethodAttribute> para fornecer valores explícitos para os cabeçalhos HTTP SOAPAction pelo qual HTTP as solicitações serão roteadas para métodos.  
  
    ```  
    [WebMethod]  
    [SoapDocumentMethod(RequestElementName="ExplicitAction")]  
    string Echo(string input);  
    ```  
  
     Essa abordagem contornar a depender valores de SOAPAction usados pelo ASP.NET e WCF, sendo o mesmo padrão.  
  
-   Evite usar extensões SOAP. Se as extensões SOAP forem necessárias, determine se a finalidade para a qual eles são considerados é um recurso que já é fornecido pelo WCF. Se esse for realmente o caso, reconsidere, em seguida, a opção de não adotar WCF imediatamente.  
  
## <a name="state-management"></a>Gerenciamento do estado  
 Evite ter que manter o estado nos serviços. Manter o estado tende a comprometer a escalabilidade de um aplicativo e os mecanismos de gerenciamento de estado do ASP.NET e WCF são muito diferentes, embora o WCF dá suporte os mecanismos ASP.NET no modo de compatibilidade do ASP.NET.  
  
## <a name="exception-handling"></a>Tratamento de Exceção  
 Também ao criar as estruturas dos tipos de dados sejam enviadas e recebidas por um serviço, estruturas de design para representar vários tipos de exceções que podem ocorrer dentro de um serviço que podem ser conveniente transmitir a um cliente.  
  
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
  
 Permitir que essas classes serializar próprios para XML:  
  
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
  
 As classes, em seguida, podem ser usadas para fornecer os detalhes de geradas explicitamente <xref:System.Web.Services.Protocols.SoapException> instâncias:  
  
```  
AnctipatedException exception = new AnticipatedException();  
exception.AnticipatedExceptionInformation = "…";  
throw new SoapException(  
     "Fault occurred",  
     SoapException.ClientFaultCode,  
     Context.Request.Url.AbsoluteUri,  
     exception.ToXML());  
```  
  
 Essas classes de exceção será prontamente reutilizáveis com o WCF<xref:System.ServiceModel.FaultException%601> classe lançar um novo `FaultException<AnticipatedException>(anticipatedException);`  
  
## <a name="security"></a>Segurança  
 A seguir estão algumas recomendações de segurança.  
  
-   Evite usar perfis do ASP.NET 2.0, como usá-los restringe o uso do modo de integração de ASP.NET se o serviço foi migrado para o WCF.  
  
-   Evite usar ACLs para controlar o acesso a serviços, como o ASP.NET Web services dá suporte a ACLs usando o Internet Information Services (IIS), o WCF não — porque dependem de serviços Web do ASP.NET no IIS para hospedar e WCF não precisam necessariamente ser hospedado no IIS.  
  
-   Considere o uso de provedores de função do ASP.NET 2.0 para autorizar o acesso aos recursos de um serviço.  
  
## <a name="see-also"></a>Consulte também  
 [Antecipando a adoção do Windows Communication Foundation: facilitando a futura integração](../../../../docs/framework/wcf/feature-details/anticipating-adopting-the-wcf-easing-future-integration.md)
