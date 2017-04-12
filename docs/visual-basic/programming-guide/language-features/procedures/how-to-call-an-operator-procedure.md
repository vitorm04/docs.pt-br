---
title: 'Como: chamar um procedimento de operador (Visual Basic) | Documentos do Microsoft'
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
- operator procedures, calling
- procedures, operator
- procedure calls, operator overloading
- syntax, Operator procedures
- operators [Visual Basic], overloading
- return values, Operator procedures
- overloaded operators, calling
- operator overloading
ms.assetid: 0dce42cc-f0b0-4c14-9f62-018b21f33497
caps.latest.revision: 16
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
ms.openlocfilehash: 2403e7a8270c17a8db5417cd8394fd47c373d493
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-call-an-operator-procedure-visual-basic"></a>Como chamar um procedimento de operador (Visual Basic)
Você pode chamar um procedimento de operador usando o símbolo do operador em uma expressão. No caso de um operador de conversão, você chama o [função CType](../../../../visual-basic/language-reference/functions/ctype-function.md) para converter um valor de um tipo de dados para outro.  
  
 Você não chama explicitamente procedimentos de operador. Você apenas usa o operador, ou o `CType` função em uma instrução de atribuição ou uma expressão, da mesma maneira que você normalmente usa um operador. [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]faz a chamada para o procedimento de operador.  
  
 Definir um operador em uma classe ou estrutura também é chamado *sobrecarga* o operador.  
  
### <a name="to-call-an-operator-procedure"></a>Para chamar um procedimento de operador  
  
1.  Use o símbolo do operador em uma expressão na forma comum.  
  
2.  Certifique-se de que os tipos de dados dos operandos são apropriados para o operador e estão na ordem correta.  
  
3.  O operador contribui para o valor da expressão conforme o esperado.  
  
### <a name="to-call-a-conversion-operator-procedure"></a>Para chamar um procedimento de operador de conversão  
  
1.  Use `CType` dentro de uma expressão.  
  
2.  Certifique-se de que os tipos de dados dos operandos são apropriados para a conversão e estão na ordem correta.  
  
3.  `CType`chama o procedimento de operador de conversão e retorna o valor convertido.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir cria dois <xref:System.TimeSpan>estruturas, adiciona-as e armazena o resultado em uma terceira <xref:System.TimeSpan>estrutura.</xref:System.TimeSpan> </xref:System.TimeSpan> O <xref:System.TimeSpan>estrutura define procedimentos de operador para sobrecarregar vários operadores padrão.</xref:System.TimeSpan>  
  
 [!code-vb[29 VbVbcnProcedures](./codesnippet/VisualBasic/how-to-call-an-operator-procedure_1.vb)]  
  
 Porque <xref:System.TimeSpan>sobrecarrega o padrão `+` operador, o exemplo anterior chama um procedimento de operador quando ele calcula o valor de `combinedSpan`.</xref:System.TimeSpan>  
  
 Para obter um exemplo de chamar um procedimento de operador de conversa, consulte [como: usar uma classe que define operadores](./how-to-use-a-class-that-defines-operators.md).  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Certifique-se de que a classe ou estrutura que você está usando define o operador que você deseja usar.  
  
## <a name="see-also"></a>Consulte também  
 [Procedimentos de operador](./operator-procedures.md)   
 [Como: definir um operador](./how-to-define-an-operator.md)   
 [Como: definir um operador de conversão](./how-to-define-a-conversion-operator.md)   
 [Instrução Operator](../../../../visual-basic/language-reference/statements/operator-statement.md)   
 [Ampliação](../../../../visual-basic/language-reference/modifiers/widening.md)   
 [Narrowing](../../../../visual-basic/language-reference/modifiers/narrowing.md)   
 [Instrução Structure](../../../../visual-basic/language-reference/statements/structure-statement.md)   
 [Como: declarar uma estrutura](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)   
 [Conversões implícitas e explícitas](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)   
 [Conversões de Widening e Narrowing](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
