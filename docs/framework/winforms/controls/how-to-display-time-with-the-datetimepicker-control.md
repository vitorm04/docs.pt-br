---
title: Como exibir a hora com o controle DateTimePicker
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time [Windows Forms], displaying in DateTimePicker control
- examples [Windows Forms], DateTimePicker control
- DateTimePicker control [Windows Forms], displaying time
ms.assetid: 0c1c8b40-1b50-4301-a90c-39516775ccb1
caps.latest.revision: 11
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 718258f25a0d3e714cf202c3d7d1c0e61325468d
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/27/2018
---
# <a name="how-to-display-time-with-the-datetimepicker-control"></a><span data-ttu-id="24a6f-102">Como exibir a hora com o controle DateTimePicker</span><span class="sxs-lookup"><span data-stu-id="24a6f-102">How to: Display Time with the DateTimePicker Control</span></span>
<span data-ttu-id="24a6f-103">Se você quiser que seu aplicativo para permitir aos usuários selecionar uma data e hora e para exibir a data e a hora no formato especificado, use o <xref:System.Windows.Forms.DateTimePicker> controle.</span><span class="sxs-lookup"><span data-stu-id="24a6f-103">If you want your application to enable users to select a date and time, and to display that date and time in the specified format, use the <xref:System.Windows.Forms.DateTimePicker> control.</span></span> <span data-ttu-id="24a6f-104">O procedimento a seguir mostra como usar o <xref:System.Windows.Forms.DateTimePicker> controle para exibir a hora.</span><span class="sxs-lookup"><span data-stu-id="24a6f-104">The following procedure shows how to use the <xref:System.Windows.Forms.DateTimePicker> control to display the time.</span></span>  
  
### <a name="to-display-the-time-with-the-datetimepicker-control"></a><span data-ttu-id="24a6f-105">Para exibir a hora com o controle DateTimePicker</span><span class="sxs-lookup"><span data-stu-id="24a6f-105">To display the time with the DateTimePicker control</span></span>  
  
1.  <span data-ttu-id="24a6f-106">Defina a propriedade <xref:System.Windows.Forms.DateTimePicker.Format%2A> como <xref:System.Windows.Forms.DateTimePickerFormat.Time></span><span class="sxs-lookup"><span data-stu-id="24a6f-106">Set the <xref:System.Windows.Forms.DateTimePicker.Format%2A> property to <xref:System.Windows.Forms.DateTimePickerFormat.Time></span></span>  
  
     [!code-csharp[System.Windows.Forms.DateTimePickerTimeOnly#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DateTimePickerTimeOnly/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.DateTimePickerTimeOnly#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DateTimePickerTimeOnly/VB/Form1.vb#2)]  
  
2.  <span data-ttu-id="24a6f-107">Definir o <xref:System.Windows.Forms.DateTimePicker.ShowUpDown%2A> propriedade para o <xref:System.Windows.Forms.DateTimePicker> para `true`.</span><span class="sxs-lookup"><span data-stu-id="24a6f-107">Set the <xref:System.Windows.Forms.DateTimePicker.ShowUpDown%2A> property for the <xref:System.Windows.Forms.DateTimePicker> to `true`.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DateTimePickerTimeOnly#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DateTimePickerTimeOnly/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.DateTimePickerTimeOnly#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DateTimePickerTimeOnly/VB/Form1.vb#3)]  
  
## <a name="example"></a><span data-ttu-id="24a6f-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="24a6f-108">Example</span></span>  
 <span data-ttu-id="24a6f-109">O exemplo de código a seguir mostra como criar um <xref:System.Windows.Forms.DateTimePicker> que permite que os usuários podem escolher apenas uma vez.</span><span class="sxs-lookup"><span data-stu-id="24a6f-109">The following code sample shows how to create a <xref:System.Windows.Forms.DateTimePicker> that enables users to choose a time only.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DateTimePickerTimeOnly#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DateTimePickerTimeOnly/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.DateTimePickerTimeOnly#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DateTimePickerTimeOnly/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="24a6f-110">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="24a6f-110">Compiling the Code</span></span>  
 <span data-ttu-id="24a6f-111">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="24a6f-111">This example requires:</span></span>  
  
-   <span data-ttu-id="24a6f-112">Referências aos assemblies System, System.Data, System.Drawing e System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="24a6f-112">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="24a6f-113">Para obter informações sobre como criar este exemplo da linha de comando para o Visual Basic ou Visual c#, consulte [Compilando a partir da linha de comando](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) ou [criação de linha de comando com csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="24a6f-113">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="24a6f-114">Você também pode criar este exemplo no Visual Studio colando o código em um novo projeto.</span><span class="sxs-lookup"><span data-stu-id="24a6f-114">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="24a6f-115">Consulte também [Como compilar e executar um exemplo completo de código do Windows Forms usando o Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="24a6f-115">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24a6f-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="24a6f-116">See Also</span></span>  
 [<span data-ttu-id="24a6f-117">Controle DateTimePicker</span><span class="sxs-lookup"><span data-stu-id="24a6f-117">DateTimePicker Control</span></span>](../../../../docs/framework/winforms/controls/datetimepicker-control-windows-forms.md)
