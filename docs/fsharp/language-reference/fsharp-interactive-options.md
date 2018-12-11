---
title: Opções do F# Interativo
description: Saiba mais sobre as opções de linha de comando com suporte pelo F# fsi.exe interativos.
ms.date: 05/16/2016
ms.openlocfilehash: cca1ef6671878acb1b837d6590139d5de7b7167d
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53128148"
---
# <a name="f-interactive-options"></a>Opções do F# Interativo

> [!NOTE]
> Atualmente, este artigo descreve somente a experiência para Windows.  Ele será reescrito.

Este tópico descreve as opções de linha de comando com suporte pelo F# interativo `fsi.exe`. F#Interativo aceita muitas das mesmas opções de linha de comando como o F# compilador, mas também aceita algumas opções adicionais.

## <a name="using-f-interactive-for-scripting"></a>Usando o F# interativo para execução de scripts
F#Interativo, `fsi.exe`, pode ser iniciado interativamente ou pode ser iniciado da linha de comando para executar um script. A sintaxe de linha de comando é

```
> fsi.exe [options] [ script-file [arguments] ]
```

A extensão de arquivo para F# arquivos de script é `.fsx`.

## <a name="table-of-f-interactive-options"></a>Tabela de F# opções interativas
A tabela a seguir resume as opções com suporte pelo F# interativo. Você pode definir essas opções na linha de comando ou por meio do IDE do Visual Studio. Para definir essas opções no IDE do Visual Studio, abra o **ferramentas** menu, selecione **opções...** , em seguida, expanda o  **F# ferramentas** nó e selecione  **F# interativo**.

Onde as listas aparecem em F# argumentos de opção interativa, elementos de lista são separados por ponto e vírgula (`;`).

