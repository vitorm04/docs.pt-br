---
title: Interoperabilidade COM em aplicativos .NET Framework (Visual Basic)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- interoperability, COM and .NET framework objects
- COM interop [Visual Basic]
- shared components
ms.assetid: f5a72143-c268-4dff-a019-974ad940e17d
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d9347f7771e0e86f9a19cbec94ef59dcf1bdb250
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2017
---
# <a name="com-interoperability-in-net-framework-applications-visual-basic"></a><span data-ttu-id="43b60-102">Interoperabilidade COM em aplicativos .NET Framework (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="43b60-102">COM Interoperability in .NET Framework Applications (Visual Basic)</span></span>
<span data-ttu-id="43b60-103">Quando você quiser usar objetos COM e objetos do .NET Framework no mesmo aplicativo, você deve considerar as diferenças em como os objetos existem na memória.</span><span class="sxs-lookup"><span data-stu-id="43b60-103">When you want to use COM objects and .NET Framework objects in the same application, you need to address the differences in how the objects exist in memory.</span></span> <span data-ttu-id="43b60-104">Um objeto do .NET Framework está localizado na memória gerenciada — memória controlada pelo common language runtime — e podem ser movidos pelo tempo de execução, conforme necessário.</span><span class="sxs-lookup"><span data-stu-id="43b60-104">A .NET Framework object is located in managed memory—the memory controlled by the common language runtime—and may be moved by the runtime as needed.</span></span> <span data-ttu-id="43b60-105">Um objeto COM está localizado na memória não gerenciada e não é esperado para mover para outro local de memória.</span><span class="sxs-lookup"><span data-stu-id="43b60-105">A COM object is located in unmanaged memory and is not expected to move to another memory location.</span></span> [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)]<span data-ttu-id="43b60-106">e o [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] fornecem ferramentas para controlar a interação entre eles gerenciados e componentes.</span><span class="sxs-lookup"><span data-stu-id="43b60-106"> and the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] provide tools to control the interaction of these managed and unmanaged components.</span></span> <span data-ttu-id="43b60-107">Para obter mais informações sobre o código gerenciado, consulte [Common Language Runtime](../../../standard/clr.md).</span><span class="sxs-lookup"><span data-stu-id="43b60-107">For more information about managed code, see [Common Language Runtime](../../../standard/clr.md).</span></span>  
  
 <span data-ttu-id="43b60-108">Além de usar objetos COM em aplicativos .NET, você talvez queira usar [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] para desenvolver objetos de acesso do código não gerenciado usando COM.</span><span class="sxs-lookup"><span data-stu-id="43b60-108">In addition to using COM objects in .NET applications, you may also want to use [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] to develop objects accessible from unmanaged code through COM.</span></span>  
  
 <span data-ttu-id="43b60-109">Os links nesta página fornecem detalhes sobre as interações entre os objetos COM e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="43b60-109">The links on this page provide details on the interactions between COM and .NET Framework objects.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="43b60-110">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="43b60-110">Related Sections</span></span>  
 [<span data-ttu-id="43b60-111">Interoperabilidade COM</span><span class="sxs-lookup"><span data-stu-id="43b60-111">COM Interop</span></span>](../../../visual-basic/programming-guide/com-interop/index.md)  
 <span data-ttu-id="43b60-112">Fornece links para tópicos que abrangem a interoperabilidade COM em Visual Basic, incluindo COM objetos ActiveX controles, DLLs Win32, os objetos gerenciados e herança de objetos COM.</span><span class="sxs-lookup"><span data-stu-id="43b60-112">Provides links to topics covering COM interoperability in Visual Basic, including COM objects, ActiveX controls, Win32 DLLs, managed objects, and inheritance of COM objects.</span></span>  
  
 [<span data-ttu-id="43b60-113">Erro de wrapper de interoperabilidade COM</span><span class="sxs-lookup"><span data-stu-id="43b60-113">COM Interop Wrapper Error</span></span>](/cpp/misc/com-interop-wrapper-error)  
 <span data-ttu-id="43b60-114">Descreve as opções e as consequências se o sistema do projeto não é possível criar um wrapper de interoperabilidade COM para um componente específico.</span><span class="sxs-lookup"><span data-stu-id="43b60-114">Describes the consequences and options if the project system cannot create a COM interoperability wrapper for a particular component.</span></span>  
  
 [<span data-ttu-id="43b60-115">Interoperação com código não gerenciado</span><span class="sxs-lookup"><span data-stu-id="43b60-115">Interoperating with Unmanaged Code</span></span>](https://msdn.microsoft.com/library/sd10k43k)  
 <span data-ttu-id="43b60-116">Brevemente descreve alguns dos problemas de interação entre o código gerenciado e não gerenciado e fornece links para estudar em mais detalhes.</span><span class="sxs-lookup"><span data-stu-id="43b60-116">Briefly describes some of the interaction issues between managed and unmanaged code, and provides links for further study.</span></span>  
  
 [<span data-ttu-id="43b60-117">Wrappers COM</span><span class="sxs-lookup"><span data-stu-id="43b60-117">COM Wrappers</span></span>](../../../framework/interop/com-wrappers.md)  
 <span data-ttu-id="43b60-118">Discute runtime callable wrappers do, que permitem que o código gerenciado chamar métodos COM, e callable wrappers COM, que permite que clientes COM chamar os métodos de objeto do .NET.</span><span class="sxs-lookup"><span data-stu-id="43b60-118">Discusses runtime callable wrappers, which allow managed code to call COM methods, and COM callable wrappers, which allow COM clients to call .NET object methods.</span></span>  
  
 [<span data-ttu-id="43b60-119">Interoperabilidade COM avançada</span><span class="sxs-lookup"><span data-stu-id="43b60-119">Advanced COM Interoperability</span></span>](http://msdn.microsoft.com/en-us/3ada36e5-2390-4d70-b490-6ad8de92f2fb)  
 <span data-ttu-id="43b60-120">Fornece links para tópicos que abrangem a interoperabilidade COM em relação ao wrappers, exceções, herança, threading, eventos, conversões e realização de marshaling.</span><span class="sxs-lookup"><span data-stu-id="43b60-120">Provides links to topics covering COM interoperability with respect to wrappers, exceptions, inheritance, threading, events, conversions, and marshaling.</span></span>  
  
 [<span data-ttu-id="43b60-121">Tlbimp.exe (Importador de Biblioteca de Tipos)</span><span class="sxs-lookup"><span data-stu-id="43b60-121">Tlbimp.exe (Type Library Importer)</span></span>](http://msdn.microsoft.com/library/ec0a8d63-11b3-4acd-b398-da1e37e97382)  
 <span data-ttu-id="43b60-122">Descreve a ferramenta que você pode usar para converter as definições de tipo encontradas dentro de uma biblioteca de tipos COM às definições equivalentes em um assembly do common language runtime.</span><span class="sxs-lookup"><span data-stu-id="43b60-122">Discusses the tool you can use to convert the type definitions found within a COM type library into equivalent definitions in a common language runtime assembly.</span></span>
