---
title: Coleta de Lixo
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1f61b63f78ea3c6131d4d1ab4e421be25149035b
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45521262"
---
# <a name="garbage-collection"></a>Coleta de Lixo
O coletor de lixo do .NET gerencia a alocação e a liberação de memória para seu aplicativo. Toda vez que você cria um novo objeto, o Common Language Runtime aloca memória para o objeto do heap gerenciado. Desde que exista espaço de endereço disponível no heap gerenciado, o tempo de execução continua alocando espaço para novos objetos. No entanto, a memória não é infinita. No fim das contas, o coletor de lixo deve realizar uma coleta para liberar algum espaço na memória. O mecanismo de otimização do coletor de lixo determina o melhor momento para executar uma coleta com base nas alocações que estão sendo feitas. Quando o coletor de lixo executa uma coleta, ele verifica se há objetos no heap gerenciado que não estão mais sendo usados pelo aplicativo e realiza as operações necessárias para recuperar sua memória.  
  
<a name="related_topics"></a>   
## <a name="related-topics"></a>Tópicos relacionados  
  
|Título|Descrição|  
|-----------|-----------------|  
|[Conceitos básicos da coleta de lixo](../../../docs/standard/garbage-collection/fundamentals.md)|Descreve como funciona a coleta de lixo, como os objetos são alocados no heap gerenciado e outros conceitos principais.|  
|[Coleta de lixo e desempenho](../../../docs/standard/garbage-collection/performance.md)|Descreve as verificações de desempenho que você pode usar para diagnosticar problemas de desempenho e de coleta de lixo.|  
|[Coletas Induzidas](../../../docs/standard/garbage-collection/induced.md)|Descreve como fazer uma coleta de lixo ocorrer.|  
|[Modos de latência](../../../docs/standard/garbage-collection/latency.md)|Descreve os modos de determinam o grau de intrusão da coleta de lixo.|  
|[Otimização para hospedagem na Web compartilhada](../../../docs/standard/garbage-collection/optimization-for-shared-web-hosting.md)|Descreve como otimizar a coleta de lixo em servidores compartilhados por vários sites pequenos.|  
|[Notificações de coleta de lixo](../../../docs/standard/garbage-collection/notifications.md)|Descreve como determinar quando uma coleta de lixo completa está se aproximando e quando ela é concluída.|  
|[Monitoramento de recursos de domínio do aplicativo](../../../docs/standard/garbage-collection/app-domain-resource-monitoring.md)|Descreve como monitorar o uso de CPU e memória por um domínio do aplicativo.|  
|[Referências fracas](../../../docs/standard/garbage-collection/weak-references.md)|Descreve os recursos que permitem que um objeto seja, simultaneamente, coletado pelo coletor de lixo e acessado pelo aplicativo.|  
  
## <a name="reference"></a>Referência  
 <xref:System.GC?displayProperty=nameWithType>  
  
 <xref:System.GCCollectionMode?displayProperty=nameWithType>  
  
 <xref:System.GCNotificationStatus?displayProperty=nameWithType>  
  
 <xref:System.Runtime.GCLatencyMode?displayProperty=nameWithType>  
  
 <xref:System.Runtime.GCSettings?displayProperty=nameWithType>  
  
 <xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode%2A?displayProperty=nameWithType>  
  
 <xref:System.Object.Finalize%2A?displayProperty=nameWithType>  
  
 <xref:System.IDisposable?displayProperty=nameWithType>  
  
## <a name="see-also"></a>Consulte também

- [Limpando recursos não gerenciados](../../../docs/standard/garbage-collection/unmanaged.md)
