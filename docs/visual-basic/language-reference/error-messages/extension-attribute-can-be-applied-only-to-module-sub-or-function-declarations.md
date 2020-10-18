---
title: O atributo 'Extension' pode ser aplicado apenas às declarações 'Module', 'Sub' ou 'Function'
ms.date: 07/20/2015
f1_keywords:
- bc36550
- vbc36550
helpviewer_keywords:
- BC36550
ms.assetid: 4387a51f-733c-45d7-abdb-eb64d4f51078
ms.openlocfilehash: bd4d14721b93800831dbce897535b4f5956fe9c7
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92160744"
---
# <a name="bc36550-extension-attribute-can-be-applied-only-to-module-sub-or-function-declarations"></a><span data-ttu-id="f4808-102">BC36550: o atributo ' extension ' só pode ser aplicado a declarações ' module ', ' Sub ' ou ' function '</span><span class="sxs-lookup"><span data-stu-id="f4808-102">BC36550: 'Extension' attribute can be applied only to 'Module', 'Sub', or 'Function' declarations</span></span>

<span data-ttu-id="f4808-103">A única maneira de estender um tipo de dados no Visual Basic é definir um método de extensão dentro de um módulo padrão.</span><span class="sxs-lookup"><span data-stu-id="f4808-103">The only way to extend a data type in Visual Basic is to define an extension method inside a standard module.</span></span> <span data-ttu-id="f4808-104">O método de extensão pode ser um `Sub` procedimento ou um `Function` procedimento.</span><span class="sxs-lookup"><span data-stu-id="f4808-104">The extension method can be a `Sub` procedure or a `Function` procedure.</span></span> <span data-ttu-id="f4808-105">Todos os métodos de extensão devem ser marcados com o atributo de extensão, `<Extension()>` , do <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> namespace.</span><span class="sxs-lookup"><span data-stu-id="f4808-105">All extension methods must be marked with the extension attribute, `<Extension()>`, from the <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="f4808-106">Opcionalmente, um módulo que contém um método de extensão pode ser marcado da mesma maneira.</span><span class="sxs-lookup"><span data-stu-id="f4808-106">Optionally, a module that contains an extension method may be marked in the same way.</span></span> <span data-ttu-id="f4808-107">Nenhum outro uso do atributo de extensão é válido.</span><span class="sxs-lookup"><span data-stu-id="f4808-107">No other use of the extension attribute is valid.</span></span>

<span data-ttu-id="f4808-108">**ID do erro:** BC36550</span><span class="sxs-lookup"><span data-stu-id="f4808-108">**Error ID:** BC36550</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="f4808-109">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="f4808-109">To correct this error</span></span>

- <span data-ttu-id="f4808-110">Remova o atributo de extensão.</span><span class="sxs-lookup"><span data-stu-id="f4808-110">Remove the extension attribute.</span></span>

- <span data-ttu-id="f4808-111">Reprojete sua extensão como um método, definido em um módulo delimitador.</span><span class="sxs-lookup"><span data-stu-id="f4808-111">Redesign your extension as a method, defined in an enclosing module.</span></span>

## <a name="example"></a><span data-ttu-id="f4808-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f4808-112">Example</span></span>

<span data-ttu-id="f4808-113">O exemplo a seguir define um `Print` método para o `String` tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="f4808-113">The following example defines a `Print` method for the `String` data type.</span></span>

```vb
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

## <a name="see-also"></a><span data-ttu-id="f4808-114">Veja também</span><span class="sxs-lookup"><span data-stu-id="f4808-114">See also</span></span>

- [<span data-ttu-id="f4808-115">Visão geral de atributos</span><span class="sxs-lookup"><span data-stu-id="f4808-115">Attributes overview</span></span>](../../programming-guide/concepts/attributes/index.md)
- [<span data-ttu-id="f4808-116">Métodos de Extensão</span><span class="sxs-lookup"><span data-stu-id="f4808-116">Extension Methods</span></span>](../../programming-guide/language-features/procedures/extension-methods.md)
- [<span data-ttu-id="f4808-117">Instrução Module</span><span class="sxs-lookup"><span data-stu-id="f4808-117">Module Statement</span></span>](../statements/module-statement.md)
