---
title: Microsoft.Transactions.TransactionBridge.EnlistTransactionFailure
ms.date: 03/30/2017
ms.assetid: 1b9f5139-e122-4716-9ef7-2f38e1813993
ms.openlocfilehash: 93c96d94aaeddeb7e7b04ea80645b8de95b0343e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61666788"
---
# <a name="microsofttransactionstransactionbridgeenlisttransactionfailure"></a><span data-ttu-id="3008e-102">Microsoft.Transactions.TransactionBridge.EnlistTransactionFailure</span><span class="sxs-lookup"><span data-stu-id="3008e-102">Microsoft.Transactions.TransactionBridge.EnlistTransactionFailure</span></span>
<span data-ttu-id="3008e-103">O serviço de protocolo WS-AT não conseguiu se inscrever em uma transação usando o contexto de coordenação fornecido.</span><span class="sxs-lookup"><span data-stu-id="3008e-103">The WS-AT protocol service failed to enlist on a transaction using the provided coordination context.</span></span>  
  
## <a name="description"></a><span data-ttu-id="3008e-104">Descrição</span><span class="sxs-lookup"><span data-stu-id="3008e-104">Description</span></span>  
 <span data-ttu-id="3008e-105">Rastreada quando o MSDTC não é capaz de se inscrever em uma transação para um protocolo 2pc determinado.</span><span class="sxs-lookup"><span data-stu-id="3008e-105">Traced when MSDTC is unable to enlist on a transaction for a given 2pc protocol.</span></span>  <span data-ttu-id="3008e-106">Isso pode acontecer porque a transação não existe mais, a inscrição não é mais permitida ou muitas inscrições já estão presentes.</span><span class="sxs-lookup"><span data-stu-id="3008e-106">This can happen because the transaction no longer exists, enlisting is no longer allowed, or too many enlistments are already present.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="3008e-107">Solução de problemas</span><span class="sxs-lookup"><span data-stu-id="3008e-107">Troubleshooting</span></span>  
 <span data-ttu-id="3008e-108">Inspecione a cadeia de caracteres de status dentro da mensagem de rastreamento para determinar se há qualquer item acionável.</span><span class="sxs-lookup"><span data-stu-id="3008e-108">Inspect the status string within the trace message to determine if any actionable item exists.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3008e-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3008e-109">See also</span></span>

- [<span data-ttu-id="3008e-110">Rastreamento</span><span class="sxs-lookup"><span data-stu-id="3008e-110">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="3008e-111">Usando o rastreamento para solucionar problemas do seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="3008e-111">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="3008e-112">Administração e diagnósticos</span><span class="sxs-lookup"><span data-stu-id="3008e-112">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
