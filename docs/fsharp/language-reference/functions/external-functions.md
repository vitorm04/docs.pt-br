---
title: "Funções externas (F#)"
description: "Saiba mais sobre o suporte de linguagem F # para chamar funções em código nativo."
keywords: "visual f#, f#, programação funcional"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: c26b6124-ceaa-471c-9dc9-861b4dfa332a
ms.openlocfilehash: 4f525b2b750c2ce42230c61aa0e72f957739b206
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="external-functions"></a><span data-ttu-id="32a02-104">Funções externas</span><span class="sxs-lookup"><span data-stu-id="32a02-104">External Functions</span></span>

<span data-ttu-id="32a02-105">Este tópico descreve o suporte da linguagem F # para chamar funções em código nativo.</span><span class="sxs-lookup"><span data-stu-id="32a02-105">This topic describes F# language support for calling functions in native code.</span></span>

## <a name="syntax"></a><span data-ttu-id="32a02-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="32a02-106">Syntax</span></span>

```fsharp
[<DllImport( arguments )>]
extern declaration
```

## <a name="remarks"></a><span data-ttu-id="32a02-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="32a02-107">Remarks</span></span>

<span data-ttu-id="32a02-108">Na sintaxe anterior, *argumentos* representa os argumentos fornecidos para o `System.Runtime.InteropServices.DllImportAttribute` atributo.</span><span class="sxs-lookup"><span data-stu-id="32a02-108">In the previous syntax, *arguments* represents arguments that are supplied to the `System.Runtime.InteropServices.DllImportAttribute` attribute.</span></span> <span data-ttu-id="32a02-109">O primeiro argumento é uma cadeia de caracteres que representa o nome da DLL que contém essa função, sem a extensão. dll.</span><span class="sxs-lookup"><span data-stu-id="32a02-109">The first argument is a string that represents the name of the DLL that contains this function, without the .dll extension.</span></span> <span data-ttu-id="32a02-110">Argumentos adicionais podem ser fornecidos para qualquer uma das propriedades públicas do `System.Runtime.InteropServices.DllImportAttribute` classe, como a convenção de chamada.</span><span class="sxs-lookup"><span data-stu-id="32a02-110">Additional arguments can be supplied for any of the public properties of the `System.Runtime.InteropServices.DllImportAttribute` class, such as the calling convention.</span></span>

<span data-ttu-id="32a02-111">Suponha que você tem um DLL do C++ que contém a seguinte função exportada nativo.</span><span class="sxs-lookup"><span data-stu-id="32a02-111">Assume you have a native C++ DLL that contains the following exported function.</span></span>

```cpp
#include <stdio.h>
extern "C" void __declspec(dllexport) HelloWorld()
{
    printf("Hello world, invoked by F#!\n");
}
```

<span data-ttu-id="32a02-112">Você pode chamar essa função do F # usando o código a seguir.</span><span class="sxs-lookup"><span data-stu-id="32a02-112">You can call this function from F# by using the following code.</span></span>

```fsharp
open System.Runtime.InteropServices

module InteropWithNative =
    [<DllImport(@"C:\bin\nativedll", CallingConvention = CallingConvention.Cdecl)>]
    extern void HelloWorld()

InteropWithNative.HelloWorld()
```

<span data-ttu-id="32a02-113">Interoperabilidade com código nativo é conhecida como *invocação de plataforma* e é um recurso do CLR.</span><span class="sxs-lookup"><span data-stu-id="32a02-113">Interoperability with native code is referred to as *platform invoke* and is a feature of the CLR.</span></span> <span data-ttu-id="32a02-114">Para obter mais informações, consulte [interoperação com código não gerenciado](https://msdn.microsoft.com/library/sd10k43k.aspx).</span><span class="sxs-lookup"><span data-stu-id="32a02-114">For more information, see [Interoperating with Unmanaged Code](https://msdn.microsoft.com/library/sd10k43k.aspx).</span></span> <span data-ttu-id="32a02-115">As informações nesta seção são aplicáveis a F #.</span><span class="sxs-lookup"><span data-stu-id="32a02-115">The information in that section is applicable to F#.</span></span>


## <a name="see-also"></a><span data-ttu-id="32a02-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="32a02-116">See Also</span></span>

[<span data-ttu-id="32a02-117">Funções</span><span class="sxs-lookup"><span data-stu-id="32a02-117">Functions</span></span>](index.md)
