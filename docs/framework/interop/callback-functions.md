---
title: Funções de retorno de chamada
ms.date: 03/30/2017
helpviewer_keywords:
- callback function
- platform invoke, calling unmanaged functions
ms.assetid: c0aa8533-3b3b-42e8-9f60-84919793098c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 65f5e11a8fb40527387c14cdd8dec7f0bfc5c697
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59196990"
---
# <a name="callback-functions"></a><span data-ttu-id="14444-102">Funções de retorno de chamada</span><span class="sxs-lookup"><span data-stu-id="14444-102">Callback Functions</span></span>
<span data-ttu-id="14444-103">Uma função de retorno de chamada é o código em um aplicativo gerenciado que ajuda uma função de DLL não gerenciada a concluir uma tarefa.</span><span class="sxs-lookup"><span data-stu-id="14444-103">A callback function is code within a managed application that helps an unmanaged DLL function complete a task.</span></span> <span data-ttu-id="14444-104">As chamadas a uma função de retorno de chamada passam indiretamente de um aplicativo gerenciado, por meio de uma função de DLL e novamente para a implementação gerenciada.</span><span class="sxs-lookup"><span data-stu-id="14444-104">Calls to a callback function pass indirectly from a managed application, through a DLL function, and back to the managed implementation.</span></span> <span data-ttu-id="14444-105">Algumas das muitas funções de DLL chamadas com a invocação de plataforma exigem que uma função de retorno de chamada no código gerenciado seja executada corretamente.</span><span class="sxs-lookup"><span data-stu-id="14444-105">Some of the many DLL functions called with platform invoke require a callback function in managed code to run properly.</span></span>  
  
 <span data-ttu-id="14444-106">Para chamar a maioria das funções de DLL por meio do código gerenciado, crie uma definição gerenciada da função e, em seguida, chame-a.</span><span class="sxs-lookup"><span data-stu-id="14444-106">To call most DLL functions from managed code, you create a managed definition of the function and then call it.</span></span> <span data-ttu-id="14444-107">O processo é simples.</span><span class="sxs-lookup"><span data-stu-id="14444-107">The process is straightforward.</span></span>  
  
 <span data-ttu-id="14444-108">O uso de uma função de DLL que exige uma função de retorno de chamada apresenta algumas etapas adicionais.</span><span class="sxs-lookup"><span data-stu-id="14444-108">Using a DLL function that requires a callback function has some additional steps.</span></span> <span data-ttu-id="14444-109">Primeiro, você deve determinar se a função exige um retorno de chamada examinando a documentação da função.</span><span class="sxs-lookup"><span data-stu-id="14444-109">First, you must determine whether the function requires a callback by looking at the documentation for the function.</span></span> <span data-ttu-id="14444-110">Em seguida, você precisa criar a função de retorno de chamada no aplicativo gerenciado.</span><span class="sxs-lookup"><span data-stu-id="14444-110">Next, you have to create the callback function in your managed application.</span></span> <span data-ttu-id="14444-111">Por fim, chame a função de DLL, passando um ponteiro para a função de retorno de chamada como um argumento.</span><span class="sxs-lookup"><span data-stu-id="14444-111">Finally, you call the DLL function, passing a pointer to the callback function as an argument.</span></span> 
 
 <span data-ttu-id="14444-112">A ilustração a seguir resume as etapas de implementação e a função de retorno de chamada:</span><span class="sxs-lookup"><span data-stu-id="14444-112">The following illustration summarizes the callback function and implementation steps:</span></span>  
  
 ![Diagrama mostrando o processo de retorno de chamada da invocação de plataforma.](./media/callback-functions/platform-invoke-callback-process.gif)  
  
 <span data-ttu-id="14444-114">As funções de retorno de chamada são ideais para uso em situações em que uma tarefa é executada repetidamente.</span><span class="sxs-lookup"><span data-stu-id="14444-114">Callback functions are ideal for use in situations in which a task is performed repeatedly.</span></span> <span data-ttu-id="14444-115">Outro uso comum é com funções de enumeração, como **EnumFontFamilies**, **EnumPrinters** e **EnumWindows** na API do Windows.</span><span class="sxs-lookup"><span data-stu-id="14444-115">Another common usage is with enumeration functions, such as **EnumFontFamilies**, **EnumPrinters**, and **EnumWindows** in the Windows API.</span></span> <span data-ttu-id="14444-116">A função **EnumWindows** enumera por meio de todas as janelas existentes no computador, chamando a função de retorno de chamada para executar uma tarefa em cada janela.</span><span class="sxs-lookup"><span data-stu-id="14444-116">The **EnumWindows** function enumerates through all existing windows on your computer, calling the callback function to perform a task on each window.</span></span> <span data-ttu-id="14444-117">Para obter instruções e um exemplo, confira [Como: Implementar funções de retorno de chamada](../../../docs/framework/interop/how-to-implement-callback-functions.md).</span><span class="sxs-lookup"><span data-stu-id="14444-117">For instructions and an example, see [How to: Implement Callback Functions](../../../docs/framework/interop/how-to-implement-callback-functions.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14444-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="14444-118">See also</span></span>

- [<span data-ttu-id="14444-119">Como: Implementar funções de retorno de chamada</span><span class="sxs-lookup"><span data-stu-id="14444-119">How to: Implement Callback Functions</span></span>](../../../docs/framework/interop/how-to-implement-callback-functions.md)
- [<span data-ttu-id="14444-120">Chamando uma função de DLL</span><span class="sxs-lookup"><span data-stu-id="14444-120">Calling a DLL Function</span></span>](../../../docs/framework/interop/calling-a-dll-function.md)
