---
title: Semântica nula
ms.date: 03/30/2017
ms.assetid: a97017ae-d634-4cf3-bbaf-054a528fd683
ms.openlocfilehash: 739ee95be45d7d64a4ad1678837b9706a533f07d
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91147535"
---
# <a name="null-semantics"></a>Semântica nula

A tabela a seguir fornece links para várias partes da [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] documentação onde `null` os `Nothing` problemas (em Visual Basic) são discutidos.  
  
|Tópico|Descrição|  
|-----------|-----------------|  
|[Incompatibilidade de SQL-CLR](sql-clr-type-mismatches.md)|A seção "semântica nula" deste tópico inclui a discussão do booliano SQL de três Estados versus o CLR (Common Language Runtime de dois Estados) <xref:System.Boolean> , o literal `Nothing` (Visual Basic) e `null` (C#) e outros problemas semelhantes.|  
|[Conversão padrão de operador de consulta](standard-query-operator-translation.md)|“A seção de semântica nula” neste tópico descreve as semânticas nula de comparação em [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].|  
|[Métodos de System.String](system-string-methods.md)|As “diferenças a seção .NET” neste tópico descrevem como um retorno de 0 de <xref:System.String.LastIndexOf%2A> pode significar qualquer pessoa que a cadeia de caracteres é nula ou que a posição encontrada é 0.|  
|[Calcular a soma dos valores em uma sequência numérica](compute-the-sum-of-values-in-a-numeric-sequence.md)|Descreve como o <xref:System.Linq.Enumerable.Sum%2A> operador é avaliado como `null` ( `Nothing` em Visual Basic) em vez de 0 para uma sequência que contém somente nulos ou para uma sequência vazia.|  
  
## <a name="see-also"></a>Confira também

- [Tipos de dados e funções](data-types-and-functions.md)
