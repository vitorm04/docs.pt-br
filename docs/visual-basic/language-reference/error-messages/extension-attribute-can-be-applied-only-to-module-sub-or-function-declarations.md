---
title: "O atributo &quot;Extension&quot; pode ser aplicado apenas às declarações &quot;Module&quot;, &quot;Sub&quot; ou &quot;Function&quot; | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc36550
- vbc36550
dev_langs:
- VB
helpviewer_keywords:
- BC36550
ms.assetid: 4387a51f-733c-45d7-abdb-eb64d4f51078
caps.latest.revision: 18
author: stevehoag
ms.author: shoag
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
ms.openlocfilehash: 3eee008f737bf625023b6e4d58e1df7d282148d3
ms.lasthandoff: 03/13/2017

---
# <a name="39extension39-attribute-can-be-applied-only-to-39module39-39sub39-or-39function39-declarations"></a>O atributo 'Extension' pode ser aplicado apenas às declarações 'Module', 'Sub' ou 'Function'
A única maneira de estender um tipo de dados no Visual Basic é definir um método de extensão dentro de um módulo padrão. O método de extensão pode ser um `Sub` procedimento ou uma `Function` procedimento. Todos os métodos de extensão devem ser marcados com o atributo de extensão, `<Extension()>`, do <xref:System.Runtime.CompilerServices?displayProperty=fullName>namespace.</xref:System.Runtime.CompilerServices?displayProperty=fullName> Opcionalmente, um módulo que contém um método de extensão pode ser marcado da mesma maneira. Nenhum outro uso do atributo de extensão é válido.  
  
 **ID do erro:** BC36550  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Remova o atributo de extensão.  
  
-   Reprojetar sua extensão como um método definido no módulo delimitador.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir define uma `Print` método para o `String` tipo de dados.  
  
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
  
## <a name="see-also"></a>Consulte também  
 [Visão geral de atributos](../../../visual-basic/programming-guide/concepts/attributes/index.md)   
 [Métodos de extensão](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)   
 [Instrução Module](../../../visual-basic/language-reference/statements/module-statement.md)
