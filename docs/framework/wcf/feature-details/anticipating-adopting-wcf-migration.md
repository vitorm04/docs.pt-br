---
title: 'Antecipando a adoção do Windows Communication Foundation: facilitando a migração futura'
ms.date: 03/30/2017
ms.assetid: f49664d9-e9e0-425c-a259-93f0a569d01b
ms.openlocfilehash: 995bdaaaba96bf8697ea75c1f1a17fa8e51ec2d5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185468"
---
# <a name="anticipating-adopting-the-windows-communication-foundation-easing-future-migration"></a>Antecipando a adoção do Windows Communication Foundation: facilitando a migração futura
Para garantir uma migração futura mais fácil de novos aplicativos de ASP.NET para o WCF, siga as recomendações anteriores, bem como as seguintes recomendações.  
  
## <a name="protocols"></a>Protocolos  
 Desativar o suporte do ASP.NET 2.0 para o SOAP 1.2:  
  
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
  
 Fazer isso é aconselhável porque o WCF requer mensagens em conformidade com diferentes protocolos, como SOAP 1.1 e SOAP 1.2, para usar diferentes pontos finais. Se um serviço web ASP.NET 2.0 for configurado para suportar tanto o SOAP 1.1 quanto o SOAP 1.2, que é a configuração padrão, então ele não poderá ser migrado para um único ponto final wcf no endereço original que certamente seria compatível com todos os ASP.NET Web os clientes existentes do serviço. Também a escolha do SOAP 1.2 em vez do 1.1 restringirá mais severamente a clientela do serviço.  
  
## <a name="service-development"></a>Desenvolvimento do serviço  
 O WCF permite que você defina contratos de serviço aplicando-o <xref:System.ServiceModel.ServiceContractAttribute> em interfaces ou em classes. Recomenda-se aplicar o atributo a uma interface e não a uma classe, pois fazê-lo cria uma definição de um contrato que pode ser implementado várias vezes por qualquer número de classes. ASP.NET 2.0 suporta a opção <xref:System.Web.Services.WebService> de aplicar o atributo em interfaces e classes. No entanto, como mencionado já, há um defeito no ASP.NET 2.0, pelo qual o parâmetro Namespace do atributo <xref:System.Web.Services.WebService> não tem efeito quando esse atributo é aplicado a uma interface em vez de uma classe. Uma vez que é geralmente aconselhável modificar o namespace `http://tempuri.org`de um serviço a partir <xref:System.Web.Services.WebService> do valor padrão, usando o parâmetro <xref:System.ServiceModel.ServiceContractAttribute> Namespace do atributo, deve-se continuar definindo ASP.NET Web Services aplicando o atributo tanto em interfaces quanto em classes.  
  
- Tenha o menor código possível nos métodos pelos quais essas interfaces são definidas. Que delegem seu trabalho para outras classes. Novos tipos de serviço sufem, então, também poderiam delegar seu trabalho substantivo para essas classes.  
  
- Fornecer nomes explícitos para as `MessageName` operações de <xref:System.Web.Services.WebMethodAttribute>um serviço usando o parâmetro do .  
  
    ```csharp  
    [WebMethod(MessageName="ExplicitName")]  
    string Echo(string input);  
    ```  
  
     Fazer isso é importante, pois os nomes padrão para operações em ASP.NET são diferentes dos nomes padrão fornecidos pelo WCF. Ao fornecer nomes explícitos, você evita confiar nos padrões.  
  
- Não implemente ASP.NET operações de serviço web com métodos polimórficos, pois o WCF não suporta operações de implementação com métodos polimórficos.  
  
- Use <xref:System.Web.Services.Protocols.SoapDocumentMethodAttribute> o para fornecer valores explícitos para os cabeçalhos SOAPAction HTTP pelos quais as solicitações HTTP serão encaminhadas para métodos.  
  
    ```csharp  
    [WebMethod]  
    [SoapDocumentMethod(RequestElementName="ExplicitAction")]  
    string Echo(string input);  
    ```  
  
     Tomar essa abordagem contornará ter que confiar nos valores de SOAPAction padrão usados por ASP.NET e WCF sendo o mesmo.  
  
- Evite usar extensões SOAP. Se as extensões SOAP forem necessárias, determine se a finalidade para a qual elas estão sendo consideradas é uma característica que já é fornecida pelo WCF. Se esse for realmente o caso, então reconsidere a escolha de não adotar o WCF imediatamente.  
  
## <a name="state-management"></a>Gerenciamento do estado  
 Evite ter que manter o estado nos serviços. Não só a manutenção do estado tende a comprometer a escalabilidade de uma aplicação, mas os mecanismos de gestão estatal de ASP.NET e WCF são muito diferentes, embora o WCF apoie os mecanismos ASP.NET no modo de compatibilidade ASP.NET.  
  
## <a name="exception-handling"></a>Tratamento de exceção  
 Ao projetar as estruturas dos tipos de dados a serem enviados e recebidos por um serviço, também projete estruturas para representar os vários tipos de exceções que podem ocorrer dentro de um serviço que se pode desejar transmitir a um cliente.  
  
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
  
 Dê a essas classes a capacidade de serializar-se ao XML:  
  
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
  
 As classes podem então ser usadas para <xref:System.Web.Services.Protocols.SoapException> fornecer os detalhes para instâncias explicitamente jogadas:  
  
```csharp  
AnticipatedException exception = new AnticipatedException();  
exception.AnticipatedExceptionInformation = "…";  
throw new SoapException(  
     "Fault occurred",  
     SoapException.ClientFaultCode,  
     Context.Request.Url.AbsoluteUri,  
     exception.ToXML());  
```  
  
 Essas classes de exceção serão facilmente utilizáveis com a classe WCF <xref:System.ServiceModel.FaultException%601> para lançar um novo`FaultException<AnticipatedException>(anticipatedException);`  
  
## <a name="security"></a>Segurança  
 A seguir, algumas recomendações de segurança.  
  
- Evite usar ASP.NET perfis 2.0, pois usá-los restringiria o uso de ASP.NET Modo de Integração se o serviço fosse migrado para o WCF.  
  
- Evite usar ACLs para controlar o acesso aos serviços, já que ASP.NET serviços da Web suportam ACLs usando Serviços de Informação da Internet (IIS), o WCF não — porque ASP.NET serviços da Web dependem do IIS para hospedagem, e o WCF não precisa necessariamente ser hospedado no IIS.  
  
- Considere usar ASP.NET Provedores de Papel 2.0 para autorizar o acesso aos recursos de um serviço.  
  
## <a name="see-also"></a>Confira também

- [Antecipando a adoção do Windows Communication Foundation: facilitando a futura integração](../../../../docs/framework/wcf/feature-details/anticipating-adopting-the-wcf-easing-future-integration.md)
