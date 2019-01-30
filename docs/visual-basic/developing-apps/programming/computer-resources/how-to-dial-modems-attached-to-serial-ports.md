---
title: 'Como: Discar modems anexados a portas seriais no Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- modems [Visual Basic], dialing
- serial ports [Visual Basic], dialing
- My.Computer.Ports object
ms.assetid: 3834db40-f431-45f1-b671-dc91787164b6
ms.openlocfilehash: db99f94d27235a7c9dca4fc5339854a39147b585
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54490607"
---
# <a name="how-to-dial-modems-attached-to-serial-ports-in-visual-basic"></a><span data-ttu-id="8f044-102">Como: Discar modems anexados a portas seriais no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="8f044-102">How to: Dial Modems Attached to Serial Ports in Visual Basic</span></span>
<span data-ttu-id="8f044-103">Este tópico descreve como usar o `My.Computer.Ports` para discar um modem no Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="8f044-103">This topic describes how to use `My.Computer.Ports` to dial a modem in Visual Basic.</span></span>  
  
 <span data-ttu-id="8f044-104">Normalmente, o modem está conectado a uma das portas seriais no computador.</span><span class="sxs-lookup"><span data-stu-id="8f044-104">Typically, the modem is connected to one of the serial ports on the computer.</span></span> <span data-ttu-id="8f044-105">Para que o seu aplicativo se comunique com o modem, é necessário enviar comandos à porta serial apropriada.</span><span class="sxs-lookup"><span data-stu-id="8f044-105">For your application to communicate with the modem, it must send commands to the appropriate serial port.</span></span>  
  
### <a name="to-dial-a-modem"></a><span data-ttu-id="8f044-106">Para discar um modem</span><span class="sxs-lookup"><span data-stu-id="8f044-106">To dial a modem</span></span>  
  
1.  <span data-ttu-id="8f044-107">Determine a porta serial à qual o modem está conectado.</span><span class="sxs-lookup"><span data-stu-id="8f044-107">Determine which serial port the modem is connected to.</span></span> <span data-ttu-id="8f044-108">Este exemplo supõe que o modem esteja na COM1.</span><span class="sxs-lookup"><span data-stu-id="8f044-108">This example assumes the modem is on COM1.</span></span>  
  
2.  <span data-ttu-id="8f044-109">Use o método `My.Computer.Ports.OpenSerialPort` para obter uma referência para a porta.</span><span class="sxs-lookup"><span data-stu-id="8f044-109">Use the `My.Computer.Ports.OpenSerialPort` method to obtain a reference to the port.</span></span> <span data-ttu-id="8f044-110">Para obter mais informações, consulte <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.</span><span class="sxs-lookup"><span data-stu-id="8f044-110">For more information, see <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.</span></span>  
  
     <span data-ttu-id="8f044-111">O bloco `Using` permite que o aplicativo feche a porta serial mesmo que ele gere uma exceção.</span><span class="sxs-lookup"><span data-stu-id="8f044-111">The `Using` block allows the application to close the serial port even if it generates an exception.</span></span> <span data-ttu-id="8f044-112">Todo o código que manipula a porta serial deve aparecer dentro deste bloco ou em um bloco `Try...Catch...Finally`.</span><span class="sxs-lookup"><span data-stu-id="8f044-112">All code that manipulates the serial port should appear within this block, or within a `Try...Catch...Finally` block.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#28](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-dial-modems-attached-to-serial-ports_1.vb)]  
  
3.  <span data-ttu-id="8f044-113">Defina a propriedade `DtrEnable` para indicar que o computador está pronto para aceitar uma transmissão de entrada do modem.</span><span class="sxs-lookup"><span data-stu-id="8f044-113">Set the `DtrEnable` property to indicate that the computer is ready to accept an incoming transmission from the modem.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#29](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-dial-modems-attached-to-serial-ports_2.vb)]  
  
4.  <span data-ttu-id="8f044-114">Envie o comando de discagem e o número de telefone para o modem através da porta serial por meio do método <xref:System.IO.Ports.SerialPort.Write%2A>.</span><span class="sxs-lookup"><span data-stu-id="8f044-114">Send the dial command and the phone number to the modem through the serial port by means of the <xref:System.IO.Ports.SerialPort.Write%2A> method.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#30](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-dial-modems-attached-to-serial-ports_3.vb)]  
  
