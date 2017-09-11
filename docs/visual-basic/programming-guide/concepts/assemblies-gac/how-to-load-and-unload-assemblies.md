---
title: 'Como: carregar e descarregar Assemblies (Visual Basic) | Documentos do Microsoft'
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: bbc84236-04b6-4c1b-9672-52773f65a5dc
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 2e38be72bb58573b532fa42a569563df0be8301d
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-load-and-unload-assemblies-visual-basic"></a><span data-ttu-id="9f564-102">Como: carregar e descarregar Assemblies (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9f564-102">How to: Load and Unload Assemblies (Visual Basic)</span></span>
<span data-ttu-id="9f564-103">Os assemblies referenciados pelo seu programa será automaticamente carregados no momento da compilação, mas também é possível carregar assemblies específicos no domínio de aplicativo em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="9f564-103">The assemblies referenced by your program will automatically be loaded at build time, but it is also possible to load specific assemblies into the current application domain at runtime.</span></span> <span data-ttu-id="9f564-104">Para obter mais informações, consulte [como: carregar Assemblies em um domínio de aplicativo](http://msdn.microsoft.com/library/1432aa2d-bd83-4346-bf3b-a1b7920e2aa9).</span><span class="sxs-lookup"><span data-stu-id="9f564-104">For more information, see [How to: Load Assemblies into an Application Domain](http://msdn.microsoft.com/library/1432aa2d-bd83-4346-bf3b-a1b7920e2aa9).</span></span>  
  
 <span data-ttu-id="9f564-105">Não há nenhuma maneira de descarregar um assembly individual sem descarregar todos os domínios de aplicativo que contêm-lo.</span><span class="sxs-lookup"><span data-stu-id="9f564-105">There is no way to unload an individual assembly without unloading all of the application domains that contain it.</span></span> <span data-ttu-id="9f564-106">Mesmo se o assembly sai do escopo, o arquivo de assembly real permanecerá carregado até que todos os domínios de aplicativo que contenham sejam descarregados.</span><span class="sxs-lookup"><span data-stu-id="9f564-106">Even if the assembly goes out of scope, the actual assembly file will remain loaded until all application domains that contain it are unloaded.</span></span>  
  
 <span data-ttu-id="9f564-107">Se você quiser descarregar alguns módulos (assemblies), mas outros não, considere criando um novo domínio de aplicativo, executar o código dentro desse domínio e, em seguida, o descarregamento desse domínio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="9f564-107">If you want to unload some assemblies but not others, consider creating a new application domain, executing the code inside that domain, and then unloading that application domain.</span></span> <span data-ttu-id="9f564-108">Para obter mais informações, consulte [como: descarregar um domínio de aplicativo](http://msdn.microsoft.com/library/f356116d-e415-4f7c-a332-6e6a60227192).</span><span class="sxs-lookup"><span data-stu-id="9f564-108">For more information, see [How to: Unload an Application Domain](http://msdn.microsoft.com/library/f356116d-e415-4f7c-a332-6e6a60227192).</span></span>  
  
### <a name="to-load-an-assembly-into-an-application-domain"></a><span data-ttu-id="9f564-109">Para carregar um assembly em um domínio de aplicativo</span><span class="sxs-lookup"><span data-stu-id="9f564-109">To load an assembly into an application domain</span></span>  
  
1.  <span data-ttu-id="9f564-110">Use um dos vários métodos de carregamento contidos em classes <xref:System.AppDomain>e <xref:System.Reflection>.</xref:System.Reflection> </xref:System.AppDomain></span><span class="sxs-lookup"><span data-stu-id="9f564-110">Use one of the several load methods contained in the classes <xref:System.AppDomain> and <xref:System.Reflection>.</span></span> <span data-ttu-id="9f564-111">Para obter mais informações, consulte [como: carregar Assemblies em um domínio de aplicativo](http://msdn.microsoft.com/library/1432aa2d-bd83-4346-bf3b-a1b7920e2aa9).</span><span class="sxs-lookup"><span data-stu-id="9f564-111">For more information, see [How to: Load Assemblies into an Application Domain](http://msdn.microsoft.com/library/1432aa2d-bd83-4346-bf3b-a1b7920e2aa9).</span></span>  
  
### <a name="to-unload-an-application-domain"></a><span data-ttu-id="9f564-112">Descarregar um domínio de aplicativo</span><span class="sxs-lookup"><span data-stu-id="9f564-112">To unload an application domain</span></span>  
  
1.  <span data-ttu-id="9f564-113">Não há nenhuma maneira de descarregar um assembly individual sem descarregar todos os domínios de aplicativo que contêm-lo.</span><span class="sxs-lookup"><span data-stu-id="9f564-113">There is no way to unload an individual assembly without unloading all of the application domains that contain it.</span></span> <span data-ttu-id="9f564-114">Use o `Unload` método <xref:System.AppDomain>descarregar os domínios de aplicativo.</xref:System.AppDomain></span><span class="sxs-lookup"><span data-stu-id="9f564-114">Use the `Unload` method from <xref:System.AppDomain> to unload the application domains.</span></span> <span data-ttu-id="9f564-115">Para obter mais informações, consulte [como: descarregar um domínio de aplicativo](http://msdn.microsoft.com/library/f356116d-e415-4f7c-a332-6e6a60227192).</span><span class="sxs-lookup"><span data-stu-id="9f564-115">For more information, see [How to: Unload an Application Domain](http://msdn.microsoft.com/library/f356116d-e415-4f7c-a332-6e6a60227192).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f564-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9f564-116">See Also</span></span>  
 <span data-ttu-id="9f564-117">[Conceitos de programação](../../../../visual-basic/programming-guide/concepts/index.md) </span><span class="sxs-lookup"><span data-stu-id="9f564-117">[Programming Concepts](../../../../visual-basic/programming-guide/concepts/index.md) </span></span>  
<span data-ttu-id="9f564-118"> [Assemblies e o Cache de Assembly Global (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md) </span><span class="sxs-lookup"><span data-stu-id="9f564-118"> [Assemblies and the Global Assembly Cache (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md) </span></span>  
<span data-ttu-id="9f564-119"> [Como: carregar Assemblies em um domínio de aplicativo](http://msdn.microsoft.com/library/1432aa2d-bd83-4346-bf3b-a1b7920e2aa9)</span><span class="sxs-lookup"><span data-stu-id="9f564-119"> [How to: Load Assemblies into an Application Domain](http://msdn.microsoft.com/library/1432aa2d-bd83-4346-bf3b-a1b7920e2aa9)</span></span>
