---
title: Como definir constantes em C#
description: Saiba como definir constantes em C#, que são campos cujos valores são definidos no momento da compilação. Use constantes para fornecer nomes significativos para valores especiais.
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, constants
- constants [C#]
ms.assetid: 43f511be-346c-4b8a-995e-aded94542ece
ms.openlocfilehash: dd8c6469c4d72da5588f0dce5314308bcc7e3b95
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91199114"
---
# <a name="how-to-define-constants-in-c"></a><span data-ttu-id="d31fd-104">Como definir constantes em C\#</span><span class="sxs-lookup"><span data-stu-id="d31fd-104">How to define constants in C\#</span></span>

<span data-ttu-id="d31fd-105">As constantes são campos cujos valores são definidos em tempo de compilação e nunca podem ser alterados.</span><span class="sxs-lookup"><span data-stu-id="d31fd-105">Constants are fields whose values are set at compile time and can never be changed.</span></span> <span data-ttu-id="d31fd-106">Use constantes para fornecer nomes significativos em vez de literais numéricos ("números mágicos") a valores especiais.</span><span class="sxs-lookup"><span data-stu-id="d31fd-106">Use constants to provide meaningful names instead of numeric literals ("magic numbers") for special values.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d31fd-107">No C#, a diretiva de pré-processador [#define](../../language-reference/preprocessor-directives/preprocessor-define.md) não pode ser utilizada para definir constantes da mesma maneira que é normalmente usada no C e no C++.</span><span class="sxs-lookup"><span data-stu-id="d31fd-107">In C# the [#define](../../language-reference/preprocessor-directives/preprocessor-define.md) preprocessor directive cannot be used to define constants in the way that is typically used in C and C++.</span></span>  
  
 <span data-ttu-id="d31fd-108">Para definir valores de constantes de tipos integrais (`int`, `byte` e assim por diante), use um tipo enumerado.</span><span class="sxs-lookup"><span data-stu-id="d31fd-108">To define constant values of integral types (`int`, `byte`, and so on) use an enumerated type.</span></span> <span data-ttu-id="d31fd-109">Para obter mais informações, consulte [enum](../../language-reference/builtin-types/enum.md).</span><span class="sxs-lookup"><span data-stu-id="d31fd-109">For more information, see [enum](../../language-reference/builtin-types/enum.md).</span></span>  
  
 <span data-ttu-id="d31fd-110">Para definir constantes não integrais, uma abordagem é agrupá-las em uma única classe estática de nome `Constants`.</span><span class="sxs-lookup"><span data-stu-id="d31fd-110">To define non-integral constants, one approach is to group them in a single static class named `Constants`.</span></span> <span data-ttu-id="d31fd-111">Isso exigirá que todas as referências às constantes sejam precedidas com o nome de classe, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="d31fd-111">This will require that all references to the constants be prefaced with the class name, as shown in the following example.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d31fd-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d31fd-112">Example</span></span>  

 [!code-csharp[csProgGuideObjects#89](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#89)]  
  
 <span data-ttu-id="d31fd-113">O uso do qualificador de nome de classe ajuda a garantir que você e outras pessoas que usam a constante entendam que ele é constante e não pode ser modificado.</span><span class="sxs-lookup"><span data-stu-id="d31fd-113">The use of the class name qualifier helps ensure that you and others who use the constant understand that it is constant and cannot be modified.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d31fd-114">Veja também</span><span class="sxs-lookup"><span data-stu-id="d31fd-114">See also</span></span>

- [<span data-ttu-id="d31fd-115">Classes e structs</span><span class="sxs-lookup"><span data-stu-id="d31fd-115">Classes and Structs</span></span>](./index.md)
