---
title: Cancelando threads de forma cooperativa
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- threads, cancellation
ms.assetid: d2d6d5fd-e263-4fa0-847b-2fc3e0d82337
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3edd0f9c991df8d8d70b14f4439c5c477e8f1401
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33581336"
---
# <a name="canceling-threads-cooperatively"></a>Cancelando threads de forma cooperativa
Antes do [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], o .NET Framework não fornecia uma maneira integrada de cancelar um thread de forma cooperativa após ele ter sido iniciado. No entanto, em [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], é possível usar tokens de cancelamento para cancelar threads, assim como você pode usá-los para cancelar consultas PLINQ ou objetos <xref:System.Threading.Tasks.Task?displayProperty=nameWithType>. Embora a classe <xref:System.Threading.Thread?displayProperty=nameWithType> não ofereça suporte interno para tokens de cancelamento, você pode passar um token para um procedimento de thread usando o constructo <xref:System.Threading.Thread> que usa um representante <xref:System.Threading.ParameterizedThreadStart>. O exemplo a seguir demonstra como fazer isso.  
  
 [!code-csharp[Cancellation#14](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/CooperativeThreads.cs#14)]
 [!code-vb[Cancellation#14](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/CooperativeThreads.vb#14)]  
  
## <a name="see-also"></a>Consulte também  
 [Usando threads e threading](../../../docs/standard/threading/using-threads-and-threading.md)
