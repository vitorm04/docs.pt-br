---
title: Comparação entre propriedades e indexadores – Guia de Programação em C#
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- properties [C#], vs. indexers
- indexers [C#], vs. properties
ms.assetid: 3358a89f-44a0-4a4d-bf8c-07237a90af39
ms.openlocfilehash: 41b27905edb8a0e00a6af5a4cce38988161326d0
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54537719"
---
# <a name="comparison-between-properties-and-indexers-c-programming-guide"></a>Comparação entre propriedades e indexadores (Guia de Programação em C#)
Os indexadores são como propriedades. Com exceção das diferenças mostradas na tabela a seguir, todas as regras definidas para acessadores de propriedade também se aplicam a acessadores de indexador.  
  
|Propriedade|Indexador|  
|--------------|-------------|  
|Permite que os métodos sejam chamados como se fossem membros de dados públicos.|Permite que elementos de uma coleção interna de um objeto sejam acessados usando uma notação de matriz no próprio objeto.|  
|Acessado por meio de um nome simples.|Acessado por meio de um índice.|  
|Pode ser estático ou um membro de instância.|Deve ser um membro da instância.|  
|Um acessador [get](../../../csharp/language-reference/keywords/get.md) de uma propriedade não tem parâmetros.|Um acessador `get` de um indexador tem a mesma lista de parâmetro formal que o indexador.|  
|Um acessador [set](../../../csharp/language-reference/keywords/set.md) de uma propriedade contém o parâmetro implícito `value`.|Um acessador `set` de um indexador tem a mesma lista de parâmetro formal que o indexador, bem como o mesmo parâmetro de [valor](../../../csharp/language-reference/keywords/value.md).|  
|Dá suporte a sintaxe reduzida com [Propriedades Autoimplementadas](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md).|Não oferece suporte a sintaxe reduzida.|  
  
## <a name="see-also"></a>Consulte também

- [Guia de Programação em C#](../../../csharp/programming-guide/index.md)
- [Indexadores](../../../csharp/programming-guide/indexers/index.md)
- [Propriedades](../../../csharp/programming-guide/classes-and-structs/properties.md)
