---
title: 'Antecipar a adoção do Windows Communication Foundation: facilitar a integração futura'
ms.date: 03/30/2017
ms.assetid: 3028bba8-6355-4ee0-9ecd-c56e614cb474
ms.openlocfilehash: c6e749c32947a4159d6bfd56c4d30a06f6ef0b7f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59316330"
---
# <a name="anticipating-adopting-the-windows-communication-foundation-easing-future-integration"></a>Antecipar a adoção do Windows Communication Foundation: facilitar a integração futura
Se você usa o ASP.NET e antecipa o uso do WCF no futuro, este tópico fornece diretrizes para garantir que novos serviços Web do ASP.NET funcione bem junto com os aplicativos do WCF.  
  
## <a name="general-recommendations"></a>Recomendações gerais  
 Adote o ASP.NET 2.0 para todos os novos serviços. Isso fornecerá acesso aos aprimoramentos e melhorias da nova versão. No entanto, ela também permitirá a possibilidade de usar componentes do ASP.NET 2.0 em conjunto com os componentes do WCF no mesmo aplicativo.  
  
## <a name="protocols"></a>Protocolos  
 Usar o novo recurso do ASP.NET 2.0 para validar a conformidade com o WS-I Basic Profile 1.1:  
  
```csharp  
[WebService(Namespace = "http://tempuri.org/")]  
[WebServiceBinding(  
     ConformsTo = WsiProfiles.BasicProfile1_1,  
     EmitConformanceClaims=true)]  
public interface IEcho  
```  
  
 Serviços Web do ASP.NET que estão em conformidade com WS-I Basic Profile 1.1 ser interoperável com clientes do WCF usando o WCF predefinido de associação, <xref:System.ServiceModel.BasicHttpBinding>.  
  
## <a name="service-development"></a>Desenvolvimento do serviço  
 Evite usar o <xref:System.Web.Services.Protocols.SoapDocumentServiceAttribute> atributo para que as mensagens roteadas para métodos com base no nome totalmente qualificado do elemento de corpo de mensagem SOAP em vez do cabeçalho HTTP SOAPAction. O WCF usa o cabeçalho HTTP SOAPAction para roteamento de mensagens.  
  
## <a name="data-representation"></a>Representação de dados  
 O XML no qual <xref:System.Xml.Serialization.XmlSerializer> serializa um tipo por padrão é semanticamente idêntico ao XML em que o <xref:System.Runtime.Serialization.DataContractSerializer> serializa um tipo, desde que o namespace para o XML seja explicitamente definido. Ao definir um tipo de dados para uso com serviços Web do ASP.NET em antecipação a adoção do WCF no futuro, faça o seguinte:  
  
1. Defina o tipo usando classes do .NET Framework em vez de esquema XML.  
  
2. Adicione somente as <xref:System.SerializableAttribute> e o <xref:System.Xml.Serialization.XmlRootAttribute> à classe, usando o último para definir explicitamente o namespace para o tipo. Fazer sem adicionar outros atributos do <xref:System.Xml.Serialization> namespace para controlar como a classe do .NET Framework deve ser convertido em XML.  
  
 Ao adotar essa abordagem, você deve ser capaz de fazer mais tarde as classes do .NET em contratos de dados com a adição do <xref:System.Runtime.Serialization.DataContractAttribute> e <xref:System.Runtime.Serialization.DataMemberAttribute> sem alterar significativamente o XML no qual as classes são serializadas para transmissão. Os tipos usados nas mensagens por serviços Web do ASP.NET poderá ser processado como contratos de dados por aplicativos do WCF, produzindo, entre outros benefícios, melhor desempenho em aplicativos do WCF.  
  
## <a name="security"></a>Segurança  
 Evite usar as opções de autenticação fornecidas pelo Internet Information Services (IIS). Clientes do WCF não oferecem suporte a isso. Se um serviço precisa ser protegido, use as opções fornecidas pelo WCF, porque essas opções são mais sofisticadas e se baseiam nos protocolos padrão.  
  
## <a name="see-also"></a>Consulte também

- [Antecipando a adoção do Windows Communication Foundation: Facilitando a migração futura](../../../../docs/framework/wcf/feature-details/anticipating-adopting-wcf-migration.md)
