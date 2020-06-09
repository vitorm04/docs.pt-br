---
title: Como usar o ChannelFactory
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d48f01b5-582b-4c8b-b547-8adddae7e371
ms.openlocfilehash: 4bb2053fb50931756e79d5346a3f14d2acbe04f6
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84595304"
---
# <a name="how-to-use-the-channelfactory"></a>Como usar o ChannelFactory
A <xref:System.ServiceModel.ChannelFactory%601> classe genérica é usada em cenários avançados que exigem a criação de uma fábrica de canais que pode ser usada para criar mais de um canal.  
  
### <a name="to-create-and-use-the-channelfactory-class"></a>Para criar e usar a classe ChannelFactory  
  
1. Compilar e executar um serviço de Windows Communication Foundation (WCF). Para obter mais informações, consulte [projetando e implementando](../designing-and-implementing-services.md)serviços, [Configurando serviços](../configuring-services.md)e [hospedando serviços](../hosting-services.md).  
  
2. Use a [ferramenta de utilitário de metadados ServiceModel (svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) para gerar o contrato (interface) para o cliente.  
  
3. No código do cliente, use a <xref:System.ServiceModel.ChannelFactory%601> classe para criar vários ouvintes de ponto de extremidade.  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[c_HowToUseChannelFactory#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtousechannelfactory/cs/source.cs#1)]
 [!code-vb[c_HowToUseChannelFactory#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtousechannelfactory/vb/source.vb#1)]
