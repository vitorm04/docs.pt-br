---
title: Diretivas de compilador
description: Saiba mais sobre F# diretivas de pré-processador de linguagem, diretivas de compilação condicional, diretivas de linha e diretivas de compilador.
ms.date: 12/10/2018
ms.openlocfilehash: 2b62fb930a3b0c55103d6b0edbe20ae056ba86bd
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65645506"
---
# <a name="compiler-directives"></a>Diretivas de compilador

Este tópico descreve as diretivas de processador e diretivas de compilador.

## <a name="preprocessor-directives"></a>Diretivas de pré-processador

Uma diretiva de pré-processador é prefixada com o símbolo # e aparece em uma linha por si só. Ele é interpretado pelo pré-processador, que é executado antes do próprio compilador.

A tabela a seguir lista as diretivas de pré-processador que estão disponíveis no F#.

|Diretiva|Descrição|
|---------|-----------|
|`#if` *symbol*|Dá suporte à compilação condicional. Código na seção após o `#if` está incluído se o *símbolo* é definido. O símbolo também pode ser negado com `!`.|
|`#else`|Dá suporte à compilação condicional. Marca uma seção de código para incluir se o símbolo usado com o anterior `#if` não está definido.|
|`#endif`|Dá suporte à compilação condicional. Marca o final de uma seção condicional do código.|
|`#`[line] *int*,<br/>`#`[line] *int* *string*,<br/>`#`[line] *int* *verbatim-string*|Indica o nome original da fonte código linha e o arquivo, para depuração. Esse recurso é fornecido para as ferramentas que geram F# código-fonte.|
|`#nowarn` *warningcode*|Desabilita um aviso do compilador ou avisos. Para desabilitar um aviso, localize seu número de saída do compilador e incluí-lo entre aspas. Omita o prefixo "FS". Para desabilitar vários números de aviso na mesma linha, incluir cada número entre aspas e separe cada cadeia de caracteres por um espaço. Por exemplo:

`#nowarn "9" "40"`

O efeito de desabilitar um aviso se aplica a todo o arquivo, incluindo partes do arquivo que precedem a diretiva. |

## <a name="conditional-compilation-directives"></a>Diretivas de compilação condicional

Código que é desativado por um dessas diretivas aparece esmaecido no Editor de código do Visual Studio.

> [!NOTE]
> O comportamento das diretivas de compilação condicional não é o mesmo que ele esteja em outras linguagens. Por exemplo, é possível usar expressões Boolianas que envolvem símbolos, e `true` e `false` não têm significado especial. Símbolos que você usar o `if` diretiva deve ser definida pela linha de comando ou nas configurações do projeto; não há nenhum `define` diretiva de pré-processador.

O código a seguir ilustra o uso do `#if`, `#else`, e `#endif` diretivas. Neste exemplo, o código contém duas versões da definição de `function1`. Quando `VERSION1` é definido usando o [-definir a opção de compilador](https://msdn.microsoft.com/library/434394ae-0d4a-459c-a684-bffede519a04), o código entre as `#if` diretiva e a `#else` diretiva é ativada. Caso contrário, o código entre `#else` e `#endif` é ativado.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet7301.fs)]

Não há nenhuma `#define` diretiva de pré-processador em F#. Você deve usar as configurações de projeto ou a opção do compilador para definir os símbolos usados pelo `#if` diretiva.

Diretivas de compilação condicional podem ser aninhadas. Recuo não é significativo para diretivas de pré-processador.

Você também pode negar um símbolo com `!`. Neste exemplo, o valor da cadeia de caracteres é algo somente quando _não_ depuração:

```fsharp
#if !DEBUG
let str = "Not debugging!"
#else
let str = "Debugging!"
#endif
```

## <a name="line-directives"></a>Diretivas de linha

Durante a criação, o compilador relata erros em F# números de código, fazendo referência a linha na qual ocorre a cada erro. Esses números de linha iniciam em 1 para a primeira linha em um arquivo. No entanto, se você estiver gerando F# código-fonte da ferramenta de outro, os números de linha no código gerado geralmente não são de interesse, pois os erros no gerado F# código provavelmente são provenientes de outra fonte. O `#line` diretiva fornece uma maneira para autores de ferramentas que geram F# código-fonte para passar informações sobre a linha original números e arquivos de origem para o gerado F# código.

Quando você usa o `#line` diretiva, nomes de arquivo devem ser colocados entre aspas. A menos que o token textual (`@`) aparece na frente da cadeia de caracteres, você deve escapar caracteres de barra invertida, usando dois caracteres de barra invertida em vez de um para usá-los no caminho. Estes são os tokens de linha válido. Nestes exemplos, suponha que o arquivo original `Script1` resulta em uma gerada automaticamente F# arquivo de código quando ele é executado por meio de uma ferramenta e o código no local dessas diretivas é gerado a partir de alguns tokens na linha 25 no arquivo `Script1`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet7303.fs)]

Esses símbolos indicam que o F# código gerado neste local é derivado do algumas construções em ou próximo à linha `25` na `Script1`.

## <a name="compiler-directives"></a>Diretivas de compilador

Diretivas de compilador se parecer com diretivas de pré-processador, porque eles são prefixados com um sinal #, mas em vez de ser interpretado pelo pré-processador, eles são deixados para o compilador a interpretar e agir.

A tabela a seguir lista a diretiva de compilador que está disponível no F#.

|Diretiva|Descrição|
|---------|-----------|
|`#light` ["on"&#124;"off"]|Habilita ou desabilita a sintaxe leve, para compatibilidade com outras versões do ML. Por padrão, a sintaxe leve está habilitada. Sintaxe detalhada está sempre habilitado. Portanto, você pode usar a sintaxe leve e a sintaxe detalhada. A diretiva `#light` por si só é equivalente a `#light "on"`. Se você especificar `#light "off"`, você deve usar a sintaxe detalhada para todas as construções de linguagem. Sintaxe na documentação do F# é apresentado com a suposição de que você está usando a sintaxe leve. Para obter mais informações, consulte [sintaxe detalhada](verbose-syntax.md).|

Para diretivas de interpretador (fsi.exe), consulte [programação interativa com F# ](../tutorials/fsharp-interactive/index.md).

## <a name="see-also"></a>Consulte também

- [Referência da Linguagem F#](index.md)
- [Opções do Compilador](compiler-options.md)
