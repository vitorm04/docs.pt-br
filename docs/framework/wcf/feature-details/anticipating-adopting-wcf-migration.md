---
title: 'Antecipar a adoção do Windows Communication Foundation: facilitar a migração futura'
ms.date: 03/30/2017
ms.assetid: f49664d9-e9e0-425c-a259-93f0a569d01b
ms.openlocfilehash: 09bbb11c58992f0fabcb822f5f3d88fef273bea9
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/28/2019
ms.locfileid: "67425278"
---
# <a name="anticipating-adopting-the-windows-communication-foundation-easing-future-migration"></a>Antecipar a adoção do Windows Communication Foundation: facilitar a migração futura
Para garantir uma migração mais fácil futuras de novos aplicativos ASP.NET ao WCF, siga as recomendações acima, bem como as recomendações a seguir.  
  
## <a name="protocols"></a>Protocolos  
 Desabilite o suporte do ASP.NET 2.0 para SOAP 1.2:  
  
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
  
 É aconselhável fazer isso, porque o WCF exige que as mensagens em conformidade com protocolos diferentes, como SOAP 1.1 e SOAP 1.2, acesse usando pontos de extremidade diferentes. Se um ASP.NET 2.0 da Web serviço está configurado para dar suporte a SOAP 1.1 e SOAP 1.2, que é a configuração padrão, em seguida, ele não pode ser migrado direta para um único ponto de extremidade do WCF no endereço original que seria certamente seja compatível com todos os Web do ASP.NET clientes existentes do serviço. Também escolher SOAP 1.2 em vez de 1.1 mais seriamente restringirá o clientele do serviço.  
  
## <a name="service-development"></a>Desenvolvimento do serviço  
 O WCF permite que você definir contratos de serviço por meio da aplicação de <xref:System.ServiceModel.ServiceContractAttribute> interfaces ou classes. É recomendável aplicar o atributo a uma interface em vez de uma classe, porque fazer isso cria uma definição de um contrato que pode ser chamado implementada por qualquer número de classes. O ASP.NET 2.0 oferece suporte a opção de aplicar o <xref:System.Web.Services.WebService> para interfaces, bem como classes de atributo. No entanto, como já mencionado, há um defeito no ASP.NET 2.0, pelo qual o parâmetro de Namespace do <xref:System.Web.Services.WebService> atributo não tem nenhum efeito quando esse atributo é aplicado a uma interface em vez de uma classe. Já que geralmente é aconselhável para modificar o namespace do valor padrão, um serviço `http://tempuri.org`, usando o parâmetro de Namespace do <xref:System.Web.Services.WebService> atributo, um deve continuar definindo serviços Web do ASP.NET por meio da aplicação a <xref:System.ServiceModel.ServiceContractAttribute> atributo para interfaces ou classes.  
  
- Ter tão pouco de código possível nos métodos pelos quais essas interfaces são definidas. Peça para delegar suas tarefas a outras classes. Novos tipos de serviço do WCF, em seguida, também podem delegar seu trabalho substancial para essas classes.  
  
- Fornecer nomes explícitos para as operações de um serviço usando o `MessageName` parâmetro do <xref:System.Web.Services.WebMethodAttribute>.  
  
    ```csharp  
    [WebMethod(MessageName="ExplicitName")]  
    string Echo(string input);  
    ```  
  
     Isso é importante, porque os nomes padrão para operações no ASP.NET são diferentes dos nomes padrão fornecidos pelo WCF. Fornecendo nomes explícitos, você evite contar com os valores padrão.  
  
- Não implemente operações de serviço Web do ASP.NET com métodos polimórficos, porque o WCF não oferece suporte a operações de implementação com métodos polimórficos.  
  
- Use o <xref:System.Web.Services.Protocols.SoapDocumentMethodAttribute> para fornecer valores explícitos para os cabeçalhos HTTP SOAPAction pelo qual HTTP solicitações serão roteadas para métodos.  
  
    ```csharp  
    [WebMethod]  
    [SoapDocumentMethod(RequestElementName="ExplicitAction")]  
    string Echo(string input);  
    ```  
  
     Essa abordagem contornarão precisar contar valores SOAPAction usados por ASP.NET e WCF que está sendo o mesmo padrão.  
  
- Evite usar extensões SOAP. Se as extensões SOAP são necessárias, determine se a finalidade para a qual eles são considerados é um recurso que já é fornecido pelo WCF. Se esse for realmente o caso, em seguida, Reconsidere a opção de não adotar imediatamente o WCF.  
  
## <a name="state-management"></a>Gerenciamento do estado  
 Evite ter que manter o estado nos serviços. Não só manter o estado tende a comprometer a escalabilidade de um aplicativo, mas os mecanismos de gerenciamento de estado do ASP.NET e WCF são muito diferentes, embora o WCF oferece suporte os mecanismos ASP.NET no modo de compatibilidade do ASP.NET.  
  
## <a name="exception-handling"></a>Tratamento de Exceção  
 Ao criar as estruturas dos tipos de dados a serem enviadas e recebidas por um serviço, também estruturas de design para representar os vários tipos de exceções que podem ocorrer dentro de um serviço que um podem desejar transmitir para um cliente.  
  
```csharp  
[Serializable]  
[XmlRoot(Namespace="ExplicitNamespace", IsNullable=true)]  
public partial class AnticipatedException 
{ 
    private string anticipatedExceptionInformationField;  

    public string AnticipatedExceptionInformation 
    {  
        get {   
            return this.anticipatedExceptionInformationField;  
        }  
        set {  
            this.anticipatedExceptionInformationField = value;  
        }  
    }  
}  
```  
  
 Permitem que essas classes se serializam para XML:  
  
```csharp  
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
  
 As classes, em seguida, podem ser usadas para fornecer os detalhes para geradas explicitamente <xref:System.Web.Services.Protocols.SoapException> instâncias:  
  
```csharp  
AnticipatedException exception = new AnticipatedException();  
exception.AnticipatedExceptionInformation = "…";  
throw new SoapException(  
     "Fault occurred",  
     SoapException.ClientFaultCode,  
     Context.Request.Url.AbsoluteUri,  
     exception.ToXML());  
```  
  
 Essas classes de exceção serão prontamente reutilizáveis com o WCF <xref:System.ServiceModel.FaultException%601> classe lançar um novo `FaultException<AnticipatedException>(anticipatedException);`  
  
## <a name="security"></a>Segurança  
 A seguir estão algumas recomendações de segurança.  
  
- Evite usar perfis do ASP.NET 2.0, como usá-los restringiriam o uso do modo de integração do ASP.NET se o serviço foi migrado para o WCF.  
  
- Evite usar ACLs para controlar o acesso a serviços, como ASP.NET Web services dá suporte a ACLs usando os serviços de informações da Internet (IIS), o WCF não — porque dependem de serviços Web do ASP.NET no IIS para hospedar e WCF não precisa necessariamente ser hospedado no IIS.  
  
- Considere o uso de provedores de função do ASP.NET 2.0 para autorizar o acesso aos recursos de um serviço.  
  
## <a name="see-also"></a>Consulte também

- [Antecipando a adoção do Windows Communication Foundation: Facilitando a futura integração](../../../../docs/framework/wcf/feature-details/anticipating-adopting-the-wcf-easing-future-integration.md)
