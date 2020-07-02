---
ms.openlocfilehash: 9a2d6a25a8ab1b8bf65b947557802e0805a7f826
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617107"
---
### <a name="foreach-iterator-variable-is-now-scoped-within-the-iteration-so-closure-capturing-semantics-are-different-in-c5"></a><span data-ttu-id="25554-101">A variável do iterador Foreach agora tem escopo na iteração, de modo que as semânticas de captura de fechamento são diferentes (no C#5)</span><span class="sxs-lookup"><span data-stu-id="25554-101">Foreach iterator variable is now scoped within the iteration, so closure capturing semantics are different (in C#5)</span></span>

#### <a name="details"></a><span data-ttu-id="25554-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="25554-102">Details</span></span>

<span data-ttu-id="25554-103">A partir do C# 5 (Visual Studio 2012), as variáveis do iterador `foreach` têm escopo dentro da iteração.</span><span class="sxs-lookup"><span data-stu-id="25554-103">Beginning with C# 5 (Visual Studio 2012), `foreach` iterator variables are scoped within the iteration.</span></span> <span data-ttu-id="25554-104">Isso poderá causar interrupções se o código anteriormente dependia das variáveis para não ser incluído no fechamento de `foreach`.</span><span class="sxs-lookup"><span data-stu-id="25554-104">This can cause breaks if code was previously depending on the variables to not be included in the `foreach`'s closure.</span></span> <span data-ttu-id="25554-105">O sintoma dessa alteração será que uma variável do iterador passada a um delegado será tratada com o valor que ela tinha no momento em que o delegado foi criado, e não com o valor que ela tinha no momento em que o delegado foi invocado.</span><span class="sxs-lookup"><span data-stu-id="25554-105">The symptom of this change is that an iterator variable passed to a delegate is treated as the value it has at the time the delegate is created, rather than the value it has at the time the delegate is invoked.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="25554-106">Sugestão</span><span class="sxs-lookup"><span data-stu-id="25554-106">Suggestion</span></span>

<span data-ttu-id="25554-107">De maneira ideal, o código deve ser atualizado para esperar o novo comportamento do compilador.</span><span class="sxs-lookup"><span data-stu-id="25554-107">Ideally, code should be updated to expect the new compiler behavior.</span></span> <span data-ttu-id="25554-108">Se as semânticas antigas forem necessárias, a variável do iterador poderá ser substituída por uma variável separada que seja explicitamente colocada fora do escopo do loop.</span><span class="sxs-lookup"><span data-stu-id="25554-108">If the old semantics are required, the iterator variable can be replaced with a separate variable which is explicitly placed outside of the loop's scope.</span></span>

| <span data-ttu-id="25554-109">Name</span><span class="sxs-lookup"><span data-stu-id="25554-109">Name</span></span>    | <span data-ttu-id="25554-110">Valor</span><span class="sxs-lookup"><span data-stu-id="25554-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="25554-111">Escopo</span><span class="sxs-lookup"><span data-stu-id="25554-111">Scope</span></span>   | <span data-ttu-id="25554-112">Principal</span><span class="sxs-lookup"><span data-stu-id="25554-112">Major</span></span>       |
| <span data-ttu-id="25554-113">Versão</span><span class="sxs-lookup"><span data-stu-id="25554-113">Version</span></span> | <span data-ttu-id="25554-114">4.5</span><span class="sxs-lookup"><span data-stu-id="25554-114">4.5</span></span>         |
| <span data-ttu-id="25554-115">Type</span><span class="sxs-lookup"><span data-stu-id="25554-115">Type</span></span>    | <span data-ttu-id="25554-116">Redirecionando</span><span class="sxs-lookup"><span data-stu-id="25554-116">Retargeting</span></span> |
