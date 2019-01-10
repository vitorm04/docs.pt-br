---
title: string – Referência de C#
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- string
- string_CSharpKeyword
helpviewer_keywords:
- strings [C#], reference
- '@ string literal'
- string literals [C#]
- string keyword [C#]
ms.assetid: 3037e558-fb22-494d-bca1-a15ade11b11a
ms.openlocfilehash: f6c76f8effc5aef82803014b9a7257c2ad6865b8
ms.sourcegitcommit: d6e419f9d9cd7e8f21ebf5acde6d016c16332579
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/12/2018
ms.locfileid: "53286475"
---
# <a name="string-c-reference"></a>string (Referência de C#)

O tipo `string` representa uma sequência de zero ou mais caracteres Unicode. `string` é um alias de <xref:System.String> no .NET.

Embora `string` seja um tipo de referência, os operadores de igualdade (`==` e `!=`) são definidos para comparar os valores dos objetos `string`, não referências. Isso torna o teste de igualdade de cadeia de caracteres mais intuitivo. Por exemplo:

```csharp
string a = "hello";
string b = "h";
// Append to contents of 'b'
b += "ello";
Console.WriteLine(a == b);
Console.WriteLine((object)a == (object)b);
```

Isso exibe "True" e, em seguida, "False" porque os conteúdos das cadeias de caracteres são equivalentes, mas `a` e `b` não fazem referência à mesma instância da cadeia de caracteres.

O operador + concatena as cadeias de caracteres:

```csharp
string a = "good " + "morning";
```

Isso cria um objeto de cadeia de caracteres que contém “good morning”.

Cadeias de caracteres são *imutável* – o conteúdo de um objeto de cadeia de caracteres não pode ser alterado depois que o objeto é criado, embora a sintaxe faça com que pareça que você pode fazer isso. Por exemplo, quando você escreve esse código, o compilador na verdade cria um novo objeto de cadeia de caracteres para manter a nova sequência de caracteres e esse novo objeto é atribuído a b. A cadeia de caracteres "h" é então qualificada para coleta de lixo.

```csharp
string b = "h";
b += "ello";
```

O operador [] pode ser usado para o acesso somente leitura a caracteres individuais de uma `string`:

```csharp
string str = "test";
char x = str[2];  // x = 's';
```

De maneira semelhante, o operador [] pode ser usado para iterar em cada caractere em uma `string`:

```csharp
string str = "test";

for (int i = 0; i < str.Length; i++)
{
  Console.Write(str[i] + " ");
}
// Output: t e s t
``` 

Literais de cadeia de caracteres são do tipo `string` e podem ser escritos de duas formas, entre aspas e @-quoted. Os literais de cadeia de caracteres entre aspas são colocados entre aspas duplas ("):

```csharp
"good morning"  // a string literal
```

Os literais de cadeia de caracteres podem conter qualquer literal de caractere. Sequências de escape são incluídas. O exemplo a seguir usa a sequência de escape `\\` de barra invertida, `\u0066` para a letra f e `\n` para a nova linha.

```csharp
string a = "\\\u0066\n";
Console.WriteLine(a);
```

> [!NOTE]
> O código de escape `\udddd` (em que `dddd` é um número de quatro dígitos) representa o caractere Unicode U+`dddd`. Os códigos de escape Unicode de oito dígitos também são reconhecidos: `\Udddddddd`.

Os literais de cadeia de caracteres textuais começam com `@` e também são colocados entre aspas duplas. Por exemplo:

```csharp
@"good morning"  // a string literal
```

A vantagem das cadeias de caracteres textuais é que as sequências de escape *não* são processadas, o que torna mais fácil escrever, por exemplo, um nome de arquivo totalmente qualificado:

```csharp
@"c:\Docs\Source\a.txt"  // rather than "c:\\Docs\\Source\\a.txt"
```

Para incluir aspas duplas em uma cadeia de caracteres @-quoted, dobre-a:

```csharp
@"""Ahoy!"" cried the captain." // "Ahoy!" cried the captain.
```

Para saber outras formas de usar o caractere especial `@`, confira [@ – identificador textual](../tokens/verbatim.md).

Para obter mais informações sobre cadeias de caracteres, consulte [Cadeias de caracteres](../../programming-guide/strings/index.md).

## <a name="example"></a>Exemplo

[!code-csharp[csrefKeywordsTypes#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#17)]  

## <a name="c-language-specification"></a>Especificação da linguagem C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Consulte também

- [Referência de C#](../index.md)
- [Guia de Programação em C#](../../programming-guide/index.md)
- [Melhores práticas para o uso de cadeias de caracteres](../../../standard/base-types/best-practices-strings.md)
- [Palavras-chave do C#](index.md)
- [Tipos de referência](reference-types.md)
- [Tipos de valor](value-types.md)
- [Operações básicas de cadeias de caracteres](../../../standard/base-types/basic-string-operations.md)
- [Criando novas cadeias de caracteres](../../../standard/base-types/creating-new.md)
- [Tabela de formatação de resultados numéricos](formatting-numeric-results-table.md)
