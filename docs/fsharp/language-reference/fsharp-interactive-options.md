---
title: Opções do F# Interativo
description: 'Saiba mais sobre as opções de linha de comando com suporte por F # interativo, fsi.exe.'
ms.date: 05/16/2016
ms.openlocfilehash: a461dd0eeff2de3d15e557ba37138fbd62ca43ba
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="f-interactive-options"></a>Opções do F# Interativo

> [!NOTE]
Atualmente, este artigo descreve somente a experiência para Windows.  Ele será reescrito.

Este tópico descreve as opções de linha de comando com suporte por F # interativo, `fsi.exe`. F # interativo aceita muitas das mesmas opções de linha de comando de compilador F #, mas também aceita algumas opções adicionais.

## <a name="using-f-interactive-for-scripting"></a>Usando F # interativo para scripts
F # interativo, `fsi.exe`, pode ser iniciado de forma interativa ou pode ser iniciado na linha de comando para executar um script. É a sintaxe de linha de comando

```
> fsi.exe [options] [ script-file [arguments] ]
```

A extensão de arquivo para arquivos de script F # é `.fsx`.

## <a name="table-of-f-interactive-options"></a>Opções de F # interativo
A tabela a seguir resume as opções de suporte por F # interativo. Você pode definir essas opções na linha de comando ou por meio do IDE do Visual Studio. Para definir essas opções no IDE do Visual Studio, abra o **ferramentas** menu, selecione **opções...** , em seguida, expanda o **ferramentas F #** nó e selecione **F # interativo**.

Onde listas aparecem em argumentos de opção F # interativo, os elementos da lista são separados por ponto e vírgula (`;`).

