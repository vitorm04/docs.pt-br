---
title: Lista de parâmetros (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- parameters [Visual Basic], Visual Basic
- parameters [Visual Basic], lists
- parameter lists [Visual Basic]
- Visual Basic code, parameter lists
- arguments [Visual Basic], Visual Basic
- procedures [Visual Basic], parameter lists
ms.assetid: 5d737319-0c34-4df9-a23d-188fc840becd
ms.openlocfilehash: 651f08812032aa1c5aacc04fdb3d7f491f12b607
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58836279"
---
# <a name="parameter-list-visual-basic"></a>Lista de parâmetros (Visual Basic)
Especifica os parâmetros do procedimento quando ele é chamado. Vários parâmetros são separados por vírgulas. A seguir está a sintaxe para um parâmetro.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
[ <attributelist> ] [ Optional ] [{ ByVal | ByRef }] [ ParamArray ]   
parametername[( )] [ As parametertype ] [ = defaultvalue ]  
```  
  
## <a name="parts"></a>Partes  
 `attributelist`  
 Opcional. Lista de atributos que se aplicam a esse parâmetro. Você deve colocar o [lista de atributos](../../../visual-basic/language-reference/statements/attribute-list.md) colchetes angulares ("`<`"e"`>`").  
  
 `Optional`  
 Opcional. Especifica que esse parâmetro não é necessário quando o procedimento é chamado.  
  
 `ByVal`  
 Opcional. Especifica que o procedimento não é possível substituir ou reatribuir o elemento variável subjacente ao argumento correspondente no código de chamada.  
  
 `ByRef`  
 Opcional. Especifica que o procedimento pode modificar o elemento subjacente de variável no código de chamada da mesma forma que o código de chamada pode.  
  
 `ParamArray`  
 Opcional. Especifica que o último parâmetro na lista de parâmetros é uma matriz opcional de elementos do tipo de dados especificado. Isso permite que o código de chamada passar um número arbitrário de argumentos para o procedimento.  
  
 `parametername`  
 Necessário. Nome da variável local representando o parâmetro.  
  
 `parametertype`  
 Necessário se `Option Strict` é `On`. Tipo de dados da variável local representando o parâmetro.  
  
 `defaultvalue`  
 Necessário para `Optional` parâmetros. Qualquer constante ou expressão constante que é avaliada para o tipo de dados do parâmetro. Se o tipo for `Object`, ou uma classe, interface, array ou estrutura, o valor padrão só pode ser `Nothing`.  
  
## <a name="remarks"></a>Comentários  
 Parâmetros estão entre parênteses e separados por vírgulas. Um parâmetro pode ser declarado com qualquer tipo de dados. Se você não especificar `parametertype`, o padrão é `Object`.  
  
 Quando o código de chamada chama o procedimento, ele passa um *argumento* para cada parâmetro obrigatório. Para obter mais informações, consulte [diferenças entre parâmetros e argumentos](../../../visual-basic/programming-guide/language-features/procedures/differences-between-parameters-and-arguments.md).  
  
 O argumento que o código de chamada passa para cada parâmetro é um ponteiro para um elemento subjacente no código de chamada. Se esse elemento estiver *invariável* (uma constante, literal, enumeração ou expressão), é impossível para qualquer código para alterá-lo. Se for um *variável* elemento (uma variável declarada, campo, propriedade, o elemento de matriz ou elemento de estrutura), o código de chamada pode alterá-lo. Para obter mais informações, consulte [diferenças entre modificáveis e não modificáveis argumentos](../../../visual-basic/programming-guide/language-features/procedures/differences-between-modifiable-and-nonmodifiable-arguments.md).  
  
 Se um elemento variável é passado `ByRef`, o procedimento pode alterá-lo também. Para obter mais informações, consulte [diferenças entre passar um argumento por valor e por referência](../../../visual-basic/programming-guide/language-features/procedures/differences-between-passing-an-argument-by-value-and-by-reference.md).  
  
## <a name="rules"></a>Regras  
  
-   **Parênteses.** Se você especificar uma lista de parâmetros, você deve colocá-la entre parênteses. Se não houver nenhum parâmetro, você ainda pode usar parênteses que incluem uma lista vazia. Isso melhora a legibilidade do código ao esclarecer que o elemento é um procedimento.  
  
-   **Parâmetros opcionais.** Se você usar o `Optional` modificador em um parâmetro, todos os parâmetros subsequentes na lista também devem ser opcionais e sejam declarados usando o `Optional` modificador.  
  
     Cada declaração de parâmetro opcional deve fornecer o `defaultvalue` cláusula.  
  
     Para obter mais informações, consulte [parâmetros opcionais](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md).  
  
-   **Matrizes de parâmetros.** Você deve especificar `ByVal` para um `ParamArray` parâmetro.  
  
     É possível usar ambos `Optional` e `ParamArray` na mesma lista de parâmetros.  
  
     Para obter mais informações, consulte [matrizes de parâmetro](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md).  
  
-   **Mecanismo de passagem.** O mecanismo padrão para cada argumento é `ByVal`, que significa que o procedimento não é possível alterar o elemento variável subjacente. No entanto, se o elemento for um tipo de referência, o procedimento pode modificar o conteúdo ou os membros do objeto subjacente, mesmo que ele não é possível substituir ou reatribuir o próprio objeto.  
  
-   **Nomes de parâmetro.** Se o tipo de dados do parâmetro é uma matriz, siga `parametername` imediatamente por parênteses. Para obter mais informações sobre nomes de parâmetro, consulte [nomes de elemento declarado](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).  
  
## <a name="example"></a>Exemplo  
 A exemplo a seguir mostra um `Function` procedimento que define dois parâmetros.  
  
 [!code-vb[VbVbalrStatements#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#2)]  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Runtime.InteropServices.DllImportAttribute>
- [Instrução Function](../../../visual-basic/language-reference/statements/function-statement.md)
- [Instrução Sub](../../../visual-basic/language-reference/statements/sub-statement.md)
- [Instrução Declare](../../../visual-basic/language-reference/statements/declare-statement.md)
- [Instrução Structure](../../../visual-basic/language-reference/statements/structure-statement.md)
- [Instrução Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [Visão geral de atributos](../../../visual-basic/programming-guide/concepts/attributes/index.md)
- [Como: quebrar e combinar instruções no código](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)
