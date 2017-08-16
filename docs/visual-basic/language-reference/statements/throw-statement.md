---
title: "Instrução throw (Visual Basic) | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Throw
dev_langs:
- VB
helpviewer_keywords:
- structured exception handling, throw statements
- try-catch exception handling, throw statements
- throw statement, about throw statements
- throwing exceptions, throw statement
- exception handling, throw statement
- On Error statement, throwing exceptions
- throwing exceptions
- exception handling, unstructured
- throw statement
ms.assetid: a6e07406-5c8a-4498-87a2-8339f3651d62
caps.latest.revision: 15
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
ms.openlocfilehash: 46812b79fafb7c1f995c1395980d19d77f90b1a6
ms.lasthandoff: 03/13/2017

---
# <a name="throw-statement-visual-basic"></a>Instrução Throw (Visual Basic)
Lança uma exceção dentro de um procedimento.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
Throw [ expression ]  
```  
  
## <a name="part"></a>Parte  
 `expression`  
 Fornece informações sobre a exceção seja lançada. Opcional quando residente em uma `Catch` instrução, caso contrário, é necessária.  
  
## <a name="remarks"></a>Comentários  
 O `Throw` instrução gera uma exceção que você pode manipular com código de manipulação de exceção estruturado (`Try`... `Catch`... `Finally`) ou código de manipulação de exceção não estruturado (`On Error GoTo`). Você pode usar o `Throw` instrução para interceptar erros em seu código, pois o Visual Basic move para cima a pilha de chamadas até encontrar o código de manipulação de exceção apropriado.  
  
 Um `Throw` instrução com nenhuma expressão somente pode ser usada em uma `Catch` no qual a instrução case Relança a exceção atualmente sendo tratada pela instrução de `Catch` instrução.  
  
 O `Throw` instrução redefine a pilha de chamadas para o `expression` exceção. Se `expression` não for fornecido, a pilha de chamadas é deixada inalterada. Você pode acessar a pilha de chamadas para a exceção através do <xref:System.Exception.StackTrace%2A>propriedade.</xref:System.Exception.StackTrace%2A>  
  
## <a name="example"></a>Exemplo  
 O código a seguir usa o `Throw` instrução lançar uma exceção:  
  
 [!code-vb[VbVbalrStatements&#84;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/throw-statement_1.vb)]  
  
## <a name="requirements"></a>Requisitos  
 **Namespace:** [Microsoft. VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)  
  
 **Módulo:**`Interaction`  
  
 **Assembly:** biblioteca de tempo de execução do Visual Basic (em Microsoft.VisualBasic.dll)  
  
## <a name="see-also"></a>Consulte também  
 [Instrução Try...Catch...Finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)   
 [Instrução On Error](../../../visual-basic/language-reference/statements/on-error-statement.md)
