---
title: "Função procedimentos (Visual Basic) | Documentos do Microsoft"
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
- Function procedures
- return values, function procedures
- Visual Basic code, procedures
- procedures, calling
- procedures, Function procedures
- syntax, function procedures
ms.assetid: 1b9f632c-553b-4cb6-920a-ded117ead8c0
caps.latest.revision: 27
author: stevehoag
ms.author: shoag
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 11baaa6985f0681aa9c67c4f2470fb9917db5b78
ms.lasthandoff: 03/13/2017

---
# <a name="function-procedures-visual-basic"></a>Procedimentos de função (Visual Basic)
A `Function` procedimento é uma série de [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] dentro de instruções de `Function` e `End Function` instruções. O `Function` procedimento executa uma tarefa e, em seguida, retorna o controle para o código de chamada. Quando ele retorna o controle, ele também retorna um valor para o código de chamada.  
  
 Cada vez que é chamada de procedimento, suas declarações são executadas, começando com a primeira instrução executável após o `Function` instrução e terminando com a primeira `End Function`, `Exit Function`, ou `Return` declaração encontrada.  
  
 Você pode definir uma `Function` procedimento em um módulo, classe ou estrutura. É `Public` por padrão, que significa que você pode chamá-lo de qualquer lugar no seu aplicativo que acessou o módulo, classe ou estrutura na qual você a definiu.  
  
 Um `Function` procedimento pode receber argumentos, como constantes, variáveis ou expressões, que são passadas a ele pelo código de chamada.  
  
## <a name="declaration-syntax"></a>Sintaxe da Declaração  
 A sintaxe para declarar uma `Function` procedimento é o seguinte:  
  
```vb  
[Modifiers] Function FunctionName [(ParameterList)] As ReturnType  
    [Statements]  
End Function  
```  
  
 O *modificadores* pode especificar o nível de acesso e informações sobre sobrecarregamento, substituições, compartilhamento e sombreamento. Para obter mais informações, consulte [declaração de função](../../../../visual-basic/language-reference/statements/function-statement.md).  
  
 Você declara cada parâmetro da mesma maneira que faria para [subprocedimentos](./sub-procedures.md).  
  
### <a name="data-type"></a>Tipo de dados  
 Cada `Function` procedimento tem um tipo de dados, assim como cada variável. Esse tipo de dados é especificado pelo `As` cláusula de `Function` instrução e ele determina o tipo de dados do valor que a função retorna para o código de chamada. As declarações de exemplo a seguir ilustram isso.  
  
```vb  
Function yesterday() As Date  
End Function  
  
Function findSqrt(ByVal radicand As Single) As Single  
End Function  
```  
  
 Para obter mais informações, veja "Partes" em [declaração de função](../../../../visual-basic/language-reference/statements/function-statement.md).  
  
## <a name="returning-values"></a>Retornando valores  
 O valor de uma `Function` procedimento envia de volta para o código de chamada é chamada seu valor de retorno. O procedimento retorna o valor de uma das seguintes maneiras:  
  
-   Ele usa o `Return` para especificar o valor de retorno e retorna o controle imediatamente para o programa de chamada. O exemplo a seguir ilustra essa situação.  
  
```vb  
Function FunctionName [(ParameterList)] As ReturnType  
    ' The following statement immediately transfers control back  
    ' to the calling code and returns the value of Expression.  
    Return Expression  
End Function  
```  
  
-   Ele atribui um valor para o seu próprio nome de função em uma ou mais declarações do procedimento. O controle retorna ao programa de chamada até que uma `Exit Function` ou `End Function` instrução é executada. O exemplo a seguir ilustra essa situação.  
  
```vb  
Function FunctionName [(ParameterList)] As ReturnType  
    ' The following statement does not transfer control back to the calling code.  
    FunctionName = Expression  
    ' When control returns to the calling code, Expression is the return value.  
End Function  
```  
  
 A vantagem de atribuir o valor de retorno ao nome da função é que o controle não retorna do procedimento até encontrar um `Exit Function` ou `End Function` instrução. Isso permite que você atribua um valor preliminar e ajustá-lo mais tarde, se necessário.  
  
 Para obter mais informações sobre como retornar valores, consulte [declaração de função](../../../../visual-basic/language-reference/statements/function-statement.md). Para obter informações sobre como retornar matrizes, consulte [matrizes](../../../../visual-basic/programming-guide/language-features/arrays/index.md).  
  
## <a name="calling-syntax"></a>Sintaxe de chamada  
 Você invocar um `Function` procedimento, incluindo seu nome e argumentos tanto no lado direito de uma instrução de atribuição ou em uma expressão. Você deve fornecer valores para todos os argumentos que não são opcionais, e você deve colocar a lista de argumentos entre parênteses. Se não for fornecido nenhum argumento, opcionalmente, você pode omitir os parênteses.  
  
 A sintaxe para chamar um `Function` procedimento é o seguinte:  
  
 *l-value*`=`*functionname* `[(` *argumentlist*    `)]`  
  
 `If ((`*functionname* `[(` *argumentlist* `)] / 3) <=` *expressão*  `) Then`  
  
 Quando você chama um `Function` procedimento, você não precisa usar seu valor de retorno. Se você não fizer isso, todas as ações da função são executadas, mas o valor de retorno será ignorado. <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A>é frequentemente chamado dessa maneira.</xref:Microsoft.VisualBasic.Interaction.MsgBox%2A>  
  
### <a name="illustration-of-declaration-and-call"></a>Ilustração da declaração e chamada  
 O seguinte `Function` procedimento calcula o maior lado, ou hipotenusa, de um triângulo, considerando os valores para os dois lados.  
  
 [!code-vb[VbVbcnProcedures n º&1;](./codesnippet/VisualBasic/function-procedures_1.vb)]  
  
 O exemplo a seguir mostra uma chamada típica para `hypotenuse`.  
  
 [!code-vb[VbVbcnProcedures n º&6;](./codesnippet/VisualBasic/function-procedures_2.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Procedimentos](./index.md)   
 [Procedimentos Sub](./sub-procedures.md)   
 [Procedimentos de propriedade](./property-procedures.md)   
 [Procedimentos de operador](./operator-procedures.md)   
 [Argumentos e parâmetros de procedimento](./procedure-parameters-and-arguments.md)   
 [Instrução Function](../../../../visual-basic/language-reference/statements/function-statement.md)   
 [Como: criar um procedimento que retorna um valor](./how-to-create-a-procedure-that-returns-a-value.md)   
 [Como: retornar um valor de um procedimento](./how-to-return-a-value-from-a-procedure.md)   
 [Como chamar um procedimento que retorna um valor](./how-to-call-a-procedure-that-returns-a-value.md)
