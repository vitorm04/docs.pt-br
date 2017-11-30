---
title: "Criando threads e passando dados na hora de início"
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
- cpp
helpviewer_keywords:
- threading [.NET Framework], creating
- threading [.NET Framework], passing data to threads
- threading [.NET Framework], retrieving data from threads
ms.assetid: 52b32222-e185-4f42-91a7-eaca65c0ab6d
caps.latest.revision: "18"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 61808dc804cc627ab368a5250414dfcc5f54c87e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="creating-threads-and-passing-data-at-start-time"></a>Criando threads e passando dados na hora de início
Quando um processo do sistema operacional é criado, o sistema operacional injeta um thread para executar o código no processo, incluindo qualquer domínio de aplicativo original. Desse ponto em diante, os domínios de aplicativo podem ser criados e destruídos sem qualquer threads do sistema operacional necessariamente que está sendo criado ou destruído. Se o código que está sendo executado é gerenciado código, em seguida, um <xref:System.Threading.Thread> do objeto para o thread em execução no domínio do aplicativo atual pode ser obtida recuperando estático <xref:System.Threading.Thread.CurrentThread%2A> propriedade do tipo <xref:System.Threading.Thread>. Este tópico descreve a criação de thread e aborda alternativas para passar dados para o procedimento de thread.  
  
## <a name="creating-a-thread"></a>Criar um Thread  
 Criando um novo <xref:System.Threading.Thread> objeto cria um novo thread gerenciado. O <xref:System.Threading.Thread> classe tem construtores que usam um <xref:System.Threading.ThreadStart> delegar ou um <xref:System.Threading.ParameterizedThreadStart> delegar; o representante encapsula o método é invocado por novo thread quando você chamar o <xref:System.Threading.Thread.Start%2A> método. Chamando <xref:System.Threading.Thread.Start%2A> mais de uma vez, faz com que um <xref:System.Threading.ThreadStateException> seja gerada.  
  
 O <xref:System.Threading.Thread.Start%2A> método retorna imediatamente, muitas vezes antes do novo segmento realmente foi iniciado. Você pode usar o <xref:System.Threading.Thread.ThreadState%2A> e <xref:System.Threading.Thread.IsAlive%2A> propriedades para determinar o estado do thread em um dado momento, mas essas propriedades nunca devem ser usado para sincronizar as atividades de threads.  
  
> [!NOTE]
>  Depois que um thread é iniciado, não é necessário manter uma referência para o <xref:System.Threading.Thread> objeto. O thread continua a executar até que o procedimento de thread termina.  
  
 O exemplo de código a seguir cria dois novos threads para chamar a instância e métodos estáticos em outro objeto.  
  
 [!code-cpp[System.Threading.ThreadStart2#2](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CPP/source2.cpp#2)]
 [!code-csharp[System.Threading.ThreadStart2#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CS/source2.cs#2)]
 [!code-vb[System.Threading.ThreadStart2#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.ThreadStart2/VB/source2.vb#2)]  
  
## <a name="passing-data-to-threads-and-retrieving-data-from-threads"></a>Transmitindo dados para Threads e recuperando dados de Threads  
 No .NET Framework versão 2.0, o <xref:System.Threading.ParameterizedThreadStart> representante fornece uma maneira fácil para passar um objeto que contém dados a um thread quando você chama o <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> sobrecarga do método. Consulte <xref:System.Threading.ParameterizedThreadStart> para obter um exemplo de código.  
  
 Usando o <xref:System.Threading.ParameterizedThreadStart> delegado não é uma maneira de tipo seguro para passar dados, porque o <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> sobrecarga do método aceita qualquer objeto. Uma alternativa é encapsular o procedimento de thread e os dados em uma classe auxiliar e usar o <xref:System.Threading.ThreadStart> representante para executar o procedimento de thread. Essa técnica é mostrada nos dois exemplos de código que segue.  
  
 Nenhum deles delegados tem um valor de retorno, porque não há nenhum local para retornar os dados de uma chamada assíncrona. Para recuperar os resultados de um método de thread, você pode usar um método de retorno de chamada, conforme demonstrado no segundo exemplo de código.  
  
 [!code-cpp[System.Threading.ThreadStart2#3](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CPP/source3.cpp#3)]
 [!code-csharp[System.Threading.ThreadStart2#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CS/source3.cs#3)]
 [!code-vb[System.Threading.ThreadStart2#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.ThreadStart2/VB/source3.vb#3)]  
  
### <a name="retrieving-data-with-callback-methods"></a>Recuperação de dados com os métodos de retorno de chamada  
 O exemplo a seguir demonstra um método de retorno de chamada que recupera dados de um thread. O construtor para a classe que contém os dados e o método de thread também aceita um delegado que representa o método de retorno de chamada; antes do método de thread termina, ele chama o representante de retorno de chamada.  
  
 [!code-cpp[System.Threading.ThreadStart2#4](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CPP/source4.cpp#4)]
 [!code-csharp[System.Threading.ThreadStart2#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CS/source4.cs#4)]
 [!code-vb[System.Threading.ThreadStart2#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.ThreadStart2/VB/source4.vb#4)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Threading.Thread>  
 <xref:System.Threading.ThreadStart>  
 <xref:System.Threading.ParameterizedThreadStart>  
 <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType>  
 [Threading](../../../docs/standard/threading/index.md)  
 [Usando threads e threading](../../../docs/standard/threading/using-threads-and-threading.md)
