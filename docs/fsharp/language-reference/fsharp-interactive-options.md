---
title: Opções do F# Interativo
description: Saiba mais sobre as opções de linha de comando F# suportadas por Interactive, FSI. exe.
ms.date: 05/16/2016
ms.openlocfilehash: e4ce0f3f76a7be803942e4b403e5fa6543a09e54
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73425311"
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
|**--verificado**[ **+** &#124; **-** ]|O mesmo que a opção de compilador **FSC. exe** . Para obter mais informações, consulte [Opções do compilador](compiler-options.md).|
|**--CodePage:&lt;int&gt;**|O mesmo que a opção de compilador **FSC. exe** . Para obter mais informações, consulte [Opções do compilador](compiler-options.md).|
|**--consolecolors**[ **+** &#124; **-** ]|Gera mensagens de aviso e de erro em cores.|
|**--crossoptimize**[ **+** &#124; **-** ]|Habilitar ou desabilitar otimizações de módulo cruzado.|
|**--debug**[ **+** &#124; **-** ]<br /><br />**--debug:** [**Full**&#124;**pdbonly**&#124;**portátil**&#124;**Embedded**]<br /><br />**-g**[ **+** &#124; **-** ]<br /><br />**-g:** [**Full**&#124;**pdbonly**&#124;**portátil**&#124;**Embedded**]|O mesmo que a opção de compilador **FSC. exe** . Para obter mais informações, consulte [Opções do compilador](compiler-options.md).|
|**--definir:&lt;cadeia de caracteres&gt;**|O mesmo que a opção de compilador **FSC. exe** . Para obter mais informações, consulte [Opções do compilador](compiler-options.md).|
|**--determinístico**[ **+** &#124; **-** ]|Produz um assembly determinístico (incluindo o GUID de versão do módulo e o carimbo de data/hora).|
|**--exec**|Instrui o F# interativo a sair depois de carregar os arquivos ou executar o arquivo de script fornecido na linha de comando.|
|**--fullpaths**|O mesmo que a opção de compilador **FSC. exe** . Para obter mais informações, consulte [Opções do compilador](compiler-options.md).|
|**--GUI**[ **+** &#124; **-** ]|Habilita ou desabilita o loop de evento Windows Forms. O padrão é habilitado.|
|**--ajuda**<br /><br />**-?**|Usado para exibir a sintaxe de linha de comando e uma breve descrição de cada opção.|
|**--lib:&lt;a lista de pastas&gt;**<br /><br />**-I: lista de pastas&lt;&gt;**|O mesmo que a opção de compilador **FSC. exe** . Para obter mais informações, consulte [Opções do compilador](compiler-options.md).|
|**--carregar:&lt;nome do arquivo&gt;**|Compila o código-fonte fornecido na inicialização e carrega as construções compiladas F# na sessão. Se a origem de destino contiver diretivas de script, como **#use** ou **#load**, você deverá usar **--use** ou **#use** em vez de **--Load** ou **#load**.|
|**--mlcompatibility**|O mesmo que a opção de compilador **FSC. exe** . Para obter mais informações, consulte [Opções do compilador](compiler-options.md).|
|**--noframework**|O mesmo que a opção de compilador **FSC. exe** . Para obter mais informações, consulte [Opções do compilador](compiler-options.md)|
|**--nologo**|O mesmo que a opção de compilador **FSC. exe** . Para obter mais informações, consulte [Opções do compilador](compiler-options.md).|
|**--nowarn: lista de avisos de&lt;&gt;**|O mesmo que a opção de compilador **FSC. exe** . Para obter mais informações, consulte [Opções do compilador](compiler-options.md).|
|**--Optimize**[ **+** &#124; **-** ]|O mesmo que a opção de compilador **FSC. exe** . Para obter mais informações, consulte [Opções do compilador](compiler-options.md).|
|**--preferreduilang:&lt;Lang&gt;**| Especifica o nome de cultura do idioma de saída preferencial (por exemplo, es-ES, ja-JP). |
|**--Quiet**|Suprimir F# a saída interativa para o fluxo **stdout** .|
|**--Cotações-depurar**|Especifica que informações adicionais de depuração devem ser emitidas para expressões derivadas de literais de F# cotação e definições refletidas. As informações de depuração são adicionadas aos atributos personalizados de F# um nó de árvore de expressão. Consulte [Incitaçãos de código](code-quotations.md) e [expr. CustomAttributes](https://msdn.microsoft.com/library/eb89943f-5f5b-474e-b125-030ca412edb3).|
|**--ReadLine**[ **+** &#124; **-** ]|Habilitar ou desabilitar o preenchimento com Tab no modo interativo.|
|**--referência:&lt;nome de arquivo&gt;**<br /><br />**-r:&lt;filename&gt;**|O mesmo que a opção de compilador **FSC. exe** . Para obter mais informações, consulte [Opções do compilador](compiler-options.md).|
|**--shadowcopyreferences**[ **+** &#124; **-** ]|Impede que as F# referências sejam bloqueadas pelo processo interativo.|
|**--simpleresolution**|Resolve referências de assembly usando regras baseadas em diretório em vez da resolução do MSBuild.|
|**--tailcalls**[ **+** &#124; **-** ]|Habilitar ou desabilitar o uso da instrução de IL final, que faz com que o quadro de pilha seja reutilizado para funções recursivas da parte final. Essa opção é habilitada por padrão.|
|**--targetprofile:&lt;cadeia de caracteres&gt;**|Especifica o perfil da estrutura de destino deste assembly. Os valores válidos são mscorlib, NetCore ou netstandard.  O padrão é mscorlib.|
|**--Use:&lt;nome de arquivo&gt;**|Instrui o intérprete a usar o arquivo fornecido na inicialização como entrada inicial.|
|**--utf8output**|O mesmo que a opção de compilador FSC. exe. Para obter mais informações, consulte [Opções do compilador](compiler-options.md).|
|**--WARN:&lt;&gt; no nível de aviso**|O mesmo que a opção de compilador **FSC. exe** . Para obter mais informações, consulte [Opções do compilador](compiler-options.md).|
|**--warnaserror**[ **+** &#124; **-** ]|O mesmo que a opção de compilador **FSC. exe** . Para obter mais informações, consulte [Opções do compilador](compiler-options.md).|
|**--warnaserror**[ **+** &#124; **-** ]: **&lt;int-List&gt;**|O mesmo que a opção de compilador **FSC. exe** . Para obter mais informações, consulte [Opções do compilador](compiler-options.md).|

## <a name="related-topics"></a>Tópicos relacionados

|Título|Descrição|
|-----|-----------|
|[Opções do Compilador](compiler-options.md)|Descreve as opções de linha de comando F# disponíveis para o compilador, **FSC. exe**.|
