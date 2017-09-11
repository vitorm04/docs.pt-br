---
title: "Como: configurar variáveis de ambiente para a linha de comando do Visual Studio"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- cs.build.commandline
dev_langs:
- CSharp
helpviewer_keywords:
- csc.exe, command-line builds
- Visual C#, command-line builds
- command-line compilers, Visual C#
- Vsvars32.bat
- builds [C#], command-line
- compilers, invoking from command line
- Vcvars32.bat file
- command line [C#], building from
- Visual C# compiler, enabling
- compiling source code, from command line
ms.assetid: 7ec09480-5612-4f6a-8d00-ad90ea9bca5d
caps.latest.revision: 15
author: BillWagner
ms.author: wiwagn
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
ms.openlocfilehash: 569683169c6d7ae50c33ed06d3b365a663f16715
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-set-environment-variables-for-the-visual-studio-command-line"></a><span data-ttu-id="128e1-102">Como: configurar variáveis de ambiente para a linha de comando do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="128e1-102">How to: Set Environment Variables for the Visual Studio Command Line</span></span>
<span data-ttu-id="128e1-103">O arquivo vsvars32.bat define as variáveis de ambiente adequadas para habilitar builds de linha de comando.</span><span class="sxs-lookup"><span data-stu-id="128e1-103">The vsvars32.bat file sets the appropriate environment variables to enable command-line builds.</span></span> <span data-ttu-id="128e1-104">Para obter mais informações sobre vsvars32.bat, consulte [Knowledge Base article Q248802 (Artigo da base de dados de conhecimento Q248802)](http://go.microsoft.com/fwlink/?LinkId=225042).</span><span class="sxs-lookup"><span data-stu-id="128e1-104">For more information about vsvars32.bat, see [Knowledge Base article Q248802](http://go.microsoft.com/fwlink/?LinkId=225042).</span></span>  
  
 <span data-ttu-id="128e1-105">Se a versão atual do Visual Studio estiver instalada em um computador que também tem uma versão anterior do Visual Studio, você não deverá executar vsvars32.bat ou vcvars32.bat das versões diferentes na mesma janela do Prompt de Comando.</span><span class="sxs-lookup"><span data-stu-id="128e1-105">If the current version of Visual Studio is installed on a computer that also has an earlier version of Visual Studio, you should not run vsvars32.bat or vcvars32.bat from different versions in the same Command Prompt window.</span></span>  
  
### <a name="to-run-vsvars32bat"></a><span data-ttu-id="128e1-106">Para executar VSVARS32.BAT</span><span class="sxs-lookup"><span data-stu-id="128e1-106">To run VSVARS32.BAT</span></span>  
  
1.  <span data-ttu-id="128e1-107">No menu **Iniciar**, abra o **Prompt de Comando do Desenvolvedor para VS2012**.</span><span class="sxs-lookup"><span data-stu-id="128e1-107">From the **Start** menu, open the **Developer Command Prompt for VS2012**.</span></span>  
  
2.  <span data-ttu-id="128e1-108">Altere para o subdiretório Arquivos de Programas\Microsoft Visual Studio *Versão*\Common7\Tools ou Arquivos de Programas (x86)\Microsoft Visual Studio *Versão*\Common7\Tools da sua instalação.</span><span class="sxs-lookup"><span data-stu-id="128e1-108">Change to the Program Files\Microsoft Visual Studio *Version*\Common7\Tools or Program Files (x86)\Microsoft Visual Studio *Version*\Common7\Tools subdirectory of your installation.</span></span>  
  
3.  <span data-ttu-id="128e1-109">Execute VSVARS32.bat digitando **VSVARS32**.</span><span class="sxs-lookup"><span data-stu-id="128e1-109">Run VSVARS32.bat by typing **VSVARS32**.</span></span>  
  
    > [!CAUTION]
    >  <span data-ttu-id="128e1-110">VSVARS32.bat pode variar de um computador para outro.</span><span class="sxs-lookup"><span data-stu-id="128e1-110">VSVARS32.bat can vary from computer to computer.</span></span> <span data-ttu-id="128e1-111">Não substitua um arquivo VSVARS32.bat não encontrado ou danificado com um VSVARS32.bat de outro computador.</span><span class="sxs-lookup"><span data-stu-id="128e1-111">Do not replace a missing or damaged VSVARS32.bat file with a VSVARS32.bat from another computer.</span></span> <span data-ttu-id="128e1-112">Em vez disso, execute novamente a instalação para substituir o arquivo não encontrado.</span><span class="sxs-lookup"><span data-stu-id="128e1-112">Instead, rerun setup to replace the missing file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="128e1-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="128e1-113">See Also</span></span>  
 [<span data-ttu-id="128e1-114">Build pela linha de comando com csc.exe</span><span class="sxs-lookup"><span data-stu-id="128e1-114">Command-line Building With csc.exe</span></span>](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)

