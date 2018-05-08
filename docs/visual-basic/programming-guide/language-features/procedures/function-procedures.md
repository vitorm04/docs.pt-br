---
title: Procedimentos de função (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Function procedures
- return values [Visual Basic], function procedures
- Visual Basic code, procedures
- procedures [Visual Basic], calling
- procedures [Visual Basic], Function procedures
- syntax [Visual Basic], function procedures
ms.assetid: 1b9f632c-553b-4cb6-920a-ded117ead8c0
ms.openlocfilehash: 887c930cb757b012542c97d64a57a62882a2eed3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="function-procedures-visual-basic"></a>Procedimentos de função (Visual Basic)
Um `Function` procedimento é uma série de instruções do Visual Basic entre o `Function` e `End Function` instruções. O `Function` procedimento executa uma tarefa e, em seguida, retorna o controle para o código de chamada. Quando ele retorna o controle, ele também retorna um valor para o código de chamada.  
  
 Cada vez que o procedimento é chamado, suas declarações são executadas, começando com a primeira instrução executável após o `Function` instrução e terminando com o primeiro `End Function`, `Exit Function`, ou `Return` instrução encontrado.  
  
 Você pode definir um `Function` procedimento em um módulo, classe ou estrutura. É `Public` por padrão, que significa que você pode chamá-lo de qualquer lugar no seu aplicativo que tem acesso para o módulo, classe ou estrutura na qual você a definiu.  
  
 Um `Function` procedimento pode receber argumentos, como constantes, variáveis ou expressões que são passadas para ele pelo código de chamada.  
  
## <a name="declaration-syntax"></a>Sintaxe da Declaração  
 A sintaxe para declarar um `Function` procedimento é o seguinte:  
  
```vb  
[Modifiers] Function FunctionName [(ParameterList)] As ReturnType  
    [Statements]  
End Function  
```  
  
 O *modificadores* pode especificar o nível de acesso e informações sobre a sobrecarga, substituindo, compartilhando e sombreamento. Para obter mais informações, consulte [instrução Function](../../../../visual-basic/language-reference/statements/function-statement.md).  
  
 Você declara cada parâmetro da mesma maneira que faria para [subprocedimentos](./sub-procedures.md).  
  
### <a name="data-type"></a>Tipo de dados  
 Cada `Function` procedimento tem um tipo de dados, assim como cada variável. Esse tipo de dados é especificado pelo `As` cláusula o `Function` instrução e ele determina o tipo de dados de valor que a função retorna para o código de chamada. As declarações de exemplo a seguir ilustram isso.  
  
```vb  
Function yesterday() As Date  
End Function  
  
Function findSqrt(ByVal radicand As Single) As Single  
End Function  
```  
  
 Para obter mais informações, veja "Partes" em [instrução Function](../../../../visual-basic/language-reference/statements/function-statement.md).  
  
## <a name="returning-values"></a>Retornando valores  
 O valor de uma `Function` procedimento envia de volta para o código de chamada é chamada seu valor de retorno. O procedimento retorna o valor de uma das seguintes maneiras:  
  
-   Ele usa o `Return` instrução para especificar o valor de retorno e retorna o controle imediatamente para o programa de chamada. O exemplo a seguir ilustra essa situação.  
  
```vb  
Function FunctionName [(ParameterList)] As ReturnType  
    ' The following statement immediately transfers control back  
    ' to the calling code and returns the value of Expression.  
    Return Expression  
End Function  
```  
  
-   Ele atribui um valor para o seu próprio nome de função em uma ou mais instruções do procedimento. O controle retorna ao programa de chamada até que uma `Exit Function` ou `End Function` instrução é executada. O exemplo a seguir ilustra essa situação.  
  
```vb  
Function FunctionName [(ParameterList)] As ReturnType  
    ' The following statement does not transfer control back to the calling code.  
    FunctionName = Expression  
    ' When control returns to the calling code, Expression is the return value.  
End Function  
```  
  
 A vantagem de atribuir o valor de retorno para o nome de função é que o controle não retorna do procedimento até encontrar um `Exit Function` ou `End Function` instrução. Isso permite que você atribua um valor preliminar e ajustá-lo mais tarde, se necessário.  
  
 Para obter mais informações sobre como retornar valores, consulte [instrução Function](../../../../visual-basic/language-reference/statements/function-statement.md). Para obter informações sobre como retornar matrizes, consulte [matrizes](../../../../visual-basic/programming-guide/language-features/arrays/index.md).  
  
## <a name="calling-syntax"></a>A sintaxe de chamada  
 Invocar um `Function` procedimento, incluindo seu nome e argumentos tanto no lado direito de uma instrução de atribuição ou em uma expressão. Você deve fornecer valores para todos os argumentos que não são opcionais, e você deve colocar a lista de argumentos entre parênteses. Se nenhum argumento for fornecido, opcionalmente, você pode omitir os parênteses.  
  
 A sintaxe para chamar um `Function` procedimento é o seguinte:  
  
 *lvalue*`=`*functionname* `[(` *argumentlist* `)]`  
  
 `If ((` *nomedafunção* `[(` *argumentlist* `)] / 3) <=` *expressão* `) Then`  
  
 Quando você chama um `Function` procedimento, você não precisa usar o valor de retorno. Se você não fizer isso, todas as ações da função são executadas, mas o valor de retorno será ignorado. <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> é geralmente chamado dessa maneira.  
  
### <a name="illustration-of-declaration-and-call"></a>Ilustração da declaração e chamada  
 O seguinte `Function` procedimento calcula o maior lado, ou hipotenusa, de um triângulo retângulo, dado os valores dos outros dois lados.  
  
 [!code-vb[VbVbcnProcedures#1](./codesnippet/VisualBasic/function-procedures_1.vb)]  
  
 O exemplo a seguir mostra uma chamada típica para `hypotenuse`.  
  
 [!code-vb[VbVbcnProcedures#6](./codesnippet/VisualBasic/function-procedures_2.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Procedimentos](./index.md)  
 [Subprocedimentos](./sub-procedures.md)  
 [Procedimentos de Propriedade](./property-procedures.md)  
 [Procedimentos de Operador](./operator-procedures.md)  
 [Parâmetros e Argumentos de Procedimento](./procedure-parameters-and-arguments.md)  
 [Instrução Function](../../../../visual-basic/language-reference/statements/function-statement.md)  
 [Como criar um procedimento que retorne um valor](./how-to-create-a-procedure-that-returns-a-value.md)  
 [Como retornar um valor de um procedimento](./how-to-return-a-value-from-a-procedure.md)  
 [Como chamar um procedimento que retorna um valor](./how-to-call-a-procedure-that-returns-a-value.md)
