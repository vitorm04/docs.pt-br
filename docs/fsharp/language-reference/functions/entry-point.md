---
title: Ponto de entrada (F#)
description: 'Saiba como configurar o ponto de entrada para um programa em F # que é compilado como um arquivo executável, onde formalmente início da execução.'
ms.date: 05/16/2016
ms.openlocfilehash: 3d6cab755dd89f2d3d669a8763aa08660432a0ac
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="entry-point"></a><span data-ttu-id="33948-103">Ponto de entrada</span><span class="sxs-lookup"><span data-stu-id="33948-103">Entry Point</span></span>

<span data-ttu-id="33948-104">Este tópico descreve o método que você usar para definir o ponto de entrada para um programa em F #.</span><span class="sxs-lookup"><span data-stu-id="33948-104">This topic describes the method that you use to set the entry point to an F# program.</span></span>


## <a name="syntax"></a><span data-ttu-id="33948-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="33948-105">Syntax</span></span>

```fsharp
[<EntryPoint>]
let-function-binding
```

## <a name="remarks"></a><span data-ttu-id="33948-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="33948-106">Remarks</span></span>
<span data-ttu-id="33948-107">Na sintaxe anterior, *permitem a associação de função* é a definição de uma função em um `let` associação.</span><span class="sxs-lookup"><span data-stu-id="33948-107">In the previous syntax, *let-function-binding* is the definition of a function in a `let` binding.</span></span>

<span data-ttu-id="33948-108">O ponto de entrada para um programa que é compilado como um arquivo executável é onde formalmente início da execução.</span><span class="sxs-lookup"><span data-stu-id="33948-108">The entry point to a program that is compiled as an executable file is where execution formally starts.</span></span> <span data-ttu-id="33948-109">Especifique o ponto de entrada para um aplicativo do F #, aplicando o `EntryPoint` de atributo para o programa `main` função.</span><span class="sxs-lookup"><span data-stu-id="33948-109">You specify the entry point to an F# application by applying the `EntryPoint` attribute to the program's `main` function.</span></span> <span data-ttu-id="33948-110">Essa função (criada usando um `let` associação) deve ser a última função no último arquivo compilado.</span><span class="sxs-lookup"><span data-stu-id="33948-110">This function (created by using a `let` binding) must be the last function in the last compiled file.</span></span> <span data-ttu-id="33948-111">O último arquivo compilado é o último arquivo do projeto ou o último arquivo que é passado para a linha de comando.</span><span class="sxs-lookup"><span data-stu-id="33948-111">The last compiled file is the last file in the project or the last file that is passed to the command line.</span></span>

<span data-ttu-id="33948-112">A função de ponto de entrada tem tipo `string array -> int`.</span><span class="sxs-lookup"><span data-stu-id="33948-112">The entry point function has type `string array -> int`.</span></span> <span data-ttu-id="33948-113">Os argumentos fornecidos na linha de comando são passados para o `main` função na matriz de cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="33948-113">The arguments provided on the command line are passed to the `main` function in the array of strings.</span></span> <span data-ttu-id="33948-114">O primeiro elemento da matriz é o primeiro argumento; o nome do arquivo executável não está incluído na matriz, pois ele está em algumas outras linguagens.</span><span class="sxs-lookup"><span data-stu-id="33948-114">The first element of the array is the first argument; the name of the executable file is not included in the array, as it is in some other languages.</span></span> <span data-ttu-id="33948-115">O valor de retorno é usado como o código de saída para o processo.</span><span class="sxs-lookup"><span data-stu-id="33948-115">The return value is used as the exit code for the process.</span></span> <span data-ttu-id="33948-116">Zero geralmente indica sucesso. valores diferentes de zero indicam um erro.</span><span class="sxs-lookup"><span data-stu-id="33948-116">Zero usually indicates success; nonzero values indicate an error.</span></span> <span data-ttu-id="33948-117">Não há nenhum convenção do significado específico de códigos de retorno diferente de zero; os significados dos códigos de retorno são específicas do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="33948-117">There is no convention for the specific meaning of nonzero return codes; the meanings of the return codes are application-specific.</span></span>

<span data-ttu-id="33948-118">O exemplo a seguir ilustra um simples `main` função.</span><span class="sxs-lookup"><span data-stu-id="33948-118">The following example illustrates a simple `main` function.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/entry-point/snippet501.fs)]

<span data-ttu-id="33948-119">Quando esse código é executado com a linha de comando `EntryPoint.exe 1 2 3`, a saída é da seguinte maneira.</span><span class="sxs-lookup"><span data-stu-id="33948-119">When this code is executed with the command line `EntryPoint.exe 1 2 3`, the output is as follows.</span></span>

```console
Arguments passed to function : [|"1"; "2"; "3"|]
```

## <a name="implicit-entry-point"></a><span data-ttu-id="33948-120">Ponto de entrada implícito</span><span class="sxs-lookup"><span data-stu-id="33948-120">Implicit Entry Point</span></span>
<span data-ttu-id="33948-121">Quando um programa não tem **EntryPoint** atributo que explicitamente indica o ponto de entrada, as associações de nível superior no último arquivo a ser compilado são usados como o ponto de entrada.</span><span class="sxs-lookup"><span data-stu-id="33948-121">When a program has no **EntryPoint** attribute that explicitly indicates the entry point, the top level bindings in the last file to be compiled are used as the entry point.</span></span>


## <a name="see-also"></a><span data-ttu-id="33948-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="33948-122">See Also</span></span>
[<span data-ttu-id="33948-123">Funções</span><span class="sxs-lookup"><span data-stu-id="33948-123">Functions</span></span>](index.md)

[<span data-ttu-id="33948-124">Associações let</span><span class="sxs-lookup"><span data-stu-id="33948-124">let Bindings</span></span>](let-bindings.md)
