---
title: "Como: determinar que tipo uma variável de objeto se refere (Visual Basic) | Documentos do Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- TypeOf operator [Visual Basic], determining object variable type
- variables [Visual Basic], object
- object variables, determining type
ms.assetid: 6f6a138d-58a4-40d1-9f4e-0a3c598eaf81
caps.latest.revision: 13
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 4945f8e1329a81c3f699e9b4018d9ef3e97de11a
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-determine-what-type-an-object-variable-refers-to-visual-basic"></a>Como determinar a que tipo uma variável de objeto se refere (Visual Basic)
Uma variável de objeto contém um ponteiro para dados armazenados em outro lugar. O tipo de dados que pode alterar durante o tempo de execução. A qualquer momento, você pode usar o <xref:System.Type.GetTypeCode%2A>método para determinar o tipo de tempo de execução atual, ou o [operador TypeOf](../../../../visual-basic/language-reference/operators/typeof-operator.md) para descobrir se o atual tipo de tempo de execução é compatível com um tipo especificado.</xref:System.Type.GetTypeCode%2A>  
  
### <a name="to-determine-the-exact-type-an-object-variable-currently-refers-to"></a>Para determinar que a exata tipo a uma variável de objeto atualmente refere-se a  
  
1.  Na variável de objeto, chame o <xref:System.Object.GetType%2A>método para recuperar um <xref:System.Type?displayProperty=fullName>objeto.</xref:System.Type?displayProperty=fullName> </xref:System.Object.GetType%2A>  
  
    ```  
    Dim myObject As Object  
    myObject.GetType()  
    ```  
  
2.  Sobre o <xref:System.Type?displayProperty=fullName>da classe, chame o método compartilhado <xref:System.Type.GetTypeCode%2A>para recuperar o <xref:System.TypeCode>valor de enumeração para o tipo de objeto.</xref:System.TypeCode> </xref:System.Type.GetTypeCode%2A> </xref:System.Type?displayProperty=fullName>  
  
    ```  
    Dim myObject As Object  
    Dim datTyp As Integer = Type.GetTypeCode(myObject.GetType())  
    MsgBox("myObject currently has type code " & CStr(datTyp))  
    ```  
  
     Você pode testar a <xref:System.TypeCode>contra qualquer enumeração membros são de interesse, como valor da enumeração `Double`.</xref:System.TypeCode>  
  
### <a name="to-determine-whether-an-object-variables-type-is-compatible-with-a-specified-type"></a>Para determinar se um objeto de tipo de variável é compatível com um tipo especificado  
  
-   Use o `TypeOf` operador em combinação com o [operador Is](../../../../visual-basic/language-reference/operators/is-operator.md) para testar o objeto com um `TypeOf`... `Is` expressão.  
  
    ```  
    If TypeOf objA Is System.Windows.Forms.Control Then  
        MsgBox("objA is compatible with the Control class")  
    End If  
    ```  
  
     The `TypeOf`... `Is` retorna `True` se o objeto do tempo de execução tipo é compatível com o tipo especificado.  
  
     O critério para compatibilidade depende se o tipo especificado é uma classe, estrutura ou interface. Em geral, os tipos são compatíveis se o objeto é do mesmo tipo como, herda de ou implementa o tipo especificado. Para obter mais informações, consulte [operador TypeOf](../../../../visual-basic/language-reference/operators/typeof-operator.md).  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Observe que o tipo especificado não pode ser uma variável ou expressão. Ele deve ser o nome de um tipo definido, como uma classe, estrutura ou interface. Isso inclui tipos intrínsecos como `Integer` e `String`.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Object.GetType%2A></xref:System.Object.GetType%2A>   
 <xref:System.Type?displayProperty=fullName></xref:System.Type?displayProperty=fullName>   
 <xref:System.Type.GetTypeCode%2A></xref:System.Type.GetTypeCode%2A>   
 <xref:System.TypeCode></xref:System.TypeCode>   
 [Variáveis de objeto](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)   
 [Valores de variáveis de objeto](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)   
 [Tipo de Dados Object](../../../../visual-basic/language-reference/data-types/object-data-type.md)
