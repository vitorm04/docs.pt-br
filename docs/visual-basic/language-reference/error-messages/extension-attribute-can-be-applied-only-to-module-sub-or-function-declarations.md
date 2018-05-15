---
title: '&#39;Extensão&#39; atributo pode ser aplicado somente a &#39;módulo&#39;, &#39;Sub&#39;, ou &#39;função&#39; declarações'
ms.date: 07/20/2015
f1_keywords:
- bc36550
- vbc36550
helpviewer_keywords:
- BC36550
ms.assetid: 4387a51f-733c-45d7-abdb-eb64d4f51078
ms.openlocfilehash: d7f8829cb879d612711ac6bcc6bf4aa065fbe323
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="39extension39-attribute-can-be-applied-only-to-39module39-39sub39-or-39function39-declarations"></a><span data-ttu-id="39adb-102">&#39;Extensão&#39; atributo pode ser aplicado somente a &#39;módulo&#39;, &#39;Sub&#39;, ou &#39;função&#39; declarações</span><span class="sxs-lookup"><span data-stu-id="39adb-102">&#39;Extension&#39; attribute can be applied only to &#39;Module&#39;, &#39;Sub&#39;, or &#39;Function&#39; declarations</span></span>
<span data-ttu-id="39adb-103">A única maneira de estender um tipo de dados no Visual Basic é definir um método de extensão dentro de um módulo padrão.</span><span class="sxs-lookup"><span data-stu-id="39adb-103">The only way to extend a data type in Visual Basic is to define an extension method inside a standard module.</span></span> <span data-ttu-id="39adb-104">O método de extensão pode ser um `Sub` procedimento ou uma `Function` procedimento.</span><span class="sxs-lookup"><span data-stu-id="39adb-104">The extension method can be a `Sub` procedure or a `Function` procedure.</span></span> <span data-ttu-id="39adb-105">Todos os métodos de extensão devem ser marcados com o atributo de extensão, `<Extension()>`, do <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> namespace.</span><span class="sxs-lookup"><span data-stu-id="39adb-105">All extension methods must be marked with the extension attribute, `<Extension()>`, from the <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="39adb-106">Opcionalmente, um módulo que contém um método de extensão pode ser marcado da mesma maneira.</span><span class="sxs-lookup"><span data-stu-id="39adb-106">Optionally, a module that contains an extension method may be marked in the same way.</span></span> <span data-ttu-id="39adb-107">Nenhum outro uso do atributo de extensão é válido.</span><span class="sxs-lookup"><span data-stu-id="39adb-107">No other use of the extension attribute is valid.</span></span>  
  
 <span data-ttu-id="39adb-108">**ID do erro:** BC36550</span><span class="sxs-lookup"><span data-stu-id="39adb-108">**Error ID:** BC36550</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="39adb-109">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="39adb-109">To correct this error</span></span>  
  
-   <span data-ttu-id="39adb-110">Remova o atributo de extensão.</span><span class="sxs-lookup"><span data-stu-id="39adb-110">Remove the extension attribute.</span></span>  
  
-   <span data-ttu-id="39adb-111">Reprojete sua extensão como um método definido no módulo delimitador.</span><span class="sxs-lookup"><span data-stu-id="39adb-111">Redesign your extension as a method, defined in an enclosing module.</span></span>  
  
## <a name="example"></a><span data-ttu-id="39adb-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="39adb-112">Example</span></span>  
 <span data-ttu-id="39adb-113">O exemplo a seguir define uma `Print` método para o `String` tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="39adb-113">The following example defines a `Print` method for the `String` data type.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="39adb-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="39adb-114">See Also</span></span>  
 [<span data-ttu-id="39adb-115">Visão geral de atributos</span><span class="sxs-lookup"><span data-stu-id="39adb-115">Attributes overview</span></span>](../../../visual-basic/programming-guide/concepts/attributes/index.md)  
 [<span data-ttu-id="39adb-116">Métodos de Extensão</span><span class="sxs-lookup"><span data-stu-id="39adb-116">Extension Methods</span></span>](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)  
 [<span data-ttu-id="39adb-117">Instrução Module</span><span class="sxs-lookup"><span data-stu-id="39adb-117">Module Statement</span></span>](../../../visual-basic/language-reference/statements/module-statement.md)
