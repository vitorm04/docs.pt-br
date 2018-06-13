---
title: Práticas recomendadas para o controle TableLayoutPanel
ms.date: 03/30/2017
helpviewer_keywords:
- layout [Windows Forms]
- TableLayoutPanel control [Windows Forms], best practices
- forms [Windows Forms], best practices
- AutoSize property [Windows Forms], tableLayoutPanel control
- controls [Windows Forms], sizing
- TableLayoutPanel control [Windows Forms], AutoSize behavior
- layout [Windows Forms], AutoSize
- layout [Windows Forms], best practices
- best practices [Windows Forms], tableLayoutPanel control
- sizing [Windows Forms], automatic
- automatic sizing
ms.assetid: b6706efb-d7a4-45ec-8cf4-08fa993e3afb
ms.openlocfilehash: 40322dc6c5facd4167a4c9ac5c12fdf2a8831b7c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33526446"
---
# <a name="best-practices-for-the-tablelayoutpanel-control"></a><span data-ttu-id="19f53-102">Práticas recomendadas para o controle TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="19f53-102">Best Practices for the TableLayoutPanel Control</span></span>
<span data-ttu-id="19f53-103">O <xref:System.Windows.Forms.TableLayoutPanel> controle fornece recursos avançados de layout que você deve considerar cuidadosamente antes de usar em seus formulários do Windows.</span><span class="sxs-lookup"><span data-stu-id="19f53-103">The <xref:System.Windows.Forms.TableLayoutPanel> control provides powerful layout features that you should consider carefully before using on your Windows Forms.</span></span>  
  
## <a name="recommendations"></a><span data-ttu-id="19f53-104">Recomendações</span><span class="sxs-lookup"><span data-stu-id="19f53-104">Recommendations</span></span>  
 <span data-ttu-id="19f53-105">As recomendações a seguir o ajudarão a usar o <xref:System.Windows.Forms.TableLayoutPanel> controle aproveitando melhor.</span><span class="sxs-lookup"><span data-stu-id="19f53-105">The following recommendations will help you use the <xref:System.Windows.Forms.TableLayoutPanel> control to its best advantage.</span></span>  
  
### <a name="targeted-use"></a><span data-ttu-id="19f53-106">Uso direcionado</span><span class="sxs-lookup"><span data-stu-id="19f53-106">Targeted Use</span></span>  
 <span data-ttu-id="19f53-107">Use o <xref:System.Windows.Forms.TableLayoutPanel> controlar com moderação.</span><span class="sxs-lookup"><span data-stu-id="19f53-107">Use the <xref:System.Windows.Forms.TableLayoutPanel> control sparingly.</span></span> <span data-ttu-id="19f53-108">Você não deve usá-lo em todas as situações que exigem um layout redimensionável.</span><span class="sxs-lookup"><span data-stu-id="19f53-108">You should not use it in all situations that require a resizable layout.</span></span> <span data-ttu-id="19f53-109">A lista a seguir descreve os layouts que se beneficiar mais com o uso do <xref:System.Windows.Forms.TableLayoutPanel> controle:</span><span class="sxs-lookup"><span data-stu-id="19f53-109">The following list describes layouts that benefit most from the use of the <xref:System.Windows.Forms.TableLayoutPanel> control:</span></span>  
  
-   <span data-ttu-id="19f53-110">Layouts em que há várias partes do formulário redimensionadas proporcionalmente umas para outras.</span><span class="sxs-lookup"><span data-stu-id="19f53-110">Layouts in which there are multiple parts of the form that resize proportionally to each other.</span></span>  
  
-   <span data-ttu-id="19f53-111">Layouts que serão modificados ou gerados dinamicamente no tempo de execução, como formulários de entrada de dados que têm campos personalizáveis pelo usuário adicionados ou subtraídos com base nas preferências.</span><span class="sxs-lookup"><span data-stu-id="19f53-111">Layouts that will be modified or generated dynamically at run time, such as data entry forms that have user-customizable fields added or subtracted based on preferences.</span></span>  
  
-   <span data-ttu-id="19f53-112">Layouts que devem permanecer em um tamanho fixo geral.</span><span class="sxs-lookup"><span data-stu-id="19f53-112">Layouts that should remain at an overall fixed size.</span></span> <span data-ttu-id="19f53-113">Por exemplo, você pode ter uma caixa de diálogo que deve permanecer menor do que 800 x 600, mas você precisa dar suporte a cadeias de caracteres localizadas.</span><span class="sxs-lookup"><span data-stu-id="19f53-113">For example, you may have a dialog box that should remain smaller than 800 x 600, but you need to support localized strings.</span></span>  
  
 <span data-ttu-id="19f53-114">A lista a seguir descreve os layouts que não se beneficiam muito do uso de <xref:System.Windows.Forms.TableLayoutPanel> controle:</span><span class="sxs-lookup"><span data-stu-id="19f53-114">The following list describes layouts that do not benefit greatly from using the <xref:System.Windows.Forms.TableLayoutPanel> control:</span></span>  
  
-   <span data-ttu-id="19f53-115">Formulários de entrada de dados simples com uma única coluna de rótulos e uma única coluna de áreas de entrada de texto.</span><span class="sxs-lookup"><span data-stu-id="19f53-115">Simple data entry forms with a single column of labels and a single column of text-entry areas.</span></span>  
  
