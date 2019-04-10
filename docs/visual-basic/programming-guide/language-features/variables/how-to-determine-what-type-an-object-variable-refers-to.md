---
title: 'Como: Determinar que tipo uma variável de objeto se refere (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- TypeOf operator [Visual Basic], determining object variable type
- variables [Visual Basic], object
- object variables [Visual Basic], determining type
ms.assetid: 6f6a138d-58a4-40d1-9f4e-0a3c598eaf81
ms.openlocfilehash: 6499dfce880cc9ce16e5d77887afc0598692f48e
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59342863"
---
# <a name="how-to-determine-what-type-an-object-variable-refers-to-visual-basic"></a>Como: Determinar que tipo uma variável de objeto se refere (Visual Basic)
Uma variável de objeto contém um ponteiro para dados armazenados em outro lugar. O tipo de dados que pode alterar durante o tempo de execução. A qualquer momento, você pode usar o <xref:System.Type.GetTypeCode%2A> método para determinar o tipo de tempo de execução atual, ou o [operador TypeOf](../../../../visual-basic/language-reference/operators/typeof-operator.md) para descobrir se atual o tipo de tempo de execução é compatível com um tipo especificado.  
  
### <a name="to-determine-the-exact-type-an-object-variable-currently-refers-to"></a>Para determinar que exatamente tipo a uma variável de objeto atualmente refere-se ao  
  
1. A variável de objeto, chame o <xref:System.Object.GetType%2A> método para recuperar um <xref:System.Type?displayProperty=nameWithType> objeto.  
  
    ```  
    Dim myObject As Object  
    myObject.GetType()  
    ```  
  
2. Sobre o <xref:System.Type?displayProperty=nameWithType> de classe, chame o método compartilhado <xref:System.Type.GetTypeCode%2A> para recuperar o <xref:System.TypeCode> valor de enumeração para o tipo do objeto.  
  
    ```  
    Dim myObject As Object  
    Dim datTyp As Integer = Type.GetTypeCode(myObject.GetType())  
    MsgBox("myObject currently has type code " & CStr(datTyp))  
    ```  
  
     Você pode testar o <xref:System.TypeCode> valor de enumeração em relação a qualquer membros de enumeração são de interesse, como `Double`.  
  
### <a name="to-determine-whether-an-object-variables-type-is-compatible-with-a-specified-type"></a>Para determinar se um objeto de tipo da variável é compatível com um tipo especificado  
  
-   Use o `TypeOf` operador em combinação com o [operador Is](../../../../visual-basic/language-reference/operators/is-operator.md) para testar o objeto com um `TypeOf`... `Is` expressão.  
  
    ```  
    If TypeOf objA Is System.Windows.Forms.Control Then  
        MsgBox("objA is compatible with the Control class")  
    End If  
    ```  
  
     O `TypeOf`... `Is` expressão retorna `True` se o objeto do tempo de execução o tipo é compatível com o tipo especificado.  
  
     O critério para compatibilidade depende se o tipo especificado é uma classe, estrutura ou interface. Em geral, os tipos são compatíveis, se o objeto, é do mesmo tipo que herda de ou implementa o tipo especificado. Para obter mais informações, consulte [operador TypeOf](../../../../visual-basic/language-reference/operators/typeof-operator.md).  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Observe que o tipo especificado não pode ser uma variável ou expressão. Ele deve ser o nome de um tipo definido, como uma classe, estrutura ou interface. Isso inclui tipos intrínsecos, como `Integer` e `String`.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Object.GetType%2A>
- <xref:System.Type?displayProperty=nameWithType>
- <xref:System.Type.GetTypeCode%2A>
- <xref:System.TypeCode>
- [Variáveis de objeto](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [Valores de variável de objeto](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)
- [Tipo de dados Object](../../../../visual-basic/language-reference/data-types/object-data-type.md)
