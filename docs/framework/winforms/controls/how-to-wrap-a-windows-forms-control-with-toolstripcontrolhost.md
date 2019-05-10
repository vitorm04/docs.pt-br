---
title: 'Como: Encapsular um controle do Windows Forms com ToolStripControlHost'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- ToolStrip control [Windows Forms], wrapping controls
- toolbars [Windows Forms], wrapping controls
- ToolStrip control [Windows Forms], hosting controls
ms.assetid: e2ce4990-661d-4882-a116-8a9eb575dc84
ms.openlocfilehash: b90e47f9cd20d4f963f6223877cefc901f1c0667
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64591561"
---
# <a name="how-to-wrap-a-windows-forms-control-with-toolstripcontrolhost"></a><span data-ttu-id="a05b2-102">Como: Encapsular um controle do Windows Forms com ToolStripControlHost</span><span class="sxs-lookup"><span data-stu-id="a05b2-102">How to: Wrap a Windows Forms Control with ToolStripControlHost</span></span>
<span data-ttu-id="a05b2-103"><xref:System.Windows.Forms.ToolStripControlHost> foi projetado para habilitar a hospedagem de controles de Windows Forms arbitrários, usando o <xref:System.Windows.Forms.ToolStripControlHost> construtor ou estendendo <xref:System.Windows.Forms.ToolStripControlHost> em si.</span><span class="sxs-lookup"><span data-stu-id="a05b2-103"><xref:System.Windows.Forms.ToolStripControlHost> is designed to enable hosting of arbitrary Windows Forms controls by using the <xref:System.Windows.Forms.ToolStripControlHost> constructor or by extending <xref:System.Windows.Forms.ToolStripControlHost> itself.</span></span> <span data-ttu-id="a05b2-104">É mais fácil encapsular o controle estendendo <xref:System.Windows.Forms.ToolStripControlHost> e implementar métodos e propriedades que expõem frequentemente usadas propriedades e métodos do controle.</span><span class="sxs-lookup"><span data-stu-id="a05b2-104">It is easier to wrap the control by extending <xref:System.Windows.Forms.ToolStripControlHost> and implementing properties and methods that expose frequently used properties and methods of the control.</span></span> <span data-ttu-id="a05b2-105">Você também pode expor eventos de controle no <xref:System.Windows.Forms.ToolStripControlHost> nível.</span><span class="sxs-lookup"><span data-stu-id="a05b2-105">You can also expose events for the control at the <xref:System.Windows.Forms.ToolStripControlHost> level.</span></span>  
  
### <a name="to-host-a-control-in-a-toolstripcontrolhost-by-derivation"></a><span data-ttu-id="a05b2-106">Para hospedar um controle em um ToolStripControlHost por derivação</span><span class="sxs-lookup"><span data-stu-id="a05b2-106">To host a control in a ToolStripControlHost by derivation</span></span>  
  
