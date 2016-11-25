---
title: Coletas induzidas
description: Coletas induzidas
keywords: .NET, .NET Core
author: stevehoag
manager: wpickett
ms.date: 08/16/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 3e09b9dd-a800-4e56-b468-619f910ae22e
translationtype: Human Translation
ms.sourcegitcommit: 213ce098bcc2b5e31c55e759d895254d5ca33caa
ms.openlocfilehash: 0bd8998cfb508294ffbc7a9619b571c9881ba294

---

# <a name="induced-collections"></a>Coletas induzidas

Na maioria dos casos, o coletor de lixo pode determinar o melhor momento para executar uma coleta e você deve permitir que ele seja executado de modo independente. Existem situações raras nas quais uma coleta forçada pode melhorar o desempenho do seu aplicativo. Nesses casos, você poderá induzir a coleta de lixo usando o método [GC.Collect](xref:System.GC.Collect) para forçar uma coleta de lixo. 

Use o método [Collect](xref:System.GC.Collect) quando houver uma redução significativa na quantidade de memória que está sendo usada em um ponto específico no código do aplicativo. Por exemplo, se seu aplicativo usar uma caixa de diálogo complexo que tem vários controles, chamar [Collect](xref:System.GC.Collect) quando a caixa de diálogo é fechada poderá melhorar o desempenho, recuperando imediatamente a memória usada pela caixa de diálogo. Certifique-se de que seu aplicativo não está induzindo a coleta de lixo com muita frequência, pois isso poderá diminuir o desempenho se o coletor de lixo estiver tentando recuperar os objetos em horários não ideais. Você pode fornecer um valor de enumeração [GCCollectionMode.Optimized](xref:System.GCCollectionMode.Optimized) para que o método [Collect](xref:System.GC.Collect) faça a coleta somente quando tal coleta for produtiva, conforme discutido na próxima seção.

## <a name="gc-collection-mode"></a>Modo de coleta de GC

Você pode usar uma das sobrecargas do método [GC.Collect](xref:System.GC.Collect), que inclui um valor [GCCollectionMode](xref:System.GCCollectionMode), para especificar o comportamento de uma coleta forçada do modo a seguir.

Valor de GCCollectionMode | Descrição
---------------------- | ----------- 
[Padrão](xref:System.GCCollectionMode.Default) | Usa a configuração de coleta de lixo padrão para a versão do .NET Framework em execução.
[Forçado](xref:System.GCCollectionMode.Forced) | Força a coleta de lixo a ocorrer imediatamente. Isso é equivalente a chamar a sobrecarga [GC.Collect()](xref:System.GC.Collect). Isso resulta em uma coleta de bloqueio total de todas as gerações. Você também pode compactar o heap de objeto grande, definindo a propriedade [GCSettings.LargeObjectHeapCompactionMode](xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode) como [GCLargeObjectHeapCompactionMode.CompactOnce](xref:System.Runtime.GCLargeObjectHeapCompactionMode.CompactOnce) antes de forçar uma coleta de lixo de bloqueio total imediata. 
[Otimizado](xref:System.GCCollectionMode.Optimized) | Permite que o coletor de lixo determine se o horário atual é ideal para recuperar objetos. O coletor de lixo pode determinar que uma coleta não seria suficientemente produtiva para se justificar, caso em que ele retornará sem recuperar objetos.
 
## <a name="background-or-blocking-collections"></a>Coletas de bloqueio ou em segundo plano

Você pode chamar a sobrecarga de método [GC.Collect(Int32, GCCollectionMode, Boolean)](xref:System.GC.Collect(System.Int32,System.GCCollectionMode,System.Boolean)) para especificar se uma coleção induzida está bloqueando ou não. O tipo de coleta executada depende de uma combinação dos parâmetros *mode* e *blocking* do método. *mode* é um membro da enumeração [GCCollectionMode](xref:System.GCCollectionMode) e *blocking* é um valor [Booliano](xref:System.Boolean). A tabela a seguir resume a interação entre os argumentos mode e blocking. 

*modo* | *blocking* = true | *blocking* = false
------ | ----------------- | ------------------
[Forçada](xref:System.GCCollectionMode.Forced) ou [Padrão](xref:System.GCCollectionMode.Default) | Uma coleção de bloqueio é executada assim que possível. Se uma coleta em segundo plano estiver em andamento e a geração for 0 ou 1, o método [Coletar (Int32, GCCollectionMode, Boolean)](xref:System.GC.Collect(System.Int32,System.GCCollectionMode,System.Boolean)) disparará imediatamente uma coleta de bloqueio e retornará quando a coleção for concluída. Se uma coleta em segundo plano estiver em andamento e o parâmetro de geração for 2, o método aguardará até que a coleta em segundo plano seja concluída, disparará uma coleta de bloqueio de geração 2 e, em seguida, retornará. | Uma coleta é executada assim que possível. O método [Collect(Int32, GCCollectionMode, Boolean)](xref:System.GC.Collect(System.Int32,System.GCCollectionMode,System.Boolean)) solicita uma coleta em segundo plano, mas isso não é garantido; dependendo das circunstâncias, ainda é possível que uma coleta de bloqueio seja executada. Se uma coleta em segundo plano já estiver em andamento, o método retornará imediatamente. 
[Otimizado](xref:System.GCCollectionMode.Optimized) | Uma coleta de bloqueio pode ser executada, dependendo do estado do coletor de lixo e do parâmetro de geração. O coletor de lixo tenta fornecer um desempenho ideal. | Uma coleta pode ser executada, dependendo do estado do coletor de lixo. O método [Collect(Int32, GCCollectionMode, Boolean)](xref:System.GC.Collect(System.Int32,System.GCCollectionMode,System.Boolean)) solicita uma coleta em segundo plano, mas isso não é garantido; dependendo das circunstâncias, ainda é possível que uma coleta de bloqueio seja executada. O coletor de lixo tenta fornecer um desempenho ideal. Se uma coleta em segundo plano já estiver em andamento, o método retornará imediatamente. 
 
## <a name="see-also"></a>Consulte também

[Modos de latência](latency.md)

[Coleta de lixo no .NET](index.md)



<!--HONumber=Nov16_HO3-->


