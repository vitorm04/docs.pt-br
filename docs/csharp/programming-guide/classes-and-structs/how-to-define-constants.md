---
title: 'Como: Definir constantes em C#'
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, constants
- constants [C#]
ms.assetid: 43f511be-346c-4b8a-995e-aded94542ece
ms.openlocfilehash: 26d46335df3333379d5577a5c21a85a39eb6e43a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54713191"
---
# <a name="how-to-define-constants-in-c"></a><span data-ttu-id="d47b2-102">Como: Definir constantes em C#</span><span class="sxs-lookup"><span data-stu-id="d47b2-102">How to: Define Constants in C#</span></span>
<span data-ttu-id="d47b2-103">As constantes são campos cujos valores são definidos em tempo de compilação e nunca podem ser alterados.</span><span class="sxs-lookup"><span data-stu-id="d47b2-103">Constants are fields whose values are set at compile time and can never be changed.</span></span> <span data-ttu-id="d47b2-104">Use constantes para fornecer nomes significativos em vez de literais numéricos ("números mágicos") a valores especiais.</span><span class="sxs-lookup"><span data-stu-id="d47b2-104">Use constants to provide meaningful names instead of numeric literals ("magic numbers") for special values.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d47b2-105">No C#, a diretiva de pré-processador [#define](../../../csharp/language-reference/preprocessor-directives/preprocessor-define.md) não pode ser utilizada para definir constantes da mesma maneira que é normalmente usada no C e no C++.</span><span class="sxs-lookup"><span data-stu-id="d47b2-105">In C# the [#define](../../../csharp/language-reference/preprocessor-directives/preprocessor-define.md) preprocessor directive cannot be used to define constants in the way that is typically used in C and C++.</span></span>  
  
 <span data-ttu-id="d47b2-106">Para definir valores de constantes de tipos integrais (`int`, `byte` e assim por diante), use um tipo enumerado.</span><span class="sxs-lookup"><span data-stu-id="d47b2-106">To define constant values of integral types (`int`, `byte`, and so on) use an enumerated type.</span></span> <span data-ttu-id="d47b2-107">Para obter mais informações, consulte [enum](../../../csharp/language-reference/keywords/enum.md).</span><span class="sxs-lookup"><span data-stu-id="d47b2-107">For more information, see [enum](../../../csharp/language-reference/keywords/enum.md).</span></span>  
  
 <span data-ttu-id="d47b2-108">Para definir constantes não integrais, uma abordagem é agrupá-las em uma única classe estática de nome `Constants`.</span><span class="sxs-lookup"><span data-stu-id="d47b2-108">To define non-integral constants, one approach is to group them in a single static class named `Constants`.</span></span> <span data-ttu-id="d47b2-109">Isso exigirá que todas as referências às constantes sejam precedidas com o nome de classe, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="d47b2-109">This will require that all references to the constants be prefaced with the class name, as shown in the following example.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d47b2-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d47b2-110">Example</span></span>  
 [!code-csharp[csProgGuideObjects#89](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-define-constants_1.cs)]  
  
 <span data-ttu-id="d47b2-111">O uso do qualificador de nome de classe ajuda a garantir que você e outras pessoas que usam a constante entendam que ele é constante e não pode ser modificado.</span><span class="sxs-lookup"><span data-stu-id="d47b2-111">The use of the class name qualifier helps ensure that you and others who use the constant understand that it is constant and cannot be modified.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d47b2-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d47b2-112">See also</span></span>

- [<span data-ttu-id="d47b2-113">Classes e Structs</span><span class="sxs-lookup"><span data-stu-id="d47b2-113">Classes and Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/index.md)
