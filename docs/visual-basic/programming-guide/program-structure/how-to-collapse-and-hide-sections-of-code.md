---
title: "Como: Recolher e ocultar seções de código (Visual Basic) | Documentos do Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- Visual Basic, code collapsing
- Visual Basic, code hiding
- Visual Basic code, collapsing and hiding
ms.assetid: b770e8f5-e07d-491a-ab4b-a977980f9ba2
caps.latest.revision: 11
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
ms.openlocfilehash: 200a90b6983277d46b6e5c7b27ee4a90ecf88c40
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-collapse-and-hide-sections-of-code-visual-basic"></a>Como recolher e ocultar seções do código (Visual Basic)
O `#Region` diretiva permite que você recolher e ocultar seções de código em [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] arquivos. O `#Region` diretiva permite que você especifique um bloco de código que você pode expandir ou recolher ao usar o [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)] editor de códigos. A capacidade de ocultar código seletivamente torna os arquivos mais gerenciável e mais fácil de ler. Para obter mais informações, consulte [Estrutura de tópicos](https://docs.microsoft.com/visualstudio/ide/outlining).  
  
 `#Region`diretivas de suportam a semântica do bloco de código como `#If...#End If`. Isso significa que eles não podem começar em um bloco e terminam em outra; o início e fim devem ser no mesmo bloco. `#Region`Não há suporte para diretivas dentro de funções.  
  
### <a name="to-collapse-and-hide-a-section-of-code"></a>Para recolher e ocultar uma seção de código  
  
-   Coloque a seção de código entre o `#Region` e `#End Region` instruções, como no exemplo a seguir:  
  
     [!code-vb[VbVbalrConditionalComp n º&6;](../../../visual-basic/language-reference/directives/codesnippet/VisualBasic/how-to-collapse-and-hide-sections-of-code_1.vb)]  
  
     O `#Region` bloco pode ser usado várias vezes em um arquivo de código; assim, os usuários podem definir seus próprios blocos de procedimentos e as classes que podem, por sua vez, ser recolhidos. `#Region`blocos também podem ser aninhados em outros `#Region` blocos.  
  
    > [!NOTE]
    >  Ocultar o código não impede que ele seja compilado e não afeta `#If...#End If` instruções.  
  
## <a name="see-also"></a>Consulte também  
 [Compilação condicional](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)   
 [Diretiva #Region](../../../visual-basic/language-reference/directives/region-directive.md)   
 [#If... Then... #Else diretivas](../../../visual-basic/language-reference/directives/if-then-else-directives.md)   
 [Estrutura de tópicos](https://docs.microsoft.com/visualstudio/ide/outlining)
