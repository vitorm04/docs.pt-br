---
title: O atributo 'Extension' pode ser aplicado apenas às declarações 'Module', 'Sub' ou 'Function'
ms.date: 07/20/2015
f1_keywords:
- bc36550
- vbc36550
helpviewer_keywords:
- BC36550
ms.assetid: 4387a51f-733c-45d7-abdb-eb64d4f51078
ms.openlocfilehash: 2ed3a10cdf941bb8d1d7c00379736e04e8cad4d7
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72583177"
---
# <a name="extension-attribute-can-be-applied-only-to-module-sub-or-function-declarations"></a>O atributo 'Extension' pode ser aplicado apenas às declarações 'Module', 'Sub' ou 'Function'

A única maneira de estender um tipo de dados no Visual Basic é definir um método de extensão dentro de um módulo padrão. O método de extensão pode ser um procedimento `Sub` ou um procedimento `Function`. Todos os métodos de extensão devem ser marcados com o atributo de extensão, `<Extension()>`, do namespace <xref:System.Runtime.CompilerServices?displayProperty=nameWithType>. Opcionalmente, um módulo que contém um método de extensão pode ser marcado da mesma maneira. Nenhum outro uso do atributo de extensão é válido.

**ID do erro:** BC36550

## <a name="to-correct-this-error"></a>Para corrigir este erro

- Remova o atributo de extensão.

- Reprojete sua extensão como um método, definido em um módulo delimitador.

## <a name="example"></a>Exemplo

O exemplo a seguir define um método `Print` para o tipo de dados `String`.

```vb
Imports StringUtility
Imports System.Runtime.CompilerServices
Namespace StringUtility
    <Extension()>
    Module StringExtensions
        <Extension()>
        Public Sub Print (ByVal str As String)
            Console.WriteLine(str)
        End Sub
    End Module
End Namespace
```

## <a name="see-also"></a>Consulte também

- [Visão geral de atributos](../../../visual-basic/programming-guide/concepts/attributes/index.md)
- [Métodos de Extensão](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)
- [Instrução Module](../../../visual-basic/language-reference/statements/module-statement.md)
