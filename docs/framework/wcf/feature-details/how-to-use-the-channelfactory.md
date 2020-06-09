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
# <a name="how-to-use-the-channelfactory"></a><span data-ttu-id="11092-102">Como usar o ChannelFactory</span><span class="sxs-lookup"><span data-stu-id="11092-102">How to: Use the ChannelFactory</span></span>
<span data-ttu-id="11092-103">A <xref:System.ServiceModel.ChannelFactory%601> classe genérica é usada em cenários avançados que exigem a criação de uma fábrica de canais que pode ser usada para criar mais de um canal.</span><span class="sxs-lookup"><span data-stu-id="11092-103">The generic <xref:System.ServiceModel.ChannelFactory%601> class is used in advanced scenarios that require the creation of a channel factory that can be used to create more than one channel.</span></span>  
  
### <a name="to-create-and-use-the-channelfactory-class"></a><span data-ttu-id="11092-104">Para criar e usar a classe ChannelFactory</span><span class="sxs-lookup"><span data-stu-id="11092-104">To create and use the ChannelFactory class</span></span>  
  
1. <span data-ttu-id="11092-105">Compilar e executar um serviço de Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="11092-105">Build and run an Windows Communication Foundation (WCF) service.</span></span> <span data-ttu-id="11092-106">Para obter mais informações, consulte [projetando e implementando](../designing-and-implementing-services.md)serviços, [Configurando serviços](../configuring-services.md)e [hospedando serviços](../hosting-services.md).</span><span class="sxs-lookup"><span data-stu-id="11092-106">For more information, see [Designing and Implementing Services](../designing-and-implementing-services.md), [Configuring Services](../configuring-services.md), and [Hosting Services](../hosting-services.md).</span></span>  
  
2. <span data-ttu-id="11092-107">Use a [ferramenta de utilitário de metadados ServiceModel (svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) para gerar o contrato (interface) para o cliente.</span><span class="sxs-lookup"><span data-stu-id="11092-107">Use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) to generate the contract (interface) for the client.</span></span>  
  
3. <span data-ttu-id="11092-108">No código do cliente, use a <xref:System.ServiceModel.ChannelFactory%601> classe para criar vários ouvintes de ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="11092-108">In the client code, use the <xref:System.ServiceModel.ChannelFactory%601> class to create multiple endpoint listeners.</span></span>  
  
## <a name="example"></a><span data-ttu-id="11092-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="11092-109">Example</span></span>  
 [!code-csharp[c_HowToUseChannelFactory#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtousechannelfactory/cs/source.cs#1)]
 [!code-vb[c_HowToUseChannelFactory#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtousechannelfactory/vb/source.vb#1)]
