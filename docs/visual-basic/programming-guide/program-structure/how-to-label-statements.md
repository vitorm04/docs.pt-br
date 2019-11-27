---
title: Como rotular instruções
ms.date: 07/20/2015
helpviewer_keywords:
- colons (:)
- statements [Visual Basic], labels
- ': separator character'
- Visual Basic code, labeling statements
ms.assetid: 38f1ff43-2054-42cb-963b-1998e60c6ed4
ms.openlocfilehash: be116ac8046c43e89e44c2d9127c6131e4dfaa52
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347377"
---
# <a name="how-to-label-statements-visual-basic"></a>Como rotular instruções (Visual Basic)

Os blocos de instrução são compostos por linhas de código delimitadas por dois-pontos. As linhas de código precedidas por uma cadeia de caracteres de identificação ou um número inteiro são consideradas *rotuladas*. Os rótulos de instrução são usados para marcar uma linha de código para identificá-lo para uso com instruções como `On Error Goto`.

Os rótulos podem ser identificadores de Visual Basic válidos — como aqueles que identificam elementos de programação — ou literais inteiros. Um rótulo deve aparecer no início de uma linha de código-fonte e deve ser seguido por dois-pontos, independentemente de ser seguido por uma instrução na mesma linha.

O compilador identifica os rótulos verificando se o início da linha corresponde a qualquer identificador já definido. Caso contrário, o compilador pressupõe que ele é um rótulo.

Os rótulos têm seu próprio espaço de declaração e não interferem em outros identificadores. O escopo de um rótulo é o corpo do método. A declaração de rótulo tem precedência em qualquer situação ambígua.

> [!NOTE]
> Os rótulos só podem ser usados em instruções Executáveis dentro de métodos.

## <a name="to-label-a-line-of-code"></a>Para rotular uma linha de código

Coloque um identificador, seguido por dois-pontos, no início da linha de código-fonte.

Por exemplo, as linhas de código a seguir são rotuladas com `Jump` e `120`, respectivamente:

[!code-vb[VbVbalrStatements#708](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#708)]

## <a name="see-also"></a>Consulte também

- [Instruções](../../../visual-basic/programming-guide/language-features/statements.md)
- [Nomes de Elementos Declarados](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)
- [Estrutura do Programa e Convenções de Código](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)
