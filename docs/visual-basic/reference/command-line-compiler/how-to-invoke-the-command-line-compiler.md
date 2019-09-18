---
title: 'Como: Invocar o compilador de linha de comando (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- command-line arguments
- vbc.exe
- Visual Basic compiler, starting
- command line [Visual Basic], arguments
ms.assetid: 0fd9a8f6-f34e-4c35-a49d-9b9bbd8da4a9
ms.openlocfilehash: a81d5b4f4eae76b0306e2d27475cb8527bda0ff2
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71054227"
---
# <a name="how-to-invoke-the-command-line-compiler-visual-basic"></a><span data-ttu-id="0d5d6-102">Como: Invocar o compilador de linha de comando (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0d5d6-102">How to: Invoke the Command-Line Compiler (Visual Basic)</span></span>

<span data-ttu-id="0d5d6-103">Você pode invocar o compilador de linha de comando digitando o nome do seu arquivo executável na linha de comando, também conhecido como o prompt do MS-DOS.</span><span class="sxs-lookup"><span data-stu-id="0d5d6-103">You can invoke the command-line compiler by typing the name of its executable file into the command line, also known as the MS-DOS prompt.</span></span> <span data-ttu-id="0d5d6-104">Se você compilar a partir do prompt de comando padrão do Windows, deverá digitar o caminho totalmente qualificado para o arquivo executável.</span><span class="sxs-lookup"><span data-stu-id="0d5d6-104">If you compile from the default Windows Command Prompt, you must type the fully qualified path to the executable file.</span></span> <span data-ttu-id="0d5d6-105">Para substituir esse comportamento padrão, você pode usar o Prompt de Comando do Desenvolvedor para o Visual Studio ou modificar a variável de ambiente PATH.</span><span class="sxs-lookup"><span data-stu-id="0d5d6-105">To override this default behavior, you can either use the Developer Command Prompt for Visual Studio, or modify the PATH environment variable.</span></span> <span data-ttu-id="0d5d6-106">Ambos permitem que você compile a partir de qualquer diretório simplesmente digitando o nome do compilador.</span><span class="sxs-lookup"><span data-stu-id="0d5d6-106">Both allow you to compile from any directory by simply typing the compiler name.</span></span>

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="to-invoke-the-compiler-using-the-developer-command-prompt-for-visual-studio"></a><span data-ttu-id="0d5d6-107">Para invocar o compilador usando o Prompt de Comando do Desenvolvedor para Visual Studio</span><span class="sxs-lookup"><span data-stu-id="0d5d6-107">To invoke the compiler using the Developer Command Prompt for Visual Studio</span></span>

1. <span data-ttu-id="0d5d6-108">Abra a pasta Ferramentas do Visual Studio Program dentro do grupo de programas Microsoft Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="0d5d6-108">Open the Visual Studio Tools program folder within the Microsoft Visual Studio program group.</span></span>

2. <span data-ttu-id="0d5d6-109">Você pode usar o Prompt de Comando do Desenvolvedor para que o Visual Studio acesse o compilador de qualquer diretório em seu computador, se o Visual Studio estiver instalado.</span><span class="sxs-lookup"><span data-stu-id="0d5d6-109">You can use the Developer Command Prompt for Visual Studio to access the compiler from any directory on your machine, if Visual Studio is installed.</span></span>

3. <span data-ttu-id="0d5d6-110">Invocar o Prompt de Comando do Desenvolvedor para o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="0d5d6-110">Invoke the Developer Command Prompt for Visual Studio.</span></span>

4. <span data-ttu-id="0d5d6-111">Na linha de comando, digite `vbc.exe` *sourceFileName* e pressione Enter.</span><span class="sxs-lookup"><span data-stu-id="0d5d6-111">At the command line, type `vbc.exe` *sourceFileName* and then press ENTER.</span></span>

    <span data-ttu-id="0d5d6-112">Por exemplo, se você armazenou o código-fonte em um `SourceFiles`diretório chamado, abra o prompt de comando e `cd SourceFiles` digite para alterar para esse diretório.</span><span class="sxs-lookup"><span data-stu-id="0d5d6-112">For example, if you stored your source code in a directory called `SourceFiles`, you would open the Command Prompt and type `cd SourceFiles` to change to that directory.</span></span> <span data-ttu-id="0d5d6-113">Se o diretório contiver um arquivo de `Source.vb`origem chamado, você poderá compilá- `vbc.exe Source.vb`lo digitando.</span><span class="sxs-lookup"><span data-stu-id="0d5d6-113">If the directory contained a source file named `Source.vb`, you could compile it by typing `vbc.exe Source.vb`.</span></span>

## <a name="to-set-the-path-environment-variable-to-the-compiler-for-the-windows-command-prompt"></a><span data-ttu-id="0d5d6-114">Para definir a variável de ambiente PATH para o compilador para o prompt de comando do Windows</span><span class="sxs-lookup"><span data-stu-id="0d5d6-114">To set the PATH environment variable to the compiler for the Windows Command Prompt</span></span>

