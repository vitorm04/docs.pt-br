---
title: Ignorar cláusula While (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QuerySkipWhile
helpviewer_keywords:
- Skip While statement [Visual Basic]
- Skip While clause [Visual Basic]
- queries [Visual Basic], Skip While
ms.assetid: 5dee8350-7520-4f1a-b00d-590cacd572d6
ms.openlocfilehash: 7f37a6fa1c9ba7fdf7978ac6853e4c2985bf72e7
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004703"
---
# <a name="skip-while-clause-visual-basic"></a>Ignorar cláusula While (Visual Basic)
Ignora os elementos em uma coleção, desde que uma condição especificada seja `true` e, em seguida, retorne os elementos restantes.  
  
## <a name="syntax"></a>Sintaxe  
  
```vb  
Skip While expression  
```  
  
## <a name="parts"></a>Partes  
  
|Termo|Definição|  
|---|---|  
|`expression`|Necessário. Uma expressão que representa uma condição para os elementos de teste. A expressão deve retornar um valor `Boolean` ou um equivalente funcional, como um `Integer` a ser avaliado como um `Boolean`.|  
  
## <a name="remarks"></a>Comentários  
 A cláusula `Skip While` ignora os elementos do início de um resultado da consulta até que o `expression` fornecido retorne `false`. Depois que `expression` retorna `false`, a consulta retorna todos os elementos restantes. O `expression` é ignorado para os resultados restantes.  
  
 A cláusula `Skip While` difere da cláusula `Where`, na qual a cláusula `Where` pode ser usada para excluir todos os elementos de uma consulta que não atendem a uma condição específica. A cláusula `Skip While` exclui elementos somente até a primeira vez em que a condição não for satisfeita. A cláusula `Skip While` é mais útil quando você está trabalhando com um resultado de consulta ordenada.  
  
 Você pode ignorar um número específico de resultados do início de um resultado de consulta usando a cláusula `Skip`.  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir usa a cláusula `Skip While` para ignorar os resultados até que o primeiro cliente do Estados Unidos seja encontrado.  
  
 [!code-vb[VbSimpleQuerySamples#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#3)]  
  
## <a name="see-also"></a>Consulte também

- [Introdução ao LINQ no Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Consultas](../../../visual-basic/language-reference/queries/index.md)
- [Cláusula Select](../../../visual-basic/language-reference/queries/select-clause.md)
- [Cláusula From](../../../visual-basic/language-reference/queries/from-clause.md)
- [Cláusula Skip](../../../visual-basic/language-reference/queries/skip-clause.md)
- [Cláusula Take While](../../../visual-basic/language-reference/queries/take-while-clause.md)
- [Cláusula Where](../../../visual-basic/language-reference/queries/where-clause.md)
