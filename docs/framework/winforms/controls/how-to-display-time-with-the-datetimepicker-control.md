---
title: 'Como: Exibir a hora com o controle DateTimePicker'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time [Windows Forms], displaying in DateTimePicker control
- examples [Windows Forms], DateTimePicker control
- DateTimePicker control [Windows Forms], displaying time
ms.assetid: 0c1c8b40-1b50-4301-a90c-39516775ccb1
ms.openlocfilehash: 7906811d5a324ba3f2bd73cc057298e007ac311b
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59329850"
---
# <a name="how-to-display-time-with-the-datetimepicker-control"></a><span data-ttu-id="a29ea-102">Como: Exibir a hora com o controle DateTimePicker</span><span class="sxs-lookup"><span data-stu-id="a29ea-102">How to: Display Time with the DateTimePicker Control</span></span>
<span data-ttu-id="a29ea-103">Se quiser que seu aplicativo para permitir aos usuários selecionar uma data e hora e para exibir a data e hora no formato especificado, use o <xref:System.Windows.Forms.DateTimePicker> controle.</span><span class="sxs-lookup"><span data-stu-id="a29ea-103">If you want your application to enable users to select a date and time, and to display that date and time in the specified format, use the <xref:System.Windows.Forms.DateTimePicker> control.</span></span> <span data-ttu-id="a29ea-104">O procedimento a seguir mostra como usar o <xref:System.Windows.Forms.DateTimePicker> controle para exibir a hora.</span><span class="sxs-lookup"><span data-stu-id="a29ea-104">The following procedure shows how to use the <xref:System.Windows.Forms.DateTimePicker> control to display the time.</span></span>  
  
### <a name="to-display-the-time-with-the-datetimepicker-control"></a><span data-ttu-id="a29ea-105">Para exibir a hora com o controle DateTimePicker</span><span class="sxs-lookup"><span data-stu-id="a29ea-105">To display the time with the DateTimePicker control</span></span>  
  
1. <span data-ttu-id="a29ea-106">Defina o <xref:System.Windows.Forms.DateTimePicker.Format%2A> propriedade</span><span class="sxs-lookup"><span data-stu-id="a29ea-106">Set the <xref:System.Windows.Forms.DateTimePicker.Format%2A> property to</span></span> <xref:System.Windows.Forms.DateTimePickerFormat.Time>  
  
     [!code-csharp[System.Windows.Forms.DateTimePickerTimeOnly#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DateTimePickerTimeOnly/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.DateTimePickerTimeOnly#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DateTimePickerTimeOnly/VB/Form1.vb#2)]  
  
2. <span data-ttu-id="a29ea-107">Defina as <xref:System.Windows.Forms.DateTimePicker.ShowUpDown%2A> propriedade para o <xref:System.Windows.Forms.DateTimePicker> para `true`.</span><span class="sxs-lookup"><span data-stu-id="a29ea-107">Set the <xref:System.Windows.Forms.DateTimePicker.ShowUpDown%2A> property for the <xref:System.Windows.Forms.DateTimePicker> to `true`.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DateTimePickerTimeOnly#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DateTimePickerTimeOnly/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.DateTimePickerTimeOnly#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DateTimePickerTimeOnly/VB/Form1.vb#3)]  
  
## <a name="example"></a><span data-ttu-id="a29ea-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a29ea-108">Example</span></span>  
 <span data-ttu-id="a29ea-109">O exemplo de código a seguir mostra como criar um <xref:System.Windows.Forms.DateTimePicker> que os usuários podem escolher apenas uma vez.</span><span class="sxs-lookup"><span data-stu-id="a29ea-109">The following code sample shows how to create a <xref:System.Windows.Forms.DateTimePicker> that enables users to choose a time only.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DateTimePickerTimeOnly#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DateTimePickerTimeOnly/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.DateTimePickerTimeOnly#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DateTimePickerTimeOnly/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="a29ea-110">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="a29ea-110">Compiling the Code</span></span>  
 <span data-ttu-id="a29ea-111">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="a29ea-111">This example requires:</span></span>  
  
-   <span data-ttu-id="a29ea-112">Referências aos assemblies System, System.Data, System.Drawing e System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="a29ea-112">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="a29ea-113">Para obter informações sobre como compilar este exemplo da linha de comando para o Visual Basic ou Visual c#, consulte [compilando da linha de comando](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) ou [criação de linha de comando com csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="a29ea-113">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="a29ea-114">Você também pode criar este exemplo no Visual Studio colando o código em um novo projeto.</span><span class="sxs-lookup"><span data-stu-id="a29ea-114">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a29ea-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a29ea-115">See also</span></span>

- [<span data-ttu-id="a29ea-116">Controle DateTimePicker</span><span class="sxs-lookup"><span data-stu-id="a29ea-116">DateTimePicker Control</span></span>](datetimepicker-control-windows-forms.md)
