---
title: Como sobrecarregar um procedimento que usa um número indefinido de parâmetros
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], parameters
- procedure overloading [Visual Basic], indefinite number of parameters
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedure parameters
- procedures [Visual Basic], overloading
- procedures [Visual Basic], multiple versions
ms.assetid: c7042de2-2422-4039-94e8-ac298896af69
ms.openlocfilehash: 94f12b4cc6cb35864fefbb3b5bb1378bec5e974c
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75347562"
---
# <a name="how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters-visual-basic"></a>Como sobrecarregar um procedimento que use um número indefinido de parâmetros (Visual Basic)
Se um procedimento tiver um parâmetro [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) , você não poderá definir uma versão sobrecarregada usando uma matriz unidimensional para a matriz de parâmetros. Para obter mais informações, consulte "sobrecargas implícitas para um parâmetro ParamArray" em [Considerações sobre procedimentos de sobrecarga](./considerations-in-overloading-procedures.md).  
  
### <a name="to-overload-a-procedure-that-takes-a-variable-number-of-parameters"></a>Para sobrecarregar um procedimento que usa um número variável de parâmetros  
  
1. Verifique se o procedimento e a chamada lógica de código se beneficia de versões sobrecarregadas mais do que de um parâmetro `ParamArray`. Consulte "sobrecargas e ParamArrays" em [Considerações sobre os procedimentos de sobrecarga](./considerations-in-overloading-procedures.md).  
  
2. Determine quais números de valores fornecidos o procedimento deve aceitar na parte variável da lista de parâmetros. Isso pode incluir o caso de nenhum valor e pode incluir o caso de uma única matriz unidimensional.  
  
3. Para cada número aceitável de valores fornecidos, grave uma instrução de declaração de `Sub` ou `Function` que define a lista de parâmetros correspondente. Não use a palavra-chave `Optional` ou `ParamArray` nessa versão sobrecarregada.  
  
4. Em cada declaração, preceda a palavra-chave `Sub` ou `Function` com a palavra-chave [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md) .  
  
5. Após cada declaração, escreva o código do procedimento que deve ser executado quando o código de chamada fornecer valores correspondentes à lista de parâmetros da declaração.  
  
6. Encerre cada procedimento com a instrução `End Sub` ou `End Function`, conforme apropriado.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra um procedimento definido com um parâmetro [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) e, em seguida, um conjunto equivalente de procedimentos sobrecarregados.  
  
 [!code-vb[VbVbcnProcedures#69](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#69)]  
  
 [!code-vb[VbVbcnProcedures#70](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#70)]  
  
 Não é possível sobrecarregar esse procedimento com uma lista de parâmetros que usa uma matriz unidimensional para a matriz de parâmetros. No entanto, você pode usar as assinaturas das outras sobrecargas implícitas. As declarações a seguir ilustram isso.  
  
 [!code-vb[VbVbcnProcedures#71](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#71)]  
  
 O código nas versões sobrecarregadas não precisa testar se o código de chamada forneceu um ou mais valores para o parâmetro `ParamArray` ou, nesse caso, quantos. Visual Basic passa o controle para a versão que corresponde à lista de argumentos de chamada.  
  
## <a name="compile-the-code"></a>Compilar o código  
 Como um procedimento com um parâmetro `ParamArray` é equivalente a um conjunto de versões sobrecarregadas, não é possível sobrecarregar esse procedimento com uma lista de parâmetros correspondente a qualquer uma dessas sobrecargas implícitas. Para obter mais informações, consulte [Considerações sobre sobrecarga de procedimentos](./considerations-in-overloading-procedures.md).  
  
## <a name="net-framework-security"></a>Segurança do .NET Framework  
 Sempre que você lida com uma matriz que pode ser indefinidamente grande, há um risco de sobreexecutar alguma capacidade interna de seu aplicativo. Se você aceitar uma matriz de parâmetros, deverá testar o comprimento da matriz que o código de chamada passou e tomar as medidas apropriadas se for muito grande para seu aplicativo.  
  
## <a name="see-also"></a>Veja também

- [Procedimentos](./index.md)
- [Parâmetros e Argumentos de Procedimento](./procedure-parameters-and-arguments.md)
- [Parâmetros Opcionais](./optional-parameters.md)
- [Matrizes de Parâmetros](./parameter-arrays.md)
- [Sobrecarga de Procedimento](./procedure-overloading.md)
- [Solução de problemas de Procedimentos](./troubleshooting-procedures.md)
- [Como definir várias versões de um procedimento](./how-to-define-multiple-versions-of-a-procedure.md)
- [Como chamar um procedimento sobrecarregado](./how-to-call-an-overloaded-procedure.md)
- [Como sobrecarregar um procedimento que usa parâmetros opcionais](./how-to-overload-a-procedure-that-takes-optional-parameters.md)
- [Resolução de Sobrecarga](./overload-resolution.md)
