---
title: 'Como: Herdar da classe Control'
ms.date: 03/30/2017
helpviewer_keywords:
- inheritance [Windows Forms], Windows Forms custom controls
- Control class [Windows Forms], inheriting from
- custom controls [Windows Forms], inheritance
- OnPaint method [Windows Forms]
- custom controls [Windows Forms], creating
ms.assetid: 46ba0df3-5cf7-443c-a3b4-a72660172476
ms.openlocfilehash: 0cb63be6774fd82cd94a1bc59b8a1025efa47df5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966575"
---
# <a name="how-to-inherit-from-the-control-class"></a><span data-ttu-id="4d4ec-102">Como: Herdar da classe Control</span><span class="sxs-lookup"><span data-stu-id="4d4ec-102">How to: Inherit from the Control Class</span></span>
<span data-ttu-id="4d4ec-103">Se você quiser criar um controle completamente personalizado para usar em um Windows Form, deverá herdar da <xref:System.Windows.Forms.Control> classe.</span><span class="sxs-lookup"><span data-stu-id="4d4ec-103">If you want to create a completely custom control to use on a Windows Form, you should inherit from the <xref:System.Windows.Forms.Control> class.</span></span> <span data-ttu-id="4d4ec-104">Embora a <xref:System.Windows.Forms.Control> herança da classe exija que você execute mais planejamento e implementação, ela também fornece a maior variedade de opções.</span><span class="sxs-lookup"><span data-stu-id="4d4ec-104">While inheriting from the <xref:System.Windows.Forms.Control> class requires that you perform more planning and implementation, it also provides you with the largest range of options.</span></span> <span data-ttu-id="4d4ec-105">Ao herdar do <xref:System.Windows.Forms.Control>, você herda a funcionalidade muito básica que faz com que os controles funcionem.</span><span class="sxs-lookup"><span data-stu-id="4d4ec-105">When inheriting from <xref:System.Windows.Forms.Control>, you inherit the very basic functionality that makes controls work.</span></span> <span data-ttu-id="4d4ec-106">A funcionalidade inerente <xref:System.Windows.Forms.Control> à classe manipula a entrada do usuário através do teclado e do mouse, define os limites e o tamanho do controle, fornece um identificador do Windows e fornece segurança e manipulação de mensagens.</span><span class="sxs-lookup"><span data-stu-id="4d4ec-106">The functionality inherent in the <xref:System.Windows.Forms.Control> class handles user input through the keyboard and mouse, defines the bounds and size of the control, provides a windows handle, and provides message handling and security.</span></span> <span data-ttu-id="4d4ec-107">Ela não incorpora nenhum pintura, que nesse caso é a renderização efetiva da interface gráfica do controle, nem incorpora qualquer funcionalidade de interação do usuário específica.</span><span class="sxs-lookup"><span data-stu-id="4d4ec-107">It does not incorporate any painting, which in this case is the actual rendering of the graphical interface of the control, nor does it incorporate any specific user interaction functionality.</span></span> <span data-ttu-id="4d4ec-108">Você deve fornecer todos esses aspectos por meio de código personalizado.</span><span class="sxs-lookup"><span data-stu-id="4d4ec-108">You must provide all of these aspects through custom code.</span></span>

## <a name="to-create-a-custom-control"></a><span data-ttu-id="4d4ec-109">Criar um controle personalizado</span><span class="sxs-lookup"><span data-stu-id="4d4ec-109">To create a custom control</span></span>

1. <span data-ttu-id="4d4ec-110">Crie um novo projeto de **Aplicativos do Windows** ou **Biblioteca de Controle do Windows**.</span><span class="sxs-lookup"><span data-stu-id="4d4ec-110">Create a new **Windows Application** or **Windows Control Library** project.</span></span>

2. <span data-ttu-id="4d4ec-111">No menu **Projeto**, escolha **Adicionar Classe**.</span><span class="sxs-lookup"><span data-stu-id="4d4ec-111">From the **Project** menu, choose **Add Class**.</span></span>

