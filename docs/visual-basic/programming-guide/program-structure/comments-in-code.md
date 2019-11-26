---
title: Comentários no código
ms.date: 07/20/2015
helpviewer_keywords:
- Uncomment button
- REM statement [Visual Basic]
- comments [Visual Basic], in code
- comments [Visual Basic], Visual Basic code
- Comment button
- buttons [Visual Basic], Uncomment
- buttons [Visual Basic], Comment
- code comments [Visual Basic], Visual Basic
- Visual Basic code, comments
- comments
- code comments
ms.assetid: 90136fba-22eb-49f9-ba81-63db629b4a47
ms.openlocfilehash: 189810393db42c54cb8a0f97b22b3d1514d9a7c4
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346170"
---
# <a name="comments-in-code-visual-basic"></a>Comentários no código (Visual Basic)
À medida que você lê os exemplos de código, você encontra geralmente o símbolo de comentário (`'`). This symbol tells the Visual Basic compiler to ignore the text following it, or the *comment*. Os comentários são uma breve explicação e/ou anotações adicionadas ao código para o benefício de quem os lê.  
  
 É uma prática de programação recomendável iniciar todos os procedimentos com um breve comentário descrevendo as características do procedimento e sua funcionalidade (o que ele faz). Isso é um benefício para o programador e é vantajoso para qualquer pessoa que examinar o código. Você deve separar os detalhes de implementação (como o procedimento faz isso) dos comentários que descrevem as características funcionais. Quando você incluir detalhes da implementação na descrição, lembre-se de atualizá-los quando você atualizar a função.  
  
 Comentários podem seguir uma instrução na mesma linha ou ocupar uma linha inteira. Ambos são ilustrados no código a seguir.  
  
 [!code-vb[VbVbcnConventions#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#16)]  
  
 Se seu comentário exigir mais de uma linha, use o símbolo de comentário em cada linha, como o exemplo a seguir mostra.  
  
 [!code-vb[VbVbcnConventions#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#17)]  
  
## <a name="commenting-guidelines"></a>Diretrizes de comentários  
 A tabela a seguir fornece diretrizes gerais para os tipos de comentários que podem preceder uma seção de código. These are suggestions; Visual Basic does not enforce rules for adding comments. Escreva o que funciona melhor, tanto para você quanto para qualquer outra pessoa que leia seu código.  
  
|||  
|---|---|  
|Tipo de comentário|Descrição do comentário|  
|Finalidade|Descreve o que o procedimento faz (não como ele faz)|  
|Suposições|Lista cada variável externa, controle, arquivo aberto ou outro elemento acessado pelo procedimento|  
|Efeitos|Listas cada variável externa, controle ou arquivo afetado, e o efeito que ele tem (somente se não for óbvio)|  
|Entradas|Especifica a finalidade do argumento|  
|Retorna|Explica os valores retornados pelo procedimento|  
  
 Lembre-se dos seguintes pontos:  
  
- Cada declaração de variável importante deve ser precedida por um comentário sobre o uso da variável sendo declarada.  
  
- Variáveis, controles e procedimentos devem ser chamados claramente o bastante para que os comentários sejam necessários somente para detalhes de implementação complexos.  
  
- Os comentários não podem seguir uma sequência de continuação de linha na mesma linha.  
  
 You can add or remove comment symbols for a block of code by selecting one or more lines of code and choosing the **Comment** (![The Visual Basic Comment button in Visual Studio.](./media/comments-in-code/visual-basic-comment-button.gif)) and **Uncomment** (![The Visual Basic Uncomment button in Visual Studio.](./media/comments-in-code/visual-basic-uncomment-button.gif)) buttons on the **Edit** toolbar.  
  
> [!NOTE]
> Você também pode adicionar comentários ao código precedendo o texto com a palavra-chave `REM`. However, the `'` symbol and the **Comment**/**Uncomment** buttons are easier to use and require less space and memory.  
  
## <a name="see-also"></a>Consulte também

- [Basic Instincts - Documenting Your Code With XML Comments](https://docs.microsoft.com/archive/msdn-magazine/2009/may/documenting-your-code-with-xml-comments)
- [Como criar documentação XML](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)
- [Marcações de Comentário XML](../../../visual-basic/language-reference/xmldoc/index.md)
- [Estrutura do Programa e Convenções de Código](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)
- [Instrução REM](../../../visual-basic/language-reference/statements/rem-statement.md)
