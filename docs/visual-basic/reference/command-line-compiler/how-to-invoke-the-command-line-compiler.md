---
title: 'Como: chamar o compilador de linha de comando (Visual Basic) | Documentos do Microsoft'
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
- command-line arguments
- vbc.exe
- Visual Basic compiler, starting
- command line, arguments
ms.assetid: 0fd9a8f6-f34e-4c35-a49d-9b9bbd8da4a9
caps.latest.revision: 28
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: e19bb506b016b774d2c497f8b17d91b35afb3eef
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-invoke-the-command-line-compiler-visual-basic"></a><span data-ttu-id="6ee63-102">Como invocar o compilador de linha de comando (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6ee63-102">How to: Invoke the Command-Line Compiler (Visual Basic)</span></span>
<span data-ttu-id="6ee63-103">Você pode chamar o compilador de linha de comando, digitando o nome do seu arquivo executável na linha de comando, também conhecido como prompt do MS-DOS.</span><span class="sxs-lookup"><span data-stu-id="6ee63-103">You can invoke the command-line compiler by typing the name of its executable file into the command line, also known as the MS-DOS prompt.</span></span> <span data-ttu-id="6ee63-104">Se você compilar a partir do Prompt de comando padrão, você deve digitar o caminho totalmente qualificado para o arquivo executável.</span><span class="sxs-lookup"><span data-stu-id="6ee63-104">If you compile from the default Windows Command Prompt, you must type the fully qualified path to the executable file.</span></span> <span data-ttu-id="6ee63-105">Para substituir esse comportamento padrão, você pode usar o [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)] Prompt de comando, ou modificar a variável de ambiente PATH.</span><span class="sxs-lookup"><span data-stu-id="6ee63-105">To override this default behavior, you can either use the [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)] Command Prompt, or modify the PATH environment variable.</span></span> <span data-ttu-id="6ee63-106">Permitem que você compile a partir de qualquer diretório simplesmente digitando o nome do compilador.</span><span class="sxs-lookup"><span data-stu-id="6ee63-106">Both allow you to compile from any directory by simply typing the compiler name.</span></span>  
  
[!INCLUDE[note_settings_general](../../../csharp/language-reference/compiler-messages/includes/note_settings_general_md.md)]  
  
### <a name="to-invoke-the-compiler-using-the-visual-studio-command-prompt"></a><span data-ttu-id="6ee63-107">Para chamar o compilador utilizando o Prompt de comando do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="6ee63-107">To invoke the compiler using the Visual Studio Command Prompt</span></span>  
  
1.  <span data-ttu-id="6ee63-108">Abra a pasta de programa ferramentas do Visual Studio dentro do grupo de programas do Microsoft Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="6ee63-108">Open the Visual Studio Tools program folder within the Microsoft Visual Studio program group.</span></span>  
  
2.  <span data-ttu-id="6ee63-109">Você pode usar o [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)] Prompt de comando para acessar o compilador de qualquer diretório no computador, se o Visual Studio está instalado.</span><span class="sxs-lookup"><span data-stu-id="6ee63-109">You can use the [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)] Command Prompt to access the compiler from any directory on your machine, if Visual Studio is installed.</span></span>  
  
3.  <span data-ttu-id="6ee63-110">Invocar o [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)] Prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="6ee63-110">Invoke the [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)] Command Prompt.</span></span>  
  
4.  <span data-ttu-id="6ee63-111">Na linha de comando, digite `vbc.exe` *sourceFileName* e pressione ENTER.</span><span class="sxs-lookup"><span data-stu-id="6ee63-111">At the command line, type `vbc.exe` *sourceFileName* and then press ENTER.</span></span>  
  
     <span data-ttu-id="6ee63-112">Por exemplo, se você armazenou seu código-fonte em um diretório chamado `SourceFiles`, abra o Prompt de comando e digite `cd SourceFiles` para alterar para aquele diretório.</span><span class="sxs-lookup"><span data-stu-id="6ee63-112">For example, if you stored your source code in a directory called `SourceFiles`, you would open the Command Prompt and type `cd SourceFiles` to change to that directory.</span></span> <span data-ttu-id="6ee63-113">Se o diretório contiver um arquivo de origem denominado `Source.vb`, você pode compilá-lo digitando `vbc.exe Source.vb`.</span><span class="sxs-lookup"><span data-stu-id="6ee63-113">If the directory contained a source file named `Source.vb`, you could compile it by typing `vbc.exe Source.vb`.</span></span>  
  
### <a name="to-set-the-path-environment-variable-to-the-compiler-for-the-windows-command-prompt"></a><span data-ttu-id="6ee63-114">Para definir a variável de ambiente PATH para o compilador para o Prompt de comando do Windows</span><span class="sxs-lookup"><span data-stu-id="6ee63-114">To set the PATH environment variable to the compiler for the Windows Command Prompt</span></span>  
  