3. <span data-ttu-id="4d4ec-112">Na caixa de diálogo **Adicionar Novo Item**, clique em **Controle Personalizado**.</span><span class="sxs-lookup"><span data-stu-id="4d4ec-112">In the **Add New Item** dialog box, click **Custom Control**.</span></span>

     <span data-ttu-id="4d4ec-113">Um novo controle personalizado será adicionado ao projeto.</span><span class="sxs-lookup"><span data-stu-id="4d4ec-113">A new custom control is added to your project.</span></span>

4. <span data-ttu-id="4d4ec-114">Pressione F7 para abrir o **Editor de código** para seu controle personalizado.</span><span class="sxs-lookup"><span data-stu-id="4d4ec-114">Press F7 to open the **Code Editor** for your custom control.</span></span>

5. <span data-ttu-id="4d4ec-115">Localize o <xref:System.Windows.Forms.Control.OnPaint%2A> método, que estará vazio, exceto para uma chamada para o <xref:System.Windows.Forms.Control.OnPaint%2A> método da classe base.</span><span class="sxs-lookup"><span data-stu-id="4d4ec-115">Locate the <xref:System.Windows.Forms.Control.OnPaint%2A> method, which will be empty except for a call to the <xref:System.Windows.Forms.Control.OnPaint%2A> method of the base class.</span></span>

6. <span data-ttu-id="4d4ec-116">Modifique o código para incorporar qualquer pintura personalizada desejada ao seu controle.</span><span class="sxs-lookup"><span data-stu-id="4d4ec-116">Modify the code to incorporate any custom painting you want for your control.</span></span>

     <span data-ttu-id="4d4ec-117">Para obter informações sobre como escrever código para renderizar elementos gráficos para controles, consulte [Pintura e renderização de controle personalizado](custom-control-painting-and-rendering.md).</span><span class="sxs-lookup"><span data-stu-id="4d4ec-117">For information about writing code to render graphics for controls, see [Custom Control Painting and Rendering](custom-control-painting-and-rendering.md).</span></span>

7. <span data-ttu-id="4d4ec-118">Implemente os métodos, propriedades ou eventos personalizados que o controle incorporará.</span><span class="sxs-lookup"><span data-stu-id="4d4ec-118">Implement any custom methods, properties, or events that your control will incorporate.</span></span>

8. <span data-ttu-id="4d4ec-119">Salve e teste seu controle.</span><span class="sxs-lookup"><span data-stu-id="4d4ec-119">Save and test your control.</span></span>

## <a name="see-also"></a><span data-ttu-id="4d4ec-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4d4ec-120">See also</span></span>

- [<span data-ttu-id="4d4ec-121">Variedades de controles personalizados</span><span class="sxs-lookup"><span data-stu-id="4d4ec-121">Varieties of Custom Controls</span></span>](varieties-of-custom-controls.md)
- [<span data-ttu-id="4d4ec-122">Como: Herdar da classe UserControl</span><span class="sxs-lookup"><span data-stu-id="4d4ec-122">How to: Inherit from the UserControl Class</span></span>](how-to-inherit-from-the-usercontrol-class.md)
- [<span data-ttu-id="4d4ec-123">Como: Herdar de controles de Windows Forms existentes</span><span class="sxs-lookup"><span data-stu-id="4d4ec-123">How to: Inherit from Existing Windows Forms Controls</span></span>](how-to-inherit-from-existing-windows-forms-controls.md)
- [<span data-ttu-id="4d4ec-124">Como: Controles de autor para Windows Forms</span><span class="sxs-lookup"><span data-stu-id="4d4ec-124">How to: Author Controls for Windows Forms</span></span>](how-to-author-controls-for-windows-forms.md)
- [<span data-ttu-id="4d4ec-125">Solucionando problemas de manipuladores de eventos herdados no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="4d4ec-125">Troubleshooting Inherited Event Handlers in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)
- [<span data-ttu-id="4d4ec-126">Desenvolvendo controles dos Windows Forms em tempo de design</span><span class="sxs-lookup"><span data-stu-id="4d4ec-126">Developing Windows Forms Controls at Design Time</span></span>](developing-windows-forms-controls-at-design-time.md)