|Opção|Descrição|
|------|-----------|
|**--**|Usado para instruir o F # interativo para tratar argumentos restantes como argumentos de linha de comando para o F # programa ou script, o que você pode acessar no código usando a lista **FSI. CommandLineArgs**.|
|**--checked**[**+**&#124;**-**]|Mesmo que o **fsc.exe** opção de compilador. Para obter mais informações, consulte [Opções do compilador](compiler-options.md).|
|**a página de código –:&lt;int&gt;**|Mesmo que o **fsc.exe** opção de compilador. Para obter mais informações, consulte [Opções do compilador](compiler-options.md).|
|**--consolecolors**[**+**&#124;**-**]|Saídas de aviso e mensagens de erro em cores.|
|**--crossoptimize**[**+**&#124;**-**]|Habilitar ou desabilitar as otimizações de módulo cruzado.|
|**--debug**[**+**&#124;**-**]<br /><br />**--debug:**[**full**&#124;**pdbonly**&#124;**portable**&#124;**embedded**]<br /><br />**-g**[**+**&#124;**-**]<br /><br />**-g**[**completo**&#124;**pdbonly**&#124;**portátil**&#124;**inserido**]|Mesmo que o **fsc.exe** opção de compilador. Para obter mais informações, consulte [Opções do compilador](compiler-options.md).|
|**--define:&lt;string&gt;**|Mesmo que o **fsc.exe** opção de compilador. Para obter mais informações, consulte [Opções do compilador](compiler-options.md).|
|**--deterministic**[**+**&#124;**-**]|Produz um assembly determinístico (incluindo o GUID da versão do módulo e o carimbo de hora).|
|**--exec**|Instrui o F # interativo seja encerrado depois de carregar os arquivos ou executar o arquivo de script fornecido na linha de comando.|
|**--fullpaths**|Mesmo que o **fsc.exe** opção de compilador. Para obter mais informações, consulte [Opções do compilador](compiler-options.md).|
|**--gui**[**+**&#124;**-**]|Habilita ou desabilita o loop de eventos do Windows Forms. O padrão é habilitado.|
|**--help**<br /><br />**-?**|Usado para exibir a sintaxe de linha de comando e uma breve descrição de cada opção.|
|**--lib:&lt;folder-list&gt;**<br /><br />**-I:&lt;lista de pastas&gt;**|Mesmo que o **fsc.exe** opção de compilador. Para obter mais informações, consulte [Opções do compilador](compiler-options.md).|
|**--load:&lt;filename&gt;**|Compila o código de origem especificado na inicialização e carrega as construções de linguagem F # compiladas para a sessão. Se a fonte de destino contém as diretivas de script como **#use** ou **#load**, em seguida, você deve usar **– use** ou **#use** em vez de **– carregar** ou **#load**.|
|**--mlcompatibility**|Mesmo que o **fsc.exe** opção de compilador. Para obter mais informações, consulte [Opções do compilador](compiler-options.md).|
|**--noframework**|Mesmo que o **fsc.exe** opção de compilador. Para obter mais informações, consulte [opções do compilador](compiler-options.md)|
|**--nologo**|Mesmo que o **fsc.exe** opção de compilador. Para obter mais informações, consulte [Opções do compilador](compiler-options.md).|
|**--nowarn:&lt;warning-list&gt;**|Mesmo que o **fsc.exe** opção de compilador. Para obter mais informações, consulte [Opções do compilador](compiler-options.md).|
|**--optimize**[**+**&#124;**-**]|Mesmo que o **fsc.exe** opção de compilador. Para obter mais informações, consulte [Opções do compilador](compiler-options.md).|
|**-preferreduilang:&lt;lang&gt;**| Especifica o nome de cultura de idioma de saída preferencial (por exemplo, es-ES, ja-JP). |
|**--quiet**|Suprimir saída da F # interativo para o **stdout** fluxo.|
|**--quotations-debug**|Especifica que as informações de depuração extra devem ser emitida para expressões que são derivadas de literais de cotação F # e refletem definições. As informações de depuração são adicionadas para os atributos personalizados de um nó de árvore de expressão F #. Consulte [citações de código](code-quotations.md) e [customattributes](https://msdn.microsoft.com/library/eb89943f-5f5b-474e-b125-030ca412edb3).|
|**--readline**[**+**&#124;**-**]|Habilitar ou desabilitar o preenchimento com tab no modo interativo.|
|**--reference:&lt;filename&gt;**<br /><br />**-r:&lt;filename&gt;**|Mesmo que o **fsc.exe** opção de compilador. Para obter mais informações, consulte [Opções do compilador](compiler-options.md).|
|**--shadowcopyreferences**[**+**&#124;**-**]|Impede que as referências sejam bloqueadas pelo processo de F # interativo.|
|**--simpleresolution**|Resolve referências de assembly usando regras baseadas em diretório, em vez da resolução do MSBuild.|
|**--tailcalls**[**+**&#124;**-**]|Habilitar ou desabilitar o uso da instrução IL final, que faz com que o quadro de pilha ser reutilizado para funções de recursivas final. Essa opção é habilitada por padrão.|
|**--targetprofile:&lt;string&gt;**|Especifica o perfil de estrutura de destino deste assembly. Os valores válidos são mscorlib, netcore ou identificadores de netstandard.  O padrão é mscorlib.|
|**--use:&lt;filename&gt;**|Informa o interpretador para usar o arquivo fornecido na inicialização como entrada inicial.|
|**--utf8output**|Mesmo que a opção de compilador fsc.exe. Para obter mais informações, consulte [Opções do compilador](compiler-options.md).|
|**--warn:&lt;warning-level&gt;**|Mesmo que o **fsc.exe** opção de compilador. Para obter mais informações, consulte [Opções do compilador](compiler-options.md).|
|**--warnaserror**[**+**&#124;**-**]|Mesmo que o **fsc.exe** opção de compilador. Para obter mais informações, consulte [Opções do compilador](compiler-options.md).|
|**--warnaserror**[**+**&#124;**-**]:**&lt;int-list&gt;**|Mesmo que o **fsc.exe** opção de compilador. Para obter mais informações, consulte [Opções do compilador](compiler-options.md).|

## <a name="related-topics"></a>Tópicos relacionados

|Título|Descrição|
|-----|-----------|
|[Opções do Compilador](compiler-options.md)|Descreve as opções de linha de comando disponíveis para o compilador F #, **fsc.exe**.|
