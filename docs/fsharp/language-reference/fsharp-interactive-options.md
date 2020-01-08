---
title: Opções interativas
description: Saiba mais sobre as opções de linha de comando F# suportadas por Interactive, FSI. exe.
ms.date: 05/16/2016
ms.openlocfilehash: cceb8fb50434f3525ebb2ede16e84720d10d320c
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75348231"
---
# <a name="f-interactive-options"></a>Opções do F# Interativo

> [!NOTE]
> Atualmente, este artigo descreve somente a experiência para Windows.  Ele será reescrito.

Este tópico descreve as opções de linha de comando com F# suporte do Interactive, `fsi.exe`. F#O Interactive aceita muitas das mesmas opções de linha de comando F# que o compilador, mas também aceita algumas opções adicionais.

## <a name="using-f-interactive-for-scripting"></a>Usando F# o Interactive para scripts

F#Interativo, `fsi.exe`, pode ser iniciado interativamente ou pode ser iniciado na linha de comando para executar um script. A sintaxe da linha de comando é

```console
> fsi.exe [options] [ script-file [arguments] ]
```

A extensão de arquivo F# para arquivos de script é `.fsx`.

## <a name="table-of-f-interactive-options"></a>Tabela de F# opções interativas

A tabela a seguir resume as opções com suporte F# do Interactive. Você pode definir essas opções na linha de comando ou por meio do IDE do Visual Studio. Para definir essas opções no IDE do Visual Studio, abra o menu **ferramentas** , selecione **opções...** , expanda o  **F# nó ferramentas** e selecione  **F# interativo**.

Onde as listas aparecem F# nos argumentos de opção interativa, os elementos de lista são separados por ponto e vírgula (`;`).

