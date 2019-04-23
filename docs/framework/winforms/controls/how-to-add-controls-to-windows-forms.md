---
title: 'Como: Adicionar Controles ao Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Windows Forms controls, adding to form
- controls [Windows Forms], adding
ms.assetid: 2af86001-9d62-4154-87fb-66db2c3cd9fd
ms.openlocfilehash: 04597283a8ff2e21a0f227268671d3605eac6356
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59343578"
---
# <a name="how-to-add-controls-to-windows-forms"></a><span data-ttu-id="6b804-102">Como: Adicionar Controles ao Windows Forms</span><span class="sxs-lookup"><span data-stu-id="6b804-102">How to: Add Controls to Windows Forms</span></span>
<span data-ttu-id="6b804-103">A maioria dos formulários é projetada adicionando controles à superfície do formulário para definir uma interface do usuário (IU).</span><span class="sxs-lookup"><span data-stu-id="6b804-103">Most forms are designed by adding controls to the surface of the form to define a user interface (UI).</span></span> <span data-ttu-id="6b804-104">Um *controle* é um componente em um formulário usado para exibir informações ou aceitar a entrada do usuário.</span><span class="sxs-lookup"><span data-stu-id="6b804-104">A *control* is a component on a form used to display information or accept user input.</span></span> <span data-ttu-id="6b804-105">Para obter mais informações sobre controles, consulte [Controles do Windows Forms](index.md).</span><span class="sxs-lookup"><span data-stu-id="6b804-105">For more information about controls, see [Windows Forms Controls](index.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6b804-106">As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas.</span><span class="sxs-lookup"><span data-stu-id="6b804-106">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="6b804-107">Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**.</span><span class="sxs-lookup"><span data-stu-id="6b804-107">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="6b804-108">Para obter mais informações, confira [Personalizar o IDE do Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="6b804-108">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-draw-a-control-on-a-form"></a><span data-ttu-id="6b804-109">Desenhar um controle em um formulário</span><span class="sxs-lookup"><span data-stu-id="6b804-109">To draw a control on a form</span></span>  
  
1. <span data-ttu-id="6b804-110">Abra o formulário.</span><span class="sxs-lookup"><span data-stu-id="6b804-110">Open the form.</span></span> <span data-ttu-id="6b804-111">Para obter mais informações, confira [Como: Exibir Windows Forms no Designer](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w5yd62ts(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="6b804-111">For more information, see [How to: Display Windows Forms in the Designer](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w5yd62ts(v=vs.100)).</span></span>  
  
2. <span data-ttu-id="6b804-112">Na **Caixa de ferramentas**, clique no controle que você deseja adicionar ao formulário.</span><span class="sxs-lookup"><span data-stu-id="6b804-112">In the **Toolbox**, click the control you want to add to your form.</span></span>  
  
3. <span data-ttu-id="6b804-113">No formulário, clique onde você deseja que o canto superior esquerdo do controle se localize e arraste até onde você deseja posicionar o canto inferior direito do controle.</span><span class="sxs-lookup"><span data-stu-id="6b804-113">On the form, click where you want the upper-left corner of the control to be located, and drag to where you want the lower-right corner of the control to be located.</span></span>  
  
     <span data-ttu-id="6b804-114">O controle é adicionado ao formulário com a localização e o tamanho especificados.</span><span class="sxs-lookup"><span data-stu-id="6b804-114">The control is added to the form with the specified location and size.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="6b804-115">Cada controle tem um tamanho padrão definido.</span><span class="sxs-lookup"><span data-stu-id="6b804-115">Each control has a default size defined.</span></span> <span data-ttu-id="6b804-116">Você pode adicionar um controle ao seu formulário no tamanho de padrão do controle arrastando-o da **Caixa de ferramentas** para o formulário.</span><span class="sxs-lookup"><span data-stu-id="6b804-116">You can add a control to your form in the control's default size by dragging it from the **Toolbox** to the form.</span></span>  
  
### <a name="to-drag-a-control-to-a-form"></a><span data-ttu-id="6b804-117">Arrastar um controle para um formulário</span><span class="sxs-lookup"><span data-stu-id="6b804-117">To drag a control to a form</span></span>  
  
1. <span data-ttu-id="6b804-118">Abra o formulário.</span><span class="sxs-lookup"><span data-stu-id="6b804-118">Open the form.</span></span> <span data-ttu-id="6b804-119">Para obter mais informações, confira [Como: Exibir Windows Forms no Designer](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w5yd62ts(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="6b804-119">For more information, see [How to: Display Windows Forms in the Designer](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w5yd62ts(v=vs.100)).</span></span>  
  
2. <span data-ttu-id="6b804-120">Na **Caixa de ferramentas**, clique no controle que você deseja e arraste-o para o formulário.</span><span class="sxs-lookup"><span data-stu-id="6b804-120">In the **Toolbox**, click the control you want and drag it to your form.</span></span>  
  
     <span data-ttu-id="6b804-121">O controle é adicionado ao formulário na localização e tamanho especificados.</span><span class="sxs-lookup"><span data-stu-id="6b804-121">The control is added to the form at the specified location in its default size.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="6b804-122">Você pode clicar duas vezes em um controle na **Caixa de ferramentas** para adicioná-lo ao canto superior esquerdo do formulário com seu tamanho padrão.</span><span class="sxs-lookup"><span data-stu-id="6b804-122">You can double-click a control in the **Toolbox** to add it to the upper-left corner of the form in its default size.</span></span>  
  
     <span data-ttu-id="6b804-123">Você também pode adicionar controles dinamicamente a um formulário no tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="6b804-123">You can also add controls dynamically to a form at run time.</span></span> <span data-ttu-id="6b804-124">No exemplo de código a seguir, uma <xref:System.Windows.Forms.TextBox> controle será adicionado ao formulário quando um <xref:System.Windows.Forms.Button> controle é clicado.</span><span class="sxs-lookup"><span data-stu-id="6b804-124">In the following code example, a <xref:System.Windows.Forms.TextBox> control will be added to the form when a <xref:System.Windows.Forms.Button> control is clicked.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="6b804-125">O procedimento a seguir requer a existência de um formulário com um controle **Botão**, `Button1`, já inserido nele.</span><span class="sxs-lookup"><span data-stu-id="6b804-125">The following procedure requires the existence of a form with a **Button** control, `Button1`, already placed on it.</span></span>  
  
### <a name="to-add-a-control-to-a-form-programmatically"></a><span data-ttu-id="6b804-126">Adicionar um controle a um formulário com programação</span><span class="sxs-lookup"><span data-stu-id="6b804-126">To add a control to a form programmatically</span></span>  
  
1. <span data-ttu-id="6b804-127">No método que trata o evento `Click` do botão na classe do formulário, insira código semelhante ao seguinte para adicionar uma referência à variável do controle, defina o `Location` do controle e adicione o controle.</span><span class="sxs-lookup"><span data-stu-id="6b804-127">In the method that handles the button's `Click` event within your form's class, insert code similar to the following to add a reference to your control variable, set the control's `Location`, and add the control.</span></span>  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click  
       Dim MyText As New TextBox()  
       MyText.Location = New Point(25, 25)  
       Me.Controls.Add(MyText)  
    End Sub  
    ```  
  
    ```csharp  
    private void button1_Click(object sender, System.EventArgs e)   
    {  
       TextBox myText = new TextBox();  
       myText.Location = new Point(25,25);  
       this.Controls.Add (myText);  
    }  
    ```  
  
    ```cpp  
    private:  
      System::Void button1_Click(System::Object ^  sender,  
        System::EventArgs ^  e)  
      {  
        TextBox ^ myText = gcnew TextBox();  
        myText->Location = Point(25,25);  
        this->Controls->Add(myText);  
      }  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="6b804-128">Você também pode adicionar código para inicializar outras propriedades do controle.</span><span class="sxs-lookup"><span data-stu-id="6b804-128">You can also add code to initialize other properties of the control.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="6b804-129">Você poderia expor seu computador local a um risco de segurança por meio da rede referenciando um `UserControl` mal-intencionado.</span><span class="sxs-lookup"><span data-stu-id="6b804-129">You might expose your local computer to a security risk through the network by referencing a malicious `UserControl`.</span></span> <span data-ttu-id="6b804-130">Isso seria um problemas apenas no caso de uma pessoa mal-intencionada criar um controle personalizado prejudicial e você adicioná-lo por engano ao seu projeto.</span><span class="sxs-lookup"><span data-stu-id="6b804-130">This would only be a concern in the case of a malicious person creating a damaging custom control, followed by you mistakenly adding it to your project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b804-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6b804-131">See also</span></span>

- [<span data-ttu-id="6b804-132">Controles dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="6b804-132">Windows Forms Controls</span></span>](index.md)
- [<span data-ttu-id="6b804-133">Organizando Controles nos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="6b804-133">Arranging Controls on Windows Forms</span></span>](arranging-controls-on-windows-forms.md)
- [<span data-ttu-id="6b804-134">Como: Redimensionar controles nos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="6b804-134">How to: Resize Controls on Windows Forms</span></span>](how-to-resize-controls-on-windows-forms.md)
- [<span data-ttu-id="6b804-135">Como: Definir o texto exibido pelo controle de um Windows Forms</span><span class="sxs-lookup"><span data-stu-id="6b804-135">How to: Set the Text Displayed by a Windows Forms Control</span></span>](how-to-set-the-text-displayed-by-a-windows-forms-control.md)
- [<span data-ttu-id="6b804-136">Controles a serem usados nos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="6b804-136">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
