---
title: "Este aplicativo de instância única não pôde se conectar à instância original"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrAppModel_SingleInstanceCantConnect
ms.assetid: 7c2c0cee-02a1-4157-be03-39d18e18408f
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: fbc8458231c36f3af9ca4de524e01e19a162ee47
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="this-single-instance-application-could-not-connect-to-the-original-instance"></a><span data-ttu-id="6ef6d-102">Este aplicativo de instância única não pôde se conectar à instância original</span><span class="sxs-lookup"><span data-stu-id="6ef6d-102">This single-instance application could not connect to the original instance</span></span>
<span data-ttu-id="6ef6d-103">Este aplicativo de instância única não pôde se conectar à instância original.</span><span class="sxs-lookup"><span data-stu-id="6ef6d-103">This single-instance application could not connect to the original instance.</span></span> <span data-ttu-id="6ef6d-104">Algumas das possíveis causas para esse problema são as seguintes:</span><span class="sxs-lookup"><span data-stu-id="6ef6d-104">Some of the possible causes for this problem are as follows:</span></span>  
  
-   <span data-ttu-id="6ef6d-105">A instância original parou de responder.</span><span class="sxs-lookup"><span data-stu-id="6ef6d-105">The original instance stopped responding.</span></span>  
  
-   <span data-ttu-id="6ef6d-106">O aplicativo não tem permissões para criar objetos kernel.</span><span class="sxs-lookup"><span data-stu-id="6ef6d-106">The application does not have permissions to create kernel objects.</span></span> <span data-ttu-id="6ef6d-107">Para obter mais informações sobre objetos de kernel, consulte [Mutexes](../../standard/threading/mutexes.md).</span><span class="sxs-lookup"><span data-stu-id="6ef6d-107">For more information about kernel objects, see [Mutexes](../../standard/threading/mutexes.md).</span></span>  
  
     <span data-ttu-id="6ef6d-108">O nome de base para os objetos kernel vem da concatenação do GUID do assembly, número da versão principal e número da versão secundária.</span><span class="sxs-lookup"><span data-stu-id="6ef6d-108">The base name for the kernel objects comes from concatenating the assembly's GUID, major version number, and minor version number.</span></span> <span data-ttu-id="6ef6d-109">Por exemplo, o nome de base poderia ser `3639f15d-9547-43da-8145-60da347829915.1`.</span><span class="sxs-lookup"><span data-stu-id="6ef6d-109">For example, the base name could be `3639f15d-9547-43da-8145-60da347829915.1`.</span></span>  
  
## <a name="to-correct-this-error-when-developing-the-application"></a><span data-ttu-id="6ef6d-110">Para corrigir esse erro durante o desenvolvimento de aplicativo</span><span class="sxs-lookup"><span data-stu-id="6ef6d-110">To correct this error when developing the application</span></span>  
  
1.  <span data-ttu-id="6ef6d-111">Verifique se o aplicativo não entrar em um estado sem resposta.</span><span class="sxs-lookup"><span data-stu-id="6ef6d-111">Check that the application does not go into an unresponsive state.</span></span>  
  
2.  <span data-ttu-id="6ef6d-112">Verifique se o aplicativo tem permissões suficientes para criar objetos de kernel.</span><span class="sxs-lookup"><span data-stu-id="6ef6d-112">Check that the application has sufficient permissions to create kernel objects.</span></span>  
  
3.  <span data-ttu-id="6ef6d-113">Reinicie a instância original do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="6ef6d-113">Restart the original instance of the application.</span></span>  
  
4.  <span data-ttu-id="6ef6d-114">Reinicie o computador para limpar qualquer processo que possam estar usando o recurso que é necessário para se conectar ao aplicativo da instância original.</span><span class="sxs-lookup"><span data-stu-id="6ef6d-114">Restart the computer to clear any process that may be using the resource that is required to connect to the original instance application.</span></span>  
  
5.  <span data-ttu-id="6ef6d-115">Observe as circunstâncias nas quais o erro ocorreu e telefone Microsoft Product Support Services.</span><span class="sxs-lookup"><span data-stu-id="6ef6d-115">Note the circumstances under which the error occurred, and telephone Microsoft Product Support Services.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ef6d-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6ef6d-116">See Also</span></span>  
 [<span data-ttu-id="6ef6d-117">NIB: Como: Especificar comportamento de instâncias de um aplicativo (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6ef6d-117">NIB: How to: Specify Instancing Behavior for an Application (Visual Basic)</span></span>](http://msdn.microsoft.com/en-us/48539ad8-d960-4210-beab-ee65f6c6dc6e)  
 [<span data-ttu-id="6ef6d-118">Noções básicas do depurador</span><span class="sxs-lookup"><span data-stu-id="6ef6d-118">Debugger Basics</span></span>](/visualstudio/debugger/debugger-basics)  
 [<span data-ttu-id="6ef6d-119">PAVEOVER suporte de produto e acessibilidade</span><span class="sxs-lookup"><span data-stu-id="6ef6d-119">PAVEOVER Product Support and Accessibility</span></span>](http://msdn.microsoft.com/en-us/14e1d293-7b6d-40a6-bf3e-a92f8ee6c88c)
