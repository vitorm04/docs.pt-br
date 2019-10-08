---
title: Cláusula Take While (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QueryTakeWhile
helpviewer_keywords:
- queries [Visual Basic], Take While
- Take While clause [Visual Basic]
- Take While statement [Visual Basic]
ms.assetid: db8f9f2f-fc9f-4a6c-b0b8-1bf048147e11
ms.openlocfilehash: fe6ee470698504bc0434930cc9aa6de712e04254
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004681"
---
# <a name="take-while-clause-visual-basic"></a>Cláusula Take While (Visual Basic)
Inclui elementos em uma coleção desde que uma condição especificada seja `true` e ignore os elementos restantes.  
  
## <a name="syntax"></a>Sintaxe  
  
```vb  
Take While expression  
```  
  
## <a name="parts"></a>Partes  
  
|Termo|Definição|  
|---|---|  
|`expression`|Necessário. Uma expressão que representa uma condição para os elementos de teste. A expressão deve retornar um valor `Boolean` ou um equivalente funcional, como um `Integer` a ser avaliado como um `Boolean`.|  
  
## <a name="remarks"></a>Comentários  
 A cláusula `Take While` inclui elementos do início de um resultado de consulta até que o `expression` fornecido retorne `false`. Depois que o `expression` retorna `false`, a consulta irá ignorar todos os elementos restantes. O `expression` é ignorado para os resultados restantes.  
  
 A cláusula `Take While` difere da cláusula `Where`, na qual a cláusula `Where` pode ser usada para incluir todos os elementos de uma consulta que atendam a uma condição específica. A cláusula `Take While` só inclui elementos até a primeira vez que a condição não for satisfeita. A cláusula `Take While` é mais útil quando você está trabalhando com um resultado de consulta ordenada.  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir usa a cláusula `Take While` para recuperar resultados até que o primeiro cliente sem nenhum pedido seja encontrado.  
  
 [!code-vb[VbSimpleQuerySamples#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#2)]  
  
## <a name="see-also"></a>Consulte também

- [Introdução ao LINQ no Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Consultas](../../../visual-basic/language-reference/queries/index.md)
- [Cláusula Select](../../../visual-basic/language-reference/queries/select-clause.md)
- [Cláusula From](../../../visual-basic/language-reference/queries/from-clause.md)
- [Cláusula Take](../../../visual-basic/language-reference/queries/take-clause.md)
- [Cláusula Skip While](../../../visual-basic/language-reference/queries/skip-while-clause.md)
- [Cláusula Where](../../../visual-basic/language-reference/queries/where-clause.md)
