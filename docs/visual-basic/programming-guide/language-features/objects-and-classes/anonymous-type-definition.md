---
title: Definição do tipo anônimo (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- anonymous types [Visual Basic], type definition
ms.assetid: 7a8a0ddc-55ba-4d67-869e-87a84d938bac
ms.openlocfilehash: 5f6486965d9e44524420975523e10ded32a135b7
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67755220"
---
# <a name="anonymous-type-definition-visual-basic"></a>Definição do tipo anônimo (Visual Basic)

Em resposta à declaração de uma instância de um tipo anônimo, o compilador cria uma nova definição de classe que contém as propriedades especificadas para o tipo.

## <a name="compiler-generated-code"></a>Código gerado pelo compilador

Para a seguinte definição de `product`, o compilador cria uma nova definição de classe que contém as propriedades `Name`, `Price`, e `OnHand`.

[!code-vb[VbVbalrAnonymousTypes#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#25)]

A definição de classe contém definições de propriedade semelhantes ao seguinte. Observe que não há nenhum `Set` método para as propriedades de chave. Os valores das propriedades de chave são somente leitura.

```vb
Public Class $Anonymous1
    Private _name As String
    Private _price As Double
    Private _onHand As Integer
     Public ReadOnly Property Name() As String
        Get
            Return _name
        End Get
    End Property

    Public ReadOnly Property Price() As Double
        Get
            Return _price
        End Get
    End Property

    Public Property OnHand() As Integer
        Get
            Return _onHand
        End Get
        Set(ByVal Value As Integer)
            _onHand = Value
        End Set
    End Property

End Class
```

Além disso, definições de tipo anônimo contêm um construtor sem parâmetros. Os construtores que exigem parâmetros não são permitidos.

Se uma declaração de tipo anônimo contém pelo menos uma propriedade de chave, a definição de tipo substitui três membros herdados <xref:System.Object>: <xref:System.Object.Equals%2A>, <xref:System.Object.GetHashCode%2A>, e <xref:System.Object.ToString%2A>. Se nenhuma propriedade de chave é declarada, apenas <xref:System.Object.ToString%2A> é substituído. As substituições fornecem a seguinte funcionalidade:

- `Equals` Retorna `True` se duas instâncias de tipo anônimo são a mesma instância, ou se eles atendem às seguintes condições:

  - Eles têm o mesmo número de propriedades.

  - As propriedades são declaradas na mesma ordem, com os mesmos nomes e os mesmos inferidos tipos. Comparações de nome não diferenciam maiusculas de minúsculas.

  - Pelo menos uma das propriedades é uma propriedade de chave e o `Key` palavra-chave é aplicada às mesmas propriedades.

  - Comparação entre cada par correspondente de propriedades de chave retorna `True`.

    Por exemplo, nos exemplos a seguir, `Equals` retorna `True` apenas para `employee01` e `employee08`. O comentário antes de cada linha especifica o motivo por que a nova instância não coincide com `employee01`.

    [!code-vb[VbVbalrAnonymousTypes#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#24)]

- `GetHashcode` Fornece um algoritmo GetHashCode adequadamente exclusivo. O algoritmo usa somente as propriedades de chave para calcular o código hash.

- `ToString` Retorna uma cadeia de caracteres concatenada de valores de propriedade, conforme mostrado no exemplo a seguir. Chave e propriedades não chave são incluídas.

  [!code-vb[VbVbalrAnonymousTypes#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#29)]

Propriedades explicitamente nomeadas de um tipo anônimo não podem entrar em conflito com esses métodos gerados. Ou seja, você não pode usar `.Equals`, `.GetHashCode`, ou `.ToString` para uma propriedade de nome.

Definições de tipo anônimo que incluem pelo menos uma propriedade de chave também implementa o <xref:System.IEquatable%601?displayProperty=nameWithType> interface, onde `T` é o tipo do tipo anônimo.

> [!NOTE]
> Declarações de tipo anônimo criar o mesmo tipo anônimo somente se ocorrerem no mesmo assembly, suas propriedades têm os mesmos nomes e os mesmos inferidos tipos, as propriedades são declaradas na mesma ordem e as mesmas propriedades são marcadas como propriedades de chave.

## <a name="see-also"></a>Consulte também

- [Tipos Anônimos](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
- [Como: Inferir nomes de propriedade e tipos em declarações de tipo anônimo](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)
