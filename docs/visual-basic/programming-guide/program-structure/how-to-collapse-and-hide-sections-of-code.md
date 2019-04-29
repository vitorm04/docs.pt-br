---
title: 'Como: Recolher e ocultar seções de código (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic, code collapsing
- Visual Basic, code hiding
- Visual Basic code, collapsing and hiding
ms.assetid: b770e8f5-e07d-491a-ab4b-a977980f9ba2
ms.openlocfilehash: bf2a7188456097ac227039e4d902a14eb182664c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61758269"
---
# <a name="how-to-collapse-and-hide-sections-of-code-visual-basic"></a>Como: Recolher e ocultar seções de código (Visual Basic)
O `#Region` diretiva permite que você recolher e ocultar seções de código em arquivos do Visual Basic. O `#Region` diretiva permite que você especifique um bloco de código que você pode expandir ou recolher ao usar o editor de código do Visual Studio. A capacidade de ocultar código seletivamente torna seus arquivos mais gerenciáveis e mais fácil de ler. Para obter mais informações, consulte [Estrutura de tópicos](/visualstudio/ide/outlining).  
  
 `#Region` diretivas de suportam a semântica de bloco de código como `#If...#End If`. Isso significa que eles não podem começar em um bloco e terminar em outra; o início e término devem ser no mesmo bloco. `#Region` Não há suporte para diretivas dentro de funções.  
  
### <a name="to-collapse-and-hide-a-section-of-code"></a>Para recolher e ocultar uma seção de código  
  
- Coloque a seção de código entre o `#Region` e `#End Region` instruções, como no exemplo a seguir:  
  
     [!code-vb[VbVbalrConditionalComp#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConditionalComp/VB/Class1.vb#6)]  
  
     O `#Region` bloco pode ser usado várias vezes em um arquivo de código; portanto, os usuários podem definir seus próprios blocos de procedimentos e as classes que podem, por sua vez, ser recolhidas. `#Region` blocos também podem ser aninhados dentro de outras `#Region` blocos.  
  
    > [!NOTE]
    >  Ocultando código não impede que ele seja compilado e não afeta `#If...#End If` instruções.  
  
## <a name="see-also"></a>Consulte também

- [Compilação Condicional](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
- [Diretiva #Region](../../../visual-basic/language-reference/directives/region-directive.md)
- [Diretivas #If...Then...#Else](../../../visual-basic/language-reference/directives/if-then-else-directives.md)
- [Estrutura de tópicos](/visualstudio/ide/outlining)
