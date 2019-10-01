---
title: 'Como: criar cadeias de caracteres usando um StringBuilder no Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- StringBuilder class
- strings [Visual Basic], using StringBuilder
ms.assetid: 9c042880-aa16-432e-9ccb-cd00abda9ae3
ms.openlocfilehash: 19e036abc9d25ec7fdfd6c33ebb420ec4f503cbc
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71700105"
---
# <a name="how-to-create-strings-using-a-stringbuilder-in-visual-basic"></a>Como: criar cadeias de caracteres usando um StringBuilder no Visual Basic

Este exemplo constrói uma cadeia de caracteres longa a partir de muitas cadeias de caracteres menores usando a classe <xref:System.Text.StringBuilder>. A classe <xref:System.Text.StringBuilder> é mais eficiente do que o operador `&=` para concatenar muitas cadeias de caracteres.

## <a name="example"></a>Exemplo

O exemplo a seguir cria uma instância da classe <xref:System.Text.StringBuilder>, acrescenta 1.000 cadeias de caracteres a essa instância e, em seguida, retorna sua representação de cadeia de caracteres:

 [!code-vb[VbVbalrStrings#70](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#70)]

## <a name="see-also"></a>Consulte também

- [Uso da classe StringBuilder](../../../../standard/base-types/stringbuilder.md)
- [Operador &=](../../../language-reference/operators/and-assignment-operator.md)
- [Cadeias de Caracteres](index.md)
- [Criando novas cadeias de caracteres](../../../../standard/base-types/creating-new.md)
- [Manipulando cadeias de caracteres](../../../../standard/base-types/manipulating-strings.md)
