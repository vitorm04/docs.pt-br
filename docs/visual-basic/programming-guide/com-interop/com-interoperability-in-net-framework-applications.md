---
title: Interoperabilidade COM em aplicativos do .NET Framework (Visual Basic) | Documentos do Microsoft
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
- interoperability, COM and .NET framework objects
- COM interop
- shared components
ms.assetid: f5a72143-c268-4dff-a019-974ad940e17d
caps.latest.revision: 15
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
ms.openlocfilehash: 6b68f35c1c63e2d7d229f89336b86c4a062e5ec9
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="com-interoperability-in-net-framework-applications-visual-basic"></a><span data-ttu-id="331f8-102">Interoperabilidade COM em aplicativos .NET Framework (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="331f8-102">COM Interoperability in .NET Framework Applications (Visual Basic)</span></span>
<span data-ttu-id="331f8-103">Quando você quiser usar objetos COM e .NET Framework no mesmo aplicativo, é necessário resolver as diferenças em como os objetos existem na memória.</span><span class="sxs-lookup"><span data-stu-id="331f8-103">When you want to use COM objects and .NET Framework objects in the same application, you need to address the differences in how the objects exist in memory.</span></span> <span data-ttu-id="331f8-104">Um objeto do .NET Framework está localizado na memória gerenciada — a memória controlada pelo common language runtime — e pode ser movido pelo tempo de execução, conforme necessário.</span><span class="sxs-lookup"><span data-stu-id="331f8-104">A .NET Framework object is located in managed memory—the memory controlled by the common language runtime—and may be moved by the runtime as needed.</span></span> <span data-ttu-id="331f8-105">Um objeto COM está localizado na memória não gerenciada e não é esperado para mover para outro local da memória.</span><span class="sxs-lookup"><span data-stu-id="331f8-105">A COM object is located in unmanaged memory and is not expected to move to another memory location.</span></span> [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)]<span data-ttu-id="331f8-106">e o [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] fornecem ferramentas para controlar a interação dessas gerenciados e não gerenciados componentes.</span><span class="sxs-lookup"><span data-stu-id="331f8-106"> and the [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] provide tools to control the interaction of these managed and unmanaged components.</span></span> <span data-ttu-id="331f8-107">Para obter mais informações sobre o código gerenciado, consulte [Common Language Runtime](http://msdn.microsoft.com/library/059a624e-f7db-4134-ba9f-08b676050482).</span><span class="sxs-lookup"><span data-stu-id="331f8-107">For more information about managed code, see [Common Language Runtime](http://msdn.microsoft.com/library/059a624e-f7db-4134-ba9f-08b676050482).</span></span>  
  
 <span data-ttu-id="331f8-108">Além de usar objetos COM em aplicativos .NET, você talvez queira usar [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] para desenvolver objetos acessíveis a partir do código não gerenciado usando COM.</span><span class="sxs-lookup"><span data-stu-id="331f8-108">In addition to using COM objects in .NET applications, you may also want to use [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] to develop objects accessible from unmanaged code through COM.</span></span>  
  
 <span data-ttu-id="331f8-109">Os links nesta página fornecem detalhes sobre as interações entre objetos COM e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="331f8-109">The links on this page provide details on the interactions between COM and .NET Framework objects.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="331f8-110">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="331f8-110">Related Sections</span></span>  
 [<span data-ttu-id="331f8-111">Interoperabilidade COM</span><span class="sxs-lookup"><span data-stu-id="331f8-111">COM Interop</span></span>](../../../visual-basic/programming-guide/com-interop/index.md)  
 <span data-ttu-id="331f8-112">Fornece links para tópicos que abrangem a interoperabilidade COM em Visual Basic, incluindo COM objetos ActiveX controles, as DLLs do Win32, os objetos gerenciados e herança de objetos COM.</span><span class="sxs-lookup"><span data-stu-id="331f8-112">Provides links to topics covering COM interoperability in Visual Basic, including COM objects, ActiveX controls, Win32 DLLs, managed objects, and inheritance of COM objects.</span></span>  
  
 [<span data-ttu-id="331f8-113">Erro de wrapper de interoperabilidade COM</span><span class="sxs-lookup"><span data-stu-id="331f8-113">COM Interop Wrapper Error</span></span>](https://docs.microsoft.com/cpp/misc/com-interop-wrapper-error)  
 <span data-ttu-id="331f8-114">Descreve as opções e as consequências se o sistema do projeto não é possível criar um wrapper de interoperabilidade COM para um componente específico.</span><span class="sxs-lookup"><span data-stu-id="331f8-114">Describes the consequences and options if the project system cannot create a COM interoperability wrapper for a particular component.</span></span>  
  
 [<span data-ttu-id="331f8-115">Interoperação com código não gerenciado</span><span class="sxs-lookup"><span data-stu-id="331f8-115">Interoperating with Unmanaged Code</span></span>](https://msdn.microsoft.com/library/sd10k43k)  
 <span data-ttu-id="331f8-116">Resumidamente descreve alguns dos problemas de interação entre código gerenciado e não gerenciado e fornece links para estudos adicionais.</span><span class="sxs-lookup"><span data-stu-id="331f8-116">Briefly describes some of the interaction issues between managed and unmanaged code, and provides links for further study.</span></span>  
  
 [<span data-ttu-id="331f8-117">Wrappers COM</span><span class="sxs-lookup"><span data-stu-id="331f8-117">COM Wrappers</span></span>](http://msdn.microsoft.com/library/e56c485b-6b67-4345-8e66-fd21835a6092)  
 <span data-ttu-id="331f8-118">Discute o runtime callable wrappers, que permitem ao código gerenciado chamar métodos COM, e callable wrappers COM, permitindo que clientes COM para chamar os métodos do objeto .NET.</span><span class="sxs-lookup"><span data-stu-id="331f8-118">Discusses runtime callable wrappers, which allow managed code to call COM methods, and COM callable wrappers, which allow COM clients to call .NET object methods.</span></span>  
  
 [<span data-ttu-id="331f8-119">Interoperabilidade COM avançada</span><span class="sxs-lookup"><span data-stu-id="331f8-119">Advanced COM Interoperability</span></span>](http://msdn.microsoft.com/en-us/3ada36e5-2390-4d70-b490-6ad8de92f2fb)  
 <span data-ttu-id="331f8-120">Fornece links para tópicos que abrangem a interoperabilidade de COM em relação ao wrappers, exceções, herança, threading, eventos, conversões e empacotamento.</span><span class="sxs-lookup"><span data-stu-id="331f8-120">Provides links to topics covering COM interoperability with respect to wrappers, exceptions, inheritance, threading, events, conversions, and marshaling.</span></span>  
  
 [<span data-ttu-id="331f8-121">Tlbimp.exe (importador de biblioteca)</span><span class="sxs-lookup"><span data-stu-id="331f8-121">Tlbimp.exe (Type Library Importer)</span></span>](http://msdn.microsoft.com/library/ec0a8d63-11b3-4acd-b398-da1e37e97382)  
 <span data-ttu-id="331f8-122">Descreve a ferramenta que você pode usar para converter as definições de tipo encontradas dentro de uma biblioteca de tipos COM em definições equivalentes em um assembly do common language runtime.</span><span class="sxs-lookup"><span data-stu-id="331f8-122">Discusses the tool you can use to convert the type definitions found within a COM type library into equivalent definitions in a common language runtime assembly.</span></span>
