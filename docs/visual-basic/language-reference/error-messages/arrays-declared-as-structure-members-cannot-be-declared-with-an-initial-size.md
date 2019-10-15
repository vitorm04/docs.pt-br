---
title: Matrizes declaradas como membros de estrutura não podem ser declaradas com um tamanho inicial
ms.date: 07/20/2015
f1_keywords:
- vbc31043
- bc31043
helpviewer_keywords:
- BC31043
ms.assetid: 5bd90c71-1b78-444b-91e1-4789451ef085
ms.openlocfilehash: 83342b780c0fa7c3a2e0a6797b80ef788117ae92
ms.sourcegitcommit: d7c298f6c2e3aab0c7498bfafc0a0a94ea1fe23e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/10/2019
ms.locfileid: "72250147"
---
# <a name="arrays-declared-as-structure-members-cannot-be-declared-with-an-initial-size"></a>Matrizes declaradas como membros de estrutura não podem ser declaradas com um tamanho inicial

Uma matriz em uma estrutura é declarada com um tamanho inicial. Você não pode inicializar nenhum elemento de estrutura e declarar um tamanho de matriz é uma forma de inicialização.

**ID do erro:** BC31043

## <a name="example"></a>Exemplo

O exemplo a seguir gera BC31043:

```vb
Structure DemoStruct
    Public demoArray(9) As Integer
End Structure
```

## <a name="to-correct-this-error"></a>Para corrigir este erro

1. Defina a matriz em sua estrutura como dinâmica (sem tamanho inicial).

2. Se você precisar de um determinado tamanho de matriz, poderá redimensionar uma matriz dinâmica com uma [instrução ReDim](../statements/redim-statement.md) quando o código estiver em execução. O exemplo a seguir ilustra isto:
  
    ```vb
    Structure DemoStruct
        Public demoArray() As Integer
    End Structure
    Sub UseStruct()
        Dim struct As DemoStruct  
        ReDim struct.demoArray(9)
        Struct.demoArray(2) = 777
    End Sub  
    ```
  
## <a name="see-also"></a>Consulte também

- [Matrizes](../../programming-guide/language-features/arrays/index.md)
- [Como: declarar uma estrutura](../../programming-guide/language-features/data-types/how-to-declare-a-structure.md)
