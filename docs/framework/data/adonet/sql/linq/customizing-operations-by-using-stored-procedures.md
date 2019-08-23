---
title: Personalizando operações usando procedimentos armazenados
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: aedbecc1-c33c-4fb4-8861-fdf7e1dc6b8a
ms.openlocfilehash: 08cc8aedac545ffa5648034119fc2267c860d499
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963287"
---
# <a name="customizing-operations-by-using-stored-procedures"></a>Personalizando operações usando procedimentos armazenados
Os procedimentos armazenados representam uma abordagem mais comum para substituir o comportamento padrão. Os exemplos neste tópico mostram como você pode usar wrappers gerados do método para procedimentos armazenados, e como você pode chamar procedimentos armazenados diretamente.  
  
 Se você estiver usando o Visual Studio, poderá usar o Object Relational Designer para atribuir procedimentos armazenados para executar inserções, atualizações e exclusões.  
  
> [!NOTE]
> Para ler valores base de dados - gerados novamente, use parâmetros de saída em seus procedimentos armazenados. Se você não puder usar parâmetros de saída, escreva uma implementação de método parcial em vez de depender de substituições geradas pelo Object Relational Designer. Os membros mapeados para os valores base de dados - gerados devem ser definidos para apropriado valores depois que `INSERT` ou operações de `UPDATE` terminar com êxito. Para obter mais informações, consulte [responsabilidades do desenvolvedor ao substituir o comportamento padrão](../../../../../../docs/framework/data/adonet/sql/linq/responsibilities-of-the-developer-in-overriding-default-behavior.md).  
  
## <a name="example"></a>Exemplo  
  
### <a name="description"></a>Descrição  
 No exemplo, presuma que a classe de `Northwind` contém dois métodos para chamar procedimentos armazenados que estão sendo usados para alternativas em uma classe derivada.  
  
### <a name="code"></a>Código  
 [!code-csharp[DLinqOverrideDefaultSproc#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefaultSproc/cs/northwind.cs#1)]
 [!code-vb[DLinqOverrideDefaultSproc#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefaultSproc/vb/northwind.vb#1)]  
  
## <a name="example"></a>Exemplo  
  
### <a name="description"></a>Descrição  
 A classe seguir usa esses métodos para substituição.  
  
### <a name="code"></a>Código  
 [!code-csharp[DLinqOverrideDefaultSproc#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefaultSproc/cs/northwind.cs#2)]
 [!code-vb[DLinqOverrideDefaultSproc#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefaultSproc/vb/northwind.vb#2)]  
  
## <a name="example"></a>Exemplo  
  
### <a name="description"></a>Descrição  
 Você pode usar `NorthwindThroughSprocs` exatamente como você usaria `Northwnd`.  
  
### <a name="code"></a>Código  
 [!code-csharp[DLinqOverrideDefaultSproc#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefaultSproc/cs/Program.cs#3)]
 [!code-vb[DLinqOverrideDefaultSproc#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefaultSproc/vb/Module1.vb#3)]  
  
## <a name="see-also"></a>Consulte também

- [Responsabilidades do desenvolvedor em substituir o comportamento padrão](../../../../../../docs/framework/data/adonet/sql/linq/responsibilities-of-the-developer-in-overriding-default-behavior.md)
