---
title: '#<a name="ifthenelse-directives"></a>If... Then... #Else diretivas'
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.#EndIf
- '#End If'
- '#Then'
- '#ElseIf'
- vb.#ElseIf
- vb.#Else
- vb.#If
helpviewer_keywords:
- Visual Basic code, compiling
- '#If directive [Visual Basic]'
- conditional compilation [Visual Basic], directives
- '#End if directive [Visual Basic]'
- selective compiling
- else directive (#else)
- '#Else directive [Visual Basic]'
ms.assetid: 10bba104-e3fd-451b-b672-faa472530502
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 77757e441ae937aa86122f237e839d1005644409
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="ifthenelse-directives"></a>Diretivas #If...Then...#Else
Compila condicionalmente blocos de código do Visual Basic selecionados.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
#If expression Then  
   statements  
[ #ElseIf expression Then  
   [ statements ]  
...  
#ElseIf expression Then  
   [ statements ] ]  
[ #Else  
   [ statements ] ]  
#End If  
```  
  
## <a name="parts"></a>Partes  
 `expression`  
 Necessário para `#If` e `#ElseIf` instruções, opcionais em outro lugar. Qualquer expressão, consistindo exclusivamente de uma ou mais constantes condicionais de compilador, literais e operadores, que é avaliada como `True` ou `False`.  
  
 `statements`  
 Necessário para `#If` bloco de declaração, opcional em outro lugar. Visual Basic programa linhas ou diretivas de compilador que são compiladas se a expressão associada for avaliada como `True`.  
  
 `#End If`  
 Encerra o `#If` bloco de instrução.  
  
## <a name="remarks"></a>Comentários  
 Na superfície, o comportamento do `#If...Then...#Else` diretivas aparece o mesmo que o `If...Then...Else` instruções. No entanto, o `#If...Then...#Else` avaliam o que é compilado pelo compilador, enquanto o `If...Then...Else` instruções avaliam condições em tempo de execução.  
  
 Compilação condicional é normalmente usada para compilar o mesmo programa para diferentes plataformas. Ele também é usado para evitar a depuração de código seja exibido em um arquivo executável. Código excluído durante compilação condicional é completamente omitido do arquivo executável final, para que ele não tem nenhum efeito no tamanho ou desempenho.  
  
 Independentemente do resultado de qualquer avaliação, todas as expressões são avaliadas usando `Option Compare Binary`. O `Option Compare` instrução não afeta as expressões nas `#If` e `#ElseIf` instruções.  
  
> [!NOTE]
>  Nenhuma forma de linha única do `#If`, `#Else`, `#ElseIf`, e `#End If` diretivas existe. Nenhum outro código pode aparecer na mesma linha como qualquer das diretivas.  
  
## <a name="example"></a>Exemplo  
 Este exemplo usa o `#If...Then...#Else` construção para determinar se deve compilar certas declarações.  
  
 [!code-vb[VbVbalrConditionalComp#1](../../../visual-basic/language-reference/directives/codesnippet/VisualBasic/if-then-else-directives_1.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Diretiva #Const](../../../visual-basic/language-reference/directives/const-directive.md)  
 [Instrução If...Then...Else](../../../visual-basic/language-reference/statements/if-then-else-statement.md)  
 [Compilação Condicional](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
