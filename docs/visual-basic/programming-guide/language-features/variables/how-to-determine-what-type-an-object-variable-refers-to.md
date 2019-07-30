---
title: 'Como: Determinar a qual tipo uma variável de objeto se refere (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- TypeOf operator [Visual Basic], determining object variable type
- variables [Visual Basic], object
- object variables [Visual Basic], determining type
ms.assetid: 6f6a138d-58a4-40d1-9f4e-0a3c598eaf81
ms.openlocfilehash: 935623dd4b6edca188f932aca0e560130199e8f6
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68626573"
---
# <a name="how-to-determine-what-type-an-object-variable-refers-to-visual-basic"></a>Como: Determinar a qual tipo uma variável de objeto se refere (Visual Basic)

Uma variável de objeto contém um ponteiro para dados que são armazenados em outro lugar. O tipo desses dados pode ser alterado durante o tempo de execução. A qualquer momento, você pode usar o <xref:System.Type.GetTypeCode%2A> método para determinar o tipo de tempo de execução atual ou o [operador typeof](../../../../visual-basic/language-reference/operators/typeof-operator.md) para descobrir se o tipo de tempo de execução atual é compatível com um tipo especificado.

### <a name="to-determine-the-exact-type-an-object-variable-currently-refers-to"></a>Para determinar o tipo exato que uma variável de objeto atualmente faz referência

1. Na variável de objeto, chame o <xref:System.Object.GetType%2A> método para recuperar um <xref:System.Type?displayProperty=nameWithType> objeto.

    ```vb
    Dim myObject As Object
    myObject.GetType()
    ```

2. Na classe, chame o método <xref:System.Type.GetTypeCode%2A> compartilhado para recuperar o <xref:System.TypeCode> valor de enumeração para o tipo do objeto. <xref:System.Type?displayProperty=nameWithType>

    ```vb
    Dim myObject As Object
    Dim datTyp As Integer = Type.GetTypeCode(myObject.GetType())
    MsgBox("myObject currently has type code " & CStr(datTyp))
    ```

    Você pode testar o <xref:System.TypeCode> valor de enumeração em relação a qualquer membro de enumeração que `Double`seja de interesse, como.

### <a name="to-determine-whether-an-object-variables-type-is-compatible-with-a-specified-type"></a>Para determinar se o tipo de uma variável de objeto é compatível com um tipo especificado

- Use o `TypeOf` operador em combinação com o [operador is](../../../../visual-basic/language-reference/operators/is-operator.md) para testar o objeto com um `TypeOf`... `Is` expressão.

    ```vb
    If TypeOf objA Is System.Windows.Forms.Control Then
        MsgBox("objA is compatible with the Control class")
    End If
    ```

    A `TypeOf`... `Is` expressão retorna`True` se o tipo de tempo de execução do objeto for compatível com o tipo especificado.

    O critério de compatibilidade depende se o tipo especificado é uma classe, estrutura ou interface. Em geral, os tipos são compatíveis se o objeto for do mesmo tipo que, herda de ou implementa o tipo especificado. Para obter mais informações, consulte [operador typeof](../../../../visual-basic/language-reference/operators/typeof-operator.md).

## <a name="compiling-the-code"></a>Compilando o código

Observe que o tipo especificado não pode ser uma variável ou expressão. Ele deve ser o nome de um tipo definido, como uma classe, estrutura ou interface. Isso inclui tipos intrínsecos, `Integer` como `String`e.

## <a name="see-also"></a>Consulte também

- <xref:System.Object.GetType%2A>
- <xref:System.Type?displayProperty=nameWithType>
- <xref:System.Type.GetTypeCode%2A>
- <xref:System.TypeCode>
- [Variáveis de Objeto](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [Valores de Variável de Objeto](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)
- [Tipo de Dados Object](../../../../visual-basic/language-reference/data-types/object-data-type.md)
