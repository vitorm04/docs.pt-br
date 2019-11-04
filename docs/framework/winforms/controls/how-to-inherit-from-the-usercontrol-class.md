---
title: Como herdar da classe UserControl
ms.date: 03/30/2017
helpviewer_keywords:
- inheritance [Windows Forms], Windows Forms custom controls
- UserControl class [Windows Forms], inheriting from
- user controls [Windows Forms], creating
- composite controls [Windows Forms], creating
ms.assetid: 67713625-e2e4-4f6a-bce7-0855ee5043d9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 10bb807d012a130ad633b7ce06f99c5abf2cdda1
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458363"
---
# <a name="how-to-inherit-from-the-usercontrol-class"></a><span data-ttu-id="05bed-102">Como herdar da classe UserControl</span><span class="sxs-lookup"><span data-stu-id="05bed-102">How to: Inherit from the UserControl Class</span></span>

<span data-ttu-id="05bed-103">Para combinar a funcionalidade de um ou mais controles do Windows Forms no modo personalizado, é possível criar um *controle de usuário*.</span><span class="sxs-lookup"><span data-stu-id="05bed-103">To combine the functionality of one or more Windows Forms controls with custom code, you can create a *user control*.</span></span> <span data-ttu-id="05bed-104">Os controles de usuário combinam rápido desenvolvimento de controle, a funcionalidade padrão de controle do Windows Forms e a versatilidade de propriedades e métodos personalizados.</span><span class="sxs-lookup"><span data-stu-id="05bed-104">User controls combine rapid control development, standard Windows Forms control functionality, and the versatility of custom properties and methods.</span></span> <span data-ttu-id="05bed-105">Ao começar a criar um controle de usuário tomamos contato com um designer visível, sobre o qual é possível colocar controles padrão do Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="05bed-105">When you begin creating a user control, you are presented with a visible designer, upon which you can place standard Windows Forms controls.</span></span> <span data-ttu-id="05bed-106">Esses controles mantêm todas suas funcionalidades inerentes, bem como a aparência e o comportamento (look and feel) dos controles padrão.</span><span class="sxs-lookup"><span data-stu-id="05bed-106">These controls retain all of their inherent functionality, as well as the appearance and behavior (look and feel) of standard controls.</span></span> <span data-ttu-id="05bed-107">No entanto, uma vez que esses controles são incorporados no controle de usuário, eles não estão mais disponíveis por meio de código.</span><span class="sxs-lookup"><span data-stu-id="05bed-107">Once these controls are built into the user control, however, they are no longer available to you through code.</span></span> <span data-ttu-id="05bed-108">O controle de usuário faz sua própria pintura e também manipula toda a funcionalidade básica associada com controles.</span><span class="sxs-lookup"><span data-stu-id="05bed-108">The user control does its own painting and also handles all of the basic functionality associated with controls.</span></span>

## <a name="to-create-a-user-control"></a><span data-ttu-id="05bed-109">Para criar um controle de usuário</span><span class="sxs-lookup"><span data-stu-id="05bed-109">To create a user control</span></span>

1. <span data-ttu-id="05bed-110">Crie um novo projeto de **biblioteca de controle do Windows** no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="05bed-110">Create a new **Windows Control Library** project in Visual Studio.</span></span>

   <span data-ttu-id="05bed-111">Um novo projeto é criado com um controle de usuário em branco.</span><span class="sxs-lookup"><span data-stu-id="05bed-111">A new project is created with a blank user control.</span></span>

2. <span data-ttu-id="05bed-112">Arraste os controles da aba **Windows Forms** da **Caixa de ferramentas** para o designer.</span><span class="sxs-lookup"><span data-stu-id="05bed-112">Drag controls from the **Windows Forms** tab of the **Toolbox** onto your designer.</span></span>

3. <span data-ttu-id="05bed-113">Esses controles devem ser posicionados e projetados como se deseja que eles apareçam no controle de usuário final.</span><span class="sxs-lookup"><span data-stu-id="05bed-113">These controls should be positioned and designed as you want them to appear in the final user control.</span></span> <span data-ttu-id="05bed-114">Se quiser permitir que os desenvolvedores acessem os controles constituintes, será preciso declará-los como públicos ou exibir seletivamente as propriedades do controle constituinte.</span><span class="sxs-lookup"><span data-stu-id="05bed-114">If you want to allow developers to access the constituent controls, you must declare them as public, or selectively expose properties of the constituent control.</span></span> <span data-ttu-id="05bed-115">Para mais detalhes, consulte [Como expor propriedades de controles constituintes](how-to-expose-properties-of-constituent-controls.md).</span><span class="sxs-lookup"><span data-stu-id="05bed-115">For details, see [How to: Expose Properties of Constituent Controls](how-to-expose-properties-of-constituent-controls.md).</span></span>

4. <span data-ttu-id="05bed-116">Implemente os métodos ou propriedades personalizados que o controle incorporará.</span><span class="sxs-lookup"><span data-stu-id="05bed-116">Implement any custom methods or properties that your control will incorporate.</span></span>

5. <span data-ttu-id="05bed-117">Pressione **F5** para compilar o projeto e executar o controle no **contêiner de teste do UserControl**.</span><span class="sxs-lookup"><span data-stu-id="05bed-117">Press **F5** to build the project and run your control in the **UserControl Test Container**.</span></span> <span data-ttu-id="05bed-118">Para obter mais informações, consulte [How to: Test the Run-Time Behavior of a UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md) (Como testar o comportamento de tempo de execução de um UserControl).</span><span class="sxs-lookup"><span data-stu-id="05bed-118">For more information, see [How to: Test the Run-Time Behavior of a UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="05bed-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="05bed-119">See also</span></span>

- [<span data-ttu-id="05bed-120">Variedades de controles personalizados</span><span class="sxs-lookup"><span data-stu-id="05bed-120">Varieties of Custom Controls</span></span>](varieties-of-custom-controls.md)
- [<span data-ttu-id="05bed-121">Como herdar da classe de controle</span><span class="sxs-lookup"><span data-stu-id="05bed-121">How to: Inherit from the Control Class</span></span>](how-to-inherit-from-the-control-class.md)
- [<span data-ttu-id="05bed-122">Como herdar de controles dos Windows Forms existentes</span><span class="sxs-lookup"><span data-stu-id="05bed-122">How to: Inherit from Existing Windows Forms Controls</span></span>](how-to-inherit-from-existing-windows-forms-controls.md)
- [<span data-ttu-id="05bed-123">Como Criar Controles para o Windows Forms</span><span class="sxs-lookup"><span data-stu-id="05bed-123">How to: Author Controls for Windows Forms</span></span>](how-to-author-controls-for-windows-forms.md)
- [<span data-ttu-id="05bed-124">Solucionar problemas de manipuladores de eventos herdados no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="05bed-124">Troubleshoot Inherited Event Handlers in Visual Basic</span></span>](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)
- [<span data-ttu-id="05bed-125">Como testar o comportamento de tempo de execução de um UserControl</span><span class="sxs-lookup"><span data-stu-id="05bed-125">How to: Test the Run-Time Behavior of a UserControl</span></span>](how-to-test-the-run-time-behavior-of-a-usercontrol.md)
