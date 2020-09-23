---
title: Este aplicativo de instância única não pôde se conectar à instância original
ms.date: 07/20/2015
f1_keywords:
- vbrAppModel_SingleInstanceCantConnect
ms.assetid: 7c2c0cee-02a1-4157-be03-39d18e18408f
ms.openlocfilehash: 8e2caa158c3874d216671979430a03b11bf60066
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91095675"
---
# <a name="this-single-instance-application-could-not-connect-to-the-original-instance"></a><span data-ttu-id="b4352-102">Este aplicativo de instância única não pôde se conectar à instância original</span><span class="sxs-lookup"><span data-stu-id="b4352-102">This single-instance application could not connect to the original instance</span></span>

<span data-ttu-id="b4352-103">Este aplicativo de instância única não pôde se conectar à instância original.</span><span class="sxs-lookup"><span data-stu-id="b4352-103">This single-instance application could not connect to the original instance.</span></span> <span data-ttu-id="b4352-104">Algumas das possíveis causas para esse problema são as seguintes:</span><span class="sxs-lookup"><span data-stu-id="b4352-104">Some of the possible causes for this problem are as follows:</span></span>  
  
- <span data-ttu-id="b4352-105">A instância original parou de responder.</span><span class="sxs-lookup"><span data-stu-id="b4352-105">The original instance stopped responding.</span></span>  
  
- <span data-ttu-id="b4352-106">O aplicativo não tem permissões para criar objetos kernel.</span><span class="sxs-lookup"><span data-stu-id="b4352-106">The application does not have permissions to create kernel objects.</span></span> <span data-ttu-id="b4352-107">Para obter mais informações sobre objetos kernel, consulte [mutexes](../../standard/threading/mutexes.md).</span><span class="sxs-lookup"><span data-stu-id="b4352-107">For more information about kernel objects, see [Mutexes](../../standard/threading/mutexes.md).</span></span>  
  
     <span data-ttu-id="b4352-108">O nome de base para os objetos kernel vem da concatenação do GUID do assembly, número da versão principal e número da versão secundária.</span><span class="sxs-lookup"><span data-stu-id="b4352-108">The base name for the kernel objects comes from concatenating the assembly's GUID, major version number, and minor version number.</span></span> <span data-ttu-id="b4352-109">Por exemplo, o nome de base pode ser `3639f15d-9547-43da-8145-60da347829915.1` .</span><span class="sxs-lookup"><span data-stu-id="b4352-109">For example, the base name could be `3639f15d-9547-43da-8145-60da347829915.1`.</span></span>  
  
## <a name="to-correct-this-error-when-developing-the-application"></a><span data-ttu-id="b4352-110">Para corrigir esse erro ao desenvolver o aplicativo</span><span class="sxs-lookup"><span data-stu-id="b4352-110">To correct this error when developing the application</span></span>  
  
1. <span data-ttu-id="b4352-111">Verifique se o aplicativo não entra em um estado sem resposta.</span><span class="sxs-lookup"><span data-stu-id="b4352-111">Check that the application does not go into an unresponsive state.</span></span>  
  
2. <span data-ttu-id="b4352-112">Verifique se o aplicativo tem permissões suficientes para criar objetos kernel.</span><span class="sxs-lookup"><span data-stu-id="b4352-112">Check that the application has sufficient permissions to create kernel objects.</span></span>  
  
3. <span data-ttu-id="b4352-113">Reinicie a instância original do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b4352-113">Restart the original instance of the application.</span></span>  
  
4. <span data-ttu-id="b4352-114">Reinicie o computador para limpar qualquer processo que possa estar usando o recurso necessário para se conectar ao aplicativo de instância original.</span><span class="sxs-lookup"><span data-stu-id="b4352-114">Restart the computer to clear any process that may be using the resource that is required to connect to the original instance application.</span></span>  
  
5. <span data-ttu-id="b4352-115">Observe as circunstâncias em que o erro ocorreu e telefone para o atendimento Microsoft.</span><span class="sxs-lookup"><span data-stu-id="b4352-115">Note the circumstances under which the error occurred, and telephone Microsoft Product Support Services.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4352-116">Confira também</span><span class="sxs-lookup"><span data-stu-id="b4352-116">See also</span></span>

- [<span data-ttu-id="b4352-117">Noções básicas do depurador</span><span class="sxs-lookup"><span data-stu-id="b4352-117">Debugger Basics</span></span>](/visualstudio/debugger/debugger-feature-tour)
