---
title: System.ServiceModel.MessageProcessingPaused
ms.date: 03/30/2017
ms.assetid: 36b5302a-93cc-478a-9bb2-8a1601fba1df
ms.openlocfilehash: 85bec8255e0d20d6e76ea354e5b8c42b83d7d8e6
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84598145"
---
# <a name="systemservicemodelmessageprocessingpaused"></a><span data-ttu-id="2b393-102">System.ServiceModel.MessageProcessingPaused</span><span class="sxs-lookup"><span data-stu-id="2b393-102">System.ServiceModel.MessageProcessingPaused</span></span>
<span data-ttu-id="2b393-103">System.ServiceModel.MessageProcessingPaused</span><span class="sxs-lookup"><span data-stu-id="2b393-103">System.ServiceModel.MessageProcessingPaused</span></span>  
  
## <a name="description"></a><span data-ttu-id="2b393-104">Descrição</span><span class="sxs-lookup"><span data-stu-id="2b393-104">Description</span></span>  
 <span data-ttu-id="2b393-105">Os threads foram alternados durante o processamento de uma mensagem.</span><span class="sxs-lookup"><span data-stu-id="2b393-105">The threads were switched while processing a message.</span></span>  
  
 <span data-ttu-id="2b393-106">O processamento de mensagens pode ser pausado pelos seguintes motivos:</span><span class="sxs-lookup"><span data-stu-id="2b393-106">Message processing can be paused by the following reasons:</span></span>  
  
- <span data-ttu-id="2b393-107">ConcurrencyMode é Single ou reentrante e o serviço está processando outra mensagem.</span><span class="sxs-lookup"><span data-stu-id="2b393-107">ConcurrencyMode is single or reentrant, and the service is processing another message.</span></span>  
  
- <span data-ttu-id="2b393-108">A transação está habilitada e o serviço está processando outra transação.</span><span class="sxs-lookup"><span data-stu-id="2b393-108">Transaction is enabled and the service is processing another transaction.</span></span>  
  
- <span data-ttu-id="2b393-109">O contexto de sincronização não é atual.</span><span class="sxs-lookup"><span data-stu-id="2b393-109">Synchronization context is not current.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b393-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2b393-110">See also</span></span>

- [<span data-ttu-id="2b393-111">Rastreamento</span><span class="sxs-lookup"><span data-stu-id="2b393-111">Tracing</span></span>](index.md)
- [<span data-ttu-id="2b393-112">Utilizando o rastreamento para solucionar problemas em seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="2b393-112">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="2b393-113">Administração e diagnóstico</span><span class="sxs-lookup"><span data-stu-id="2b393-113">Administration and Diagnostics</span></span>](../index.md)
