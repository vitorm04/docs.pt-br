---
title: "Comparação entre Propriedades e Indexadores (Guia de Programação em C#) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- properties [C#], vs. indexers
- indexers [C#], vs. properties
ms.assetid: 3358a89f-44a0-4a4d-bf8c-07237a90af39
caps.latest.revision: 14
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 97172a3113d04cb345f52b5cd6a8957d279982b1
ms.lasthandoff: 03/13/2017

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
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)   
 [Indexadores](../../../csharp/programming-guide/indexers/index.md)   
 [Propriedades](../../../csharp/programming-guide/classes-and-structs/properties.md)
