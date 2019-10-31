---
title: Como percorrer uma árvore binária com tarefas paralelas
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, how to traverse a tree
ms.assetid: 4265d169-6c69-4f36-b10d-b7ae7f72f4df
ms.openlocfilehash: b79337e6ee8057506ff87c696cecd6b038eeebfc
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141646"
---
# <a name="how-to-traverse-a-binary-tree-with-parallel-tasks"></a>Como percorrer uma árvore binária com tarefas paralelas
O exemplo a seguir mostra duas maneiras pelas quais tarefas paralelas podem ser usadas para percorrer uma estrutura de dados de árvore. A criação da árvore em si permanece como um exercício.  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[TPL#16](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl/cs/tpl.cs#16)]
 [!code-vb[TPL#16](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl/vb/treewalk.vb#16)]  
  
 Os dois métodos mostrados são funcionalmente equivalentes. Usando o método <xref:System.Threading.Tasks.TaskFactory.StartNew%2A> para criar e executar as tarefas, você obter um identificador de tarefas que pode ser usado para aguardar as tarefas e manipular exceções.  
  
## <a name="see-also"></a>Consulte também

- [TPL (Biblioteca de Paralelismo de Tarefas)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)
