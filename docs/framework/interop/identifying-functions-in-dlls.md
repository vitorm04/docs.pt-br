---
title: Identificando funções em DLLs
description: Identifique as funções nas DLLs. A identidade de uma função de DLL consiste em um nome de função ou ordinal, e o nome do arquivo DLL no qual a implementação pode ser encontrada.
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
ms.openlocfilehash: 054d1351a9ee6adab17117c9f423aa26d0d9ed59
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622725"
---
# <a name="identifying-functions-in-dlls"></a><span data-ttu-id="6494a-104">Identificando funções em DLLs</span><span class="sxs-lookup"><span data-stu-id="6494a-104">Identifying Functions in DLLs</span></span>
<span data-ttu-id="6494a-105">A identidade de uma função de DLL consiste dos seguintes elementos:</span><span class="sxs-lookup"><span data-stu-id="6494a-105">The identity of a DLL function consists of the following elements:</span></span>  
  
- <span data-ttu-id="6494a-106">Ordinal ou nome da função</span><span class="sxs-lookup"><span data-stu-id="6494a-106">Function name or ordinal</span></span>  
  
- <span data-ttu-id="6494a-107">Nome do arquivo DLL em que a implementação pode ser encontrada</span><span class="sxs-lookup"><span data-stu-id="6494a-107">Name of the DLL file in which the implementation can be found</span></span>  
  
 <span data-ttu-id="6494a-108">Por exemplo, especificar a função **MessageBox** na User32.dll identifica a função (**MessageBox**) e sua localização (User32.dll, User32 ou user32).</span><span class="sxs-lookup"><span data-stu-id="6494a-108">For example, specifying the **MessageBox** function in the User32.dll identifies the function (**MessageBox**) and its location (User32.dll, User32, or user32).</span></span> <span data-ttu-id="6494a-109">A interface de programação de aplicativo (API do Windows) do Microsoft Windows pode conter duas versões de cada função que manipula caracteres e cadeias de caracteres: uma versão ANSI do caractere de 1 byte e uma versão Unicode do caractere de 2 bytes.</span><span class="sxs-lookup"><span data-stu-id="6494a-109">The Microsoft Windows application programming interface (Windows API) can contain two versions of each function that handles characters and strings: a 1-byte character ANSI version and a 2-byte character Unicode version.</span></span> <span data-ttu-id="6494a-110">Quando não especificado, o conjunto de caracteres, representado pelo campo <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet>, torna-se ANSI por padrão.</span><span class="sxs-lookup"><span data-stu-id="6494a-110">When unspecified, the character set, represented by the <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet> field, defaults to ANSI.</span></span> <span data-ttu-id="6494a-111">Algumas funções podem ter mais de duas versões.</span><span class="sxs-lookup"><span data-stu-id="6494a-111">Some functions can have more than two versions.</span></span>  
  
 <span data-ttu-id="6494a-112">**MessageBoxA** é o ponto de entrada ANSI para a função **MessageBox**; **MessageBoxW** é a versão Unicode.</span><span class="sxs-lookup"><span data-stu-id="6494a-112">**MessageBoxA** is the ANSI entry point for the **MessageBox** function; **MessageBoxW** is the Unicode version.</span></span> <span data-ttu-id="6494a-113">Você pode listar os nomes de função para uma DLL específica, como user32.dll, por meio da execução de uma variedade de ferramentas de linha de comando.</span><span class="sxs-lookup"><span data-stu-id="6494a-113">You can list function names for a specific DLL, such as user32.dll, by running a variety of command-line tools.</span></span> <span data-ttu-id="6494a-114">Por exemplo, você pode usar `dumpbin /exports user32.dll` ou `link /dump /exports user32.dll` para obter nomes de função.</span><span class="sxs-lookup"><span data-stu-id="6494a-114">For example, you can use `dumpbin /exports user32.dll` or `link /dump /exports user32.dll` to obtain function names.</span></span>  
  
 <span data-ttu-id="6494a-115">Você pode renomear uma função não gerenciada para o que você quiser em seu código desde que você mapeie o novo nome para o ponto de entrada original na DLL.</span><span class="sxs-lookup"><span data-stu-id="6494a-115">You can rename an unmanaged function to whatever you like within your code as long as you map the new name to the original entry point in the DLL.</span></span> <span data-ttu-id="6494a-116">Para obter instruções sobre como renomear uma função de DLL não gerenciada no código-fonte gerenciado, consulte [Especificando um ponto de entrada](specifying-an-entry-point.md).</span><span class="sxs-lookup"><span data-stu-id="6494a-116">For instructions on renaming an unmanaged DLL function in managed source code, see the [Specifying an Entry Point](specifying-an-entry-point.md).</span></span>  
  
 <span data-ttu-id="6494a-117">A invocação de plataforma permite que você controle uma parte significativa do sistema operacional chamando funções na API do Windows e outras DLLs.</span><span class="sxs-lookup"><span data-stu-id="6494a-117">Platform invoke enables you to control a significant portion of the operating system by calling functions in the Windows API and other DLLs.</span></span> <span data-ttu-id="6494a-118">Além da API do Windows, há várias outras APIs e DLLs disponíveis para você por meio da invocação de plataforma.</span><span class="sxs-lookup"><span data-stu-id="6494a-118">In addition to the Windows API, there are numerous other APIs and DLLs available to you through platform invoke.</span></span>  
  
 <span data-ttu-id="6494a-119">A tabela a seguir descreve várias DLLs comumente usadas na API do Windows.</span><span class="sxs-lookup"><span data-stu-id="6494a-119">The following table describes several commonly used DLLs in the Windows API.</span></span>  
  
