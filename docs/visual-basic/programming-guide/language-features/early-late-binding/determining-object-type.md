---
title: Determinando o tipo de objeto (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- classes [Visual Basic], discovering which an object belongs to
- types [Visual Basic], determining Visual Basic object types
- object variables [Visual Basic], testing values
- TypeOf...Is expression, object type at run time
- TypeName function
- objects [Visual Basic], type determining
ms.assetid: d95e7ad1-cd63-41d6-9a28-d7a1380d49c1
ms.openlocfilehash: 4014bef2e0c27a0f6a684bc1ed95019f392062a5
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59302706"
---
# <a name="determining-object-type-visual-basic"></a>Determinando o tipo de objeto (Visual Basic)
Variáveis de objeto genérico (ou seja, as variáveis que você declare como `Object`) pode conter objetos de qualquer classe. Ao usar as variáveis do tipo `Object`, talvez você precise executar ações diferentes com base na classe do objeto; por exemplo, alguns objetos podem não dar suporte a uma determinada propriedade ou método. O Visual Basic fornece dois meios para determinar qual tipo de objeto é armazenado em uma variável de objeto: o `TypeName` função e o `TypeOf...Is` operador.  
  
## <a name="typename-and-typeofis"></a>TypeName e TypeOf... É  
 O `TypeName` função retorna uma cadeia de caracteres e é a melhor opção quando você precisa armazenar ou exibir o nome de classe de um objeto, conforme mostrado no seguinte fragmento de código:  
  
 [!code-vb[VbVbalrOOP#92](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#92)]  
  
 O `TypeOf...Is` operador é a melhor opção para testar o tipo de um objeto, porque ele é muito mais rápido que uma comparação de cadeia de caracteres equivalente usando `TypeName`. O fragmento de código a seguir usa `TypeOf...Is` dentro de um `If...Then...Else` instrução:  
  
 [!code-vb[VbVbalrOOP#93](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#93)]  
  
 Uma palavra de advertência aqui é devida. O `TypeOf...Is` operador retorna `True` se um objeto é de um tipo específico, ou é derivado de um tipo específico. Quase tudo o que fazer com o Visual Basic envolve a objetos, que incluem alguns elementos que não são considerados normalmente objetos, como cadeias de caracteres e inteiros. Esses objetos são derivados e herdam os métodos de <xref:System.Object>. Quando passado um `Integer` e avaliados com `Object`, o `TypeOf...Is` operador retorna `True`. O exemplo a seguir relata que o parâmetro `InParam` for tanto um `Object` e um `Integer`:  
  
 [!code-vb[VbVbalrOOP#94](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#94)]  
  
 O exemplo a seguir usa ambos `TypeOf...Is` e `TypeName` para determinar o tipo de objeto passado para ele no `Ctrl` argumento. O `TestObject` chamadas de procedimento `ShowType` com três tipos diferentes de controles.  
  
#### <a name="to-run-the-example"></a>Para executar o exemplo  
  
1. Criar um novo projeto de aplicativo do Windows e adicione uma <xref:System.Windows.Forms.Button> controle, um <xref:System.Windows.Forms.CheckBox> controle e um <xref:System.Windows.Forms.RadioButton> controle ao formulário.  
  
2. Com o botão no formulário, chame o `TestObject` procedimento.  
  
3. Adicione o seguinte código ao seu formulário:  
  
     [!code-vb[VbVbalrOOP#95](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#95)]  
  
## <a name="see-also"></a>Consulte também

- <xref:Microsoft.VisualBasic.Information.TypeName%2A>
- [Chamando uma propriedade ou um método usando o nome de uma cadeia de caracteres](../../../../visual-basic/programming-guide/language-features/early-late-binding/calling-a-property-or-method-using-a-string-name.md)
- [Tipo de dados Object](../../../../visual-basic/language-reference/data-types/object-data-type.md)
- [Instrução If...Then...Else](../../../../visual-basic/language-reference/statements/if-then-else-statement.md)
- [Tipo de dados da cadeia de caracteres](../../../../visual-basic/language-reference/data-types/string-data-type.md)
- [Tipo de dados inteiro](../../../../visual-basic/language-reference/data-types/integer-data-type.md)
