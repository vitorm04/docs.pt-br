---
title: Como criar um novo método para um guia de C# programação de enumeração
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [C#]
- extension methods [C#], for enums
- enum extensibility [C#]
ms.assetid: 100106f9-1e54-462c-8ebe-3892fe23b6eb
ms.openlocfilehash: 02af55c851392ce5dde4c83fd32d18b927950a3f
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73971025"
---
# <a name="how-to-create-a-new-method-for-an-enumeration-c-programming-guide"></a><span data-ttu-id="3371f-102">Como criar um novo método para uma enumeração (C# guia de programação)</span><span class="sxs-lookup"><span data-stu-id="3371f-102">How to create a new method for an enumeration (C# Programming Guide)</span></span>
<span data-ttu-id="3371f-103">Você pode usar métodos de extensão para adicionar funcionalidades específica para um tipo de enumeração específico.</span><span class="sxs-lookup"><span data-stu-id="3371f-103">You can use extension methods to add functionality specific to a particular enum type.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3371f-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3371f-104">Example</span></span>  
 <span data-ttu-id="3371f-105">No exemplo a seguir, a enumeração `Grades` representa as letras possíveis que um aluno pode receber em uma classe.</span><span class="sxs-lookup"><span data-stu-id="3371f-105">In the following example, the `Grades` enumeration represents the possible letter grades that a student may receive in a class.</span></span> <span data-ttu-id="3371f-106">Um método de extensão chamado `Passing` é adicionado ao tipo `Grades` de forma que cada instância desse tipo agora "sabe" se ele representa uma nota de aprovação ou não.</span><span class="sxs-lookup"><span data-stu-id="3371f-106">An extension method named `Passing` is added to the `Grades` type so that each instance of that type now "knows" whether it represents a passing grade or not.</span></span>  
  
 [!code-csharp[csProgGuideExtensionMethods#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExtensionMethods/cs/extensionmethods.cs#2)]  
  
 <span data-ttu-id="3371f-107">Observe que a classe `Extensions` também contém uma variável estática atualizada dinamicamente e que o valor retornado do método de extensão reflete o valor atual dessa variável.</span><span class="sxs-lookup"><span data-stu-id="3371f-107">Note that the `Extensions` class also contains a static variable that is updated dynamically and that the return value of the extension method reflects the current value of that variable.</span></span> <span data-ttu-id="3371f-108">Isso demonstra que, nos bastidores, os métodos de extensão são chamados diretamente na classe estática na qual eles são definidos.</span><span class="sxs-lookup"><span data-stu-id="3371f-108">This demonstrates that, behind the scenes, extension methods are invoked directly on the static class in which they are defined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3371f-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3371f-109">See also</span></span>

- [<span data-ttu-id="3371f-110">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="3371f-110">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="3371f-111">Métodos de Extensão</span><span class="sxs-lookup"><span data-stu-id="3371f-111">Extension Methods</span></span>](./extension-methods.md)
