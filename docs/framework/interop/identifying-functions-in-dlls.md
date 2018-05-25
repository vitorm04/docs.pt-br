---
title: Identificando funções em DLLs
ms.date: 03/30/2017
helpviewer_keywords:
- platform invoke, identifying functions
- COM interop, DLL functions
- unmanaged functions
- COM interop, platform invoke
- interoperation with unmanaged code, DLL functions
- interoperation with unmanaged code, platform invoke
- identifying DLL functions
- DLL functions
ms.assetid: 3e3f6780-6d90-4413-bad7-ba641220364d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bc160678817266dc649f60dc3f2cc77044c05691
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="identifying-functions-in-dlls"></a><span data-ttu-id="271b1-102">Identificando funções em DLLs</span><span class="sxs-lookup"><span data-stu-id="271b1-102">Identifying Functions in DLLs</span></span>
<span data-ttu-id="271b1-103">A identidade de uma função de DLL consiste dos seguintes elementos:</span><span class="sxs-lookup"><span data-stu-id="271b1-103">The identity of a DLL function consists of the following elements:</span></span>  
  
-   <span data-ttu-id="271b1-104">Ordinal ou nome da função</span><span class="sxs-lookup"><span data-stu-id="271b1-104">Function name or ordinal</span></span>  
  
-   <span data-ttu-id="271b1-105">Nome do arquivo DLL em que a implementação pode ser encontrada</span><span class="sxs-lookup"><span data-stu-id="271b1-105">Name of the DLL file in which the implementation can be found</span></span>  
  
 <span data-ttu-id="271b1-106">Por exemplo, especificar a função **MessageBox** na User32.dll identifica a função (**MessageBox**) e sua localização (User32.dll, User32 ou user32).</span><span class="sxs-lookup"><span data-stu-id="271b1-106">For example, specifying the **MessageBox** function in the User32.dll identifies the function (**MessageBox**) and its location (User32.dll, User32, or user32).</span></span> <span data-ttu-id="271b1-107">A interface de programação de aplicativo (API do Win32) do Microsoft Windows pode conter duas versões de cada função que manipula caracteres e cadeias de caracteres: uma versão ANSI do caractere de 1 byte e uma versão Unicode do caractere de 2 bytes.</span><span class="sxs-lookup"><span data-stu-id="271b1-107">The Microsoft Windows application programming interface (Win32 API) can contain two versions of each function that handles characters and strings: a 1-byte character ANSI version and a 2-byte character Unicode version.</span></span> <span data-ttu-id="271b1-108">Quando não especificado, o conjunto de caracteres, representado pelo campo <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet>, torna-se ANSI por padrão.</span><span class="sxs-lookup"><span data-stu-id="271b1-108">When unspecified, the character set, represented by the <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet> field, defaults to ANSI.</span></span> <span data-ttu-id="271b1-109">Algumas funções podem ter mais de duas versões.</span><span class="sxs-lookup"><span data-stu-id="271b1-109">Some functions can have more than two versions.</span></span>  
  
 <span data-ttu-id="271b1-110">**MessageBoxA** é o ponto de entrada ANSI para a função **MessageBox**; **MessageBoxW** é a versão Unicode.</span><span class="sxs-lookup"><span data-stu-id="271b1-110">**MessageBoxA** is the ANSI entry point for the **MessageBox** function; **MessageBoxW** is the Unicode version.</span></span> <span data-ttu-id="271b1-111">Você pode listar os nomes de função para uma DLL específica, como user32.dll, por meio da execução de uma variedade de ferramentas de linha de comando.</span><span class="sxs-lookup"><span data-stu-id="271b1-111">You can list function names for a specific DLL, such as user32.dll, by running a variety of command-line tools.</span></span> <span data-ttu-id="271b1-112">Por exemplo, você pode usar `dumpbin /exports user32.dll` ou `link /dump /exports user32.dll` para obter nomes de função.</span><span class="sxs-lookup"><span data-stu-id="271b1-112">For example, you can use `dumpbin /exports user32.dll` or `link /dump /exports user32.dll` to obtain function names.</span></span>  
  
 <span data-ttu-id="271b1-113">Você pode renomear uma função não gerenciada para o que você quiser em seu código desde que você mapeie o novo nome para o ponto de entrada original na DLL.</span><span class="sxs-lookup"><span data-stu-id="271b1-113">You can rename an unmanaged function to whatever you like within your code as long as you map the new name to the original entry point in the DLL.</span></span> <span data-ttu-id="271b1-114">Para obter instruções sobre como renomear uma função de DLL não gerenciada no código-fonte gerenciado, consulte [Especificando um ponto de entrada](../../../docs/framework/interop/specifying-an-entry-point.md).</span><span class="sxs-lookup"><span data-stu-id="271b1-114">For instructions on renaming an unmanaged DLL function in managed source code, see the [Specifying an Entry Point](../../../docs/framework/interop/specifying-an-entry-point.md).</span></span>  
  
 <span data-ttu-id="271b1-115">A invocação de plataforma permite que você controle uma parte significativa do sistema operacional chamando funções na API do Win32 e outras DLLs.</span><span class="sxs-lookup"><span data-stu-id="271b1-115">Platform invoke enables you to control a significant portion of the operating system by calling functions in the Win32 API and other DLLs.</span></span> <span data-ttu-id="271b1-116">Além de API do Win32, há várias outras APIs e DLLs disponíveis para você por meio da invocação de plataforma.</span><span class="sxs-lookup"><span data-stu-id="271b1-116">In addition to the Win32 API, there are numerous other APIs and DLLs available to you through platform invoke.</span></span>  
  
 <span data-ttu-id="271b1-117">A tabela a seguir descreve várias DLLs usadas na API do Win32.</span><span class="sxs-lookup"><span data-stu-id="271b1-117">The following table describes several commonly used DLLs in the Win32 API.</span></span>  
  