|<span data-ttu-id="6494a-120">DLL</span><span class="sxs-lookup"><span data-stu-id="6494a-120">DLL</span></span>|<span data-ttu-id="6494a-121">Descrição dos conteúdos</span><span class="sxs-lookup"><span data-stu-id="6494a-121">Description of Contents</span></span>|  
|---------|-----------------------------|  
|<span data-ttu-id="6494a-122">GDI32.dll</span><span class="sxs-lookup"><span data-stu-id="6494a-122">GDI32.dll</span></span>|<span data-ttu-id="6494a-123">As funções de GDI (Graphics Device Interface) para o dispositivo de saída, tais como aquelas para desenho e para gerenciamento de fontes.</span><span class="sxs-lookup"><span data-stu-id="6494a-123">Graphics Device Interface (GDI) functions for device output, such as those for drawing and font management.</span></span>|  
|<span data-ttu-id="6494a-124">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="6494a-124">Kernel32.dll</span></span>|<span data-ttu-id="6494a-125">Funções do sistema de operacional de baixo nível para gerenciamento de memória e manipulação de recursos.</span><span class="sxs-lookup"><span data-stu-id="6494a-125">Low-level operating system functions for memory management and resource handling.</span></span>|  
|<span data-ttu-id="6494a-126">User32.dll</span><span class="sxs-lookup"><span data-stu-id="6494a-126">User32.dll</span></span>|<span data-ttu-id="6494a-127">Funções de gerenciamento do Windows para a manipulação de mensagens, temporizadores, menus e comunicações.</span><span class="sxs-lookup"><span data-stu-id="6494a-127">Windows management functions for message handling, timers, menus, and communications.</span></span>|  
  
 <span data-ttu-id="6494a-128">Para obter a documentação completa sobre a API do Windows, confira o SDK da Plataforma.</span><span class="sxs-lookup"><span data-stu-id="6494a-128">For complete documentation on the Windows API, see the Platform SDK.</span></span> <span data-ttu-id="6494a-129">Para obter exemplos que demonstram como construir declarações baseadas no .NET a serem usadas com a invocação de plataforma, consulte [Realizando marshaling de dados com a invocação de plataforma](marshaling-data-with-platform-invoke.md).</span><span class="sxs-lookup"><span data-stu-id="6494a-129">For examples that demonstrate how to construct .NET-based declarations to be used with platform invoke, see [Marshaling Data with Platform Invoke](marshaling-data-with-platform-invoke.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6494a-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6494a-130">See also</span></span>

- [<span data-ttu-id="6494a-131">Consumindo funções de DLL não gerenciadas</span><span class="sxs-lookup"><span data-stu-id="6494a-131">Consuming Unmanaged DLL Functions</span></span>](consuming-unmanaged-dll-functions.md)
- [<span data-ttu-id="6494a-132">Especificando um ponto de entrada</span><span class="sxs-lookup"><span data-stu-id="6494a-132">Specifying an Entry Point</span></span>](specifying-an-entry-point.md)
- [<span data-ttu-id="6494a-133">Criando uma classe para conter funções de DLL</span><span class="sxs-lookup"><span data-stu-id="6494a-133">Creating a Class to Hold DLL Functions</span></span>](creating-a-class-to-hold-dll-functions.md)
- [<span data-ttu-id="6494a-134">Criando protótipos em código gerenciado</span><span class="sxs-lookup"><span data-stu-id="6494a-134">Creating Prototypes in Managed Code</span></span>](creating-prototypes-in-managed-code.md)
- [<span data-ttu-id="6494a-135">Chamando uma função de DLL</span><span class="sxs-lookup"><span data-stu-id="6494a-135">Calling a DLL Function</span></span>](calling-a-dll-function.md)
