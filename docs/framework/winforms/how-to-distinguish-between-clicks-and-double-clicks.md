---
title: Como distinguir entre cliques e cliques duplos
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- mouse [Windows Forms], click
- mouse [Windows Forms], double-click
- mouse clicks [Windows Forms], single versus double
ms.assetid: d836ac8c-85bc-4f3a-a761-8aee03dc682c
caps.latest.revision: 13
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: b8bd383c94afb5c8bb3574e2fee80bca8c4a9143
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-distinguish-between-clicks-and-double-clicks"></a><span data-ttu-id="9b217-102">Como distinguir entre cliques e cliques duplos</span><span class="sxs-lookup"><span data-stu-id="9b217-102">How to: Distinguish Between Clicks and Double-Clicks</span></span>
<span data-ttu-id="9b217-103">Normalmente, um único *clique* inicia uma interface do usuário e um *clique duplo* estende a ação.</span><span class="sxs-lookup"><span data-stu-id="9b217-103">Typically, a single *click* initiates a user interface (UI) action and a *double-click* extends the action.</span></span> <span data-ttu-id="9b217-104">Por exemplo, um clique normalmente seleciona um item e um clique duplo edita o item selecionado.</span><span class="sxs-lookup"><span data-stu-id="9b217-104">For example, one click usually selects an item, and a double-click edits the selected item.</span></span> <span data-ttu-id="9b217-105">No entanto, eventos de clique de formulários do Windows não acomodam facilmente um cenário onde um clique e um clique duplo executam ações incompatíveis, porque uma ação ligados a <xref:System.Windows.Forms.Control.Click> ou <xref:System.Windows.Forms.Control.MouseClick> evento é executado antes da ação ligada para o <xref:System.Windows.Forms.Control.DoubleClick>ou <xref:System.Windows.Forms.Control.MouseDoubleClick> eventos.</span><span class="sxs-lookup"><span data-stu-id="9b217-105">However, the Windows Forms click events do not easily accommodate a scenario where a click and a double-click perform incompatible actions, because an action tied to the <xref:System.Windows.Forms.Control.Click> or <xref:System.Windows.Forms.Control.MouseClick> event is performed before the action tied to the <xref:System.Windows.Forms.Control.DoubleClick> or <xref:System.Windows.Forms.Control.MouseDoubleClick> event.</span></span> <span data-ttu-id="9b217-106">Este tópico demonstra duas soluções para esse problema.</span><span class="sxs-lookup"><span data-stu-id="9b217-106">This topic demonstrates two solutions to this problem.</span></span> <span data-ttu-id="9b217-107">Uma solução é manipular o evento de clique duplo e reverter as ações no tratamento de evento de clique.</span><span class="sxs-lookup"><span data-stu-id="9b217-107">One solution is to handle the double-click event and roll back the actions in the handling of the click event.</span></span> <span data-ttu-id="9b217-108">Em situações raras convém simular clique e clique duas vezes em comportamento manipulando o <xref:System.Windows.Forms.Control.MouseDown> eventos e usando o <xref:System.Windows.Forms.SystemInformation.DoubleClickTime%2A> e <xref:System.Windows.Forms.SystemInformation.DoubleClickSize%2A> propriedades da <xref:System.Windows.Forms.SystemInformation> classe.</span><span class="sxs-lookup"><span data-stu-id="9b217-108">In rare situations you may need to simulate click and double-click behavior by handling the <xref:System.Windows.Forms.Control.MouseDown> event and by using the <xref:System.Windows.Forms.SystemInformation.DoubleClickTime%2A> and <xref:System.Windows.Forms.SystemInformation.DoubleClickSize%2A> properties of the <xref:System.Windows.Forms.SystemInformation> class.</span></span> <span data-ttu-id="9b217-109">Medir o tempo entre cliques e se um segundo clique ocorre antes do valor de <xref:System.Windows.Forms.SystemInformation.DoubleClickTime%2A> for atingido e o clique foi dentro de um retângulo definido por <xref:System.Windows.Forms.SystemInformation.DoubleClickSize%2A>, execute a ação de clique duplo; caso contrário, execute a ação de clique.</span><span class="sxs-lookup"><span data-stu-id="9b217-109">You measure the time between clicks and if a second click occurs before the value of <xref:System.Windows.Forms.SystemInformation.DoubleClickTime%2A> is reached and the click is within a rectangle defined by <xref:System.Windows.Forms.SystemInformation.DoubleClickSize%2A>, perform the double-click action; otherwise, perform the click action.</span></span>  
  
### <a name="to-roll-back-a-click-action"></a><span data-ttu-id="9b217-110">Reverter uma ação de clique</span><span class="sxs-lookup"><span data-stu-id="9b217-110">To roll back a click action</span></span>  
  
