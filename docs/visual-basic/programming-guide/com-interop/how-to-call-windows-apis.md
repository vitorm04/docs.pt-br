---
title: 'Como: chamar APIs do Windows (Visual Basic) | Documentos do Microsoft'
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- API calls
- Windows API, calling
- API calls, platform invoke
- calls, stored procedures
ms.assetid: 27d75f0a-54ab-4ee1-b91d-43513a19b12d
caps.latest.revision: 14
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 8070ef07392b747776b86a9d922e3e0e7115080e
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-call-windows-apis-visual-basic"></a><span data-ttu-id="44e8f-102">Como chamar APIs do Windows (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="44e8f-102">How to: Call Windows APIs (Visual Basic)</span></span>
<span data-ttu-id="44e8f-103">Este exemplo define e chama o `MessageBox` função na User32. dll e, em seguida, passa uma cadeia de caracteres para ele.</span><span class="sxs-lookup"><span data-stu-id="44e8f-103">This example defines and calls the `MessageBox` function in user32.dll and then passes a string to it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="44e8f-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="44e8f-104">Example</span></span>  
 <span data-ttu-id="44e8f-105">[!code-vb[VbVbalrInterop n º&1;](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/how-to-call-windows-apis_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="44e8f-105">[!code-vb[VbVbalrInterop#1](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/how-to-call-windows-apis_1.vb)]</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="44e8f-106">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="44e8f-106">Compiling the Code</span></span>  
 <span data-ttu-id="44e8f-107">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="44e8f-107">This example requires:</span></span>  
  
-   <span data-ttu-id="44e8f-108">Uma referência para o <xref:System>namespace.</xref:System></span><span class="sxs-lookup"><span data-stu-id="44e8f-108">A reference to the <xref:System> namespace.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="44e8f-109">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="44e8f-109">Robust Programming</span></span>  
 <span data-ttu-id="44e8f-110">As seguintes condições podem causar uma exceção:</span><span class="sxs-lookup"><span data-stu-id="44e8f-110">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="44e8f-111">O método não é estático, é abstrato ou foi definido anteriormente.</span><span class="sxs-lookup"><span data-stu-id="44e8f-111">The method is not static, is abstract, or has been previously defined.</span></span> <span data-ttu-id="44e8f-112">O tipo pai é uma interface, ou o comprimento de *nome* ou *dllName* é zero.</span><span class="sxs-lookup"><span data-stu-id="44e8f-112">The parent type is an interface, or the length of *name* or *dllName* is zero.</span></span> <span data-ttu-id="44e8f-113">(<xref:System.ArgumentException>)</xref:System.ArgumentException></span><span class="sxs-lookup"><span data-stu-id="44e8f-113">(<xref:System.ArgumentException>)</span></span>  
  
-   <span data-ttu-id="44e8f-114">The *name* or *dllName* is `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="44e8f-114">The *name* or *dllName* is `Nothing`.</span></span> <span data-ttu-id="44e8f-115">(<xref:System.ArgumentNullException>)</xref:System.ArgumentNullException></span><span class="sxs-lookup"><span data-stu-id="44e8f-115">(<xref:System.ArgumentNullException>)</span></span>  
  
-   <span data-ttu-id="44e8f-116">O tipo recipiente foi criado anteriormente usando `CreateType`.</span><span class="sxs-lookup"><span data-stu-id="44e8f-116">The containing type has been previously created using `CreateType`.</span></span> <span data-ttu-id="44e8f-117">(<xref:System.InvalidOperationException>)</xref:System.InvalidOperationException></span><span class="sxs-lookup"><span data-stu-id="44e8f-117">(<xref:System.InvalidOperationException>)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44e8f-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="44e8f-118">See Also</span></span>  
 <span data-ttu-id="44e8f-119">[Invocação de plataforma examinar mais de perto](http://msdn.microsoft.com/en-us/ba9dd55b-2eaa-45cd-8afd-75cb8d64d243) </span><span class="sxs-lookup"><span data-stu-id="44e8f-119">[A Closer Look at Platform Invoke](http://msdn.microsoft.com/en-us/ba9dd55b-2eaa-45cd-8afd-75cb8d64d243) </span></span>  
<span data-ttu-id="44e8f-120"> [Exemplos de invocação de plataforma](http://msdn.microsoft.com/library/15926806-f0b7-487e-93a6-4e9367ec689f) </span><span class="sxs-lookup"><span data-stu-id="44e8f-120"> [Platform Invoke Examples](http://msdn.microsoft.com/library/15926806-f0b7-487e-93a6-4e9367ec689f) </span></span>  
<span data-ttu-id="44e8f-121"> [Consumindo funções de DLL não gerenciada](http://msdn.microsoft.com/library/eca7606e-ebfb-4f47-b8d9-289903fdc045) </span><span class="sxs-lookup"><span data-stu-id="44e8f-121"> [Consuming Unmanaged DLL Functions](http://msdn.microsoft.com/library/eca7606e-ebfb-4f47-b8d9-289903fdc045) </span></span>  
<span data-ttu-id="44e8f-122"> [Definindo um método com reflexão emissão](http://msdn.microsoft.com/en-us/84fd3bf6-628f-41aa-83d9-b990cf926e81) </span><span class="sxs-lookup"><span data-stu-id="44e8f-122"> [Defining a Method with Reflection Emit](http://msdn.microsoft.com/en-us/84fd3bf6-628f-41aa-83d9-b990cf926e81) </span></span>  
<span data-ttu-id="44e8f-123"> [Passo a passo: Chamando APIs do Windows](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md) </span><span class="sxs-lookup"><span data-stu-id="44e8f-123"> [Walkthrough: Calling Windows APIs](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md) </span></span>  
<span data-ttu-id="44e8f-124"> [Interoperabilidade COM](../../../visual-basic/programming-guide/com-interop/index.md)</span><span class="sxs-lookup"><span data-stu-id="44e8f-124"> [COM Interop](../../../visual-basic/programming-guide/com-interop/index.md)</span></span>