-   <span data-ttu-id="19f53-116">Formulários com uma única área de exibição grande que deve preencher o espaço disponível quando ocorre um redimensionamento.</span><span class="sxs-lookup"><span data-stu-id="19f53-116">Forms with a single large display area that should fill all the available space when a resize occurs.</span></span> <span data-ttu-id="19f53-117">Um exemplo disso é um formulário que exibe uma única <xref:System.Windows.Forms.PropertyGrid> controle.</span><span class="sxs-lookup"><span data-stu-id="19f53-117">An example of this is a form that displays a single <xref:System.Windows.Forms.PropertyGrid> control.</span></span> <span data-ttu-id="19f53-118">Nesse caso, use ancoragem, pois nada mais deve expandir quando o formulário é redimensionado.</span><span class="sxs-lookup"><span data-stu-id="19f53-118">In this case, use anchoring, because nothing else should expand when the form is resized.</span></span>  
  
 <span data-ttu-id="19f53-119">Escolha cuidadosamente quais controles precisam estar em um <xref:System.Windows.Forms.TableLayoutPanel> controle.</span><span class="sxs-lookup"><span data-stu-id="19f53-119">Choose carefully which controls need to be in a <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span> <span data-ttu-id="19f53-120">Se você tem espaço para crescer em 30% usando ancoragem seu texto, considere usar o <xref:System.Windows.Forms.Control.Anchor%2A> apenas com a propriedade.</span><span class="sxs-lookup"><span data-stu-id="19f53-120">If you have room for your text to grow by 30% using anchoring, consider using the <xref:System.Windows.Forms.Control.Anchor%2A> property only.</span></span> <span data-ttu-id="19f53-121">Se você pode estimar o espaço necessário para o layout, o uso de <xref:System.Windows.Forms.Control.Dock%2A> e <xref:System.Windows.Forms.Control.Anchor%2A> é mais fácil do que os detalhes de espaço restante e <xref:System.Windows.Forms.Control.AutoSize%2A> comportamento.</span><span class="sxs-lookup"><span data-stu-id="19f53-121">If you can estimate the space required by your layout, use of <xref:System.Windows.Forms.Control.Dock%2A> and <xref:System.Windows.Forms.Control.Anchor%2A> is easier than estimating the details of remaining space and <xref:System.Windows.Forms.Control.AutoSize%2A> behavior.</span></span>  
  
 <span data-ttu-id="19f53-122">Em geral, ao projetar o layout com o <xref:System.Windows.Forms.TableLayoutPanel> controlar, mantenha o design mais simples possível.</span><span class="sxs-lookup"><span data-stu-id="19f53-122">In general, when designing your layout with the <xref:System.Windows.Forms.TableLayoutPanel> control, keep the design as simple as possible.</span></span>  
  
### <a name="use-the-document-outline-window"></a><span data-ttu-id="19f53-123">Usar a janela Estrutura de Tópicos de Documento</span><span class="sxs-lookup"><span data-stu-id="19f53-123">Use the Document Outline Window</span></span>  
 <span data-ttu-id="19f53-124">A janela Estrutura de Tópicos de Documento fornece um modo de exibição de árvore do layout, que pode ser usada para manipular as relações pai-filho e de ordem z dos controles.</span><span class="sxs-lookup"><span data-stu-id="19f53-124">The Document Outline window gives you a tree view of your layout, which you can use to manipulate the z-order and parent-child relationships of your controls.</span></span> <span data-ttu-id="19f53-125">No **menu Exibir**, selecione **Outras Janelas** e escolha **Estrutura de Tópicos de Documento**.</span><span class="sxs-lookup"><span data-stu-id="19f53-125">From the **View menu**, select **Other Windows**, then select **Document Outline**.</span></span>  
  
### <a name="avoid-nesting"></a><span data-ttu-id="19f53-126">Evitar aninhamento</span><span class="sxs-lookup"><span data-stu-id="19f53-126">Avoid Nesting</span></span>  
 <span data-ttu-id="19f53-127">Evite aninhamento outros <xref:System.Windows.Forms.TableLayoutPanel> controla dentro de um <xref:System.Windows.Forms.TableLayoutPanel> controle.</span><span class="sxs-lookup"><span data-stu-id="19f53-127">Avoid nesting other <xref:System.Windows.Forms.TableLayoutPanel> controls within a <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span> <span data-ttu-id="19f53-128">Pode ser difícil depurar layouts aninhados.</span><span class="sxs-lookup"><span data-stu-id="19f53-128">Debugging nested layouts can be difficult.</span></span>  
  
### <a name="avoid-visual-inheritance"></a><span data-ttu-id="19f53-129">Evitar herança visual</span><span class="sxs-lookup"><span data-stu-id="19f53-129">Avoid Visual Inheritance</span></span>  
 <span data-ttu-id="19f53-130">O <xref:System.Windows.Forms.TableLayoutPanel> controle não oferece suporte a herança visual no Designer de formulários do Windows.</span><span class="sxs-lookup"><span data-stu-id="19f53-130">The <xref:System.Windows.Forms.TableLayoutPanel> control does not support visual inheritance in the Windows Forms Designer.</span></span> <span data-ttu-id="19f53-131">Um <xref:System.Windows.Forms.TableLayoutPanel> controle em uma classe derivada é exibido como "bloqueada" em tempo de design.</span><span class="sxs-lookup"><span data-stu-id="19f53-131">A <xref:System.Windows.Forms.TableLayoutPanel> control in a derived class appears as "locked" at design time.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19f53-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="19f53-132">See Also</span></span>  
 <xref:System.Windows.Forms.TableLayoutPanel>  
 <xref:System.Windows.Forms.FlowLayoutPanel>
