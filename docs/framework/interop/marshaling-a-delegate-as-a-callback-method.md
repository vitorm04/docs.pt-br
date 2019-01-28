---
title: Realizando marshaling de um delegado como um método de retorno de chamada
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- data marshaling, Callback sample
- marshaling, Callback sample
ms.assetid: 6ddd7866-9804-4571-84de-83f5cc017a5a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2aa999199ddf11a1a2db57b6f7b1dd198b4ea61d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54529837"
---
# <a name="marshaling-a-delegate-as-a-callback-method"></a><span data-ttu-id="1e1b7-102">Realizando marshaling de um delegado como um método de retorno de chamada</span><span class="sxs-lookup"><span data-stu-id="1e1b7-102">Marshaling a Delegate as a Callback Method</span></span>
<span data-ttu-id="1e1b7-103">Este exemplo demonstra como passar delegados para uma função não gerenciada esperando ponteiros de função.</span><span class="sxs-lookup"><span data-stu-id="1e1b7-103">This sample demonstrates how to pass delegates to an unmanaged function expecting function pointers.</span></span> <span data-ttu-id="1e1b7-104">Um delegado é uma classe que pode conter uma referência a um método e é equivalente a um ponteiro de função fortemente tipada ou a uma função de retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="1e1b7-104">A delegate is a class that can hold a reference to a method and is equivalent to a type-safe function pointer or a callback function.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1e1b7-105">Quando você usa um delegado dentro de uma chamada, o Common Language Runtime protege o delegado de sofrer coleta de lixo pela duração da chamada.</span><span class="sxs-lookup"><span data-stu-id="1e1b7-105">When you use a delegate inside a call, the common language runtime protects the delegate from being garbage collected for the duration of that call.</span></span> <span data-ttu-id="1e1b7-106">No entanto, se a função não gerenciada armazena o delegado para uso após a conclusão da chamada, você deve evitar manualmente a coleta de lixo até que a função não gerenciada termine de usar o delegado.</span><span class="sxs-lookup"><span data-stu-id="1e1b7-106">However, if the unmanaged function stores the delegate to use after the call completes, you must manually prevent garbage collection until the unmanaged function finishes with the delegate.</span></span> <span data-ttu-id="1e1b7-107">Para obter mais informações, consulte a [Amostra de HandleRef](https://msdn.microsoft.com/library/ab23b04e-1d53-4ec7-b27a-e892d9298959(v=vs.100)) e [Amostra de GCHandle](https://msdn.microsoft.com/library/6acce798-0385-4ded-a790-77da842c113f(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="1e1b7-107">For more information, see the [HandleRef Sample](https://msdn.microsoft.com/library/ab23b04e-1d53-4ec7-b27a-e892d9298959(v=vs.100)) and [GCHandle Sample](https://msdn.microsoft.com/library/6acce798-0385-4ded-a790-77da842c113f(v=vs.100)).</span></span>  
  
 <span data-ttu-id="1e1b7-108">A amostra de Callback usa as seguintes funções não gerenciadas, mostradas com a respectiva declaração de função original:</span><span class="sxs-lookup"><span data-stu-id="1e1b7-108">The Callback sample uses the following unmanaged functions, shown with their original function declaration:</span></span>  
  
-   <span data-ttu-id="1e1b7-109">**TestCallBack** exportado de PinvokeLib.dll.</span><span class="sxs-lookup"><span data-stu-id="1e1b7-109">**TestCallBack** exported from PinvokeLib.dll.</span></span>  
  
    ```  
    void TestCallBack(FPTR pf, int value);  
    ```  
  
