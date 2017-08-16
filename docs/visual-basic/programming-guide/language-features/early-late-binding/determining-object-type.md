---
title: Determinando o tipo de objeto (Visual Basic) | Documentos do Microsoft
ms.custom: 
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
- classes [Visual Basic], discovering which an object belongs to
- types [Visual Basic], determining Visual Basic object types
- object variables, testing values
- TypeOf...Is expression, object type at run time
- TypeName function
- objects [Visual Basic], type determining
ms.assetid: d95e7ad1-cd63-41d6-9a28-d7a1380d49c1
caps.latest.revision: 13
author: dotnet-bot
ms.author: dotnetcontent
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
ms.openlocfilehash: 2486d989801fc4866a50747aa963b509a627994d
ms.lasthandoff: 03/13/2017

---
# <a name="determining-object-type-visual-basic"></a>Determinando o tipo de objeto (Visual Basic)
Variáveis de objeto genérico (ou seja, variáveis que você declara como `Object`) pode conter objetos de qualquer classe. Ao usar variáveis do tipo `Object`, talvez você precise executar ações diferentes com base na classe de objeto; por exemplo, alguns objetos podem não oferecer suporte a uma determinada propriedade ou método. [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]fornece dois meios de determinar qual tipo de objeto é armazenado em uma variável de objeto: o `TypeName` função e o `TypeOf...Is` operador.  
  
## <a name="typename-and-typeofis"></a>TypeName e TypeOf... É  
 O `TypeName` função retorna uma cadeia de caracteres e é a melhor opção quando você precisa armazenar ou exibir o nome da classe de um objeto, conforme mostrado no fragmento de código a seguir:  
  
 [!code-vb[VbVbalrOOP&#92;](../../../../visual-basic/misc/codesnippet/VisualBasic/determining-object-type_1.vb)]  
  
 O `TypeOf...Is` operador é a melhor opção para testar tipo de um objeto, pois é muito mais rápido do que uma comparação de cadeia de caracteres equivalente usando `TypeName`. O fragmento de código a seguir usa `TypeOf...Is` dentro de um `If...Then...Else` instrução:  
  
 [!code-vb[VbVbalrOOP&#93;](../../../../visual-basic/misc/codesnippet/VisualBasic/determining-object-type_2.vb)]  
  
 Uma nota de advertência aqui é devida. O `TypeOf...Is` operador retorna `True` se um objeto for de um tipo específico, ou é derivado de um tipo específico. Quase tudo o que fazer com [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] envolve objetos, que incluem alguns elementos que normalmente não são considerados objetos, como cadeias de caracteres e inteiros. Esses objetos são derivados de e herdam métodos de <xref:System.Object>.</xref:System.Object> Quando passado um `Integer` e avaliadas com `Object`, o `TypeOf...Is` retornará `True`. O exemplo a seguir relata que o parâmetro `InParam` tanto uma `Object` e um `Integer`:  
  
 [!code-vb[VbVbalrOOP&#94;](../../../../visual-basic/misc/codesnippet/VisualBasic/determining-object-type_3.vb)]  
  
 O exemplo a seguir usa `TypeOf...Is` e `TypeName` para determinar o tipo de objeto passado para ele no `Ctrl` argumento. O `TestObject` chamadas de procedimento `ShowType` com três tipos diferentes de controles.  
  
#### <a name="to-run-the-example"></a>Para executar o exemplo  
  
1.  Criar um novo projeto de aplicativo do Windows e adicionar um <xref:System.Windows.Forms.Button>controle, um <xref:System.Windows.Forms.CheckBox>controle e um <xref:System.Windows.Forms.RadioButton>controle ao formulário.</xref:System.Windows.Forms.RadioButton> </xref:System.Windows.Forms.CheckBox> </xref:System.Windows.Forms.Button>  
  
2.  Com o botão no formulário, chame o `TestObject` procedimento.  
  
3.  Adicione o seguinte código ao seu formulário:  
  
     [!code-vb[VbVbalrOOP&#95;](../../../../visual-basic/misc/codesnippet/VisualBasic/determining-object-type_4.vb)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualBasic.Information.TypeName%2A></xref:Microsoft.VisualBasic.Information.TypeName%2A>   
 [Chamando uma propriedade ou método usando um nome de cadeia de caracteres](../../../../visual-basic/programming-guide/language-features/early-late-binding/calling-a-property-or-method-using-a-string-name.md)   
 [Tipo de dados Object](../../../../visual-basic/language-reference/data-types/object-data-type.md)   
 [If... Then... Instrução else](../../../../visual-basic/language-reference/statements/if-then-else-statement.md)   
 [Tipo de dados String](../../../../visual-basic/language-reference/data-types/string-data-type.md)   
 [Tipo de Dados Integer](../../../../visual-basic/language-reference/data-types/integer-data-type.md)
