---
title: Microsoft.Transactions.TransactionBridge.CoordinatorStateMachineFinished
ms.date: 03/30/2017
ms.assetid: 16cb428d-d886-4789-a961-6fded4b0dbba
ms.openlocfilehash: 3b9a3703e49c3932f62fcfb6994c9028b074bbe8
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84594407"
---
# <a name="microsofttransactionstransactionbridgecoordinatorstatemachinefinished"></a><span data-ttu-id="830d1-102">Microsoft.Transactions.TransactionBridge.CoordinatorStateMachineFinished</span><span class="sxs-lookup"><span data-stu-id="830d1-102">Microsoft.Transactions.TransactionBridge.CoordinatorStateMachineFinished</span></span>
<span data-ttu-id="830d1-103">A máquina de estado para uma inscrição de coordenador entrou no estado concluído.</span><span class="sxs-lookup"><span data-stu-id="830d1-103">The state machine for a coordinator enlistment has entered the finished state.</span></span>  
  
## <a name="description"></a><span data-ttu-id="830d1-104">Descrição</span><span class="sxs-lookup"><span data-stu-id="830d1-104">Description</span></span>  
 <span data-ttu-id="830d1-105">Rastreado quando o Gerenciador de transações local acredita que uma inscrição de coordenador superior concluiu o processamento de 2pc.</span><span class="sxs-lookup"><span data-stu-id="830d1-105">Traced when the local Transaction Manager believes a superior coordinator enlistment has completed 2pc processing.</span></span> <span data-ttu-id="830d1-106">O resultado da inscrição pode ser confirmado ou anulado ou esquecido.</span><span class="sxs-lookup"><span data-stu-id="830d1-106">The outcome for the enlistment can be Committed or Aborted or Forgotten.</span></span> <span data-ttu-id="830d1-107">Ele também será rastreado se o Gerenciador de transações local votar em ReadOnly durante a preparação.</span><span class="sxs-lookup"><span data-stu-id="830d1-107">It is also traced if the local Transaction Manager votes ReadOnly during Prepare.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="830d1-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="830d1-108">See also</span></span>

- [<span data-ttu-id="830d1-109">Rastreamento</span><span class="sxs-lookup"><span data-stu-id="830d1-109">Tracing</span></span>](index.md)
- [<span data-ttu-id="830d1-110">Utilizando o rastreamento para solucionar problemas em seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="830d1-110">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="830d1-111">Administração e diagnóstico</span><span class="sxs-lookup"><span data-stu-id="830d1-111">Administration and Diagnostics</span></span>](../index.md)
