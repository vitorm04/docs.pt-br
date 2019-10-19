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
ms.openlocfilehash: 0dded7fd68256b9b9de8ebe4b48073eb40696c12
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582177"
---
# <a name="parameter-list-visual-basic"></a>Lista de parâmetros (Visual Basic)

Especifica os parâmetros que um procedimento espera quando é chamado. Vários parâmetros são separados por vírgulas. Veja a seguir a sintaxe de um parâmetro.

## <a name="syntax"></a>Sintaxe

```vb
[ <attributelist> ] [ Optional ] [{ ByVal | ByRef }] [ ParamArray ]
parametername[( )] [ As parametertype ] [ = defaultvalue ]
```

## <a name="parts"></a>Partes

`attributelist`  
Opcional. Lista de atributos que se aplicam a esse parâmetro. Você deve colocar a [lista de atributos](../../../visual-basic/language-reference/statements/attribute-list.md) entre colchetes angulares ("`<`" e "`>`").

`Optional`  
Opcional. Especifica que esse parâmetro não é necessário quando o procedimento é chamado.

`ByVal`  
Opcional. Especifica que o procedimento não pode substituir ou reatribuir o elemento Variable subjacente ao argumento correspondente no código de chamada.

`ByRef`  
Opcional. Especifica que o procedimento pode modificar o elemento variável subjacente no código de chamada da mesma maneira que o próprio código de chamada pode.

`ParamArray`  
Opcional. Especifica que o último parâmetro na lista de parâmetros é uma matriz opcional de elementos do tipo de dados especificado. Isso permite que o código de chamada passe um número arbitrário de argumentos para o procedimento.

`parametername`  
Necessário. Nome da variável local que representa o parâmetro.

`parametertype`  
Necessário se `Option Strict` for `On`. Tipo de dados da variável local que representa o parâmetro.

`defaultvalue`  
Necessário para parâmetros de `Optional`. Qualquer expressão constante ou constante que seja avaliada como o tipo de dados do parâmetro. Se o tipo for `Object` ou uma classe, interface, matriz ou estrutura, o valor padrão só poderá ser `Nothing`.

## <a name="remarks"></a>Comentários

Os parâmetros são circundados por parênteses e separados por vírgulas. Um parâmetro pode ser declarado com qualquer tipo de dados. Se você não especificar `parametertype`, o padrão será `Object`.

Quando o código de chamada chama o procedimento, ele passa um *argumento* para cada parâmetro necessário. Para obter mais informações, consulte [diferenças entre parâmetros e argumentos](../../../visual-basic/programming-guide/language-features/procedures/differences-between-parameters-and-arguments.md).

O argumento que o código de chamada passa para cada parâmetro é um ponteiro para um elemento subjacente no código de chamada. Se esse elemento não for *variável* (uma constante, literal, enumeração ou expressão), será impossível para qualquer código alterá-lo. Se for um elemento *variável* (uma variável declarada, um campo, uma propriedade, um elemento de matriz ou um elemento de estrutura), o código de chamada poderá alterá-lo. Para obter mais informações, consulte [diferenças entre argumentos modificáveis e não modificáveis](../../../visual-basic/programming-guide/language-features/procedures/differences-between-modifiable-and-nonmodifiable-arguments.md).

Se um elemento variable for passado `ByRef`, o procedimento também poderá alterá-lo. Para obter mais informações, consulte [diferenças entre passar um argumento por valor e por referência](../../../visual-basic/programming-guide/language-features/procedures/differences-between-passing-an-argument-by-value-and-by-reference.md).

## <a name="rules"></a>Regras

- **Parênteses.** Se você especificar uma lista de parâmetros, deverá colocá-la entre parênteses. Se não houver parâmetros, você ainda poderá usar parênteses delimitando uma lista vazia. Isso melhora a legibilidade do seu código, esclarecendo que o elemento é um procedimento.

- **Parâmetros opcionais.** Se você usar o modificador `Optional` em um parâmetro, todos os parâmetros subsequentes na lista também deverão ser opcionais e declarados usando o modificador `Optional`.

     Cada declaração de parâmetro opcional deve fornecer a cláusula `defaultvalue`.

     Para obter mais informações, consulte [parâmetros opcionais](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md).

- **Matrizes de parâmetros.** Você deve especificar `ByVal` para um parâmetro `ParamArray`.

     Você não pode usar `Optional` e `ParamArray` na mesma lista de parâmetros.

     Para obter mais informações, consulte [matrizes de parâmetros](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md).

- **Mecanismo de passagem.** O mecanismo padrão para cada argumento é `ByVal`, o que significa que o procedimento não pode alterar o elemento de variável subjacente. No entanto, se o elemento for um tipo de referência, o procedimento poderá modificar o conteúdo ou os membros do objeto subjacente, mesmo que ele não possa substituir ou reatribuir o próprio objeto.

- **Nomes de parâmetro.** Se o tipo de dados do parâmetro for uma matriz, siga `parametername` imediatamente por parênteses. Para obter mais informações sobre nomes de parâmetro, consulte [nomes de elemento declarados](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).

## <a name="example"></a>Exemplo

O exemplo a seguir mostra um procedimento `Function` que define dois parâmetros.

[!code-vb[VbVbalrStatements#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#2)]

## <a name="see-also"></a>Consulte também

- <xref:System.Runtime.InteropServices.DllImportAttribute>
- [Instrução Function](../../../visual-basic/language-reference/statements/function-statement.md)
- [Instrução Sub](../../../visual-basic/language-reference/statements/sub-statement.md)
- [Instrução Declare](../../../visual-basic/language-reference/statements/declare-statement.md)
- [Instrução Structure](../../../visual-basic/language-reference/statements/structure-statement.md)
- [Instrução Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [Visão geral de atributos](../../../visual-basic/programming-guide/concepts/attributes/index.md)
- [Como quebrar e combinar instruções no código](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)
