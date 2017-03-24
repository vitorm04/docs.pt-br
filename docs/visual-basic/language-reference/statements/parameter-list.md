---
title: "Lista de parâmetros (Visual Basic) | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- Visual Basic code, procedures
- parameters, Visual Basic
- parameters, lists
- parameter lists
- Visual Basic code, parameter lists
- arguments [Visual Basic], Visual Basic
- procedures, parameter lists
ms.assetid: 5d737319-0c34-4df9-a23d-188fc840becd
caps.latest.revision: 19
author: stevehoag
ms.author: shoag
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
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: abadaa8e035bfa4c92acc30ab633d6a7e958676c
ms.lasthandoff: 03/13/2017

---
# <a name="parameter-list-visual-basic"></a>Lista de parâmetros (Visual Basic)
Especifica os parâmetros do procedimento quando é chamado. Vários parâmetros são separados por vírgulas. A seguir está a sintaxe de um parâmetro.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
[ <attributelist> ] [ Optional ] [{ ByVal | ByRef }] [ ParamArray ]   
parametername[( )] [ As parametertype ] [ = defaultvalue ]  
```  
  
## <a name="parts"></a>Partes  
 `attributelist`  
 Opcional. Lista de atributos que se aplicam a esse parâmetro. Você deve colocar o [a lista de atributos](../../../visual-basic/language-reference/statements/attribute-list.md) entre colchetes angulares ("`<`"e"`>`").  
  
 `Optional`  
 Opcional. Especifica que este parâmetro não é necessário quando o procedimento é chamado.  
  
 `ByVal`  
 Opcional. Especifica que o procedimento não pode substituir ou reatribuir o elemento variável subjacente ao argumento correspondente no código de chamada.  
  
 `ByRef`  
 Opcional. Especifica que o procedimento pode modificar o elemento variável subjacente no código de chamada da mesma forma que o código de chamada em si pode.  
  
 `ParamArray`  
 Opcional. Especifica que o último parâmetro na lista de parâmetros é uma matriz opcional de elementos do tipo de dados especificado. Isso permite que o código de chamada passe um número arbitrário de argumentos para o procedimento.  
  
 `parametername`  
 Necessário. Nome da variável local representando o parâmetro.  
  
 `parametertype`  
 Necessário se `Option Strict` é `On`. Tipo de dados da variável local representando o parâmetro.  
  
 `defaultvalue`  
 Necessário para `Optional` parâmetros. Qualquer constante ou expressão constante que é avaliada como o tipo de dados do parâmetro. Se o tipo for `Object`, ou uma classe, interface, matriz ou estrutura, o valor padrão só pode ser `Nothing`.  
  
## <a name="remarks"></a>Comentários  
 Parâmetros estão entre parênteses e separados por vírgulas. Um parâmetro pode ser declarado com qualquer tipo de dados. Se você não especificar `parametertype`, o padrão é `Object`.  
  
 Quando o código de chamada chama o procedimento, ele passa um *argumento* para cada parâmetro necessário. Para obter mais informações, consulte [as diferenças entre parâmetros e argumentos](../../../visual-basic/programming-guide/language-features/procedures/differences-between-parameters-and-arguments.md).  
  
 O argumento que o código de chamada passa para cada parâmetro é um ponteiro para um elemento subjacente no código de chamada. Se este elemento é *invariável* (uma constante, literal, enumeração ou expressão), é impossível para qualquer código mudá-lo. Se for um *variável* elemento (uma variável declarada, campo, propriedade, elemento de matriz ou elemento de estrutura), o código de chamada pode alterá-lo. Para obter mais informações, consulte [as diferenças entre modificáveis e não modificáveis argumentos](../../../visual-basic/programming-guide/language-features/procedures/differences-between-modifiable-and-nonmodifiable-arguments.md).  
  
 Se um elemento variável é passado `ByRef`, o procedimento pode alterá-lo também. Para obter mais informações, consulte [as diferenças entre passar um argumento por valor e por referência](../../../visual-basic/programming-guide/language-features/procedures/differences-between-passing-an-argument-by-value-and-by-reference.md).  
  
## <a name="rules"></a>Regras  
  
-   **Parênteses.** Se você especificar uma lista de parâmetros, você deve colocá-la entre parênteses. Se não houver nenhum parâmetro, você ainda pode usar parênteses delimitando uma lista vazia. Isso melhora a legibilidade do código deixando mais claro que o elemento é um procedimento.  
  
-   **Parâmetros opcionais.** Se você usar o `Optional` modificador em um parâmetro, todos os parâmetros subsequentes na lista também deve ser opcionais e sejam declarados usando o `Optional` modificador.  
  
     Cada declaração de parâmetro opcional deve fornecer a `defaultvalue` cláusula.  
  
     Para obter mais informações, consulte [parâmetros opcionais](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md).  
  
-   **Matrizes de parâmetros.** Você deve especificar `ByVal` para um `ParamArray` parâmetro.  
  
     Não é possível usar ambos `Optional` e `ParamArray` na mesma lista de parâmetros.  
  
     Para obter mais informações, consulte [matrizes de parâmetros](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md).  
  
-   **Mecanismo de passagem.** É o mecanismo padrão para cada argumento `ByVal`, que significa que o procedimento não pode alterar o elemento variável subjacente. No entanto, se o elemento for um tipo de referência, o procedimento pode modificar os conteúdos ou membros do objeto subjacente, mesmo que não é possível substituir ou reatribuir o objeto.  
  
-   **Nomes de parâmetro.** Se o tipo de dados do parâmetro é uma matriz, execute `parametername` imediatamente por parênteses. Para obter mais informações sobre nomes de parâmetro, consulte [nomes de elemento declarado](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).  
  
## <a name="example"></a>Exemplo  
 A exemplo a seguir mostra uma `Function` procedimento que define dois parâmetros.  
  
 [!code-vb[VbVbalrStatements n º&2;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/parameter-list_1.vb)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Runtime.InteropServices.DllImportAttribute></xref:System.Runtime.InteropServices.DllImportAttribute>   
 [Instrução Function](../../../visual-basic/language-reference/statements/function-statement.md)   
 [Instrução sub](../../../visual-basic/language-reference/statements/sub-statement.md)   
 [Instrução Declare](../../../visual-basic/language-reference/statements/declare-statement.md)   
 [Instrução Structure](../../../visual-basic/language-reference/statements/structure-statement.md)   
 [Instrução Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md)   
 [Visão geral de atributos](../../../visual-basic/programming-guide/concepts/attributes/index.md)   
 [Como quebrar e combinar instruções no código](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)
