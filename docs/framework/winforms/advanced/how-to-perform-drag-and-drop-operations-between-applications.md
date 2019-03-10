---
title: 'Como: Executar operações de arrastar e soltar entre aplicativos'
ms.date: 03/30/2017
helpviewer_keywords:
- drag and drop [Windows Forms], between applications
ms.assetid: fa347436-2b12-4dd6-8507-59d7241f6a06
ms.openlocfilehash: 1e9556a69f3f5da4a47c5f5b1a6043a9a73dd8ff
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57713426"
---
# <a name="how-to-perform-drag-and-drop-operations-between-applications"></a><span data-ttu-id="90b2b-102">Como: Executar operações de arrastar e soltar entre aplicativos</span><span class="sxs-lookup"><span data-stu-id="90b2b-102">How to: Perform Drag-and-Drop Operations Between Applications</span></span>
<span data-ttu-id="90b2b-103">Executar operações de arrastar e soltar entre aplicativos não é diferente de ativar esta ação dentro de um aplicativo, desde que os dois aplicativos envolvidos se comportam de acordo com o "contrato" estabelecido entre o <xref:System.Windows.Forms.DragEventArgs.AllowedEffect%2A> e <xref:System.Windows.Forms.DragEventArgs.Effect%2A> Propriedades.</span><span class="sxs-lookup"><span data-stu-id="90b2b-103">Performing drag-and-drop operations between applications is no different than enabling this action within an application, as long as both applications involved behave according to the "contract" established between the <xref:System.Windows.Forms.DragEventArgs.AllowedEffect%2A> and <xref:System.Windows.Forms.DragEventArgs.Effect%2A> properties.</span></span>  
  
 <span data-ttu-id="90b2b-104">No procedimento a seguir, você usará um aplicativo do Windows que você criou e o processador de texto WordPad incluído no sistema operacional Windows para executar operações do tipo "arrastar e soltar" entre aplicativos.</span><span class="sxs-lookup"><span data-stu-id="90b2b-104">In the following procedure, you will use a Windows-based application you create and the WordPad word processor that is included with the Windows operating system to perform drag-and-drop operations between applications.</span></span> <span data-ttu-id="90b2b-105">O WordPad tem um certo conjunto de efeitos permitidos para o texto que está sendo arrastado e solto; o aplicativo do Windows para o qual o código está sendo escrito funcionará com esses efeitos para que as operações do tipo "arrastar e soltar" possam ser concluídas com êxito.</span><span class="sxs-lookup"><span data-stu-id="90b2b-105">WordPad has a certain set of allowed effects for text being dragged and dropped; the Windows-based application you will write code for will work with these effects so that drag-and-drop operations may be completed successfully.</span></span>  
  
### <a name="to-perform-a-drag-and-drop-procedure-between-applications"></a><span data-ttu-id="90b2b-106">Realizar um procedimento do tipo "arrastar e soltar" entre aplicativos</span><span class="sxs-lookup"><span data-stu-id="90b2b-106">To perform a drag-and-drop procedure between applications</span></span>  
  
1.  <span data-ttu-id="90b2b-107">Criar um novo aplicativo Windows Form.</span><span class="sxs-lookup"><span data-stu-id="90b2b-107">Create a new Windows Forms application.</span></span>  
  
2.  <span data-ttu-id="90b2b-108">Adicione um controle <xref:System.Windows.Forms.TextBox> ao seu formulário.</span><span class="sxs-lookup"><span data-stu-id="90b2b-108">Add a <xref:System.Windows.Forms.TextBox> control to your form.</span></span>  
  
