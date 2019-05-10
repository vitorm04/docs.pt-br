---
title: 'Como: Chamar APIs do Windows (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- API calls [Visual Basic]
- Windows API, calling
- API calls [Visual Basic], platform invoke
- calls [Visual Basic], stored procedures
ms.assetid: 27d75f0a-54ab-4ee1-b91d-43513a19b12d
ms.openlocfilehash: 3769da28e1c9a27c8363b0d6ec639cedaf0f03be
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64624849"
---
# <a name="how-to-call-windows-apis-visual-basic"></a><span data-ttu-id="5a5a4-102">Como: Chamar APIs do Windows (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5a5a4-102">How to: Call Windows APIs (Visual Basic)</span></span>
<span data-ttu-id="5a5a4-103">Este exemplo define e chama o `MessageBox` função na User32. dll e, em seguida, passa uma cadeia de caracteres para ele.</span><span class="sxs-lookup"><span data-stu-id="5a5a4-103">This example defines and calls the `MessageBox` function in user32.dll and then passes a string to it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5a5a4-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5a5a4-104">Example</span></span>  
 [!code-vb[VbVbalrInterop#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="5a5a4-105">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="5a5a4-105">Compiling the Code</span></span>  
 <span data-ttu-id="5a5a4-106">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="5a5a4-106">This example requires:</span></span>  
  
- <span data-ttu-id="5a5a4-107">Uma referência para o <xref:System> namespace.</span><span class="sxs-lookup"><span data-stu-id="5a5a4-107">A reference to the <xref:System> namespace.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="5a5a4-108">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="5a5a4-108">Robust Programming</span></span>  
 <span data-ttu-id="5a5a4-109">As seguintes condições podem causar uma exceção:</span><span class="sxs-lookup"><span data-stu-id="5a5a4-109">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="5a5a4-110">O método não é estático, é abstrato ou foi definido anteriormente.</span><span class="sxs-lookup"><span data-stu-id="5a5a4-110">The method is not static, is abstract, or has been previously defined.</span></span> <span data-ttu-id="5a5a4-111">O tipo pai é uma interface ou o comprimento da *nome* ou *dllName* é zero.</span><span class="sxs-lookup"><span data-stu-id="5a5a4-111">The parent type is an interface, or the length of *name* or *dllName* is zero.</span></span> <span data-ttu-id="5a5a4-112">(<xref:System.ArgumentException>)</span><span class="sxs-lookup"><span data-stu-id="5a5a4-112">(<xref:System.ArgumentException>)</span></span>  
  
- <span data-ttu-id="5a5a4-113">O *nome* ou *dllName* é `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="5a5a4-113">The *name* or *dllName* is `Nothing`.</span></span> <span data-ttu-id="5a5a4-114">(<xref:System.ArgumentNullException>)</span><span class="sxs-lookup"><span data-stu-id="5a5a4-114">(<xref:System.ArgumentNullException>)</span></span>  
  
- <span data-ttu-id="5a5a4-115">O tipo recipiente foi criado anteriormente usando `CreateType`.</span><span class="sxs-lookup"><span data-stu-id="5a5a4-115">The containing type has been previously created using `CreateType`.</span></span> <span data-ttu-id="5a5a4-116">(<xref:System.InvalidOperationException>)</span><span class="sxs-lookup"><span data-stu-id="5a5a4-116">(<xref:System.InvalidOperationException>)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a5a4-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5a5a4-117">See also</span></span>

- [<span data-ttu-id="5a5a4-118">Um olhar detalhado sobre invocação de plataforma</span><span class="sxs-lookup"><span data-stu-id="5a5a4-118">A Closer Look at Platform Invoke</span></span>](../../../framework/interop/consuming-unmanaged-dll-functions.md#a-closer-look-at-platform-invoke)
- [<span data-ttu-id="5a5a4-119">Exemplos de invocação de plataforma</span><span class="sxs-lookup"><span data-stu-id="5a5a4-119">Platform Invoke Examples</span></span>](../../../framework/interop/platform-invoke-examples.md)
- [<span data-ttu-id="5a5a4-120">Consumindo funções de DLL não gerenciadas</span><span class="sxs-lookup"><span data-stu-id="5a5a4-120">Consuming Unmanaged DLL Functions</span></span>](../../../framework/interop/consuming-unmanaged-dll-functions.md)
- <span data-ttu-id="5a5a4-121">[Emissão de definição de um método com reflexão](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/w63y4d4f(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="5a5a4-121">[Defining a Method with Reflection Emit](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/w63y4d4f(v=vs.100))</span></span>
- [<span data-ttu-id="5a5a4-122">Passo a passo: fazer chamadas de APIs do Windows</span><span class="sxs-lookup"><span data-stu-id="5a5a4-122">Walkthrough: Calling Windows APIs</span></span>](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md)
- [<span data-ttu-id="5a5a4-123">Interoperabilidade COM</span><span class="sxs-lookup"><span data-stu-id="5a5a4-123">COM Interop</span></span>](../../../visual-basic/programming-guide/com-interop/index.md)
