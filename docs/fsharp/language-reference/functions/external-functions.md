---
title: Funções externas (F#)
description: 'Saiba mais sobre o suporte de linguagem F # para chamar funções em código nativo.'
ms.date: 05/16/2016
ms.openlocfilehash: 398697c5e0deab7f8d81ec5198ab1918bd865e13
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33564476"
---
# <a name="external-functions"></a><span data-ttu-id="2a601-103">Funções externas</span><span class="sxs-lookup"><span data-stu-id="2a601-103">External Functions</span></span>

<span data-ttu-id="2a601-104">Este tópico descreve o suporte da linguagem F # para chamar funções em código nativo.</span><span class="sxs-lookup"><span data-stu-id="2a601-104">This topic describes F# language support for calling functions in native code.</span></span>

## <a name="syntax"></a><span data-ttu-id="2a601-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2a601-105">Syntax</span></span>

```fsharp
[<DllImport( arguments )>]
extern declaration
```

## <a name="remarks"></a><span data-ttu-id="2a601-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="2a601-106">Remarks</span></span>

<span data-ttu-id="2a601-107">Na sintaxe anterior, *argumentos* representa os argumentos fornecidos para o `System.Runtime.InteropServices.DllImportAttribute` atributo.</span><span class="sxs-lookup"><span data-stu-id="2a601-107">In the previous syntax, *arguments* represents arguments that are supplied to the `System.Runtime.InteropServices.DllImportAttribute` attribute.</span></span> <span data-ttu-id="2a601-108">O primeiro argumento é uma cadeia de caracteres que representa o nome da DLL que contém essa função, sem a extensão. dll.</span><span class="sxs-lookup"><span data-stu-id="2a601-108">The first argument is a string that represents the name of the DLL that contains this function, without the .dll extension.</span></span> <span data-ttu-id="2a601-109">Argumentos adicionais podem ser fornecidos para qualquer uma das propriedades públicas do `System.Runtime.InteropServices.DllImportAttribute` classe, como a convenção de chamada.</span><span class="sxs-lookup"><span data-stu-id="2a601-109">Additional arguments can be supplied for any of the public properties of the `System.Runtime.InteropServices.DllImportAttribute` class, such as the calling convention.</span></span>

<span data-ttu-id="2a601-110">Suponha que você tem um DLL do C++ que contém a seguinte função exportada nativo.</span><span class="sxs-lookup"><span data-stu-id="2a601-110">Assume you have a native C++ DLL that contains the following exported function.</span></span>

```cpp
#include <stdio.h>
extern "C" void __declspec(dllexport) HelloWorld()
{
    printf("Hello world, invoked by F#!\n");
}
```

<span data-ttu-id="2a601-111">Você pode chamar essa função do F # usando o código a seguir.</span><span class="sxs-lookup"><span data-stu-id="2a601-111">You can call this function from F# by using the following code.</span></span>

```fsharp
open System.Runtime.InteropServices

module InteropWithNative =
    [<DllImport(@"C:\bin\nativedll", CallingConvention = CallingConvention.Cdecl)>]
    extern void HelloWorld()

InteropWithNative.HelloWorld()
```

<span data-ttu-id="2a601-112">Interoperabilidade com código nativo é conhecida como *invocação de plataforma* e é um recurso do CLR.</span><span class="sxs-lookup"><span data-stu-id="2a601-112">Interoperability with native code is referred to as *platform invoke* and is a feature of the CLR.</span></span> <span data-ttu-id="2a601-113">Para obter mais informações, consulte [interoperação com código não gerenciado](../../../../docs/framework/interop/index.md).</span><span class="sxs-lookup"><span data-stu-id="2a601-113">For more information, see [Interoperating with Unmanaged Code](../../../../docs/framework/interop/index.md).</span></span> <span data-ttu-id="2a601-114">As informações nesta seção são aplicáveis a F #.</span><span class="sxs-lookup"><span data-stu-id="2a601-114">The information in that section is applicable to F#.</span></span>


## <a name="see-also"></a><span data-ttu-id="2a601-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2a601-115">See Also</span></span>

[<span data-ttu-id="2a601-116">Funções</span><span class="sxs-lookup"><span data-stu-id="2a601-116">Functions</span></span>](index.md)
