---
title: "Codificação e globalização de formulários do Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ListView control [Windows Forms], lack of Unicode support
- DateTimePicker control [Windows Forms], lack of Unicode support
- TrackBar control [Windows Forms], lack of Unicode support
- ImageList component [Windows Forms], lack of Unicode support
- Unicode [Windows Forms]
- ToolBar control [Windows Forms], lack of Unicode support
- international applications [Windows Forms], character display
- StatusBar control [Windows Forms], lack of Unicode support
- MonthCalendar control [Windows Forms], lack of Unicode support
- international characters
- TabControl control [Windows Forms], lack of Unicode support
- Windows Forms, encoding
- TreeView control [Windows Forms], lack of Unicode support
- ProgressBar control [Windows Forms], Unicode-enabled forms
- localization [Windows Forms], character sets
- globalization [Windows Forms], character sets
ms.assetid: 22e8965d-a712-42b3-8167-3ee346bd70f9
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f25f4f7206b68e961f3c09a488af643ad5d0a4fd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="encoding-and-windows-forms-globalization"></a><span data-ttu-id="4eb74-102">Codificação e globalização de formulários do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="4eb74-102">Encoding and Windows Forms Globalization</span></span>
<span data-ttu-id="4eb74-103">Aplicativos dos Windows Forms são totalmente habilitados para Unicode, o que significa que cada caractere é representado por um número exclusivo, independente da plataforma, programa ou linguagem.</span><span class="sxs-lookup"><span data-stu-id="4eb74-103">Windows Forms applications are entirely Unicode-enabled, meaning that each character is represented by a unique number, no matter what the platform, program, or language.</span></span> <span data-ttu-id="4eb74-104">Para obter mais informações sobre Unicode, consulte o [site da Unicode Consortium](http://www.unicode.org).</span><span class="sxs-lookup"><span data-stu-id="4eb74-104">For more information about Unicode, see the [Unicode consortium Web site](http://www.unicode.org).</span></span>  
  
## <a name="benefits-of-unicode"></a><span data-ttu-id="4eb74-105">Benefícios do Unicode</span><span class="sxs-lookup"><span data-stu-id="4eb74-105">Benefits of Unicode</span></span>  
 <span data-ttu-id="4eb74-106">Os benefícios de formulários habilitados para Unicode incluem a capacidade de trabalhar com scripts voltados apenas para Unicode, como Hindi.</span><span class="sxs-lookup"><span data-stu-id="4eb74-106">The benefits of Unicode-enabled forms include the ability to work with scripts that are Unicode-only, such as Hindi.</span></span> <span data-ttu-id="4eb74-107">Além disso, é possível usar vários idiomas em um único formulário.</span><span class="sxs-lookup"><span data-stu-id="4eb74-107">In addition, you can use multiple languages on a single form.</span></span> <span data-ttu-id="4eb74-108">Em Unicode, todos os caracteres têm dois bytes, portanto nenhum esforço especial é necessário para representar caracteres de byte duplo.</span><span class="sxs-lookup"><span data-stu-id="4eb74-108">In Unicode, all characters are two bytes long, so no special effort is needed to represent double-byte characters.</span></span> <span data-ttu-id="4eb74-109">Também é possível escrever um único conjunto de códigos que funcionará em todas as plataformas.</span><span class="sxs-lookup"><span data-stu-id="4eb74-109">You can also write a single set of code that will work on all platforms.</span></span> <span data-ttu-id="4eb74-110">Essa é uma alteração das versões anteriores do [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)], em que era necessário escrever código diferente para diferentes plataformas, como Windows NT e [!INCLUDE[win98](../../../../includes/win98-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4eb74-110">This is a change from previous versions of [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)], in which you had to write different code for different platforms, such as Windows NT and [!INCLUDE[win98](../../../../includes/win98-md.md)].</span></span>  
  
 <span data-ttu-id="4eb74-111">No entanto, certos controles não dão suporte a Unicode no [!INCLUDE[win98](../../../../includes/win98-md.md)] e Windows Millennium Edition.</span><span class="sxs-lookup"><span data-stu-id="4eb74-111">However, certain controls do not support Unicode in [!INCLUDE[win98](../../../../includes/win98-md.md)] and Windows Millennium Edition.</span></span> <span data-ttu-id="4eb74-112">Esses controles, todos com herança do controle comum, processarão dados com as páginas de código do Windows, como [!INCLUDE[vcpransi](../../../../includes/vcpransi-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4eb74-112">These controls, all of which inherit from the common control, will process data with the Windows code pages, as [!INCLUDE[vcpransi](../../../../includes/vcpransi-md.md)].</span></span> <span data-ttu-id="4eb74-113">Esses controles estão: <xref:System.Windows.Forms.TabControl>, <xref:System.Windows.Forms.ListView>, <xref:System.Windows.Forms.TreeView>, <xref:System.Windows.Forms.DateTimePicker>, <xref:System.Windows.Forms.MonthCalendar>, <xref:System.Windows.Forms.TrackBar>, <xref:System.Windows.Forms.ProgressBar>, <xref:System.Windows.Forms.ImageList>, <xref:System.Windows.Forms.ToolBar>, e <xref:System.Windows.Forms.StatusBar>.</span><span class="sxs-lookup"><span data-stu-id="4eb74-113">These controls are: <xref:System.Windows.Forms.TabControl>, <xref:System.Windows.Forms.ListView>, <xref:System.Windows.Forms.TreeView>, <xref:System.Windows.Forms.DateTimePicker>, <xref:System.Windows.Forms.MonthCalendar>, <xref:System.Windows.Forms.TrackBar>, <xref:System.Windows.Forms.ProgressBar>, <xref:System.Windows.Forms.ImageList>, <xref:System.Windows.Forms.ToolBar>, and <xref:System.Windows.Forms.StatusBar>.</span></span> <span data-ttu-id="4eb74-114">Como resultado, não é possível exibir dados Unicode nesses controles nas plataformas listadas.</span><span class="sxs-lookup"><span data-stu-id="4eb74-114">As a result, you cannot display Unicode data in these controls on the listed platforms.</span></span> <span data-ttu-id="4eb74-115">Por exemplo, não é possível exibir caracteres em japonês em um em sistema operacional [!INCLUDE[win98](../../../../includes/win98-md.md)] em inglês.</span><span class="sxs-lookup"><span data-stu-id="4eb74-115">For example, you cannot display Japanese characters on an English [!INCLUDE[win98](../../../../includes/win98-md.md)] operating system.</span></span>  
  
 <span data-ttu-id="4eb74-116">Para alternativas cientes do Unicode para a <xref:System.Windows.Forms.ToolBar> e <xref:System.Windows.Forms.StatusBar> controles, use o <xref:System.Windows.Forms.ToolStrip> e <xref:System.Windows.Forms.StatusStrip> controles, que substituem estes controles mais antigos.</span><span class="sxs-lookup"><span data-stu-id="4eb74-116">For Unicode-aware alternatives to the <xref:System.Windows.Forms.ToolBar> and <xref:System.Windows.Forms.StatusBar> controls, use the <xref:System.Windows.Forms.ToolStrip> and <xref:System.Windows.Forms.StatusStrip> controls, which replace these older controls.</span></span> <span data-ttu-id="4eb74-117">Para manter uma aparência semelhante entre elementos visuais em seu aplicativo, use o <xref:System.Windows.Forms.MenuStrip> controle menus de renderização, em vez de <xref:System.Windows.Forms.MainMenu>.</span><span class="sxs-lookup"><span data-stu-id="4eb74-117">To maintain a similar look and feel between visual elements in your application, use the <xref:System.Windows.Forms.MenuStrip> control for rendering menus instead of <xref:System.Windows.Forms.MainMenu>.</span></span> <span data-ttu-id="4eb74-118">Como <xref:System.Windows.Forms.ToolStrip> e <xref:System.Windows.Forms.StatusStrip>, <xref:System.Windows.Forms.MenuStrip> também pode processar e exibir os caracteres Unicode.</span><span class="sxs-lookup"><span data-stu-id="4eb74-118">Like <xref:System.Windows.Forms.ToolStrip> and <xref:System.Windows.Forms.StatusStrip>, <xref:System.Windows.Forms.MenuStrip> can also process and display Unicode characters.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4eb74-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4eb74-119">See Also</span></span>  
 [<span data-ttu-id="4eb74-120">Globalizando o Windows Forms</span><span class="sxs-lookup"><span data-stu-id="4eb74-120">Globalizing Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/globalizing-windows-forms.md)
