---
title: 'Como: Discar modems anexados a portas seriais no Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- modems [Visual Basic], dialing
- serial ports [Visual Basic], dialing
- My.Computer.Ports object
ms.assetid: 3834db40-f431-45f1-b671-dc91787164b6
ms.openlocfilehash: f8eda72f72a1d152030aef620a4e3868573b7244
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56971644"
---
# <a name="how-to-dial-modems-attached-to-serial-ports-in-visual-basic"></a><span data-ttu-id="fe542-102">Como: Discar modems anexados a portas seriais no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="fe542-102">How to: Dial Modems Attached to Serial Ports in Visual Basic</span></span>
<span data-ttu-id="fe542-103">Este tópico descreve como usar o `My.Computer.Ports` para discar um modem no Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="fe542-103">This topic describes how to use `My.Computer.Ports` to dial a modem in Visual Basic.</span></span>  
  
 <span data-ttu-id="fe542-104">Normalmente, o modem está conectado a uma das portas seriais no computador.</span><span class="sxs-lookup"><span data-stu-id="fe542-104">Typically, the modem is connected to one of the serial ports on the computer.</span></span> <span data-ttu-id="fe542-105">Para que o seu aplicativo se comunique com o modem, é necessário enviar comandos à porta serial apropriada.</span><span class="sxs-lookup"><span data-stu-id="fe542-105">For your application to communicate with the modem, it must send commands to the appropriate serial port.</span></span>  
  
### <a name="to-dial-a-modem"></a><span data-ttu-id="fe542-106">Para discar um modem</span><span class="sxs-lookup"><span data-stu-id="fe542-106">To dial a modem</span></span>  
  
1.  <span data-ttu-id="fe542-107">Determine a porta serial à qual o modem está conectado.</span><span class="sxs-lookup"><span data-stu-id="fe542-107">Determine which serial port the modem is connected to.</span></span> <span data-ttu-id="fe542-108">Este exemplo supõe que o modem esteja na COM1.</span><span class="sxs-lookup"><span data-stu-id="fe542-108">This example assumes the modem is on COM1.</span></span>  
  
2.  <span data-ttu-id="fe542-109">Use o método `My.Computer.Ports.OpenSerialPort` para obter uma referência para a porta.</span><span class="sxs-lookup"><span data-stu-id="fe542-109">Use the `My.Computer.Ports.OpenSerialPort` method to obtain a reference to the port.</span></span> <span data-ttu-id="fe542-110">Para obter mais informações, consulte <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.</span><span class="sxs-lookup"><span data-stu-id="fe542-110">For more information, see <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.</span></span>  
  
     <span data-ttu-id="fe542-111">O bloco `Using` permite que o aplicativo feche a porta serial mesmo que ele gere uma exceção.</span><span class="sxs-lookup"><span data-stu-id="fe542-111">The `Using` block allows the application to close the serial port even if it generates an exception.</span></span> <span data-ttu-id="fe542-112">Todo o código que manipula a porta serial deve aparecer dentro deste bloco ou em um bloco `Try...Catch...Finally`.</span><span class="sxs-lookup"><span data-stu-id="fe542-112">All code that manipulates the serial port should appear within this block, or within a `Try...Catch...Finally` block.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#28)]  
  
3.  <span data-ttu-id="fe542-113">Defina a propriedade `DtrEnable` para indicar que o computador está pronto para aceitar uma transmissão de entrada do modem.</span><span class="sxs-lookup"><span data-stu-id="fe542-113">Set the `DtrEnable` property to indicate that the computer is ready to accept an incoming transmission from the modem.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#29)]  
  
4.  <span data-ttu-id="fe542-114">Envie o comando de discagem e o número de telefone para o modem através da porta serial por meio do método <xref:System.IO.Ports.SerialPort.Write%2A>.</span><span class="sxs-lookup"><span data-stu-id="fe542-114">Send the dial command and the phone number to the modem through the serial port by means of the <xref:System.IO.Ports.SerialPort.Write%2A> method.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#30)]  
  
