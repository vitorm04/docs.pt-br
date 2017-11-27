---
title: "Consumindo funções de DLL não gerenciadas"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- unmanaged functions, calling
- COM interop, DLL functions
- unmanaged functions
- COM interop, platform invoke
- platform invoke, about platform invoke
- DLL functions, consuming unmanaged
- interoperation with unmanaged code, DLL functions
- interoperation with unmanaged code, platform invoke
- platform invoke
- DLL functions
ms.assetid: eca7606e-ebfb-4f47-b8d9-289903fdc045
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ec93728566d6aa16d4b9b15b171d79831cc0dbeb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="consuming-unmanaged-dll-functions"></a><span data-ttu-id="b3550-102">Consumindo funções de DLL não gerenciadas</span><span class="sxs-lookup"><span data-stu-id="b3550-102">Consuming Unmanaged DLL Functions</span></span>
<span data-ttu-id="b3550-103">A invocação de plataforma é um serviço que permite que um código gerenciado chame funções não gerenciadas implementadas em DLLs (bibliotecas de vínculo dinâmico), como aquelas na API do Win32.</span><span class="sxs-lookup"><span data-stu-id="b3550-103">Platform invoke is a service that enables managed code to call unmanaged functions implemented in dynamic link libraries (DLLs), such as those in the Win32 API.</span></span> <span data-ttu-id="b3550-104">Ela localiza e invoca uma função exportada e realiza marshaling dos argumentos (inteiros, cadeias de caracteres, matrizes, estruturas e assim por diante) além do limite de interoperação, conforme necessário.</span><span class="sxs-lookup"><span data-stu-id="b3550-104">It locates and invokes an exported function and marshals its arguments (integers, strings, arrays, structures, and so on) across the interoperation boundary as needed.</span></span> <span data-ttu-id="b3550-105">Para obter mais informações sobre esse serviço, consulte [Visão aprofundada da invocação de plataforma](http://msdn.microsoft.com/en-us/ba9dd55b-2eaa-45cd-8afd-75cb8d64d243).</span><span class="sxs-lookup"><span data-stu-id="b3550-105">For more information about this service, see [A Closer Look at Platform Invoke](http://msdn.microsoft.com/en-us/ba9dd55b-2eaa-45cd-8afd-75cb8d64d243).</span></span>  
  
 <span data-ttu-id="b3550-106">Esta seção apresenta várias tarefas associadas ao consumo de funções de DLL não gerenciadas.</span><span class="sxs-lookup"><span data-stu-id="b3550-106">This section introduces several tasks associated with consuming unmanaged DLL functions.</span></span> <span data-ttu-id="b3550-107">Além das tarefas a seguir, há considerações gerais e um link que fornece exemplos e informações adicionais.</span><span class="sxs-lookup"><span data-stu-id="b3550-107">In addition to the following tasks, there are general considerations and a link providing additional information and examples.</span></span>  
  
#### <a name="to-consume-exported-dll-functions"></a><span data-ttu-id="b3550-108">Para consumir funções de DLL exportadas</span><span class="sxs-lookup"><span data-stu-id="b3550-108">To consume exported DLL functions</span></span>  
  
1.  <span data-ttu-id="b3550-109">[Identifique as funções nas DLLs](../../../docs/framework/interop/identifying-functions-in-dlls.md).</span><span class="sxs-lookup"><span data-stu-id="b3550-109">[Identify functions in DLLs](../../../docs/framework/interop/identifying-functions-in-dlls.md).</span></span>  
  
     <span data-ttu-id="b3550-110">No mínimo, é necessário especificar o nome da função e o nome da DLL que ela contém.</span><span class="sxs-lookup"><span data-stu-id="b3550-110">Minimally, you must specify the name of the function and name of the DLL that contains it.</span></span>  
  
2.  <span data-ttu-id="b3550-111">[Crie uma classe para conter funções de DLL](../../../docs/framework/interop/creating-a-class-to-hold-dll-functions.md).</span><span class="sxs-lookup"><span data-stu-id="b3550-111">[Create a class to hold DLL functions](../../../docs/framework/interop/creating-a-class-to-hold-dll-functions.md).</span></span>  
  
     <span data-ttu-id="b3550-112">Use uma classe existente, crie uma classe individual para cada função não gerenciada ou crie uma classe que contém um conjunto de funções não gerenciadas relacionadas.</span><span class="sxs-lookup"><span data-stu-id="b3550-112">You can use an existing class, create an individual class for each unmanaged function, or create one class that contains a set of related unmanaged functions.</span></span>  
  
3.  <span data-ttu-id="b3550-113">[Crie protótipos em um código gerenciado](../../../docs/framework/interop/creating-prototypes-in-managed-code.md).</span><span class="sxs-lookup"><span data-stu-id="b3550-113">[Create prototypes in managed code](../../../docs/framework/interop/creating-prototypes-in-managed-code.md).</span></span>  
  
     <span data-ttu-id="b3550-114">[Visual Basic] Use a instrução **Declare** com as palavras-chave **Function** e **Lib**.</span><span class="sxs-lookup"><span data-stu-id="b3550-114">[Visual Basic] Use the **Declare** statement with the **Function** and **Lib** keywords.</span></span> <span data-ttu-id="b3550-115">Em alguns casos raros, é possível usar o **DllImportAttribute** com as palavras-chave **Shared Function**.</span><span class="sxs-lookup"><span data-stu-id="b3550-115">In some rare cases, you can use the **DllImportAttribute** with the **Shared Function** keywords.</span></span> <span data-ttu-id="b3550-116">Esses casos são explicados mais adiante nesta seção.</span><span class="sxs-lookup"><span data-stu-id="b3550-116">These cases are explained later in this section.</span></span>  
  
     <span data-ttu-id="b3550-117">[C#] Use o **DllImportAttribute** para identificar a DLL e a função.</span><span class="sxs-lookup"><span data-stu-id="b3550-117">[C#] Use the **DllImportAttribute** to identify the DLL and function.</span></span> <span data-ttu-id="b3550-118">Marque o método com os modificadores **static** e **extern**.</span><span class="sxs-lookup"><span data-stu-id="b3550-118">Mark the method with the **static** and **extern** modifiers.</span></span>  
  
     <span data-ttu-id="b3550-119">[C++] Use o **DllImportAttribute** para identificar a DLL e a função.</span><span class="sxs-lookup"><span data-stu-id="b3550-119">[C++] Use the **DllImportAttribute** to identify the DLL and function.</span></span> <span data-ttu-id="b3550-120">Marque o método wrapper ou a função com **extern "C"**.</span><span class="sxs-lookup"><span data-stu-id="b3550-120">Mark the wrapper method or function with **extern "C"**.</span></span>  
  
4.  <span data-ttu-id="b3550-121">[Chame uma função de DLL](../../../docs/framework/interop/calling-a-dll-function.md).</span><span class="sxs-lookup"><span data-stu-id="b3550-121">[Call a DLL function](../../../docs/framework/interop/calling-a-dll-function.md).</span></span>  
  
     <span data-ttu-id="b3550-122">Chame o método na classe gerenciada como faria com qualquer outro método gerenciado.</span><span class="sxs-lookup"><span data-stu-id="b3550-122">Call the method on your managed class as you would any other managed method.</span></span> <span data-ttu-id="b3550-123">[Passar estruturas](../../../docs/framework/interop/passing-structures.md) e [implementar funções de retorno de chamada](../../../docs/framework/interop/callback-functions.md) são casos especiais.</span><span class="sxs-lookup"><span data-stu-id="b3550-123">[Passing structures](../../../docs/framework/interop/passing-structures.md) and [implementing callback functions](../../../docs/framework/interop/callback-functions.md) are special cases.</span></span>  
  
 <span data-ttu-id="b3550-124">Para obter exemplos que demonstram como construir declarações baseadas no .NET a serem usadas com a invocação de plataforma, consulte [Realizando marshaling de dados com a invocação de plataforma](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md).</span><span class="sxs-lookup"><span data-stu-id="b3550-124">For examples that demonstrate how to construct .NET-based declarations to be used with platform invoke, see [Marshaling Data with Platform Invoke](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md).</span></span>  
  
## <a name="a-closer-look-at-platform-invoke"></a><span data-ttu-id="b3550-125">Visão aprofundada da invocação de plataforma</span><span class="sxs-lookup"><span data-stu-id="b3550-125">A closer look at platform invoke</span></span>  
 <span data-ttu-id="b3550-126">A invocação de plataforma se baseia nos metadados para localizar funções exportadas e realizar marshaling em seus argumentos em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="b3550-126">Platform invoke relies on metadata to locate exported functions and marshal their arguments at run time.</span></span> <span data-ttu-id="b3550-127">A ilustração a seguir mostra esse processo.</span><span class="sxs-lookup"><span data-stu-id="b3550-127">The following illustration shows this process.</span></span>  
  
 <span data-ttu-id="b3550-128">![Invocação de plataforma](../../../docs/framework/interop/media/pinvoke.gif "pinvoke")</span><span class="sxs-lookup"><span data-stu-id="b3550-128">![Platform invoke](../../../docs/framework/interop/media/pinvoke.gif "pinvoke")</span></span>  
<span data-ttu-id="b3550-129">Uma chamada da invocação de plataforma a uma função de DLL não gerenciada</span><span class="sxs-lookup"><span data-stu-id="b3550-129">A platform invoke call to an unmanaged DLL function</span></span>  
  
 <span data-ttu-id="b3550-130">Quando uma invocação de plataforma chama uma função não gerenciada, ela executa a seguinte sequência de ações:</span><span class="sxs-lookup"><span data-stu-id="b3550-130">When platform invoke calls an unmanaged function, it performs the following sequence of actions:</span></span>  
  
1.  <span data-ttu-id="b3550-131">Localiza a DLL que contém a função.</span><span class="sxs-lookup"><span data-stu-id="b3550-131">Locates the DLL containing the function.</span></span>  
  
2.  <span data-ttu-id="b3550-132">Carrega a DLL na memória.</span><span class="sxs-lookup"><span data-stu-id="b3550-132">Loads the DLL into memory.</span></span>  
  
3.  <span data-ttu-id="b3550-133">Localiza o endereço da função na memória e efetua push de seus argumentos para a pilha, realizando marshaling dos dados, conforme necessário.</span><span class="sxs-lookup"><span data-stu-id="b3550-133">Locates the address of the function in memory and pushes its arguments onto the stack, marshaling data as required.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b3550-134">A localização e o carregamento da DLL, bem como a localização do endereço da função na memória, ocorrem apenas na primeira chamada à função.</span><span class="sxs-lookup"><span data-stu-id="b3550-134">Locating and loading the DLL, and locating the address of the function in memory occur only on the first call to the function.</span></span>  
  
4.  <span data-ttu-id="b3550-135">Transfere o controle para a função não gerenciada.</span><span class="sxs-lookup"><span data-stu-id="b3550-135">Transfers control to the unmanaged function.</span></span>  
  
 <span data-ttu-id="b3550-136">A invocação de plataforma gera exceções geradas pela função não gerenciada para o chamador gerenciado.</span><span class="sxs-lookup"><span data-stu-id="b3550-136">Platform invoke throws exceptions generated by the unmanaged function to the managed caller.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3550-137">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b3550-137">See Also</span></span>  
 [<span data-ttu-id="b3550-138">Interoperação com código não gerenciado</span><span class="sxs-lookup"><span data-stu-id="b3550-138">Interoperating with Unmanaged Code</span></span>](../../../docs/framework/interop/index.md)  
 [<span data-ttu-id="b3550-139">Exemplos de invocação de plataforma</span><span class="sxs-lookup"><span data-stu-id="b3550-139">Platform Invoke Examples</span></span>](../../../docs/framework/interop/platform-invoke-examples.md)  
 [<span data-ttu-id="b3550-140">Marshaling de interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="b3550-140">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)  
 [<span data-ttu-id="b3550-141">Consumindo funções de DLL não gerenciadas</span><span class="sxs-lookup"><span data-stu-id="b3550-141">Consuming Unmanaged DLL Functions</span></span>](../../../docs/framework/interop/consuming-unmanaged-dll-functions.md)
