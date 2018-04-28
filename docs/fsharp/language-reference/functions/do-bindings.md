---
title: Associações do (F#)
description: "Saiba como F # 'do' associação é usado para executar código sem definir uma função ou um valor."
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 4c63da0c5e2f4130d59f9efa6bc54a55e5fe9fd8
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2018
---
# <a name="do-bindings"></a><span data-ttu-id="62cd1-103">Associações do</span><span class="sxs-lookup"><span data-stu-id="62cd1-103">do Bindings</span></span>

<span data-ttu-id="62cd1-104">Um `do` associação é usada para executar o código sem definir uma função ou um valor.</span><span class="sxs-lookup"><span data-stu-id="62cd1-104">A `do` binding is used to execute code without defining a function or value.</span></span> <span data-ttu-id="62cd1-105">Além disso, associações pode ser usado em classes, consulte [ `do` associações em Classes](../members/do-bindings-in-classes.md).</span><span class="sxs-lookup"><span data-stu-id="62cd1-105">Also, do bindings can be used in classes, see [`do` Bindings in Classes](../members/do-bindings-in-classes.md).</span></span>


## <a name="syntax"></a><span data-ttu-id="62cd1-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="62cd1-106">Syntax</span></span>

```fsharp
[ attributes ]
[ do ]expression
```

## <a name="remarks"></a><span data-ttu-id="62cd1-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="62cd1-107">Remarks</span></span>
<span data-ttu-id="62cd1-108">Use um `do` quando você quer executar código independentemente de uma definição de função ou o valor de associação.</span><span class="sxs-lookup"><span data-stu-id="62cd1-108">Use a `do` binding when you want to execute code independently of a function or value definition.</span></span> <span data-ttu-id="62cd1-109">A expressão em uma `do` associação deve retornar `unit`.</span><span class="sxs-lookup"><span data-stu-id="62cd1-109">The expression in a `do` binding must return `unit`.</span></span> <span data-ttu-id="62cd1-110">Código em um nível superior `do` associação é executada quando o módulo é inicializado.</span><span class="sxs-lookup"><span data-stu-id="62cd1-110">Code in a top-level `do` binding is executed when the module is initialized.</span></span> <span data-ttu-id="62cd1-111">A palavra-chave `do` é opcional.</span><span class="sxs-lookup"><span data-stu-id="62cd1-111">The keyword `do` is optional.</span></span>

<span data-ttu-id="62cd1-112">Atributos podem ser aplicados a um nível superior `do` associação.</span><span class="sxs-lookup"><span data-stu-id="62cd1-112">Attributes can be applied to a top-level `do` binding.</span></span> <span data-ttu-id="62cd1-113">Por exemplo, se o programa usa a interoperabilidade COM, convém aplicar o `STAThread` de atributo para o seu programa.</span><span class="sxs-lookup"><span data-stu-id="62cd1-113">For example, if your program uses COM interop, you might want to apply the `STAThread` attribute to your program.</span></span> <span data-ttu-id="62cd1-114">Você pode fazer isso usando um atributo em uma `do` de associação, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="62cd1-114">You can do this by using an attribute on a `do` binding, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet201.fs)]
    
## <a name="see-also"></a><span data-ttu-id="62cd1-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="62cd1-115">See Also</span></span>
[<span data-ttu-id="62cd1-116">Referência da Linguagem F#</span><span class="sxs-lookup"><span data-stu-id="62cd1-116">F# Language Reference</span></span>](../index.md)

[<span data-ttu-id="62cd1-117">Funções</span><span class="sxs-lookup"><span data-stu-id="62cd1-117">Functions</span></span>](index.md)