## <a name="example"></a><span data-ttu-id="fe542-115">Exemplo</span><span class="sxs-lookup"><span data-stu-id="fe542-115">Example</span></span>  
 [!code-vb[VbVbalrMyComputer#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#27)]  
  
 <span data-ttu-id="fe542-116">Este exemplo de código também está disponível como um snippet de código do IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="fe542-116">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="fe542-117">No selecionador de snippet de código, ele está localizado em **Conectividade e Redes**.</span><span class="sxs-lookup"><span data-stu-id="fe542-117">In the code snippet picker, it is located in **Connectivity and Networking**.</span></span> <span data-ttu-id="fe542-118">Para obter mais informações, consulte [Snippets de Código](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="fe542-118">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="fe542-119">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="fe542-119">Compiling the Code</span></span>  
 <span data-ttu-id="fe542-120">Este exemplo exige uma referência ao namespace <xref:System?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="fe542-120">This example requires a reference to the <xref:System?displayProperty=nameWithType> namespace.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="fe542-121">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="fe542-121">Robust Programming</span></span>  
 <span data-ttu-id="fe542-122">Este exemplo supõe que o modem esteja conectado à porta COM1.</span><span class="sxs-lookup"><span data-stu-id="fe542-122">This example assumes the modem is connected to COM1.</span></span> <span data-ttu-id="fe542-123">É recomendável que seu código permita que o usuário selecione a porta serial desejada em uma lista de portas disponíveis.</span><span class="sxs-lookup"><span data-stu-id="fe542-123">We recommend that your code allow the user to select the desired serial port from a list of available ports.</span></span> <span data-ttu-id="fe542-124">Para obter mais informações, confira [Como: Mostrar portas seriais disponíveis](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md).</span><span class="sxs-lookup"><span data-stu-id="fe542-124">For more information, see [How to: Show Available Serial Ports](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md).</span></span>  
  
 <span data-ttu-id="fe542-125">Este exemplo usa um bloco `Using` para garantir que o aplicativo feche a porta mesmo que ele lance uma exceção.</span><span class="sxs-lookup"><span data-stu-id="fe542-125">This example uses a `Using` block to make sure that the application closes the port even if it throws an exception.</span></span> <span data-ttu-id="fe542-126">Para obter mais informações, consulte [Instrução using](../../../../visual-basic/language-reference/statements/using-statement.md).</span><span class="sxs-lookup"><span data-stu-id="fe542-126">For more information, see [Using Statement](../../../../visual-basic/language-reference/statements/using-statement.md).</span></span>  
  
 <span data-ttu-id="fe542-127">Neste exemplo, o aplicativo desconecta a porta serial após discar o modem.</span><span class="sxs-lookup"><span data-stu-id="fe542-127">In this example, the application disconnects the serial port after it dials the modem.</span></span> <span data-ttu-id="fe542-128">Na verdade, você desejará transferir dados de/para o modem.</span><span class="sxs-lookup"><span data-stu-id="fe542-128">Realistically, you will want to transfer data to and from the modem.</span></span> <span data-ttu-id="fe542-129">Para obter mais informações, confira [Como: Receber cadeias de caracteres de portas seriais](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-receive-strings-from-serial-ports.md).</span><span class="sxs-lookup"><span data-stu-id="fe542-129">For more information, see [How to: Receive Strings From Serial Ports](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-receive-strings-from-serial-ports.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe542-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fe542-130">See also</span></span>
- <xref:Microsoft.VisualBasic.Devices.Ports>
- <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType>
- [<span data-ttu-id="fe542-131">Como: Enviar cadeias de caracteres para portas seriais</span><span class="sxs-lookup"><span data-stu-id="fe542-131">How to: Send Strings to Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-send-strings-to-serial-ports.md)
- [<span data-ttu-id="fe542-132">Como: Receber cadeias de caracteres de portas seriais</span><span class="sxs-lookup"><span data-stu-id="fe542-132">How to: Receive Strings From Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-receive-strings-from-serial-ports.md)
- [<span data-ttu-id="fe542-133">Como: Mostrar portas seriais disponíveis</span><span class="sxs-lookup"><span data-stu-id="fe542-133">How to: Show Available Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md)
