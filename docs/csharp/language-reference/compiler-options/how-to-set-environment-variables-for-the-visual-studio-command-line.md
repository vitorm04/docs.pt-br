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
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75342360"
---
# <a name="how-to-set-environment-variables-for-the-visual-studio-command-line"></a>Como configurar variáveis de ambiente para a linha de comando do Visual Studio

O arquivo VsDevCmd.bat define as variáveis de ambiente adequadas para habilitar builds de linha de comando.

> [!NOTE]
> O Visual Studio 2015 e versões anteriores usaram VSVARS32. bat, não VsDevCmd. bat para a mesma finalidade. Esse arquivo era armazenado em \Arquivos de Programas\Microsoft Visual Studio\\*Versão*\Common7\Tools ou Arquivos de Programas (x86)\Microsoft Visual Studio\\*Versão*\Common7\Tools.

Se a versão atual do Visual Studio estiver instalada em um computador que também tiver uma versão anterior do Visual Studio, você não deverá executar VsDevCmd.bat e VSVARS32.bat de versões diferentes na mesma janela do Prompt de Comando. Em vez disso, você deve executar o comando para cada versão em sua própria janela.

### <a name="to-run-vsdevcmdbat"></a>Para executar o VsDevCmd.BAT

1. No menu **Iniciar** , abra o **Prompt de Comando do Desenvolvedor para vs 2019**.  Está na pasta do **Visual Studio 2019** .

2. Altere para o subdiretório \Arquivos de Programas\Microsoft Visual Studio\\*Versão*\\*Oferta*\Common7\Tools ou \Arquivos de Programas (x86)\Microsoft Visual Studio\\*Versão*\\*Oferta*\Common7\Tools da sua instalação.  (A*versão* é *2019* para a versão atual. *Oferta* é uma entre *Enterprise*, *Professional* ou *Community*).

3. Execute o VsDevCmd.bat digitando **VsDevCmd**.

    > [!CAUTION]
    > O VsDevCmd.bat pode variar de um computador para outro. Não substitua um arquivo VsDevCmd.bat não encontrado ou danificado por um VsDevCmd.bat de outro computador. Em vez disso, execute novamente a instalação para substituir o arquivo não encontrado.

### <a name="available-options-for-vsdevcmdbat"></a>Opções disponíveis para o VsDevCmd.BAT

Para ver as opções disponíveis para VsDevCmd.BAT, execute o comando com a opção `-help`:

```console
VsDevCmd.bat -help
```

## <a name="see-also"></a>Veja também

- [Build pela linha de comando com csc.exe](./command-line-building-with-csc-exe.md)
