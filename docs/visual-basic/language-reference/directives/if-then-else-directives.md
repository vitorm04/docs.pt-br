---
title: '#Se... Diretivas then... #Else (Visual Basic)'
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
ms.openlocfilehash: 697521276e2d5a8d0a4aaae38789a21b7aa87fcb
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69940756"
---
# <a name="ifthenelse-directives"></a>Diretivas #If...Then...#Else
Compila condicionalmente os blocos selecionados de código de Visual Basic.  
  
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
 Necessário para `#If` instruções `#ElseIf` and, opcional em outro lugar. Qualquer expressão, consistindo exclusivamente em uma ou mais constantes de compilador condicionais, literais e operadores, que é avaliada `False`como `True` ou.  
  
 `statements`  
 Necessário para `#If` bloco de instrução, opcional em outro lugar. Visual Basic linhas de programa ou diretivas de compilador que são compiladas se a expressão associada `True`for avaliada como.  
  
 `#End If`  
 Encerra o bloco `#If` de instruções.  
  
## <a name="remarks"></a>Comentários  
 Na superfície, o comportamento das `#If...Then...#Else` diretivas é exibido da mesma forma que `If...Then...Else` as instruções. No entanto `#If...Then...#Else` , as diretivas avaliam o que é compilado pelo compilador `If...Then...Else` , enquanto as instruções avaliam condições em tempo de execução.  
  
 A compilação condicional é normalmente usada para compilar o mesmo programa para diferentes plataformas. Ele também é usado para impedir que o código de depuração apareça em um arquivo executável. O código excluído durante a compilação condicional é completamente omitido do arquivo executável final, portanto, não tem efeito sobre o tamanho ou o desempenho.  
  
 Independentemente do resultado de qualquer avaliação, todas as expressões são avaliadas `Option Compare Binary`usando. A `Option Compare` instrução não afeta as expressões nas `#If` instruções `#ElseIf` e.  
  
> [!NOTE]
> Não existe uma forma de linha única `#If`das `#Else`diretivas `#ElseIf`,, `#End If` e. Nenhum outro código pode aparecer na mesma linha que qualquer uma das diretivas. 

As instruções em um bloco de compilação condicional devem ser instruções lógicas completas. Por exemplo, você não pode compilar condicionalmente apenas os atributos de uma função, mas pode declarar condicionalmente a função junto com seus atributos:

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
 Este exemplo usa a `#If...Then...#Else` construção para determinar se deve compilar determinadas instruções.  
  
 [!code-vb[VbVbalrConditionalComp#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConditionalComp/VB/Class1.vb#1)]  
  
## <a name="see-also"></a>Consulte também

- [Diretiva #Const](../../../visual-basic/language-reference/directives/const-directive.md)
- [Instrução If...Then...Else](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
- [Compilação Condicional](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
- <xref:System.Diagnostics.ConditionalAttribute?displayProperty=nameWithType>
