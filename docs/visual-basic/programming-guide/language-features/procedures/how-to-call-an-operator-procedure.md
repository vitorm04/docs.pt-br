---
title: 'Como: Chamar um procedimento de operador (Visual Basic)'
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
ms.openlocfilehash: d68781aa12ab7c1c717031ca252c5f3120649edc
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59335479"
---
# <a name="how-to-call-an-operator-procedure-visual-basic"></a>Como: Chamar um procedimento de operador (Visual Basic)
Você pode chamar um procedimento de operador, usando o símbolo do operador em uma expressão. No caso de um operador de conversão, você chama o [função CType](../../../../visual-basic/language-reference/functions/ctype-function.md) para converter um valor de um tipo de dados para outro.  
  
 Você não pode chamar procedimentos de operador explicitamente. Você apenas usa o operador, ou o `CType` função em uma instrução de atribuição ou uma expressão, da mesma maneira que você normalmente usa um operador. Visual Basic faz a chamada para o procedimento de operador.  
  
 Definir um operador em uma classe ou estrutura também é chamado *sobrecarga* o operador.  
  
### <a name="to-call-an-operator-procedure"></a>Para chamar um procedimento de operador  
  
1. Use o símbolo do operador em uma expressão na forma comum.  
  
2. Certifique-se de que os tipos de dados dos operandos são apropriados para o operador e na ordem correta.  
  
3. O operador contribui para o valor da expressão conforme o esperado.  
  
### <a name="to-call-a-conversion-operator-procedure"></a>Para chamar um procedimento de operador de conversão  
  
1. Use `CType` dentro de uma expressão.  
  
2. Certifique-se de que os tipos de dados dos operandos são apropriados para a conversão e na ordem correta.  
  
3. `CType` chama o procedimento de operador de conversão e retorna o valor convertido.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir cria dois <xref:System.TimeSpan> estruturas, adiciona-os juntos e armazena o resultado em uma terceira <xref:System.TimeSpan> estrutura. O <xref:System.TimeSpan> estrutura define procedimentos de operador para sobrecarregar vários operadores padrão.  
  
 [!code-vb[VbVbcnProcedures#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#29)]  
  
 Porque <xref:System.TimeSpan> sobrecarrega o padrão `+` operador, o exemplo anterior chama um procedimento de operador quando ele calcula o valor de `combinedSpan`.  
  
 Para obter um exemplo de como chamar um procedimento de operador de conversa, consulte [como: Usar uma classe que define operadores](./how-to-use-a-class-that-defines-operators.md).  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Certifique-se de que a classe ou estrutura que você está usando define o operador que você deseja usar.  
  
## <a name="see-also"></a>Consulte também

- [Procedimentos de Operador](./operator-procedures.md)
- [Como: Definir um operador](./how-to-define-an-operator.md)
- [Como: Definir um operador de conversão](./how-to-define-a-conversion-operator.md)
- [Instrução Operator](../../../../visual-basic/language-reference/statements/operator-statement.md)
- [Ampliação](../../../../visual-basic/language-reference/modifiers/widening.md)
- [Narrowing](../../../../visual-basic/language-reference/modifiers/narrowing.md)
- [Instrução Structure](../../../../visual-basic/language-reference/statements/structure-statement.md)
- [Como: declarar uma estrutura](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
- [Conversões Implícitas e Explícitas](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [Conversões de Widening e Narrowing](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
