---
title: 'Como: criar strings usando um StringBuilder'
ms.date: 07/20/2015
helpviewer_keywords:
- StringBuilder class
- strings [Visual Basic], using StringBuilder
ms.assetid: 9c042880-aa16-432e-9ccb-cd00abda9ae3
ms.openlocfilehash: c41db584df83782dab99b90043045aa2cabcb6ff
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/20/2020
ms.locfileid: "81645323"
---
# <a name="how-to-create-strings-using-a-stringbuilder-in-visual-basic"></a>Como: criar strings usando um StringBuilder no Visual Basic

Este exemplo constrói uma longa seqüência de <xref:System.Text.StringBuilder> muitas strings menores usando a classe. A <xref:System.Text.StringBuilder> classe é mais `&=` eficiente do que o operador para concatenar muitas cordas.

## <a name="example"></a>Exemplo

O exemplo a seguir <xref:System.Text.StringBuilder> cria uma instância da classe, anexa 1.000 strings a essa instância e, em seguida, retorna sua representação de strings:

 [!code-vb[VbVbalrStrings#70](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#70)]

## <a name="see-also"></a>Confira também

- [Uso da classe StringBuilder](../../../../standard/base-types/stringbuilder.md)
- [&= Operador](../../../language-reference/operators/and-assignment-operator.md)
- [Cadeias de caracteres](index.md)
- [Criar novas cadeias de caracteres](../../../../standard/base-types/creating-new.md)
- [Manipular cadeias de caracteres](../../../../standard/base-types/best-practices-strings.md)
