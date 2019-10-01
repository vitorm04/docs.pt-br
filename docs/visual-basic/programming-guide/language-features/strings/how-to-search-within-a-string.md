---
title: 'Como: Pesquisar dentro de uma cadeia de caracteres-Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], finding
- strings [Visual Basic], searching
- examples [Visual Basic], strings
ms.assetid: ae4c79e0-08ea-489f-bdb2-5eb6d355f284
ms.openlocfilehash: fe9e50dc5458fdf8546094e5f41c2f001f1d2791
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71700071"
---
# <a name="how-to-search-within-a-string-visual-basic"></a>Como: Pesquisar dentro de uma cadeia de caracteres (Visual Basic)

Este artigo mostra um exemplo de como Pesquisar dentro de uma cadeia de caracteres em Visual Basic.

## <a name="example"></a>Exemplo

Este exemplo chama o método <xref:System.String.IndexOf%2A> em um objeto <xref:System.String> para relatar o índice da primeira ocorrência de uma subcadeia de caracteres:

 [!code-vb[VbVbalrStrings#71](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#71)]

## <a name="robust-programming"></a>Programação robusta

O método <xref:System.String.IndexOf%2A> retorna o local do primeiro caractere da primeira ocorrência da subcadeia de caracteres. O índice é baseado em 0, o que significa que o primeiro caractere de uma cadeia de caracteres tem um índice de 0.

Se <xref:System.String.IndexOf%2A> não encontrar a subcadeia de caracteres, ela retornará-1.

O método <xref:System.String.IndexOf%2A> diferencia maiúsculas de minúsculas e usa a cultura atual.

Para obter um controle de erro ideal, talvez você queira colocar a pesquisa de cadeia de caracteres no bloco `Try` de uma [tentativa... Capturar... Instrução Finally](../../../language-reference/statements/try-catch-finally-statement.md) .

## <a name="see-also"></a>Consulte também

- <xref:System.String.IndexOf%2A>
- [Instrução Try...Catch...Finally](../../../language-reference/statements/try-catch-finally-statement.md)
- [Introdução às cadeias de caracteres no Visual Basic](introduction-to-strings.md)
- [Cadeias de Caracteres](index.md)
