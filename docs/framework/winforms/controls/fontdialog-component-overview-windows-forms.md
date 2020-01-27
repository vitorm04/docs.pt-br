---
title: Visão geral do componente FontDialog
ms.date: 03/30/2017
f1_keywords:
- FontDialog
helpviewer_keywords:
- Font dialog box [Windows Forms], Windows Forms
- Font dialog box
- FontDialog component [Windows Forms], about FontDialog component
ms.assetid: daf46e57-1b4b-4b7a-bad0-b50ca7ba75dc
ms.openlocfilehash: 664b756dc068ca283e4f43edbdd0f3266f5d1142
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745699"
---
# <a name="fontdialog-component-overview-windows-forms"></a><span data-ttu-id="a5e9d-102">Visão geral do componente FontDialog (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="a5e9d-102">FontDialog Component Overview (Windows Forms)</span></span>
<span data-ttu-id="a5e9d-103">O Windows Forms <xref:System.Windows.Forms.FontDialog> componente é uma caixa de diálogo pré-configurada, que é a caixa de diálogo de **fontes** padrão do Windows usada para expor as fontes atualmente instaladas no sistema.</span><span class="sxs-lookup"><span data-stu-id="a5e9d-103">The Windows Forms <xref:System.Windows.Forms.FontDialog> component is a pre-configured dialog box, which is the standard Windows **Font** dialog box used to expose the fonts that are currently installed on the system.</span></span> <span data-ttu-id="a5e9d-104">Use-o em seu aplicativo baseado no Windows como uma solução simples para seleção de fonte em vez de configurar sua própria caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="a5e9d-104">Use it within your Windows-based application as a simple solution for font selection in lieu of configuring your own dialog box.</span></span>  
  
 <span data-ttu-id="a5e9d-105">Por padrão, a caixa de diálogo mostra caixas de listagem de Fonte, Estilo da fonte e Tamanho. Caixas de seleção para efeitos como Riscado e Sublinhado; uma lista suspensa para Script e um exemplo de como a fonte aparecerá.</span><span class="sxs-lookup"><span data-stu-id="a5e9d-105">By default, the dialog box shows list boxes for Font, Font style, and Size; check boxes for effects like Strikeout and Underline; a drop-down list for Script; and a sample of how the font will appear.</span></span> <span data-ttu-id="a5e9d-106">(O script refere-se a scripts de caracteres diferentes que estão disponíveis para uma determinada fonte, por exemplo, hebraico ou japonês.) Para exibir a caixa de diálogo fonte, chame o método <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A>.</span><span class="sxs-lookup"><span data-stu-id="a5e9d-106">(Script refers to different character scripts that are available for a given font, for example, Hebrew or Japanese.) To display the font dialog box, call the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method.</span></span>  
  
## <a name="key-properties"></a><span data-ttu-id="a5e9d-107">Propriedades da chave</span><span class="sxs-lookup"><span data-stu-id="a5e9d-107">Key Properties</span></span>  
 <span data-ttu-id="a5e9d-108">O componente tem inúmeras propriedades que configuram sua aparência.</span><span class="sxs-lookup"><span data-stu-id="a5e9d-108">The component has a number of properties that configure its appearance.</span></span> <span data-ttu-id="a5e9d-109">As propriedades que definem as seleções da caixa de diálogo são <xref:System.Windows.Forms.FontDialog.Font%2A> e <xref:System.Windows.Forms.FontDialog.Color%2A>.</span><span class="sxs-lookup"><span data-stu-id="a5e9d-109">The properties that set the dialog-box selections are <xref:System.Windows.Forms.FontDialog.Font%2A> and <xref:System.Windows.Forms.FontDialog.Color%2A>.</span></span> <span data-ttu-id="a5e9d-110">A propriedade <xref:System.Windows.Forms.FontDialog.Font%2A> define a fonte, o estilo, o tamanho, o script e os efeitos; por exemplo, `Arial, 10pt, style=Italic, Strikeout`.</span><span class="sxs-lookup"><span data-stu-id="a5e9d-110">The <xref:System.Windows.Forms.FontDialog.Font%2A> property sets the font, style, size, script, and effects; for example, `Arial, 10pt, style=Italic, Strikeout`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5e9d-111">Veja também</span><span class="sxs-lookup"><span data-stu-id="a5e9d-111">See also</span></span>

- <xref:System.Windows.Forms.FontDialog>
- [<span data-ttu-id="a5e9d-112">Componente FontDialog</span><span class="sxs-lookup"><span data-stu-id="a5e9d-112">FontDialog Component</span></span>](fontdialog-component-windows-forms.md)
