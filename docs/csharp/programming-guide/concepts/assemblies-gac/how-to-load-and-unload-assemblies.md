---
title: Como carregar e descarregar assemblies (C#)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 6a4f490f-3576-471f-9533-003737cad4a3
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: e4b7c9e257a1fff6236770ff39f5d26cd97224b6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-load-and-unload-assemblies-c"></a><span data-ttu-id="2851d-102">Como carregar e descarregar assemblies (C#)</span><span class="sxs-lookup"><span data-stu-id="2851d-102">How to: Load and Unload Assemblies (C#)</span></span>
<span data-ttu-id="2851d-103">Os assemblies referenciados pelo seu programa serão automaticamente carregados e tempo de build, mas também é possível carregar assemblies específicos no domínio do aplicativo atual em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="2851d-103">The assemblies referenced by your program will automatically be loaded at build time, but it is also possible to load specific assemblies into the current application domain at runtime.</span></span> <span data-ttu-id="2851d-104">Para obter mais informações, consulte [Como carregar assemblies em um domínio do aplicativo](../../../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md).</span><span class="sxs-lookup"><span data-stu-id="2851d-104">For more information, see [How to: Load Assemblies into an Application Domain](../../../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md).</span></span>  
  
 <span data-ttu-id="2851d-105">Não há nenhuma maneira de descarregar um assembly individual sem descarregar todos os domínios de aplicativo que o contêm.</span><span class="sxs-lookup"><span data-stu-id="2851d-105">There is no way to unload an individual assembly without unloading all of the application domains that contain it.</span></span> <span data-ttu-id="2851d-106">Mesmo se o assembly sair do escopo, o arquivo do assembly real permanecerá carregado até que todos os domínios do aplicativo que o contenham sejam descarregados.</span><span class="sxs-lookup"><span data-stu-id="2851d-106">Even if the assembly goes out of scope, the actual assembly file will remain loaded until all application domains that contain it are unloaded.</span></span>  
  
 <span data-ttu-id="2851d-107">Se você quiser descarregar alguns assemblies, mas não outros, considere criar um novo domínio do aplicativo, executando o código dentro desse domínio e descarregando esse domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="2851d-107">If you want to unload some assemblies but not others, consider creating a new application domain, executing the code inside that domain, and then unloading that application domain.</span></span> <span data-ttu-id="2851d-108">Para obter mais informações, consulte [Como descarregar um domínio de aplicativo](../../../../framework/app-domains/how-to-unload-an-application-domain.md).</span><span class="sxs-lookup"><span data-stu-id="2851d-108">For more information, see [How to: Unload an Application Domain](../../../../framework/app-domains/how-to-unload-an-application-domain.md).</span></span>  
  
### <a name="to-load-an-assembly-into-an-application-domain"></a><span data-ttu-id="2851d-109">Para carregar um assembly em um domínio de aplicativo</span><span class="sxs-lookup"><span data-stu-id="2851d-109">To load an assembly into an application domain</span></span>  
  
1.  <span data-ttu-id="2851d-110">Use um dos vários métodos de carga contidos nas classes <xref:System.AppDomain> e <xref:System.Reflection>.</span><span class="sxs-lookup"><span data-stu-id="2851d-110">Use one of the several load methods contained in the classes <xref:System.AppDomain> and <xref:System.Reflection>.</span></span> <span data-ttu-id="2851d-111">Para obter mais informações, consulte [Como carregar assemblies em um domínio do aplicativo](../../../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md).</span><span class="sxs-lookup"><span data-stu-id="2851d-111">For more information, see [How to: Load Assemblies into an Application Domain](../../../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md).</span></span>  
  
### <a name="to-unload-an-application-domain"></a><span data-ttu-id="2851d-112">Para descarregar um domínio de aplicativo</span><span class="sxs-lookup"><span data-stu-id="2851d-112">To unload an application domain</span></span>  
  
1.  <span data-ttu-id="2851d-113">Não há nenhuma maneira de descarregar um assembly individual sem descarregar todos os domínios de aplicativo que o contêm.</span><span class="sxs-lookup"><span data-stu-id="2851d-113">There is no way to unload an individual assembly without unloading all of the application domains that contain it.</span></span> <span data-ttu-id="2851d-114">Use o método `Unload` de <xref:System.AppDomain> para descarregar os domínios de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="2851d-114">Use the `Unload` method from <xref:System.AppDomain> to unload the application domains.</span></span> <span data-ttu-id="2851d-115">Para obter mais informações, consulte [Como descarregar um domínio de aplicativo](../../../../framework/app-domains/how-to-unload-an-application-domain.md).</span><span class="sxs-lookup"><span data-stu-id="2851d-115">For more information, see [How to: Unload an Application Domain](../../../../framework/app-domains/how-to-unload-an-application-domain.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2851d-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2851d-116">See Also</span></span>  
 [<span data-ttu-id="2851d-117">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="2851d-117">C# Programming Guide</span></span>](../../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="2851d-118">Assemblies e o Cache de Assembly Global (C#)</span><span class="sxs-lookup"><span data-stu-id="2851d-118">Assemblies and the Global Assembly Cache (C#)</span></span>](../../../../csharp/programming-guide/concepts/assemblies-gac/index.md)  
 [<span data-ttu-id="2851d-119">Como carregar assemblies em um domínio do aplicativo</span><span class="sxs-lookup"><span data-stu-id="2851d-119">How to: Load Assemblies into an Application Domain</span></span>](../../../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md)
