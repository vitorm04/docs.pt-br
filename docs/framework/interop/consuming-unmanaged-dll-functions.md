---
title: Consumindo funções de DLL não gerenciadas
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9ef6a31ba9589ded9527d15e90724d0d04749579
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71051840"
---
# <a name="consuming-unmanaged-dll-functions"></a><span data-ttu-id="05b64-102">Consumindo funções de DLL não gerenciadas</span><span class="sxs-lookup"><span data-stu-id="05b64-102">Consuming Unmanaged DLL Functions</span></span>
<span data-ttu-id="05b64-103">A invocação de plataforma é um serviço que permite que um código gerenciado chame funções não gerenciadas implementadas em DLLs (bibliotecas de vínculo dinâmico), como aquelas na API do Windows.</span><span class="sxs-lookup"><span data-stu-id="05b64-103">Platform invoke is a service that enables managed code to call unmanaged functions implemented in dynamic link libraries (DLLs), such as those in the Windows API.</span></span> <span data-ttu-id="05b64-104">Ela localiza e invoca uma função exportada e realiza marshaling dos argumentos (inteiros, cadeias de caracteres, matrizes, estruturas e assim por diante) além do limite de interoperação, conforme necessário.</span><span class="sxs-lookup"><span data-stu-id="05b64-104">It locates and invokes an exported function and marshals its arguments (integers, strings, arrays, structures, and so on) across the interoperation boundary as needed.</span></span>  
  
 <span data-ttu-id="05b64-105">Esta seção apresenta as tarefas associadas às funções DLL não gerenciadas de consumo e fornece mais informações sobre invocação de plataforma.</span><span class="sxs-lookup"><span data-stu-id="05b64-105">This section introduces tasks associated with consuming unmanaged DLL functions and provides more information about platform invoke.</span></span> <span data-ttu-id="05b64-106">Além das tarefas a seguir, há considerações gerais e um link que fornece exemplos e informações adicionais.</span><span class="sxs-lookup"><span data-stu-id="05b64-106">In addition to the following tasks, there are general considerations and a link providing additional information and examples.</span></span>  
  
#### <a name="to-consume-exported-dll-functions"></a><span data-ttu-id="05b64-107">Para consumir funções de DLL exportadas</span><span class="sxs-lookup"><span data-stu-id="05b64-107">To consume exported DLL functions</span></span>  
  
1. <span data-ttu-id="05b64-108">[Identifique as funções nas DLLs](identifying-functions-in-dlls.md).</span><span class="sxs-lookup"><span data-stu-id="05b64-108">[Identify functions in DLLs](identifying-functions-in-dlls.md).</span></span>  
  
     <span data-ttu-id="05b64-109">No mínimo, é necessário especificar o nome da função e o nome da DLL que ela contém.</span><span class="sxs-lookup"><span data-stu-id="05b64-109">Minimally, you must specify the name of the function and name of the DLL that contains it.</span></span>  
  
2. <span data-ttu-id="05b64-110">[Crie uma classe para conter funções de DLL](creating-a-class-to-hold-dll-functions.md).</span><span class="sxs-lookup"><span data-stu-id="05b64-110">[Create a class to hold DLL functions](creating-a-class-to-hold-dll-functions.md).</span></span>  
  
     <span data-ttu-id="05b64-111">Use uma classe existente, crie uma classe individual para cada função não gerenciada ou crie uma classe que contém um conjunto de funções não gerenciadas relacionadas.</span><span class="sxs-lookup"><span data-stu-id="05b64-111">You can use an existing class, create an individual class for each unmanaged function, or create one class that contains a set of related unmanaged functions.</span></span>  
  