1. <span data-ttu-id="a05b2-107">Estender <xref:System.Windows.Forms.ToolStripControlHost>.</span><span class="sxs-lookup"><span data-stu-id="a05b2-107">Extend <xref:System.Windows.Forms.ToolStripControlHost>.</span></span> <span data-ttu-id="a05b2-108">Implemente um construtor padrão que chama o construtor de classe base que passa no controle desejado.</span><span class="sxs-lookup"><span data-stu-id="a05b2-108">Implement a default constructor that calls the base class constructor passing in the desired control.</span></span>  
  
     [!code-cpp[System.Windows.Forms.ToolStripControlHost#10](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CPP/form1.cpp#10)]
     [!code-csharp[System.Windows.Forms.ToolStripControlHost#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CS/form1.cs#10)]
     [!code-vb[System.Windows.Forms.ToolStripControlHost#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/VB/form1.vb#10)]  
  
2. <span data-ttu-id="a05b2-109">Declare uma propriedade do mesmo tipo que o controle encapsulado e retorne `Control` como o tipo correto de controle no acessador de propriedade.</span><span class="sxs-lookup"><span data-stu-id="a05b2-109">Declare a property of the same type as the wrapped control and return `Control` as the correct type of control in the property's accessor.</span></span>  
  
     [!code-cpp[System.Windows.Forms.ToolStripControlHost#11](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CPP/form1.cpp#11)]
     [!code-csharp[System.Windows.Forms.ToolStripControlHost#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CS/form1.cs#11)]
     [!code-vb[System.Windows.Forms.ToolStripControlHost#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/VB/form1.vb#11)]  
  
3. <span data-ttu-id="a05b2-110">Exponha outras propriedades e métodos usados com frequência do controle encapsulado com propriedades e métodos na classe estendida.</span><span class="sxs-lookup"><span data-stu-id="a05b2-110">Expose other frequently used properties and methods of the wrapped control with properties and methods in the extended class.</span></span>  
  
     [!code-cpp[System.Windows.Forms.ToolStripControlHost#12](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CPP/form1.cpp#12)]
     [!code-csharp[System.Windows.Forms.ToolStripControlHost#12](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CS/form1.cs#12)]
     [!code-vb[System.Windows.Forms.ToolStripControlHost#12](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/VB/form1.vb#12)]  
  
4. <span data-ttu-id="a05b2-111">Opcionalmente, substituir os <xref:System.Windows.Forms.ToolStripControlHost.OnSubscribeControlEvents%2A>, e <xref:System.Windows.Forms.ToolStripControlHost.OnUnsubscribeControlEvents%2A> métodos e adicionar os eventos de controle que você deseja expor.</span><span class="sxs-lookup"><span data-stu-id="a05b2-111">Optionally, override the <xref:System.Windows.Forms.ToolStripControlHost.OnSubscribeControlEvents%2A>, and <xref:System.Windows.Forms.ToolStripControlHost.OnUnsubscribeControlEvents%2A> methods and add the control events you want to expose.</span></span>  
  
     [!code-cpp[System.Windows.Forms.ToolStripControlHost#16](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CPP/form1.cpp#16)]
     [!code-csharp[System.Windows.Forms.ToolStripControlHost#16](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CS/form1.cs#16)]
     [!code-vb[System.Windows.Forms.ToolStripControlHost#16](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/VB/form1.vb#16)]  
  
5. <span data-ttu-id="a05b2-112">Forneça o encapsulamento necessário para os eventos que deseja expor.</span><span class="sxs-lookup"><span data-stu-id="a05b2-112">Provide the necessary wrapping for the events you want to expose.</span></span>  
  
     [!code-cpp[System.Windows.Forms.ToolStripControlHost#17](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CPP/form1.cpp#17)]
     [!code-csharp[System.Windows.Forms.ToolStripControlHost#17](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CS/form1.cs#17)]
     [!code-vb[System.Windows.Forms.ToolStripControlHost#17](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/VB/form1.vb#17)]  
  
## <a name="example"></a><span data-ttu-id="a05b2-113">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a05b2-113">Example</span></span>  
 [!code-cpp[System.Windows.Forms.ToolStripControlHost#13](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CPP/form1.cpp#13)]
 [!code-csharp[System.Windows.Forms.ToolStripControlHost#13](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CS/form1.cs#13)]
 [!code-vb[System.Windows.Forms.ToolStripControlHost#13](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/VB/form1.vb#13)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="a05b2-114">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="a05b2-114">Compiling the Code</span></span>  
  
- <span data-ttu-id="a05b2-115">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="a05b2-115">This example requires:</span></span>  
  
- <span data-ttu-id="a05b2-116">Referências aos assemblies Sistema e System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="a05b2-116">References to the System and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="a05b2-117">Para obter informações sobre como compilar este exemplo da linha de comando para o Visual Basic ou Visual c#, consulte [compilando da linha de comando](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) ou [criação de linha de comando com csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="a05b2-117">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="a05b2-118">Você também pode criar este exemplo no Visual Studio colando o código em um novo projeto.</span><span class="sxs-lookup"><span data-stu-id="a05b2-118">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a05b2-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a05b2-119">See also</span></span>

- <xref:System.Windows.Forms.ToolStripControlHost>
- [<span data-ttu-id="a05b2-120">Visão geral do controle ToolStrip</span><span class="sxs-lookup"><span data-stu-id="a05b2-120">ToolStrip Control Overview</span></span>](toolstrip-control-overview-windows-forms.md)
- [<span data-ttu-id="a05b2-121">Arquitetura de controle do ToolStrip</span><span class="sxs-lookup"><span data-stu-id="a05b2-121">ToolStrip Control Architecture</span></span>](toolstrip-control-architecture.md)
- [<span data-ttu-id="a05b2-122">Resumo da tecnologia de ToolStrip</span><span class="sxs-lookup"><span data-stu-id="a05b2-122">ToolStrip Technology Summary</span></span>](toolstrip-technology-summary.md)
