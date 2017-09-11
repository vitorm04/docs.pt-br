---
title: "Como: alterar a aparência de um controle DataRepeater (Visual Studio) | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- DataRepeater, customizing
- DataRepeater, changing run time appearance
ms.assetid: 2af6dfce-760b-489e-b863-8da967f315c3
caps.latest.revision: 12
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
ms.openlocfilehash: 25dca0294fd6c721a869966e02a80db6ebde5641
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-change-the-appearance-of-a-datarepeater-control-visual-studio"></a><span data-ttu-id="2924b-102">Como alterar a aparência de um controle DataRepeater (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="2924b-102">How to: Change the Appearance of a DataRepeater Control (Visual Studio)</span></span>
<span data-ttu-id="2924b-103">Você pode alterar a aparência de um <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>controle em tempo de design, definindo propriedades ou em tempo de execução manipulando o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem>evento.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> </xref:Microsoft.VisualBasic.PowerPacks.DataRepeater></span><span class="sxs-lookup"><span data-stu-id="2924b-103">You can change the appearance of a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control at design time by setting properties or at run time by handling the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> event.</span></span>  
  
 <span data-ttu-id="2924b-104">Propriedades que podem ser definidas em tempo de design, quando é selecionada a seção de modelo de item do controle serão repetidas para cada <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem>em tempo de execução.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem></span><span class="sxs-lookup"><span data-stu-id="2924b-104">Properties that you set at design time when the item template section of the control is selected will be repeated for each <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> at run time.</span></span> <span data-ttu-id="2924b-105">Propriedades relacionadas à aparência do <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>próprio controle ficará visível em tempo de execução somente se uma parte do contêiner é deixado descoberto (por exemplo, se o <xref:System.Windows.Forms.Control.Padding%2A>propriedade é definida como um valor grande).</xref:System.Windows.Forms.Control.Padding%2A> </xref:Microsoft.VisualBasic.PowerPacks.DataRepeater></span><span class="sxs-lookup"><span data-stu-id="2924b-105">Appearance-related properties of the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control itself will be visible at run time only if a part of the container is left uncovered (for example, if the <xref:System.Windows.Forms.Control.Padding%2A> property is set to a large value).</span></span>  
  
 <span data-ttu-id="2924b-106">Em tempo de execução propriedades relacionadas à aparência podem ser definidas com base em condições.</span><span class="sxs-lookup"><span data-stu-id="2924b-106">At run time, appearance-related properties can be set based on conditions.</span></span> <span data-ttu-id="2924b-107">Por exemplo, em um aplicativo de planejamento, você pode alterar a cor de plano de fundo de um item para avisar os usuários quando um item está vencido.</span><span class="sxs-lookup"><span data-stu-id="2924b-107">For example, in a scheduling application, you might change the background color of an item to warn users when an item is past due.</span></span> <span data-ttu-id="2924b-108">No <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem>manipulador de eventos, se você definir uma propriedade em uma instrução condicional, como `If…Then`, você também deve usar um `Else` cláusula para especificar a aparência de quando a condição não for atendidos.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem></span><span class="sxs-lookup"><span data-stu-id="2924b-108">In the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> event handler, if you set a property in a conditional statement such as `If…Then`, you must also use an `Else` clause to specify the appearance when the condition is not met.</span></span>  
  
### <a name="to-change-the-appearance-at-design-time"></a><span data-ttu-id="2924b-109">Para alterar a aparência em tempo de design</span><span class="sxs-lookup"><span data-stu-id="2924b-109">To change the appearance at design time</span></span>  
  
1.  <span data-ttu-id="2924b-110">No Windows Forms Designer, selecione a região de modelo (superior) do item do <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>controle.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater></span><span class="sxs-lookup"><span data-stu-id="2924b-110">In the Windows Forms Designer, select the item template (upper) region of the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
2.  <span data-ttu-id="2924b-111">Na janela Propriedades, selecione uma propriedade e altere o valor.</span><span class="sxs-lookup"><span data-stu-id="2924b-111">In the Properties window, select a property and change the value.</span></span> <span data-ttu-id="2924b-112">Propriedades comuns que afetam a aparência incluem <xref:System.Windows.Forms.Control.BackColor%2A>, <xref:System.Windows.Forms.Control.BackgroundImage%2A>, <xref:System.Windows.Forms.Panel.BorderStyle%2A>e <xref:System.Windows.Forms.Control.ForeColor%2A>.</xref:System.Windows.Forms.Control.ForeColor%2A> </xref:System.Windows.Forms.Panel.BorderStyle%2A> </xref:System.Windows.Forms.Control.BackgroundImage%2A> </xref:System.Windows.Forms.Control.BackColor%2A></span><span class="sxs-lookup"><span data-stu-id="2924b-112">Common properties that affect appearance include <xref:System.Windows.Forms.Control.BackColor%2A>, <xref:System.Windows.Forms.Control.BackgroundImage%2A>, <xref:System.Windows.Forms.Panel.BorderStyle%2A>, and <xref:System.Windows.Forms.Control.ForeColor%2A>.</span></span>  
  
