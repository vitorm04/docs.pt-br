---
title: '#If... Then... #Else diretivas (Visual Basic)'
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
ms.openlocfilehash: 8c0aece749edf144fdd5c8ede9ec7e2e4c96ad54
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58823383"
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
 Necessário para `#If` e `#ElseIf` instruções, opcionais em outro lugar. Qualquer expressão, que consiste exclusivamente em vez de um ou mais constantes condicionais de compilador, literais e operadores, que é avaliada como `True` ou `False`.  
  
 `statements`  
 Necessário para `#If` instrução bloco, opcional em outro lugar. Linhas de programa do Visual Basic ou diretivas de compilador que são compiladas se a expressão associada for avaliada como `True`.  
  
 `#End If`  
 Encerra o `#If` bloco de instrução.  
  
## <a name="remarks"></a>Comentários  
 Na superfície, o comportamento do `#If...Then...#Else` diretivas parece o mesmo que o `If...Then...Else` instruções. No entanto, o `#If...Then...#Else` diretivas de avaliam o que é compilado pelo compilador, enquanto o `If...Then...Else` instruções avaliam condições em tempo de execução.  
  
 Normalmente, a compilação condicional é usada para compilar o mesmo programa para diferentes plataformas. Ele também é usado para impedir que código depurado seja exibido em um arquivo executável. Código excluído durante a compilação condicional é completamente omitido do arquivo executável final, para que ele não tem nenhum efeito no desempenho ou de tamanho.  
  
 Independentemente do resultado de qualquer avaliação, todas as expressões são avaliadas usando `Option Compare Binary`. O `Option Compare` instrução não afeta as expressões nas `#If` e `#ElseIf` instruções.  
  
> [!NOTE]
>  Nenhuma forma de linha única do `#If`, `#Else`, `#ElseIf`, e `#End If` diretivas existe. Nenhum outro código pode aparecer na mesma linha como qualquer uma das diretivas. 

As instruções dentro de um bloco de compilação condicional devem ser concluída lógico. Por exemplo, você não pode compilar condicionalmente somente os atributos de uma função, mas você pode declarar condicionalmente a função juntamente com seus atributos:

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
 Este exemplo usa o `#If...Then...#Else` constructo para determinar se deve compilar certas declarações.  
  
 [!code-vb[VbVbalrConditionalComp#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConditionalComp/VB/Class1.vb#1)]  
  
## <a name="see-also"></a>Consulte também

- [Diretiva #Const](../../../visual-basic/language-reference/directives/const-directive.md)
- [Instrução If...Then...Else](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
- [Compilação Condicional](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
- <xref:System.Diagnostics.ConditionalAttribute?displayProperty=nameWithType>
