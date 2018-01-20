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
ms.openlocfilehash: 772db789fba4552a4645d2c6a242ba01944652ee
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-call-windows-apis-visual-basic"></a><span data-ttu-id="21412-102">Como chamar APIs do Windows (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="21412-102">How to: Call Windows APIs (Visual Basic)</span></span>
<span data-ttu-id="21412-103">Este exemplo define e chama o `MessageBox` função na User32. dll e, em seguida, passa uma cadeia de caracteres para ele.</span><span class="sxs-lookup"><span data-stu-id="21412-103">This example defines and calls the `MessageBox` function in user32.dll and then passes a string to it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="21412-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="21412-104">Example</span></span>  
 [!code-vb[VbVbalrInterop#1](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/how-to-call-windows-apis_1.vb)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="21412-105">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="21412-105">Compiling the Code</span></span>  
 <span data-ttu-id="21412-106">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="21412-106">This example requires:</span></span>  
  
-   <span data-ttu-id="21412-107">Uma referência para o <xref:System> namespace.</span><span class="sxs-lookup"><span data-stu-id="21412-107">A reference to the <xref:System> namespace.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="21412-108">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="21412-108">Robust Programming</span></span>  
 <span data-ttu-id="21412-109">As seguintes condições podem causar uma exceção:</span><span class="sxs-lookup"><span data-stu-id="21412-109">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="21412-110">O método não é estático, é abstrato ou foi definido anteriormente.</span><span class="sxs-lookup"><span data-stu-id="21412-110">The method is not static, is abstract, or has been previously defined.</span></span> <span data-ttu-id="21412-111">O tipo pai é uma interface ou o comprimento de *nome* ou *Nomedadll* é zero.</span><span class="sxs-lookup"><span data-stu-id="21412-111">The parent type is an interface, or the length of *name* or *dllName* is zero.</span></span> <span data-ttu-id="21412-112">(<xref:System.ArgumentException>)</span><span class="sxs-lookup"><span data-stu-id="21412-112">(<xref:System.ArgumentException>)</span></span>  
  
-   <span data-ttu-id="21412-113">O *nome* ou *Nomedadll* é `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="21412-113">The *name* or *dllName* is `Nothing`.</span></span> <span data-ttu-id="21412-114">(<xref:System.ArgumentNullException>)</span><span class="sxs-lookup"><span data-stu-id="21412-114">(<xref:System.ArgumentNullException>)</span></span>  
  
-   <span data-ttu-id="21412-115">O tipo recipiente foi criado anteriormente usando `CreateType`.</span><span class="sxs-lookup"><span data-stu-id="21412-115">The containing type has been previously created using `CreateType`.</span></span> <span data-ttu-id="21412-116">(<xref:System.InvalidOperationException>)</span><span class="sxs-lookup"><span data-stu-id="21412-116">(<xref:System.InvalidOperationException>)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21412-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="21412-117">See Also</span></span>  
 [<span data-ttu-id="21412-118">Invocação de plataforma examinar mais detalhadamente</span><span class="sxs-lookup"><span data-stu-id="21412-118">A Closer Look at Platform Invoke</span></span>](http://msdn.microsoft.com/library/ba9dd55b-2eaa-45cd-8afd-75cb8d64d243)  
 [<span data-ttu-id="21412-119">Exemplos de invocação de plataforma</span><span class="sxs-lookup"><span data-stu-id="21412-119">Platform Invoke Examples</span></span>](../../../framework/interop/platform-invoke-examples.md)  
 [<span data-ttu-id="21412-120">Consumindo funções de DLL não gerenciadas</span><span class="sxs-lookup"><span data-stu-id="21412-120">Consuming Unmanaged DLL Functions</span></span>](../../../framework/interop/consuming-unmanaged-dll-functions.md)  
 [<span data-ttu-id="21412-121">Emissão de definição de um método com reflexão</span><span class="sxs-lookup"><span data-stu-id="21412-121">Defining a Method with Reflection Emit</span></span>](http://msdn.microsoft.com/library/84fd3bf6-628f-41aa-83d9-b990cf926e81)  
 [<span data-ttu-id="21412-122">Instruções passo a passo: chamando APIs do Windows</span><span class="sxs-lookup"><span data-stu-id="21412-122">Walkthrough: Calling Windows APIs</span></span>](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md)  
 [<span data-ttu-id="21412-123">Interoperabilidade COM</span><span class="sxs-lookup"><span data-stu-id="21412-123">COM Interop</span></span>](../../../visual-basic/programming-guide/com-interop/index.md)
