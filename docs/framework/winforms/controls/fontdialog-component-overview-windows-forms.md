---
title: Visão geral do componente FontDialog (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- FontDialog
helpviewer_keywords:
- Font dialog box [Windows Forms], Windows Forms
- Font dialog box
- FontDialog component [Windows Forms], about FontDialog component
ms.assetid: daf46e57-1b4b-4b7a-bad0-b50ca7ba75dc
ms.openlocfilehash: 26bfb561c1050438b78c4ae0a3e6e8da32458cdd
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57725032"
---
# <a name="fontdialog-component-overview-windows-forms"></a><span data-ttu-id="ee51a-102">Visão geral do componente FontDialog (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="ee51a-102">FontDialog Component Overview (Windows Forms)</span></span>
<span data-ttu-id="ee51a-103">Os formulários do Windows <xref:System.Windows.Forms.FontDialog> componente é uma caixa de diálogo pré-configurada, que é o padrão Windows **fonte** caixa de diálogo usada para expor as fontes que estão atualmente instaladas no sistema.</span><span class="sxs-lookup"><span data-stu-id="ee51a-103">The Windows Forms <xref:System.Windows.Forms.FontDialog> component is a pre-configured dialog box, which is the standard Windows **Font** dialog box used to expose the fonts that are currently installed on the system.</span></span> <span data-ttu-id="ee51a-104">Use-o em seu aplicativo baseado no Windows como uma solução simples para seleção de fonte em vez de configurar sua própria caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="ee51a-104">Use it within your Windows-based application as a simple solution for font selection in lieu of configuring your own dialog box.</span></span>  
  
 <span data-ttu-id="ee51a-105">Por padrão, a caixa de diálogo mostra caixas de listagem de Fonte, Estilo da fonte e Tamanho. Caixas de seleção para efeitos como Riscado e Sublinhado; uma lista suspensa para Script e um exemplo de como a fonte aparecerá.</span><span class="sxs-lookup"><span data-stu-id="ee51a-105">By default, the dialog box shows list boxes for Font, Font style, and Size; check boxes for effects like Strikeout and Underline; a drop-down list for Script; and a sample of how the font will appear.</span></span> <span data-ttu-id="ee51a-106">(Script refere-se a scripts de caracteres diferentes que estão disponíveis para determinada fonte, por exemplo, hebraico ou japonês.) Para exibir a caixa de diálogo de fonte, chame o <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> método.</span><span class="sxs-lookup"><span data-stu-id="ee51a-106">(Script refers to different character scripts that are available for a given font, for example, Hebrew or Japanese.) To display the font dialog box, call the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method.</span></span>  
  
## <a name="key-properties"></a><span data-ttu-id="ee51a-107">Propriedades da chave</span><span class="sxs-lookup"><span data-stu-id="ee51a-107">Key Properties</span></span>  
 <span data-ttu-id="ee51a-108">O componente tem inúmeras propriedades que configuram sua aparência.</span><span class="sxs-lookup"><span data-stu-id="ee51a-108">The component has a number of properties that configure its appearance.</span></span> <span data-ttu-id="ee51a-109">As propriedades que defina as seleções de caixa de diálogo são <xref:System.Windows.Forms.FontDialog.Font%2A> e <xref:System.Windows.Forms.FontDialog.Color%2A>.</span><span class="sxs-lookup"><span data-stu-id="ee51a-109">The properties that set the dialog-box selections are <xref:System.Windows.Forms.FontDialog.Font%2A> and <xref:System.Windows.Forms.FontDialog.Color%2A>.</span></span> <span data-ttu-id="ee51a-110">O <xref:System.Windows.Forms.FontDialog.Font%2A> propriedade define a fonte, estilo, tamanho, script e efeitos; por exemplo, `Arial, 10pt, style=Italic, Strikeout`.</span><span class="sxs-lookup"><span data-stu-id="ee51a-110">The <xref:System.Windows.Forms.FontDialog.Font%2A> property sets the font, style, size, script, and effects; for example, `Arial, 10pt, style=Italic, Strikeout`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee51a-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ee51a-111">See also</span></span>
- <xref:System.Windows.Forms.FontDialog>
- [<span data-ttu-id="ee51a-112">Componente FontDialog</span><span class="sxs-lookup"><span data-stu-id="ee51a-112">FontDialog Component</span></span>](fontdialog-component-windows-forms.md)
