---
title: Como criar um novo método para uma enumeração (Guia de Programação em C#)
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [C#]
- extension methods [C#], for enums
- enum extensibility [C#]
ms.assetid: 100106f9-1e54-462c-8ebe-3892fe23b6eb
ms.openlocfilehash: 8de44cbddf26af45245709d0e28d2d157256ce59
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33313027"
---
# <a name="how-to-create-a-new-method-for-an-enumeration-c-programming-guide"></a><span data-ttu-id="03e51-102">Como criar um novo método para uma enumeração (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="03e51-102">How to: Create a New Method for an Enumeration (C# Programming Guide)</span></span>
<span data-ttu-id="03e51-103">Você pode usar métodos de extensão para adicionar funcionalidades específica para um tipo de enumeração específico.</span><span class="sxs-lookup"><span data-stu-id="03e51-103">You can use extension methods to add functionality specific to a particular enum type.</span></span>  
  
## <a name="example"></a><span data-ttu-id="03e51-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="03e51-104">Example</span></span>  
 <span data-ttu-id="03e51-105">No exemplo a seguir, a enumeração `Grades` representa as letras possíveis que um aluno pode receber em uma classe.</span><span class="sxs-lookup"><span data-stu-id="03e51-105">In the following example, the `Grades` enumeration represents the possible letter grades that a student may receive in a class.</span></span> <span data-ttu-id="03e51-106">Um método de extensão chamado `Passing` é adicionado ao tipo `Grades` de forma que cada instância desse tipo agora "sabe" se ele representa uma nota de aprovação ou não.</span><span class="sxs-lookup"><span data-stu-id="03e51-106">An extension method named `Passing` is added to the `Grades` type so that each instance of that type now "knows" whether it represents a passing grade or not.</span></span>  
  
 [!code-csharp[csProgGuideExtensionMethods#2](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-create-a-new-method-for-an-enumeration_1.cs)]  
  
 <span data-ttu-id="03e51-107">Observe que a classe `Extensions` também contém uma variável estática atualizada dinamicamente e que o valor retornado do método de extensão reflete o valor atual dessa variável.</span><span class="sxs-lookup"><span data-stu-id="03e51-107">Note that the `Extensions` class also contains a static variable that is updated dynamically and that the return value of the extension method reflects the current value of that variable.</span></span> <span data-ttu-id="03e51-108">Isso demonstra que, nos bastidores, os métodos de extensão são chamados diretamente na classe estática na qual eles são definidos.</span><span class="sxs-lookup"><span data-stu-id="03e51-108">This demonstrates that, behind the scenes, extension methods are invoked directly on the static class in which they are defined.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="03e51-109">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="03e51-109">Compiling the Code</span></span>  
 <span data-ttu-id="03e51-110">Para executar esse código, copie e cole-o em um projeto de aplicativo de console do Visual C# que foi criado no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="03e51-110">To run this code, copy and paste it into a Visual C# console application project that has been created in Visual Studio.</span></span> <span data-ttu-id="03e51-111">Por padrão, esse projeto é direcionado para a versão 3.5 do [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] e ele tem uma referência ao System.Core.dll e uma diretriz `using` para System.Linq.</span><span class="sxs-lookup"><span data-stu-id="03e51-111">By default, this project targets version 3.5 of the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], and it has a reference to System.Core.dll and a `using` directive for System.Linq.</span></span> <span data-ttu-id="03e51-112">Se um ou mais desses requisitos estiverem ausentes no projeto, você poderá adicioná-los manualmente.</span><span class="sxs-lookup"><span data-stu-id="03e51-112">If one or more of these requirements are missing from the project, you can add them manually.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03e51-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="03e51-113">See Also</span></span>  
 [<span data-ttu-id="03e51-114">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="03e51-114">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="03e51-115">Métodos de Extensão</span><span class="sxs-lookup"><span data-stu-id="03e51-115">Extension Methods</span></span>](../../../csharp/programming-guide/classes-and-structs/extension-methods.md)
