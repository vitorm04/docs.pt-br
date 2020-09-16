---
title: 'Como: Chamar APIs do Windows'
ms.date: 07/20/2015
helpviewer_keywords:
- API calls [Visual Basic]
- Windows API, calling
- API calls [Visual Basic], platform invoke
- calls [Visual Basic], stored procedures
ms.assetid: 27d75f0a-54ab-4ee1-b91d-43513a19b12d
ms.openlocfilehash: 863986e94855e02e9fd04685f7dc3e8e7f7b1cc3
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90548059"
---
# <a name="how-to-call-windows-apis-visual-basic"></a><span data-ttu-id="a05e2-102">Como chamar APIs do Windows (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a05e2-102">How to: Call Windows APIs (Visual Basic)</span></span>
<span data-ttu-id="a05e2-103">Este exemplo define e chama a `MessageBox` função em user32.dll e, em seguida, passa uma cadeia de caracteres para ela.</span><span class="sxs-lookup"><span data-stu-id="a05e2-103">This example defines and calls the `MessageBox` function in user32.dll and then passes a string to it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a05e2-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a05e2-104">Example</span></span>  
 [!code-vb[VbVbalrInterop#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#1)]  
  
## <a name="compile-the-code"></a><span data-ttu-id="a05e2-105">Compilar o código</span><span class="sxs-lookup"><span data-stu-id="a05e2-105">Compile the code</span></span>  
 <span data-ttu-id="a05e2-106">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="a05e2-106">This example requires:</span></span>  
  
- <span data-ttu-id="a05e2-107">Uma referência ao <xref:System> namespace.</span><span class="sxs-lookup"><span data-stu-id="a05e2-107">A reference to the <xref:System> namespace.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="a05e2-108">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="a05e2-108">Robust Programming</span></span>  
 <span data-ttu-id="a05e2-109">As seguintes condições podem causar uma exceção:</span><span class="sxs-lookup"><span data-stu-id="a05e2-109">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="a05e2-110">O método não é estático, é abstrato ou foi definido anteriormente.</span><span class="sxs-lookup"><span data-stu-id="a05e2-110">The method is not static, is abstract, or has been previously defined.</span></span> <span data-ttu-id="a05e2-111">O tipo de pai é uma interface ou o comprimento de *Name* ou *DllName* é zero.</span><span class="sxs-lookup"><span data-stu-id="a05e2-111">The parent type is an interface, or the length of *name* or *dllName* is zero.</span></span> <span data-ttu-id="a05e2-112">(<xref:System.ArgumentException>)</span><span class="sxs-lookup"><span data-stu-id="a05e2-112">(<xref:System.ArgumentException>)</span></span>  
  
- <span data-ttu-id="a05e2-113">O *nome* ou *DllName* é `Nothing` .</span><span class="sxs-lookup"><span data-stu-id="a05e2-113">The *name* or *dllName* is `Nothing`.</span></span> <span data-ttu-id="a05e2-114">(<xref:System.ArgumentNullException>)</span><span class="sxs-lookup"><span data-stu-id="a05e2-114">(<xref:System.ArgumentNullException>)</span></span>  
  
- <span data-ttu-id="a05e2-115">O tipo recipiente foi criado anteriormente usando `CreateType`.</span><span class="sxs-lookup"><span data-stu-id="a05e2-115">The containing type has been previously created using `CreateType`.</span></span> <span data-ttu-id="a05e2-116">(<xref:System.InvalidOperationException>)</span><span class="sxs-lookup"><span data-stu-id="a05e2-116">(<xref:System.InvalidOperationException>)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a05e2-117">Confira também</span><span class="sxs-lookup"><span data-stu-id="a05e2-117">See also</span></span>

- [<span data-ttu-id="a05e2-118">Um olhar detalhado sobre invocação de plataforma</span><span class="sxs-lookup"><span data-stu-id="a05e2-118">A Closer Look at Platform Invoke</span></span>](../../../framework/interop/consuming-unmanaged-dll-functions.md#a-closer-look-at-platform-invoke)
- [<span data-ttu-id="a05e2-119">Exemplos de invocação de plataforma</span><span class="sxs-lookup"><span data-stu-id="a05e2-119">Platform Invoke Examples</span></span>](../../../framework/interop/platform-invoke-examples.md)
- [<span data-ttu-id="a05e2-120">Consumindo funções de DLL não gerenciadas</span><span class="sxs-lookup"><span data-stu-id="a05e2-120">Consuming Unmanaged DLL Functions</span></span>](../../../framework/interop/consuming-unmanaged-dll-functions.md)
- <span data-ttu-id="a05e2-121">[Definindo um método com a emissão de reflexão](/previous-versions/dotnet/netframework-4.0/w63y4d4f(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="a05e2-121">[Defining a Method with Reflection Emit](/previous-versions/dotnet/netframework-4.0/w63y4d4f(v=vs.100))</span></span>
- [<span data-ttu-id="a05e2-122">Passo a passo: Fazer chamadas de APIs do Windows</span><span class="sxs-lookup"><span data-stu-id="a05e2-122">Walkthrough: Calling Windows APIs</span></span>](walkthrough-calling-windows-apis.md)
- [<span data-ttu-id="a05e2-123">Interoperabilidade COM</span><span class="sxs-lookup"><span data-stu-id="a05e2-123">COM Interop</span></span>](index.md)
