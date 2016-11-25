---
title: "Modos de latência"
description: "Modos de latência"
keywords: .NET, .NET Core
author: stevehoag
manager: wpickett
ms.date: 08/18/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 810bd8be-5a48-42c6-b080-3afdb31fc61b
translationtype: Human Translation
ms.sourcegitcommit: de0dab146fc811e895dc32f98f877db5e757f82b
ms.openlocfilehash: 6976bb49e9124a787abb1c0a2791cda86dac1007

---

# <a name="latency-modes"></a>Modos de latência

Para recuperar objetos, o coletor de lixo deve interromper todos os threads em execução em um aplicativo. Em algumas situações, como quando um aplicativo recupera dados ou exibe conteúdo, uma coleta de lixo completa pode ocorrer em um momento crítico e impedir o desempenho. Você pode ajustar a intrusão do coletor de lixo, definindo a propriedade [GCSettings.LatencyMode](xref:System.Runtime.GCSettings.LatencyMode) como um dos valores [System.Runtime.GCLatencyMode](xref:System.Runtime.GCLatencyMode). 

A latência refere-se à hora em que o coletor de lixo invade seu aplicativo. Durante períodos de baixa latência, o coletor de lixo é mais conservador e menos intrusivo na recuperação de objetos. A enumeração [System.Runtime.GCLatencyMode](xref:System.Runtime.GCLatencyMode) fornece duas configurações de baixa latência:

* [LowLatency](xref:System.Runtime.GCLatencyMode.LowLatency) suprime coletas da geração 2 e executa somente coletas da geração 0 e 1. Ela pode ser usada somente por curtos períodos. Em períodos mais longos, se o sistema estiver sob pressão de memória, o coletor de lixo disparará uma coleção, que pode pausar o aplicativo rapidamente e interromper uma operação de tempo crítico. Essa configuração está disponível somente para coleta de lixo de estação de trabalho. 

* [SustainedLowLatency](xref:System.Runtime.GCLatencyMode.SustainedLowLatency) suprime coletas da geração 2 em primeiro plano e executa somente a geração 0, 1 e coletas da geração 2 em segundo plano. Ela pode ser usada por longos períodos e está disponível para coleta de lixo de estação de trabalho e servidor. Essa configuração não poderá ser usada se a [coleta de lixo simultânea](https://msdn.microsoft.com/library/yhwwzef8.aspx) estiver desabilitada.

Durante períodos de baixa latência, coletas da geração 2 são suprimidas, a menos que ocorra o seguinte:

* O sistema recebe uma notificação de falta de memória do sistema operacional.

* O código do aplicativo induz uma coleção, chamando o método [GC.Collect](xref:System.GC.Collect(System.Int32)) e especificando 2 para o parâmetro de geração.

A tabela a seguir lista os cenários de aplicativo para uso dos valores [GCLatencyMode](xref:System.Runtime.GCLatencyMode).

Modo de latência | Cenários de aplicativo
------------ | --------------------- 
[Lote](xref:System.Runtime.GCLatencyMode.Batch) | Para aplicativos que não têm operações de interface do usuário ou do servidor. Este é o modo padrão quando a [coleta de lixo simultânea](https://msdn.microsoft.com/library/yhwwzef8.aspx) está desabilitada.
[Interativo](xref:System.Runtime.GCLatencyMode.Interactive) | Para a maioria dos aplicativos que têm uma interface do usuário. Para aplicativos que não têm operações de interface do usuário ou do servidor. Este é o modo padrão quando a [coleta de lixo simultânea](https://msdn.microsoft.com/library/yhwwzef8.aspx) está habilitada.
[LowLatency](xref:System.Runtime.GCLatencyMode.LowLatency) | Para aplicativos que têm operações de curto prazo, sensíveis ao tempo, durante o qual as interrupções do coletor de lixo podem ser prejudiciais. Por exemplo, os aplicativos com funções de aquisição de dados ou renderização de animação.
[SustainedLowLatency](xref:System.Runtime.GCLatencyMode.SustainedLowLatency) | Para aplicativos que têm operações sensíveis ao tempo, por uma duração contida, mas potencialmente maior, durante a qual as interrupções do coletor de lixo poderiam ser prejudiciais. Por exemplo, aplicativos que precisam de tempos de resposta rápidos, como alterações de dados de mercado durante o horário comercial.   Esse modo resulta em um tamanho maior do heap gerenciado do que outros modos. Como ele não compacta o heap gerenciado, é possível maior fragmentação. Verifique se há memória suficiente disponível.
 
## <a name="guidelines-for-using-low-latency"></a>Diretrizes para uso de baixa latência

Ao usar o modo [LowLatency](xref:System.Runtime.GCLatencyMode.LowLatency), considere as seguintes diretrizes:

* Mantenha o período de baixa latência o mais curto possível.

* Evite a alocação de grande quantidade de memória durante períodos de baixa latência. Notificações de memória insuficiente podem ocorrer porque a coleta de lixo recupera menos objetos. 

* No modo de baixa latência, minimize o número de alocações feitas, principalmente alocações em heap de objetos grandes e objetos fixados. 

* Esteja atento a ameaças que possam ser alocadas. Como a configuração da propriedade [LatencyMode](xref:System.Runtime.GCSettings.LatencyMode) é de todo o processo, você pode gerar uma [OutOfMemoryException](xref:System.OutOfMemoryException) em qualquer thread que possa ser alocado. 

* Você pode forçar coletas da geração 2 durante um período de baixa latência ao chamar o método [GC. Coletar GCCollectionMode (Int32)](xref:System.GC.Collect(System.Int32,System.GCCollectionMode)).

## <a name="see-also"></a>Consulte também

[System.GC](xref:System.GC)

[Coletas Induzidas](induced.md)

[Coleta de lixo no .NET](index.md)



<!--HONumber=Nov16_HO3-->


