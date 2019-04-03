---
title: Operador GetType (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.GetType
helpviewer_keywords:
- GetType operator [Visual Basic]
- GetType keyword [Visual Basic]
ms.assetid: 4f733297-2503-4607-850c-15eba65fff90
ms.openlocfilehash: 34ab192814583db5cdc0d0183c73cc22b8633e9c
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58840309"
---
# <a name="gettype-operator-visual-basic"></a>Operador GetType (Visual Basic)
Retorna um <xref:System.Type> objeto para o tipo especificado. O <xref:System.Type> objeto fornece informações sobre o tipo como suas propriedades, métodos e eventos.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
GetType(typename)  
```  
  
## <a name="parameters"></a>Parâmetros  
  
|Parâmetro|Descrição|  
|---|---|  
|`typename`|O nome do tipo do qual você deseja informações.|  
  
## <a name="remarks"></a>Comentários  
 O `GetType` operador retorna o <xref:System.Type> o objeto especificado `typename`. Você pode passar o nome de qualquer tipo definido em `typename`. Isso inclui o seguinte:  
  
-   Tipo de dados de qualquer Visual Basic, como `Boolean` ou `Date`.  
  
-   Qualquer classe do .NET Framework, estrutura, módulo ou interface, tais como <xref:System.ArgumentException?displayProperty=nameWithType> ou <xref:System.Double?displayProperty=nameWithType>.  
  
-   Qualquer classe, estrutura, módulo ou interface definida por seu aplicativo.  
  
-   Qualquer matriz definida por seu aplicativo.  
  
-   Qualquer delegado definido pelo seu aplicativo.  
  
-   Qualquer enumeração definida por seu aplicativo, o .NET Framework ou Visual Basic.  
  
 Se você deseja obter o objeto do tipo de uma variável de objeto, use o <xref:System.Type.GetType%2A?displayProperty=nameWithType> método.  
  
 O `GetType` operador pode ser útil nas seguintes circunstâncias:  
  
-   Você deve acessar os metadados para um tipo em tempo de execução. O <xref:System.Type> objeto fornece metadados como membros de tipo e informações de implantação. Você precisa, por exemplo, para refletir sobre um assembly. Para obter mais informações, consulte <xref:System.Reflection?displayProperty=nameWithType>.  
  
-   Você deseja comparar duas referências de objeto para ver se elas se referem a instâncias do mesmo tipo. Se Sim, `GetType` retorna referências para o mesmo <xref:System.Type> objeto.  
  
## <a name="example"></a>Exemplo  
 Os exemplos a seguir mostram o `GetType` operador em uso.  
  
 [!code-vb[VbVbalrOperators#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#26)]  
  
## <a name="see-also"></a>Consulte também

- [Precedência do operador no Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Operadores Listados por Funcionalidade](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Operadores e Expressões](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
