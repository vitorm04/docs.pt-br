---
title: "O atributo &#39;Extension&#39; pode ser aplicado apenas &#224;s declara&#231;&#245;es &#39;Module&#39;, &#39;Sub&#39; ou &#39;Function&#39; | Microsoft Docs"
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
  - "bc36550"
  - "vbc36550"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC36550"
ms.assetid: 4387a51f-733c-45d7-abdb-eb64d4f51078
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# O atributo &#39;Extension&#39; pode ser aplicado apenas &#224;s declara&#231;&#245;es &#39;Module&#39;, &#39;Sub&#39; ou &#39;Function&#39;
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

A única maneira para estender um tipo de dados em Visual Basic é definir um método de extensão dentro de um módulo padrão.  O método de extensão pode ser um `Sub` procedimento ou um `Function` procedimento.  Todos os métodos de extensão devem ser marcados com o atributo de extensão, `<Extension()>`, do <xref:System.Runtime.CompilerServices?displayProperty=fullName> namespace.  Opcionalmente, um módulo que contém um método de extensão pode ser marcado da mesma forma.  Há outro uso do atributo de extensão é válido.  
  
 **Identificação do erro:**  BC36550  
  
### Para corrigir este erro  
  
-   Remova o atributo de extensão.  
  
-   Reprojetar sua extensão como um método definido no módulo um delimitador.  
  
## Exemplo  
 O exemplo a seguir define um `Print` método para a `String` tipo de dados.  
  
```  
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
  
## Consulte também  
 [Atributos](../Topic/Attributes%20\(C%23%20and%20Visual%20Basic\).md)   
 [Métodos de extensão](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)   
 [Instrução Module](../../../visual-basic/language-reference/statements/module-statement.md)