---
title: 'Como: herdar Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- inherited forms [Windows Forms], creating at run-time
- inheritance [Windows Forms], forms
- Windows Forms, inheritance
ms.assetid: cb3e1c0f-3d2a-4cdc-b0d1-c92eae567ffb
ms.openlocfilehash: 0d8799359a12b9bb64331d83df2500bede8c0ff2
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59314536"
---
# <a name="how-to-inherit-windows-forms"></a><span data-ttu-id="b5a11-102">Como: herdar Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b5a11-102">How to: Inherit Windows Forms</span></span>
<span data-ttu-id="b5a11-103">Criar novo Windows Forms herdando de formulários base é uma maneira prática de duplicar seus melhores esforços sem passar pelo processo de recriar inteiramente um formulário toda vez que precisar dele.</span><span class="sxs-lookup"><span data-stu-id="b5a11-103">Creating new Windows Forms by inheriting from base forms is a handy way to duplicate your best efforts without going through the process of entirely recreating a form every time you require it.</span></span>  
  
 <span data-ttu-id="b5a11-104">Para obter mais informações sobre herdar formulários em tempo de design usando o **selecionador de herança** controles de caixa de diálogo e como distinguir visualmente entre níveis de segurança de herdados, consulte [como: Herdar formulários usando a caixa de diálogo selecionador de herança](how-to-inherit-forms-using-the-inheritance-picker-dialog-box.md).</span><span class="sxs-lookup"><span data-stu-id="b5a11-104">For more information about inheriting forms at design time using the **Inheritance Picker** dialog box and how to visually distinguish between security levels of inherited controls, see [How to: Inherit Forms Using the Inheritance Picker Dialog Box](how-to-inherit-forms-using-the-inheritance-picker-dialog-box.md).</span></span>  
  
 <span data-ttu-id="b5a11-105">**Observação** para herdar de um formulário, o arquivo ou namespace que contém esse formulário deve ter sido incorporado em um arquivo executável ou DLL.</span><span class="sxs-lookup"><span data-stu-id="b5a11-105">**Note** In order to inherit from a form, the file or namespace containing that form must have been built into an executable file or DLL.</span></span> <span data-ttu-id="b5a11-106">Para compilar o projeto, escolha **Compilar** no menu **Compilar**.</span><span class="sxs-lookup"><span data-stu-id="b5a11-106">To build the project, choose **Build** from the **Build** menu.</span></span> <span data-ttu-id="b5a11-107">Além disso, uma referência ao namespace deve ser adicionada à classe que herda o formulário.</span><span class="sxs-lookup"><span data-stu-id="b5a11-107">Also, a reference to the namespace must be added to the class inheriting the form.</span></span> <span data-ttu-id="b5a11-108">As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas.</span><span class="sxs-lookup"><span data-stu-id="b5a11-108">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="b5a11-109">Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**.</span><span class="sxs-lookup"><span data-stu-id="b5a11-109">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="b5a11-110">Para obter mais informações, confira [Personalizar o IDE do Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="b5a11-110">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-inherit-a-form-programmatically"></a><span data-ttu-id="b5a11-111">Herdar um formulário programaticamente</span><span class="sxs-lookup"><span data-stu-id="b5a11-111">To inherit a form programmatically</span></span>  
  
1. <span data-ttu-id="b5a11-112">Em sua classe, adicione uma referência ao namespace que contém o formulário que se deseja herdar.</span><span class="sxs-lookup"><span data-stu-id="b5a11-112">In your class, add a reference to the namespace containing the form you wish to inherit from.</span></span>  
  
2. <span data-ttu-id="b5a11-113">Na definição de classe, adicione uma referência ao formulário de onde será herdado.</span><span class="sxs-lookup"><span data-stu-id="b5a11-113">In the class definition, add a reference to the form to inherit from.</span></span> <span data-ttu-id="b5a11-114">A referência deve incluir o namespace que contém o formulário seguido por uma vírgula, depois o nome do próprio formulário base.</span><span class="sxs-lookup"><span data-stu-id="b5a11-114">The reference should include the namespace that contains the form, followed by a period, then the name of the base form itself.</span></span>  
  
    ```vb  
    Public Class Form2  
        Inherits Namespace1.Form1  
    ```  
  
    ```csharp  
    public class Form2 : Namespace1.Form1  
    ```  
  
 <span data-ttu-id="b5a11-115">Ao herdar formulários, tenha em mente que podem surgir problemas em relação a manipuladores de eventos sendo chamado duas vezes, porque cada evento está sendo manipulado pela classe base e pela classe herdada.</span><span class="sxs-lookup"><span data-stu-id="b5a11-115">When inheriting forms, keep in mind that issues may arise with regard to event handlers being called twice, because each event is being handled by both the base class and the inherited class.</span></span> <span data-ttu-id="b5a11-116">para mais informações sobre como evitar esse problema, consulte [Solucionando problemas de manipuladores de eventos herdados no Visual Basic](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md).</span><span class="sxs-lookup"><span data-stu-id="b5a11-116">For more information on how to avoid this problem, see [Troubleshooting Inherited Event Handlers in Visual Basic](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5a11-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b5a11-117">See also</span></span>

- [<span data-ttu-id="b5a11-118">Instrução Inherits</span><span class="sxs-lookup"><span data-stu-id="b5a11-118">Inherits Statement</span></span>](~/docs/visual-basic/language-reference/statements/inherits-statement.md)
- [<span data-ttu-id="b5a11-119">Instrução Imports (tipo e namespace .NET)</span><span class="sxs-lookup"><span data-stu-id="b5a11-119">Imports Statement (.NET Namespace and Type)</span></span>](~/docs/visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
- [<span data-ttu-id="b5a11-120">using</span><span class="sxs-lookup"><span data-stu-id="b5a11-120">using</span></span>](~/docs/csharp/language-reference/keywords/using.md)
- [<span data-ttu-id="b5a11-121">Efeitos da modificação da aparência de um formulário base</span><span class="sxs-lookup"><span data-stu-id="b5a11-121">Effects of Modifying a Base Form's Appearance</span></span>](effects-of-modifying-base-form-appearance.md)
- [<span data-ttu-id="b5a11-122">Herança visual dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b5a11-122">Windows Forms Visual Inheritance</span></span>](windows-forms-visual-inheritance.md)
