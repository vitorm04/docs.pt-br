---
title: "Como: Criar tarefas pré-computadas"
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
helpviewer_keywords: tasks, creating pre-computed
ms.assetid: a73eafa2-1f49-4106-a19e-997186029b58
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4596b28afe48aad4a84a7dd72b4a1d44a9ada8a2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-create-pre-computed-tasks"></a>Como: Criar tarefas pré-computadas
Este documento descreve como usar o <xref:System.Threading.Tasks.Task.FromResult%2A?displayProperty=nameWithType> método para recuperar os resultados das operações assíncronas de download que são mantidos em um cache. O <xref:System.Threading.Tasks.Task.FromResult%2A> método retorna um terminar <xref:System.Threading.Tasks.Task%601> objeto que contém o valor fornecido como sua <xref:System.Threading.Tasks.Task%601.Result%2A> propriedade. Este método é útil quando você executa uma operação assíncrona que retorna um objeto <xref:System.Threading.Tasks.Task%601> e o resultado do objeto <xref:System.Threading.Tasks.Task%601> já está calculado.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir faz o download de cadeias de caracteres da web. Define o `DownloadStringAsync` método. Esse método baixa cadeias de caracteres da web assincronamente. Este exemplo também usa um <xref:System.Collections.Concurrent.ConcurrentDictionary%602> objeto em cache os resultados de operações anteriores. Se o endereço de entrada é mantido no cache, `DownloadStringAsync` usa o <xref:System.Threading.Tasks.Task.FromResult%2A> método para produzir um <xref:System.Threading.Tasks.Task%601> objeto que contém o conteúdo nesse endereço. Caso contrário, `DownloadStringAsync` baixa o arquivo da web e adiciona o resultado para o cache.  
  
 [!code-csharp[TPL_CachedDownloads#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_cacheddownloads/cs/cacheddownloads.cs#1)]
 [!code-vb[TPL_CachedDownloads#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_cacheddownloads/vb/cacheddownloads.vb#1)]  
  
 Esse exemplo calcula o tempo necessário para baixar várias cadeias de caracteres duas vezes. O segundo conjunto de operações de download deve levar menos tempo do que o primeiro conjunto porque os resultados são mantidos no cache. O <xref:System.Threading.Tasks.Task.FromResult%2A> método habilita o `DownloadStringAsync` método para criar <xref:System.Threading.Tasks.Task%601> objetos que contêm esses pré-computadas resultados.  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Copie o código de exemplo e cole-o em um projeto do Visual Studio ou colá-lo em um arquivo chamado `CachedDownloads.cs` (`CachedDownloads.vb` para [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]), e, em seguida, execute o seguinte comando em uma janela de Prompt de comando do Visual Studio.  
  
 [!INCLUDE[csprcs](../../../includes/csprcs-md.md)]  
  
 **CSC.exe CachedDownloads.cs**  
  
 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]  
  
 **Vbc.exe CachedDownloads.vb**  
  
## <a name="robust-programming"></a>Programação robusta  
  
## <a name="see-also"></a>Consulte também  
 [Programação assíncrona baseada em tarefa](../../../docs/standard/parallel-programming/task-based-asynchronous-programming.md)
