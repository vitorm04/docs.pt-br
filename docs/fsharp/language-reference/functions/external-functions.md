---
title: Funções externas
description: Saiba mais sobre F# o suporte de idioma para chamar funções em código nativo.
ms.date: 05/16/2016
ms.openlocfilehash: 3c8edaba25e07b6ca2c44a58c4b55dc98a13b4fc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968727"
---
# <a name="external-functions"></a><span data-ttu-id="6eb17-103">Funções externas</span><span class="sxs-lookup"><span data-stu-id="6eb17-103">External Functions</span></span>

<span data-ttu-id="6eb17-104">Este tópico descreve F# o suporte a idiomas para chamar funções em código nativo.</span><span class="sxs-lookup"><span data-stu-id="6eb17-104">This topic describes F# language support for calling functions in native code.</span></span>

## <a name="syntax"></a><span data-ttu-id="6eb17-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6eb17-105">Syntax</span></span>

```fsharp
[<DllImport( arguments )>]
extern declaration
```

## <a name="remarks"></a><span data-ttu-id="6eb17-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="6eb17-106">Remarks</span></span>

<span data-ttu-id="6eb17-107">Na sintaxe anterior, *arguments* representa argumentos que são fornecidos para o `System.Runtime.InteropServices.DllImportAttribute` atributo.</span><span class="sxs-lookup"><span data-stu-id="6eb17-107">In the previous syntax, *arguments* represents arguments that are supplied to the `System.Runtime.InteropServices.DllImportAttribute` attribute.</span></span> <span data-ttu-id="6eb17-108">O primeiro argumento é uma cadeia de caracteres que representa o nome da DLL que contém essa função, sem a extensão. dll.</span><span class="sxs-lookup"><span data-stu-id="6eb17-108">The first argument is a string that represents the name of the DLL that contains this function, without the .dll extension.</span></span> <span data-ttu-id="6eb17-109">Argumentos adicionais podem ser fornecidos para qualquer uma das propriedades públicas da `System.Runtime.InteropServices.DllImportAttribute` classe, como a Convenção de chamada.</span><span class="sxs-lookup"><span data-stu-id="6eb17-109">Additional arguments can be supplied for any of the public properties of the `System.Runtime.InteropServices.DllImportAttribute` class, such as the calling convention.</span></span>

<span data-ttu-id="6eb17-110">Suponha que você tenha uma C++ DLL nativa que contenha a seguinte função exportada.</span><span class="sxs-lookup"><span data-stu-id="6eb17-110">Assume you have a native C++ DLL that contains the following exported function.</span></span>

```cpp
#include <stdio.h>
extern "C" void __declspec(dllexport) HelloWorld()
{
    printf("Hello world, invoked by F#!\n");
}
```

<span data-ttu-id="6eb17-111">Você pode chamar essa função F# usando o código a seguir.</span><span class="sxs-lookup"><span data-stu-id="6eb17-111">You can call this function from F# by using the following code.</span></span>

```fsharp
open System.Runtime.InteropServices

module InteropWithNative =
    [<DllImport(@"C:\bin\nativedll", CallingConvention = CallingConvention.Cdecl)>]
    extern void HelloWorld()

InteropWithNative.HelloWorld()
```

<span data-ttu-id="6eb17-112">A interoperabilidade com código nativo é conhecida como invocação de *plataforma* e é um recurso do CLR.</span><span class="sxs-lookup"><span data-stu-id="6eb17-112">Interoperability with native code is referred to as *platform invoke* and is a feature of the CLR.</span></span> <span data-ttu-id="6eb17-113">Para obter mais informações, consulte [interoperação com código não gerenciado](../../../framework/interop/index.md).</span><span class="sxs-lookup"><span data-stu-id="6eb17-113">For more information, see [Interoperating with Unmanaged Code](../../../framework/interop/index.md).</span></span> <span data-ttu-id="6eb17-114">As informações contidas nessa seção são aplicáveis F#ao.</span><span class="sxs-lookup"><span data-stu-id="6eb17-114">The information in that section is applicable to F#.</span></span>

## <a name="see-also"></a><span data-ttu-id="6eb17-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6eb17-115">See also</span></span>

- [<span data-ttu-id="6eb17-116">Funções</span><span class="sxs-lookup"><span data-stu-id="6eb17-116">Functions</span></span>](index.md)
