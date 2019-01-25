---
title: 'Como: Invocar o compilador de linha de comando (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- command-line arguments
- vbc.exe
- Visual Basic compiler, starting
- command line [Visual Basic], arguments
ms.assetid: 0fd9a8f6-f34e-4c35-a49d-9b9bbd8da4a9
ms.openlocfilehash: dd5fadb9c9f248b5fb4f289bb2d24f1b085a79a8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54503723"
---
# <a name="how-to-invoke-the-command-line-compiler-visual-basic"></a><span data-ttu-id="146ce-102">Como: Invocar o compilador de linha de comando (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="146ce-102">How to: Invoke the Command-Line Compiler (Visual Basic)</span></span>
<span data-ttu-id="146ce-103">Você pode invocar o compilador de linha de comando, digitando o nome do seu arquivo executável na linha de comando, também conhecido como prompt do MS-DOS.</span><span class="sxs-lookup"><span data-stu-id="146ce-103">You can invoke the command-line compiler by typing the name of its executable file into the command line, also known as the MS-DOS prompt.</span></span> <span data-ttu-id="146ce-104">Se você compilar do Prompt de comando do Windows padrão, você deve digitar o caminho totalmente qualificado para o arquivo executável.</span><span class="sxs-lookup"><span data-stu-id="146ce-104">If you compile from the default Windows Command Prompt, you must type the fully qualified path to the executable file.</span></span> <span data-ttu-id="146ce-105">Para substituir esse comportamento padrão, você pode usar o Prompt de comando do desenvolvedor para Visual Studio ou modificar a variável de ambiente PATH.</span><span class="sxs-lookup"><span data-stu-id="146ce-105">To override this default behavior, you can either use the Developer Command Prompt for Visual Studio, or modify the PATH environment variable.</span></span> <span data-ttu-id="146ce-106">Ambos permitem que você compile de qualquer diretório simplesmente digitando o nome do compilador.</span><span class="sxs-lookup"><span data-stu-id="146ce-106">Both allow you to compile from any directory by simply typing the compiler name.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-invoke-the-compiler-using-the-developer-command-prompt-for-visual-studio"></a><span data-ttu-id="146ce-107">Para chamar o compilador usando o Prompt de comando do desenvolvedor para Visual Studio</span><span class="sxs-lookup"><span data-stu-id="146ce-107">To invoke the compiler using the Developer Command Prompt for Visual Studio</span></span>  
  
1.  <span data-ttu-id="146ce-108">Abra a pasta do programa de ferramentas do Visual Studio dentro do grupo de programas do Microsoft Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="146ce-108">Open the Visual Studio Tools program folder within the Microsoft Visual Studio program group.</span></span>  
  
2.  <span data-ttu-id="146ce-109">Você pode usar o Prompt de comando do desenvolvedor para Visual Studio para acessar o compilador a partir de qualquer diretório em seu computador, se o Visual Studio está instalado.</span><span class="sxs-lookup"><span data-stu-id="146ce-109">You can use the Developer Command Prompt for Visual Studio to access the compiler from any directory on your machine, if Visual Studio is installed.</span></span>  
  
3.  <span data-ttu-id="146ce-110">Invocar o Prompt de comando do desenvolvedor para Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="146ce-110">Invoke the Developer Command Prompt for Visual Studio.</span></span>  
  
4.  <span data-ttu-id="146ce-111">Na linha de comando, digite `vbc.exe` *sourceFileName* e, em seguida, pressione ENTER.</span><span class="sxs-lookup"><span data-stu-id="146ce-111">At the command line, type `vbc.exe` *sourceFileName* and then press ENTER.</span></span>  
  
     <span data-ttu-id="146ce-112">Por exemplo, se você armazenou seu código-fonte em um diretório chamado `SourceFiles`, abra o Prompt de comando e o tipo `cd SourceFiles` para alterar para aquele diretório.</span><span class="sxs-lookup"><span data-stu-id="146ce-112">For example, if you stored your source code in a directory called `SourceFiles`, you would open the Command Prompt and type `cd SourceFiles` to change to that directory.</span></span> <span data-ttu-id="146ce-113">Se o diretório contiver um arquivo de origem denominado `Source.vb`, você pode compilá-lo digitando `vbc.exe Source.vb`.</span><span class="sxs-lookup"><span data-stu-id="146ce-113">If the directory contained a source file named `Source.vb`, you could compile it by typing `vbc.exe Source.vb`.</span></span>  
  
### <a name="to-set-the-path-environment-variable-to-the-compiler-for-the-windows-command-prompt"></a><span data-ttu-id="146ce-114">Para definir a variável de ambiente PATH para o compilador para o Prompt de comando do Windows</span><span class="sxs-lookup"><span data-stu-id="146ce-114">To set the PATH environment variable to the compiler for the Windows Command Prompt</span></span>  
  
