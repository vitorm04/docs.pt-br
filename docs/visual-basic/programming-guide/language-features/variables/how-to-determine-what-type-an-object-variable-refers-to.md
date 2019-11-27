---
title: Como determinar a que tipo uma variável de objeto se refere
ms.date: 07/20/2015
helpviewer_keywords:
- TypeOf operator [Visual Basic], determining object variable type
- variables [Visual Basic], object
- object variables [Visual Basic], determining type
ms.assetid: 6f6a138d-58a4-40d1-9f4e-0a3c598eaf81
ms.openlocfilehash: 9f9b89e2fea0bd69cba6d50fa1d1fb9cc3927685
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348612"
---
# <a name="how-to-determine-what-type-an-object-variable-refers-to-visual-basic"></a>Como determinar a que tipo uma variável de objeto se refere (Visual Basic)

Uma variável de objeto contém um ponteiro para dados que são armazenados em outro lugar. O tipo desses dados pode ser alterado durante o tempo de execução. A qualquer momento, você pode usar o método <xref:System.Type.GetTypeCode%2A> para determinar o tipo de tempo de execução atual ou o [operador typeof](../../../../visual-basic/language-reference/operators/typeof-operator.md) para descobrir se o tipo de tempo de execução atual é compatível com um tipo especificado.

### <a name="to-determine-the-exact-type-an-object-variable-currently-refers-to"></a>Para determinar o tipo exato que uma variável de objeto atualmente faz referência

1. Na variável de objeto, chame o método <xref:System.Object.GetType%2A> para recuperar um objeto <xref:System.Type?displayProperty=nameWithType>.

    ```vb
    Dim myObject As Object
    myObject.GetType()
    ```

2. Na classe <xref:System.Type?displayProperty=nameWithType>, chame o método compartilhado <xref:System.Type.GetTypeCode%2A> para recuperar o valor de enumeração <xref:System.TypeCode> para o tipo do objeto.

    ```vb
    Dim myObject As Object
    Dim datTyp As Integer = Type.GetTypeCode(myObject.GetType())
    MsgBox("myObject currently has type code " & CStr(datTyp))
    ```

    Você pode testar o valor de enumeração <xref:System.TypeCode> em relação a qualquer membro de enumeração que seja de interesse, como `Double`.

### <a name="to-determine-whether-an-object-variables-type-is-compatible-with-a-specified-type"></a>Para determinar se o tipo de uma variável de objeto é compatível com um tipo especificado

- Use o operador `TypeOf` em combinação com o [operador is](../../../../visual-basic/language-reference/operators/is-operator.md) para testar o objeto com uma expressão `TypeOf`...`Is`.

    ```vb
    If TypeOf objA Is System.Windows.Forms.Control Then
        MsgBox("objA is compatible with the Control class")
    End If
    ```

    A expressão `TypeOf`...`Is` retornará `True` se o tipo de tempo de execução do objeto for compatível com o tipo especificado.

    O critério de compatibilidade depende se o tipo especificado é uma classe, estrutura ou interface. Em geral, os tipos são compatíveis se o objeto for do mesmo tipo que, herda de ou implementa o tipo especificado. Para obter mais informações, consulte [operador typeof](../../../../visual-basic/language-reference/operators/typeof-operator.md).

## <a name="compiling-the-code"></a>Compilando o Código

Observe que o tipo especificado não pode ser uma variável ou expressão. Ele deve ser o nome de um tipo definido, como uma classe, estrutura ou interface. Isso inclui tipos intrínsecos, como `Integer` e `String`.

## <a name="see-also"></a>Consulte também

- <xref:System.Object.GetType%2A>
- <xref:System.Type?displayProperty=nameWithType>
- <xref:System.Type.GetTypeCode%2A>
- <xref:System.TypeCode>
- [Variáveis de Objeto](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [Valores de Variável de Objeto](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)
- [Tipo de Dados Object](../../../../visual-basic/language-reference/data-types/object-data-type.md)
