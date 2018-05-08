---
title: Serialização e transferência de dados
ms.date: 03/30/2017
helpviewer_keywords:
- data serialization [WCF]
- data transfer [WCF]
ms.assetid: 0f03c635-f3e7-4c5c-9463-3cb0135e221e
ms.openlocfilehash: 53c1421bf14c598611e116c61353c4ecd465f1aa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="data-transfer-and-serialization"></a>Serialização e transferência de dados
Em um sistema conectado, o clientes e serviços dependem da troca de dados para realizar qualquer tarefa. Como desenvolvedor de um serviço ou cliente, você também deve entender como o Windows Communication Foundation (WCF) controla a serialização de dados e dados para criar aplicativos que são eficiente e fácil de manter.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Especificando transferência de dados em contratos de serviço](../../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md)  
 Descreve os conceitos básicos de transferência de dados nos serviços.  
  
 [Usando contratos de dados](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)  
 Descreve contratos de dados que são e como criar e usá-los.  
  
 [Serializador de contrato de dados](../../../../docs/framework/wcf/feature-details/data-contract-serializer.md)  
 Descreve como realizar a serialização de dados com o <xref:System.Runtime.Serialization.DataContractSerializer> classe ou qualquer extensão do <xref:System.Runtime.Serialization.XmlObjectSerializer> classe.  
  
 [Usando a classe XmlSerializer](../../../../docs/framework/wcf/feature-details/using-the-xmlserializer-class.md)  
 Descreve como e por que usar o <xref:System.Xml.Serialization.XmlSerializer> classe, uma alternativa para o <xref:System.Runtime.Serialization.DataContractSerializer> classe.  
  
 [Usando contratos de mensagem](../../../../docs/framework/wcf/feature-details/using-message-contracts.md)  
 Descreve como contratos de mensagem permitem controle refinado sobre mensagens SOAP.  
  
 [Usando a classe de mensagens](../../../../docs/framework/wcf/feature-details/using-the-message-class.md)  
 Descreve como usar recursos de classe de mensagem.  
  
 [Filtragem](../../../../docs/framework/wcf/feature-details/filtering.md)  
 Descreve a filtragem, que permite que o pré-processamento de uma mensagem com base em vários critérios.  
  
 [Dados grandes e streaming](../../../../docs/framework/wcf/feature-details/large-data-and-streaming.md)  
 Descreve como enviar um grande bloco de dados, como um arquivo binário.  
  
 [Considerações sobre segurança para dados](../../../../docs/framework/wcf/feature-details/security-considerations-for-data.md)  
 Descreve itens deve estar atento ao programar a serialização e transferência de dados.  
  
 [Visão geral da arquitetura de transferência de dados](../../../../docs/framework/wcf/feature-details/data-transfer-architectural-overview.md)  
 Descreve uma exibição do design geral de transferência de dados do WCF.  
  
## <a name="reference"></a>Referência  
 <xref:System.ServiceModel>  
  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
  
 <xref:System.Xml.Serialization.XmlSerializer>  
  
 <xref:System.Runtime.Serialization>  
  
 <xref:System.Xml.Serialization>  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Estendendo codificadores e serializadores](../../../../docs/framework/wcf/extending/extending-encoders-and-serializers.md)  
  
## <a name="see-also"></a>Consulte também  
 [Práticas recomendadas: controle de versão de contrato de dados](../../../../docs/framework/wcf/best-practices-data-contract-versioning.md)  
 [Controle de versão de serviço](../../../../docs/framework/wcf/service-versioning.md)
