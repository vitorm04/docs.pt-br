---
title: "'<membername>' é ambíguo nas interfaces herdadas '<interfacename1>' e '<interfacename2>'"
ms.date: 07/20/2015
f1_keywords:
- vbc30685
- bc30685
helpviewer_keywords:
- BC30685
ms.assetid: 756add7a-23d5-4b4f-a48d-8297d6459c73
ms.openlocfilehash: f666bf380f8b94c50c2bc5fd865b37d96e92991f
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92162434"
---
# <a name="bc30685-membername-is-ambiguous-across-the-inherited-interfaces-interfacename1-and-interfacename2"></a>BC30685: ' \<membername> ' é ambíguo nas interfaces herdadas ' \<interfacename1> ' e ' \<interfacename2> '

A interface herda dois ou mais membros com o mesmo nome de várias interfaces.

 **ID do erro:** BC30685

## <a name="to-correct-this-error"></a>Para corrigir este erro

- Converta o valor para a interface base que você deseja usar; por exemplo:

    ```vb
    Interface Left
        Sub MySub()
    End Interface

    Interface Right
        Sub MySub()
    End Interface

    Interface LeftRight
        Inherits Left, Right
    End Interface

    Module test
        Sub Main()
            Dim x As LeftRight
            ' x.MySub()  'x is ambiguous.
            CType(x, Left).MySub() ' Cast to base type.
            CType(x, Right).MySub() ' Call the other base type.
        End Sub
    End Module
    ```

## <a name="see-also"></a>Veja também

- [Interfaces](../../programming-guide/language-features/interfaces/index.md)
