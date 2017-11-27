---
title: "Associações do (F#)"
description: "Saiba como F # 'do' associação é usado para executar código sem definir uma função ou um valor."
keywords: "visual f#, f#, programação funcional"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 4c1057a3-3aa1-4b64-b46a-25ffe33f0be9
ms.openlocfilehash: f2563d384b67c005c96c2ff487c786476d385e70
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="do-bindings"></a><span data-ttu-id="4b284-104">Associações do</span><span class="sxs-lookup"><span data-stu-id="4b284-104">do Bindings</span></span>

<span data-ttu-id="4b284-105">Um `do` associação é usada para executar o código sem definir uma função ou um valor.</span><span class="sxs-lookup"><span data-stu-id="4b284-105">A `do` binding is used to execute code without defining a function or value.</span></span> <span data-ttu-id="4b284-106">Além disso, associações pode ser usado em classes, consulte [ `do` associações em Classes](../members/do-bindings-in-classes.md).</span><span class="sxs-lookup"><span data-stu-id="4b284-106">Also, do bindings can be used in classes, see [`do` Bindings in Classes](../members/do-bindings-in-classes.md).</span></span>


## <a name="syntax"></a><span data-ttu-id="4b284-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4b284-107">Syntax</span></span>

```fsharp
[ attributes ]
[ do ]expression
```

## <a name="remarks"></a><span data-ttu-id="4b284-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="4b284-108">Remarks</span></span>
<span data-ttu-id="4b284-109">Use um `do` quando você quer executar código independentemente de uma definição de função ou o valor de associação.</span><span class="sxs-lookup"><span data-stu-id="4b284-109">Use a `do` binding when you want to execute code independently of a function or value definition.</span></span> <span data-ttu-id="4b284-110">A expressão em uma `do` associação deve retornar `unit`.</span><span class="sxs-lookup"><span data-stu-id="4b284-110">The expression in a `do` binding must return `unit`.</span></span> <span data-ttu-id="4b284-111">Código em um nível superior `do` associação é executada quando o módulo é inicializado.</span><span class="sxs-lookup"><span data-stu-id="4b284-111">Code in a top-level `do` binding is executed when the module is initialized.</span></span> <span data-ttu-id="4b284-112">A palavra-chave `do` é opcional.</span><span class="sxs-lookup"><span data-stu-id="4b284-112">The keyword `do` is optional.</span></span>

<span data-ttu-id="4b284-113">Atributos podem ser aplicados a um nível superior `do` associação.</span><span class="sxs-lookup"><span data-stu-id="4b284-113">Attributes can be applied to a top-level `do` binding.</span></span> <span data-ttu-id="4b284-114">Por exemplo, se o programa usa a interoperabilidade COM, convém aplicar o `STAThread` de atributo para o seu programa.</span><span class="sxs-lookup"><span data-stu-id="4b284-114">For example, if your program uses COM interop, you might want to apply the `STAThread` attribute to your program.</span></span> <span data-ttu-id="4b284-115">Você pode fazer isso usando um atributo em uma `do` de associação, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="4b284-115">You can do this by using an attribute on a `do` binding, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet201.fs)]
    
## <a name="see-also"></a><span data-ttu-id="4b284-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4b284-116">See Also</span></span>
[<span data-ttu-id="4b284-117">Referência da Linguagem F#</span><span class="sxs-lookup"><span data-stu-id="4b284-117">F# Language Reference</span></span>](../index.md)

[<span data-ttu-id="4b284-118">Funções</span><span class="sxs-lookup"><span data-stu-id="4b284-118">Functions</span></span>](index.md)

