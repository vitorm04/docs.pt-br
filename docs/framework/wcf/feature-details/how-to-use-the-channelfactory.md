---
title: 'Como: usar o ChannelFactory'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d48f01b5-582b-4c8b-b547-8adddae7e371
ms.openlocfilehash: 7d542a3dcae514e75194b49c23a8dec5dd7e8c3b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59773721"
---
# <a name="how-to-use-the-channelfactory"></a><span data-ttu-id="1ff84-102">Como: usar o ChannelFactory</span><span class="sxs-lookup"><span data-stu-id="1ff84-102">How to: Use the ChannelFactory</span></span>
<span data-ttu-id="1ff84-103">Genérica <xref:System.ServiceModel.ChannelFactory%601> classe é usada em cenários avançados que exigem a criação de uma fábrica de canais que pode ser usada para criar mais de um canal.</span><span class="sxs-lookup"><span data-stu-id="1ff84-103">The generic <xref:System.ServiceModel.ChannelFactory%601> class is used in advanced scenarios that require the creation of a channel factory that can be used to create more than one channel.</span></span>  
  
### <a name="to-create-and-use-the-channelfactory-class"></a><span data-ttu-id="1ff84-104">Para criar e usar a classe ChannelFactory</span><span class="sxs-lookup"><span data-stu-id="1ff84-104">To create and use the ChannelFactory class</span></span>  
  
1. <span data-ttu-id="1ff84-105">Compilar e executar um serviço do Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="1ff84-105">Build and run an Windows Communication Foundation (WCF) service.</span></span> <span data-ttu-id="1ff84-106">Para obter mais informações, consulte [Projetando e Implementando serviços](../../../../docs/framework/wcf/designing-and-implementing-services.md), [Configurando os serviços](../../../../docs/framework/wcf/configuring-services.md), e [serviços de hospedagem](../../../../docs/framework/wcf/hosting-services.md).</span><span class="sxs-lookup"><span data-stu-id="1ff84-106">For more information, see [Designing and Implementing Services](../../../../docs/framework/wcf/designing-and-implementing-services.md), [Configuring Services](../../../../docs/framework/wcf/configuring-services.md), and [Hosting Services](../../../../docs/framework/wcf/hosting-services.md).</span></span>  
  
2. <span data-ttu-id="1ff84-107">Use o [ferramenta de utilitário de metadados ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) para gerar o contrato (interface) para o cliente.</span><span class="sxs-lookup"><span data-stu-id="1ff84-107">Use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to generate the contract (interface) for the client.</span></span>  
  
3. <span data-ttu-id="1ff84-108">No código do cliente, use o <xref:System.ServiceModel.ChannelFactory%601> classe para criar vários ouvintes do ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="1ff84-108">In the client code, use the <xref:System.ServiceModel.ChannelFactory%601> class to create multiple endpoint listeners.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1ff84-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1ff84-109">Example</span></span>  
 [!code-csharp[c_HowToUseChannelFactory#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtousechannelfactory/cs/source.cs#1)]
 [!code-vb[c_HowToUseChannelFactory#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtousechannelfactory/vb/source.vb#1)]
