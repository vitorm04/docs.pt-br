---
title: 'Como: Responder a alterações de esquema de fontes em um aplicativo do Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Forms, font scheme changes
ms.assetid: 4db27702-22e7-43bf-a07d-9a004549853c
ms.openlocfilehash: 4c34a65ed8ddabfb99451e055048502cb7617e4f
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57715965"
---
# <a name="how-to-respond-to-font-scheme-changes-in-a-windows-forms-application"></a><span data-ttu-id="854fa-102">Como: Responder a alterações de esquema de fontes em um aplicativo do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="854fa-102">How to: Respond to Font Scheme Changes in a Windows Forms Application</span></span>
<span data-ttu-id="854fa-103">Nos sistemas operacionais Windows, um usuário pode alterar as configurações de fonte de todo o sistema para tornar a fonte padrão maior ou menor.</span><span class="sxs-lookup"><span data-stu-id="854fa-103">In the Windows operating systems, a user can change the system-wide font settings to make the default font appear larger or smaller.</span></span> <span data-ttu-id="854fa-104">A alteração dessas configurações de fonte é essencial para usuários com deficiência visual, que requerem letras maiores para ler o texto em suas telas.</span><span class="sxs-lookup"><span data-stu-id="854fa-104">Changing these font settings is critical for users who are visually impaired and require larger type to read the text on their screens.</span></span> <span data-ttu-id="854fa-105">É possível ajustar seu aplicativo do Windows Forms para reagir a essas alterações aumentando ou diminuindo o tamanho do formulário e todo o texto contido nele sempre que o esquema de fontes for alterado.</span><span class="sxs-lookup"><span data-stu-id="854fa-105">You can adjust your Windows Forms application to react to these changes by increasing or decreasing the size of the form and all contained text whenever the font scheme changes.</span></span> <span data-ttu-id="854fa-106">Se desejar que seu formulário acomode as alterações em tamanhos de fonte dinamicamente, será possível adicionar código a ele.</span><span class="sxs-lookup"><span data-stu-id="854fa-106">If you want your form to accommodate changes in font sizes dynamically, you can add code to your form.</span></span>  
  
 <span data-ttu-id="854fa-107">Normalmente, a fonte padrão usada pelo Windows Forms é a fonte retornada pela <xref:Microsoft.Win32> chamada de namespace para `GetStockObject(DEFAULT_GUI_FONT)`.</span><span class="sxs-lookup"><span data-stu-id="854fa-107">Typically, the default font used by Windows Forms is the font returned by the <xref:Microsoft.Win32> namespace call to `GetStockObject(DEFAULT_GUI_FONT)`.</span></span> <span data-ttu-id="854fa-108">A fonte retornada por essa chamada muda apenas quando a resolução da tela é alterada.</span><span class="sxs-lookup"><span data-stu-id="854fa-108">The font returned by this call only changes when the screen resolution changes.</span></span> <span data-ttu-id="854fa-109">Conforme mostrado no procedimento a seguir, o código deve alterar a fonte padrão para <xref:System.Drawing.SystemFonts.IconTitleFont%2A> para responder a alterações no tamanho da fonte.</span><span class="sxs-lookup"><span data-stu-id="854fa-109">As shown in the following procedure, your code must change the default font to <xref:System.Drawing.SystemFonts.IconTitleFont%2A> to respond to changes in font size.</span></span>  
  
### <a name="to-use-the-desktop-font-and-respond-to-font-scheme-changes"></a><span data-ttu-id="854fa-110">Utilizar a fonte da área de trabalho e responder a alterações no esquema de fontes</span><span class="sxs-lookup"><span data-stu-id="854fa-110">To use the desktop font and respond to font scheme changes</span></span>  
  
