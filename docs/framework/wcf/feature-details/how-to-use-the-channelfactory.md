---
title: Como usar o ChannelFactory
description: Saiba como criar uma fábrica de canais para criar mais de um canal para acessar serviços usando um cliente WCF.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d48f01b5-582b-4c8b-b547-8adddae7e371
ms.openlocfilehash: 7c87026ca4cf7c739f4615da9bc7f0272a382392
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85246656"
---
# <a name="how-to-use-the-channelfactory"></a><span data-ttu-id="80da9-103">Como usar o ChannelFactory</span><span class="sxs-lookup"><span data-stu-id="80da9-103">How to: Use the ChannelFactory</span></span>
<span data-ttu-id="80da9-104">A <xref:System.ServiceModel.ChannelFactory%601> classe genérica é usada em cenários avançados que exigem a criação de uma fábrica de canais que pode ser usada para criar mais de um canal.</span><span class="sxs-lookup"><span data-stu-id="80da9-104">The generic <xref:System.ServiceModel.ChannelFactory%601> class is used in advanced scenarios that require the creation of a channel factory that can be used to create more than one channel.</span></span>  
  
### <a name="to-create-and-use-the-channelfactory-class"></a><span data-ttu-id="80da9-105">Para criar e usar a classe ChannelFactory</span><span class="sxs-lookup"><span data-stu-id="80da9-105">To create and use the ChannelFactory class</span></span>  
  
1. <span data-ttu-id="80da9-106">Compilar e executar um serviço de Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="80da9-106">Build and run an Windows Communication Foundation (WCF) service.</span></span> <span data-ttu-id="80da9-107">Para obter mais informações, consulte [projetando e implementando](../designing-and-implementing-services.md)serviços, [Configurando serviços](../configuring-services.md)e [hospedando serviços](../hosting-services.md).</span><span class="sxs-lookup"><span data-stu-id="80da9-107">For more information, see [Designing and Implementing Services](../designing-and-implementing-services.md), [Configuring Services](../configuring-services.md), and [Hosting Services](../hosting-services.md).</span></span>  
  
2. <span data-ttu-id="80da9-108">Use a [ferramenta de utilitário de metadados ServiceModel (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) para gerar o contrato (interface) para o cliente.</span><span class="sxs-lookup"><span data-stu-id="80da9-108">Use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) to generate the contract (interface) for the client.</span></span>  
  
3. <span data-ttu-id="80da9-109">No código do cliente, use a <xref:System.ServiceModel.ChannelFactory%601> classe para criar vários ouvintes de ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="80da9-109">In the client code, use the <xref:System.ServiceModel.ChannelFactory%601> class to create multiple endpoint listeners.</span></span>  
  
## <a name="example"></a><span data-ttu-id="80da9-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="80da9-110">Example</span></span>  
 [!code-csharp[c_HowToUseChannelFactory#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtousechannelfactory/cs/source.cs#1)]
 [!code-vb[c_HowToUseChannelFactory#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtousechannelfactory/vb/source.vb#1)]
