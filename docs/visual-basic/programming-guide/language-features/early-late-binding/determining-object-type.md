---
title: Determinando o tipo de objeto (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- classes [Visual Basic], discovering which an object belongs to
- types [Visual Basic], determining Visual Basic object types
- object variables [Visual Basic], testing values
- TypeOf...Is expression, object type at run time
- TypeName function
- objects [Visual Basic], type determining
ms.assetid: d95e7ad1-cd63-41d6-9a28-d7a1380d49c1
caps.latest.revision: 13
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a6d24be68ea4a9872f8f4fe89c1aabb943fbcb91
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="determining-object-type-visual-basic"></a>Determinando o tipo de objeto (Visual Basic)
Variáveis de objeto genérico (ou seja, variáveis que você declare como `Object`) pode conter objetos de qualquer classe. Ao usar variáveis do tipo `Object`, talvez seja necessário executar ações diferentes com base na classe do objeto; por exemplo, alguns objetos podem não dar suporte a uma determinada propriedade ou método. Visual Basic fornece dois meios de determinar que tipo de objeto é armazenado em uma variável de objeto: o `TypeName` função e o `TypeOf...Is` operador.  
  
## <a name="typename-and-typeofis"></a>TypeName e TypeOf... É  
 O `TypeName` função retorna uma cadeia de caracteres e é a melhor opção quando você precisa armazenar ou exibir o nome da classe de um objeto, como mostrado no fragmento de código a seguir:  
  
 [!code-vb[VbVbalrOOP#92](../../../../visual-basic/misc/codesnippet/VisualBasic/determining-object-type_1.vb)]  
  
 O `TypeOf...Is` operador é a melhor opção para testar de tipo um objeto, porque ele é muito mais rápido que uma comparação de cadeia de caracteres equivalente usando `TypeName`. O fragmento de código a seguir usa `TypeOf...Is` dentro de um `If...Then...Else` instrução:  
  
 [!code-vb[VbVbalrOOP#93](../../../../visual-basic/misc/codesnippet/VisualBasic/determining-object-type_2.vb)]  
  
 Uma palavra de advertência é conclusão aqui. O `TypeOf...Is` operador retorna `True` se um objeto é de um tipo específico, ou é derivado de um tipo específico. Quase tudo o que fazer com o Visual Basic envolve a objetos, que incluem alguns elementos que normalmente não são considerados objetos, como cadeias de caracteres e inteiros. Esses objetos são derivados do e herda os métodos de <xref:System.Object>. Quando passado um `Integer` e avaliadas com `Object`, o `TypeOf...Is` operador retornará `True`. O exemplo a seguir relata que o parâmetro `InParam` é um `Object` e um `Integer`:  
  
 [!code-vb[VbVbalrOOP#94](../../../../visual-basic/misc/codesnippet/VisualBasic/determining-object-type_3.vb)]  
  
 O exemplo a seguir usa `TypeOf...Is` e `TypeName` para determinar o tipo de objeto passado para ele no `Ctrl` argumento. O `TestObject` chamadas de procedimento `ShowType` com três tipos diferentes de controles.  
  
#### <a name="to-run-the-example"></a>Para executar o exemplo  
  
1.  Criar um novo projeto de aplicativo do Windows e adicionar um <xref:System.Windows.Forms.Button> controle, uma <xref:System.Windows.Forms.CheckBox> controle e um <xref:System.Windows.Forms.RadioButton> controle no formulário.  
  
2.  Com o botão do formulário, chame o `TestObject` procedimento.  
  
3.  Adicione o seguinte código ao formulário:  
  
     [!code-vb[VbVbalrOOP#95](../../../../visual-basic/misc/codesnippet/VisualBasic/determining-object-type_4.vb)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualBasic.Information.TypeName%2A>  
 [Chamando uma Propriedade ou um Método Usando o Nome de uma Cadeia de Caracteres](../../../../visual-basic/programming-guide/language-features/early-late-binding/calling-a-property-or-method-using-a-string-name.md)  
 [Tipo de Dados Object](../../../../visual-basic/language-reference/data-types/object-data-type.md)  
 [Instrução If...Then...Else](../../../../visual-basic/language-reference/statements/if-then-else-statement.md)  
 [Tipo de Dados String](../../../../visual-basic/language-reference/data-types/string-data-type.md)  
 [Tipo de Dados Integer](../../../../visual-basic/language-reference/data-types/integer-data-type.md)