1.  <span data-ttu-id="146ce-115">Use o recurso do Windows Search para encontrar Vbc.exe em seu disco local.</span><span class="sxs-lookup"><span data-stu-id="146ce-115">Use the Windows Search feature to find Vbc.exe on your local disk.</span></span>  
  
     <span data-ttu-id="146ce-116">O nome exato da pasta onde está o compilador depende do local do diretório do Windows e a versão do ".NET Framework" instalado.</span><span class="sxs-lookup"><span data-stu-id="146ce-116">The exact name of the directory where the compiler is located depends on the location of the Windows directory and the version of the ".NET Framework" installed.</span></span> <span data-ttu-id="146ce-117">Se você tiver mais de uma versão do ".NET Framework" instalado, você deve determinar qual versão usar (geralmente a versão mais recente).</span><span class="sxs-lookup"><span data-stu-id="146ce-117">If you have more than one version of the ".NET Framework" installed, you must determine which version to use (typically the latest version).</span></span>  
  
2.  <span data-ttu-id="146ce-118">De seu **inicie** Menu, clique com botão direito **meu computador**e, em seguida, clique em **propriedades** no menu de atalho.</span><span class="sxs-lookup"><span data-stu-id="146ce-118">From your **Start** Menu, right-click **My Computer**, and then click **Properties** from the shortcut menu.</span></span>  
  
3.  <span data-ttu-id="146ce-119">Clique o **Advanced** guia e, em seguida, clique em **variáveis de ambiente**.</span><span class="sxs-lookup"><span data-stu-id="146ce-119">Click the **Advanced** tab, and then click **Environment Variables**.</span></span>  
  
4.  <span data-ttu-id="146ce-120">No **System** painel de variáveis, selecione **caminho** na lista e clique em **editar**.</span><span class="sxs-lookup"><span data-stu-id="146ce-120">In the **System** variables pane, select **Path** from the list and click **Edit**.</span></span>  
  
5.  <span data-ttu-id="146ce-121">No **Editar System** caixa de diálogo variável, mover o ponto de inserção para o fim da cadeia de caracteres a **valor da variável** do campo e digite um ponto e vírgula (;) seguido pelo nome do diretório completo encontrado na etapa 1.</span><span class="sxs-lookup"><span data-stu-id="146ce-121">In the **Edit System** Variable dialog box, move the insertion point to the end of the string in the **Variable Value** field and type a semicolon (;) followed by the full directory name found in Step 1.</span></span>  
  
6.  <span data-ttu-id="146ce-122">Clique em **Okey** para confirmar as edições e fechar as caixas de diálogo.</span><span class="sxs-lookup"><span data-stu-id="146ce-122">Click **OK** to confirm your edits and close the dialog boxes.</span></span>  
  
     <span data-ttu-id="146ce-123">Depois de alterar a variável de ambiente PATH, você pode executar o compilador do Visual Basic no Prompt de comando do Windows de qualquer diretório no computador.</span><span class="sxs-lookup"><span data-stu-id="146ce-123">After you change the PATH environment variable, you can run the Visual Basic compiler at the Windows Command Prompt from any directory on the computer.</span></span>  
  
### <a name="to-invoke-the-compiler-using-the-windows-command-prompt"></a><span data-ttu-id="146ce-124">Para chamar o compilador usando o Prompt de comando do Windows</span><span class="sxs-lookup"><span data-stu-id="146ce-124">To invoke the compiler using the Windows Command Prompt</span></span>  
  
1.  <span data-ttu-id="146ce-125">Dos **iniciar** menu, clique na **Acessórios** pasta e, em seguida, abra o **Prompt de comando do Windows**.</span><span class="sxs-lookup"><span data-stu-id="146ce-125">From the **Start** menu, click on the **Accessories** folder, and then open the **Windows Command Prompt**.</span></span>  
  
2.  <span data-ttu-id="146ce-126">Na linha de comando, digite `vbc.exe` *sourceFileName* e, em seguida, pressione ENTER.</span><span class="sxs-lookup"><span data-stu-id="146ce-126">At the command line, type `vbc.exe`*sourceFileName* and then press ENTER.</span></span>  
  
     <span data-ttu-id="146ce-127">Por exemplo, se você armazenou seu código-fonte em um diretório chamado `SourceFiles`, abra o Prompt de comando e o tipo `cd SourceFiles` para alterar para aquele diretório.</span><span class="sxs-lookup"><span data-stu-id="146ce-127">For example, if you stored your source code in a directory called `SourceFiles`, you would open the Command Prompt and type `cd SourceFiles` to change to that directory.</span></span> <span data-ttu-id="146ce-128">Se o diretório contiver um arquivo de origem denominado `Source.vb`, você pode compilá-lo digitando `vbc.exe Source.vb`.</span><span class="sxs-lookup"><span data-stu-id="146ce-128">If the directory contained a source file named `Source.vb`, you could compile it by typing `vbc.exe Source.vb`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="146ce-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="146ce-129">See also</span></span>
- [<span data-ttu-id="146ce-130">Compilador de linha de comando do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="146ce-130">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="146ce-131">Compilação Condicional</span><span class="sxs-lookup"><span data-stu-id="146ce-131">Conditional Compilation</span></span>](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
