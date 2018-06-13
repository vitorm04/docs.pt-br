---
title: Como herdar da classe de controle
ms.date: 03/30/2017
helpviewer_keywords:
- inheritance [Windows Forms], Windows Forms custom controls
- Control class [Windows Forms], inheriting from
- custom controls [Windows Forms], inheritance
- OnPaint method [Windows Forms]
- custom controls [Windows Forms], creating
ms.assetid: 46ba0df3-5cf7-443c-a3b4-a72660172476
ms.openlocfilehash: da80d46f27d7cd721af7a9600d2b0cde84876d23
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33534577"
---
# <a name="how-to-inherit-from-the-control-class"></a><span data-ttu-id="34e1d-102">Como herdar da classe de controle</span><span class="sxs-lookup"><span data-stu-id="34e1d-102">How to: Inherit from the Control Class</span></span>
<span data-ttu-id="34e1d-103">Se você quiser criar um controle personalizado completamente a ser usado em um formulário do Windows, você deve herdar do <xref:System.Windows.Forms.Control> classe.</span><span class="sxs-lookup"><span data-stu-id="34e1d-103">If you want to create a completely custom control to use on a Windows Form, you should inherit from the <xref:System.Windows.Forms.Control> class.</span></span> <span data-ttu-id="34e1d-104">Ao herdar do <xref:System.Windows.Forms.Control> classe requer que você executar o planejamento e implementação mais, ele também fornece a maior variedade de opções.</span><span class="sxs-lookup"><span data-stu-id="34e1d-104">While inheriting from the <xref:System.Windows.Forms.Control> class requires that you perform more planning and implementation, it also provides you with the largest range of options.</span></span> <span data-ttu-id="34e1d-105">Ao herdar de <xref:System.Windows.Forms.Control>, herdam a funcionalidade básica que faz com que os controles de trabalho.</span><span class="sxs-lookup"><span data-stu-id="34e1d-105">When inheriting from <xref:System.Windows.Forms.Control>, you inherit the very basic functionality that makes controls work.</span></span> <span data-ttu-id="34e1d-106">A funcionalidade inerente a <xref:System.Windows.Forms.Control> classe manipula a entrada do usuário por meio do teclado e mouse, define os limites e o tamanho do controle, fornece um identificador do windows e fornece segurança e tratamento de mensagens.</span><span class="sxs-lookup"><span data-stu-id="34e1d-106">The functionality inherent in the <xref:System.Windows.Forms.Control> class handles user input through the keyboard and mouse, defines the bounds and size of the control, provides a windows handle, and provides message handling and security.</span></span> <span data-ttu-id="34e1d-107">Ela não incorpora nenhum pintura, que nesse caso é a renderização efetiva da interface gráfica do controle, nem incorpora qualquer funcionalidade de interação do usuário específica.</span><span class="sxs-lookup"><span data-stu-id="34e1d-107">It does not incorporate any painting, which in this case is the actual rendering of the graphical interface of the control, nor does it incorporate any specific user interaction functionality.</span></span> <span data-ttu-id="34e1d-108">Você deve fornecer todos esses aspectos por meio de código personalizado.</span><span class="sxs-lookup"><span data-stu-id="34e1d-108">You must provide all of these aspects through custom code.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="34e1d-109">As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas.</span><span class="sxs-lookup"><span data-stu-id="34e1d-109">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="34e1d-110">Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**.</span><span class="sxs-lookup"><span data-stu-id="34e1d-110">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="34e1d-111">Para obter mais informações, consulte [Personalizando configurações de desenvolvimento no Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="34e1d-111">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-create-a-custom-control"></a><span data-ttu-id="34e1d-112">Criar um controle personalizado</span><span class="sxs-lookup"><span data-stu-id="34e1d-112">To create a custom control</span></span>  
  
1.  <span data-ttu-id="34e1d-113">Crie um novo projeto de **Aplicativos do Windows** ou **Biblioteca de Controle do Windows**.</span><span class="sxs-lookup"><span data-stu-id="34e1d-113">Create a new **Windows Application** or **Windows Control Library** project.</span></span>  
  
2.  <span data-ttu-id="34e1d-114">No menu **Projeto**, escolha **Adicionar Classe**.</span><span class="sxs-lookup"><span data-stu-id="34e1d-114">From the **Project** menu, choose **Add Class**.</span></span>  
  
3.  <span data-ttu-id="34e1d-115">Na caixa de diálogo **Adicionar Novo Item**, clique em **Controle Personalizado**.</span><span class="sxs-lookup"><span data-stu-id="34e1d-115">In the **Add New Item** dialog box, click **Custom Control**.</span></span>  
  
     <span data-ttu-id="34e1d-116">Um novo controle personalizado será adicionado ao projeto.</span><span class="sxs-lookup"><span data-stu-id="34e1d-116">A new custom control is added to your project.</span></span>  
  
4.  <span data-ttu-id="34e1d-117">Pressione F7 para abrir o **Editor de código** para seu controle personalizado.</span><span class="sxs-lookup"><span data-stu-id="34e1d-117">Press F7 to open the **Code Editor** for your custom control.</span></span>  
  
5.  <span data-ttu-id="34e1d-118">Localize o <xref:System.Windows.Forms.Control.OnPaint%2A> método, que estará vazio, exceto uma chamada para o <xref:System.Windows.Forms.Control.OnPaint%2A> método da classe base.</span><span class="sxs-lookup"><span data-stu-id="34e1d-118">Locate the <xref:System.Windows.Forms.Control.OnPaint%2A> method, which will be empty except for a call to the <xref:System.Windows.Forms.Control.OnPaint%2A> method of the base class.</span></span>  
  
6.  <span data-ttu-id="34e1d-119">Modifique o código para incorporar qualquer pintura personalizada desejada ao seu controle.</span><span class="sxs-lookup"><span data-stu-id="34e1d-119">Modify the code to incorporate any custom painting you want for your control.</span></span>  
  
     <span data-ttu-id="34e1d-120">Para obter informações sobre como escrever código para renderizar elementos gráficos para controles, consulte [Pintura e renderização de controle personalizado](../../../../docs/framework/winforms/controls/custom-control-painting-and-rendering.md).</span><span class="sxs-lookup"><span data-stu-id="34e1d-120">For information about writing code to render graphics for controls, see [Custom Control Painting and Rendering](../../../../docs/framework/winforms/controls/custom-control-painting-and-rendering.md).</span></span>  
  
7.  <span data-ttu-id="34e1d-121">Implemente os métodos, propriedades ou eventos personalizados que o controle incorporará.</span><span class="sxs-lookup"><span data-stu-id="34e1d-121">Implement any custom methods, properties, or events that your control will incorporate.</span></span>  
  
8.  <span data-ttu-id="34e1d-122">Salve e teste seu controle.</span><span class="sxs-lookup"><span data-stu-id="34e1d-122">Save and test your control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34e1d-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="34e1d-123">See Also</span></span>  
 [<span data-ttu-id="34e1d-124">Variedades de controles personalizados</span><span class="sxs-lookup"><span data-stu-id="34e1d-124">Varieties of Custom Controls</span></span>](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)  
 [<span data-ttu-id="34e1d-125">Como herdar da classe UserControl</span><span class="sxs-lookup"><span data-stu-id="34e1d-125">How to: Inherit from the UserControl Class</span></span>](../../../../docs/framework/winforms/controls/how-to-inherit-from-the-usercontrol-class.md)  
 [<span data-ttu-id="34e1d-126">Como herdar de controles dos Windows Forms existentes</span><span class="sxs-lookup"><span data-stu-id="34e1d-126">How to: Inherit from Existing Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/how-to-inherit-from-existing-windows-forms-controls.md)  
 [<span data-ttu-id="34e1d-127">Como Criar Controles para o Windows Forms</span><span class="sxs-lookup"><span data-stu-id="34e1d-127">How to: Author Controls for Windows Forms</span></span>](../../../../docs/framework/winforms/controls/how-to-author-controls-for-windows-forms.md)  
 [<span data-ttu-id="34e1d-128">Solucionando problemas de manipuladores de eventos herdados no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="34e1d-128">Troubleshooting Inherited Event Handlers in Visual Basic</span></span>](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)  
 [<span data-ttu-id="34e1d-129">Desenvolvendo controles dos Windows Forms em tempo de design</span><span class="sxs-lookup"><span data-stu-id="34e1d-129">Developing Windows Forms Controls at Design Time</span></span>](../../../../docs/framework/winforms/controls/developing-windows-forms-controls-at-design-time.md)
