---
title: "Lista de par&#226;metros (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "argumentos [Visual Basic], Visual Basic"
  - "listas de parâmetros"
  - "parâmetros, listas"
  - "parâmetros, Visual Basic"
  - "procedimentos, listas de parâmetros"
  - "código do Visual Basic, listas de parâmetros"
  - "código do Visual Basic, procedimentos"
ms.assetid: 5d737319-0c34-4df9-a23d-188fc840becd
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Lista de par&#226;metros (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Especifica os parâmetros do procedimento quando é chamado.  Múltiplos parâmetros são separados por vírgulas.  O seguinte trecho é a sintaxe para um parâmetro.  
  
## Sintaxe  
  
```  
[ <attributelist> ] [ Optional ] [{ ByVal | ByRef }] [ ParamArray ]   
parametername[( )] [ As parametertype ] [ = defaultvalue ]  
```  
  
## Partes  
 `attributelist`  
 Opcional.  Lista de atributos que se aplicam a esse parâmetro.  Você delimitar a [Lista de atributos](../../../visual-basic/language-reference/statements/attribute-list.md) entre colchetes \("`<`" e "`>`"\).  
  
 `Optional`  
 Opcional.  Especifica que este parâmetro não é necessário quando o procedimento é chamado.  
  
 `ByVal`  
 Opcional.  Especifica que o procedimento não pode substituir or reatribuir o elemento variável dando suporte ao argumento correspondente num código de chamada.  
  
 `ByRef`  
 Opcional.  Especifica que o procedimento pode modificar o elemento variável oculto no código de chamada da mesma maneira que o código de chamada em si pode.  
  
 `ParamArray`  
 Opcional.  Especifica que o último parâmetro na lista de parâmetros é um array opcional de elementos do tipo de dados especificados.  Isso permite que o código de chamada passe um número arbitrário de argumentos ao procedimento.  
  
 `parametername`  
 Obrigatório.  Nome da variável local representando o parâmetro.  
  
 `parametertype`  
 Necessário se `Option Strict` estiver `On`.  Tipo de dados da variável local representando o parâmetro.  
  
 `defaultvalue`  
 Necessário para parâmetros `Optional`.  Qualquer constante ou expressão constante que avalia o tipo de dados do parâmetro.  Se o tipo é `Object`, ou uma classe, interface, array, ou estrutura, o valor padrão pode ser apenas `Nothing`.  
  
## Comentários  
 Parâmetros são rodeados por parênteses e separados por vírgulas.  Um parâmetro pode ser declarado com qualquer tipo de dados.  Se você não especificar `parametertype`, o padrão é `Object`.  
  
 Quando o código de chamada chama o procedimento, ele passa um *argumento* para cada parâmetro requisitado.  Para obter mais informações, consulte [Diferenças entre parâmetros e argumentos](../../../visual-basic/programming-guide/language-features/procedures/differences-between-parameters-and-arguments.md).  
  
 O argumento que o código de chamada passa para cada parâmetro é um ponteiro para um elemento oculto no código de chamada.  Se este elemento é*invariável* \(uma constante, literal, enumeração, ou expressão\), é impossível para qualquer código mudá\-lo.  Se é um elemento *variável* \(uma variável declarada, campo, propriedade, elemento de array, ou elemento de estrutura\), o código de chamada pode mudá\-lo.  Para obter mais informações, consulte [Diferenças entre argumentos modificáveis e não modificáveis](../../../visual-basic/programming-guide/language-features/procedures/differences-between-modifiable-and-nonmodifiable-arguments.md).  
  
 Se um elemento variável é passado `ByRef`, o procedimento pode mudá\-lo da mesma maneira.  Para obter mais informações, consulte [Diferenças entre passar um argumento por valor e por referência](../../../visual-basic/programming-guide/language-features/procedures/differences-between-passing-an-argument-by-value-and-by-reference.md).  
  
## Regras  
  
-   **Entre parênteses.** Se você especificar uma lista de parâmetro, você deve delimitá\-la entre parênteses.  Se não há parâmetros, você ainda pode usar parênteses delimitando uma lista vazia.  Isto melhora a legibilidade se seu código deixando mais claro que o elemento é um procedimento.  
  
-   **Parâmetros opcionais.** Se você usar o `Optional` modificador em um parâmetro, todos os parâmetros subseqüentes na lista também deve ser opcionais e ser declarados usando a `Optional` modificador.  
  
     Toda declaração de parâmetro opcional deve fornecer a cláusula `defaultvalue`.  
  
     Para obter mais informações, consulte [Parâmetros opcionais](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md).  
  
-   **Arrays de parâmetro.** Você deve especificar `ByVal` para um `ParamArray` parâmetro.  
  
     Você não pode usar ambos `Optional` e `ParamArray` na mesma lista de parâmetros.  
  
     Para obter mais informações, consulte [Matrizes de parâmetros](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md).  
  
-   **Mecanismo de Passagem.** O mecanismo padrão para cada argumento é `ByVal`, que significa que o procedimento não é possível alterar o elemento variável subjacente.  Entretanto, se o elemento é um tipo de referência, o procedimento pode modificar os conteúdos ou membros do objeto oculto, mesmo se ele mesmo não pode substituir ou reatribuir o objeto.  
  
-   **Nomes de parâmetro.** Se o tipo de dados do parâmetro for uma matriz, execute `parametername` imediatamente por parênteses.  Para mais informações sobre nomes de parâmetros, consulte [Nomes de elemento declarados](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).  
  
## Exemplo  
 O seguinte exemplo mostra um procedimento `Function` que define dois parâmetros.  
  
 [!code-vb[VbVbalrStatements#2](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/parameter-list_1.vb)]  
  
## Consulte também  
 <xref:System.Runtime.InteropServices.DllImportAttribute>   
 [Instrução Function](../../../visual-basic/language-reference/statements/function-statement.md)   
 [Instrução Sub](../../../visual-basic/language-reference/statements/sub-statement.md)   
 [Instrução Declare](../../../visual-basic/language-reference/statements/declare-statement.md)   
 [Instrução Structure](../../../visual-basic/language-reference/statements/structure-statement.md)   
 [Instrução Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md)   
 [Atributos](../Topic/Attributes%20\(C%23%20and%20Visual%20Basic\).md)   
 [Como quebrar e combinar instruções no código](../Topic/How%20to:%20Break%20and%20Combine%20Statements%20in%20Code%20\(Visual%20Basic\).md)