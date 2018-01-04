---
title: "Antecipando a adoção do Windows Communication Foundation: facilitando a migração futura"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f49664d9-e9e0-425c-a259-93f0a569d01b
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 76770eff76a7a641ee853f314b5d2c14a56737c1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="anticipating-adopting-the-windows-communication-foundation-easing-future-migration"></a>Antecipando a adoção do Windows Communication Foundation: facilitando a migração futura
Para garantir uma migração futura mais fácil de novos aplicativos ASP.NET para [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], siga as recomendações acima, bem como as recomendações a seguir.  
  
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
  
 É aconselhável fazer isso porque [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] requer mensagens em conformidade com os protocolos diferentes, como SOAP 1.1 e SOAP 1.2, usando diferentes pontos de extremidade. Se um serviço Web do ASP.NET 2.0 está configurado para dar suporte a SOAP 1.1 e SOAP 1.2, que é a configuração padrão, e não podem ser migrada para a frente a um único [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ponto de extremidade no endereço original que seria certamente ser compatível com todos o ASP Clientes existentes do serviço web do .NET. Escolher também SOAP 1.2 em vez de 1.1 mais severos restringirá clientele do serviço.  
  
## <a name="service-development"></a>Desenvolvimento do serviço  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]permite que você defina os contratos de serviço aplicando o <xref:System.ServiceModel.ServiceContractAttribute> para interfaces ou classes. É recomendável aplicar o atributo a uma interface em vez de uma classe, porque fazer isso cria uma definição de um contrato que pode ser implementada diversos por qualquer número de classes. ASP.NET 2.0 dá suporte a opção de aplicar o <xref:System.Web.Services.WebService> a interfaces, bem como classes de atributo. No entanto, como já mencionado, há um defeito no ASP.NET 2.0, pelo qual o parâmetro de Namespace do <xref:System.Web.Services.WebService> atributo não tem nenhum efeito quando esse atributo é aplicado a uma interface em vez de uma classe. Como é geralmente é recomendável modificar o espaço para nome de um serviço do valor padrão, http://tempuri.org, usando o parâmetro de Namespace do <xref:System.Web.Services.WebService> atributo, um deve continuar definindo serviços Web ASP.NET, aplicando o <xref:System.ServiceModel.ServiceContractAttribute> atributo para interfaces ou classes.  
  
-   Ter apenas código possível nos métodos pelos quais as interfaces são definidas. Tê-los delegar seus trabalhos para outras classes. Novo [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] tipos de serviço, em seguida, também podem delegar seu trabalho substancial para essas classes.  
  
-   Fornecer nomes explícitos para as operações de um serviço usando o `MessageName` parâmetro o <xref:System.Web.Services.WebMethodAttribute>.  
  
    ```  
    [WebMethod(MessageName="ExplicitName")]  
    string Echo(string input);  
    ```  
  
     Isso é importante, porque os nomes padrão para operações no ASP.NET são diferentes dos nomes padrão fornecidos pelo [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. Fornecendo nomes explícito, você evitar contar com as definições padrão.  
  
-   Não implementar operações de serviço Web do ASP.NET com métodos polimórficos, porque [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] não oferece suporte a operações de implementação com métodos polimórficos.  
  
-   Use o <xref:System.Web.Services.Protocols.SoapDocumentMethodAttribute> para fornecer valores explícitos para os cabeçalhos HTTP SOAPAction pelo qual HTTP as solicitações serão roteadas para métodos.  
  
    ```  
    [WebMethod]  
    [SoapDocumentMethod(RequestElementName="ExplicitAction")]  
    string Echo(string input);  
    ```  
  
     Essa abordagem contornar a precisar contar com o padrão usados por ASP.NET os valores de SOAPAction e [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] sendo o mesmo.  
  
-   Evite usar extensões SOAP. Se as extensões SOAP forem necessárias, determinar se a finalidade para a qual eles são considerados é um recurso que já é fornecido pelos [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. Se esse for realmente o caso, reconsidere, em seguida, a opção de não adotar [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] imediatamente.  
  
## <a name="state-management"></a>Gerenciamento do estado  
 Evite ter que manter o estado nos serviços. Não só mantém o estado tendem a comprometer a escalabilidade de um aplicativo, mas os mecanismos de gerenciamento de estado do ASP.NET e [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] são muito diferentes, embora [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] dá suporte os mecanismos ASP.NET na compatibilidade com ASP.NET modo.  
  
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
  
 Essas classes de exceção será prontamente reutilizáveis com o[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] <xref:System.ServiceModel.FaultException%601> classe lançar um novo`FaultException<AnticipatedException>(anticipatedException);`  
  
## <a name="security"></a>Segurança  
 A seguir estão algumas recomendações de segurança.  
  
-   Evite usar perfis do ASP.NET 2.0, como usá-los restringe o uso do modo de integração de ASP.NET se o serviço foi migrado para [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
-   Evite usar ACLs para controlar o acesso a serviços, como ACLs usando o Internet Information Services (IIS) oferece suporte a serviços Web do ASP.NET [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] não — porque dependem de serviços Web do ASP.NET no IIS para hospedar e WCF não precisam necessariamente ser hospedado no IIS.  
  
-   Considere o uso de provedores de função do ASP.NET 2.0 para autorizar o acesso aos recursos de um serviço.  
  
## <a name="see-also"></a>Consulte também  
 [Antecipando a adoção do Windows Communication Foundation: facilitando a futura integração](../../../../docs/framework/wcf/feature-details/anticipating-adopting-the-wcf-easing-future-integration.md)
