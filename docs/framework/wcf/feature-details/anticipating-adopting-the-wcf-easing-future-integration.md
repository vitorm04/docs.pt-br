---
title: "Antecipando a adoção do Windows Communication Foundation: facilitando a futura integração"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3028bba8-6355-4ee0-9ecd-c56e614cb474
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ccf6e5363da872d3902c12713bd19f5820370428
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="anticipating-adopting-the-windows-communication-foundation-easing-future-integration"></a>Antecipando a adoção do Windows Communication Foundation: facilitando a futura integração
Se você usar o ASP.NET e prever usando [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] no futuro, este tópico fornece diretrizes para garantir que novos serviços da Web do ASP.NET funciona bem junto com [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplicativos.  
  
## <a name="general-recommendations"></a>Recomendações gerais  
 Adote o ASP.NET 2.0 para quaisquer novos serviços. Isso fornecerá acesso aos aprimoramentos e melhorias da nova versão. No entanto, ele também permitirá a possibilidade de usar o ASP.NET 2.0 componentes junto com [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] componentes no mesmo aplicativo.  
  
## <a name="protocols"></a>Protocolos  
 Use o recurso novo do ASP.NET 2.0 para validar a conformidade com o WS-I Basic Profile 1.1:  
  
```  
[WebService(Namespace = "http://tempuri.org/")]  
[WebServiceBinding(  
     ConformsTo = WsiProfiles.BasicProfile1_1,  
     EmitConformanceClaims=true)]  
public interface IEcho  
```  
  
 Serviços Web do ASP.NET que estão de acordo com WS-I Basic Profile 1.1 será interoperável com [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] clientes usando [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] predefinidos de associação, <xref:System.ServiceModel.BasicHttpBinding>.  
  
## <a name="service-development"></a>Desenvolvimento do serviço  
 Evite usar o <xref:System.Web.Services.Protocols.SoapDocumentServiceAttribute> atributo para que as mensagens roteadas para os métodos com base no nome totalmente qualificado do elemento de corpo de mensagem SOAP em vez de um cabeçalho HTTP SOAPAction. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]usa o cabeçalho HTTP SOAPAction para roteamento de mensagens.  
  
## <a name="data-representation"></a>Representação de dados  
 O XML no qual <xref:System.Xml.Serialization.XmlSerializer> serializa um tipo por padrão é semanticamente idêntico ao XML no qual o <xref:System.Runtime.Serialization.DataContractSerializer> serializa um tipo, fornecido o namespace para o XML é definido explicitamente. Quando definir um tipo de dados para uso com o ASP.NET Web services antecipadamente adotando [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] no futuro, faça o seguinte:  
  
1.  Defina o tipo usando classes do .NET Framework em vez de esquema XML.  
  
2.  Adicione somente o <xref:System.SerializableAttribute> e <xref:System.Xml.Serialization.XmlRootAttribute> para a classe usando o último definir explicitamente o namespace para o tipo. Fazer sem adicionar atributos adicionais do <xref:System.Xml.Serialization> namespace para controlar como a classe do .NET Framework é para ser convertido em XML.  
  
 Ao adotar essa abordagem, você deve ser capaz de fazer mais tarde as classes do .NET em contratos de dados com a adição do <xref:System.Runtime.Serialization.DataContractAttribute> e <xref:System.Runtime.Serialization.DataMemberAttribute> sem alterar significativamente o XML no qual as classes são serializadas para transmissão. Os tipos usados em mensagens, serviços Web ASP.NET poderão ser processados como contratos de dados por [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplicativos, gerando, entre outros benefícios, melhor desempenho em [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplicativos.  
  
## <a name="security"></a>Segurança  
 Evite usar as opções de autenticação fornecidas pelo Internet Information Services (IIS). [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]os clientes não dão suporte a eles. Se um serviço precisa ser protegido, use as opções fornecidas por [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], porque essas opções são mais sofisticadas e baseadas em protocolos padrão.  
  
## <a name="see-also"></a>Consulte também  
 [Antecipando a adoção do Windows Communication Foundation: facilitando a migração futura](../../../../docs/framework/wcf/feature-details/anticipating-adopting-wcf-migration.md)
