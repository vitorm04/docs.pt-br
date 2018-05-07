---
title: 'Antecipando a adoção do Windows Communication Foundation: facilitando a futura integração'
ms.date: 03/30/2017
ms.assetid: 3028bba8-6355-4ee0-9ecd-c56e614cb474
ms.openlocfilehash: f81e158a5e7f897307c0c6d376dfe01dac127ead
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="anticipating-adopting-the-windows-communication-foundation-easing-future-integration"></a>Antecipando a adoção do Windows Communication Foundation: facilitando a futura integração
Se você usa o ASP.NET e prever usando o WCF no futuro, este tópico fornece diretrizes para garantir que os novos serviços da Web do ASP.NET funcionará bem com aplicativos do WCF.  
  
## <a name="general-recommendations"></a>Recomendações gerais  
 Adote o ASP.NET 2.0 para quaisquer novos serviços. Isso fornecerá acesso aos aprimoramentos e melhorias da nova versão. No entanto, ele também permitirá a possibilidade de usar o ASP.NET 2.0 componentes junto com os componentes do WCF no mesmo aplicativo.  
  
## <a name="protocols"></a>Protocolos  
 Use o recurso novo do ASP.NET 2.0 para validar a conformidade com o WS-I Basic Profile 1.1:  
  
```  
[WebService(Namespace = "http://tempuri.org/")]  
[WebServiceBinding(  
     ConformsTo = WsiProfiles.BasicProfile1_1,  
     EmitConformanceClaims=true)]  
public interface IEcho  
```  
  
 Serviços Web do ASP.NET que estão de acordo com WS-I Basic Profile 1.1 será interoperável com clientes do WCF usando o WCF predefinido de associação, <xref:System.ServiceModel.BasicHttpBinding>.  
  
## <a name="service-development"></a>Desenvolvimento do serviço  
 Evite usar o <xref:System.Web.Services.Protocols.SoapDocumentServiceAttribute> atributo para que as mensagens roteadas para os métodos com base no nome totalmente qualificado do elemento de corpo de mensagem SOAP em vez de um cabeçalho HTTP SOAPAction. WCF usa o cabeçalho HTTP SOAPAction para roteamento de mensagens.  
  
## <a name="data-representation"></a>Representação de dados  
 O XML no qual <xref:System.Xml.Serialization.XmlSerializer> serializa um tipo por padrão é semanticamente idêntico ao XML no qual o <xref:System.Runtime.Serialization.DataContractSerializer> serializa um tipo, fornecido o namespace para o XML é definido explicitamente. Ao definir um tipo de dados para uso com serviços Web do ASP.NET em antecipação a adoção do WCF no futuro, faça o seguinte:  
  
1.  Defina o tipo usando classes do .NET Framework em vez de esquema XML.  
  
2.  Adicione somente o <xref:System.SerializableAttribute> e <xref:System.Xml.Serialization.XmlRootAttribute> para a classe usando o último definir explicitamente o namespace para o tipo. Fazer sem adicionar atributos adicionais do <xref:System.Xml.Serialization> namespace para controlar como a classe do .NET Framework é para ser convertido em XML.  
  
 Ao adotar essa abordagem, você deve ser capaz de fazer mais tarde as classes do .NET em contratos de dados com a adição do <xref:System.Runtime.Serialization.DataContractAttribute> e <xref:System.Runtime.Serialization.DataMemberAttribute> sem alterar significativamente o XML no qual as classes são serializadas para transmissão. Os tipos usados em mensagens, serviços Web ASP.NET poderão ser processados como contratos de dados por aplicativos do WCF, gerando, entre outros benefícios, melhor desempenho em aplicativos do WCF.  
  
## <a name="security"></a>Segurança  
 Evite usar as opções de autenticação fornecidas pelo Internet Information Services (IIS). Clientes do WCF não dão suporte a eles. Se um serviço precisa ser protegido, use as opções fornecidas pelo WCF, porque essas opções são mais sofisticadas e baseadas em protocolos padrão.  
  
## <a name="see-also"></a>Consulte também  
 [Antecipando a adoção do Windows Communication Foundation: facilitando a migração futura](../../../../docs/framework/wcf/feature-details/anticipating-adopting-wcf-migration.md)