|Opção|Descrição|
|------|-----------|
|**--**|Usado para instruir o F# interativo para manipular argumentos restantes como argumentos de linha de comando para o F# programa ou script, que pode ser acessado no código usando a lista **CommandLineArgs**.|
|**--checked**[**+**&#124;**-**]|Mesmo que o **fsc.exe** opção de compilador. Para obter mais informações, consulte [Opções do compilador](compiler-options.md).|
|**-codepage:&lt;int&gt;**|Mesmo que o **fsc.exe** opção de compilador. Para obter mais informações, consulte [Opções do compilador](compiler-options.md).|
|**--consolecolors**[**+**&#124;**-**]|Saídas de aviso e mensagens de erro na cor.|
|**--crossoptimize**[**+**&#124;**-**]|Habilitar ou desabilitar as otimizações de módulo cruzado.|
|**--debug**[**+**&#124;**-**]<br /><br />**--debug:**[**full**&#124;**pdbonly**&#124;**portable**&#124;**embedded**]<br /><br />**-g**[**+**&#124;**-**]<br /><br />**-g**[**completa**&#124;**pdbonly**&#124;**portátil**&#124;**embedded**]|Mesmo que o **fsc.exe** opção de compilador. Para obter mais informações, consulte [Opções do compilador](compiler-options.md).|
|**--define:&lt;string&gt;**|Mesmo que o **fsc.exe** opção de compilador. Para obter mais informações, consulte [Opções do compilador](compiler-options.md).|
|**--deterministic**[**+**&#124;**-**]|Produz um assembly determinístico (incluindo o GUID da versão do módulo e o carimbo de hora).|
|**--exec**|Instrui o F# interativo a sair após o carregamento de arquivos ou executar o arquivo de script fornecido na linha de comando.|
|**--fullpaths**|Mesmo que o **fsc.exe** opção de compilador. Para obter mais informações, consulte [Opções do compilador](compiler-options.md).|
|**--gui**[**+**&#124;**-**]|Habilita ou desabilita o loop de eventos do Windows Forms. O padrão é habilitado.|
|**--help**<br /><br />**-?**|Usado para exibir a sintaxe de linha de comando e uma breve descrição de cada opção.|
|**--lib:&lt;folder-list&gt;**<br /><br />**-I:&lt;lista de pastas&gt;**|Mesmo que o **fsc.exe** opção de compilador. Para obter mais informações, consulte [Opções do compilador](compiler-options.md).|
|**--load:&lt;filename&gt;**|Compila o código-fonte fornecido na inicialização e carrega compilado F# constrói para a sessão. Se a fonte de destino contiver diretivas de script como **#use** ou **#load**, em seguida, você deve usar **– use** ou **#use** em vez de **– carregar** ou **#load**.|
|**--mlcompatibility**|Mesmo que o **fsc.exe** opção de compilador. Para obter mais informações, consulte [Opções do compilador](compiler-options.md).|
|**--noframework**|Mesmo que o **fsc.exe** opção de compilador. Para obter mais informações, consulte [opções do compilador](compiler-options.md)|
|**--nologo**|Mesmo que o **fsc.exe** opção de compilador. Para obter mais informações, consulte [Opções do compilador](compiler-options.md).|
|**--nowarn:&lt;warning-list&gt;**|Mesmo que o **fsc.exe** opção de compilador. Para obter mais informações, consulte [Opções do compilador](compiler-options.md).|
|**--optimize**[**+**&#124;**-**]|Mesmo que o **fsc.exe** opção de compilador. Para obter mais informações, consulte [Opções do compilador](compiler-options.md).|
|**-preferreduilang:&lt;lang&gt;**| Especifica o nome de cultura do idioma preferencial de saída (por exemplo, es-ES, ja-JP). |
|**--quiet**|Suprimir F# saída de interativo para o **stdout** stream.|
|**--quotations-debug**|Especifica que informações de depuração adicionais devem ser emitidas para expressões que são derivadas de F# literais de aspas duplas e definições refletidas. As informações de depuração são adicionadas para os atributos personalizados de um F# nó de árvore de expressão. Ver [citações de código](code-quotations.md) e [expr. customattributes](https://msdn.microsoft.com/library/eb89943f-5f5b-474e-b125-030ca412edb3).|
|**--readline**[**+**&#124;**-**]|Habilitar ou desabilitar o preenchimento com tab no modo interativo.|
|**--reference:&lt;filename&gt;**<br /><br />**-r:&lt;filename&gt;**|Mesmo que o **fsc.exe** opção de compilador. Para obter mais informações, consulte [Opções do compilador](compiler-options.md).|
|**--shadowcopyreferences**[**+**&#124;**-**]|Impede que as referências do que está sendo bloqueado pelo F# processo interativo.|
|**--simpleresolution**|Resolve referências de assembly usando regras baseadas em diretório, em vez da resolução do MSBuild.|
|**--tailcalls**[**+**&#124;**-**]|Habilitar ou desabilitar o uso da instrução do IL final, que faz com que o quadro de pilha seja reutilizado para funções recursivas finais. Essa opção é habilitada por padrão.|
|**--targetprofile:&lt;string&gt;**|Especifica o perfil de framework de destino desse assembly. Valores válidos são mscorlib, netcore ou netstandard.  O padrão é mscorlib.|
|**--use:&lt;filename&gt;**|Diz ao intérprete para usar o arquivo fornecido na inicialização como entrada inicial.|
|**--utf8output**|Mesmo que a opção do compilador fsc.exe. Para obter mais informações, consulte [Opções do compilador](compiler-options.md).|
|**--warn:&lt;warning-level&gt;**|Mesmo que o **fsc.exe** opção de compilador. Para obter mais informações, consulte [Opções do compilador](compiler-options.md).|
|**--warnaserror**[**+**&#124;**-**]|Mesmo que o **fsc.exe** opção de compilador. Para obter mais informações, consulte [Opções do compilador](compiler-options.md).|
|**--warnaserror**[**+**&#124;**-**]:**&lt;int-list&gt;**|Mesmo que o **fsc.exe** opção de compilador. Para obter mais informações, consulte [Opções do compilador](compiler-options.md).|

## <a name="related-topics"></a>Tópicos relacionados

|Título|Descrição|
|-----|-----------|
|[Opções do Compilador](compiler-options.md)|Descreve as opções de linha de comando disponíveis para o F# compilador, **fsc.exe**.|
