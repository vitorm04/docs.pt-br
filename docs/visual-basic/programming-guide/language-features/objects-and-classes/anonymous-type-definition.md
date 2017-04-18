---
title: "Definição de tipo anônimo (Visual Basic) | Documentos do Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- anonymous types [Visual Basic], type definition
ms.assetid: 7a8a0ddc-55ba-4d67-869e-87a84d938bac
caps.latest.revision: 21
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
ms.openlocfilehash: 7ea9c0a181d79fd709f80565f4bdbb1f629441b2
ms.lasthandoff: 03/13/2017

---
# <a name="anonymous-type-definition-visual-basic"></a>Definição do tipo anônimo (Visual Basic)
Em resposta à declaração de uma instância de um tipo anônimo, o compilador cria uma nova definição de classe que contém as propriedades especificadas para o tipo.  
  
## <a name="compiler-generated-code"></a>Código gerado pelo compilador  
 Para a seguinte definição de `product`, o compilador cria uma nova definição de classe que contém propriedades `Name`, `Price`, e `OnHand`.  
  
 [!code-vb[25 VbVbalrAnonymousTypes](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-type-definition_1.vb)]  
  
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
  
 Além disso, definições de tipo anônimo contêm um construtor padrão. Os construtores que exigem parâmetros não são permitidos.  
  
 Se uma declaração de tipo anônimo contém pelo menos uma propriedade de chave, a definição de tipo substitui três membros herdados <xref:System.Object>: <xref:System.Object.Equals%2A>, <xref:System.Object.GetHashCode%2A>e <xref:System.Object.ToString%2A>.</xref:System.Object.ToString%2A> </xref:System.Object.GetHashCode%2A> </xref:System.Object.Equals%2A> </xref:System.Object> Se nenhuma propriedade de chave é declarada, somente <xref:System.Object.ToString%2A>é substituído.</xref:System.Object.ToString%2A> As substituições fornecem a seguinte funcionalidade:  
  
-   `Equals`Retorna `True` se duas instâncias de tipo anônimo se a mesma instância, ou se eles atendem às seguintes condições:  
  
    -   Eles têm o mesmo número de propriedades.  
  
    -   As propriedades são declaradas na mesma ordem, com os mesmos nomes e os mesmos inferidos tipos. Nome comparações não diferenciam maiusculas de minúsculas.  
  
    -   Pelo menos uma das propriedades é uma propriedade de chave e o `Key` palavra-chave é aplicada às mesmas propriedades.  
  
    -   Comparação entre cada par correspondente de propriedades chave retorna `True`.  
  
     Por exemplo, nos exemplos a seguir, `Equals` retorna `True` apenas para `employee01` e `employee08`. O comentário antes de cada linha especifica o motivo por que não coincide com a nova instância `employee01`.  
  
     [!code-vb[VbVbalrAnonymousTypes&#24;](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-type-definition_2.vb)]  
  
-   `GetHashcode`Fornece um algoritmo GetHashCode adequadamente exclusivo. O algoritmo usa somente as propriedades da chave para calcular o código hash.  
  
-   `ToString`Retorna uma cadeia de caracteres de valores de propriedade concatenados, como mostrado no exemplo a seguir. Chave e propriedades de chave não são incluídas.  
  
     [!code-vb[29 VbVbalrAnonymousTypes](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-type-definition_3.vb)]  
  
 Propriedades explicitamente nomeadas de um tipo anônimo não entram em conflito com esses métodos gerados. Ou seja, você não pode usar `.Equals`, `.GetHashCode`, ou `.ToString` para nomear uma propriedade.  
  
 Tipo anônimo definições que incluem pelo menos uma propriedade de chave também implementa o <xref:System.IEquatable%601?displayProperty=fullName>interface, onde `T` é o tipo do tipo anônimo.</xref:System.IEquatable%601?displayProperty=fullName>  
  
> [!NOTE]
>  Tipo anônimo declarações criar o mesmo tipo anônimo somente se ocorrerem no mesmo assembly, suas propriedades possuem os mesmos nomes e os mesmos inferidos tipos, as propriedades são declaradas na mesma ordem e as mesmas propriedades são marcadas como propriedades de chave.  
  
## <a name="see-also"></a>Consulte também  
 [Tipos anônimos](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)   
 [Como inferir nomes e tipos de propriedade na declaração de tipo anônimo](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)
