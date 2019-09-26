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
ms.openlocfilehash: 402386e16687162e25e16e5c30c787f7e721fbba
ms.sourcegitcommit: 1e72e2990220b3635cebc39586828af9deb72d8c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/26/2019
ms.locfileid: "71306368"
---
# <a name="how-to-inherit-windows-forms"></a><span data-ttu-id="b4c50-102">Como: herdar Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b4c50-102">How to: Inherit Windows Forms</span></span>

<span data-ttu-id="b4c50-103">Criar novo Windows Forms herdando de formulários base é uma maneira prática de duplicar seus melhores esforços sem passar pelo processo de recriar inteiramente um formulário toda vez que precisar dele.</span><span class="sxs-lookup"><span data-stu-id="b4c50-103">Creating new Windows Forms by inheriting from base forms is a handy way to duplicate your best efforts without going through the process of entirely recreating a form every time you require it.</span></span>

<span data-ttu-id="b4c50-104">Para obter mais informações sobre como herdar formulários em tempo de design usando a caixa de diálogo **seletor de herança** e como distinguir visualmente entre níveis [de segurança de controles herdados, consulte Como: Herdar Formulários usando a caixa](how-to-inherit-forms-using-the-inheritance-picker-dialog-box.md)de diálogo Seletor de herança.</span><span class="sxs-lookup"><span data-stu-id="b4c50-104">For more information about inheriting forms at design time using the **Inheritance Picker** dialog box and how to visually distinguish between security levels of inherited controls, see [How to: Inherit Forms Using the Inheritance Picker Dialog Box](how-to-inherit-forms-using-the-inheritance-picker-dialog-box.md).</span></span>

> [!NOTE]
> <span data-ttu-id="b4c50-105">Para herdar de um formulário, o arquivo ou namespace que contém esse formulário deve ter sido compilado em um arquivo executável ou DLL.</span><span class="sxs-lookup"><span data-stu-id="b4c50-105">In order to inherit from a form, the file or namespace containing that form must have been built into an executable file or DLL.</span></span> <span data-ttu-id="b4c50-106">Para compilar o projeto, escolha **Compilar** no menu **Compilar**.</span><span class="sxs-lookup"><span data-stu-id="b4c50-106">To build the project, choose **Build** from the **Build** menu.</span></span> <span data-ttu-id="b4c50-107">Além disso, uma referência ao namespace deve ser adicionada à classe que herda o formulário.</span><span class="sxs-lookup"><span data-stu-id="b4c50-107">Also, a reference to the namespace must be added to the class inheriting the form.</span></span>

## <a name="inherit-a-form-programmatically"></a><span data-ttu-id="b4c50-108">Herdar um formulário programaticamente</span><span class="sxs-lookup"><span data-stu-id="b4c50-108">Inherit a form programmatically</span></span>

1. <span data-ttu-id="b4c50-109">Em sua classe, adicione uma referência ao namespace que contém o formulário que se deseja herdar.</span><span class="sxs-lookup"><span data-stu-id="b4c50-109">In your class, add a reference to the namespace containing the form you wish to inherit from.</span></span>

2. <span data-ttu-id="b4c50-110">Na definição de classe, adicione uma referência ao formulário de onde será herdado.</span><span class="sxs-lookup"><span data-stu-id="b4c50-110">In the class definition, add a reference to the form to inherit from.</span></span> <span data-ttu-id="b4c50-111">A referência deve incluir o namespace que contém o formulário seguido por uma vírgula, depois o nome do próprio formulário base.</span><span class="sxs-lookup"><span data-stu-id="b4c50-111">The reference should include the namespace that contains the form, followed by a period, then the name of the base form itself.</span></span>

    ```vb
    Public Class Form2
        Inherits Namespace1.Form1
    ```

    ```csharp
    public class Form2 : Namespace1.Form1
    ```

 <span data-ttu-id="b4c50-112">Ao herdar formulários, tenha em mente que podem surgir problemas em relação a manipuladores de eventos sendo chamado duas vezes, porque cada evento está sendo manipulado pela classe base e pela classe herdada.</span><span class="sxs-lookup"><span data-stu-id="b4c50-112">When inheriting forms, keep in mind that issues may arise with regard to event handlers being called twice, because each event is being handled by both the base class and the inherited class.</span></span> <span data-ttu-id="b4c50-113">para mais informações sobre como evitar esse problema, consulte [Solucionando problemas de manipuladores de eventos herdados no Visual Basic](../../../visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md).</span><span class="sxs-lookup"><span data-stu-id="b4c50-113">For more information on how to avoid this problem, see [Troubleshooting Inherited Event Handlers in Visual Basic](../../../visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="b4c50-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b4c50-114">See also</span></span>

- [<span data-ttu-id="b4c50-115">Instrução Inherits</span><span class="sxs-lookup"><span data-stu-id="b4c50-115">Inherits Statement</span></span>](../../../visual-basic/language-reference/statements/inherits-statement.md)
- [<span data-ttu-id="b4c50-116">Instrução Imports (Tipo e Namespace .NET)</span><span class="sxs-lookup"><span data-stu-id="b4c50-116">Imports Statement (.NET Namespace and Type)</span></span>](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
- [<span data-ttu-id="b4c50-117">using</span><span class="sxs-lookup"><span data-stu-id="b4c50-117">using</span></span>](../../../csharp/language-reference/keywords/using.md)
- [<span data-ttu-id="b4c50-118">Efeitos da Modificação da Aparência de um Formulário Base</span><span class="sxs-lookup"><span data-stu-id="b4c50-118">Effects of Modifying a Base Form's Appearance</span></span>](effects-of-modifying-base-form-appearance.md)
- [<span data-ttu-id="b4c50-119">Herança Visual dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b4c50-119">Windows Forms Visual Inheritance</span></span>](windows-forms-visual-inheritance.md)
