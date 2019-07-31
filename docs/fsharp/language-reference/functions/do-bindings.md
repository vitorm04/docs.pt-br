---
title: Associações do
description: Saiba como uma F# Associação ' do ' é usada para executar o código sem definir uma função ou um valor.
ms.date: 05/16/2016
ms.openlocfilehash: f98f523296bfaceeda35d4861eafbfeaa5a60c32
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630531"
---
# <a name="do-bindings"></a><span data-ttu-id="7aa10-103">Associações do</span><span class="sxs-lookup"><span data-stu-id="7aa10-103">do Bindings</span></span>

<span data-ttu-id="7aa10-104">Uma `do` associação é usada para executar código sem definir uma função ou um valor.</span><span class="sxs-lookup"><span data-stu-id="7aa10-104">A `do` binding is used to execute code without defining a function or value.</span></span> <span data-ttu-id="7aa10-105">Além disso, as associações podem ser usadas em classes, consulte [ `do` associações em classes](../members/do-bindings-in-classes.md).</span><span class="sxs-lookup"><span data-stu-id="7aa10-105">Also, do bindings can be used in classes, see [`do` Bindings in Classes](../members/do-bindings-in-classes.md).</span></span>

## <a name="syntax"></a><span data-ttu-id="7aa10-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7aa10-106">Syntax</span></span>

```fsharp
[ attributes ]
[ do ]expression
```

## <a name="remarks"></a><span data-ttu-id="7aa10-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="7aa10-107">Remarks</span></span>

<span data-ttu-id="7aa10-108">Use uma `do` associação quando desejar executar código independentemente de uma definição de função ou valor.</span><span class="sxs-lookup"><span data-stu-id="7aa10-108">Use a `do` binding when you want to execute code independently of a function or value definition.</span></span> <span data-ttu-id="7aa10-109">A expressão em uma `do` associação deve retornar `unit`.</span><span class="sxs-lookup"><span data-stu-id="7aa10-109">The expression in a `do` binding must return `unit`.</span></span> <span data-ttu-id="7aa10-110">O código em uma associação de `do` nível superior é executado quando o módulo é inicializado.</span><span class="sxs-lookup"><span data-stu-id="7aa10-110">Code in a top-level `do` binding is executed when the module is initialized.</span></span> <span data-ttu-id="7aa10-111">A palavra `do` -chave é opcional.</span><span class="sxs-lookup"><span data-stu-id="7aa10-111">The keyword `do` is optional.</span></span>

<span data-ttu-id="7aa10-112">Os atributos podem ser aplicados a uma associação de `do` nível superior.</span><span class="sxs-lookup"><span data-stu-id="7aa10-112">Attributes can be applied to a top-level `do` binding.</span></span> <span data-ttu-id="7aa10-113">Por exemplo, se o seu programa usar a interoperabilidade com, talvez você `STAThread` queira aplicar o atributo ao seu programa.</span><span class="sxs-lookup"><span data-stu-id="7aa10-113">For example, if your program uses COM interop, you might want to apply the `STAThread` attribute to your program.</span></span> <span data-ttu-id="7aa10-114">Você pode fazer isso usando um atributo em uma `do` associação, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="7aa10-114">You can do this by using an attribute on a `do` binding, as shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet201.fs)]

## <a name="see-also"></a><span data-ttu-id="7aa10-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7aa10-115">See also</span></span>

- [<span data-ttu-id="7aa10-116">Referência da Linguagem F#</span><span class="sxs-lookup"><span data-stu-id="7aa10-116">F# Language Reference</span></span>](../index.md)
- [<span data-ttu-id="7aa10-117">Funções</span><span class="sxs-lookup"><span data-stu-id="7aa10-117">Functions</span></span>](index.md)
