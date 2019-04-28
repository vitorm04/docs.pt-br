---
title: O atributo 'Extension' pode ser aplicado apenas às declarações 'Module', 'Sub' ou 'Function'
ms.date: 07/20/2015
f1_keywords:
- bc36550
- vbc36550
helpviewer_keywords:
- BC36550
ms.assetid: 4387a51f-733c-45d7-abdb-eb64d4f51078
ms.openlocfilehash: a4561359e4d7cb0f6ebe44a5deb09b3374556ed8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61801641"
---
# <a name="extension-attribute-can-be-applied-only-to-module-sub-or-function-declarations"></a><span data-ttu-id="0403f-102">O atributo 'Extension' pode ser aplicado apenas às declarações 'Module', 'Sub' ou 'Function'</span><span class="sxs-lookup"><span data-stu-id="0403f-102">'Extension' attribute can be applied only to 'Module', 'Sub', or 'Function' declarations</span></span>
<span data-ttu-id="0403f-103">A única maneira de estender um tipo de dados no Visual Basic é definir um método de extensão dentro de um módulo padrão.</span><span class="sxs-lookup"><span data-stu-id="0403f-103">The only way to extend a data type in Visual Basic is to define an extension method inside a standard module.</span></span> <span data-ttu-id="0403f-104">O método de extensão pode ser um `Sub` procedimento ou uma `Function` procedimento.</span><span class="sxs-lookup"><span data-stu-id="0403f-104">The extension method can be a `Sub` procedure or a `Function` procedure.</span></span> <span data-ttu-id="0403f-105">Todos os métodos de extensão devem ser marcados com o atributo de extensão `<Extension()>`, da <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> namespace.</span><span class="sxs-lookup"><span data-stu-id="0403f-105">All extension methods must be marked with the extension attribute, `<Extension()>`, from the <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="0403f-106">Opcionalmente, um módulo que contém um método de extensão pode ser marcado da mesma maneira.</span><span class="sxs-lookup"><span data-stu-id="0403f-106">Optionally, a module that contains an extension method may be marked in the same way.</span></span> <span data-ttu-id="0403f-107">Nenhum outro uso do atributo de extensão é válido.</span><span class="sxs-lookup"><span data-stu-id="0403f-107">No other use of the extension attribute is valid.</span></span>  
  
 <span data-ttu-id="0403f-108">**ID do erro:** BC36550</span><span class="sxs-lookup"><span data-stu-id="0403f-108">**Error ID:** BC36550</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="0403f-109">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="0403f-109">To correct this error</span></span>  
  
- <span data-ttu-id="0403f-110">Remova o atributo de extensão.</span><span class="sxs-lookup"><span data-stu-id="0403f-110">Remove the extension attribute.</span></span>  
  
- <span data-ttu-id="0403f-111">Reprojetar sua extensão como um método, definido no módulo delimitador.</span><span class="sxs-lookup"><span data-stu-id="0403f-111">Redesign your extension as a method, defined in an enclosing module.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0403f-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0403f-112">Example</span></span>  
 <span data-ttu-id="0403f-113">O exemplo a seguir define uma `Print` método para o `String` tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="0403f-113">The following example defines a `Print` method for the `String` data type.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="0403f-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0403f-114">See also</span></span>

- [<span data-ttu-id="0403f-115">Visão geral de atributos</span><span class="sxs-lookup"><span data-stu-id="0403f-115">Attributes overview</span></span>](../../../visual-basic/programming-guide/concepts/attributes/index.md)
- [<span data-ttu-id="0403f-116">Métodos de Extensão</span><span class="sxs-lookup"><span data-stu-id="0403f-116">Extension Methods</span></span>](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)
- [<span data-ttu-id="0403f-117">Instrução Module</span><span class="sxs-lookup"><span data-stu-id="0403f-117">Module Statement</span></span>](../../../visual-basic/language-reference/statements/module-statement.md)
