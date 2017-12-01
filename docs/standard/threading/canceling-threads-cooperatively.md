---
title: Cancelando threads de forma cooperativa
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: threads, cancellation
ms.assetid: d2d6d5fd-e263-4fa0-847b-2fc3e0d82337
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 482f48b347af1a4f76231abcb15abc2f4dba168b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="canceling-threads-cooperatively"></a>Cancelando threads de forma cooperativa
Antes do [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], o .NET Framework não fornecido nenhum modo interno para cancelar um thread de forma cooperativa depois que ele foi iniciado. No entanto, em [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], você pode usar tokens de cancelamento para cancelar threads, assim como você pode usá-los para cancelar <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> consultas PLINQ ou objetos. Embora o <xref:System.Threading.Thread?displayProperty=nameWithType> classe não oferece suporte interno para tokens de cancelamento, você pode passar um token para um procedimento de thread usando o <xref:System.Threading.Thread> construtor que usa um <xref:System.Threading.ParameterizedThreadStart> delegate. O exemplo a seguir demonstra como fazer isso.  
  
 [!code-csharp[Cancellation#14](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/CooperativeThreads.cs#14)]
 [!code-vb[Cancellation#14](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/CooperativeThreads.vb#14)]  
  
## <a name="see-also"></a>Consulte também  
 [Usando threads e threading](../../../docs/standard/threading/using-threads-and-threading.md)
