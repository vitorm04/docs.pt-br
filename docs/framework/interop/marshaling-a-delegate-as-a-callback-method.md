---
title: "Realizando marshaling de um delegado como um método de retorno de chamada"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- data marshaling, Callback sample
- marshaling, Callback sample
ms.assetid: 6ddd7866-9804-4571-84de-83f5cc017a5a
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c8c4eca35c406b38da603dc10358920ee887b137
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="marshaling-a-delegate-as-a-callback-method"></a><span data-ttu-id="ac815-102">Realizando marshaling de um delegado como um método de retorno de chamada</span><span class="sxs-lookup"><span data-stu-id="ac815-102">Marshaling a Delegate as a Callback Method</span></span>
<span data-ttu-id="ac815-103">Este exemplo demonstra como passar delegados para uma função não gerenciada esperando ponteiros de função.</span><span class="sxs-lookup"><span data-stu-id="ac815-103">This sample demonstrates how to pass delegates to an unmanaged function expecting function pointers.</span></span> <span data-ttu-id="ac815-104">Um delegado é uma classe que pode conter uma referência a um método e é equivalente a um ponteiro de função fortemente tipada ou a uma função de retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="ac815-104">A delegate is a class that can hold a reference to a method and is equivalent to a type-safe function pointer or a callback function.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ac815-105">Quando você usa um delegado dentro de uma chamada, o Common Language Runtime protege o delegado de sofrer coleta de lixo pela duração da chamada.</span><span class="sxs-lookup"><span data-stu-id="ac815-105">When you use a delegate inside a call, the common language runtime protects the delegate from being garbage collected for the duration of that call.</span></span> <span data-ttu-id="ac815-106">No entanto, se a função não gerenciada armazena o delegado para uso após a conclusão da chamada, você deve evitar manualmente a coleta de lixo até que a função não gerenciada termine de usar o delegado.</span><span class="sxs-lookup"><span data-stu-id="ac815-106">However, if the unmanaged function stores the delegate to use after the call completes, you must manually prevent garbage collection until the unmanaged function finishes with the delegate.</span></span> <span data-ttu-id="ac815-107">Para obter mais informações, consulte a [Amostra de HandleRef](http://msdn.microsoft.com/en-us/ab23b04e-1d53-4ec7-b27a-e892d9298959) e [Amostra de GCHandle](http://msdn.microsoft.com/en-us/6acce798-0385-4ded-a790-77da842c113f).</span><span class="sxs-lookup"><span data-stu-id="ac815-107">For more information, see the [HandleRef Sample](http://msdn.microsoft.com/en-us/ab23b04e-1d53-4ec7-b27a-e892d9298959) and [GCHandle Sample](http://msdn.microsoft.com/en-us/6acce798-0385-4ded-a790-77da842c113f).</span></span>  
  
 <span data-ttu-id="ac815-108">A amostra de Callback usa as seguintes funções não gerenciadas, mostradas com a respectiva declaração de função original:</span><span class="sxs-lookup"><span data-stu-id="ac815-108">The Callback sample uses the following unmanaged functions, shown with their original function declaration:</span></span>  
  
-   <span data-ttu-id="ac815-109">**TestCallBack** exportado de PinvokeLib.dll.</span><span class="sxs-lookup"><span data-stu-id="ac815-109">**TestCallBack** exported from PinvokeLib.dll.</span></span>  
  
    ```  
    void TestCallBack(FPTR pf, int value);  
    ```  
  
-   <span data-ttu-id="ac815-110">**TestCallBack2** exportado de PinvokeLib.dll.</span><span class="sxs-lookup"><span data-stu-id="ac815-110">**TestCallBack2** exported from PinvokeLib.dll.</span></span>  
  
    ```  
    void TestCallBack2(FPTR2 pf2, char* value);  
    ```  
  
 <span data-ttu-id="ac815-111">[PinvokeLib.dll](http://msdn.microsoft.com/en-us/5d1438d7-9946-489d-8ede-6c694a08f614) é uma biblioteca personalizada não gerenciada que contém uma implementação para as funções listadas anteriormente.</span><span class="sxs-lookup"><span data-stu-id="ac815-111">[PinvokeLib.dll](http://msdn.microsoft.com/en-us/5d1438d7-9946-489d-8ede-6c694a08f614) is a custom unmanaged library that contains an implementation for the previously listed functions.</span></span>  
  
 <span data-ttu-id="ac815-112">Neste exemplo, a classe `LibWrap` contém protótipos gerenciados para os métodos `TestCallBack` e `TestCallBack2`.</span><span class="sxs-lookup"><span data-stu-id="ac815-112">In this sample, the `LibWrap` class contains managed prototypes for the `TestCallBack` and `TestCallBack2` methods.</span></span> <span data-ttu-id="ac815-113">Ambos os métodos passam um delegado para uma função de retorno de chamada como um parâmetro.</span><span class="sxs-lookup"><span data-stu-id="ac815-113">Both methods pass a delegate to a callback function as a parameter.</span></span> <span data-ttu-id="ac815-114">A assinatura do delegado deve corresponder à assinatura do método ao qual ele faz referência.</span><span class="sxs-lookup"><span data-stu-id="ac815-114">The signature of the delegate must match the signature of the method it references.</span></span> <span data-ttu-id="ac815-115">Por exemplo, os delegados `FPtr` e `FPtr2` têm assinaturas que são idênticas aos métodos `DoSomething` e `DoSomething2`.</span><span class="sxs-lookup"><span data-stu-id="ac815-115">For example, the `FPtr` and `FPtr2` delegates have signatures that are identical to the `DoSomething` and `DoSomething2` methods.</span></span>  
  
## <a name="declaring-prototypes"></a><span data-ttu-id="ac815-116">Declarando Protótipos</span><span class="sxs-lookup"><span data-stu-id="ac815-116">Declaring Prototypes</span></span>  
 [!code-cpp[Conceptual.Interop.Marshaling#37](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/callback.cpp#37)]
 [!code-csharp[Conceptual.Interop.Marshaling#37](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/callback.cs#37)]
 [!code-vb[Conceptual.Interop.Marshaling#37](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/callback.vb#37)]  
  
## <a name="calling-functions"></a><span data-ttu-id="ac815-117">Chamando Funções</span><span class="sxs-lookup"><span data-stu-id="ac815-117">Calling Functions</span></span>  
 [!code-cpp[Conceptual.Interop.Marshaling#38](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/callback.cpp#38)]
 [!code-csharp[Conceptual.Interop.Marshaling#38](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/callback.cs#38)]
 [!code-vb[Conceptual.Interop.Marshaling#38](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/callback.vb#38)]  
  
## <a name="see-also"></a><span data-ttu-id="ac815-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ac815-118">See Also</span></span>  
 [<span data-ttu-id="ac815-119">Exemplos diversos de marshaling</span><span class="sxs-lookup"><span data-stu-id="ac815-119">Miscellaneous Marshaling Samples</span></span>](http://msdn.microsoft.com/en-us/a915c948-54e9-4d0f-a525-95a77fd8ed70)  
 [<span data-ttu-id="ac815-120">Tipos de dados de invocação de plataforma</span><span class="sxs-lookup"><span data-stu-id="ac815-120">Platform Invoke Data Types</span></span>](http://msdn.microsoft.com/en-us/16014d9f-d6bd-481e-83f0-df11377c550f)  
 [<span data-ttu-id="ac815-121">Criando protótipos em código gerenciado</span><span class="sxs-lookup"><span data-stu-id="ac815-121">Creating Prototypes in Managed Code</span></span>](../../../docs/framework/interop/creating-prototypes-in-managed-code.md)
