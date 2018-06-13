---
title: Como recolher e ocultar seções do código (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic, code collapsing
- Visual Basic, code hiding
- Visual Basic code, collapsing and hiding
ms.assetid: b770e8f5-e07d-491a-ab4b-a977980f9ba2
ms.openlocfilehash: f6c272b7ac016258d99873512cb789bba6739727
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33650849"
---
# <a name="how-to-collapse-and-hide-sections-of-code-visual-basic"></a>Como recolher e ocultar seções do código (Visual Basic)
O `#Region` diretiva permite que você recolher e ocultar seções de código em arquivos do Visual Basic. O `#Region` diretiva permite especificar um bloco de código que você pode expandir ou recolher ao usar o editor de códigos do Visual Studio. A capacidade de ocultar código seletivamente torna os arquivos mais gerenciáveis e mais fáceis de ler. Para obter mais informações, consulte [Estrutura de tópicos](/visualstudio/ide/outlining).  
  
 `#Region` diretivas de suportam a semântica do bloco de código como `#If...#End If`. Isso significa que eles não podem começar em um bloco e terminar em outra; o início e término devem estar no mesmo bloco. `#Region` Não há suporte para diretivas dentro de funções.  
  
### <a name="to-collapse-and-hide-a-section-of-code"></a>Para recolher e ocultar uma seção de código  
  
-   Coloque a seção de código entre as `#Region` e `#End Region` instruções, como no exemplo a seguir:  
  
     [!code-vb[VbVbalrConditionalComp#6](../../../visual-basic/language-reference/directives/codesnippet/VisualBasic/how-to-collapse-and-hide-sections-of-code_1.vb)]  
  
     O `#Region` bloco pode ser usado várias vezes em um arquivo de código; portanto, os usuários podem definir seus próprios blocos de procedimentos e classes que por sua vez, podem ser recolhidos. `#Region` blocos também podem ser aninhados em outros `#Region` blocos.  
  
    > [!NOTE]
    >  Ocultando código não impede que ele está sendo compilada e não afeta `#If...#End If` instruções.  
  
## <a name="see-also"></a>Consulte também  
 [Compilação Condicional](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)  
 [Diretiva #Region](../../../visual-basic/language-reference/directives/region-directive.md)  
 [Diretivas #If...Then...#Else](../../../visual-basic/language-reference/directives/if-then-else-directives.md)  
 [Estrutura de tópicos](/visualstudio/ide/outlining)
