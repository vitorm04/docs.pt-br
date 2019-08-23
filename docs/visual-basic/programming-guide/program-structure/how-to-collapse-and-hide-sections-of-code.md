---
title: 'Como: Recolher e ocultar seções de código (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic, code collapsing
- Visual Basic, code hiding
- Visual Basic code, collapsing and hiding
ms.assetid: b770e8f5-e07d-491a-ab4b-a977980f9ba2
ms.openlocfilehash: db396adf24c12542f720d3b235068aea2329288d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69949725"
---
# <a name="how-to-collapse-and-hide-sections-of-code-visual-basic"></a>Como: Recolher e ocultar seções de código (Visual Basic)
A `#Region` diretiva permite que você recolha e oculte seções de código em arquivos Visual Basic. A `#Region` diretiva permite especificar um bloco de código que você pode expandir ou recolher ao usar o editor de código do Visual Studio. A capacidade de ocultar o código seletivamente torna os arquivos mais gerenciáveis e fáceis de ler. Para obter mais informações, consulte [Estrutura de tópicos](/visualstudio/ide/outlining).  
  
 `#Region`as diretivas dão suporte à semântica de bloco `#If...#End If`de código, como. Isso significa que eles não podem começar em um bloco e terminar em outro; o início e o fim devem estar no mesmo bloco. `#Region`Não há suporte para diretivas em funções.  
  
### <a name="to-collapse-and-hide-a-section-of-code"></a>Para recolher e ocultar uma seção de código  
  
- Coloque a seção de código entre as `#Region` instruções `#End Region` e, como no exemplo a seguir:  
  
     [!code-vb[VbVbalrConditionalComp#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConditionalComp/VB/Class1.vb#6)]  
  
     O `#Region` bloco pode ser usado várias vezes em um arquivo de código; assim, os usuários podem definir seus próprios blocos de procedimentos e classes que podem, por sua vez, ser recolhidos. `#Region`os blocos também podem ser aninhados `#Region` dentro de outros blocos.  
  
    > [!NOTE]
    > Ocultar o código não impede que ele seja compilado e não afeta `#If...#End If` as instruções.  
  
## <a name="see-also"></a>Consulte também

- [Compilação Condicional](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
- [Diretiva #Region](../../../visual-basic/language-reference/directives/region-directive.md)
- [Diretivas #If...Then...#Else](../../../visual-basic/language-reference/directives/if-then-else-directives.md)
- [Estrutura de tópicos](/visualstudio/ide/outlining)
