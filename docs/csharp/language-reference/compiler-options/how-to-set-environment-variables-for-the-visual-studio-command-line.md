---
title: "Como: configurar variáveis de ambiente para a linha de comando do Visual Studio"
ms.date: 09-29-2017
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: cs.build.commandline
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
caps.latest.revision: "15"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 8012e310bb04ec3acef0790f9cd50ed42dd9286a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-set-environment-variables-for-the-visual-studio-command-line"></a><span data-ttu-id="ec4a7-102">Como: configurar variáveis de ambiente para a linha de comando do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="ec4a7-102">How to: Set Environment Variables for the Visual Studio Command Line</span></span>

<span data-ttu-id="ec4a7-103">O arquivo VsDevCmd.bat define as variáveis de ambiente apropriadas para habilitar as compilações de linha de comando.</span><span class="sxs-lookup"><span data-stu-id="ec4a7-103">The VsDevCmd.bat file sets the appropriate environment variables to enable command-line builds.</span></span> <span data-ttu-id="ec4a7-104">Para obter mais informações sobre VsDevCmd.bat, consulte [artigo da Base de dados de Conhecimento Q248802](http://go.microsoft.com/fwlink/?LinkId=225042).</span><span class="sxs-lookup"><span data-stu-id="ec4a7-104">For more information about VsDevCmd.bat, see [Knowledge Base article Q248802](http://go.microsoft.com/fwlink/?LinkId=225042).</span></span>  

> [!NOTE]
> <span data-ttu-id="ec4a7-105">O arquivo VsDevCmd.bat é um novo arquivo fornecido com o Visual Studio de 2017.</span><span class="sxs-lookup"><span data-stu-id="ec4a7-105">The VsDevCmd.bat file is a new file delivered with Visual Studio 2017.</span></span> <span data-ttu-id="ec4a7-106">Visual Studio 2015 e versões anteriores usados VSVARS32.bat para a mesma finalidade.</span><span class="sxs-lookup"><span data-stu-id="ec4a7-106">Visual Studio 2015 and earlier versions used VSVARS32.bat for the same purpose.</span></span> <span data-ttu-id="ec4a7-107">Esse arquivo foi armazenado no Visual Studio de \Program Files\Microsoft\\*versão*\Common7\Tools ou (x86) os arquivos de programas \Microsoft Visual Studio\\*versão*\Common7\Tools.</span><span class="sxs-lookup"><span data-stu-id="ec4a7-107">This file was stored in \Program Files\Microsoft Visual Studio\\*Version*\Common7\Tools or Program Files (x86)\Microsoft Visual Studio\\*Version*\Common7\Tools.</span></span>
  
<span data-ttu-id="ec4a7-108">Se a versão atual do Visual Studio está instalada em um computador que também tem uma versão anterior do Visual Studio, você não deve executar VsDevCmd.bat e VSVARS32. BAT de versões diferentes na mesma janela do Prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="ec4a7-108">If the current version of Visual Studio is installed on a computer that also has an earlier version of Visual Studio, you should not run VsDevCmd.bat and VSVARS32.BAT from different versions in the same Command Prompt window.</span></span> <span data-ttu-id="ec4a7-109">Em vez disso, você deve executar o comando para cada versão em sua própria janela.</span><span class="sxs-lookup"><span data-stu-id="ec4a7-109">Instead, you should run the command for each version in its own window.</span></span>
  
### <a name="to-run-vsdevcmdbat"></a><span data-ttu-id="ec4a7-110">Para executar VsDevCmd.BAT</span><span class="sxs-lookup"><span data-stu-id="ec4a7-110">To run VsDevCmd.BAT</span></span>  
  
1.  <span data-ttu-id="ec4a7-111">Do **iniciar** menu, abrir o **Prompt de comando do desenvolvedor para VS 2017**.</span><span class="sxs-lookup"><span data-stu-id="ec4a7-111">From the **Start** menu, open the **Developer Command Prompt for VS 2017**.</span></span>  <span data-ttu-id="ec4a7-112">Ele está no **2017 do Visual Studio** pasta.</span><span class="sxs-lookup"><span data-stu-id="ec4a7-112">It's in the **Visual Studio 2017** folder.</span></span>
  
2.  <span data-ttu-id="ec4a7-113">Altere para o Visual Studio \Program Files\Microsoft\\*versão*\\*oferta*\Common7\Tools ou \Program arquivos (x86) \Microsoft Visual Studio\\ *Versão*\\*oferta*\Common7\Tools subdiretório de sua instalação.</span><span class="sxs-lookup"><span data-stu-id="ec4a7-113">Change to the \Program Files\Microsoft Visual Studio\\*Version*\\*Offering*\Common7\Tools or \Program Files (x86)\Microsoft Visual Studio\\*Version*\\*Offering*\Common7\Tools subdirectory of your installation.</span></span>  <span data-ttu-id="ec4a7-114">(*Versão* é *2017* para a versão atual.</span><span class="sxs-lookup"><span data-stu-id="ec4a7-114">(*Version* is *2017* for the current version.</span></span> <span data-ttu-id="ec4a7-115">*Oferta* é um dos *Enterprise*, *Professional* ou *Community*.)</span><span class="sxs-lookup"><span data-stu-id="ec4a7-115">*Offering* is one of *Enterprise*, *Professional* or *Community*.)</span></span>
  
3.  <span data-ttu-id="ec4a7-116">Execute VsDevCmd.bat digitando **VsDevCmd**.</span><span class="sxs-lookup"><span data-stu-id="ec4a7-116">Run VsDevCmd.bat by typing **VsDevCmd**.</span></span>  
  
    > [!CAUTION]
    >  <span data-ttu-id="ec4a7-117">VsDevCmd.bat pode variar de um computador para outro.</span><span class="sxs-lookup"><span data-stu-id="ec4a7-117">VsDevCmd.bat can vary from computer to computer.</span></span> <span data-ttu-id="ec4a7-118">Não substitua um arquivo de VsDevCmd.bat ausente ou danificado com um VsDevCmd.bat de outro computador.</span><span class="sxs-lookup"><span data-stu-id="ec4a7-118">Do not replace a missing or damaged VsDevCmd.bat file with a VsDevCmd.bat from another computer.</span></span> <span data-ttu-id="ec4a7-119">Em vez disso, execute novamente a instalação para substituir o arquivo não encontrado.</span><span class="sxs-lookup"><span data-stu-id="ec4a7-119">Instead, rerun setup to replace the missing file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec4a7-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ec4a7-120">See Also</span></span>  
 [<span data-ttu-id="ec4a7-121">Build pela linha de comando com csc.exe</span><span class="sxs-lookup"><span data-stu-id="ec4a7-121">Command-line Building With csc.exe</span></span>](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)
