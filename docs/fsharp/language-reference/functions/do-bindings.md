---
title: Associações do (F#)
description: "Saiba como F # 'do' associação é usado para executar o código sem definir uma função ou um valor."
ms.date: 05/16/2016
ms.openlocfilehash: 78dbf8da0fe40b5af566ad98693df1109eede7e4
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44192140"
---
# <a name="do-bindings"></a><span data-ttu-id="b2031-103">Associações do</span><span class="sxs-lookup"><span data-stu-id="b2031-103">do Bindings</span></span>

<span data-ttu-id="b2031-104">Um `do` associação é usada para executar o código sem definir uma função ou um valor.</span><span class="sxs-lookup"><span data-stu-id="b2031-104">A `do` binding is used to execute code without defining a function or value.</span></span> <span data-ttu-id="b2031-105">Além disso, as associações fazem pode ser usado em classes, consulte [ `do` associações em Classes](../members/do-bindings-in-classes.md).</span><span class="sxs-lookup"><span data-stu-id="b2031-105">Also, do bindings can be used in classes, see [`do` Bindings in Classes](../members/do-bindings-in-classes.md).</span></span>

## <a name="syntax"></a><span data-ttu-id="b2031-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b2031-106">Syntax</span></span>

```fsharp
[ attributes ]
[ do ]expression
```

## <a name="remarks"></a><span data-ttu-id="b2031-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="b2031-107">Remarks</span></span>

<span data-ttu-id="b2031-108">Use um `do` quando você deseja executar o código, independentemente de uma definição de função ou o valor de associação.</span><span class="sxs-lookup"><span data-stu-id="b2031-108">Use a `do` binding when you want to execute code independently of a function or value definition.</span></span> <span data-ttu-id="b2031-109">A expressão em uma `do` associação deve retornar `unit`.</span><span class="sxs-lookup"><span data-stu-id="b2031-109">The expression in a `do` binding must return `unit`.</span></span> <span data-ttu-id="b2031-110">Código em um nível superior `do` associação é executada quando o módulo é inicializado.</span><span class="sxs-lookup"><span data-stu-id="b2031-110">Code in a top-level `do` binding is executed when the module is initialized.</span></span> <span data-ttu-id="b2031-111">A palavra-chave `do` é opcional.</span><span class="sxs-lookup"><span data-stu-id="b2031-111">The keyword `do` is optional.</span></span>

<span data-ttu-id="b2031-112">Atributos podem ser aplicados a um nível superior `do` associação.</span><span class="sxs-lookup"><span data-stu-id="b2031-112">Attributes can be applied to a top-level `do` binding.</span></span> <span data-ttu-id="b2031-113">Por exemplo, se seu programa usa interoperabilidade COM, você talvez queira aplicar o `STAThread` de atributo para o seu programa.</span><span class="sxs-lookup"><span data-stu-id="b2031-113">For example, if your program uses COM interop, you might want to apply the `STAThread` attribute to your program.</span></span> <span data-ttu-id="b2031-114">Você pode fazer isso usando um atributo em um `do` de associação, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="b2031-114">You can do this by using an attribute on a `do` binding, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet201.fs)]

## <a name="see-also"></a><span data-ttu-id="b2031-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b2031-115">See also</span></span>

- [<span data-ttu-id="b2031-116">Referência da Linguagem F#</span><span class="sxs-lookup"><span data-stu-id="b2031-116">F# Language Reference</span></span>](../index.md)
- [<span data-ttu-id="b2031-117">Funções</span><span class="sxs-lookup"><span data-stu-id="b2031-117">Functions</span></span>](index.md)
