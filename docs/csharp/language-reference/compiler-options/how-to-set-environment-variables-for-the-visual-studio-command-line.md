---
title: Como configurar variáveis de ambiente para a linha de comando do Visual Studio
ms.date: 12/20/2019
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
ms.openlocfilehash: 99e2a837877494dd4c7e0106047bce3cc39a9282
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75342360"
---
# <a name="how-to-set-environment-variables-for-the-visual-studio-command-line"></a><span data-ttu-id="e30f7-102">Como configurar variáveis de ambiente para a linha de comando do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="e30f7-102">How to set environment variables for the Visual Studio Command Line</span></span>

<span data-ttu-id="e30f7-103">O arquivo VsDevCmd.bat define as variáveis de ambiente adequadas para habilitar builds de linha de comando.</span><span class="sxs-lookup"><span data-stu-id="e30f7-103">The VsDevCmd.bat file sets the appropriate environment variables to enable command-line builds.</span></span>

> [!NOTE]
> <span data-ttu-id="e30f7-104">Visual Studio 2015 e versões anteriores usavam VSVARS32.bat, não VsDevCmd.bat com o mesmo propósito.</span><span class="sxs-lookup"><span data-stu-id="e30f7-104">Visual Studio 2015 and earlier versions used VSVARS32.bat, not VsDevCmd.bat for the same purpose.</span></span> <span data-ttu-id="e30f7-105">Esse arquivo era armazenado em \Arquivos de Programas\Microsoft Visual Studio\\*Versão*\Common7\Tools ou Arquivos de Programas (x86)\Microsoft Visual Studio\\*Versão*\Common7\Tools.</span><span class="sxs-lookup"><span data-stu-id="e30f7-105">This file was stored in \Program Files\Microsoft Visual Studio\\*Version*\Common7\Tools or Program Files (x86)\Microsoft Visual Studio\\*Version*\Common7\Tools.</span></span>

<span data-ttu-id="e30f7-106">Se a versão atual do Visual Studio estiver instalada em um computador que também tiver uma versão anterior do Visual Studio, você não deverá executar VsDevCmd.bat e VSVARS32.bat de versões diferentes na mesma janela do Prompt de Comando.</span><span class="sxs-lookup"><span data-stu-id="e30f7-106">If the current version of Visual Studio is installed on a computer that also has an earlier version of Visual Studio, you should not run VsDevCmd.bat and VSVARS32.BAT from different versions in the same Command Prompt window.</span></span> <span data-ttu-id="e30f7-107">Em vez disso, você deve executar o comando para cada versão em sua própria janela.</span><span class="sxs-lookup"><span data-stu-id="e30f7-107">Instead, you should run the command for each version in its own window.</span></span>

### <a name="to-run-vsdevcmdbat"></a><span data-ttu-id="e30f7-108">Para executar o VsDevCmd.BAT</span><span class="sxs-lookup"><span data-stu-id="e30f7-108">To run VsDevCmd.BAT</span></span>

1. <span data-ttu-id="e30f7-109">A partir do menu **Iniciar,** abra o **Prompt de comando do desenvolvedor para VS 2019**.</span><span class="sxs-lookup"><span data-stu-id="e30f7-109">From the **Start** menu, open the **Developer Command Prompt for VS 2019**.</span></span>  <span data-ttu-id="e30f7-110">Está na pasta **Visual Studio 2019.**</span><span class="sxs-lookup"><span data-stu-id="e30f7-110">It's in the **Visual Studio 2019** folder.</span></span>

2. <span data-ttu-id="e30f7-111">Alterar para o \Arquivos do\\Programa\Microsoft Visual Studio*Versão*\\*oferecendo*\Common7\Tools ou\\\Arquivos de programa (x86)\Microsoft Visual Studio*Versão*\\*oferecendo*\Common7\Tools subdiretório de sua instalação.</span><span class="sxs-lookup"><span data-stu-id="e30f7-111">Change to the \Program Files\Microsoft Visual Studio\\*Version*\\*Offering*\Common7\Tools or \Program Files (x86)\Microsoft Visual Studio\\*Version*\\*Offering*\Common7\Tools subdirectory of your installation.</span></span>  <span data-ttu-id="e30f7-112">(*Versão* é *2019* para a versão atual.</span><span class="sxs-lookup"><span data-stu-id="e30f7-112">(*Version* is *2019* for the current version.</span></span> <span data-ttu-id="e30f7-113">*Oferta* é uma entre *Enterprise*, *Professional* ou *Community*).</span><span class="sxs-lookup"><span data-stu-id="e30f7-113">*Offering* is one of *Enterprise*, *Professional* or *Community*.)</span></span>

3. <span data-ttu-id="e30f7-114">Execute o VsDevCmd.bat digitando **VsDevCmd**.</span><span class="sxs-lookup"><span data-stu-id="e30f7-114">Run VsDevCmd.bat by typing **VsDevCmd**.</span></span>

    > [!CAUTION]
    > <span data-ttu-id="e30f7-115">O VsDevCmd.bat pode variar de um computador para outro.</span><span class="sxs-lookup"><span data-stu-id="e30f7-115">VsDevCmd.bat can vary from computer to computer.</span></span> <span data-ttu-id="e30f7-116">Não substitua um arquivo VsDevCmd.bat não encontrado ou danificado por um VsDevCmd.bat de outro computador.</span><span class="sxs-lookup"><span data-stu-id="e30f7-116">Do not replace a missing or damaged VsDevCmd.bat file with a VsDevCmd.bat from another computer.</span></span> <span data-ttu-id="e30f7-117">Em vez disso, execute novamente a instalação para substituir o arquivo não encontrado.</span><span class="sxs-lookup"><span data-stu-id="e30f7-117">Instead, rerun setup to replace the missing file.</span></span>

### <a name="available-options-for-vsdevcmdbat"></a><span data-ttu-id="e30f7-118">Opções disponíveis para o VsDevCmd.BAT</span><span class="sxs-lookup"><span data-stu-id="e30f7-118">Available options for VsDevCmd.BAT</span></span>

<span data-ttu-id="e30f7-119">Para ver as opções disponíveis para VsDevCmd.BAT, execute o comando com a opção `-help`:</span><span class="sxs-lookup"><span data-stu-id="e30f7-119">To see the available options for VsDevCmd.BAT, run the command with the `-help` option:</span></span>

```console
VsDevCmd.bat -help
```

## <a name="see-also"></a><span data-ttu-id="e30f7-120">Confira também</span><span class="sxs-lookup"><span data-stu-id="e30f7-120">See also</span></span>

- [<span data-ttu-id="e30f7-121">Build pela linha de comando com csc.exe</span><span class="sxs-lookup"><span data-stu-id="e30f7-121">Command-line Building With csc.exe</span></span>](./command-line-building-with-csc-exe.md)
