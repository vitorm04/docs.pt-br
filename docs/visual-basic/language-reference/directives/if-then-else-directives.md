---
title: '#If... Then... #Else diretivas | Documentos do Microsoft'
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.#EndIf
- '#End If'
- '#Then'
- '#ElseIf'
- vb.#ElseIf
- vb.#Else
- vb.#If
dev_langs:
- VB
helpviewer_keywords:
- Visual Basic code, compiling
- '#If directive [Visual Basic]'
- conditional compilation, directives
- '#End if directive [Visual Basic]'
- selective compiling
- else directive (#else)
- '#Else directive [Visual Basic]'
ms.assetid: 10bba104-e3fd-451b-b672-faa472530502
caps.latest.revision: 14
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
ms.openlocfilehash: 6ba40346e25501c97bfcc3a081a69764d5c0d763
ms.lasthandoff: 03/13/2017

---
# <a name="ifthenelse-directives"></a>#If... Then... #Else diretivas
Condicionalmente compila blocos de código do Visual Basic selecionados.  
  
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
 Necessário para `#If` e `#ElseIf` instruções, opcionais em outro lugar. Qualquer expressão, consistindo exclusivamente de uma ou mais constantes de compilação condicional, literais e operadores, que é avaliada como `True` ou `False`.  
  
 `statements`  
 Necessário para `#If` bloco de declaração, opcional em outro lugar. Visual Basic programa linhas ou diretivas de compilador que são compiladas se a expressão associada for avaliada como `True`.  
  
 `#End If`  
 Encerra o `#If` bloco de instrução.  
  
## <a name="remarks"></a>Comentários  
 Na superfície, o comportamento do `#If...Then...#Else` diretivas parece o mesmo que o `If...Then...Else` instruções. No entanto, o `#If...Then...#Else` avaliam o que é compilado pelo compilador, enquanto o `If...Then...Else` instruções avaliam condições em tempo de execução.  
  
 Compilação condicional é normalmente usada para compilar o mesmo programa para diferentes plataformas. Ele também é usado para impedir que código depurado seja exibido em um arquivo executável. Código excluído durante compilação condicional é completamente omitido do arquivo executável final, para que ele não tem nenhum efeito no desempenho ou tamanho.  
  
 Independentemente do resultado de qualquer avaliação, todas as expressões são avaliadas usando `Option Compare Binary`. O `Option Compare` instrução não afeta as expressões nas `#If` e `#ElseIf` instruções.  
  
> [!NOTE]
>  Nenhum formulário de linha única da `#If`, `#Else`, `#ElseIf`, e `#End If` diretivas existe. Nenhum outro código pode aparecer na mesma linha que qualquer um das diretivas.  
  
## <a name="example"></a>Exemplo  
 Este exemplo usa o `#If...Then...#Else` construção para determinar se deve compilar certas declarações.  
  
 [!code-vb[VbVbalrConditionalComp n º&1;](../../../visual-basic/language-reference/directives/codesnippet/VisualBasic/if-then-else-directives_1.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [# Diretiva const](../../../visual-basic/language-reference/directives/const-directive.md)   
 [If... Then... Instrução else](../../../visual-basic/language-reference/statements/if-then-else-statement.md)   
 [Compilação Condicional](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