|<span data-ttu-id="271b1-118">DLL</span><span class="sxs-lookup"><span data-stu-id="271b1-118">DLL</span></span>|<span data-ttu-id="271b1-119">Descrição dos conteúdos</span><span class="sxs-lookup"><span data-stu-id="271b1-119">Description of Contents</span></span>|  
|---------|-----------------------------|  
|<span data-ttu-id="271b1-120">GDI32.dll</span><span class="sxs-lookup"><span data-stu-id="271b1-120">GDI32.dll</span></span>|<span data-ttu-id="271b1-121">As funções de GDI (Graphics Device Interface) para o dispositivo de saída, tais como aquelas para desenho e para gerenciamento de fontes.</span><span class="sxs-lookup"><span data-stu-id="271b1-121">Graphics Device Interface (GDI) functions for device output, such as those for drawing and font management.</span></span>|  
|<span data-ttu-id="271b1-122">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="271b1-122">Kernel32.dll</span></span>|<span data-ttu-id="271b1-123">Funções do sistema de operacional de baixo nível para gerenciamento de memória e manipulação de recursos.</span><span class="sxs-lookup"><span data-stu-id="271b1-123">Low-level operating system functions for memory management and resource handling.</span></span>|  
|<span data-ttu-id="271b1-124">User32.dll</span><span class="sxs-lookup"><span data-stu-id="271b1-124">User32.dll</span></span>|<span data-ttu-id="271b1-125">Funções de gerenciamento do Windows para a manipulação de mensagens, temporizadores, menus e comunicações.</span><span class="sxs-lookup"><span data-stu-id="271b1-125">Windows management functions for message handling, timers, menus, and communications.</span></span>|  
  
 <span data-ttu-id="271b1-126">Para a documentação completa sobre a API do Win32, consulte o SDK de plataforma.</span><span class="sxs-lookup"><span data-stu-id="271b1-126">For complete documentation on the Win32 API, see the Platform SDK.</span></span> <span data-ttu-id="271b1-127">Para obter exemplos que demonstram como construir declarações baseadas no .NET a serem usadas com a invocação de plataforma, consulte [Realizando marshaling de dados com a invocação de plataforma](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md).</span><span class="sxs-lookup"><span data-stu-id="271b1-127">For examples that demonstrate how to construct .NET-based declarations to be used with platform invoke, see [Marshaling Data with Platform Invoke](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="271b1-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="271b1-128">See Also</span></span>  
 [<span data-ttu-id="271b1-129">Consumindo funções de DLL não gerenciadas</span><span class="sxs-lookup"><span data-stu-id="271b1-129">Consuming Unmanaged DLL Functions</span></span>](../../../docs/framework/interop/consuming-unmanaged-dll-functions.md)  
 [<span data-ttu-id="271b1-130">Especificando um ponto de entrada</span><span class="sxs-lookup"><span data-stu-id="271b1-130">Specifying an Entry Point</span></span>](../../../docs/framework/interop/specifying-an-entry-point.md)  
 [<span data-ttu-id="271b1-131">Criando uma classe para conter funções de DLL</span><span class="sxs-lookup"><span data-stu-id="271b1-131">Creating a Class to Hold DLL Functions</span></span>](../../../docs/framework/interop/creating-a-class-to-hold-dll-functions.md)  
 [<span data-ttu-id="271b1-132">Criando protótipos em código gerenciado</span><span class="sxs-lookup"><span data-stu-id="271b1-132">Creating Prototypes in Managed Code</span></span>](../../../docs/framework/interop/creating-prototypes-in-managed-code.md)  
 [<span data-ttu-id="271b1-133">Chamando uma função de DLL</span><span class="sxs-lookup"><span data-stu-id="271b1-133">Calling a DLL Function</span></span>](../../../docs/framework/interop/calling-a-dll-function.md)