3. <span data-ttu-id="05b64-112">[Crie protótipos em um código gerenciado](creating-prototypes-in-managed-code.md).</span><span class="sxs-lookup"><span data-stu-id="05b64-112">[Create prototypes in managed code](creating-prototypes-in-managed-code.md).</span></span>  
  
     <span data-ttu-id="05b64-113">[Visual Basic] Use a instrução **Declare** com as palavras-chave **Function** e **Lib**.</span><span class="sxs-lookup"><span data-stu-id="05b64-113">[Visual Basic] Use the **Declare** statement with the **Function** and **Lib** keywords.</span></span> <span data-ttu-id="05b64-114">Em alguns casos raros, é possível usar o **DllImportAttribute** com as palavras-chave **Shared Function**.</span><span class="sxs-lookup"><span data-stu-id="05b64-114">In some rare cases, you can use the **DllImportAttribute** with the **Shared Function** keywords.</span></span> <span data-ttu-id="05b64-115">Esses casos são explicados mais adiante nesta seção.</span><span class="sxs-lookup"><span data-stu-id="05b64-115">These cases are explained later in this section.</span></span>  
  
     <span data-ttu-id="05b64-116">[C#] Use o **DllImportAttribute** para identificar a DLL e a função.</span><span class="sxs-lookup"><span data-stu-id="05b64-116">[C#] Use the **DllImportAttribute** to identify the DLL and function.</span></span> <span data-ttu-id="05b64-117">Marque o método com os modificadores **static** e **extern**.</span><span class="sxs-lookup"><span data-stu-id="05b64-117">Mark the method with the **static** and **extern** modifiers.</span></span>  
  
     <span data-ttu-id="05b64-118">[C++] Use o **DllImportAttribute** para identificar a DLL e a função.</span><span class="sxs-lookup"><span data-stu-id="05b64-118">[C++] Use the **DllImportAttribute** to identify the DLL and function.</span></span> <span data-ttu-id="05b64-119">Marque o método wrapper ou a função com **extern "C"** .</span><span class="sxs-lookup"><span data-stu-id="05b64-119">Mark the wrapper method or function with **extern "C"**.</span></span>  
  
4. <span data-ttu-id="05b64-120">[Chame uma função de DLL](calling-a-dll-function.md).</span><span class="sxs-lookup"><span data-stu-id="05b64-120">[Call a DLL function](calling-a-dll-function.md).</span></span>  
  
     <span data-ttu-id="05b64-121">Chame o método na classe gerenciada como faria com qualquer outro método gerenciado.</span><span class="sxs-lookup"><span data-stu-id="05b64-121">Call the method on your managed class as you would any other managed method.</span></span> <span data-ttu-id="05b64-122">[Passar estruturas](passing-structures.md) e [implementar funções de retorno de chamada](callback-functions.md) são casos especiais.</span><span class="sxs-lookup"><span data-stu-id="05b64-122">[Passing structures](passing-structures.md) and [implementing callback functions](callback-functions.md) are special cases.</span></span>  
  
 <span data-ttu-id="05b64-123">Para obter exemplos que demonstram como construir declarações baseadas no .NET a serem usadas com a invocação de plataforma, consulte [Realizando marshaling de dados com a invocação de plataforma](marshaling-data-with-platform-invoke.md).</span><span class="sxs-lookup"><span data-stu-id="05b64-123">For examples that demonstrate how to construct .NET-based declarations to be used with platform invoke, see [Marshaling Data with Platform Invoke](marshaling-data-with-platform-invoke.md).</span></span>  
  
## <a name="a-closer-look-at-platform-invoke"></a><span data-ttu-id="05b64-124">Visão aprofundada da invocação de plataforma</span><span class="sxs-lookup"><span data-stu-id="05b64-124">A closer look at platform invoke</span></span>  
 <span data-ttu-id="05b64-125">A invocação de plataforma se baseia nos metadados para localizar funções exportadas e realizar marshaling em seus argumentos em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="05b64-125">Platform invoke relies on metadata to locate exported functions and marshal their arguments at run time.</span></span> <span data-ttu-id="05b64-126">A ilustração a seguir mostra esse processo.</span><span class="sxs-lookup"><span data-stu-id="05b64-126">The following illustration shows this process.</span></span>  
  
 ![Diagrama que mostra uma chamada de invocação de plataforma.](./media/consuming-unmanaged-dll-functions/platform-invoke-call.gif)  
  
 <span data-ttu-id="05b64-128">Quando uma invocação de plataforma chama uma função não gerenciada, ela executa a seguinte sequência de ações:</span><span class="sxs-lookup"><span data-stu-id="05b64-128">When platform invoke calls an unmanaged function, it performs the following sequence of actions:</span></span>  
  
1. <span data-ttu-id="05b64-129">Localiza a DLL que contém a função.</span><span class="sxs-lookup"><span data-stu-id="05b64-129">Locates the DLL containing the function.</span></span>  
  
2. <span data-ttu-id="05b64-130">Carrega a DLL na memória.</span><span class="sxs-lookup"><span data-stu-id="05b64-130">Loads the DLL into memory.</span></span>  
  
3. <span data-ttu-id="05b64-131">Localiza o endereço da função na memória e efetua push de seus argumentos para a pilha, realizando marshaling dos dados, conforme necessário.</span><span class="sxs-lookup"><span data-stu-id="05b64-131">Locates the address of the function in memory and pushes its arguments onto the stack, marshaling data as required.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="05b64-132">A localização e o carregamento da DLL, bem como a localização do endereço da função na memória, ocorrem apenas na primeira chamada à função.</span><span class="sxs-lookup"><span data-stu-id="05b64-132">Locating and loading the DLL, and locating the address of the function in memory occur only on the first call to the function.</span></span>  
  
4. <span data-ttu-id="05b64-133">Transfere o controle para a função não gerenciada.</span><span class="sxs-lookup"><span data-stu-id="05b64-133">Transfers control to the unmanaged function.</span></span>  
  
 <span data-ttu-id="05b64-134">A invocação de plataforma gera exceções geradas pela função não gerenciada para o chamador gerenciado.</span><span class="sxs-lookup"><span data-stu-id="05b64-134">Platform invoke throws exceptions generated by the unmanaged function to the managed caller.</span></span>

## <a name="see-also"></a><span data-ttu-id="05b64-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="05b64-135">See also</span></span>

- [<span data-ttu-id="05b64-136">Interoperação com código não gerenciado</span><span class="sxs-lookup"><span data-stu-id="05b64-136">Interoperating with Unmanaged Code</span></span>](index.md)
- [<span data-ttu-id="05b64-137">Exemplos de invocação de plataforma</span><span class="sxs-lookup"><span data-stu-id="05b64-137">Platform Invoke Examples</span></span>](platform-invoke-examples.md)
- [<span data-ttu-id="05b64-138">Marshaling de interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="05b64-138">Interop Marshaling</span></span>](interop-marshaling.md)
