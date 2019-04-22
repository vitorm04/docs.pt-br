---
title: Valores de variável de objeto (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- object variables [Visual Basic], values
- values [Visual Basic], of object variables
- data types [Visual Basic], object variable
- variables [Visual Basic], object
ms.assetid: 31555704-58a3-49f1-9a0a-6421f605664f
ms.openlocfilehash: c17c5f85952596f0a080ca473e8f792740e66b8f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58840382"
---
# <a name="object-variable-values-visual-basic"></a>Valores de variável de objeto (Visual Basic)
Uma variável do [tipo de dados de objeto](../../../../visual-basic/language-reference/data-types/object-data-type.md) pode se referir a qualquer tipo de dados. O valor que você armazene em um `Object` variável é mantida em outro lugar na memória, enquanto a variável contém um ponteiro para os dados.  
  
## <a name="object-classifier-functions"></a>Funções de classificação do objeto  
 Visual Basic fornece funções que retornam informações sobre o que um `Object` variável refere-se a, conforme mostrado na tabela a seguir.  
  
|Função|Retorna VERDADEIRO se a variável de objeto se refere a|  
|--------------|---------------------------------------------------|  
|<xref:Microsoft.VisualBasic.Information.IsArray%2A>|Uma matriz de valores, em vez de um único valor|  
|<xref:Microsoft.VisualBasic.Information.IsDate%2A>|Um [tipo de dados Date](../../../../visual-basic/language-reference/data-types/date-data-type.md) valor ou uma cadeia de caracteres que pode ser interpretada como um valor de data e hora|  
|<xref:Microsoft.VisualBasic.Information.IsDBNull%2A>|Um objeto do tipo <xref:System.DBNull>, que representa dados ausentes ou inexistentes|  
|<xref:Microsoft.VisualBasic.Information.IsError%2A>|Um objeto de exceção, que deriva de <xref:System.Exception>|  
|<xref:Microsoft.VisualBasic.Information.IsNothing%2A>|[Nada](../../../../visual-basic/language-reference/nothing.md), ou seja, nenhum objeto atualmente atribuído à variável|  
|<xref:Microsoft.VisualBasic.Information.IsNumeric%2A>|Um número ou uma cadeia de caracteres que pode ser interpretada como um número|  
|<xref:Microsoft.VisualBasic.Information.IsReference%2A>|Um tipo de referência (como uma cadeia de caracteres, matriz, delegado ou tipo de classe)|  
  
 Você pode usar essas funções para evitar enviar um valor inválido para uma operação ou um procedimento.  
  
## <a name="typeof-operator"></a>Operador TypeOf  
 Você também pode usar o [operador TypeOf](../../../../visual-basic/language-reference/operators/typeof-operator.md) para determinar se uma variável de objeto no momento se refere a um tipo de dados específico. O `TypeOf`... `Is` expressão é avaliada como `True` se o tipo de tempo de execução do operando é derivado de ou implementa o tipo especificado.  
  
 O exemplo a seguir usa `TypeOf` em variáveis de objeto fazendo referência aos tipos de valor e referência.  
  
```  
' The following statement puts a value type (Integer) in an Object variable.  
Dim num As Object = 10  
' The following statement puts a reference type (Form) in an Object variable.  
Dim frm As Object = New Form()  
If TypeOf num Is Long Then Debug.WriteLine("num is Long")  
If TypeOf num Is Integer Then Debug.WriteLine("num is Integer")  
If TypeOf num Is Short Then Debug.WriteLine("num is Short")  
If TypeOf num Is Object Then Debug.WriteLine("num is Object")  
If TypeOf frm Is Form Then Debug.WriteLine("frm is Form")  
If TypeOf frm Is Label Then Debug.WriteLine("frm is Label")  
If TypeOf frm Is Object Then Debug.WriteLine("frm is Object")  
```  
  
 O exemplo anterior grava as seguintes linhas para o **depurar** janela:  
  
 `num is Integer`  
  
 `num is Object`  
  
 `frm is Form`  
  
 `frm is Object`  
  
 A variável de objeto `num` refere-se ao tipo de dados `Integer`, e `frm` refere-se a um objeto da classe <xref:System.Windows.Forms.Form>.  
  
## <a name="object-arrays"></a>Matrizes de objetos  
 Você pode declarar e usar uma matriz de `Object` variáveis. Isso é útil quando você precisar manipular uma variedade de tipos de dados e classes de objeto. Todos os elementos em uma matriz devem ter os mesmos dados declarados de tipo. Declarando esse tipo de dados como `Object` permite armazenar objetos e instâncias juntamente com outros tipos de dados na matriz de classe.  
  
## <a name="see-also"></a>Consulte também

- [Variáveis de Objeto](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [Declaração de Variável do Objeto](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)
- [Atribuição de variável do objeto](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)
- [Como: Fazer referência à instância atual de um objeto](../../../../visual-basic/programming-guide/language-features/variables/how-to-refer-to-the-current-instance-of-an-object.md)
- [Como: Determinar que tipo uma variável de objeto se refere a](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-what-type-an-object-variable-refers-to.md)
- [Como: Determinar se dois objetos estão relacionados](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-related.md)
- [Como: Determinar se dois objetos são idênticos](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-identical.md)
- [Tipos de Dados](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