1.  <span data-ttu-id="854fa-111">Crie seu formulário e adicione os controles desejados a ele.</span><span class="sxs-lookup"><span data-stu-id="854fa-111">Create your form, and add the controls you want to it.</span></span> <span data-ttu-id="854fa-112">Para obter mais informações, confira [Como: Criar um aplicativo de formulários do Windows da linha de comando](how-to-create-a-windows-forms-application-from-the-command-line.md) e [controles a serem usados nos Windows Forms](./controls/controls-to-use-on-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="854fa-112">For more information, see [How to: Create a Windows Forms Application from the Command Line](how-to-create-a-windows-forms-application-from-the-command-line.md) and [Controls to Use on Windows Forms](./controls/controls-to-use-on-windows-forms.md).</span></span>  
  
2.  <span data-ttu-id="854fa-113">Adicione uma referência para o <xref:Microsoft.Win32> namespace ao seu código.</span><span class="sxs-lookup"><span data-stu-id="854fa-113">Add a reference to the <xref:Microsoft.Win32> namespace to your code.</span></span>  
  
     [!code-csharp[WinFormsAutoScaling#2](~/samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#2)]
     [!code-vb[WinFormsAutoScaling#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#2)]  
  
3.  <span data-ttu-id="854fa-114">Adicione o seguinte código ao construtor do formulário para ligar manipuladores de eventos necessários e para alterar a fonte padrão em uso do formulário.</span><span class="sxs-lookup"><span data-stu-id="854fa-114">Add the following code to the constructor of your form to hook up required event handlers, and to change the default font in use for the form.</span></span>  
  
     [!code-csharp[WinFormsAutoScaling#3](~/samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#3)]
     [!code-vb[WinFormsAutoScaling#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#3)]  
  
4.  <span data-ttu-id="854fa-115">Implemente um manipulador para o <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged> evento que faz com que o formulário dimensionar automaticamente quando o <xref:Microsoft.Win32.UserPreferenceCategory.Window> as alterações de categoria.</span><span class="sxs-lookup"><span data-stu-id="854fa-115">Implement a handler for the <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged> event that causes the form to scale automatically when the <xref:Microsoft.Win32.UserPreferenceCategory.Window> category changes.</span></span>  
  
     [!code-csharp[WinFormsAutoScaling#4](~/samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#4)]
     [!code-vb[WinFormsAutoScaling#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#4)]  
  
5.  <span data-ttu-id="854fa-116">Finalmente, implemente um manipulador para o <xref:System.Windows.Forms.Form.FormClosing> evento que dispara o <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged> manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="854fa-116">Finally, implement a handler for the <xref:System.Windows.Forms.Form.FormClosing> event that detaches the <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged> event handler.</span></span>  
  
     > [!IMPORTANT]
     > <span data-ttu-id="854fa-117">Uma falha na inclusão desse código fará com que ocorra vazamento de memória no aplicativo.</span><span class="sxs-lookup"><span data-stu-id="854fa-117">Failure to include this code will cause your application to leak memory.</span></span>  
  
     [!code-csharp[WinFormsAutoScaling#5](~/samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#5)]
     [!code-vb[WinFormsAutoScaling#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#5)]  
  
6.  <span data-ttu-id="854fa-118">Compile e execute o código.</span><span class="sxs-lookup"><span data-stu-id="854fa-118">Compile and run the code.</span></span>  
  
### <a name="to-manually-change-the-font-scheme-in-windows-xp"></a><span data-ttu-id="854fa-119">Alterar manualmente o esquema de fontes no Windows XP</span><span class="sxs-lookup"><span data-stu-id="854fa-119">To manually change the font scheme in Windows XP</span></span>  
  
1.  <span data-ttu-id="854fa-120">Enquanto o Aplicativo do Windows Forms está em execução, clique com o botão direito do mouse na área de trabalho do Windows e escolha **Propriedades** no menu de atalho.</span><span class="sxs-lookup"><span data-stu-id="854fa-120">While your Windows Forms application is running, right-click the Windows desktop and choose **Properties** from the shortcut menu.</span></span>  
  
2.  <span data-ttu-id="854fa-121">Na caixa de diálogo **Propriedades de Exibição**, clique na guia **Aparência**.</span><span class="sxs-lookup"><span data-stu-id="854fa-121">In the **Display Properties** dialog box, click the **Appearance** tab.</span></span>  
  
3.  <span data-ttu-id="854fa-122">Na caixa de listagem suspensa **Tamanho da Fonte**, selecione um novo tamanho da fonte.</span><span class="sxs-lookup"><span data-stu-id="854fa-122">From the **Font Size** drop-down list box, select a new font size.</span></span>  
  
     <span data-ttu-id="854fa-123">Você observará que o formulário agora reage a alterações de tempo de execução no esquema de fontes da área de trabalho.</span><span class="sxs-lookup"><span data-stu-id="854fa-123">You'll notice that the form now reacts to run-time changes in the desktop font scheme.</span></span> <span data-ttu-id="854fa-124">Quando o usuário altera entre **Normal**, **Fontes Grandes** e **Fontes Extra Grandes**, o formulário muda a fonte e ajusta a escala corretamente.</span><span class="sxs-lookup"><span data-stu-id="854fa-124">When the user changes between **Normal**, **Large Fonts**, and **Extra Large Fonts**, the form changes font and scales correctly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="854fa-125">Exemplo</span><span class="sxs-lookup"><span data-stu-id="854fa-125">Example</span></span>  
 [!code-csharp[WinFormsAutoScaling#1](~/samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#1)]
 [!code-vb[WinFormsAutoScaling#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#1)]  
  
 <span data-ttu-id="854fa-126">O construtor nesse exemplo de código contém uma chamada para `InitializeComponent`, definida ao criar um novo projeto do Windows Forms no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="854fa-126">The constructer in this code example contains a call to `InitializeComponent`, which is defined when you create a new Windows Forms project in Visual Studio.</span></span> <span data-ttu-id="854fa-127">Remova essa linha de código se estiver compilando um aplicativo na linha de comando.</span><span class="sxs-lookup"><span data-stu-id="854fa-127">Remove this line of code if you are building your application on the command line.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="854fa-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="854fa-128">See also</span></span>
- <xref:System.Windows.Forms.ContainerControl.PerformAutoScale%2A>
- [<span data-ttu-id="854fa-129">Dimensionamento automático no Windows Forms</span><span class="sxs-lookup"><span data-stu-id="854fa-129">Automatic Scaling in Windows Forms</span></span>](automatic-scaling-in-windows-forms.md)
