---
title: Usando o Document Object Model HTML gerenciado
ms.date: 03/30/2017
helpviewer_keywords:
- managed HTML DOM
ms.assetid: a017dd5c-cd7b-47e4-952c-f4f54cb48409
ms.openlocfilehash: 1405bb43e971f02bafa892de84a6b8acde2e319b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54691418"
---
# <a name="using-the-managed-html-document-object-model"></a><span data-ttu-id="6b4c6-102">Usando o Document Object Model HTML gerenciado</span><span class="sxs-lookup"><span data-stu-id="6b4c6-102">Using the Managed HTML Document Object Model</span></span>
<span data-ttu-id="6b4c6-103">O Modelo de Objeto do Documento (DOM) HTML gerenciado fornece um wrapper com base no [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] para as classes HTML expostas pelo Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="6b4c6-103">The managed HTML document object model (DOM) provides a wrapper based on the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] for the HTML classes exposed by Internet Explorer.</span></span> <span data-ttu-id="6b4c6-104">Use essas classes para manipular páginas HTML hospedadas no <xref:System.Windows.Forms.WebBrowser> controle, ou para criar novas páginas desde o início.</span><span class="sxs-lookup"><span data-stu-id="6b4c6-104">Use these classes to manipulate HTML pages hosted in the <xref:System.Windows.Forms.WebBrowser> control, or to build new pages from the beginning.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6b4c6-105">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="6b4c6-105">In This Section</span></span>  
 [<span data-ttu-id="6b4c6-106">Como: Acessar o modelo de objeto do documento HTML gerenciado</span><span class="sxs-lookup"><span data-stu-id="6b4c6-106">How to: Access the Managed HTML Document Object Model</span></span>](../../../../docs/framework/winforms/controls/how-to-access-the-managed-html-document-object-model.md)  
 <span data-ttu-id="6b4c6-107">Descreve como obter uma instância válida do <xref:System.Windows.Forms.HtmlDocument> de um aplicativo de formulários do Windows ou um <xref:System.Windows.Forms.UserControl> hospedado no Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="6b4c6-107">Describes how to obtain a valid instance of <xref:System.Windows.Forms.HtmlDocument> from either a Windows Forms application or a <xref:System.Windows.Forms.UserControl> hosted in Internet Explorer.</span></span>  
  
 [<span data-ttu-id="6b4c6-108">Como: Acessar a fonte HTML no modelo de objeto do documento HTML gerenciado</span><span class="sxs-lookup"><span data-stu-id="6b4c6-108">How to: Access the HTML Source in the Managed HTML Document Object Model</span></span>](../../../../docs/framework/winforms/controls/how-to-access-the-html-source-in-the-managed-html-document-object-model.md)  
 <span data-ttu-id="6b4c6-109">Descreve como obter o a fonte HTML original, sem modificações e como obter a fonte "ativa" que reflete o estado atual do DOM.</span><span class="sxs-lookup"><span data-stu-id="6b4c6-109">Describes how to obtain the original, unmodified HTML source, and how to obtain the "live" source that reflects the current state of the DOM.</span></span>  
  
 [<span data-ttu-id="6b4c6-110">Como: Alterar estilos em um elemento no modelo de objeto do documento HTML gerenciado</span><span class="sxs-lookup"><span data-stu-id="6b4c6-110">How to: Change Styles on an Element in the Managed HTML Document Object Model</span></span>](../../../../docs/framework/winforms/controls/how-to-change-styles-on-an-element-in-the-managed-html-document-object-model.md)  
 <span data-ttu-id="6b4c6-111">Descreve como manipular estilos que são usados para controlar a exibição visual de elementos.</span><span class="sxs-lookup"><span data-stu-id="6b4c6-111">Describes how to manipulate styles, which are used to control the visual display of elements.</span></span>  
  
 [<span data-ttu-id="6b4c6-112">Acessando quadros no Modelo de Objeto do Documento HTML gerenciado</span><span class="sxs-lookup"><span data-stu-id="6b4c6-112">Accessing Frames in the Managed HTML Document Object Model</span></span>](../../../../docs/framework/winforms/controls/accessing-frames-in-the-managed-html-document-object-model.md)  
 <span data-ttu-id="6b4c6-113">Descreve quais são os quadros e conjuntos de quadros e como acessar o DOM de um quadro.</span><span class="sxs-lookup"><span data-stu-id="6b4c6-113">Describes what frames and framesets are, and how to access the DOM of a frame.</span></span>  
  
 [<span data-ttu-id="6b4c6-114">Acessando membros não expostos no Modelo de Objeto do Documento HTML gerenciado</span><span class="sxs-lookup"><span data-stu-id="6b4c6-114">Accessing Unexposed Members on the Managed HTML Document Object Model</span></span>](../../../../docs/framework/winforms/controls/accessing-unexposed-members-on-the-managed-html-document-object-model.md)  
 <span data-ttu-id="6b4c6-115">Descreve como acessar membros do DOM subjacente que não tenham um equivalente gerenciado.</span><span class="sxs-lookup"><span data-stu-id="6b4c6-115">Describes how to access members of the underlying DOM that do not have a managed equivalent.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="6b4c6-116">Referência</span><span class="sxs-lookup"><span data-stu-id="6b4c6-116">Reference</span></span>  
 <xref:System.Windows.Forms.HtmlDocument>  
  
 <xref:System.Windows.Forms.HtmlElement>  
  
 <xref:System.Windows.Forms.HtmlWindow>  
  
## <a name="related-sections"></a><span data-ttu-id="6b4c6-117">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="6b4c6-117">Related Sections</span></span>  
 [<span data-ttu-id="6b4c6-118">Controle WebBrowser</span><span class="sxs-lookup"><span data-stu-id="6b4c6-118">WebBrowser Control</span></span>](../../../../docs/framework/winforms/controls/webbrowser-control-windows-forms.md)  
  
## <a name="see-also"></a><span data-ttu-id="6b4c6-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6b4c6-119">See also</span></span>
- [<span data-ttu-id="6b4c6-120">Sobre o modelo de objeto DHTML</span><span class="sxs-lookup"><span data-stu-id="6b4c6-120">About the DHTML Object Model</span></span>](https://msdn.microsoft.com/library/default.asp?url=/workshop/author/om/doc_object.asp)
