---
title: Microsoft.Transactions.TransactionBridge.CoordinatorStateMachineFinished
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 16cb428d-d886-4789-a961-6fded4b0dbba
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 7c9a456e668560cb2172de80295b731a6103aa7a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="microsofttransactionstransactionbridgecoordinatorstatemachinefinished"></a><span data-ttu-id="44cc1-102">Microsoft.Transactions.TransactionBridge.CoordinatorStateMachineFinished</span><span class="sxs-lookup"><span data-stu-id="44cc1-102">Microsoft.Transactions.TransactionBridge.CoordinatorStateMachineFinished</span></span>
<span data-ttu-id="44cc1-103">A máquina de estado para uma inscrição de coordenador entrou no estado terminado.</span><span class="sxs-lookup"><span data-stu-id="44cc1-103">The state machine for a coordinator enlistment has entered the finished state.</span></span>  
  
## <a name="description"></a><span data-ttu-id="44cc1-104">Descrição</span><span class="sxs-lookup"><span data-stu-id="44cc1-104">Description</span></span>  
 <span data-ttu-id="44cc1-105">Rastreada quando o Gerenciador de transações local reconhece que uma inscrição de coordenador superior concluiu o processamento de 2pc.</span><span class="sxs-lookup"><span data-stu-id="44cc1-105">Traced when the local Transaction Manager believes a superior coordinator enlistment has completed 2pc processing.</span></span> <span data-ttu-id="44cc1-106">O resultado para a inscrição pode ser confirmado ou anulado ou Forgotten.</span><span class="sxs-lookup"><span data-stu-id="44cc1-106">The outcome for the enlistment can be Committed or Aborted or Forgotten.</span></span> <span data-ttu-id="44cc1-107">Se o Gerenciador de transações locais votos somente leitura durante a preparação também são rastreados.</span><span class="sxs-lookup"><span data-stu-id="44cc1-107">It is also traced if the local Transaction Manager votes ReadOnly during Prepare.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44cc1-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="44cc1-108">See Also</span></span>  
 [<span data-ttu-id="44cc1-109">Rastreamento</span><span class="sxs-lookup"><span data-stu-id="44cc1-109">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="44cc1-110">Usando o rastreamento para solucionar problemas de seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="44cc1-110">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 <span data-ttu-id="44cc1-111">[Administration and Diagnostics](../../../../../docs/framework/wcf/diagnostics/index.md) (Administração e diagnósticos)</span><span class="sxs-lookup"><span data-stu-id="44cc1-111">[Administration and Diagnostics](../../../../../docs/framework/wcf/diagnostics/index.md)</span></span>