1. <span data-ttu-id="0d5d6-115">Use o recurso de pesquisa do Windows para localizar o Vbc. exe no disco local.</span><span class="sxs-lookup"><span data-stu-id="0d5d6-115">Use the Windows Search feature to find Vbc.exe on your local disk.</span></span>

    <span data-ttu-id="0d5d6-116">O nome exato do diretório em que o compilador está localizado depende do local do diretório do Windows e da versão do ".NET Framework" instalado.</span><span class="sxs-lookup"><span data-stu-id="0d5d6-116">The exact name of the directory where the compiler is located depends on the location of the Windows directory and the version of the ".NET Framework" installed.</span></span> <span data-ttu-id="0d5d6-117">Se você tiver mais de uma versão do ".NET Framework" instalada, deverá determinar qual versão usar (normalmente a versão mais recente).</span><span class="sxs-lookup"><span data-stu-id="0d5d6-117">If you have more than one version of the ".NET Framework" installed, you must determine which version to use (typically the latest version).</span></span>

2. <span data-ttu-id="0d5d6-118">No menu **Iniciar** , clique com o botão direito do mouse em **meu computador**e, em seguida, clique em **Propriedades** no menu de atalho.</span><span class="sxs-lookup"><span data-stu-id="0d5d6-118">From your **Start** Menu, right-click **My Computer**, and then click **Properties** from the shortcut menu.</span></span>

3. <span data-ttu-id="0d5d6-119">Clique na guia **avançado** e, em seguida, clique em **variáveis de ambiente**.</span><span class="sxs-lookup"><span data-stu-id="0d5d6-119">Click the **Advanced** tab, and then click **Environment Variables**.</span></span>

4. <span data-ttu-id="0d5d6-120">No painel variáveis do **sistema** , selecione **caminho** na lista e clique em **Editar**.</span><span class="sxs-lookup"><span data-stu-id="0d5d6-120">In the **System** variables pane, select **Path** from the list and click **Edit**.</span></span>

5. <span data-ttu-id="0d5d6-121">Na caixa de diálogo Editar variável do **sistema** , mova o ponto de inserção para o final da cadeia de caracteres no campo **valor da variável** e digite um ponto e vírgula (;) seguido do nome completo do diretório encontrado na etapa 1.</span><span class="sxs-lookup"><span data-stu-id="0d5d6-121">In the **Edit System** Variable dialog box, move the insertion point to the end of the string in the **Variable Value** field and type a semicolon (;) followed by the full directory name found in Step 1.</span></span>

6. <span data-ttu-id="0d5d6-122">Clique em **OK** para confirmar suas edições e fechar as caixas de diálogo.</span><span class="sxs-lookup"><span data-stu-id="0d5d6-122">Click **OK** to confirm your edits and close the dialog boxes.</span></span>

     <span data-ttu-id="0d5d6-123">Depois de alterar a variável de ambiente PATH, você pode executar o compilador Visual Basic no prompt de comando do Windows de qualquer diretório no computador.</span><span class="sxs-lookup"><span data-stu-id="0d5d6-123">After you change the PATH environment variable, you can run the Visual Basic compiler at the Windows Command Prompt from any directory on the computer.</span></span>

## <a name="to-invoke-the-compiler-using-the-windows-command-prompt"></a><span data-ttu-id="0d5d6-124">Para invocar o compilador usando o prompt de comando do Windows</span><span class="sxs-lookup"><span data-stu-id="0d5d6-124">To invoke the compiler using the Windows Command Prompt</span></span>

1. <span data-ttu-id="0d5d6-125">No menu **Iniciar** , clique na pasta **acessórios** e, em seguida, abra o **prompt de comando do Windows**.</span><span class="sxs-lookup"><span data-stu-id="0d5d6-125">From the **Start** menu, click on the **Accessories** folder, and then open the **Windows Command Prompt**.</span></span>

2. <span data-ttu-id="0d5d6-126">Na linha de comando, digite `vbc.exe` *sourceFileName* e pressione Enter.</span><span class="sxs-lookup"><span data-stu-id="0d5d6-126">At the command line, type `vbc.exe`*sourceFileName* and then press ENTER.</span></span>

     <span data-ttu-id="0d5d6-127">Por exemplo, se você armazenou o código-fonte em um `SourceFiles`diretório chamado, abra o prompt de comando e `cd SourceFiles` digite para alterar para esse diretório.</span><span class="sxs-lookup"><span data-stu-id="0d5d6-127">For example, if you stored your source code in a directory called `SourceFiles`, you would open the Command Prompt and type `cd SourceFiles` to change to that directory.</span></span> <span data-ttu-id="0d5d6-128">Se o diretório contiver um arquivo de `Source.vb`origem chamado, você poderá compilá- `vbc.exe Source.vb`lo digitando.</span><span class="sxs-lookup"><span data-stu-id="0d5d6-128">If the directory contained a source file named `Source.vb`, you could compile it by typing `vbc.exe Source.vb`.</span></span>

## <a name="see-also"></a><span data-ttu-id="0d5d6-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0d5d6-129">See also</span></span>

- [<span data-ttu-id="0d5d6-130">Compilador de linha de comando do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0d5d6-130">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="0d5d6-131">Compilação Condicional</span><span class="sxs-lookup"><span data-stu-id="0d5d6-131">Conditional Compilation</span></span>](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
