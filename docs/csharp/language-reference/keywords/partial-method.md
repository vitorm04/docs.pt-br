---
title: Método partial – Referência de C#
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- partialmethod_CSharpKeyword
helpviewer_keywords:
- partial methods [C#]
ms.assetid: 43f40242-17e0-4452-8573-090503ad3137
ms.openlocfilehash: 742d6ca744ac723179718f1400e600411712dd40
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53238280"
---
# <a name="partial-method-c-reference"></a>Método parcial (C# Reference)

Um método parcial tem sua assinatura definida em uma parte de um tipo parcial e sua implementação definida em outra parte do tipo. Os métodos parciais permitem que os designers de classe forneçam ganchos de método, semelhantes a manipuladores de eventos, que os desenvolvedores podem decidir implementar ou não. Se o desenvolvedor não fornecer uma implementação, o compilador removerá a assinatura no tempo de compilação. As seguintes condições são aplicáveis a métodos parciais:

- As assinaturas em ambas as partes do tipo parcial devem ser correspondentes.

- O método deve retornar nulo.

- Não é permitido nenhum modificador de acesso. Métodos parciais são implicitamente privados.

O exemplo a seguir mostra um método parcial definido em duas partes de uma classe parcial:

[!code-csharp[csrefKeywordsContextual#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#9)]

Para obter mais informações, consulte [Classes e métodos parciais](../../programming-guide/classes-and-structs/partial-classes-and-methods.md).

## <a name="see-also"></a>Consulte também

- [Referência de C#](../index.md)
- [Tipo parcial](partial-type.md)