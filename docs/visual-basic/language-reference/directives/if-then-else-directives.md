---
title: '#If... Then... #Else diretivas'
ms.date: 04/11/2018
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 69ce56d770de5f004f204b1764fd51d948ba92c1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
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

As instruções dentro de um bloco de compilação condicional devem ser concluída lógico. Por exemplo, você não pode compilar condicionalmente apenas os atributos de uma função, mas condicionalmente, você pode declarar a função juntamente com seus atributos:

```vb
   #If DEBUG Then
   <WebMethod()>
   Public Function SomeFunction() As String
   #Else
   <WebMethod(CacheDuration:=86400)>
   Public Function SomeFunction() As String
   #End If
```

## <a name="example"></a>Exemplo
 Este exemplo usa o `#If...Then...#Else` construção para determinar se deve compilar certas declarações.  
  
 [!code-vb[VbVbalrConditionalComp#1](../../../visual-basic/language-reference/directives/codesnippet/VisualBasic/if-then-else-directives_1.vb)]  
  
## <a name="see-also"></a>Consulte também  
[Diretiva #Const](../../../visual-basic/language-reference/directives/const-directive.md)  
[Instrução If...Then...Else](../../../visual-basic/language-reference/statements/if-then-else-statement.md)  
[Compilação condicional](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)   
<xref:System.Diagnostics.ConditionalAttribute?displayProperty=nameWithType>   


