---
title: Sobrecargas (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Overloads
- Overloads
helpviewer_keywords:
- Overloads keyword [Visual Basic]
- hiding by signature
- Shadows keyword [Visual Basic]
- signature, hiding by
ms.assetid: 0c6820b8-25b2-4664-bc59-5ca93c99c042
ms.openlocfilehash: 838207fe3ac5b8f57d030617546b9b7fa25dc939
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/09/2019
ms.locfileid: "67663536"
---
# <a name="overloads-visual-basic"></a>Sobrecargas (Visual Basic)

Especifica que uma propriedade ou procedimento redeclara uma ou mais propriedades ou procedimentos existentes com o mesmo nome.

## <a name="remarks"></a>Comentários

*Sobrecarregando* é a prática de fornecer mais de uma definição para um determinado nome de propriedade ou procedimento no mesmo escopo. Às vezes é chamado declarar uma propriedade ou procedimento com uma assinatura diferente *ocultação por assinatura*.

## <a name="rules"></a>Regras

- **Contexto da declaração.** Você pode usar `Overloads` somente em uma instrução de declaração de propriedade ou procedimento.

- **Modificadores combinados.** Não é possível especificar `Overloads` junto com [sombras](../../../visual-basic/language-reference/modifiers/shadows.md) na mesma declaração de procedimento.

- **Diferenças necessárias.** O *assinatura* nessa declaração deve ser diferente da assinatura de cada propriedade ou procedimento que ela sobrecarrega. A assinatura inclui o nome de propriedade ou procedimento junto com o seguinte:

  - o número de parâmetros

  - a ordem dos parâmetros

  - os tipos de dados dos parâmetros

  - o número de parâmetros de tipo (para um procedimento genérico)

  - o tipo de retorno (somente para um procedimento de operador de conversão)

  Todas as sobrecargas devem ter o mesmo nome, mas cada um deve ser diferente de todas as outras em uma ou mais dentre as condições citadas. Isso permite que o compilador a distinguir qual versão usar quando o código chama a propriedade ou procedimento.

- **Diferenças não permitidas.** Alterar um ou mais dos procedimentos a seguir não é válido para a sobrecarga de uma propriedade ou procedimento, porque eles não fazem parte da assinatura:

  - Se ele retorna um valor (para um procedimento)

  - o tipo de dados do valor de retorno (exceto para um operador de conversão)

  - os nomes dos parâmetros ou parâmetros de tipo

  - as restrições as parâmetros de tipo (para um procedimento genérico)

  - palavras-chave de modificador de parâmetro (como `ByRef` ou `Optional`)

  - propriedade ou procedimento palavras-chave de modificador (como `Public` ou `Shared`)

- **Modificador opcional.** Você não precisa usar o `Overloads` modificador quando você estiver definindo várias propriedades ou procedimentos sobrecarregados na mesma classe. No entanto, se você usar `Overloads` em uma das declarações, você deve usá-lo em todos eles.

- **Sombreamento e sobrecarga.** `Overloads` também pode ser usado para sombrear um membro existente, ou conjunto de membros sobrecarregados, em uma classe base. Quando você usa `Overloads` dessa forma, você declara a propriedade ou método com o mesmo nome e a mesma lista de parâmetros como membro da classe base, e você não fornecer o `Shadows` palavra-chave.

Se você usar `Overrides`, o compilador adicionará implicitamente `Overloads` para que sua biblioteca de APIs de trabalhar com C# com mais facilidade.

O `Overloads` modificador pode ser usado nestes contextos:

- [Instrução Function](../../../visual-basic/language-reference/statements/function-statement.md)

- [Instrução Operator](../../../visual-basic/language-reference/statements/operator-statement.md)

- [Instrução Property](../../../visual-basic/language-reference/statements/property-statement.md)

- [Instrução Sub](../../../visual-basic/language-reference/statements/sub-statement.md)

## <a name="see-also"></a>Consulte também

- [Sombras](../../../visual-basic/language-reference/modifiers/shadows.md)
- [Sobrecarga de Procedimento](../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md)
- [Tipos genéricos no Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [Procedimentos de Operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)
- [Como: Definir um operador de conversão](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
