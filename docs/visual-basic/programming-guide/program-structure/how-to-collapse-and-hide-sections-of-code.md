---
title: Como recolher e ocultar seções do código
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic, code collapsing
- Visual Basic, code hiding
- Visual Basic code, collapsing and hiding
ms.assetid: b770e8f5-e07d-491a-ab4b-a977980f9ba2
ms.openlocfilehash: e7aacdc3f41199127b00d276b382ec4a5f258da0
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347402"
---
# <a name="how-to-collapse-and-hide-sections-of-code-visual-basic"></a>Como recolher e ocultar seções do código (Visual Basic)

A diretiva `#Region` permite que você recolha e oculte seções de código em arquivos Visual Basic. A diretiva `#Region` permite especificar um bloco de código que você pode expandir ou recolher ao usar o editor de código do Visual Studio. A capacidade de ocultar o código seletivamente torna os arquivos mais gerenciáveis e fáceis de ler. Para obter mais informações, consulte [Estrutura de tópicos](/visualstudio/ide/outlining).

`#Region` diretivas dão suporte à semântica de bloco de código, como `#If...#End If`. Isso significa que eles não podem começar em um bloco e terminar em outro; o início e o fim devem estar no mesmo bloco. Não há suporte para diretivas de `#Region` em funções.

## <a name="to-collapse-and-hide-a-section-of-code"></a>Para recolher e ocultar uma seção de código

Coloque a seção de código entre as instruções `#Region` e `#End Region`, como no exemplo a seguir:

[!code-vb[VbVbalrConditionalComp#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConditionalComp/VB/Class1.vb#6)]

O bloco de `#Region` pode ser usado várias vezes em um arquivo de código; assim, os usuários podem definir seus próprios blocos de procedimentos e classes que podem, por sua vez, ser recolhidos. os blocos de `#Region` também podem ser aninhados em outros blocos de `#Region`.

> [!NOTE]
> Ocultar o código não impede que ele seja compilado e não afeta `#If...#End If` instruções.

## <a name="see-also"></a>Consulte também

- [Compilação Condicional](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
- [Diretiva #Region](../../../visual-basic/language-reference/directives/region-directive.md)
- [Diretivas #If...Then...#Else](../../../visual-basic/language-reference/directives/if-then-else-directives.md)
- [Estrutura de tópicos](/visualstudio/ide/outlining)
