---
title: Como exibir a hora com o controle DateTimePicker
description: Saiba como usar o controle DateTimePicker Windows Forms para permitir que os usuários selecionem uma data e hora e exibam essa data e hora no formato especificado.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time [Windows Forms], displaying in DateTimePicker control
- examples [Windows Forms], DateTimePicker control
- DateTimePicker control [Windows Forms], displaying time
ms.assetid: 0c1c8b40-1b50-4301-a90c-39516775ccb1
ms.openlocfilehash: ab584367a189d05e567bb57d386c6bf629201102
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325579"
---
# <a name="how-to-display-time-with-the-datetimepicker-control"></a><span data-ttu-id="f642a-103">Como exibir a hora com o controle DateTimePicker</span><span class="sxs-lookup"><span data-stu-id="f642a-103">How to: Display Time with the DateTimePicker Control</span></span>
<span data-ttu-id="f642a-104">Se você quiser que o aplicativo permita que os usuários selecionem uma data e hora e exibam essa data e hora no formato especificado, use o <xref:System.Windows.Forms.DateTimePicker> controle.</span><span class="sxs-lookup"><span data-stu-id="f642a-104">If you want your application to enable users to select a date and time, and to display that date and time in the specified format, use the <xref:System.Windows.Forms.DateTimePicker> control.</span></span> <span data-ttu-id="f642a-105">O procedimento a seguir mostra como usar o <xref:System.Windows.Forms.DateTimePicker> controle para exibir a hora.</span><span class="sxs-lookup"><span data-stu-id="f642a-105">The following procedure shows how to use the <xref:System.Windows.Forms.DateTimePicker> control to display the time.</span></span>  
  
### <a name="to-display-the-time-with-the-datetimepicker-control"></a><span data-ttu-id="f642a-106">Para exibir a hora com o controle DateTimePicker</span><span class="sxs-lookup"><span data-stu-id="f642a-106">To display the time with the DateTimePicker control</span></span>  
  
1. <span data-ttu-id="f642a-107">Defina a propriedade <xref:System.Windows.Forms.DateTimePicker.Format%2A> como <xref:System.Windows.Forms.DateTimePickerFormat.Time></span><span class="sxs-lookup"><span data-stu-id="f642a-107">Set the <xref:System.Windows.Forms.DateTimePicker.Format%2A> property to <xref:System.Windows.Forms.DateTimePickerFormat.Time></span></span>  
  
     [!code-csharp[System.Windows.Forms.DateTimePickerTimeOnly#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DateTimePickerTimeOnly/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.DateTimePickerTimeOnly#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DateTimePickerTimeOnly/VB/Form1.vb#2)]  
  
2. <span data-ttu-id="f642a-108">Defina a <xref:System.Windows.Forms.DateTimePicker.ShowUpDown%2A> propriedade para o <xref:System.Windows.Forms.DateTimePicker> como `true` .</span><span class="sxs-lookup"><span data-stu-id="f642a-108">Set the <xref:System.Windows.Forms.DateTimePicker.ShowUpDown%2A> property for the <xref:System.Windows.Forms.DateTimePicker> to `true`.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DateTimePickerTimeOnly#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DateTimePickerTimeOnly/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.DateTimePickerTimeOnly#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DateTimePickerTimeOnly/VB/Form1.vb#3)]  
  
## <a name="example"></a><span data-ttu-id="f642a-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f642a-109">Example</span></span>  
 <span data-ttu-id="f642a-110">O exemplo de código a seguir mostra como criar um <xref:System.Windows.Forms.DateTimePicker> que permite que os usuários escolham apenas um tempo.</span><span class="sxs-lookup"><span data-stu-id="f642a-110">The following code sample shows how to create a <xref:System.Windows.Forms.DateTimePicker> that enables users to choose a time only.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DateTimePickerTimeOnly#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DateTimePickerTimeOnly/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.DateTimePickerTimeOnly#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DateTimePickerTimeOnly/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="f642a-111">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="f642a-111">Compiling the Code</span></span>  
 <span data-ttu-id="f642a-112">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="f642a-112">This example requires:</span></span>  
  
- <span data-ttu-id="f642a-113">Referências aos assemblies System, System.Data, System.Drawing e System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="f642a-113">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f642a-114">Veja também</span><span class="sxs-lookup"><span data-stu-id="f642a-114">See also</span></span>

- [<span data-ttu-id="f642a-115">Controle DateTimePicker</span><span class="sxs-lookup"><span data-stu-id="f642a-115">DateTimePicker Control</span></span>](datetimepicker-control-windows-forms.md)
