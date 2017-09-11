---
title: Como receber cadeias de caracteres de portas seriais no Visual Basic
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- serial ports, retrieving strings
- strings [Visual Basic], retrieving from serial ports
- My.Resources object
ms.assetid: 8371ce2c-e1c7-476b-a86d-9afc2614b6b7
caps.latest.revision: 21
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 500a6c651f6eb991eb9fefef601d0f593a38352f
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-receive-strings-from-serial-ports-in-visual-basic"></a><span data-ttu-id="fdad7-102">Como receber cadeias de caracteres de portas seriais no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="fdad7-102">How to: Receive Strings From Serial Ports in Visual Basic</span></span>
<span data-ttu-id="fdad7-103">Este tópico descreve como usar o `My.Computer.Ports` para receber cadeias de caracteres de portas seriais do computador no [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span><span class="sxs-lookup"><span data-stu-id="fdad7-103">This topic describes how to use `My.Computer.Ports` to receive strings from the computer's serial ports in [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span></span>  
  
### <a name="to-receive-strings-from-the-serial-port"></a><span data-ttu-id="fdad7-104">Para receber cadeias de caracteres da porta serial</span><span class="sxs-lookup"><span data-stu-id="fdad7-104">To receive strings from the serial port</span></span>  
  
1.  <span data-ttu-id="fdad7-105">Inicialize a cadeia de caracteres de retorno.</span><span class="sxs-lookup"><span data-stu-id="fdad7-105">Initialize the return string.</span></span>  
  
     <span data-ttu-id="fdad7-106">[!code-vb[VbVbalrMyComputer#38](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-receive-strings-from-serial-ports_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="fdad7-106">[!code-vb[VbVbalrMyComputer#38](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-receive-strings-from-serial-ports_1.vb)]</span></span>  
  
2.  <span data-ttu-id="fdad7-107">Determine qual porta serial deve fornecer as cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="fdad7-107">Determine which serial port should provide the strings.</span></span> <span data-ttu-id="fdad7-108">Este exemplo assume que é `COM1`.</span><span class="sxs-lookup"><span data-stu-id="fdad7-108">This example assumes it is `COM1`.</span></span>  
  
3.  <span data-ttu-id="fdad7-109">Use o método `My.Computer.Ports.OpenSerialPort` para obter uma referência para a porta.</span><span class="sxs-lookup"><span data-stu-id="fdad7-109">Use the `My.Computer.Ports.OpenSerialPort` method to obtain a reference to the port.</span></span> <span data-ttu-id="fdad7-110">Para obter mais informações, consulte <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.</span><span class="sxs-lookup"><span data-stu-id="fdad7-110">For more information, see <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.</span></span>  
  
     <span data-ttu-id="fdad7-111">O bloco `Try...Catch...Finally` permite que o aplicativo feche a porta serial mesmo que ele gere uma exceção.</span><span class="sxs-lookup"><span data-stu-id="fdad7-111">The `Try...Catch...Finally` block allows the application to close the serial port even if it generates an exception.</span></span> <span data-ttu-id="fdad7-112">Todo o código que manipula a porta serial deve aparecer dentro deste bloco.</span><span class="sxs-lookup"><span data-stu-id="fdad7-112">All code that manipulates the serial port should appear within this block.</span></span>  
  
     <span data-ttu-id="fdad7-113">[!code-vb[VbVbalrMyComputer#39](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-receive-strings-from-serial-ports_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="fdad7-113">[!code-vb[VbVbalrMyComputer#39](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-receive-strings-from-serial-ports_2.vb)]</span></span>  
  
4.  <span data-ttu-id="fdad7-114">Crie um loop de `Do` para ler linhas do texto até que não haja mais linhas disponíveis.</span><span class="sxs-lookup"><span data-stu-id="fdad7-114">Create a `Do` loop for reading lines of text until no more lines are available.</span></span>  
  
     <span data-ttu-id="fdad7-115">[!code-vb[VbVbalrMyComputer#40](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-receive-strings-from-serial-ports_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="fdad7-115">[!code-vb[VbVbalrMyComputer#40](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-receive-strings-from-serial-ports_3.vb)]</span></span>  
  
5.  <span data-ttu-id="fdad7-116">Use o método <xref:System.IO.Ports.SerialPort.ReadLine%2A> para ler a próxima linha de texto disponível da porta serial.</span><span class="sxs-lookup"><span data-stu-id="fdad7-116">Use the <xref:System.IO.Ports.SerialPort.ReadLine%2A> method to read the next available line of text from the serial port.</span></span>  
  
     <span data-ttu-id="fdad7-117">[!code-vb[VbVbalrMyComputer#41](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-receive-strings-from-serial-ports_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="fdad7-117">[!code-vb[VbVbalrMyComputer#41](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-receive-strings-from-serial-ports_4.vb)]</span></span>  
  
6.  <span data-ttu-id="fdad7-118">Use uma instrução `If` para determinar se o método <xref:System.IO.Ports.SerialPort.ReadLine%2A> retorna `Nothing` (o que significa que não há mais texto disponível).</span><span class="sxs-lookup"><span data-stu-id="fdad7-118">Use an `If` statement to determine if the <xref:System.IO.Ports.SerialPort.ReadLine%2A> method returns `Nothing` (which means no more text is available).</span></span> <span data-ttu-id="fdad7-119">Se ele retornar `Nothing`, saia do loop de `Do`.</span><span class="sxs-lookup"><span data-stu-id="fdad7-119">If it does return `Nothing`, exit the `Do` loop.</span></span>  
  
     <span data-ttu-id="fdad7-120">[!code-vb[VbVbalrMyComputer#42](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-receive-strings-from-serial-ports_5.vb)]</span><span class="sxs-lookup"><span data-stu-id="fdad7-120">[!code-vb[VbVbalrMyComputer#42](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-receive-strings-from-serial-ports_5.vb)]</span></span>  
  
7.  <span data-ttu-id="fdad7-121">Adicione um bloco `Else` à instrução `If` para lidar com o caso se a cadeia de caracteres for realmente lida.</span><span class="sxs-lookup"><span data-stu-id="fdad7-121">Add an `Else` block to the `If` statement to handle the case if the string is actually read.</span></span> <span data-ttu-id="fdad7-122">O bloco acrescenta a cadeia de caracteres da porta serial à cadeia de caracteres de retorno.</span><span class="sxs-lookup"><span data-stu-id="fdad7-122">The block appends the string from the serial port to the return string.</span></span>  
  
     <span data-ttu-id="fdad7-123">[!code-vb[VbVbalrMyComputer#43](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-receive-strings-from-serial-ports_6.vb)]</span><span class="sxs-lookup"><span data-stu-id="fdad7-123">[!code-vb[VbVbalrMyComputer#43](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-receive-strings-from-serial-ports_6.vb)]</span></span>  
  
8.  <span data-ttu-id="fdad7-124">Retorne a cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="fdad7-124">Return the string.</span></span>  
  
     <span data-ttu-id="fdad7-125">[!code-vb[VbVbalrMyComputer#44](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-receive-strings-from-serial-ports_7.vb)]</span><span class="sxs-lookup"><span data-stu-id="fdad7-125">[!code-vb[VbVbalrMyComputer#44](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-receive-strings-from-serial-ports_7.vb)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="fdad7-126">Exemplo</span><span class="sxs-lookup"><span data-stu-id="fdad7-126">Example</span></span>  
 <span data-ttu-id="fdad7-127">[!code-vb[VbVbalrMyComputer#37](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-receive-strings-from-serial-ports_8.vb)]</span><span class="sxs-lookup"><span data-stu-id="fdad7-127">[!code-vb[VbVbalrMyComputer#37](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-receive-strings-from-serial-ports_8.vb)]</span></span>  
  
 <span data-ttu-id="fdad7-128">Este exemplo de código também está disponível como um trecho de código do IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="fdad7-128">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="fdad7-129">No selecionador de trecho de código, ele está localizado em **Conectividade e Redes**.</span><span class="sxs-lookup"><span data-stu-id="fdad7-129">In the code snippet picker, it is located in **Connectivity and Networking**.</span></span> <span data-ttu-id="fdad7-130">Para obter mais informações, consulte [Trechos de Código](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="fdad7-130">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="fdad7-131">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="fdad7-131">Compiling the Code</span></span>  
 <span data-ttu-id="fdad7-132">Este exemplo pressupõe que o computador esteja usando a `COM1`.</span><span class="sxs-lookup"><span data-stu-id="fdad7-132">This example assumes the computer is using `COM1`.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="fdad7-133">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="fdad7-133">Robust Programming</span></span>  
 <span data-ttu-id="fdad7-134">Este exemplo pressupõe que o computador esteja usando a `COM1`.</span><span class="sxs-lookup"><span data-stu-id="fdad7-134">This example assumes the computer is using `COM1`.</span></span> <span data-ttu-id="fdad7-135">Para obter mais flexibilidade, o código deve permitir que o usuário selecione a porta serial desejada na lista de portas disponíveis.</span><span class="sxs-lookup"><span data-stu-id="fdad7-135">For more flexibility, the code should allow the user to select the desired serial port from a list of available ports.</span></span> <span data-ttu-id="fdad7-136">Para obter mais informações, consulte [Como mostrar portas seriais disponíveis](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md).</span><span class="sxs-lookup"><span data-stu-id="fdad7-136">For more information, see [How to: Show Available Serial Ports](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md).</span></span>  
  
 <span data-ttu-id="fdad7-137">Este exemplo usa um bloco `Try...Catch...Finally` para garantir que o aplicativo feche a porta e capture quaisquer exceções de tempo limite.</span><span class="sxs-lookup"><span data-stu-id="fdad7-137">This example uses a `Try...Catch...Finally` block to make sure that the application closes the port and to catch any timeout exceptions.</span></span> <span data-ttu-id="fdad7-138">Para obter mais informações, consulte [Instrução Try...Catch...Finally](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span><span class="sxs-lookup"><span data-stu-id="fdad7-138">For more information, see [Try...Catch...Finally Statement](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fdad7-139">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fdad7-139">See Also</span></span>  
 <span data-ttu-id="fdad7-140"><xref:Microsoft.VisualBasic.Devices.Ports></span><span class="sxs-lookup"><span data-stu-id="fdad7-140"><xref:Microsoft.VisualBasic.Devices.Ports></span></span>   
 <span data-ttu-id="fdad7-141"><xref:System.IO.Ports.SerialPort?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="fdad7-141"><xref:System.IO.Ports.SerialPort?displayProperty=fullName></span></span>   
 <span data-ttu-id="fdad7-142">[Como discar modems conectados às portas seriais](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-dial-modems-attached-to-serial-ports.md) </span><span class="sxs-lookup"><span data-stu-id="fdad7-142">[How to: Dial Modems Attached to Serial Ports](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-dial-modems-attached-to-serial-ports.md) </span></span>  
 <span data-ttu-id="fdad7-143">[Como enviar cadeias de caracteres para portas seriais](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-send-strings-to-serial-ports.md) </span><span class="sxs-lookup"><span data-stu-id="fdad7-143">[How to: Send Strings to Serial Ports](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-send-strings-to-serial-ports.md) </span></span>  
 [<span data-ttu-id="fdad7-144">Como Mostrar Portas Seriais Disponíveis</span><span class="sxs-lookup"><span data-stu-id="fdad7-144">How to: Show Available Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md)

