---
title: Associações do
description: Saiba como um F# 'do' associação é usado para executar o código sem definir uma função ou um valor.
ms.date: 05/16/2016
ms.openlocfilehash: 0755e36912fc4e5a645e55eb4bee5c730a56cadf
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65641904"
---
# <a name="do-bindings"></a><span data-ttu-id="bf16e-103">Associações do</span><span class="sxs-lookup"><span data-stu-id="bf16e-103">do Bindings</span></span>

<span data-ttu-id="bf16e-104">Um `do` associação é usada para executar o código sem definir uma função ou um valor.</span><span class="sxs-lookup"><span data-stu-id="bf16e-104">A `do` binding is used to execute code without defining a function or value.</span></span> <span data-ttu-id="bf16e-105">Além disso, as associações fazem pode ser usado em classes, consulte [ `do` associações em Classes](../members/do-bindings-in-classes.md).</span><span class="sxs-lookup"><span data-stu-id="bf16e-105">Also, do bindings can be used in classes, see [`do` Bindings in Classes](../members/do-bindings-in-classes.md).</span></span>

## <a name="syntax"></a><span data-ttu-id="bf16e-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bf16e-106">Syntax</span></span>

```fsharp
[ attributes ]
[ do ]expression
```

## <a name="remarks"></a><span data-ttu-id="bf16e-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="bf16e-107">Remarks</span></span>

<span data-ttu-id="bf16e-108">Use um `do` quando você deseja executar o código, independentemente de uma definição de função ou o valor de associação.</span><span class="sxs-lookup"><span data-stu-id="bf16e-108">Use a `do` binding when you want to execute code independently of a function or value definition.</span></span> <span data-ttu-id="bf16e-109">A expressão em uma `do` associação deve retornar `unit`.</span><span class="sxs-lookup"><span data-stu-id="bf16e-109">The expression in a `do` binding must return `unit`.</span></span> <span data-ttu-id="bf16e-110">Código em um nível superior `do` associação é executada quando o módulo é inicializado.</span><span class="sxs-lookup"><span data-stu-id="bf16e-110">Code in a top-level `do` binding is executed when the module is initialized.</span></span> <span data-ttu-id="bf16e-111">A palavra-chave `do` é opcional.</span><span class="sxs-lookup"><span data-stu-id="bf16e-111">The keyword `do` is optional.</span></span>

<span data-ttu-id="bf16e-112">Atributos podem ser aplicados a um nível superior `do` associação.</span><span class="sxs-lookup"><span data-stu-id="bf16e-112">Attributes can be applied to a top-level `do` binding.</span></span> <span data-ttu-id="bf16e-113">Por exemplo, se seu programa usa interoperabilidade COM, você talvez queira aplicar o `STAThread` de atributo para o seu programa.</span><span class="sxs-lookup"><span data-stu-id="bf16e-113">For example, if your program uses COM interop, you might want to apply the `STAThread` attribute to your program.</span></span> <span data-ttu-id="bf16e-114">Você pode fazer isso usando um atributo em um `do` de associação, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="bf16e-114">You can do this by using an attribute on a `do` binding, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet201.fs)]

## <a name="see-also"></a><span data-ttu-id="bf16e-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bf16e-115">See also</span></span>

- [<span data-ttu-id="bf16e-116">Referência da Linguagem F#</span><span class="sxs-lookup"><span data-stu-id="bf16e-116">F# Language Reference</span></span>](../index.md)
- [<span data-ttu-id="bf16e-117">Funções</span><span class="sxs-lookup"><span data-stu-id="bf16e-117">Functions</span></span>](index.md)
