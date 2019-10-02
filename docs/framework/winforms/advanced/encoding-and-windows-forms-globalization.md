---
title: Codificação e globalização de formulários do Windows Forms
ms.date: 03/30/2017
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
ms.openlocfilehash: 60ca9f7ba2f716b5dab1b0276bc3cd07ddd8f65c
ms.sourcegitcommit: 878ca7550b653114c3968ef8906da2b3e60e3c7a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/02/2019
ms.locfileid: "71736881"
---
# <a name="encoding-and-windows-forms-globalization"></a><span data-ttu-id="8fdb4-102">Codificação e globalização de formulários do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8fdb4-102">Encoding and Windows Forms Globalization</span></span>

<span data-ttu-id="8fdb4-103">Aplicativos dos Windows Forms são totalmente habilitados para Unicode, o que significa que cada caractere é representado por um número exclusivo, independente da plataforma, programa ou linguagem.</span><span class="sxs-lookup"><span data-stu-id="8fdb4-103">Windows Forms applications are entirely Unicode-enabled, meaning that each character is represented by a unique number, no matter what the platform, program, or language.</span></span> <span data-ttu-id="8fdb4-104">Para obter mais informações sobre Unicode, consulte o [site da Unicode Consortium](https://www.unicode.org).</span><span class="sxs-lookup"><span data-stu-id="8fdb4-104">For more information about Unicode, see the [Unicode consortium Web site](https://www.unicode.org).</span></span>

## <a name="benefits-of-unicode"></a><span data-ttu-id="8fdb4-105">Benefícios do Unicode</span><span class="sxs-lookup"><span data-stu-id="8fdb4-105">Benefits of Unicode</span></span>

<span data-ttu-id="8fdb4-106">Os benefícios de formulários habilitados para Unicode incluem a capacidade de trabalhar com scripts voltados apenas para Unicode, como Hindi.</span><span class="sxs-lookup"><span data-stu-id="8fdb4-106">The benefits of Unicode-enabled forms include the ability to work with scripts that are Unicode-only, such as Hindi.</span></span> <span data-ttu-id="8fdb4-107">Além disso, é possível usar vários idiomas em um único formulário.</span><span class="sxs-lookup"><span data-stu-id="8fdb4-107">In addition, you can use multiple languages on a single form.</span></span> <span data-ttu-id="8fdb4-108">Em Unicode, todos os caracteres têm dois bytes, portanto nenhum esforço especial é necessário para representar caracteres de byte duplo.</span><span class="sxs-lookup"><span data-stu-id="8fdb4-108">In Unicode, all characters are two bytes long, so no special effort is needed to represent double-byte characters.</span></span> <span data-ttu-id="8fdb4-109">Também é possível escrever um único conjunto de códigos que funcionará em todas as plataformas.</span><span class="sxs-lookup"><span data-stu-id="8fdb4-109">You can also write a single set of code that will work on all platforms.</span></span> <span data-ttu-id="8fdb4-110">Essa é uma alteração das versões anteriores do Visual Basic, na qual era necessário escrever código diferente para diferentes plataformas, como o Windows NT e o Windows 98.</span><span class="sxs-lookup"><span data-stu-id="8fdb4-110">This is a change from previous versions of Visual Basic, in which you had to write different code for different platforms, such as Windows NT and Windows 98.</span></span>

<span data-ttu-id="8fdb4-111">No entanto, determinados controles não oferecem suporte a Unicode no Windows 98 e no Windows Millennium Edition.</span><span class="sxs-lookup"><span data-stu-id="8fdb4-111">However, certain controls do not support Unicode in Windows 98 and Windows Millennium Edition.</span></span> <span data-ttu-id="8fdb4-112">Esses controles, todos herdados do controle comum, processarão dados com as páginas de código do Windows, como ANSI.</span><span class="sxs-lookup"><span data-stu-id="8fdb4-112">These controls, all of which inherit from the common control, will process data with the Windows code pages, as ANSI.</span></span> <span data-ttu-id="8fdb4-113">Esses controles são: <xref:System.Windows.Forms.TabControl>, <xref:System.Windows.Forms.ListView>, <xref:System.Windows.Forms.TreeView>, <xref:System.Windows.Forms.DateTimePicker>, <xref:System.Windows.Forms.MonthCalendar>, <xref:System.Windows.Forms.TrackBar>, <xref:System.Windows.Forms.ProgressBar>, <xref:System.Windows.Forms.ImageList>, <xref:System.Windows.Forms.ToolBar> e <xref:System.Windows.Forms.StatusBar>.</span><span class="sxs-lookup"><span data-stu-id="8fdb4-113">These controls are: <xref:System.Windows.Forms.TabControl>, <xref:System.Windows.Forms.ListView>, <xref:System.Windows.Forms.TreeView>, <xref:System.Windows.Forms.DateTimePicker>, <xref:System.Windows.Forms.MonthCalendar>, <xref:System.Windows.Forms.TrackBar>, <xref:System.Windows.Forms.ProgressBar>, <xref:System.Windows.Forms.ImageList>, <xref:System.Windows.Forms.ToolBar>, and <xref:System.Windows.Forms.StatusBar>.</span></span> <span data-ttu-id="8fdb4-114">Como resultado, não é possível exibir dados Unicode nesses controles nas plataformas listadas.</span><span class="sxs-lookup"><span data-stu-id="8fdb4-114">As a result, you cannot display Unicode data in these controls on the listed platforms.</span></span> <span data-ttu-id="8fdb4-115">Por exemplo, você não pode exibir caracteres japoneses em um sistema operacional Windows 98 em inglês.</span><span class="sxs-lookup"><span data-stu-id="8fdb4-115">For example, you cannot display Japanese characters on an English Windows 98 operating system.</span></span>

<span data-ttu-id="8fdb4-116">Para alternativas que reconhecem Unicode para os controles <xref:System.Windows.Forms.ToolBar> e <xref:System.Windows.Forms.StatusBar>, use os controles <xref:System.Windows.Forms.ToolStrip> e <xref:System.Windows.Forms.StatusStrip>, que substituem esses controles mais antigos.</span><span class="sxs-lookup"><span data-stu-id="8fdb4-116">For Unicode-aware alternatives to the <xref:System.Windows.Forms.ToolBar> and <xref:System.Windows.Forms.StatusBar> controls, use the <xref:System.Windows.Forms.ToolStrip> and <xref:System.Windows.Forms.StatusStrip> controls, which replace these older controls.</span></span> <span data-ttu-id="8fdb4-117">Para manter uma aparência semelhante entre os elementos visuais em seu aplicativo, use o controle <xref:System.Windows.Forms.MenuStrip> para renderizar menus em vez de <xref:System.Windows.Forms.MainMenu>.</span><span class="sxs-lookup"><span data-stu-id="8fdb4-117">To maintain a similar look and feel between visual elements in your application, use the <xref:System.Windows.Forms.MenuStrip> control for rendering menus instead of <xref:System.Windows.Forms.MainMenu>.</span></span> <span data-ttu-id="8fdb4-118">Assim como <xref:System.Windows.Forms.ToolStrip> e <xref:System.Windows.Forms.StatusStrip>, <xref:System.Windows.Forms.MenuStrip> também podem processar e exibir caracteres Unicode.</span><span class="sxs-lookup"><span data-stu-id="8fdb4-118">Like <xref:System.Windows.Forms.ToolStrip> and <xref:System.Windows.Forms.StatusStrip>, <xref:System.Windows.Forms.MenuStrip> can also process and display Unicode characters.</span></span>

## <a name="see-also"></a><span data-ttu-id="8fdb4-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8fdb4-119">See also</span></span>

- [<span data-ttu-id="8fdb4-120">Globalizando aplicativos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8fdb4-120">Globalizing Windows Forms applications</span></span>](globalizing-windows-forms.md)
