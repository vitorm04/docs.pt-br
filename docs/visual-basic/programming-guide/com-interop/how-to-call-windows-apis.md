---
title: 'Como: Chamar APIs do Windows'
ms.date: 07/20/2015
helpviewer_keywords:
- API calls [Visual Basic]
- Windows API, calling
- API calls [Visual Basic], platform invoke
- calls [Visual Basic], stored procedures
ms.assetid: 27d75f0a-54ab-4ee1-b91d-43513a19b12d
ms.openlocfilehash: 2c3bb599b79575180eb2b0ec89453f01901f94c0
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84396837"
---
# <a name="how-to-call-windows-apis-visual-basic"></a><span data-ttu-id="13f5b-102">Como chamar APIs do Windows (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="13f5b-102">How to: Call Windows APIs (Visual Basic)</span></span>
<span data-ttu-id="13f5b-103">Este exemplo define e chama a `MessageBox` função em user32. dll e, em seguida, passa uma cadeia de caracteres para ela.</span><span class="sxs-lookup"><span data-stu-id="13f5b-103">This example defines and calls the `MessageBox` function in user32.dll and then passes a string to it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="13f5b-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="13f5b-104">Example</span></span>  
 [!code-vb[VbVbalrInterop#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#1)]  
  
## <a name="compile-the-code"></a><span data-ttu-id="13f5b-105">Compilar o código</span><span class="sxs-lookup"><span data-stu-id="13f5b-105">Compile the code</span></span>  
 <span data-ttu-id="13f5b-106">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="13f5b-106">This example requires:</span></span>  
  
- <span data-ttu-id="13f5b-107">Uma referência ao <xref:System> namespace.</span><span class="sxs-lookup"><span data-stu-id="13f5b-107">A reference to the <xref:System> namespace.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="13f5b-108">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="13f5b-108">Robust Programming</span></span>  
 <span data-ttu-id="13f5b-109">As seguintes condições podem causar uma exceção:</span><span class="sxs-lookup"><span data-stu-id="13f5b-109">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="13f5b-110">O método não é estático, é abstrato ou foi definido anteriormente.</span><span class="sxs-lookup"><span data-stu-id="13f5b-110">The method is not static, is abstract, or has been previously defined.</span></span> <span data-ttu-id="13f5b-111">O tipo de pai é uma interface ou o comprimento de *Name* ou *DllName* é zero.</span><span class="sxs-lookup"><span data-stu-id="13f5b-111">The parent type is an interface, or the length of *name* or *dllName* is zero.</span></span> <span data-ttu-id="13f5b-112">(<xref:System.ArgumentException>)</span><span class="sxs-lookup"><span data-stu-id="13f5b-112">(<xref:System.ArgumentException>)</span></span>  
  
- <span data-ttu-id="13f5b-113">O *nome* ou *DllName* é `Nothing` .</span><span class="sxs-lookup"><span data-stu-id="13f5b-113">The *name* or *dllName* is `Nothing`.</span></span> <span data-ttu-id="13f5b-114">(<xref:System.ArgumentNullException>)</span><span class="sxs-lookup"><span data-stu-id="13f5b-114">(<xref:System.ArgumentNullException>)</span></span>  
  
- <span data-ttu-id="13f5b-115">O tipo recipiente foi criado anteriormente usando `CreateType`.</span><span class="sxs-lookup"><span data-stu-id="13f5b-115">The containing type has been previously created using `CreateType`.</span></span> <span data-ttu-id="13f5b-116">(<xref:System.InvalidOperationException>)</span><span class="sxs-lookup"><span data-stu-id="13f5b-116">(<xref:System.InvalidOperationException>)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13f5b-117">Confira também</span><span class="sxs-lookup"><span data-stu-id="13f5b-117">See also</span></span>

- [<span data-ttu-id="13f5b-118">Um olhar detalhado sobre invocação de plataforma</span><span class="sxs-lookup"><span data-stu-id="13f5b-118">A Closer Look at Platform Invoke</span></span>](../../../framework/interop/consuming-unmanaged-dll-functions.md#a-closer-look-at-platform-invoke)
- [<span data-ttu-id="13f5b-119">Exemplos de invocação de plataforma</span><span class="sxs-lookup"><span data-stu-id="13f5b-119">Platform Invoke Examples</span></span>](../../../framework/interop/platform-invoke-examples.md)
- [<span data-ttu-id="13f5b-120">Consumindo funções de DLL não gerenciadas</span><span class="sxs-lookup"><span data-stu-id="13f5b-120">Consuming Unmanaged DLL Functions</span></span>](../../../framework/interop/consuming-unmanaged-dll-functions.md)
- <span data-ttu-id="13f5b-121">[Definindo um método com a emissão de reflexão](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/w63y4d4f(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="13f5b-121">[Defining a Method with Reflection Emit](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/w63y4d4f(v=vs.100))</span></span>
- [<span data-ttu-id="13f5b-122">Passo a passo: Fazer chamadas de APIs do Windows</span><span class="sxs-lookup"><span data-stu-id="13f5b-122">Walkthrough: Calling Windows APIs</span></span>](walkthrough-calling-windows-apis.md)
- [<span data-ttu-id="13f5b-123">Interoperabilidade COM</span><span class="sxs-lookup"><span data-stu-id="13f5b-123">COM Interop</span></span>](index.md)
