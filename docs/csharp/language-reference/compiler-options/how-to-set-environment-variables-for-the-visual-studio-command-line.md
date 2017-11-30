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
# <a name="how-to-set-environment-variables-for-the-visual-studio-command-line"></a>Como: configurar variáveis de ambiente para a linha de comando do Visual Studio

O arquivo VsDevCmd.bat define as variáveis de ambiente apropriadas para habilitar as compilações de linha de comando. Para obter mais informações sobre VsDevCmd.bat, consulte [artigo da Base de dados de Conhecimento Q248802](http://go.microsoft.com/fwlink/?LinkId=225042).  

> [!NOTE]
> O arquivo VsDevCmd.bat é um novo arquivo fornecido com o Visual Studio de 2017. Visual Studio 2015 e versões anteriores usados VSVARS32.bat para a mesma finalidade. Esse arquivo foi armazenado no Visual Studio de \Program Files\Microsoft\\*versão*\Common7\Tools ou (x86) os arquivos de programas \Microsoft Visual Studio\\*versão*\Common7\Tools.
  
Se a versão atual do Visual Studio está instalada em um computador que também tem uma versão anterior do Visual Studio, você não deve executar VsDevCmd.bat e VSVARS32. BAT de versões diferentes na mesma janela do Prompt de comando. Em vez disso, você deve executar o comando para cada versão em sua própria janela.
  
### <a name="to-run-vsdevcmdbat"></a>Para executar VsDevCmd.BAT  
  
1.  Do **iniciar** menu, abrir o **Prompt de comando do desenvolvedor para VS 2017**.  Ele está no **2017 do Visual Studio** pasta.
  
2.  Altere para o Visual Studio \Program Files\Microsoft\\*versão*\\*oferta*\Common7\Tools ou \Program arquivos (x86) \Microsoft Visual Studio\\ *Versão*\\*oferta*\Common7\Tools subdiretório de sua instalação.  (*Versão* é *2017* para a versão atual. *Oferta* é um dos *Enterprise*, *Professional* ou *Community*.)
  
3.  Execute VsDevCmd.bat digitando **VsDevCmd**.  
  
    > [!CAUTION]
    >  VsDevCmd.bat pode variar de um computador para outro. Não substitua um arquivo de VsDevCmd.bat ausente ou danificado com um VsDevCmd.bat de outro computador. Em vez disso, execute novamente a instalação para substituir o arquivo não encontrado.  
  
## <a name="see-also"></a>Consulte também  
 [Build pela linha de comando com csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)
