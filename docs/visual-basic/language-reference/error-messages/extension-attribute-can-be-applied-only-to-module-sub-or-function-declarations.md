---
title: "&#39; Extensão &#39; atributo pode ser aplicado somente a &#39; Módulo &#39; &#39; Sub &#39; ou &#39; Função &#39; declarações"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc36550
- vbc36550
helpviewer_keywords: BC36550
ms.assetid: 4387a51f-733c-45d7-abdb-eb64d4f51078
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9d77933c52484eb934501107d1ddad15f0eca826
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="39extension39-attribute-can-be-applied-only-to-39module39-39sub39-or-39function39-declarations"></a><span data-ttu-id="e9116-102">&#39; Extensão &#39; atributo pode ser aplicado somente a &#39; Módulo &#39; &#39; Sub &#39; ou &#39; Função &#39; declarações</span><span class="sxs-lookup"><span data-stu-id="e9116-102">&#39;Extension&#39; attribute can be applied only to &#39;Module&#39;, &#39;Sub&#39;, or &#39;Function&#39; declarations</span></span>
<span data-ttu-id="e9116-103">A única maneira de estender um tipo de dados no Visual Basic é definir um método de extensão dentro de um módulo padrão.</span><span class="sxs-lookup"><span data-stu-id="e9116-103">The only way to extend a data type in Visual Basic is to define an extension method inside a standard module.</span></span> <span data-ttu-id="e9116-104">O método de extensão pode ser um `Sub` procedimento ou uma `Function` procedimento.</span><span class="sxs-lookup"><span data-stu-id="e9116-104">The extension method can be a `Sub` procedure or a `Function` procedure.</span></span> <span data-ttu-id="e9116-105">Todos os métodos de extensão devem ser marcados com o atributo de extensão, `<Extension()>`, do <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> namespace.</span><span class="sxs-lookup"><span data-stu-id="e9116-105">All extension methods must be marked with the extension attribute, `<Extension()>`, from the <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="e9116-106">Opcionalmente, um módulo que contém um método de extensão pode ser marcado da mesma maneira.</span><span class="sxs-lookup"><span data-stu-id="e9116-106">Optionally, a module that contains an extension method may be marked in the same way.</span></span> <span data-ttu-id="e9116-107">Nenhum outro uso do atributo de extensão é válido.</span><span class="sxs-lookup"><span data-stu-id="e9116-107">No other use of the extension attribute is valid.</span></span>  
  
 <span data-ttu-id="e9116-108">**ID do erro:** BC36550</span><span class="sxs-lookup"><span data-stu-id="e9116-108">**Error ID:** BC36550</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="e9116-109">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="e9116-109">To correct this error</span></span>  
  
-   <span data-ttu-id="e9116-110">Remova o atributo de extensão.</span><span class="sxs-lookup"><span data-stu-id="e9116-110">Remove the extension attribute.</span></span>  
  
-   <span data-ttu-id="e9116-111">Reprojete sua extensão como um método definido no módulo delimitador.</span><span class="sxs-lookup"><span data-stu-id="e9116-111">Redesign your extension as a method, defined in an enclosing module.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e9116-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e9116-112">Example</span></span>  
 <span data-ttu-id="e9116-113">O exemplo a seguir define uma `Print` método para o `String` tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="e9116-113">The following example defines a `Print` method for the `String` data type.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e9116-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e9116-114">See Also</span></span>  
 [<span data-ttu-id="e9116-115">Visão geral de atributos</span><span class="sxs-lookup"><span data-stu-id="e9116-115">Attributes overview</span></span>](../../../visual-basic/programming-guide/concepts/attributes/index.md)  
 [<span data-ttu-id="e9116-116">Métodos de Extensão</span><span class="sxs-lookup"><span data-stu-id="e9116-116">Extension Methods</span></span>](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)  
 [<span data-ttu-id="e9116-117">Instrução Module</span><span class="sxs-lookup"><span data-stu-id="e9116-117">Module Statement</span></span>](../../../visual-basic/language-reference/statements/module-statement.md)
