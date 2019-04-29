---
title: Semântica nula
ms.date: 03/30/2017
ms.assetid: a97017ae-d634-4cf3-bbaf-054a528fd683
ms.openlocfilehash: eb1e96ba44c5d64e8366a654c2d06d89c9b46c9a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61767527"
---
# <a name="null-semantics"></a>Semântica nula
A tabela a seguir fornece links para várias partes do [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] documentação onde `null` (`Nothing` no Visual Basic) problemas são discutidos.  
  
|Tópico|Descrição|  
|-----------|-----------------|  
|[Tipos incompatíveis CLR do SQL](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mismatches.md)|A seção "Semântica nula" neste tópico inclui a discussão sobre as três estado SQL booleano versus o dois estados common language runtime (CLR) <xref:System.Boolean>, o literal `Nothing` (Visual Basic) e `null` (C#) e outros semelhantes problemas.|  
|[Conversão de operador de consulta padrão](../../../../../../docs/framework/data/adonet/sql/linq/standard-query-operator-translation.md)|“A seção de semântica nula” neste tópico descreve as semânticas nula de comparação em [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].|  
|[Métodos de System.String](../../../../../../docs/framework/data/adonet/sql/linq/system-string-methods.md)|As “diferenças a seção .NET” neste tópico descrevem como um retorno de 0 de <xref:System.String.LastIndexOf%2A> pode significar qualquer pessoa que a cadeia de caracteres é nula ou que a posição encontrada é 0.|  
|[Calcular a soma dos valores em uma sequência numérica](../../../../../../docs/framework/data/adonet/sql/linq/compute-the-sum-of-values-in-a-numeric-sequence.md)|Descreve como o <xref:System.Linq.Enumerable.Sum%2A> operador é avaliado como `null` (`Nothing` no Visual Basic) em vez de 0 para uma sequência que contém somente nulos ou para uma sequência vazia.|  
  
## <a name="see-also"></a>Consulte também

- [Funções e tipos de dados](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)
