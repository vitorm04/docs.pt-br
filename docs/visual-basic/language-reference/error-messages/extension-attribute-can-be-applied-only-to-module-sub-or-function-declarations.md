---
title: '&#39;Extensão de&#39; atributo pode ser aplicado somente ao &#39;módulo&#39;, &#39;Sub&#39;, ou &#39;função&#39; declarações'
ms.date: 07/20/2015
f1_keywords:
- bc36550
- vbc36550
helpviewer_keywords:
- BC36550
ms.assetid: 4387a51f-733c-45d7-abdb-eb64d4f51078
ms.openlocfilehash: fabd602f31a362fe33954253d565e86a065e0a83
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54718228"
---
# <a name="39extension39-attribute-can-be-applied-only-to-39module39-39sub39-or-39function39-declarations"></a>&#39;Extensão de&#39; atributo pode ser aplicado somente ao &#39;módulo&#39;, &#39;Sub&#39;, ou &#39;função&#39; declarações
A única maneira de estender um tipo de dados no Visual Basic é definir um método de extensão dentro de um módulo padrão. O método de extensão pode ser um `Sub` procedimento ou uma `Function` procedimento. Todos os métodos de extensão devem ser marcados com o atributo de extensão `<Extension()>`, da <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> namespace. Opcionalmente, um módulo que contém um método de extensão pode ser marcado da mesma maneira. Nenhum outro uso do atributo de extensão é válido.  
  
 **ID do erro:** BC36550  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Remova o atributo de extensão.  
  
-   Reprojetar sua extensão como um método, definido no módulo delimitador.  
  
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
- [Visão geral de atributos](../../../visual-basic/programming-guide/concepts/attributes/index.md)
- [Métodos de Extensão](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)
- [Instrução Module](../../../visual-basic/language-reference/statements/module-statement.md)
