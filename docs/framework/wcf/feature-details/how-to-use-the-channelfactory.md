---
title: Como usar o ChannelFactory
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: d48f01b5-582b-4c8b-b547-8adddae7e371
caps.latest.revision: 14
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a076fb5b95c6750e6352235490b4e2e9ab883bbe
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2018
---
# <a name="how-to-use-the-channelfactory"></a>Como usar o ChannelFactory
Genérica <xref:System.ServiceModel.ChannelFactory%601> classe é usada em cenários avançados que exigem a criação de uma fábrica de canais que pode ser usada para criar mais de um canal.  
  
### <a name="to-create-and-use-the-channelfactory-class"></a>Para criar e usar a classe ChannelFactory  
  
1.  Compilar e executar um [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] serviço. Para obter mais informações, consulte [Projetando e Implementando serviços](../../../../docs/framework/wcf/designing-and-implementing-services.md), [Configurando os serviços de](../../../../docs/framework/wcf/configuring-services.md), e [serviços de hospedagem](../../../../docs/framework/wcf/hosting-services.md).  
  
2.  Use o [Ferramenta Utilitária de metadados ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) para gerar o contrato (interface) para o cliente.  
  
3.  No código do cliente, use o <xref:System.ServiceModel.ChannelFactory%601> classe para criar vários ouvintes de ponto de extremidade.  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[c_HowToUseChannelFactory#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtousechannelfactory/cs/source.cs#1)]
 [!code-vb[c_HowToUseChannelFactory#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtousechannelfactory/vb/source.vb#1)]
