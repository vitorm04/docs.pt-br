---
title: 'Como: Sobrecarregar um procedimento que usa um número indefinido de parâmetros (Visual Basic)'
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
ms.openlocfilehash: 3cf75fc6221364704379eb23d308481c34e6c0d6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59316447"
---
# <a name="how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters-visual-basic"></a>Como: Sobrecarregar um procedimento que usa um número indefinido de parâmetros (Visual Basic)
Se um procedimento tem um [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) parâmetro, você não pode definir uma versão sobrecarregada, levando a uma matriz unidimensional para a matriz de parâmetros. Para obter mais informações, consulte "Implícita sobrecargas para um parâmetro ParamArray" na [considerações sobre procedimentos de sobrecarga](./considerations-in-overloading-procedures.md).  
  
### <a name="to-overload-a-procedure-that-takes-a-variable-number-of-parameters"></a>Para sobrecarregar um procedimento que usa um número variável de parâmetros  
  
1. Verificar que o procedimento e chamar os benefícios de lógica de código de versões sobrecarregadas mais de um `ParamArray` parâmetro. Consulte "Sobrecargas e ParamArrays" nos [considerações sobre procedimentos de sobrecarga](./considerations-in-overloading-procedures.md).  
  
2. Determine quais números de valores fornecidos, o procedimento deve aceitar na variável parte da lista de parâmetros. Isso pode incluir o caso de nenhum valor, e ele pode incluir o caso de uma única matriz unidimensional.  
  
3. Para cada número aceitável de valores fornecidos, escreva uma `Sub` ou `Function` instrução de declaração que define a lista de parâmetro correspondente. Não pode usar uma as `Optional` ou o `ParamArray` palavra-chave nesta versão sobrecarregada.  
  
4. Em cada declaração, preceda a `Sub` ou `Function` palavra-chave com o [sobrecarrega](../../../../visual-basic/language-reference/modifiers/overloads.md) palavra-chave.  
  
5. Após cada declaração, escreva o código de procedimento que deve ser executado quando o código de chamada fornece valores correspondentes à lista de parâmetros da declaração.  
  
6. Encerrar cada procedimento com o `End Sub` ou `End Function` instrução conforme apropriado.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra um procedimento definido com um [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) parâmetro e, em seguida, um conjunto equivalente de procedimentos sobrecarregados.  
  
 [!code-vb[VbVbcnProcedures#69](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#69)]  
  
 [!code-vb[VbVbcnProcedures#70](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#70)]  
  
 Você não pode sobrecarregar tal procedimento com uma lista de parâmetros que usa uma matriz unidimensional para a matriz de parâmetros. No entanto, você pode usar as assinaturas das outras sobrecargas implícitas. As declarações a seguir ilustram isso.  
  
 [!code-vb[VbVbcnProcedures#71](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#71)]  
  
 O código em que as versões sobrecarregadas não precisa testar se o código de chamada fornecido um ou mais valores para o `ParamArray` parâmetro, ou em caso afirmativo, quantos. Visual Basic passa o controle para a versão correspondente a lista de argumentos de chamada.  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Porque um procedimento com um `ParamArray` parâmetro é equivalente a um conjunto de versões sobrecarregadas, você não pode sobrecarregar tal procedimento com uma lista de parâmetro correspondente a qualquer uma dessas sobrecargas implícitas. Para obter mais informações, consulte [considerações sobre procedimentos de sobrecarga](./considerations-in-overloading-procedures.md).  
  
## <a name="net-framework-security"></a>Segurança do .NET Framework  
 Sempre que você lida com uma matriz que pode ser indefinidamente grande, há um risco de ultrapassar alguma capacidade interna do seu aplicativo. Se você aceitar uma matriz de parâmetros, de teste para o comprimento da matriz em que o código de chamada passado para ele e tomar as medidas adequadas se ele for muito grande para o seu aplicativo.  
  
## <a name="see-also"></a>Consulte também

- [Procedimentos](./index.md)
- [Parâmetros e Argumentos de Procedimento](./procedure-parameters-and-arguments.md)
- [Parâmetros Opcionais](./optional-parameters.md)
- [Matrizes de Parâmetros](./parameter-arrays.md)
- [Sobrecarga de Procedimento](./procedure-overloading.md)
- [Solução de problemas de Procedimentos](./troubleshooting-procedures.md)
- [Como: Definir várias versões de um procedimento](./how-to-define-multiple-versions-of-a-procedure.md)
- [Como: Chamar um procedimento sobrecarregado](./how-to-call-an-overloaded-procedure.md)
- [Como: Sobrecarregar um procedimento que usa parâmetros opcionais](./how-to-overload-a-procedure-that-takes-optional-parameters.md)
- [Resolução de Sobrecarga](./overload-resolution.md)
