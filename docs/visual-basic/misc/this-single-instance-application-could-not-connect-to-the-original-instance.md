---
title: "Este aplicativo de instância única não pôde se conectar à instância original | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrAppModel_SingleInstanceCantConnect
ms.assetid: 7c2c0cee-02a1-4157-be03-39d18e18408f
caps.latest.revision: 12
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 113923e7cb72d1da0a8fb289f29e9afa60dda558
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="this-single-instance-application-could-not-connect-to-the-original-instance"></a><span data-ttu-id="08ff5-102">Este aplicativo de instância única não pôde se conectar à instância original</span><span class="sxs-lookup"><span data-stu-id="08ff5-102">This single-instance application could not connect to the original instance</span></span>
<span data-ttu-id="08ff5-103">Este aplicativo de instância única não pôde se conectar à instância original.</span><span class="sxs-lookup"><span data-stu-id="08ff5-103">This single-instance application could not connect to the original instance.</span></span> <span data-ttu-id="08ff5-104">Algumas das possíveis causas para esse problema são as seguintes:</span><span class="sxs-lookup"><span data-stu-id="08ff5-104">Some of the possible causes for this problem are as follows:</span></span>  
  
-   <span data-ttu-id="08ff5-105">A instância original parou de responder.</span><span class="sxs-lookup"><span data-stu-id="08ff5-105">The original instance stopped responding.</span></span>  
  
-   <span data-ttu-id="08ff5-106">O aplicativo não tem permissões para criar objetos kernel.</span><span class="sxs-lookup"><span data-stu-id="08ff5-106">The application does not have permissions to create kernel objects.</span></span> <span data-ttu-id="08ff5-107">Para obter mais informações sobre objetos kernel, consulte [Mutexes](http://msdn.microsoft.com/library/9dd06e25-12c0-4a9e-855a-452dc83803e2).</span><span class="sxs-lookup"><span data-stu-id="08ff5-107">For more information about kernel objects, see [Mutexes](http://msdn.microsoft.com/library/9dd06e25-12c0-4a9e-855a-452dc83803e2).</span></span>  
  
     <span data-ttu-id="08ff5-108">O nome de base para os objetos kernel vem da concatenação do GUID do assembly, número da versão principal e número da versão secundária.</span><span class="sxs-lookup"><span data-stu-id="08ff5-108">The base name for the kernel objects comes from concatenating the assembly's GUID, major version number, and minor version number.</span></span> <span data-ttu-id="08ff5-109">Por exemplo, o nome de base poderia ser `3639f15d-9547-43da-8145-60da347829915.1`.</span><span class="sxs-lookup"><span data-stu-id="08ff5-109">For example, the base name could be `3639f15d-9547-43da-8145-60da347829915.1`.</span></span>  
  
## <a name="to-correct-this-error-when-developing-the-application"></a><span data-ttu-id="08ff5-110">Para corrigir esse erro ao desenvolver o aplicativo</span><span class="sxs-lookup"><span data-stu-id="08ff5-110">To correct this error when developing the application</span></span>  
  
1.  <span data-ttu-id="08ff5-111">Verifique se o aplicativo não entra em um estado sem resposta.</span><span class="sxs-lookup"><span data-stu-id="08ff5-111">Check that the application does not go into an unresponsive state.</span></span>  
  
2.  <span data-ttu-id="08ff5-112">Verifique se o aplicativo tem permissões suficientes para criar objetos kernel.</span><span class="sxs-lookup"><span data-stu-id="08ff5-112">Check that the application has sufficient permissions to create kernel objects.</span></span>  
  
3.  <span data-ttu-id="08ff5-113">Reinicie a instância original do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="08ff5-113">Restart the original instance of the application.</span></span>  
  
4.  <span data-ttu-id="08ff5-114">Reinicie o computador para limpar qualquer processo que possa estar usando o recurso que é necessário para se conectar ao aplicativo da instância original.</span><span class="sxs-lookup"><span data-stu-id="08ff5-114">Restart the computer to clear any process that may be using the resource that is required to connect to the original instance application.</span></span>  
  
5.  <span data-ttu-id="08ff5-115">Observe as circunstâncias nas quais o erro ocorreu e telefone o Atendimento Microsoft.</span><span class="sxs-lookup"><span data-stu-id="08ff5-115">Note the circumstances under which the error occurred, and telephone Microsoft Product Support Services.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08ff5-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="08ff5-116">See Also</span></span>  
 <span data-ttu-id="08ff5-117">[NIB: Como: Especificar comportamento de instâncias para um aplicativo (Visual Basic)](http://msdn.microsoft.com/en-us/48539ad8-d960-4210-beab-ee65f6c6dc6e) </span><span class="sxs-lookup"><span data-stu-id="08ff5-117">[NIB: How to: Specify Instancing Behavior for an Application (Visual Basic)](http://msdn.microsoft.com/en-us/48539ad8-d960-4210-beab-ee65f6c6dc6e) </span></span>  
<span data-ttu-id="08ff5-118"> [Noções básicas do depurador](https://docs.microsoft.com/visualstudio/debugger/debugger-basics) </span><span class="sxs-lookup"><span data-stu-id="08ff5-118"> [Debugger Basics](https://docs.microsoft.com/visualstudio/debugger/debugger-basics) </span></span>  
<span data-ttu-id="08ff5-119"> [Acessibilidade e suporte a produtos PAVEOVER](http://msdn.microsoft.com/en-us/14e1d293-7b6d-40a6-bf3e-a92f8ee6c88c)</span><span class="sxs-lookup"><span data-stu-id="08ff5-119"> [PAVEOVER Product Support and Accessibility](http://msdn.microsoft.com/en-us/14e1d293-7b6d-40a6-bf3e-a92f8ee6c88c)</span></span>