3.  <span data-ttu-id="90b2b-109">Configurar o <xref:System.Windows.Forms.TextBox> controle para receber dados descartados.</span><span class="sxs-lookup"><span data-stu-id="90b2b-109">Configure the <xref:System.Windows.Forms.TextBox> control to receive dropped data.</span></span>  
  
     <span data-ttu-id="90b2b-110">Para obter mais informações, confira [Passo a passo: Executando uma operação de arrastar e soltar no Windows Forms](walkthrough-performing-a-drag-and-drop-operation-in-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="90b2b-110">For more information, see [Walkthrough: Performing a Drag-and-Drop Operation in Windows Forms](walkthrough-performing-a-drag-and-drop-operation-in-windows-forms.md).</span></span>  
  
4.  <span data-ttu-id="90b2b-111">Execute seu aplicativo do Windows e, enquanto o aplicativo está em execução, execute o WordPad.</span><span class="sxs-lookup"><span data-stu-id="90b2b-111">Run your Windows-based application, and while the application is running, run WordPad.</span></span>  
  
     <span data-ttu-id="90b2b-112">O WordPad é um editor de texto instalado pelo Windows que permite realizar operações do tipo "arrastar e soltar".</span><span class="sxs-lookup"><span data-stu-id="90b2b-112">WordPad is a text editor installed by Windows that allows drag-and-drop operations.</span></span> <span data-ttu-id="90b2b-113">Ele pode ser acessado pressionando o botão **Iniciar**, selecionando **Executar** e digitando `WordPad` na caixa de texto da caixa de diálogo **Executar** e clicando em **OK**.</span><span class="sxs-lookup"><span data-stu-id="90b2b-113">It is accessible by pressing the **Start** button, selecting **Run**, and then typing `WordPad` into the text box of the **Run** dialog box and clicking **OK**.</span></span>  
  
5.  <span data-ttu-id="90b2b-114">Após abrir o WordPad, digite uma cadeia de caracteres de texto nele.</span><span class="sxs-lookup"><span data-stu-id="90b2b-114">Once WordPad is open, type a string of text into it.</span></span>  
  
6.  <span data-ttu-id="90b2b-115">Usando o mouse, selecione o texto e arraste o texto selecionado para o <xref:System.Windows.Forms.TextBox> controle em seu aplicativo baseado em Windows.</span><span class="sxs-lookup"><span data-stu-id="90b2b-115">Using the mouse, select the text, and then drag the selected text over to the <xref:System.Windows.Forms.TextBox> control in your Windows-based application.</span></span>  
  
     <span data-ttu-id="90b2b-116">Observe que quando você passa o mouse sobre o <xref:System.Windows.Forms.TextBox> controle (e, consequentemente, gerar o <xref:System.Windows.Forms.Control.DragEnter> evento), o cursor muda e você pode soltar o texto selecionado para o <xref:System.Windows.Forms.TextBox> controle.</span><span class="sxs-lookup"><span data-stu-id="90b2b-116">Observe that when you mouse over the <xref:System.Windows.Forms.TextBox> control (and, consequently, raise the <xref:System.Windows.Forms.Control.DragEnter> event), the cursor changes, and you can drop the selected text into the <xref:System.Windows.Forms.TextBox> control.</span></span>  
  
     <span data-ttu-id="90b2b-117">Além disso, você pode configurar seu <xref:System.Windows.Forms.TextBox> controle para permitir que cadeias de caracteres de texto sejam arrastadas e soltas no WordPad.</span><span class="sxs-lookup"><span data-stu-id="90b2b-117">Additionally, you can configure your <xref:System.Windows.Forms.TextBox> control to allow text strings to be dragged and dropped into WordPad.</span></span> <span data-ttu-id="90b2b-118">Para obter mais informações, confira [Passo a passo: Executando uma operação de arrastar e soltar no Windows Forms](walkthrough-performing-a-drag-and-drop-operation-in-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="90b2b-118">For more information, see [Walkthrough: Performing a Drag-and-Drop Operation in Windows Forms](walkthrough-performing-a-drag-and-drop-operation-in-windows-forms.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90b2b-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="90b2b-119">See also</span></span>
- [<span data-ttu-id="90b2b-120">Como: Adicionar dados à área de transferência</span><span class="sxs-lookup"><span data-stu-id="90b2b-120">How to: Add Data to the Clipboard</span></span>](how-to-add-data-to-the-clipboard.md)
- [<span data-ttu-id="90b2b-121">Como: Recuperar dados da área de transferência</span><span class="sxs-lookup"><span data-stu-id="90b2b-121">How to: Retrieve Data from the Clipboard</span></span>](how-to-retrieve-data-from-the-clipboard.md)
- [<span data-ttu-id="90b2b-122">Operações do Tipo "Arrastar e Soltar" e Suporte à Área de Transferência</span><span class="sxs-lookup"><span data-stu-id="90b2b-122">Drag-and-Drop Operations and Clipboard Support</span></span>](drag-and-drop-operations-and-clipboard-support.md)