-   <span data-ttu-id="1e1b7-110">**TestCallBack2** exportado de PinvokeLib.dll.</span><span class="sxs-lookup"><span data-stu-id="1e1b7-110">**TestCallBack2** exported from PinvokeLib.dll.</span></span>  
  
    ```  
    void TestCallBack2(FPTR2 pf2, char* value);  
    ```  
  
 <span data-ttu-id="1e1b7-111">[PinvokeLib.dll](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/as6wyhwt(v=vs.100)) é uma biblioteca personalizada não gerenciada que contém uma implementação para as funções listadas anteriormente.</span><span class="sxs-lookup"><span data-stu-id="1e1b7-111">[PinvokeLib.dll](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/as6wyhwt(v=vs.100)) is a custom unmanaged library that contains an implementation for the previously listed functions.</span></span>  
  
 <span data-ttu-id="1e1b7-112">Neste exemplo, a classe `LibWrap` contém protótipos gerenciados para os métodos `TestCallBack` e `TestCallBack2`.</span><span class="sxs-lookup"><span data-stu-id="1e1b7-112">In this sample, the `LibWrap` class contains managed prototypes for the `TestCallBack` and `TestCallBack2` methods.</span></span> <span data-ttu-id="1e1b7-113">Ambos os métodos passam um delegado para uma função de retorno de chamada como um parâmetro.</span><span class="sxs-lookup"><span data-stu-id="1e1b7-113">Both methods pass a delegate to a callback function as a parameter.</span></span> <span data-ttu-id="1e1b7-114">A assinatura do delegado deve corresponder à assinatura do método ao qual ele faz referência.</span><span class="sxs-lookup"><span data-stu-id="1e1b7-114">The signature of the delegate must match the signature of the method it references.</span></span> <span data-ttu-id="1e1b7-115">Por exemplo, os delegados `FPtr` e `FPtr2` têm assinaturas que são idênticas aos métodos `DoSomething` e `DoSomething2`.</span><span class="sxs-lookup"><span data-stu-id="1e1b7-115">For example, the `FPtr` and `FPtr2` delegates have signatures that are identical to the `DoSomething` and `DoSomething2` methods.</span></span>  
  
## <a name="declaring-prototypes"></a><span data-ttu-id="1e1b7-116">Declarando Protótipos</span><span class="sxs-lookup"><span data-stu-id="1e1b7-116">Declaring Prototypes</span></span>  
 [!code-cpp[Conceptual.Interop.Marshaling#37](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/callback.cpp#37)]
 [!code-csharp[Conceptual.Interop.Marshaling#37](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/callback.cs#37)]
 [!code-vb[Conceptual.Interop.Marshaling#37](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/callback.vb#37)]  
  
## <a name="calling-functions"></a><span data-ttu-id="1e1b7-117">Chamando Funções</span><span class="sxs-lookup"><span data-stu-id="1e1b7-117">Calling Functions</span></span>  
 [!code-cpp[Conceptual.Interop.Marshaling#38](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/callback.cpp#38)]
 [!code-csharp[Conceptual.Interop.Marshaling#38](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/callback.cs#38)]
 [!code-vb[Conceptual.Interop.Marshaling#38](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/callback.vb#38)]  
  
## <a name="see-also"></a><span data-ttu-id="1e1b7-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1e1b7-118">See also</span></span>
- <span data-ttu-id="1e1b7-119">[Exemplos diversos de marshaling](https://msdn.microsoft.com/library/a915c948-54e9-4d0f-a525-95a77fd8ed70(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="1e1b7-119">[Miscellaneous Marshaling Samples](https://msdn.microsoft.com/library/a915c948-54e9-4d0f-a525-95a77fd8ed70(v=vs.100))</span></span>
- <span data-ttu-id="1e1b7-120">[Tipos de dados de invocação de plataforma](https://msdn.microsoft.com/library/16014d9f-d6bd-481e-83f0-df11377c550f(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="1e1b7-120">[Platform Invoke Data Types](https://msdn.microsoft.com/library/16014d9f-d6bd-481e-83f0-df11377c550f(v=vs.100))</span></span>
- [<span data-ttu-id="1e1b7-121">Criando protótipos em código gerenciado</span><span class="sxs-lookup"><span data-stu-id="1e1b7-121">Creating Prototypes in Managed Code</span></span>](creating-prototypes-in-managed-code.md)
