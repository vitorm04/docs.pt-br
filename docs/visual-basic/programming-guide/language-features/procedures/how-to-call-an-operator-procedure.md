---
title: Como chamar um procedimento de operador
ms.date: 07/20/2015
helpviewer_keywords:
- operator procedures [Visual Basic], calling
- procedures [Visual Basic], operator
- procedure calls [Visual Basic], operator overloading
- syntax [Visual Basic], Operator procedures
- operators [Visual Basic], overloading
- return values [Visual Basic], Operator procedures
- overloaded operators [Visual Basic], calling
- operator overloading
ms.assetid: 0dce42cc-f0b0-4c14-9f62-018b21f33497
ms.openlocfilehash: a977b17d4b2c797bbe38d289a57f3d9d31fa64fa
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75345960"
---
# <a name="how-to-call-an-operator-procedure-visual-basic"></a>Como chamar um procedimento de operador (Visual Basic)
Você chama um procedimento de operador usando o símbolo de operador em uma expressão. No caso de um operador de conversão, você chama a [função CType](../../../../visual-basic/language-reference/functions/ctype-function.md) para converter um valor de um tipo de dados para outro.  
  
 Você não chama os procedimentos de operador explicitamente. Basta usar o operador ou a função `CType`, em uma instrução de atribuição ou uma expressão, da mesma maneira que você usa um operador normalmente. Visual Basic faz a chamada para o procedimento de operador.  
  
 A definição de um operador em uma classe ou estrutura também é chamada de *sobrecarga* do operador.  
  
### <a name="to-call-an-operator-procedure"></a>Para chamar um procedimento de operador  
  
1. Use o símbolo do operador em uma expressão da maneira comum.  
  
2. Verifique se os tipos de dados dos operandos são apropriados para o operador e na ordem correta.  
  
3. O operador contribui para o valor da expressão conforme esperado.  
  
### <a name="to-call-a-conversion-operator-procedure"></a>Para chamar um procedimento de operador de conversão  
  
1. Use `CType` dentro de uma expressão.  
  
2. Verifique se os tipos de dados dos operandos são apropriados para a conversão e na ordem correta.  
  
3. `CType` chama o procedimento de operador de conversão e retorna o valor convertido.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir cria duas estruturas <xref:System.TimeSpan>, adiciona-as juntas e armazena o resultado em uma terceira estrutura de <xref:System.TimeSpan>. A estrutura de <xref:System.TimeSpan> define procedimentos de operador para sobrecarregar vários operadores padrão.  
  
 [!code-vb[VbVbcnProcedures#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#29)]  
  
 Como <xref:System.TimeSpan> sobrecarrega o operador de `+` padrão, o exemplo anterior chama um procedimento de operador quando calcula o valor de `combinedSpan`.  
  
 Para obter um exemplo de como chamar um procedimento de operador de conversa, consulte [como: usar uma classe que define operadores](./how-to-use-a-class-that-defines-operators.md).  
  
## <a name="compile-the-code"></a>Compilar o código  
 Certifique-se de que a classe ou estrutura que você está usando define o operador que você deseja usar.  
  
## <a name="see-also"></a>Veja também

- [Procedimentos de Operador](./operator-procedures.md)
- [Como definir um operador](./how-to-define-an-operator.md)
- [Como definir um operador de conversão](./how-to-define-a-conversion-operator.md)
- [Instrução Operator](../../../../visual-basic/language-reference/statements/operator-statement.md)
- [Ampliação](../../../../visual-basic/language-reference/modifiers/widening.md)
- [Narrowing](../../../../visual-basic/language-reference/modifiers/narrowing.md)
- [Instrução Structure](../../../../visual-basic/language-reference/statements/structure-statement.md)
- [Como declarar uma estrutura](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
- [Conversões Implícitas e Explícitas](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [Conversões de Widening e Narrowing](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
