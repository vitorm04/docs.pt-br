---
title: Processando o arquivo XML – Guia de Programação em C#
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- XML processing [C#]
- XML [C#], processing
ms.assetid: 60c71193-9dac-4cd3-98c5-100bd0edcc42
ms.openlocfilehash: b2b19a2b2c46df5b78b6ebba48955cae55d32121
ms.sourcegitcommit: 337bdc5a463875daf2cc6883e5a2da97d56f5000
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/24/2019
ms.locfileid: "72846931"
---
# <a name="processing-the-xml-file-c-programming-guide"></a>Processando o arquivo XML (Guia de Programação em C#)

O compilador gera uma cadeia de identificação para cada constructo no seu código marcado para gerar a documentação. (Para obter informações sobre como marcar seu código, consulte [marcas recomendadas para comentários de documentação](./recommended-tags-for-documentation-comments.md).) A cadeia de caracteres de ID identifica exclusivamente a construção. Programas que processam o arquivo XML podem usar a cadeia de identificação para identificar o item de metadados/reflexão do .NET Framework correspondente ao qual a documentação se aplica.

O arquivo XML não é uma representação hierárquica de seu código; é uma lista simples com uma ID gerada para cada elemento.

O compilador observa as seguintes regras quando gera as cadeias de identificação:

- Não há espaços em branco na cadeia de caracteres.

- A primeira parte da cadeia de identificação identifica o tipo de membro que está sendo identificado por meio de um único caractere seguido por dois-pontos. São usados os seguintes tipos de membro:

    |Caractere|Descrição|
    |---------------|-----------------|
    |N|namespace<br /><br /> Não é possível adicionar comentários de documentação a um namespace, mas será possível fazer referências cref a eles se houver suporte.|
    |T|tipo: classe, interface, struct, enumeração, delegado|
    |F|campo|
    |P|propriedade (incluindo indexadores ou outras propriedades indexadas)|
    |M|método (incluindo métodos especiais como construtores, operadores e assim por diante)|
    |E|evento|
    |!|cadeia de caracteres de erro<br /><br /> O restante da cadeia de caracteres fornece informações sobre o erro. O compilador C# gera informações de erro para links que não podem ser resolvidos.|

- A segunda parte da cadeia de caracteres é o nome totalmente qualificado do item, iniciando na raiz do namespace. O nome do item, seus tipos delimitadores e o namespace são separados por pontos. Se o nome do próprio item tiver pontos, eles serão substituídos pelo sustenido ('#'). Supõe-se que nenhum item tem um sustenido diretamente em seu nome. Por exemplo, o nome totalmente qualificado do construtor de cadeia de caracteres seria "System.String.#ctor".

- Para propriedades e métodos, se houver argumentos para o método, seguirá a lista de argumentos entre parênteses. Se não houver nenhum argumento, não haverá parênteses. Os argumentos são separados por vírgulas. A codificação de cada argumento segue diretamente a maneira como ele é codificado em uma assinatura do .NET Framework:

  - Tipos base. Tipos regulares (ELEMENT_TYPE_CLASS ou ELEMENT_TYPE_VALUETYPE) são representados como o nome totalmente qualificado do tipo.

  - Os tipos intrínsecos (por exemplo, ELEMENT_TYPE_I4, ELEMENT_TYPE_OBJECT, ELEMENT_TYPE_STRING, ELEMENT_TYPE_TYPEDBYREF e ELEMENT_TYPE_VOID) são representados como o nome totalmente qualificado do tipo completo correspondente. Por exemplo, System.Int32 ou System.TypedReference.

  - ELEMENT_TYPE_PTR é representado como um '\*' após o tipo modificado.

  - ELEMENT_TYPE_BYREF é representado como um "\@" após o tipo modificado.

  - ELEMENT_TYPE_PINNED é representado como um '^' após o tipo modificado. O compilador C# nunca gera isso.

  - ELEMENT_TYPE_CMOD_REQ é representado como um '&#124;' e o nome totalmente qualificado da classe do modificador, após o tipo modificado. O compilador C# nunca gera isso.

  - ELEMENT_TYPE_CMOD_OPT é representado como um '!' e o nome totalmente qualificado da classe do modificador, após o tipo modificado.

  - ELEMENT_TYPE_SZARRAY é representado como "[]" após o tipo de elemento da matriz.

  - ELEMENT_TYPE_GENERICARRAY é representado como "[?]" após o tipo de elemento da matriz. O compilador C# nunca gera isso.

  - ELEMENT_TYPE_ARRAY é representado como [*lowerbound*:`size`,*lowerbound*:`size`] em que o número de vírgulas é a classificação -1 e os limites e o tamanho inferiores de cada dimensão, se conhecidos, são representados no formato decimal. Se um limite ou tamanho inferior não for especificado, ele é simplesmente omitido. Se o limite e o tamanho inferiores de uma determinada dimensão forem omitidos, o ':' será omitido também. Por exemplo, uma matriz bidimensional com 1 como limites inferiores e tamanhos não especificados é [1:,1:].

  - ELEMENT_TYPE_FNPTR é representado como "=FUNC:`type`(*assinatura*)", em que `type` é o tipo de retorno e *assinatura* são os argumentos do método. Se não houver nenhum argumento, os parênteses serão omitidos. O compilador C# nunca gera isso.

    Os seguintes componentes de assinatura não são representados, porque nunca são usadas para diferenciar métodos sobrecarregados:

  - convenção de chamada

  - tipo de retorno

  - ELEMENT_TYPE_SENTINEL

- Somente para operadores de conversão (op_Implicit e op_Explicit), o valor retornado do método é codificado como um '~' seguido pelo tipo de retorno, conforme codificado acima.

- Para tipos genéricos, o nome do tipo é seguido por um caractere de acento grave e, em seguida, por um número que indica o número de parâmetros de tipo genérico. Por exemplo:

     ``<member name="T:SampleClass`2">`` é a marcação de um tipo definido como `public class SampleClass<T, U>`.

     Para métodos que aceitam tipos genéricos como parâmetros, os parâmetros de tipo genérico são especificados como números precedidos por caracteres de acento grave (por exemplo \`0,\`1). Cada número que representa uma notação de matriz com base em zero para parâmetros genéricos do tipo.

## <a name="examples"></a>Exemplos

Os exemplos a seguir mostram como as cadeias de identificação para uma classe e seus membros seriam geradas:

[!code-csharp[csProgGuidePointers#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers.cs#21)]

## <a name="see-also"></a>Consulte também

- [Guia de Programação em C#](../index.md)
- [-doc (opções do compilador do C#)](../../language-reference/compiler-options/doc-compiler-option.md)
- [Comentários da documentação XML](./index.md)
