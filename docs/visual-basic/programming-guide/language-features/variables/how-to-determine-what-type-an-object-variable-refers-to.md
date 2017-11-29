---
title: "Como determinar a que tipo uma variável de objeto se refere (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- TypeOf operator [Visual Basic], determining object variable type
- variables [Visual Basic], object
- object variables [Visual Basic], determining type
ms.assetid: 6f6a138d-58a4-40d1-9f4e-0a3c598eaf81
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5dd6785ecd48be3f0455de63b9e3f13a485ddbb2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-determine-what-type-an-object-variable-refers-to-visual-basic"></a>Como determinar a que tipo uma variável de objeto se refere (Visual Basic)
Uma variável de objeto contém um ponteiro para dados armazenados em outro lugar. O tipo de dados pode alterar durante o tempo de execução. A qualquer momento, você pode usar o <xref:System.Type.GetTypeCode%2A> método para determinar o tipo de tempo de execução atual, ou o [operador TypeOf](../../../../visual-basic/language-reference/operators/typeof-operator.md) para descobrir se o atual tipo de tempo de execução é compatível com um tipo especificado.  
  
### <a name="to-determine-the-exact-type-an-object-variable-currently-refers-to"></a>Para determinar que exatamente tipo a uma variável de objeto atualmente refere-se a  
  
1.  A variável de objeto, chame o <xref:System.Object.GetType%2A> método para recuperar um <xref:System.Type?displayProperty=nameWithType> objeto.  
  
    ```  
    Dim myObject As Object  
    myObject.GetType()  
    ```  
  
2.  Sobre o <xref:System.Type?displayProperty=nameWithType> classe, chame o método compartilhado <xref:System.Type.GetTypeCode%2A> para recuperar o <xref:System.TypeCode> valor de enumeração para o tipo de objeto.  
  
    ```  
    Dim myObject As Object  
    Dim datTyp As Integer = Type.GetTypeCode(myObject.GetType())  
    MsgBox("myObject currently has type code " & CStr(datTyp))  
    ```  
  
     Você pode testar o <xref:System.TypeCode> valor de enumeração contra qualquer enumeração membros são de interesse, como `Double`.  
  
### <a name="to-determine-whether-an-object-variables-type-is-compatible-with-a-specified-type"></a>Para determinar se um objeto de tipo de variável é compatível com um tipo especificado  
  
-   Use o `TypeOf` operador em combinação com o [operador Is](../../../../visual-basic/language-reference/operators/is-operator.md) para testar o objeto com um `TypeOf`... `Is` expressão.  
  
    ```  
    If TypeOf objA Is System.Windows.Forms.Control Then  
        MsgBox("objA is compatible with the Control class")  
    End If  
    ```  
  
     O `TypeOf`... `Is` retorna `True` se o objeto do tempo de execução tipo é compatível com o tipo especificado.  
  
     O critério para compatibilidade depende se o tipo especificado é uma classe, estrutura ou interface. Em geral, os tipos são compatíveis, se o objeto é do mesmo tipo, herda de ou implementa o tipo especificado. Para obter mais informações, consulte [operador TypeOf](../../../../visual-basic/language-reference/operators/typeof-operator.md).  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Observe que o tipo especificado não pode ser uma variável ou expressão. Ele deve ser o nome de um tipo definido, como uma classe, estrutura ou interface. Isso inclui tipos intrínsecos como `Integer` e `String`.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Object.GetType%2A>  
 <xref:System.Type?displayProperty=nameWithType>  
 <xref:System.Type.GetTypeCode%2A>  
 <xref:System.TypeCode>  
 [Variáveis de Objeto](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)  
 [Valores de Variável de Objeto](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)  
 [Tipo de Dados Object](../../../../visual-basic/language-reference/data-types/object-data-type.md)
