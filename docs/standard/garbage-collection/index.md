---
title: .NET coleta de lixo
ms.date: 04/21/2020
ms.technology: dotnet-standard
helpviewer_keywords:
- memory, garbage collection
- garbage collection, automatic memory management
- GC [.NET Framework]
- memory, allocating
- common language runtime, garbage collection
- garbage collector
- cleanup operations
- garbage collection
- memory, releasing
- common language runtime, automatic memory management
- automatic memory management
- runtime, automatic memory management
- runtime, garbage collection
- garbage collection, about
ms.assetid: 22b6cb97-0c80-4eeb-a2cf-5ed7655e37f9
ms.openlocfilehash: c087deb033a373dd8b3980feb7ec6901c7909569
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102236"
---
# <a name="garbage-collection"></a>Coleta de lixo

O coletor de lixo do .NET gerencia a alocação e a liberação de memória para seu aplicativo. Toda vez que você cria um novo objeto, o Common Language Runtime aloca memória para o objeto do heap gerenciado. Desde que exista espaço de endereço disponível no heap gerenciado, o runtime continua alocando espaço para novos objetos. No entanto, a memória não é infinita. No fim das contas, o coletor de lixo deve realizar uma coleta para liberar algum espaço na memória. O mecanismo de otimização do coletor de lixo determina o melhor momento para executar uma coleta com base nas alocações que estão sendo feitas. Quando o coletor de lixo executa uma coleta, ele verifica se há objetos no heap gerenciado que não estão mais sendo usados pelo aplicativo e realiza as operações necessárias para recuperar sua memória.  
  
## <a name="in-this-section"></a>Nesta seção
  
|Title|Descrição|  
|-----------|-----------------|  
|[Fundamentos da coleta de lixo](../../../docs/standard/garbage-collection/fundamentals.md)|Descreve como funciona a coleta de lixo, como os objetos são alocados no heap gerenciado e outros conceitos principais.|  
|[Coleta de lixo de estação de trabalho ou de servidor](workstation-server-gc.md)|Descreve as diferenças entre a coleta de lixo da estação de trabalho para aplicativos clientes e a coleta de lixo do servidor para aplicativos de servidor.|
|[Coleta de lixo de fundo](background-gc.md)|Descreve a coleta de lixo de fundo, que é a coleta de objetos de geração 0 e 1 enquanto a coleta da geração 2 está em andamento.|
|[O grande monte de objetos](large-object-heap.md)|Descreve o grande monte de objetos (LOH) e como objetos grandes são coletados em lixo.|
|[Coleta de lixo e desempenho](../../../docs/standard/garbage-collection/performance.md)|Descreve as verificações de desempenho que você pode usar para diagnosticar problemas de desempenho e de coleta de lixo.|  
|[Coletas induzidas](../../../docs/standard/garbage-collection/induced.md)|Descreve como fazer uma coleta de lixo ocorrer.|  
|[Modos de latência](../../../docs/standard/garbage-collection/latency.md)|Descreve os modos de determinam o grau de intrusão da coleta de lixo.|  
|[Otimização da hospedagem Web compartilhada](../../../docs/standard/garbage-collection/optimization-for-shared-web-hosting.md)|Descreve como otimizar a coleta de lixo em servidores compartilhados por vários sites pequenos.|  
|[Notificações da coleta de lixo](../../../docs/standard/garbage-collection/notifications.md)|Descreve como determinar quando uma coleta de lixo completa está se aproximando e quando ela é concluída.|  
|[Monitoramento de recursos do domínio do aplicativo](../../../docs/standard/garbage-collection/app-domain-resource-monitoring.md)|Descreve como monitorar o uso de CPU e memória por um domínio do aplicativo.|  
|[Referências fracas](../../../docs/standard/garbage-collection/weak-references.md)|Descreve os recursos que permitem que um objeto seja, simultaneamente, coletado pelo coletor de lixo e acessado pelo aplicativo.|  
  
## <a name="reference"></a>Referência

- <xref:System.GC?displayProperty=nameWithType>  
- <xref:System.GCCollectionMode?displayProperty=nameWithType>  
- <xref:System.GCNotificationStatus?displayProperty=nameWithType>  
- <xref:System.Runtime.GCLatencyMode?displayProperty=nameWithType>  
- <xref:System.Runtime.GCSettings?displayProperty=nameWithType>  
- <xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode%2A?displayProperty=nameWithType>  
- <xref:System.Object.Finalize%2A?displayProperty=nameWithType>  
- <xref:System.IDisposable?displayProperty=nameWithType>  
  
## <a name="see-also"></a>Confira também

- [Limpar recursos não gerenciados](../../../docs/standard/garbage-collection/unmanaged.md)
