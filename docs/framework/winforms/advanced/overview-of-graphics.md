---
title: Visão geral de elementos gráficos
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [Windows Forms], using managed interface
- graphics [Windows Forms], about graphics
ms.assetid: a602aef8-a8c8-4c36-9816-74e7bad96a68
ms.openlocfilehash: f0e2fd9dcf31e5fdce16b5a3b6fd21eab6eab66a
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/02/2019
ms.locfileid: "67505328"
---
# <a name="overview-of-graphics"></a><span data-ttu-id="fa329-102">Visão geral de elementos gráficos</span><span class="sxs-lookup"><span data-stu-id="fa329-102">Overview of Graphics</span></span>
<span data-ttu-id="fa329-103">GDI+ é uma interface de programação de aplicativo (API) que forma o subsistema do sistema operacional Microsoft Windows.</span><span class="sxs-lookup"><span data-stu-id="fa329-103">GDI+ is an application programming interface (API) that forms the subsystem of the Microsoft Windows operating system.</span></span> <span data-ttu-id="fa329-104">GDI+ é responsável por exibir informações nas telas e impressoras.</span><span class="sxs-lookup"><span data-stu-id="fa329-104">GDI+ is responsible for displaying information on screens and printers.</span></span> <span data-ttu-id="fa329-105">Como o nome sugere, GDI+ é o sucessor do GDI, a Graphics Device Interface incluída em versões anteriores do Windows.</span><span class="sxs-lookup"><span data-stu-id="fa329-105">As its name suggests, GDI+ is the successor to GDI, the Graphics Device Interface included with earlier versions of Windows.</span></span>  
  
## <a name="managed-class-interface"></a><span data-ttu-id="fa329-106">interface de classe gerenciada</span><span class="sxs-lookup"><span data-stu-id="fa329-106">Managed Class Interface</span></span>  
 <span data-ttu-id="fa329-107">A API GDI+ é exposta por meio de um conjunto de classes implantado como código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="fa329-107">The GDI+ API is exposed through a set of classes deployed as managed code.</span></span> <span data-ttu-id="fa329-108">Esse conjunto de classes é chamado de *interface de classe gerenciada* ao GDI+.</span><span class="sxs-lookup"><span data-stu-id="fa329-108">This set of classes is called the *managed class interface* to GDI+.</span></span> <span data-ttu-id="fa329-109">Os namespaces a seguir compõem a interface da classe gerenciada:</span><span class="sxs-lookup"><span data-stu-id="fa329-109">The following namespaces make up the managed class interface:</span></span>  
  
- <xref:System.Drawing>  
  
- <xref:System.Drawing.Drawing2D>  
  
- <xref:System.Drawing.Imaging>  
  
- <xref:System.Drawing.Text>  
  
- <xref:System.Drawing.Printing>  
  
 <span data-ttu-id="fa329-110">Com uma Interface gráfica de dispositivo, como o GDI+, você pode exibir informações em uma tela ou impressora sem precisar se preocupar com os detalhes de um dispositivo de vídeo específico.</span><span class="sxs-lookup"><span data-stu-id="fa329-110">With a Graphics Device Interface, such as GDI+, you can display information on a screen or printer without having to be concerned about the details of a particular display device.</span></span> <span data-ttu-id="fa329-111">O programador faz chamadas para métodos fornecidos pelas classes de GDI+.</span><span class="sxs-lookup"><span data-stu-id="fa329-111">The programmer makes calls to methods provided by GDI+ classes.</span></span> <span data-ttu-id="fa329-112">Esses métodos, por sua vez, fazem as chamadas apropriadas aos drivers de dispositivo específicos.</span><span class="sxs-lookup"><span data-stu-id="fa329-112">Those methods, in turn, make the appropriate calls to specific device drivers.</span></span> <span data-ttu-id="fa329-113">GDI+ isola o aplicativo do hardware gráfico.</span><span class="sxs-lookup"><span data-stu-id="fa329-113">GDI+ insulates the application from the graphics hardware.</span></span> <span data-ttu-id="fa329-114">É esse isolamento que permite que um programador crie aplicativos independentes de dispositivo.</span><span class="sxs-lookup"><span data-stu-id="fa329-114">It is this insulation that enables a programmer to create device-independent applications.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa329-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fa329-115">See also</span></span>

- [<span data-ttu-id="fa329-116">Visão geral de elementos gráficos</span><span class="sxs-lookup"><span data-stu-id="fa329-116">Graphics Overview</span></span>](graphics-overview-windows-forms.md)
