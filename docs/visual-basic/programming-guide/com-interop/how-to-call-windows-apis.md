---
title: Como chamar APIs do Windows (Visual Basic)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- API calls [Visual Basic]
- Windows API, calling
- API calls [Visual Basic], platform invoke
- calls [Visual Basic], stored procedures
ms.assetid: 27d75f0a-54ab-4ee1-b91d-43513a19b12d
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a219e031cdd36c713db8dcee6cc1da3849c9cf93
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-call-windows-apis-visual-basic"></a><span data-ttu-id="2d1be-102">Como chamar APIs do Windows (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2d1be-102">How to: Call Windows APIs (Visual Basic)</span></span>
<span data-ttu-id="2d1be-103">Este exemplo define e chama o `MessageBox` função na User32. dll e, em seguida, passa uma cadeia de caracteres para ele.</span><span class="sxs-lookup"><span data-stu-id="2d1be-103">This example defines and calls the `MessageBox` function in user32.dll and then passes a string to it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2d1be-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2d1be-104">Example</span></span>  
 [!code-vb[VbVbalrInterop#1](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/how-to-call-windows-apis_1.vb)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="2d1be-105">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="2d1be-105">Compiling the Code</span></span>  
 <span data-ttu-id="2d1be-106">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="2d1be-106">This example requires:</span></span>  
  
-   <span data-ttu-id="2d1be-107">Uma referência para o <xref:System> namespace.</span><span class="sxs-lookup"><span data-stu-id="2d1be-107">A reference to the <xref:System> namespace.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="2d1be-108">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="2d1be-108">Robust Programming</span></span>  
 <span data-ttu-id="2d1be-109">As seguintes condições podem causar uma exceção:</span><span class="sxs-lookup"><span data-stu-id="2d1be-109">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="2d1be-110">O método não é estático, é abstrato ou foi definido anteriormente.</span><span class="sxs-lookup"><span data-stu-id="2d1be-110">The method is not static, is abstract, or has been previously defined.</span></span> <span data-ttu-id="2d1be-111">O tipo pai é uma interface ou o comprimento de *nome* ou *Nomedadll* é zero.</span><span class="sxs-lookup"><span data-stu-id="2d1be-111">The parent type is an interface, or the length of *name* or *dllName* is zero.</span></span> <span data-ttu-id="2d1be-112">(<xref:System.ArgumentException>)</span><span class="sxs-lookup"><span data-stu-id="2d1be-112">(<xref:System.ArgumentException>)</span></span>  
  
-   <span data-ttu-id="2d1be-113">O *nome* ou *Nomedadll* é `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="2d1be-113">The *name* or *dllName* is `Nothing`.</span></span> <span data-ttu-id="2d1be-114">(<xref:System.ArgumentNullException>)</span><span class="sxs-lookup"><span data-stu-id="2d1be-114">(<xref:System.ArgumentNullException>)</span></span>  
  
-   <span data-ttu-id="2d1be-115">O tipo recipiente foi criado anteriormente usando `CreateType`.</span><span class="sxs-lookup"><span data-stu-id="2d1be-115">The containing type has been previously created using `CreateType`.</span></span> <span data-ttu-id="2d1be-116">(<xref:System.InvalidOperationException>)</span><span class="sxs-lookup"><span data-stu-id="2d1be-116">(<xref:System.InvalidOperationException>)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d1be-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2d1be-117">See Also</span></span>  
 [<span data-ttu-id="2d1be-118">Invocação de plataforma examinar mais detalhadamente</span><span class="sxs-lookup"><span data-stu-id="2d1be-118">A Closer Look at Platform Invoke</span></span>](http://msdn.microsoft.com/en-us/ba9dd55b-2eaa-45cd-8afd-75cb8d64d243)  
 [<span data-ttu-id="2d1be-119">Exemplos de invocação de plataforma</span><span class="sxs-lookup"><span data-stu-id="2d1be-119">Platform Invoke Examples</span></span>](../../../framework/interop/platform-invoke-examples.md)  
 [<span data-ttu-id="2d1be-120">Consumindo funções de DLL não gerenciadas</span><span class="sxs-lookup"><span data-stu-id="2d1be-120">Consuming Unmanaged DLL Functions</span></span>](../../../framework/interop/consuming-unmanaged-dll-functions.md)  
 [<span data-ttu-id="2d1be-121">Emissão de definição de um método com reflexão</span><span class="sxs-lookup"><span data-stu-id="2d1be-121">Defining a Method with Reflection Emit</span></span>](http://msdn.microsoft.com/en-us/84fd3bf6-628f-41aa-83d9-b990cf926e81)  
 [<span data-ttu-id="2d1be-122">Instruções passo a passo: chamando APIs do Windows</span><span class="sxs-lookup"><span data-stu-id="2d1be-122">Walkthrough: Calling Windows APIs</span></span>](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md)  
 [<span data-ttu-id="2d1be-123">Interoperabilidade COM</span><span class="sxs-lookup"><span data-stu-id="2d1be-123">COM Interop</span></span>](../../../visual-basic/programming-guide/com-interop/index.md)
