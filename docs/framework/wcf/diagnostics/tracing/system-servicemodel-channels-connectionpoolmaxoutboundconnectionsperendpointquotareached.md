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
# <a name="microsofttransactionstransactionbridgeenlisttransactionfailure"></a>Microsoft.Transactions.TransactionBridge.EnlistTransactionFailure
O serviço de protocolo WS-AT não conseguiu se inscrever em uma transação usando o contexto de coordenação fornecido.  
  
## <a name="description"></a>Descrição  
 Rastreada quando MSDTC não pode se inscrever em uma transação para um protocolo 2pc determinado.  Isso pode acontecer porque a transação não existe mais, inscrição não é mais permitido ou muitas inscrições já estão presentes.  
  
## <a name="troubleshooting"></a>Solução de problemas  
 Verifique se a cadeia de caracteres de status dentro da mensagem de rastreamento para determinar se há qualquer item acionável.  
  
## <a name="see-also"></a>Consulte também  
 [Rastreamento](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [Usando o rastreamento para solucionar problemas do seu aplicativo](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [Administração e diagnósticos](../../../../../docs/framework/wcf/diagnostics/index.md)
