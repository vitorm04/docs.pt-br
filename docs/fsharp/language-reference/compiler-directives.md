---
title: Diretivas de compilador (F#)
description: 'Saiba mais sobre as diretivas de pré-processador em linguagem F #, diretivas de compilação condicional, diretivas de linha e diretivas de compilador.'
ms.date: 05/16/2016
ms.openlocfilehash: 5b7974d586b085ad8a40bc2d872cdd425494475a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33563380"
---
# <a name="compiler-directives"></a>Diretivas de compilador

Este tópico descreve as diretivas de processador e diretivas de compilador.


## <a name="preprocessor-directives"></a>Diretivas de pré-processador
Uma diretiva de pré-processamento é prefixada com o símbolo # e aparece em uma linha por si só. Ele será interpretado pré-processador, que é executado antes do compilador em si.

A tabela a seguir lista as diretivas de pré-processador que estão disponíveis em F #.


|Diretiva|Descrição|
|---------|-----------|
|`#if` *symbol*|Dá suporte à compilação condicional. Código na seção após o `#if` é incluído se o *símbolo* está definido.|
|`#else`|Dá suporte à compilação condicional. Marca uma seção de código para incluir se o símbolo usado com anterior `#if` não está definido.|
|`#endif`|Dá suporte à compilação condicional. Marca o final de uma seção condicional de código.|
|`#`[linha] *int*,<br/>`#`[linha] *int* *cadeia de caracteres*,<br/>`#`[linha] *int* *cadeia de caracteres textuais*|Indica o nome original da fonte código linha e arquivo, para depuração. Esse recurso é fornecido para as ferramentas que geram um código de origem F #.|
|`#nowarn` *warningcode*|Desabilita um aviso do compilador ou avisos. Para desabilitar um aviso, localize o número da saída do compilador e incluí-lo entre aspas. Omita o prefixo "FS". Para desabilitar vários números de aviso na mesma linha, incluir cada número de aspas e separe cada cadeia de caracteres por um espaço. Por exemplo:

`#nowarn "9" "40"`


O efeito de desabilitar um aviso se aplica a todo o arquivo, incluindo partes do arquivo que precedem a diretiva. |

## <a name="conditional-compilation-directives"></a>Diretivas de compilação condicional
Código que é desativado por um essas diretivas esmaecido no Editor StudioCode Visual.


>[!NOTE] 
O comportamento das diretivas de compilação condicional não é o mesmo como seria em outros idiomas. Por exemplo, você não pode usar expressões Boolianas que envolvem símbolos, e `true` e `false` não têm nenhum significado especial. Símbolos que você use o `if` diretiva deve ser definida pela linha de comando ou nas configurações do projeto, não há nenhum `define` diretiva de pré-processador.


O código a seguir ilustra o uso do `#if`, `#else`, e `#endif` diretivas. Neste exemplo, o código contém duas versões da definição de `function1`. Quando `VERSION1` é definido usando o [-definir a opção de compilador](https://msdn.microsoft.com/library/434394ae-0d4a-459c-a684-bffede519a04), o código entre as `#if` diretiva e a `#else` diretiva está ativada. Caso contrário, o código entre `#else` e `#endif` está ativado.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet7301.fs)]

Não há nenhum `#define` diretiva de pré-processador em F #. Você deve usar as configurações de projeto ou a opção de compilador para definir os símbolos utilizados pelo `#if` diretiva.

Diretivas de compilação condicional podem ser aninhadas. Recuo não é significativo para diretivas de pré-processador.


## <a name="line-directives"></a>Diretivas de linha
Durante a criação, o compilador relata erros no código F #, fazendo referência a números de linha em que cada erro ocorre. Esses números de linha iniciam em 1 para a primeira linha em um arquivo. No entanto, se você estiver gerando o código de origem F # de outra ferramenta, os números de linha no código gerado geralmente não são de interesse, porque os erros no F # código gerado provavelmente são provenientes de outra fonte. O `#line` diretiva fornece uma maneira para autores de ferramentas que geram um código de origem F # para passar informações sobre a linha original números e arquivos de origem para o código gerado do F #.

Quando você usa o `#line` diretiva, nomes de arquivo devem ser colocados entre aspas. A menos que o token textual (`@`) aparece na frente da cadeia de caracteres, você deve escapar caracteres de barra invertida usando dois caracteres de barra invertida em vez de um para usá-los no caminho. Estes são os tokens de linha válido. Nestes exemplos, suponha que o arquivo original `Script1` resulta em um arquivo de código F # gerado automaticamente quando ele é executado por meio de uma ferramenta e o código no local dessas diretivas gerado de alguns tokens na linha 25 no arquivo `Script1`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet7303.fs)]

Esses tokens indicam que o código F # gerado nesse local é derivado de algumas construções em ou próximo à linha `25` em `Script1`.


## <a name="compiler-directives"></a>Diretivas de compilador
Diretivas de compilador lembram diretivas de pré-processador, porque eles são prefixados com um sinal #, mas em vez de ser interpretado pelo pré-processador, eles são deixados para o compilador a interpretar e agir sobre.

A tabela a seguir lista a diretiva de compilador que está disponível em F #.


|Diretiva|Descrição|
|---------|-----------|
|`#light` ["on"&#124;"off"]|Habilita ou desabilita a sintaxe leve, para compatibilidade com outras versões do ML. Por padrão, a sintaxe leve está habilitado. Sintaxe detalhada está sempre habilitado. Portanto, você pode usar a sintaxe leve e sintaxe detalhada. A diretiva `#light` por si só é equivalente a `#light "on"`. Se você especificar `#light "off"`, você deve usar a sintaxe detalhada para todas as construções de linguagem. Sintaxe na documentação do F # é apresentado com a suposição de que você está usando a sintaxe leve. Para obter mais informações, consulte [sintaxe detalhada](verbose-syntax.md).|
Para diretivas do interpretador (fsi.exe), consulte [de programação com F # interativo](../tutorials/fsharp-interactive/index.md).


## <a name="see-also"></a>Consulte também
[Referência da Linguagem F#](index.md)

[Opções do Compilador](compiler-options.md)

