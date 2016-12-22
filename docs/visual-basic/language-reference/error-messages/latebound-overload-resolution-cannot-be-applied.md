---
title: "N&#227;o &#233; poss&#237;vel aplicar a resolu&#231;&#227;o de sobrecarga com associa&#231;&#227;o tardia a &#39;&lt;procedurename&gt;&#39; porque a inst&#226;ncia de acesso &#233; um tipo de interface | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30933"
  - "bc30933"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30933"
  - "resolução de sobrecarga, com argumento de associação tardia"
ms.assetid: 8182eea0-dd34-4d6e-9ca0-41d8713e9dc4
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# N&#227;o &#233; poss&#237;vel aplicar a resolu&#231;&#227;o de sobrecarga com associa&#231;&#227;o tardia a &#39;&lt;procedurename&gt;&#39; porque a inst&#226;ncia de acesso &#233; um tipo de interface
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

O compilador está tentando resolver uma referência a uma propriedade ou procedimento sobrecarregado, mas a referência falha porque um argumento é do tipo `Object` e o objeto da referência possui o tipo de dados de uma interface.  O argumento `Object` obriga o compilador a resolver a referência como ligada tardiamente.  
  
 Nesteas circunstâncias, o compilador resolve o sobrecarregamento através da classe implementadora ao invés da interface subjacente.  Se a classe renomeia uma das versões sobrecarregadas, o compilador não considera que aquela versão seja um sobrecarregamento porque seu nome é diferente.  Isto por sua vez faz o compilador ignorar a versão renomeada quando ela puder ter sido a escolha correta para resolver a referência.  
  
 **Identificação do erro:**  BC30933  
  
### Para corrigir este erro  
  
-   Use `CType` para lançar um argumento de `Object` ao tipo especificado pela assinatura do sobrecarregamento que você deseja chamar.  
  
     Note que isso não ajuda a lançar o objeto que faz referência na interface subjacente.  Você precisa lançar o argumento para evitar este erro.  
  
## Exemplo  
 O exemplo a seguir mostra uma chamada para um procedimento `Sub` sobrecarregado que causa este erro no momento da compilação.  
  
```  
Module m1  
    Interface i1  
        Sub s1(ByVal p1 As Integer)  
        Sub s1(ByVal p1 As Double)  
    End Interface  
    Class c1  
        Implements i1  
        Public Overloads Sub s1(ByVal p1 As Integer) Implements i1.s1  
        End Sub  
        Public Overloads Sub s2(ByVal p1 As Double) Implements i1.s1  
        End Sub  
    End Class  
    Sub Main()  
        Dim refer As i1 = New c1  
        Dim o1 As Object = 3.1415  
        ' The following reference is INVALID and causes a compiler error.  
        refer.s1(o1)   
    End Sub  
End Module  
```  
  
 No exemplo anterior, se o compilador permitisse a chamada a `s1` como escrito, a resolução teria se realizado através da classe `c1` ao invés da onterface `i1`.  Isto significaria que o compilador não consideraria `s2` porque seu nome é diferente `c1`, muito embora seja a escolha correta como definido por `i1`.  
  
 Você pode corrigir o erro alterando a chamada para uma das seguites linhas do código:  
  
```  
refer.s1(CType(o1, Integer))  
refer.s1(CType(o1, Double))  
```  
  
 Cada uma das linhas de código anteriores explicitamente projeta o `Object` variável `o1` a um dos tipos de parâmetro definidos para as sobrecargas.  
  
## Consulte também  
 [Sobrecarga de procedimento](../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md)   
 [Resolução de sobrecarga](../../../visual-basic/programming-guide/language-features/procedures/overload-resolution.md)   
 [Função CType](../../../visual-basic/language-reference/functions/ctype-function.md)