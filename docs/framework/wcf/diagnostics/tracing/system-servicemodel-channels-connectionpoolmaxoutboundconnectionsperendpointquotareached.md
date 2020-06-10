---
title: Microsoft.Transactions.TransactionBridge.EnlistTransactionFailure
ms.date: 03/30/2017
ms.assetid: 1b9f5139-e122-4716-9ef7-2f38e1813993
ms.openlocfilehash: 742e80a3115e8f8caa728e0d8c460ee8b964ddc9
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84588711"
---
# <a name="microsofttransactionstransactionbridgeenlisttransactionfailure"></a><span data-ttu-id="34b0a-102">Microsoft.Transactions.TransactionBridge.EnlistTransactionFailure</span><span class="sxs-lookup"><span data-stu-id="34b0a-102">Microsoft.Transactions.TransactionBridge.EnlistTransactionFailure</span></span>
<span data-ttu-id="34b0a-103">Falha do serviço de protocolo WS-AT ao inscrever-se em uma transação usando o contexto de coordenação fornecido.</span><span class="sxs-lookup"><span data-stu-id="34b0a-103">The WS-AT protocol service failed to enlist on a transaction using the provided coordination context.</span></span>  
  
## <a name="description"></a><span data-ttu-id="34b0a-104">Descrição</span><span class="sxs-lookup"><span data-stu-id="34b0a-104">Description</span></span>  
 <span data-ttu-id="34b0a-105">Rastreado quando o MSDTC não pode se inscrever em uma transação para um determinado protocolo 2PC.</span><span class="sxs-lookup"><span data-stu-id="34b0a-105">Traced when MSDTC is unable to enlist on a transaction for a given 2pc protocol.</span></span>  <span data-ttu-id="34b0a-106">Isso pode acontecer porque a transação não existe mais, a lista de inlistagem não é mais permitida ou muitas inlistagens já estão presentes.</span><span class="sxs-lookup"><span data-stu-id="34b0a-106">This can happen because the transaction no longer exists, enlisting is no longer allowed, or too many enlistments are already present.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="34b0a-107">Solução de problemas</span><span class="sxs-lookup"><span data-stu-id="34b0a-107">Troubleshooting</span></span>  
 <span data-ttu-id="34b0a-108">Inspecione a cadeia de caracteres de status na mensagem de rastreamento para determinar se existe algum item acionável.</span><span class="sxs-lookup"><span data-stu-id="34b0a-108">Inspect the status string within the trace message to determine if any actionable item exists.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34b0a-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="34b0a-109">See also</span></span>

- [<span data-ttu-id="34b0a-110">Rastreamento</span><span class="sxs-lookup"><span data-stu-id="34b0a-110">Tracing</span></span>](index.md)
- [<span data-ttu-id="34b0a-111">Utilizando o rastreamento para solucionar problemas em seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="34b0a-111">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="34b0a-112">Administração e diagnóstico</span><span class="sxs-lookup"><span data-stu-id="34b0a-112">Administration and Diagnostics</span></span>](../index.md)
