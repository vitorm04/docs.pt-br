---
title: 'Como: configurar variáveis de ambiente para a linha de comando do Visual Studio.'
ms.date: 09/29/2017
f1_keywords:
- cs.build.commandline
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
ms.openlocfilehash: 9eea7f76d386816aad060e9b99cea6b906a09ab9
ms.sourcegitcommit: 438919211260bb415fc8f96ca3eabc33cf2d681d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2019
ms.locfileid: "59612115"
---
# <a name="how-to-set-environment-variables-for-the-visual-studio-command-line"></a><span data-ttu-id="8b9a0-102">Como: configurar variáveis de ambiente para a linha de comando do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="8b9a0-102">How to: Set Environment Variables for the Visual Studio Command Line</span></span>

<span data-ttu-id="8b9a0-103">O arquivo VsDevCmd.bat define as variáveis de ambiente adequadas para habilitar builds de linha de comando.</span><span class="sxs-lookup"><span data-stu-id="8b9a0-103">The VsDevCmd.bat file sets the appropriate environment variables to enable command-line builds.</span></span>

> [!NOTE]
> <span data-ttu-id="8b9a0-104">O arquivo VsDevCmd.bat é um novo arquivo fornecido com o Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="8b9a0-104">The VsDevCmd.bat file is a new file delivered with Visual Studio 2017.</span></span> <span data-ttu-id="8b9a0-105">O Visual Studio 2015 e versões anteriores usavam o VSVARS32.bat para a mesma finalidade.</span><span class="sxs-lookup"><span data-stu-id="8b9a0-105">Visual Studio 2015 and earlier versions used VSVARS32.bat for the same purpose.</span></span> <span data-ttu-id="8b9a0-106">Esse arquivo era armazenado em \Arquivos de Programas\Microsoft Visual Studio\\*Versão*\Common7\Tools ou Arquivos de Programas (x86)\Microsoft Visual Studio\\*Versão*\Common7\Tools.</span><span class="sxs-lookup"><span data-stu-id="8b9a0-106">This file was stored in \Program Files\Microsoft Visual Studio\\*Version*\Common7\Tools or Program Files (x86)\Microsoft Visual Studio\\*Version*\Common7\Tools.</span></span>

<span data-ttu-id="8b9a0-107">Se a versão atual do Visual Studio estiver instalada em um computador que também tiver uma versão anterior do Visual Studio, você não deverá executar VsDevCmd.bat e VSVARS32.bat de versões diferentes na mesma janela do Prompt de Comando.</span><span class="sxs-lookup"><span data-stu-id="8b9a0-107">If the current version of Visual Studio is installed on a computer that also has an earlier version of Visual Studio, you should not run VsDevCmd.bat and VSVARS32.BAT from different versions in the same Command Prompt window.</span></span> <span data-ttu-id="8b9a0-108">Em vez disso, você deve executar o comando para cada versão em sua própria janela.</span><span class="sxs-lookup"><span data-stu-id="8b9a0-108">Instead, you should run the command for each version in its own window.</span></span>

### <a name="to-run-vsdevcmdbat"></a><span data-ttu-id="8b9a0-109">Para executar o VsDevCmd.BAT</span><span class="sxs-lookup"><span data-stu-id="8b9a0-109">To run VsDevCmd.BAT</span></span>

1. <span data-ttu-id="8b9a0-110">No menu **Iniciar**, abra o **Prompt de Comando do Desenvolvedor para VS 2017**.</span><span class="sxs-lookup"><span data-stu-id="8b9a0-110">From the **Start** menu, open the **Developer Command Prompt for VS 2017**.</span></span>  <span data-ttu-id="8b9a0-111">Ele está na pasta do **Visual Studio 2017**.</span><span class="sxs-lookup"><span data-stu-id="8b9a0-111">It's in the **Visual Studio 2017** folder.</span></span>

2. <span data-ttu-id="8b9a0-112">Altere para o subdiretório \Arquivos de Programas\Microsoft Visual Studio\\*Versão*\\*Oferta*\Common7\Tools ou \Arquivos de Programas (x86)\Microsoft Visual Studio\\*Versão*\\*Oferta*\Common7\Tools da sua instalação.</span><span class="sxs-lookup"><span data-stu-id="8b9a0-112">Change to the \Program Files\Microsoft Visual Studio\\*Version*\\*Offering*\Common7\Tools or \Program Files (x86)\Microsoft Visual Studio\\*Version*\\*Offering*\Common7\Tools subdirectory of your installation.</span></span>  <span data-ttu-id="8b9a0-113">(a *Versão* é *2017* para a versão atual.</span><span class="sxs-lookup"><span data-stu-id="8b9a0-113">(*Version* is *2017* for the current version.</span></span> <span data-ttu-id="8b9a0-114">*Oferta* é uma entre *Enterprise*, *Professional* ou *Community*).</span><span class="sxs-lookup"><span data-stu-id="8b9a0-114">*Offering* is one of *Enterprise*, *Professional* or *Community*.)</span></span>

3. <span data-ttu-id="8b9a0-115">Execute o VsDevCmd.bat digitando **VsDevCmd**.</span><span class="sxs-lookup"><span data-stu-id="8b9a0-115">Run VsDevCmd.bat by typing **VsDevCmd**.</span></span>

    > [!CAUTION]
    > <span data-ttu-id="8b9a0-116">O VsDevCmd.bat pode variar de um computador para outro.</span><span class="sxs-lookup"><span data-stu-id="8b9a0-116">VsDevCmd.bat can vary from computer to computer.</span></span> <span data-ttu-id="8b9a0-117">Não substitua um arquivo VsDevCmd.bat não encontrado ou danificado por um VsDevCmd.bat de outro computador.</span><span class="sxs-lookup"><span data-stu-id="8b9a0-117">Do not replace a missing or damaged VsDevCmd.bat file with a VsDevCmd.bat from another computer.</span></span> <span data-ttu-id="8b9a0-118">Em vez disso, execute novamente a instalação para substituir o arquivo não encontrado.</span><span class="sxs-lookup"><span data-stu-id="8b9a0-118">Instead, rerun setup to replace the missing file.</span></span>

### <a name="available-options-for-vsdevcmdbat"></a><span data-ttu-id="8b9a0-119">Opções disponíveis para o VsDevCmd.BAT</span><span class="sxs-lookup"><span data-stu-id="8b9a0-119">Available options for VsDevCmd.BAT</span></span>

<span data-ttu-id="8b9a0-120">Para ver as opções disponíveis para VsDevCmd.BAT, execute o comando com a opção `-help`:</span><span class="sxs-lookup"><span data-stu-id="8b9a0-120">To see the available options for VsDevCmd.BAT, run the command with the `-help` option:</span></span>

```console
VsDevCmd.bat -help
```

## <a name="see-also"></a><span data-ttu-id="8b9a0-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8b9a0-121">See also</span></span>

- [<span data-ttu-id="8b9a0-122">Build pela linha de comando com csc.exe</span><span class="sxs-lookup"><span data-stu-id="8b9a0-122">Command-line Building With csc.exe</span></span>](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)
