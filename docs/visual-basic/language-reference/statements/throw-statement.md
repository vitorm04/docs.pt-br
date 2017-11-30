---
title: "Instrução Throw (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Throw
helpviewer_keywords:
- structured exception handling, throw statements
- try-catch exception handling, throw statements
- throw statement [Visual Basic], about throw statements
- throwing exceptions, throw statement
- exception handling, throw statement
- On Error statement [Visual Basic], throwing exceptions
- throwing exceptions
- exception handling, unstructured
- throw statement [Visual Basic]
ms.assetid: a6e07406-5c8a-4498-87a2-8339f3651d62
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 50ada551c32b8296f0dad2ae929ca9c81a14a711
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="throw-statement-visual-basic"></a>Instrução Throw (Visual Basic)
Gera uma exceção dentro de um procedimento.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
Throw [ expression ]  
```  
  
## <a name="part"></a>Parte  
 `expression`  
 Fornece informações sobre a exceção seja lançada. Opcional quando residente em um `Catch` instrução, caso contrário, é necessária.  
  
## <a name="remarks"></a>Comentários  
 O `Throw` instrução gera uma exceção que você pode manipular com código de tratamento de exceções estruturado (`Try`... `Catch`... `Finally`) ou código de tratamento de exceção não estruturado (`On Error GoTo`). Você pode usar o `Throw` instrução para interceptar erros em seu código, pois o Visual Basic move para cima a pilha de chamadas até encontrar o código de tratamento de exceção apropriado.  
  
 Um `Throw` instrução com nenhuma expressão somente pode ser usada em uma `Catch` instrução, em que a instrução lança novamente a exceção atualmente sendo tratada pelo `Catch` instrução.  
  
 O `Throw` instrução redefine a pilha de chamadas para o `expression` exceção. Se `expression` não for fornecido, a pilha de chamadas é deixada inalterada. Você pode acessar a pilha de chamadas para a exceção por meio de <xref:System.Exception.StackTrace%2A> propriedade.  
  
## <a name="example"></a>Exemplo  
 O código a seguir usa o `Throw` instrução para lançar uma exceção:  
  
 [!code-vb[VbVbalrStatements#84](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/throw-statement_1.vb)]  
  
## <a name="requirements"></a>Requisitos  
 **Namespace:** [Microsoft. VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)  
  
 **Módulo:**`Interaction`  
  
 **Assembly:** Visual Basic Runtime Library (em Microsoft.VisualBasic.dll)  
  
## <a name="see-also"></a>Consulte também  
 [Instrução Try...Catch...Finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)  
 [Instrução On Error](../../../visual-basic/language-reference/statements/on-error-statement.md)
