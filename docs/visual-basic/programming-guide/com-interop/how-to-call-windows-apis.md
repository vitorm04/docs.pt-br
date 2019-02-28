---
title: 'Como: Chamar APIs do Windows (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- API calls [Visual Basic]
- Windows API, calling
- API calls [Visual Basic], platform invoke
- calls [Visual Basic], stored procedures
ms.assetid: 27d75f0a-54ab-4ee1-b91d-43513a19b12d
ms.openlocfilehash: e7b76495b83cb9a1dfe7629a1d82695d2046eac2
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56972762"
---
# <a name="how-to-call-windows-apis-visual-basic"></a><span data-ttu-id="cecb9-102">Como: Chamar APIs do Windows (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cecb9-102">How to: Call Windows APIs (Visual Basic)</span></span>
<span data-ttu-id="cecb9-103">Este exemplo define e chama o `MessageBox` função na User32. dll e, em seguida, passa uma cadeia de caracteres para ele.</span><span class="sxs-lookup"><span data-stu-id="cecb9-103">This example defines and calls the `MessageBox` function in user32.dll and then passes a string to it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cecb9-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="cecb9-104">Example</span></span>  
 [!code-vb[VbVbalrInterop#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="cecb9-105">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="cecb9-105">Compiling the Code</span></span>  
 <span data-ttu-id="cecb9-106">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="cecb9-106">This example requires:</span></span>  
  
-   <span data-ttu-id="cecb9-107">Uma referência para o <xref:System> namespace.</span><span class="sxs-lookup"><span data-stu-id="cecb9-107">A reference to the <xref:System> namespace.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="cecb9-108">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="cecb9-108">Robust Programming</span></span>  
 <span data-ttu-id="cecb9-109">As seguintes condições podem causar uma exceção:</span><span class="sxs-lookup"><span data-stu-id="cecb9-109">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="cecb9-110">O método não é estático, é abstrato ou foi definido anteriormente.</span><span class="sxs-lookup"><span data-stu-id="cecb9-110">The method is not static, is abstract, or has been previously defined.</span></span> <span data-ttu-id="cecb9-111">O tipo pai é uma interface ou o comprimento da *nome* ou *dllName* é zero.</span><span class="sxs-lookup"><span data-stu-id="cecb9-111">The parent type is an interface, or the length of *name* or *dllName* is zero.</span></span> <span data-ttu-id="cecb9-112">(<xref:System.ArgumentException>)</span><span class="sxs-lookup"><span data-stu-id="cecb9-112">(<xref:System.ArgumentException>)</span></span>  
  
-   <span data-ttu-id="cecb9-113">O *nome* ou *dllName* é `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="cecb9-113">The *name* or *dllName* is `Nothing`.</span></span> <span data-ttu-id="cecb9-114">(<xref:System.ArgumentNullException>)</span><span class="sxs-lookup"><span data-stu-id="cecb9-114">(<xref:System.ArgumentNullException>)</span></span>  
  
-   <span data-ttu-id="cecb9-115">O tipo recipiente foi criado anteriormente usando `CreateType`.</span><span class="sxs-lookup"><span data-stu-id="cecb9-115">The containing type has been previously created using `CreateType`.</span></span> <span data-ttu-id="cecb9-116">(<xref:System.InvalidOperationException>)</span><span class="sxs-lookup"><span data-stu-id="cecb9-116">(<xref:System.InvalidOperationException>)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cecb9-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cecb9-117">See also</span></span>

- [<span data-ttu-id="cecb9-118">Um olhar detalhado sobre invocação de plataforma</span><span class="sxs-lookup"><span data-stu-id="cecb9-118">A Closer Look at Platform Invoke</span></span>](../../../framework/interop/consuming-unmanaged-dll-functions.md#a-closer-look-at-platform-invoke)
- [<span data-ttu-id="cecb9-119">Exemplos de invocação de plataforma</span><span class="sxs-lookup"><span data-stu-id="cecb9-119">Platform Invoke Examples</span></span>](../../../framework/interop/platform-invoke-examples.md)
- [<span data-ttu-id="cecb9-120">Consumindo funções de DLL não gerenciadas</span><span class="sxs-lookup"><span data-stu-id="cecb9-120">Consuming Unmanaged DLL Functions</span></span>](../../../framework/interop/consuming-unmanaged-dll-functions.md)
- <span data-ttu-id="cecb9-121">[Emissão de definição de um método com reflexão](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/w63y4d4f(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="cecb9-121">[Defining a Method with Reflection Emit](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/w63y4d4f(v=vs.100))</span></span>
- [<span data-ttu-id="cecb9-122">Passo a passo: fazer chamadas de APIs do Windows</span><span class="sxs-lookup"><span data-stu-id="cecb9-122">Walkthrough: Calling Windows APIs</span></span>](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md)
- [<span data-ttu-id="cecb9-123">Interoperabilidade COM</span><span class="sxs-lookup"><span data-stu-id="cecb9-123">COM Interop</span></span>](../../../visual-basic/programming-guide/com-interop/index.md)
