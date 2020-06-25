---
title: 'Como: criar manipuladores de eventos em tempo de execução'
description: Saiba como criar um manipulador de eventos em tempo de execução com o Designer de Formulários do Windows no Visual Studio. Essa ação permite que você conecte manipuladores de eventos em tempo de execução.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Windows Forms, event handling
- event handlers [Windows Forms], creating
- run time [Windows Forms], creating event handlers at
- examples [Windows Forms], event handling
- Button control [Windows Forms], event handlers
ms.assetid: 2e7c9e1a-61fe-444d-8113-3c5bacf1c8cb
ms.openlocfilehash: 857076c46377b3276154d9b193d4bbe51841828f
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325799"
---
# <a name="how-to-create-event-handlers-at-run-time-for-windows-forms"></a><span data-ttu-id="dfc4f-104">Como: criar manipuladores de eventos em tempo de execução para o Windows Forms</span><span class="sxs-lookup"><span data-stu-id="dfc4f-104">How to: Create Event Handlers at Run Time for Windows Forms</span></span>

<span data-ttu-id="dfc4f-105">Além de criar eventos usando o Designer de Formulários do Windows no Visual Studio, você também pode criar um manipulador de eventos em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="dfc4f-105">In addition to creating events using the Windows Forms Designer in Visual Studio, you can also create an event handler at run time.</span></span> <span data-ttu-id="dfc4f-106">Essa ação permite que você conecte manipuladores de eventos com base em condições no código no tempo de execução em vez de conectá-los quando o programa inicia.</span><span class="sxs-lookup"><span data-stu-id="dfc4f-106">This action allows you to connect event handlers based on conditions in code at run time as opposed to having them connected when the program initially starts.</span></span>

## <a name="create-an-event-handler-at-run-time"></a><span data-ttu-id="dfc4f-107">Criar um manipulador de eventos em tempo de execução</span><span class="sxs-lookup"><span data-stu-id="dfc4f-107">Create an event handler at run time</span></span>

1. <span data-ttu-id="dfc4f-108">Abra o formulário ao qual você deseja adicionar um manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="dfc4f-108">Open the form that you want to add an event handler to.</span></span>

2. <span data-ttu-id="dfc4f-109">Adicione um método ao seu formulário com a assinatura do método para o evento que deseja manipular.</span><span class="sxs-lookup"><span data-stu-id="dfc4f-109">Add a method to your form with the method signature for the event that you want to handle.</span></span>

     <span data-ttu-id="dfc4f-110">Por exemplo, se você estivesse manipulando o <xref:System.Windows.Forms.Control.Click> evento de um <xref:System.Windows.Forms.Button> controle, você criaria um método como o seguinte:</span><span class="sxs-lookup"><span data-stu-id="dfc4f-110">For example, if you were handling the <xref:System.Windows.Forms.Control.Click> event of a <xref:System.Windows.Forms.Button> control, you would create a method such as the following:</span></span>

    ```vb
    Private Sub Button1_Click(ByVal sender As Object, ByVal e As EventArgs)
       ' Add event handler code here.
    End Sub
    ```

    ```csharp
    private void button1_Click(object sender, System.EventArgs e)
    {
    // Add event handler code here.
    }
    ```

    ```cpp
    private:
       void button1_Click(System::Object ^ sender,
          System::EventArgs ^ e)
       {
          // Add event handler code here.
       }
    ```

3. <span data-ttu-id="dfc4f-111">Adicione código ao manipulador de eventos conforme apropriado para seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="dfc4f-111">Add code to the event handler as appropriate to your application.</span></span>

4. <span data-ttu-id="dfc4f-112">Determine para qual formulário ou controle deseja criar um manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="dfc4f-112">Determine which form or control you want to create an event handler for.</span></span>

5. <span data-ttu-id="dfc4f-113">Em um método na classe do formulário, adicione o código que especifica o manipulador de eventos para manipular o evento.</span><span class="sxs-lookup"><span data-stu-id="dfc4f-113">In a method within your form's class, add code that specifies the event handler to handle the event.</span></span> <span data-ttu-id="dfc4f-114">Por exemplo, o código a seguir especifica o manipulador `button1_Click` de eventos que manipula o <xref:System.Windows.Forms.Control.Click> evento de um <xref:System.Windows.Forms.Button> controle:</span><span class="sxs-lookup"><span data-stu-id="dfc4f-114">For example, the following code specifies the event handler `button1_Click` handles the <xref:System.Windows.Forms.Control.Click> event of a <xref:System.Windows.Forms.Button> control:</span></span>

    ```vb
    AddHandler Button1.Click, AddressOf Button1_Click
    ```

    ```csharp
    button1.Click += new EventHandler(button1_Click);
    ```

    ```cpp
    button1->Click += gcnew System::EventHandler(this, &Form1::button1_Click);
    ```

     <span data-ttu-id="dfc4f-115">O <xref:System.ComponentModel.EventHandlerList.AddHandler%2A> método demonstrado no código de Visual Basic acima estabelece um manipulador de eventos de clique para o botão.</span><span class="sxs-lookup"><span data-stu-id="dfc4f-115">The <xref:System.ComponentModel.EventHandlerList.AddHandler%2A> method demonstrated in the Visual Basic code above establishes a click event handler for the button.</span></span>

## <a name="see-also"></a><span data-ttu-id="dfc4f-116">Veja também</span><span class="sxs-lookup"><span data-stu-id="dfc4f-116">See also</span></span>

- [<span data-ttu-id="dfc4f-117">Criando manipuladores de eventos no Windows Forms</span><span class="sxs-lookup"><span data-stu-id="dfc4f-117">Creating Event Handlers in Windows Forms</span></span>](creating-event-handlers-in-windows-forms.md)
- [<span data-ttu-id="dfc4f-118">Visão geral de manipuladores de eventos</span><span class="sxs-lookup"><span data-stu-id="dfc4f-118">Event Handlers Overview</span></span>](event-handlers-overview-windows-forms.md)
- [<span data-ttu-id="dfc4f-119">Solucionando problemas de manipuladores de eventos herdados no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="dfc4f-119">Troubleshooting Inherited Event Handlers in Visual Basic</span></span>](../../visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)
