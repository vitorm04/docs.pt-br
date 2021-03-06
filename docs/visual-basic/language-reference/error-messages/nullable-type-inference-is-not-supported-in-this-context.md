---
title: Inferência de tipo que permite valor nulo não suportada neste contexto
ms.date: 07/20/2015
f1_keywords:
- vbc36629
- bc36629
helpviewer_keywords:
- BC36629
ms.assetid: 0a1e2dbc-d9a4-433d-9306-c5540782b81d
ms.openlocfilehash: 610d2dc427d882c412b87eb67f021a8a86025f25
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92159919"
---
# <a name="bc36629-nullable-type-inference-is-not-supported-in-this-context"></a>BC36629: não há suporte para inferência de tipo anulável neste contexto

Tipos e estruturas de valor podem ser declarados como anuláveis.

```vb
Dim a? As Integer
Dim b As Integer?
```

 No entanto, você não pode usar a declaração anulável em combinação com a inferência de tipos. Os exemplos a seguir causam esse erro.

```vb
' Not valid.
' Dim c? = 10
' Dim d? = a
```

 **ID do erro:** BC36629

## <a name="to-correct-this-error"></a>Para corrigir este erro

- Use uma `As` cláusula para declarar a variável como um tipo de valor anulável.

## <a name="see-also"></a>Veja também

- [Tipos de valor anulável](../../programming-guide/language-features/data-types/nullable-value-types.md)
- [Inferência de Tipo de Variável Local](../../programming-guide/language-features/variables/local-type-inference.md)
