---
title: "Como mostrar portas seriais disponíveis no Visual Basic"
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
- serial ports, availability
- My.Computer.Ports.SerialPortNames property
- My.Computer.Ports object
- ports, serial port availability
ms.assetid: eaf2ee5a-8103-4e10-a205-ed1d4db120ba
caps.latest.revision: 20
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
ms.openlocfilehash: bab6177c788a847b46586db19a525c1a1b36476d
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-show-available-serial-ports-in-visual-basic"></a><span data-ttu-id="fb744-102">Como mostrar portas seriais disponíveis no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="fb744-102">How to: Show Available Serial Ports in Visual Basic</span></span>
<span data-ttu-id="fb744-103">Este tópico descreve como usar `My.Computer.Ports` para mostrar as portas seriais disponíveis do computador no [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span><span class="sxs-lookup"><span data-stu-id="fb744-103">This topic describes how to use `My.Computer.Ports` to show the available serial ports of the computer in [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span></span>  
  
 <span data-ttu-id="fb744-104">Para permitir que um usuário selecione qual porta usar, os nomes das portas seriais são colocados em um controle <xref:System.Windows.Forms.ListBox>.</span><span class="sxs-lookup"><span data-stu-id="fb744-104">To allow a user to select which port to use, the names of the serial ports are placed in a <xref:System.Windows.Forms.ListBox> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fb744-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="fb744-105">Example</span></span>  
 <span data-ttu-id="fb744-106">Este exemplo faz um loop em todas as cadeias de caracteres que a propriedade `My.Computer.Ports.SerialPortNames` retorna.</span><span class="sxs-lookup"><span data-stu-id="fb744-106">This example loops over all the strings that the `My.Computer.Ports.SerialPortNames` property returns.</span></span> <span data-ttu-id="fb744-107">Essas cadeias de caracteres são os nomes das portas seriais disponíveis no computador.</span><span class="sxs-lookup"><span data-stu-id="fb744-107">These strings are the names of the available serial ports on the computer.</span></span>  
  
 <span data-ttu-id="fb744-108">Normalmente, um usuário seleciona qual porta serial o aplicativo deve usar na lista de portas disponíveis.</span><span class="sxs-lookup"><span data-stu-id="fb744-108">Typically, a user selects which serial port the application should use from the list of available ports.</span></span> <span data-ttu-id="fb744-109">Neste exemplo, os nomes das portas seriais são armazenados em um controle <xref:System.Windows.Forms.ListBox>.</span><span class="sxs-lookup"><span data-stu-id="fb744-109">In this example, the serial port names are stored in a <xref:System.Windows.Forms.ListBox> control.</span></span> <span data-ttu-id="fb744-110">Para saber mais, veja [Controle ListBox](../../../../framework/winforms/controls/listbox-control-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="fb744-110">For more information, see [ListBox Control](../../../../framework/winforms/controls/listbox-control-windows-forms.md).</span></span>  
  
 <span data-ttu-id="fb744-111">[!code-vb[VbVbalrMyComputer#45](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-show-available-serial-ports_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="fb744-111">[!code-vb[VbVbalrMyComputer#45](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-show-available-serial-ports_1.vb)]</span></span>  
  
 <span data-ttu-id="fb744-112">Este exemplo de código também está disponível como um trecho de código do IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="fb744-112">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="fb744-113">No selecionador de trecho de código, ele está localizado em **Conectividade e Redes**.</span><span class="sxs-lookup"><span data-stu-id="fb744-113">In the code snippet picker, it is located in **Connectivity and Networking**.</span></span> <span data-ttu-id="fb744-114">Para obter mais informações, consulte [Trechos de Código](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="fb744-114">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="fb744-115">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="fb744-115">Compiling the Code</span></span>  
 <span data-ttu-id="fb744-116">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="fb744-116">This example requires:</span></span>  
  
-   <span data-ttu-id="fb744-117">Uma referência de projeto ao System.Windows.Forms.dll.</span><span class="sxs-lookup"><span data-stu-id="fb744-117">A project reference to System.Windows.Forms.dll.</span></span>  
  
-   <span data-ttu-id="fb744-118">Acesso aos membros do namespace <xref:System.Windows.Forms>.</span><span class="sxs-lookup"><span data-stu-id="fb744-118">Access to the members of the <xref:System.Windows.Forms> namespace.</span></span> <span data-ttu-id="fb744-119">Adicione uma instrução `Imports` se você não está qualificando totalmente os nomes de membros em seu código.</span><span class="sxs-lookup"><span data-stu-id="fb744-119">Add an `Imports` statement if you are not fully qualifying member names in your code.</span></span> <span data-ttu-id="fb744-120">Para obter mais informações, consulte [Instrução Imports (tipo e namespace .NET)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span><span class="sxs-lookup"><span data-stu-id="fb744-120">For more information, see [Imports Statement (.NET Namespace and Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span></span>  
  
-   <span data-ttu-id="fb744-121">Que seu formulário tenha um controle <xref:System.Windows.Forms.ListBox> chamado `ListBox1`.</span><span class="sxs-lookup"><span data-stu-id="fb744-121">That your form have a <xref:System.Windows.Forms.ListBox> control named `ListBox1`.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="fb744-122">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="fb744-122">Robust Programming</span></span>  
 <span data-ttu-id="fb744-123">Você não precisa usar o controle <xref:System.Windows.Forms.ListBox> para exibir os nomes das portas seriais disponíveis.</span><span class="sxs-lookup"><span data-stu-id="fb744-123">You do not have to use the <xref:System.Windows.Forms.ListBox> control to display the available serial port names.</span></span> <span data-ttu-id="fb744-124">Em vez disso, você pode usar um <xref:System.Windows.Forms.ComboBox> ou outro controle.</span><span class="sxs-lookup"><span data-stu-id="fb744-124">Instead, you can use a <xref:System.Windows.Forms.ComboBox> or other control.</span></span> <span data-ttu-id="fb744-125">Se o aplicativo não precisa de uma resposta do usuário, você pode usar um controle <xref:System.Windows.Forms.TextBox> para exibir as informações.</span><span class="sxs-lookup"><span data-stu-id="fb744-125">If the application does not need a response from the user, you can use a <xref:System.Windows.Forms.TextBox> control to display the information.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fb744-126">Os nomes das portas retornados por `My.Computer.Ports.SerialPortNames` podem estar incorretos quando executados no Windows 98.</span><span class="sxs-lookup"><span data-stu-id="fb744-126">The port names returned by `My.Computer.Ports.SerialPortNames` may be incorrect when run on Windows 98.</span></span> <span data-ttu-id="fb744-127">Para evitar erros de aplicativo, use o tratamento de exceções, como a instrução `Try...Catch...Finally` ou a instrução `Using`, ao usar os nomes de portas para abrir portas.</span><span class="sxs-lookup"><span data-stu-id="fb744-127">To prevent application errors, use exception handling, such as the `Try...Catch...Finally` statement or the `Using` statement, when using the port names to open ports.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb744-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fb744-128">See Also</span></span>  
 <span data-ttu-id="fb744-129"><xref:Microsoft.VisualBasic.Devices.Ports></span><span class="sxs-lookup"><span data-stu-id="fb744-129"><xref:Microsoft.VisualBasic.Devices.Ports></span></span>   
 <span data-ttu-id="fb744-130">[Como discar modems conectados às portas seriais](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-dial-modems-attached-to-serial-ports.md) </span><span class="sxs-lookup"><span data-stu-id="fb744-130">[How to: Dial Modems Attached to Serial Ports](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-dial-modems-attached-to-serial-ports.md) </span></span>  
 <span data-ttu-id="fb744-131">[Como enviar cadeias de caracteres para portas seriais](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-send-strings-to-serial-ports.md) </span><span class="sxs-lookup"><span data-stu-id="fb744-131">[How to: Send Strings to Serial Ports](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-send-strings-to-serial-ports.md) </span></span>  
 [<span data-ttu-id="fb744-132">Como Receber Cadeias de Caracteres de Portas Seriais</span><span class="sxs-lookup"><span data-stu-id="fb744-132">How to: Receive Strings From Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-receive-strings-from-serial-ports.md)

