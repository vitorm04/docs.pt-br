---
title: "Como: configurar variáveis de ambiente para a linha de comando do Visual Studio"
ms.date: 09/29/2017
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
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
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 298006629bedf33e4d2521a88c010fcce824585c
ms.sourcegitcommit: 96cc82cac4650adfb65ba351506d8a8fbcd17b5c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/19/2018
---
# <a name="how-to-set-environment-variables-for-the-visual-studio-command-line"></a>Como: configurar variáveis de ambiente para a linha de comando do Visual Studio

O arquivo VsDevCmd.bat define as variáveis de ambiente adequadas para habilitar builds de linha de comando. Para obter mais informações sobre VsDevCmd.bat, consulte [Artigo da base de dados de conhecimento Q248802](https://support.microsoft.com/help/248802/you-receive-the-out-of-environment-space-error-message-when-you-execut).  

> [!NOTE]
> O arquivo VsDevCmd.bat é um novo arquivo fornecido com o Visual Studio 2017. O Visual Studio 2015 e versões anteriores usavam o VSVARS32.bat para a mesma finalidade. Esse arquivo era armazenado em \Arquivos de Programas\Microsoft Visual Studio\\*Versão*\Common7\Tools ou Arquivos de Programas (x86)\Microsoft Visual Studio\\*Versão*\Common7\Tools.
  
Se a versão atual do Visual Studio estiver instalada em um computador que também tiver uma versão anterior do Visual Studio, você não deverá executar VsDevCmd.bat e VSVARS32.bat de versões diferentes na mesma janela do Prompt de Comando. Em vez disso, você deve executar o comando para cada versão em sua própria janela.
  
### <a name="to-run-vsdevcmdbat"></a>Para executar o VsDevCmd.BAT  
  
1.  No menu **Iniciar**, abra o **Prompt de Comando do Desenvolvedor para VS 2017**.  Ele está na pasta do **Visual Studio 2017**.
  
2.  Altere para o subdiretório \Arquivos de Programas\Microsoft Visual Studio\\*Versão*\\*Oferta*\Common7\Tools ou \Arquivos de Programas (x86)\Microsoft Visual Studio\\*Versão*\\*Oferta*\Common7\Tools da sua instalação.  (a *Versão* é *2017* para a versão atual. *Oferta* é uma entre *Enterprise*, *Professional* ou *Community*).
  
3.  Execute o VsDevCmd.bat digitando **VsDevCmd**.  
  
    > [!CAUTION]
    >  O VsDevCmd.bat pode variar de um computador para outro. Não substitua um arquivo VsDevCmd.bat não encontrado ou danificado por um VsDevCmd.bat de outro computador. Em vez disso, execute novamente a instalação para substituir o arquivo não encontrado.  
  
## <a name="see-also"></a>Consulte também  
 [Build pela linha de comando com csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)