|Opção|Descrição|
|------|-----------|
|**--**|Usado para instruir F# interativamente a tratar os argumentos restantes como argumentos F# de linha de comando para o programa ou script, que você pode acessar no código usando a lista **FSI. CommandLineArgs**.|
|**--checked**[ **+** &#124; **-** ]|O mesmo que a opção de compilador **FSC. exe** . Para obter mais informações, consulte [Opções do compilador](compiler-options.md).|
|**--codepage:&lt;int&gt;**|O mesmo que a opção de compilador **FSC. exe** . Para obter mais informações, consulte [Opções do compilador](compiler-options.md).|
|**--consolecolors**[ **+** &#124; **-** ]|Gera mensagens de aviso e de erro em cores.|
|**--crossoptimize**[ **+** &#124; **-** ]|Habilitar ou desabilitar otimizações de módulo cruzado.|
|**--debug**[ **+** &#124; **-** ]<br /><br />**--debug:** [**full**&#124;**pdbonly**&#124;**portable**&#124;**embedded**]<br /><br />**-g**[ **+** &#124; **-** ]<br /><br />**-g:** [**full**&#124;**pdbonly**&#124;**portable**&#124;**embedded**]|O mesmo que a opção de compilador **FSC. exe** . Para obter mais informações, consulte [Opções do compilador](compiler-options.md).|
|**--define:&lt;string&gt;**|O mesmo que a opção de compilador **FSC. exe** . Para obter mais informações, consulte [Opções do compilador](compiler-options.md).|
|**--deterministic**[ **+** &#124; **-** ]|Produz um assembly determinístico (incluindo o GUID de versão do módulo e o carimbo de data/hora).|
|**--exec**|Instrui o F# interativo a sair depois de carregar os arquivos ou executar o arquivo de script fornecido na linha de comando.|
|**--fullpaths**|O mesmo que a opção de compilador **FSC. exe** . Para obter mais informações, consulte [Opções do compilador](compiler-options.md).|
|**--gui**[ **+** &#124; **-** ]|Habilita ou desabilita o loop de evento Windows Forms. O padrão é habilitado.|
|**--help**<br /><br />**-?**|Usado para exibir a sintaxe de linha de comando e uma breve descrição de cada opção.|
|**--lib:&lt;folder-list&gt;**<br /><br />**-I:&lt;folder-list&gt;**|O mesmo que a opção de compilador **FSC. exe** . Para obter mais informações, consulte [Opções do compilador](compiler-options.md).|
|**--load:&lt;filename&gt;**|Compila o código-fonte fornecido na inicialização e carrega as construções compiladas F# na sessão. Se a origem de destino contiver diretivas de script, como **#use** ou **#load**, você deverá usar **--use** ou **#use** em vez de **--Load** ou **#load**.|
|**--mlcompatibility**|O mesmo que a opção de compilador **FSC. exe** . Para obter mais informações, consulte [Opções do compilador](compiler-options.md).|
|**--noframework**|O mesmo que a opção de compilador **FSC. exe** . Para obter mais informações, consulte [Opções do compilador](compiler-options.md)|
|**--nologo**|O mesmo que a opção de compilador **FSC. exe** . Para obter mais informações, consulte [Opções do compilador](compiler-options.md).|
|**--nowarn:&lt;warning-list&gt;**|O mesmo que a opção de compilador **FSC. exe** . Para obter mais informações, consulte [Opções do compilador](compiler-options.md).|
|**--optimize**[ **+** &#124; **-** ]|O mesmo que a opção de compilador **FSC. exe** . Para obter mais informações, consulte [Opções do compilador](compiler-options.md).|
|**--preferreduilang:&lt;lang&gt;**| Especifica o nome de cultura do idioma de saída preferencial (por exemplo, es-ES, ja-JP). |
|**--quiet**|Suprimir F# a saída interativa para o fluxo **stdout** .|
|**--quotations-debug**|Especifica que informações adicionais de depuração devem ser emitidas para expressões derivadas de literais de F# cotação e definições refletidas. As informações de depuração são adicionadas aos atributos personalizados de F# um nó de árvore de expressão. Consulte [Incitaçãos de código](code-quotations.md) e [expr. CustomAttributes](https://msdn.microsoft.com/library/eb89943f-5f5b-474e-b125-030ca412edb3).|
|**--readline**[ **+** &#124; **-** ]|Habilitar ou desabilitar o preenchimento com Tab no modo interativo.|
|**--reference:&lt;filename&gt;**<br /><br />**-r:&lt;filename&gt;**|O mesmo que a opção de compilador **FSC. exe** . Para obter mais informações, consulte [Opções do compilador](compiler-options.md).|
|**--shadowcopyreferences**[ **+** &#124; **-** ]|Impede que as F# referências sejam bloqueadas pelo processo interativo.|
|**--simpleresolution**|Resolve referências de assembly usando regras baseadas em diretório em vez da resolução do MSBuild.|
|**--tailcalls**[ **+** &#124; **-** ]|Habilitar ou desabilitar o uso da instrução de IL final, que faz com que o quadro de pilha seja reutilizado para funções recursivas da parte final. Essa opção é habilitada por padrão.|
|**--targetprofile:&lt;string&gt;**|Especifica o perfil da estrutura de destino deste assembly. Os valores válidos são mscorlib, NetCore ou netstandard.  O padrão é mscorlib.|
|**--use:&lt;filename&gt;**|Instrui o intérprete a usar o arquivo fornecido na inicialização como entrada inicial.|
|**--utf8output**|O mesmo que a opção de compilador FSC. exe. Para obter mais informações, consulte [Opções do compilador](compiler-options.md).|
|**--warn:&lt;warning-level&gt;**|O mesmo que a opção de compilador **FSC. exe** . Para obter mais informações, consulte [Opções do compilador](compiler-options.md).|
|**--warnaserror**[ **+** &#124; **-** ]|O mesmo que a opção de compilador **FSC. exe** . Para obter mais informações, consulte [Opções do compilador](compiler-options.md).|
|**--warnaserror**[ **+** &#124; **-** ]: **&lt;int-list&gt;**|O mesmo que a opção de compilador **FSC. exe** . Para obter mais informações, consulte [Opções do compilador](compiler-options.md).|

## <a name="related-topics"></a>Tópicos relacionados

|Cargo|Descrição|
|-----|-----------|
|[Opções do Compilador](compiler-options.md)|Descreve as opções de linha de comando F# disponíveis para o compilador, **FSC. exe**.|
