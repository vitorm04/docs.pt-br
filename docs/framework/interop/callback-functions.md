---
title: Funções de retorno de chamada
description: Leia sobre as funções de retorno de chamada, que são o código com um aplicativo gerenciado que ajuda uma função DLL não gerenciada a concluir uma tarefa.
ms.date: 03/30/2017
helpviewer_keywords:
- callback function
- platform invoke, calling unmanaged functions
ms.assetid: c0aa8533-3b3b-42e8-9f60-84919793098c
ms.openlocfilehash: e28756b5ed935aff83363b38d6f33982e87718b2
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621711"
---
# <a name="callback-functions"></a><span data-ttu-id="ebf28-103">Funções de retorno de chamada</span><span class="sxs-lookup"><span data-stu-id="ebf28-103">Callback Functions</span></span>
<span data-ttu-id="ebf28-104">Uma função de retorno de chamada é o código em um aplicativo gerenciado que ajuda uma função de DLL não gerenciada a concluir uma tarefa.</span><span class="sxs-lookup"><span data-stu-id="ebf28-104">A callback function is code within a managed application that helps an unmanaged DLL function complete a task.</span></span> <span data-ttu-id="ebf28-105">As chamadas a uma função de retorno de chamada passam indiretamente de um aplicativo gerenciado, por meio de uma função de DLL e novamente para a implementação gerenciada.</span><span class="sxs-lookup"><span data-stu-id="ebf28-105">Calls to a callback function pass indirectly from a managed application, through a DLL function, and back to the managed implementation.</span></span> <span data-ttu-id="ebf28-106">Algumas das muitas funções de DLL chamadas com a invocação de plataforma exigem que uma função de retorno de chamada no código gerenciado seja executada corretamente.</span><span class="sxs-lookup"><span data-stu-id="ebf28-106">Some of the many DLL functions called with platform invoke require a callback function in managed code to run properly.</span></span>  
  
 <span data-ttu-id="ebf28-107">Para chamar a maioria das funções de DLL por meio do código gerenciado, crie uma definição gerenciada da função e, em seguida, chame-a.</span><span class="sxs-lookup"><span data-stu-id="ebf28-107">To call most DLL functions from managed code, you create a managed definition of the function and then call it.</span></span> <span data-ttu-id="ebf28-108">O processo é simples.</span><span class="sxs-lookup"><span data-stu-id="ebf28-108">The process is straightforward.</span></span>  
  
 <span data-ttu-id="ebf28-109">O uso de uma função de DLL que exige uma função de retorno de chamada apresenta algumas etapas adicionais.</span><span class="sxs-lookup"><span data-stu-id="ebf28-109">Using a DLL function that requires a callback function has some additional steps.</span></span> <span data-ttu-id="ebf28-110">Primeiro, você deve determinar se a função exige um retorno de chamada examinando a documentação da função.</span><span class="sxs-lookup"><span data-stu-id="ebf28-110">First, you must determine whether the function requires a callback by looking at the documentation for the function.</span></span> <span data-ttu-id="ebf28-111">Em seguida, você precisa criar a função de retorno de chamada no aplicativo gerenciado.</span><span class="sxs-lookup"><span data-stu-id="ebf28-111">Next, you have to create the callback function in your managed application.</span></span> <span data-ttu-id="ebf28-112">Por fim, chame a função de DLL, passando um ponteiro para a função de retorno de chamada como um argumento.</span><span class="sxs-lookup"><span data-stu-id="ebf28-112">Finally, you call the DLL function, passing a pointer to the callback function as an argument.</span></span>

 <span data-ttu-id="ebf28-113">A ilustração a seguir resume as etapas de implementação e a função de retorno de chamada:</span><span class="sxs-lookup"><span data-stu-id="ebf28-113">The following illustration summarizes the callback function and implementation steps:</span></span>  
  
 ![Diagrama mostrando o processo de retorno de chamada da invocação de plataforma.](./media/callback-functions/platform-invoke-callback-process.gif)  
  
 <span data-ttu-id="ebf28-115">As funções de retorno de chamada são ideais para uso em situações em que uma tarefa é executada repetidamente.</span><span class="sxs-lookup"><span data-stu-id="ebf28-115">Callback functions are ideal for use in situations in which a task is performed repeatedly.</span></span> <span data-ttu-id="ebf28-116">Outro uso comum é com funções de enumeração, como **EnumFontFamilies**, **EnumPrinters** e **EnumWindows** na API do Windows.</span><span class="sxs-lookup"><span data-stu-id="ebf28-116">Another common usage is with enumeration functions, such as **EnumFontFamilies**, **EnumPrinters**, and **EnumWindows** in the Windows API.</span></span> <span data-ttu-id="ebf28-117">A função **EnumWindows** enumera por meio de todas as janelas existentes no computador, chamando a função de retorno de chamada para executar uma tarefa em cada janela.</span><span class="sxs-lookup"><span data-stu-id="ebf28-117">The **EnumWindows** function enumerates through all existing windows on your computer, calling the callback function to perform a task on each window.</span></span> <span data-ttu-id="ebf28-118">Para obter instruções e um exemplo, consulte [Como implementar funções de retorno de chamada](how-to-implement-callback-functions.md).</span><span class="sxs-lookup"><span data-stu-id="ebf28-118">For instructions and an example, see [How to: Implement Callback Functions](how-to-implement-callback-functions.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ebf28-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ebf28-119">See also</span></span>

- [<span data-ttu-id="ebf28-120">Como: Implementar funções de retorno de chamada</span><span class="sxs-lookup"><span data-stu-id="ebf28-120">How to: Implement Callback Functions</span></span>](how-to-implement-callback-functions.md)
- [<span data-ttu-id="ebf28-121">Chamando uma função de DLL</span><span class="sxs-lookup"><span data-stu-id="ebf28-121">Calling a DLL Function</span></span>](calling-a-dll-function.md)
