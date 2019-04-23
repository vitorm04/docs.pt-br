---
title: Visão geral de elementos gráficos
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [Windows Forms], using managed interface
- graphics [Windows Forms], about graphics
ms.assetid: a602aef8-a8c8-4c36-9816-74e7bad96a68
ms.openlocfilehash: a95086645771de61cfc859e34b225992bc16eac9
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59103922"
---
# <a name="overview-of-graphics"></a><span data-ttu-id="54736-102">Visão geral de elementos gráficos</span><span class="sxs-lookup"><span data-stu-id="54736-102">Overview of Graphics</span></span>
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] <span data-ttu-id="54736-103">é uma interface de programação de aplicativo (API) que forma o subsistema do sistema operacional Microsoft Windows.</span><span class="sxs-lookup"><span data-stu-id="54736-103">is an application programming interface (API) that forms the subsystem of the Microsoft Windows operating system.</span></span> <span data-ttu-id="54736-104">O [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] é responsável por exibir informações nas telas e impressoras.</span><span class="sxs-lookup"><span data-stu-id="54736-104">[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] is responsible for displaying information on screens and printers.</span></span> <span data-ttu-id="54736-105">Como o nome sugere, o [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] é o sucessor do [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)], a Graphics Device Interface incluída em versões anteriores do Windows.</span><span class="sxs-lookup"><span data-stu-id="54736-105">As its name suggests, [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] is the successor to [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)], the Graphics Device Interface included with earlier versions of Windows.</span></span>  
  
## <a name="managed-class-interface"></a><span data-ttu-id="54736-106">interface de classe gerenciada</span><span class="sxs-lookup"><span data-stu-id="54736-106">Managed Class Interface</span></span>  
 <span data-ttu-id="54736-107">A API [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] é exposta por meio de um conjunto de classes implantado como código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="54736-107">The [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] API is exposed through a set of classes deployed as managed code.</span></span> <span data-ttu-id="54736-108">Esse conjunto de classes é chamado de *interface de classe gerenciada* para [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)].</span><span class="sxs-lookup"><span data-stu-id="54736-108">This set of classes is called the *managed class interface* to [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)].</span></span> <span data-ttu-id="54736-109">Os namespaces a seguir compõem a interface da classe gerenciada:</span><span class="sxs-lookup"><span data-stu-id="54736-109">The following namespaces make up the managed class interface:</span></span>  
  
-   <xref:System.Drawing>  
  
-   <xref:System.Drawing.Drawing2D>  
  
-   <xref:System.Drawing.Imaging>  
  
-   <xref:System.Drawing.Text>  
  
-   <xref:System.Drawing.Printing>  
  
 <span data-ttu-id="54736-110">Com uma Graphics Device Interface, como [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], você pode exibir informações em uma tela ou impressora sem precisar se preocupar com os detalhes de um dispositivo de vídeo específico.</span><span class="sxs-lookup"><span data-stu-id="54736-110">With a Graphics Device Interface, such as [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], you can display information on a screen or printer without having to be concerned about the details of a particular display device.</span></span> <span data-ttu-id="54736-111">O programador faz chamadas para métodos fornecidos pelas classes [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)].</span><span class="sxs-lookup"><span data-stu-id="54736-111">The programmer makes calls to methods provided by [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] classes.</span></span> <span data-ttu-id="54736-112">Esses métodos, por sua vez, fazem as chamadas apropriadas aos drivers de dispositivo específicos.</span><span class="sxs-lookup"><span data-stu-id="54736-112">Those methods, in turn, make the appropriate calls to specific device drivers.</span></span> <span data-ttu-id="54736-113">O [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] isola o aplicativo do hardware de elementos gráficos.</span><span class="sxs-lookup"><span data-stu-id="54736-113">[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] insulates the application from the graphics hardware.</span></span> <span data-ttu-id="54736-114">É esse isolamento que permite que um programador crie aplicativos independentes de dispositivo.</span><span class="sxs-lookup"><span data-stu-id="54736-114">It is this insulation that enables a programmer to create device-independent applications.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54736-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="54736-115">See also</span></span>

- [<span data-ttu-id="54736-116">Visão geral de elementos gráficos</span><span class="sxs-lookup"><span data-stu-id="54736-116">Graphics Overview</span></span>](graphics-overview-windows-forms.md)