## <a name="example"></a><span data-ttu-id="8f044-115">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8f044-115">Example</span></span>  
 [!code-vb[VbVbalrMyComputer#27](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-dial-modems-attached-to-serial-ports_4.vb)]  
  
 <span data-ttu-id="8f044-116">Este exemplo de código também está disponível como um snippet de código do IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="8f044-116">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="8f044-117">No selecionador de snippet de código, ele está localizado em **Conectividade e Redes**.</span><span class="sxs-lookup"><span data-stu-id="8f044-117">In the code snippet picker, it is located in **Connectivity and Networking**.</span></span> <span data-ttu-id="8f044-118">Para obter mais informações, consulte [Snippets de Código](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="8f044-118">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="8f044-119">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="8f044-119">Compiling the Code</span></span>  
 <span data-ttu-id="8f044-120">Este exemplo exige uma referência ao namespace <xref:System?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="8f044-120">This example requires a reference to the <xref:System?displayProperty=nameWithType> namespace.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="8f044-121">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="8f044-121">Robust Programming</span></span>  
 <span data-ttu-id="8f044-122">Este exemplo supõe que o modem esteja conectado à porta COM1.</span><span class="sxs-lookup"><span data-stu-id="8f044-122">This example assumes the modem is connected to COM1.</span></span> <span data-ttu-id="8f044-123">É recomendável que seu código permita que o usuário selecione a porta serial desejada em uma lista de portas disponíveis.</span><span class="sxs-lookup"><span data-stu-id="8f044-123">We recommend that your code allow the user to select the desired serial port from a list of available ports.</span></span> <span data-ttu-id="8f044-124">Para obter mais informações, confira [Como: Mostrar portas seriais disponíveis](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md).</span><span class="sxs-lookup"><span data-stu-id="8f044-124">For more information, see [How to: Show Available Serial Ports](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md).</span></span>  
  
 <span data-ttu-id="8f044-125">Este exemplo usa um bloco `Using` para garantir que o aplicativo feche a porta mesmo que ele lance uma exceção.</span><span class="sxs-lookup"><span data-stu-id="8f044-125">This example uses a `Using` block to make sure that the application closes the port even if it throws an exception.</span></span> <span data-ttu-id="8f044-126">Para obter mais informações, consulte [Instrução using](../../../../visual-basic/language-reference/statements/using-statement.md).</span><span class="sxs-lookup"><span data-stu-id="8f044-126">For more information, see [Using Statement](../../../../visual-basic/language-reference/statements/using-statement.md).</span></span>  
  
 <span data-ttu-id="8f044-127">Neste exemplo, o aplicativo desconecta a porta serial após discar o modem.</span><span class="sxs-lookup"><span data-stu-id="8f044-127">In this example, the application disconnects the serial port after it dials the modem.</span></span> <span data-ttu-id="8f044-128">Na verdade, você desejará transferir dados de/para o modem.</span><span class="sxs-lookup"><span data-stu-id="8f044-128">Realistically, you will want to transfer data to and from the modem.</span></span> <span data-ttu-id="8f044-129">Para obter mais informações, confira [Como: Receber cadeias de caracteres de portas seriais](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-receive-strings-from-serial-ports.md).</span><span class="sxs-lookup"><span data-stu-id="8f044-129">For more information, see [How to: Receive Strings From Serial Ports](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-receive-strings-from-serial-ports.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f044-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8f044-130">See also</span></span>
- <xref:Microsoft.VisualBasic.Devices.Ports>
- <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType>
- [<span data-ttu-id="8f044-131">Como: Enviar cadeias de caracteres para portas seriais</span><span class="sxs-lookup"><span data-stu-id="8f044-131">How to: Send Strings to Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-send-strings-to-serial-ports.md)
- [<span data-ttu-id="8f044-132">Como: Receber cadeias de caracteres de portas seriais</span><span class="sxs-lookup"><span data-stu-id="8f044-132">How to: Receive Strings From Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-receive-strings-from-serial-ports.md)
- [<span data-ttu-id="8f044-133">Como: Mostrar portas seriais disponíveis</span><span class="sxs-lookup"><span data-stu-id="8f044-133">How to: Show Available Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md)
