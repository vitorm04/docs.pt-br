---
title: Como forçar um argumento a ser passado por valor (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- procedures [Visual Basic], arguments
- procedures [Visual Basic], parameters
- procedure arguments
- Visual Basic code, procedures
- arguments [Visual Basic], ByVal
- arguments [Visual Basic], passing by value
- procedure parameters
- procedures [Visual Basic], calling
- arguments [Visual Basic], in parentheses
- procedure arguments [Visual Basic], in parentheses
- arguments [Visual Basic], changing value
ms.assetid: 77b4f2d2-1055-4c2f-a521-874d1db86946
caps.latest.revision: 16
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 30f5e5fe7b9c92f90673dc99a0e299136a38305b
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-force-an-argument-to-be-passed-by-value-visual-basic"></a>Como forçar um argumento a ser passado por valor (Visual Basic)
A declaração do procedimento determina o mecanismo de passagem. Se um parâmetro for declarado [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), Visual Basic espera passar o argumento correspondente por referência. Isso permite que o procedimento alterar o valor do elemento de programação subjacente do argumento no código de chamada. Se você desejar proteger o elemento subjacente contra alteração, você pode substituir o `ByRef` mecanismo de passagem no procedimento de chamada colocando o nome do argumento entre parênteses. Esses parênteses são além de parênteses delimitando a lista de argumentos na chamada.  
  
 O código de chamada não pode substituir um [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) mecanismo.  
  
### <a name="to-force-an-argument-to-be-passed-by-value"></a>Para forçar um argumento a ser passado por valor  
  
-   Se o parâmetro correspondente é declarado `ByVal` no procedimento, você não precisa executar etapas adicionais. Visual Basic já espera passar o argumento por valor.  
  
-   Se o parâmetro correspondente é declarado `ByRef` no procedimento, coloque o argumento entre parênteses na chamada de procedimento.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir substitui um `ByRef` declaração de parâmetro. Na chamada de força `ByVal`, observe os dois níveis de parênteses.  
  
 [!code-vb[VbVbcnProcedures#39](./codesnippet/VisualBasic/how-to-force-an-argument-to-be-passed-by-value_1.vb)]  
  
 [!code-vb[VbVbcnProcedures#40](./codesnippet/VisualBasic/how-to-force-an-argument-to-be-passed-by-value_2.vb)]  
  
 Quando `str` é colocado entre parênteses extras dentro da lista de argumento, o `setNewString` procedimento não é possível alterar o valor no código de chamada, e `MsgBox` exibe "Não pode ser substituído se passado ByVal". Quando `str` não é colocado entre parênteses extras, o procedimento pode alterá-la, e `MsgBox` exibe "Este é um novo valor para o argumento inString."  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Quando uma variável é passada por referência, você deve usar o `ByRef` palavra-chave para especificar esse mecanismo.  
  
 O padrão no Visual Basic é passar argumentos por valor. No entanto, é uma boa prática para incluir qualquer um de programação de [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) ou [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) palavra-chave com cada parâmetro declarado. Isso facilita a leitura do seu código.  
  
## <a name="robust-programming"></a>Programação robusta  
 Se um procedimento declara um parâmetro [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), a execução correta do código pode depender de poder alterar o elemento subjacente no código de chamada. Se o código de chamada substitui esse mecanismo de chamada, colocando o argumento entre parênteses, ou se ele passa um argumento não modificável, o procedimento não pode alterar o elemento subjacente. Isso pode produzir resultados inesperados no código de chamada.  
  
## <a name="net-framework-security"></a>Segurança do .NET Framework  
 Sempre há um risco potencial em permitir que um procedimento alterar o valor subjacente um argumento no código de chamada. Verifique se você espera que esse valor a ser alterado e esteja preparado para verificá-lo para validade antes de usá-lo.  
  
## <a name="see-also"></a>Consulte também  
 [Procedimentos](./index.md)  
 [Parâmetros e Argumentos de Procedimento](./procedure-parameters-and-arguments.md)  
 [Como passar argumentos para um procedimento](./how-to-pass-arguments-to-a-procedure.md)  
 [Passando Argumentos por Valor e por Referência](./passing-arguments-by-value-and-by-reference.md)  
 [Diferenças entre argumentos modificáveis e não modificáveis](./differences-between-modifiable-and-nonmodifiable-arguments.md)  
 [Diferenças entre passar um argumento por valor e por referência](./differences-between-passing-an-argument-by-value-and-by-reference.md)  
 [Como alterar o valor de um argumento de procedimento](./how-to-change-the-value-of-a-procedure-argument.md)  
 [Como proteger um argumento de procedimento contra alterações de valor](./how-to-protect-a-procedure-argument-against-value-changes.md)  
 [Passando Argumentos por Posição e Nome](./passing-arguments-by-position-and-by-name.md)  
 [Tipos de Valor e Tipos de Referência](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
