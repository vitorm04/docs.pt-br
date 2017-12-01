---
title: SpinWait
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
helpviewer_keywords: synchronization primitives, SpinWait
ms.assetid: 36012f42-34e5-4f86-adf4-973f433ed6c6
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: cfaf85c0fe1de3be89618ae540e9c183b66a11eb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="spinwait"></a>SpinWait
<xref:System.Threading.SpinWait?displayProperty=nameWithType>é um tipo de sincronização leve que você pode usar em cenários de baixo nível para evitar as alternâncias de contexto caro e transições de kernel que são necessárias para eventos de kernel. Em computadores com vários núcleos, quando um recurso não deve ser mantido por longos períodos de tempo, pode ser mais eficiente para um thread de espera executar no modo de usuário para alguns ciclos de dezenas de algumas centenas e, em seguida, tente novamente para adquirir o recurso. Se o recurso está disponível após a rotação, terá salvo vários ciclos de milhar. Se o recurso ainda não estiver disponível, você passou apenas alguns ciclos e ainda é possível inserir uma espera de kernel. Essa combinação de espera de, em seguida, girando às vezes é conhecida como um *operação bifásica de espera*.  
  
 <xref:System.Threading.SpinWait>foi projetado para ser usado em conjunto com os tipos do .NET Framework que encapsulam os eventos de kernel como <xref:System.Threading.ManualResetEvent>. <xref:System.Threading.SpinWait>também pode ser usado por si só para a funcionalidade básica giratório em apenas um programa.  
  
 <xref:System.Threading.SpinWait>é mais do que apenas um loop vazio. É implementado com cuidado para fornecer comportamento giratório correto para o caso geral e se inicia alternâncias de contexto se ele precisar tempo suficiente (aproximadamente o período de tempo necessário para uma transição de kernel). Por exemplo, em computadores de núcleo único, <xref:System.Threading.SpinWait> produz a fatia de tempo do thread imediatamente porque blocos giratório encaminham progresso em todos os threads. <xref:System.Threading.SpinWait>também gera mesmo em máquinas com vários núcleos para impedir que o thread de espera de bloqueio de threads de prioridade mais alta ou o coletor de lixo. Portanto, se você estiver usando um <xref:System.Threading.SpinWait> em uma operação de espera de duas fases, recomendamos que você chamar a espera de kernel antes do <xref:System.Threading.SpinWait> se inicia uma alternância de contexto. <xref:System.Threading.SpinWait>fornece o <xref:System.Threading.SpinWait.NextSpinWillYield%2A> propriedade, que você pode verificar antes de cada chamada para <xref:System.Threading.SpinWait.SpinOnce%2A>. Quando a propriedade retornar `true`, iniciar sua operação de espera. Para obter um exemplo, consulte [como: usar SpinWait para implementar uma operação de espera de confirmação de duas fases](../../../docs/standard/threading/how-to-use-spinwait-to-implement-a-two-phase-wait-operation.md).  
  
 Se você não estiver executando uma operação de espera de duas fases, mas é apenas girando até que alguma condição for verdadeira, você pode habilitar <xref:System.Threading.SpinWait> executar seu contexto alterna para que seja um bom cidadão no ambiente do sistema operacional Windows. O exemplo básico a seguir mostra um <xref:System.Threading.SpinWait> em uma pilha sem bloqueio. Se você precisar de uma pilha de alto desempenho, thread-safe, considere o uso de <xref:System.Collections.Concurrent.ConcurrentStack%601?displayProperty=nameWithType>.  
  
 [!code-csharp[CDS_SpinWait#05](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_spinwait/cs/spinwait.cs#05)]
 [!code-vb[CDS_SpinWait#05](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_spinwait/vb/cds_spinwait1.vb#05)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Threading.Thread.SpinWait%2A>  
 [Objetos e recursos de threading](../../../docs/standard/threading/threading-objects-and-features.md)
