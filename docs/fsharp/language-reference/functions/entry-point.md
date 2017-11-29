---
title: Ponto de entrada (F#)
description: "Saiba como configurar o ponto de entrada para um programa em F # que é compilado como um arquivo executável, onde formalmente início da execução."
keywords: "visual f#, f#, programação funcional"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 91455443-ff9d-4510-a7e9-1560bdcd0bb0
ms.openlocfilehash: 685fd4da67119aa5fcaaffd142a0a17c8f5dc7f6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="entry-point"></a><span data-ttu-id="6ab64-104">Ponto de entrada</span><span class="sxs-lookup"><span data-stu-id="6ab64-104">Entry Point</span></span>

<span data-ttu-id="6ab64-105">Este tópico descreve o método que você usar para definir o ponto de entrada para um programa em F #.</span><span class="sxs-lookup"><span data-stu-id="6ab64-105">This topic describes the method that you use to set the entry point to an F# program.</span></span>


## <a name="syntax"></a><span data-ttu-id="6ab64-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6ab64-106">Syntax</span></span>

```fsharp
[<EntryPoint>]
let-function-binding
```

## <a name="remarks"></a><span data-ttu-id="6ab64-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="6ab64-107">Remarks</span></span>
<span data-ttu-id="6ab64-108">Na sintaxe anterior, *permitem a associação de função* é a definição de uma função em um `let` associação.</span><span class="sxs-lookup"><span data-stu-id="6ab64-108">In the previous syntax, *let-function-binding* is the definition of a function in a `let` binding.</span></span>

<span data-ttu-id="6ab64-109">O ponto de entrada para um programa que é compilado como um arquivo executável é onde formalmente início da execução.</span><span class="sxs-lookup"><span data-stu-id="6ab64-109">The entry point to a program that is compiled as an executable file is where execution formally starts.</span></span> <span data-ttu-id="6ab64-110">Especifique o ponto de entrada para um aplicativo do F #, aplicando o `EntryPoint` de atributo para o programa `main` função.</span><span class="sxs-lookup"><span data-stu-id="6ab64-110">You specify the entry point to an F# application by applying the `EntryPoint` attribute to the program's `main` function.</span></span> <span data-ttu-id="6ab64-111">Essa função (criada usando um `let` associação) deve ser a última função no último arquivo compilado.</span><span class="sxs-lookup"><span data-stu-id="6ab64-111">This function (created by using a `let` binding) must be the last function in the last compiled file.</span></span> <span data-ttu-id="6ab64-112">O último arquivo compilado é o último arquivo do projeto ou o último arquivo que é passado para a linha de comando.</span><span class="sxs-lookup"><span data-stu-id="6ab64-112">The last compiled file is the last file in the project or the last file that is passed to the command line.</span></span>

<span data-ttu-id="6ab64-113">A função de ponto de entrada tem tipo `string array -> int`.</span><span class="sxs-lookup"><span data-stu-id="6ab64-113">The entry point function has type `string array -> int`.</span></span> <span data-ttu-id="6ab64-114">Os argumentos fornecidos na linha de comando são passados para o `main` função na matriz de cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="6ab64-114">The arguments provided on the command line are passed to the `main` function in the array of strings.</span></span> <span data-ttu-id="6ab64-115">O primeiro elemento da matriz é o primeiro argumento; o nome do arquivo executável não está incluído na matriz, pois ele está em algumas outras linguagens.</span><span class="sxs-lookup"><span data-stu-id="6ab64-115">The first element of the array is the first argument; the name of the executable file is not included in the array, as it is in some other languages.</span></span> <span data-ttu-id="6ab64-116">O valor de retorno é usado como o código de saída para o processo.</span><span class="sxs-lookup"><span data-stu-id="6ab64-116">The return value is used as the exit code for the process.</span></span> <span data-ttu-id="6ab64-117">Zero geralmente indica sucesso. valores diferentes de zero indicam um erro.</span><span class="sxs-lookup"><span data-stu-id="6ab64-117">Zero usually indicates success; nonzero values indicate an error.</span></span> <span data-ttu-id="6ab64-118">Não há nenhum convenção do significado específico de códigos de retorno diferente de zero; os significados dos códigos de retorno são específicas do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="6ab64-118">There is no convention for the specific meaning of nonzero return codes; the meanings of the return codes are application-specific.</span></span>

<span data-ttu-id="6ab64-119">O exemplo a seguir ilustra um simples `main` função.</span><span class="sxs-lookup"><span data-stu-id="6ab64-119">The following example illustrates a simple `main` function.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/entry-point/snippet501.fs)]

<span data-ttu-id="6ab64-120">Quando esse código é executado com a linha de comando `EntryPoint.exe 1 2 3`, a saída é da seguinte maneira.</span><span class="sxs-lookup"><span data-stu-id="6ab64-120">When this code is executed with the command line `EntryPoint.exe 1 2 3`, the output is as follows.</span></span>

```console
Arguments passed to function : [|"1"; "2"; "3"|]
```

## <a name="implicit-entry-point"></a><span data-ttu-id="6ab64-121">Ponto de entrada implícito</span><span class="sxs-lookup"><span data-stu-id="6ab64-121">Implicit Entry Point</span></span>
<span data-ttu-id="6ab64-122">Quando um programa não tem **EntryPoint** atributo que explicitamente indica o ponto de entrada, as associações de nível superior no último arquivo a ser compilado são usados como o ponto de entrada.</span><span class="sxs-lookup"><span data-stu-id="6ab64-122">When a program has no **EntryPoint** attribute that explicitly indicates the entry point, the top level bindings in the last file to be compiled are used as the entry point.</span></span>


## <a name="see-also"></a><span data-ttu-id="6ab64-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6ab64-123">See Also</span></span>
[<span data-ttu-id="6ab64-124">Funções</span><span class="sxs-lookup"><span data-stu-id="6ab64-124">Functions</span></span>](index.md)

[<span data-ttu-id="6ab64-125">Associações let</span><span class="sxs-lookup"><span data-stu-id="6ab64-125">let Bindings</span></span>](let-bindings.md)
