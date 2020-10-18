---
title: Parâmetros opcionais devem especificar um valor padrão
ms.date: 07/20/2015
f1_keywords:
- vbc30812
- bc30812
helpviewer_keywords:
- BC30812
ms.assetid: 5091a250-be66-413b-98a3-2a9974c4d600
ms.openlocfilehash: 3718fe5c42c8af0948f3b5cb0d120c6876c6f98f
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92162447"
---
# <a name="bc30812-optional-parameters-must-specify-a-default-value"></a>BC30812: parâmetros opcionais devem especificar um valor padrão

Parâmetros opcionais devem fornecer valores padrão que podem ser usados se nenhum parâmetro for fornecido por um procedimento de chamada.

**ID do erro:** BC30812

## <a name="example"></a>Exemplo

O exemplo a seguir gera BC30812:

```vb
Sub Proc1(x As Integer, Optional y As String)
    Console.WriteLine("Default argument is: " & y)
End Sub
```

## <a name="to-correct-this-error"></a>Para corrigir este erro

Especifique valores padrão para parâmetros opcionais:

```vb
Sub Proc1(x As Integer, Optional y As String = "Default Value")
    Console.WriteLine("Default argument is: " & y)
End Sub
```

## <a name="see-also"></a>Veja também

- [Opcional](../modifiers/optional.md)
