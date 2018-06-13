---
title: Microsoft.Transactions.TransactionBridge.EnlistTransactionFailure
ms.date: 03/30/2017
ms.assetid: 1b9f5139-e122-4716-9ef7-2f38e1813993
ms.openlocfilehash: 9dd2ba5a3e94ff794d4b8a8775944355b105f790
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33482002"
---
# <a name="microsofttransactionstransactionbridgeenlisttransactionfailure"></a><span data-ttu-id="d1b79-102">Microsoft.Transactions.TransactionBridge.EnlistTransactionFailure</span><span class="sxs-lookup"><span data-stu-id="d1b79-102">Microsoft.Transactions.TransactionBridge.EnlistTransactionFailure</span></span>
<span data-ttu-id="d1b79-103">O serviço de protocolo WS-AT não conseguiu se inscrever em uma transação usando o contexto de coordenação fornecido.</span><span class="sxs-lookup"><span data-stu-id="d1b79-103">The WS-AT protocol service failed to enlist on a transaction using the provided coordination context.</span></span>  
  
## <a name="description"></a><span data-ttu-id="d1b79-104">Descrição</span><span class="sxs-lookup"><span data-stu-id="d1b79-104">Description</span></span>  
 <span data-ttu-id="d1b79-105">Rastreada quando MSDTC não pode se inscrever em uma transação para um protocolo 2pc determinado.</span><span class="sxs-lookup"><span data-stu-id="d1b79-105">Traced when MSDTC is unable to enlist on a transaction for a given 2pc protocol.</span></span>  <span data-ttu-id="d1b79-106">Isso pode acontecer porque a transação não existe mais, inscrição não é mais permitido ou muitas inscrições já estão presentes.</span><span class="sxs-lookup"><span data-stu-id="d1b79-106">This can happen because the transaction no longer exists, enlisting is no longer allowed, or too many enlistments are already present.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="d1b79-107">Solução de problemas</span><span class="sxs-lookup"><span data-stu-id="d1b79-107">Troubleshooting</span></span>  
 <span data-ttu-id="d1b79-108">Verifique se a cadeia de caracteres de status dentro da mensagem de rastreamento para determinar se há qualquer item acionável.</span><span class="sxs-lookup"><span data-stu-id="d1b79-108">Inspect the status string within the trace message to determine if any actionable item exists.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1b79-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d1b79-109">See Also</span></span>  
 [<span data-ttu-id="d1b79-110">Rastreamento</span><span class="sxs-lookup"><span data-stu-id="d1b79-110">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="d1b79-111">Usando o rastreamento para solucionar problemas do seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="d1b79-111">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="d1b79-112">Administração e diagnósticos</span><span class="sxs-lookup"><span data-stu-id="d1b79-112">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
