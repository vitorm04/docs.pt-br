---
title: 'Como: declarar uma variável de objeto e atribuir um objeto a ela'
ms.date: 07/20/2015
helpviewer_keywords:
- object variables [Visual Basic], declaring
- declaring object variables [Visual Basic]
ms.assetid: 2fa77dde-1fb2-439a-80d4-3e9787649fad
ms.openlocfilehash: 4cfad1d820b584d4610d24c392b14ac3958471b7
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352901"
---
# <a name="how-to-declare-an-object-variable-and-assign-an-object-to-it-in-visual-basic"></a>Como declarar uma variável de objeto e atribuir um objeto a ela no Visual Basic

Você declara uma variável do [tipo de dados Object](../../../../visual-basic/language-reference/data-types/object-data-type.md) especificando `As Object` em uma [instrução Dim](../../../../visual-basic/language-reference/statements/dim-statement.md). Você atribui um objeto a tal variável colocando o objeto após o sinal de igual (`=`) em uma instrução de atribuição ou cláusula de inicialização.

## <a name="example"></a>Exemplo

O exemplo a seguir declara uma variável `Object` e atribui a instância atual a ela.

```vb
Dim thisObject As Object
thisObject = "This is an Object"
```

Você pode combinar a declaração e a atribuição inicializando a variável como parte de sua declaração. O exemplo a seguir é equivalente ao exemplo anterior.

```vb
Dim thisObject As Object= "This is an Object"
```

## <a name="compiling-the-code"></a>Compilando o código

Este exemplo requer:

- Uma referência ao namespace <xref:System>.

- Uma classe, estrutura ou módulo no qual colocar a instrução `Dim`.

- Um procedimento no qual colocar a instrução de atribuição.

## <a name="see-also"></a>Consulte também

- [Declaração de Variável](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [Variáveis de Objeto](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [Declaração de Variável do Objeto](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)
- [Tipo de Dados Object](../../../../visual-basic/language-reference/data-types/object-data-type.md)
- [Instrução Dim](../../../../visual-basic/language-reference/statements/dim-statement.md)
- [Inferência de Tipo de Variável Local](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [Instrução Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