-   <span data-ttu-id="9b217-111">Verifique se o controle em que você está trabalhando tem um comportamento de clique duplo padrão.</span><span class="sxs-lookup"><span data-stu-id="9b217-111">Ensure that the control you are working with has standard double-click behavior.</span></span> <span data-ttu-id="9b217-112">Se não, habilite o controle com o <xref:System.Windows.Forms.Control.SetStyle%2A> método.</span><span class="sxs-lookup"><span data-stu-id="9b217-112">If not, enable the control with the <xref:System.Windows.Forms.Control.SetStyle%2A> method.</span></span> <span data-ttu-id="9b217-113">Trate o evento de clique duplo e reverta a ação de clique, bem como a ação de clique duplo.</span><span class="sxs-lookup"><span data-stu-id="9b217-113">Handle the double-click event and roll back the click action as well as the double-click action.</span></span> <span data-ttu-id="9b217-114">O exemplo de código a seguir demonstra um como criar um botão personalizado com clique duplo habilitado, bem como reverter a ação de clique no código de tratamento de eventos de clique duplo.</span><span class="sxs-lookup"><span data-stu-id="9b217-114">The following code example demonstrates a how to create a custom button with double-click enabled, as well as how to roll back the click action in the double-click event handling code.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ButtonDoubleClick#1](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ButtonDoubleClick/CS/Form1.cs#1)]
     [!code-vb[System.Windows.Forms.ButtonDoubleClick#1](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ButtonDoubleClick/VB/Form1.vb#1)]  
  
### <a name="to-distinguish-between-clicks-in-the-mousedown-event"></a><span data-ttu-id="9b217-115">Distinguir entre cliques no evento MouseDown</span><span class="sxs-lookup"><span data-stu-id="9b217-115">To distinguish between clicks in the MouseDown event</span></span>  
  
-   <span data-ttu-id="9b217-116">Manipular o <xref:System.Windows.Forms.Control.MouseDown> eventos e determinar o local e o tempo de espaço entre os cliques usando apropriada <xref:System.Windows.Forms.SystemInformation> propriedades e uma <xref:System.Windows.Forms.Timer> componente.</span><span class="sxs-lookup"><span data-stu-id="9b217-116">Handle the <xref:System.Windows.Forms.Control.MouseDown> event and determine the location and time span between clicks using the appropriate <xref:System.Windows.Forms.SystemInformation> properties and a <xref:System.Windows.Forms.Timer> component.</span></span> <span data-ttu-id="9b217-117">Execute a ação apropriada dependendo se ocorreu um clique ou um clique duplo.</span><span class="sxs-lookup"><span data-stu-id="9b217-117">Perform the appropriate action depending on whether a click or double-click takes place.</span></span> <span data-ttu-id="9b217-118">O exemplo de código a seguir demonstra como fazer isso.</span><span class="sxs-lookup"><span data-stu-id="9b217-118">The following code example demonstrates how this can be done.</span></span>  
  
     [!code-cpp[System.Windows.Forms.SingleVersusDoubleClick#0](../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.SingleVersusDoubleClick/cpp/form1.cpp#0)]
     [!code-csharp[System.Windows.Forms.SingleVersusDoubleClick#0](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.SingleVersusDoubleClick/CS/form1.cs#0)]
     [!code-vb[System.Windows.Forms.SingleVersusDoubleClick#0](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.SingleVersusDoubleClick/VB/form1.vb#0)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="9b217-119">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="9b217-119">Compiling the Code</span></span>  
 <span data-ttu-id="9b217-120">Esses exemplos precisam de:</span><span class="sxs-lookup"><span data-stu-id="9b217-120">These examples require:</span></span>  
  
-   <span data-ttu-id="9b217-121">Referências aos assemblies System, System.Drawing e System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="9b217-121">References to the System, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="9b217-122">Para obter informações sobre como criar esses exemplos de linha de comando para o Visual Basic ou Visual c#, consulte [Compilando a partir da linha de comando](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) ou [criação de linha de comando com csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="9b217-122">For information about building these examples from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="9b217-123">Você também pode compilar esses exemplos em [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] colando o código em novos projetos.</span><span class="sxs-lookup"><span data-stu-id="9b217-123">You can also build these examples in [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] by pasting the code into new projects.</span></span>  <span data-ttu-id="9b217-124">Consulte também [Como compilar e executar um exemplo completo de código do Windows Forms usando o Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="9b217-124">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b217-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9b217-125">See Also</span></span>  
 [<span data-ttu-id="9b217-126">Entrada do mouse em um Aplicativo do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="9b217-126">Mouse Input in a Windows Forms Application</span></span>](../../../docs/framework/winforms/mouse-input-in-a-windows-forms-application.md)