1.  <span data-ttu-id="6ee63-115">Use o recurso de pesquisa do Windows para localizar Vbc.exe em seu disco local.</span><span class="sxs-lookup"><span data-stu-id="6ee63-115">Use the Windows Search feature to find Vbc.exe on your local disk.</span></span>  
  
     <span data-ttu-id="6ee63-116">O nome exato da pasta onde está o compilador depende do local do diretório do Windows e a versão do [!INCLUDE[Compact](../../../visual-basic/reference/command-line-compiler/includes/compact_md.md)] instalado.</span><span class="sxs-lookup"><span data-stu-id="6ee63-116">The exact name of the directory where the compiler is located depends on the location of the Windows directory and the version of the [!INCLUDE[Compact](../../../visual-basic/reference/command-line-compiler/includes/compact_md.md)] installed.</span></span> <span data-ttu-id="6ee63-117">Se você tiver mais de uma versão dos [!INCLUDE[Compact](../../../visual-basic/reference/command-line-compiler/includes/compact_md.md)] instalado, você deve determinar qual versão usar (geralmente a versão mais recente).</span><span class="sxs-lookup"><span data-stu-id="6ee63-117">If you have more than one version of the [!INCLUDE[Compact](../../../visual-basic/reference/command-line-compiler/includes/compact_md.md)] installed, you must determine which version to use (typically the latest version).</span></span>  
  
2.  <span data-ttu-id="6ee63-118">De seu **iniciar** Menu, clique com botão direito **meu computador**e, em seguida, clique em **propriedades** no menu de atalho.</span><span class="sxs-lookup"><span data-stu-id="6ee63-118">From your **Start** Menu, right-click **My Computer**, and then click **Properties** from the shortcut menu.</span></span>  
  
3.  <span data-ttu-id="6ee63-119">Clique o **avançado** guia e, em seguida, clique em **variáveis de ambiente**.</span><span class="sxs-lookup"><span data-stu-id="6ee63-119">Click the **Advanced** tab, and then click **Environment Variables**.</span></span>  
  
4.  <span data-ttu-id="6ee63-120">No **sistema** painel variáveis, selecione **caminho** na lista e clique em **editar**.</span><span class="sxs-lookup"><span data-stu-id="6ee63-120">In the **System** variables pane, select **Path** from the list and click **Edit**.</span></span>  
  
5.  <span data-ttu-id="6ee63-121">No **sistema editar** caixa de diálogo variável, mover o ponto de inserção para o final da cadeia de caracteres de **valor da variável** e digite um ponto e vírgula (;) seguido pelo nome do diretório completo encontrado na etapa 1.</span><span class="sxs-lookup"><span data-stu-id="6ee63-121">In the **Edit System** Variable dialog box, move the insertion point to the end of the string in the **Variable Value** field and type a semicolon (;) followed by the full directory name found in Step 1.</span></span>  
  
6.  <span data-ttu-id="6ee63-122">Clique em **Okey** para confirmar suas edições e fechar as caixas de diálogo.</span><span class="sxs-lookup"><span data-stu-id="6ee63-122">Click **OK** to confirm your edits and close the dialog boxes.</span></span>  
  
     <span data-ttu-id="6ee63-123">Depois de alterar a variável de ambiente PATH, você pode executar o [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compilador no Prompt de comando do Windows de qualquer diretório no computador.</span><span class="sxs-lookup"><span data-stu-id="6ee63-123">After you change the PATH environment variable, you can run the [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compiler at the Windows Command Prompt from any directory on the computer.</span></span>  
  
### <a name="to-invoke-the-compiler-using-the-windows-command-prompt"></a><span data-ttu-id="6ee63-124">Para chamar o compilador utilizando o Prompt de comando do Windows</span><span class="sxs-lookup"><span data-stu-id="6ee63-124">To invoke the compiler using the Windows Command Prompt</span></span>  
  
1.  <span data-ttu-id="6ee63-125">Do **iniciar** menu, clique no **Acessórios** pasta e abra o **Prompt de comando do Windows**.</span><span class="sxs-lookup"><span data-stu-id="6ee63-125">From the **Start** menu, click on the **Accessories** folder, and then open the **Windows Command Prompt**.</span></span>  
  
2.  <span data-ttu-id="6ee63-126">Na linha de comando, digite `vbc.exe` *sourceFileName* e pressione ENTER.</span><span class="sxs-lookup"><span data-stu-id="6ee63-126">At the command line, type `vbc.exe`*sourceFileName* and then press ENTER.</span></span>  
  
     <span data-ttu-id="6ee63-127">Por exemplo, se você armazenou seu código-fonte em um diretório chamado `SourceFiles`, abra o Prompt de comando e digite `cd SourceFiles` para alterar para aquele diretório.</span><span class="sxs-lookup"><span data-stu-id="6ee63-127">For example, if you stored your source code in a directory called `SourceFiles`, you would open the Command Prompt and type `cd SourceFiles` to change to that directory.</span></span> <span data-ttu-id="6ee63-128">Se o diretório contiver um arquivo de origem denominado `Source.vb`, você pode compilá-lo digitando `vbc.exe Source.vb`.</span><span class="sxs-lookup"><span data-stu-id="6ee63-128">If the directory contained a source file named `Source.vb`, you could compile it by typing `vbc.exe Source.vb`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ee63-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6ee63-129">See Also</span></span>  
 <span data-ttu-id="6ee63-130">[Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md) </span><span class="sxs-lookup"><span data-stu-id="6ee63-130">[Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md) </span></span>  
<span data-ttu-id="6ee63-131"> [Compilação Condicional](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)</span><span class="sxs-lookup"><span data-stu-id="6ee63-131"> [Conditional Compilation](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)</span></span>
