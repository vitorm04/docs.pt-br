---
title: Definição do tipo anônimo
ms.date: 07/20/2015
helpviewer_keywords:
- anonymous types [Visual Basic], type definition
ms.assetid: 7a8a0ddc-55ba-4d67-869e-87a84d938bac
ms.openlocfilehash: f8ac26577a7fbef865605a7ecf643fa733b2c2c0
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344926"
---
# <a name="anonymous-type-definition-visual-basic"></a>Definição do tipo anônimo (Visual Basic)

Em resposta à declaração de uma instância de um tipo anônimo, o compilador cria uma nova definição de classe que contém as propriedades especificadas para o tipo.

## <a name="compiler-generated-code"></a>Código gerado pelo compilador

Para a seguinte definição de `product`, o compilador cria uma nova definição de classe que contém propriedades `Name`, `Price`e `OnHand`.

[!code-vb[VbVbalrAnonymousTypes#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#25)]

A definição de classe contém definições de propriedade semelhantes às seguintes. Observe que não há nenhum método de `Set` para as propriedades de chave. Os valores das propriedades de chave são somente leitura.

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

Além disso, as definições de tipo anônimo contêm um construtor sem parâmetros. Os construtores que exigem parâmetros não são permitidos.

Se uma declaração de tipo anônimo contiver pelo menos uma propriedade de chave, a definição de tipo substituirá três membros herdados de <xref:System.Object>: <xref:System.Object.Equals%2A>, <xref:System.Object.GetHashCode%2A>e <xref:System.Object.ToString%2A>. Se nenhuma propriedade de chave for declarada, somente <xref:System.Object.ToString%2A> será substituído. As substituições fornecem a seguinte funcionalidade:

- `Equals` retornará `True` se duas instâncias de tipo anônimo forem a mesma instância ou se atenderem às seguintes condições:

  - Eles têm o mesmo número de propriedades.

  - As propriedades são declaradas na mesma ordem, com os mesmos nomes e os mesmos tipos inferidos. Comparações de nome não diferenciam maiúsculas de minúsculas.

  - Pelo menos uma das propriedades é uma propriedade de chave e a palavra-chave `Key` é aplicada às mesmas propriedades.

  - A comparação de cada par correspondente de propriedades de chave retorna `True`.

    Por exemplo, nos exemplos a seguir, `Equals` retorna `True` somente para `employee01` e `employee08`. O comentário antes de cada linha especifica o motivo pelo qual a nova instância não corresponde `employee01`.

    [!code-vb[VbVbalrAnonymousTypes#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#24)]

- `GetHashcode` fornece um algoritmo GetHashCode adequadamente exclusivo. O algoritmo usa apenas as propriedades de chave para calcular o código hash.

- `ToString` retorna uma cadeia de caracteres de valores de propriedade concatenados, conforme mostrado no exemplo a seguir. As propriedades Key e non-key são incluídas.

  [!code-vb[VbVbalrAnonymousTypes#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#29)]

As propriedades nomeadas explicitamente de um tipo anônimo não podem entrar em conflito com esses métodos gerados. Ou seja, você não pode usar `.Equals`, `.GetHashCode`ou `.ToString` para nomear uma propriedade.

Definições de tipo anônimo que incluem pelo menos uma propriedade de chave também implementam a interface <xref:System.IEquatable%601?displayProperty=nameWithType>, em que `T` é o tipo do tipo anônimo.

> [!NOTE]
> Declarações de tipo anônimo criam o mesmo tipo anônimo somente se eles ocorrerem no mesmo assembly, suas propriedades têm os mesmos nomes e os mesmos tipos inferidos, as propriedades são declaradas na mesma ordem e as mesmas propriedades são marcadas como propriedades de chave.

## <a name="see-also"></a>Consulte também

- [Tipos Anônimos](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
- [Como inferir nomes e tipos de propriedade na declaração de tipo anônimo](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)