### <a name="to-change-the-appearance-at-run-time"></a><span data-ttu-id="2924b-113">Para alterar a aparência em tempo de execução</span><span class="sxs-lookup"><span data-stu-id="2924b-113">To change the appearance at run time</span></span>  
  
1.  <span data-ttu-id="2924b-114">No Editor de código, lista suspensa de eventos, clique em **DrawItem**.</span><span class="sxs-lookup"><span data-stu-id="2924b-114">In the Code Editor, in the Event drop-down list, click **DrawItem**.</span></span>  
  
2.  <span data-ttu-id="2924b-115">No <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem>manipulador de eventos, adicione código para definir as propriedades:</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem></span><span class="sxs-lookup"><span data-stu-id="2924b-115">In the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> event handler, add code to set the properties:</span></span>  
  
     <span data-ttu-id="2924b-116">[!code-cs[&#1; VbPowerPacksDataRepeaterAppearance](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio_1.cs) ] 
     [!code-vb [VbPowerPacksDataRepeaterAppearance n º&1;](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="2924b-116">[!code-cs[VbPowerPacksDataRepeaterAppearance#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio_1.cs)]
 [!code-vb[VbPowerPacksDataRepeaterAppearance#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio_1.vb)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="2924b-117">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2924b-117">Example</span></span>  
 <span data-ttu-id="2924b-118">Algumas personalizações comuns para o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>controle incluem exibindo as linhas em cores alternadas e alterando a cor de um campo com base em uma condição.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater></span><span class="sxs-lookup"><span data-stu-id="2924b-118">Some common customizations for the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control include displaying the rows in alternating colors and changing the color of a field based on a condition.</span></span> <span data-ttu-id="2924b-119">O exemplo a seguir mostra como realizar essas personalizações.</span><span class="sxs-lookup"><span data-stu-id="2924b-119">The following example shows how to perform these customizations.</span></span> <span data-ttu-id="2924b-120">Este exemplo pressupõe que você tenha um <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>controle ligado à tabela Produtos no banco de dados Northwind.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater></span><span class="sxs-lookup"><span data-stu-id="2924b-120">This example assumes that you have a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control that is bound to the Products table in the Northwind database.</span></span>  
  
 <span data-ttu-id="2924b-121">[!code-vb[&#1; VbPowerPacksDataRepeaterAlternateBackColor](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio_2.vb) ] 
 [!code-cs [VbPowerPacksDataRepeaterAlternateBackColor n º&1;](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="2924b-121">[!code-vb[VbPowerPacksDataRepeaterAlternateBackColor#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio_2.vb)]
 [!code-cs[VbPowerPacksDataRepeaterAlternateBackColor#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio_2.cs)]</span></span>  
  
 <span data-ttu-id="2924b-122">Observe que, para ambas essas personalizações, você deve fornecer o código para definir as propriedades de ambos os lados da condição.</span><span class="sxs-lookup"><span data-stu-id="2924b-122">Note that for both of these customizations, you must provide code to set the properties for both sides of the condition.</span></span> <span data-ttu-id="2924b-123">Se você não especificar o `Else` condição, você verá resultados inesperados em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="2924b-123">If you do not specify the `Else` condition, you will see unexpected results at run time.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2924b-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2924b-124">See Also</span></span>  
 <span data-ttu-id="2924b-125"><xref:Microsoft.VisualBasic.PowerPacks.DataRepeater></xref:Microsoft.VisualBasic.PowerPacks.DataRepeater></span><span class="sxs-lookup"><span data-stu-id="2924b-125"><xref:Microsoft.VisualBasic.PowerPacks.DataRepeater></span></span>   
 <span data-ttu-id="2924b-126"><xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem></xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem></span><span class="sxs-lookup"><span data-stu-id="2924b-126"><xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem></span></span>   
<span data-ttu-id="2924b-127"> [Introdução ao controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md) </span><span class="sxs-lookup"><span data-stu-id="2924b-127"> [Introduction to the DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md) </span></span>  
<span data-ttu-id="2924b-128"> [Solucionando problemas do controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md) </span><span class="sxs-lookup"><span data-stu-id="2924b-128"> [Troubleshooting the DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md) </span></span>  
<span data-ttu-id="2924b-129"> [Como: exibir dados associados em um controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md) </span><span class="sxs-lookup"><span data-stu-id="2924b-129"> [How to: Display Bound Data in a DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md) </span></span>  
<span data-ttu-id="2924b-130"> [Como: exibir controles não associados em um controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-display-unbound-controls-in-a-datarepeater-control-visual-studio.md) </span><span class="sxs-lookup"><span data-stu-id="2924b-130"> [How to: Display Unbound Controls in a DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/how-to-display-unbound-controls-in-a-datarepeater-control-visual-studio.md) </span></span>  
<span data-ttu-id="2924b-131"> [Como exibir cabeçalhos de item em um controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-display-item-headers-in-a-datarepeater-control-visual-studio.md)</span><span class="sxs-lookup"><span data-stu-id="2924b-131"> [How to: Display Item Headers in a DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/how-to-display-item-headers-in-a-datarepeater-control-visual-studio.md)</span></span>
