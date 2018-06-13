---
title: Como usar o ChannelFactory
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d48f01b5-582b-4c8b-b547-8adddae7e371
ms.openlocfilehash: b407c76c86c7b4c988da5280d76c91969c155841
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33491352"
---
# <a name="how-to-use-the-channelfactory"></a>Como usar o ChannelFactory
Genérica <xref:System.ServiceModel.ChannelFactory%601> classe é usada em cenários avançados que exigem a criação de uma fábrica de canais que pode ser usada para criar mais de um canal.  
  
### <a name="to-create-and-use-the-channelfactory-class"></a>Para criar e usar a classe ChannelFactory  
  
1.  Compilar e executar um serviço do Windows Communication Foundation (WCF). Para obter mais informações, consulte [Projetando e Implementando serviços](../../../../docs/framework/wcf/designing-and-implementing-services.md), [Configurando os serviços de](../../../../docs/framework/wcf/configuring-services.md), e [serviços de hospedagem](../../../../docs/framework/wcf/hosting-services.md).  
  
2.  Use o [Ferramenta Utilitária de metadados ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) para gerar o contrato (interface) para o cliente.  
  
3.  No código do cliente, use o <xref:System.ServiceModel.ChannelFactory%601> classe para criar vários ouvintes de ponto de extremidade.  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[c_HowToUseChannelFactory#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtousechannelfactory/cs/source.cs#1)]
 [!code-vb[c_HowToUseChannelFactory#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtousechannelfactory/vb/source.vb#1)]
