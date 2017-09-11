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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 14abadaf548e228244a1ff7ca72fa3896ef4eb5d
ms.openlocfilehash: e88241180fe1320bfd1db90a38a9a7560ae3dead
ms.contentlocale: pt-br
ms.lasthandoff: 05/23/2017

---
# <a name="39extension39-attribute-can-be-applied-only-to-39module39-39sub39-or-39function39-declarations"></a><span data-ttu-id="f7010-102">O atributo 'Extension' pode ser aplicado apenas às declarações 'Module', 'Sub' ou 'Function'</span><span class="sxs-lookup"><span data-stu-id="f7010-102">&#39;Extension&#39; attribute can be applied only to &#39;Module&#39;, &#39;Sub&#39;, or &#39;Function&#39; declarations</span></span>
<span data-ttu-id="f7010-103">A única maneira de estender um tipo de dados no Visual Basic é definir um método de extensão dentro de um módulo padrão.</span><span class="sxs-lookup"><span data-stu-id="f7010-103">The only way to extend a data type in Visual Basic is to define an extension method inside a standard module.</span></span> <span data-ttu-id="f7010-104">O método de extensão pode ser um `Sub` procedimento ou uma `Function` procedimento.</span><span class="sxs-lookup"><span data-stu-id="f7010-104">The extension method can be a `Sub` procedure or a `Function` procedure.</span></span> <span data-ttu-id="f7010-105">Todos os métodos de extensão devem ser marcados com o atributo de extensão, `<Extension()>`, do <xref:System.Runtime.CompilerServices?displayProperty=fullName>namespace.</xref:System.Runtime.CompilerServices?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="f7010-105">All extension methods must be marked with the extension attribute, `<Extension()>`, from the <xref:System.Runtime.CompilerServices?displayProperty=fullName> namespace.</span></span> <span data-ttu-id="f7010-106">Opcionalmente, um módulo que contém um método de extensão pode ser marcado da mesma maneira.</span><span class="sxs-lookup"><span data-stu-id="f7010-106">Optionally, a module that contains an extension method may be marked in the same way.</span></span> <span data-ttu-id="f7010-107">Nenhum outro uso do atributo de extensão é válido.</span><span class="sxs-lookup"><span data-stu-id="f7010-107">No other use of the extension attribute is valid.</span></span>  
  
 <span data-ttu-id="f7010-108">**ID do erro:** BC36550</span><span class="sxs-lookup"><span data-stu-id="f7010-108">**Error ID:** BC36550</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="f7010-109">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="f7010-109">To correct this error</span></span>  
  
-   <span data-ttu-id="f7010-110">Remova o atributo de extensão.</span><span class="sxs-lookup"><span data-stu-id="f7010-110">Remove the extension attribute.</span></span>  
  
-   <span data-ttu-id="f7010-111">Reprojetar sua extensão como um método definido no módulo delimitador.</span><span class="sxs-lookup"><span data-stu-id="f7010-111">Redesign your extension as a method, defined in an enclosing module.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f7010-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f7010-112">Example</span></span>  
 <span data-ttu-id="f7010-113">O exemplo a seguir define uma `Print` método para o `String` tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="f7010-113">The following example defines a `Print` method for the `String` data type.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f7010-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f7010-114">See Also</span></span>  
 <span data-ttu-id="f7010-115">[Visão geral de atributos](../../../visual-basic/programming-guide/concepts/attributes/index.md) </span><span class="sxs-lookup"><span data-stu-id="f7010-115">[Attributes overview](../../../visual-basic/programming-guide/concepts/attributes/index.md) </span></span>  
<span data-ttu-id="f7010-116"> [Métodos de extensão](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md) </span><span class="sxs-lookup"><span data-stu-id="f7010-116"> [Extension Methods](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md) </span></span>  
<span data-ttu-id="f7010-117"> [Instrução Module](../../../visual-basic/language-reference/statements/module-statement.md)</span><span class="sxs-lookup"><span data-stu-id="f7010-117"> [Module Statement](../../../visual-basic/language-reference/statements/module-statement.md)</span></span>

