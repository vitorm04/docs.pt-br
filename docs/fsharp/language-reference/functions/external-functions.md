---
title: Funções externas
description: Saiba mais sobre o F# suporte de linguagem para chamar funções em código nativo.
ms.date: 05/16/2016
ms.openlocfilehash: 86ea78844fb812361233f8360c377465d83be203
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61934622"
---
# <a name="external-functions"></a><span data-ttu-id="9fa0a-103">Funções externas</span><span class="sxs-lookup"><span data-stu-id="9fa0a-103">External Functions</span></span>

<span data-ttu-id="9fa0a-104">Este tópico descreve F# suporte de linguagem para chamar funções em código nativo.</span><span class="sxs-lookup"><span data-stu-id="9fa0a-104">This topic describes F# language support for calling functions in native code.</span></span>

## <a name="syntax"></a><span data-ttu-id="9fa0a-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9fa0a-105">Syntax</span></span>

```fsharp
[<DllImport( arguments )>]
extern declaration
```

## <a name="remarks"></a><span data-ttu-id="9fa0a-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="9fa0a-106">Remarks</span></span>

<span data-ttu-id="9fa0a-107">Na sintaxe anterior, *argumentos* representa os argumentos que são fornecidos para o `System.Runtime.InteropServices.DllImportAttribute` atributo.</span><span class="sxs-lookup"><span data-stu-id="9fa0a-107">In the previous syntax, *arguments* represents arguments that are supplied to the `System.Runtime.InteropServices.DllImportAttribute` attribute.</span></span> <span data-ttu-id="9fa0a-108">O primeiro argumento é uma cadeia de caracteres que representa o nome da DLL que contém essa função, sem a extensão. dll.</span><span class="sxs-lookup"><span data-stu-id="9fa0a-108">The first argument is a string that represents the name of the DLL that contains this function, without the .dll extension.</span></span> <span data-ttu-id="9fa0a-109">Argumentos adicionais podem ser fornecidos para qualquer uma das propriedades públicas do `System.Runtime.InteropServices.DllImportAttribute` classe, como a convenção de chamada.</span><span class="sxs-lookup"><span data-stu-id="9fa0a-109">Additional arguments can be supplied for any of the public properties of the `System.Runtime.InteropServices.DllImportAttribute` class, such as the calling convention.</span></span>

<span data-ttu-id="9fa0a-110">Suponha que você tem um C++ DLL que contém a seguinte função exportada nativo.</span><span class="sxs-lookup"><span data-stu-id="9fa0a-110">Assume you have a native C++ DLL that contains the following exported function.</span></span>

```cpp
#include <stdio.h>
extern "C" void __declspec(dllexport) HelloWorld()
{
    printf("Hello world, invoked by F#!\n");
}
```

<span data-ttu-id="9fa0a-111">Você pode chamar essa função do F# usando o código a seguir.</span><span class="sxs-lookup"><span data-stu-id="9fa0a-111">You can call this function from F# by using the following code.</span></span>

```fsharp
open System.Runtime.InteropServices

module InteropWithNative =
    [<DllImport(@"C:\bin\nativedll", CallingConvention = CallingConvention.Cdecl)>]
    extern void HelloWorld()

InteropWithNative.HelloWorld()
```

<span data-ttu-id="9fa0a-112">Interoperabilidade com código nativo é conhecida como *de invocação de plataforma* e é um recurso do CLR.</span><span class="sxs-lookup"><span data-stu-id="9fa0a-112">Interoperability with native code is referred to as *platform invoke* and is a feature of the CLR.</span></span> <span data-ttu-id="9fa0a-113">Para obter mais informações, consulte [interoperação com código não gerenciado](../../../../docs/framework/interop/index.md).</span><span class="sxs-lookup"><span data-stu-id="9fa0a-113">For more information, see [Interoperating with Unmanaged Code](../../../../docs/framework/interop/index.md).</span></span> <span data-ttu-id="9fa0a-114">As informações nesta seção são aplicáveis a F#.</span><span class="sxs-lookup"><span data-stu-id="9fa0a-114">The information in that section is applicable to F#.</span></span>

## <a name="see-also"></a><span data-ttu-id="9fa0a-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9fa0a-115">See also</span></span>

- [<span data-ttu-id="9fa0a-116">Funções</span><span class="sxs-lookup"><span data-stu-id="9fa0a-116">Functions</span></span>](index.md)