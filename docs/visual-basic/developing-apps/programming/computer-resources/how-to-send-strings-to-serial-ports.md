---
title: 'Como: Enviar cadeias de caracteres para portas seriais no Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- ports, sending strings to
- strings [Visual Basic], sending to serial ports
- My.Computer.Ports object
- serial ports, sending strings to
ms.assetid: 6ebf46cd-b2d0-4b2c-9a1f-be177b22ad52
ms.openlocfilehash: e1f0c9d5ba428f5379f8025c0e733cdbeb5204e0
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58822850"
---
# <a name="how-to-send-strings-to-serial-ports-in-visual-basic"></a><span data-ttu-id="d75bf-102">Como: Enviar cadeias de caracteres para portas seriais no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d75bf-102">How to: Send Strings to Serial Ports in Visual Basic</span></span>
<span data-ttu-id="d75bf-103">Este tópico descreve como usar o `My.Computer.Ports` para enviar cadeias de caracteres para portas seriais do computador em Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="d75bf-103">This topic describes how to use `My.Computer.Ports` to send strings to the computer's serial ports in Visual Basic.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d75bf-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d75bf-104">Example</span></span>  
 <span data-ttu-id="d75bf-105">Este exemplo envia uma cadeia de caracteres para a porta serial COM1.</span><span class="sxs-lookup"><span data-stu-id="d75bf-105">This example sends a string to the COM1 serial port.</span></span> <span data-ttu-id="d75bf-106">Talvez você precise usar uma porta serial diferente em seu computador.</span><span class="sxs-lookup"><span data-stu-id="d75bf-106">You may need to use a different serial port on your computer.</span></span>  
  
 <span data-ttu-id="d75bf-107">Use o método `My.Computer.Ports.OpenSerialPort` para obter uma referência para a porta.</span><span class="sxs-lookup"><span data-stu-id="d75bf-107">Use the `My.Computer.Ports.OpenSerialPort` method to obtain a reference to the port.</span></span> <span data-ttu-id="d75bf-108">Para obter mais informações, consulte <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.</span><span class="sxs-lookup"><span data-stu-id="d75bf-108">For more information, see <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.</span></span>  
  
 <span data-ttu-id="d75bf-109">O bloco `Using` permite que o aplicativo feche a porta serial mesmo que ele gere uma exceção.</span><span class="sxs-lookup"><span data-stu-id="d75bf-109">The `Using` block allows the application to close the serial port even if it generates an exception.</span></span> <span data-ttu-id="d75bf-110">Todo o código que manipula a porta serial deve aparecer dentro deste bloco ou em um bloco `Try...Catch...Finally`.</span><span class="sxs-lookup"><span data-stu-id="d75bf-110">All code that manipulates the serial port should appear within this block or within a `Try...Catch...Finally` block.</span></span>  
  
 <span data-ttu-id="d75bf-111">O método <xref:System.IO.Ports.SerialPort.WriteLine%2A> envia os dados à porta serial.</span><span class="sxs-lookup"><span data-stu-id="d75bf-111">The <xref:System.IO.Ports.SerialPort.WriteLine%2A> method sends the data to the serial port.</span></span>  
  
 [!code-vb[VbVbalrMyComputer#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#33)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="d75bf-112">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="d75bf-112">Compiling the Code</span></span>  
  
-   <span data-ttu-id="d75bf-113">Este exemplo pressupõe que o computador esteja usando a `COM1`.</span><span class="sxs-lookup"><span data-stu-id="d75bf-113">This example assumes the computer is using `COM1`.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="d75bf-114">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="d75bf-114">Robust Programming</span></span>  
 <span data-ttu-id="d75bf-115">Este exemplo pressupõe que o computador esteja usando a `COM1`. Para obter mais flexibilidade, o código deve permitir que o usuário selecione a porta serial desejada na lista de portas disponíveis.</span><span class="sxs-lookup"><span data-stu-id="d75bf-115">This example assumes the computer is using `COM1`; for more flexibility, the code should allow the user to select the desired serial port from a list of available ports.</span></span> <span data-ttu-id="d75bf-116">Para obter mais informações, confira [Como: Mostrar portas seriais disponíveis](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md).</span><span class="sxs-lookup"><span data-stu-id="d75bf-116">For more information, see [How to: Show Available Serial Ports](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md).</span></span>  
  
 <span data-ttu-id="d75bf-117">Este exemplo usa um bloco `Using` para garantir que o aplicativo feche a porta mesmo que ele lance uma exceção.</span><span class="sxs-lookup"><span data-stu-id="d75bf-117">This example uses a `Using` block to make sure that the application closes the port even if it throws an exception.</span></span> <span data-ttu-id="d75bf-118">Para obter mais informações, consulte [Instrução using](../../../../visual-basic/language-reference/statements/using-statement.md).</span><span class="sxs-lookup"><span data-stu-id="d75bf-118">For more information, see [Using Statement](../../../../visual-basic/language-reference/statements/using-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d75bf-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d75bf-119">See also</span></span>

- <xref:Microsoft.VisualBasic.Devices.Ports>
- <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType>
- [<span data-ttu-id="d75bf-120">Como: Discar modems anexados a portas seriais</span><span class="sxs-lookup"><span data-stu-id="d75bf-120">How to: Dial Modems Attached to Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-dial-modems-attached-to-serial-ports.md)
- [<span data-ttu-id="d75bf-121">Como: Mostrar portas seriais disponíveis</span><span class="sxs-lookup"><span data-stu-id="d75bf-121">How to: Show Available Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md)
