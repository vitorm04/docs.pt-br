---
title: "Interpolação de cadeia de caracteres - C#"
description: "Saiba como funciona o interpolação de cadeia de caracteres no C# 6"
keywords: .NET, .NET Core, C#, cadeia de caracteres
author: mgroves
ms.author: wiwagn
ms.date: 03/06/2017
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: f8806f6b-3ac7-4ee6-9b3e-c524d5301ae9
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: de8f77e44319731f87f00d227a5373a78bf40e32
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---

# <a name="string-interpolation-in-c"></a>Interpolação de cadeia de caracteres no C# #

A interpolação de cadeia de caracteres é a maneira que os espaços reservados em uma cadeia de caracteres são substituídos pelo valor de uma variável de cadeia de caracteres. Antes do C# 6, a maneira de fazer isso era com `System.String.Format`. Isso funciona, mas como ele usa espaços reservados numerados, pode ser mais difícil de ler e ser mais detalhado.

Outras linguagens de programação tiveram interpolação de cadeia de caracteres integradas à linguagem por algum tempo. Por exemplo, em PHP:

```php
$name = "Jonas";
echo "My name is $name.";
// This will output "My name is Jonas."
```

No C# 6, finalmente temos esse estilo de interpolação de cadeia de caracteres. Você pode usar um `$` antes de uma cadeia de caracteres para indicar que ele deve substituir variáveis/expressões para seus valores.

## <a name="prerequisites"></a>Pré-requisitos
Você precisará configurar seu computador para executar o .NET Core. Você encontrará as instruções de instalação na página do [.NET Core](https://www.microsoft.com/net/core).
Você pode executar esse aplicativo no Windows, Ubuntu Linux, macOS ou em um contêiner do Docker. Será necessário instalar o editor de código de sua preferência. As descrições a seguir usam o [Visual Studio Code](https://code.visualstudio.com/), que é uma software livre, no editor de plataforma. No entanto, você pode usar quaisquer ferramentas que esteja familiarizado.

## <a name="create-the-application"></a>Criar o aplicativo

Agora que você instalou todas as ferramentas, crie um novo aplicativo do .NET Core. Para usar o gerador de linha de comando, crie um diretório para seu projeto, como `interpolated`e execute o seguinte comando no shell de sua preferência:

```
dotnet new console
```

Esse comando criará um projeto do .NET Core barebones com um arquivo de projeto, *interpolated.csproj*, e um arquivo de código-fonte, *Program.cs*. Você precisará executar `dotnet restore` para restaurar as dependências necessárias para compilar esse projeto.

Para executar o programa, use `dotnet run`. Você deve ver a saída do "Olá, Mundo" no console.

## <a name="intro-to-string-interpolation"></a>Introdução à interpolação de cadeia de caracteres

Com `System.String.Format`, especifique "espaços reservados" em uma cadeia de caracteres que são substituídos pelos parâmetros na cadeia de caracteres a seguir. Por exemplo:

[!code-csharp[Exemplo de String.Format](../../../samples/snippets/csharp/new-in-6/string-interpolation.cs#StringFormatExample)]  

Isso produzirá "Meu nome é Matt Groves".

No C# 6, em vez de usar `String.Format`, você define uma cadeia de caracteres interpolada acrescentando-a com o símbolo `$` e, em seguida, usando as variáveis diretamente na cadeia de caracteres. Por exemplo:

[!code-csharp[Exemplo de interpolação](../../../samples/snippets/csharp/new-in-6/string-interpolation.cs#InterpolationExample)]  

Você não precisa usar apenas variáveis. Você pode usar qualquer expressão entre colchetes. Por exemplo:

[!code-csharp[Exemplo de expressão de interpolação](../../../samples/snippets/csharp/new-in-6/string-interpolation.cs#InterpolationExpressionExample)]  

O que resultaria:

```
This is line number 1
This is line number 2
This is line number 3
This is line number 4
This is line number 5
```

## <a name="how-string-interpolation-works"></a>Como funciona o interpolação de cadeia de caracteres

Nos bastidores, essa sintaxe de interpolação de cadeia de caracteres é convertida em String.Format pelo compilador. Portanto, você pode fazer o [mesmo que já fez antes com String.Format](https://msdn.microsoft.com/en-us/library/dwhawy9k(v=vs.110).aspx).

Por exemplo, você pode adicionar preenchimento e formatação numérica:

[!code-csharp[Exemplo de formatação de interpolação](../../../samples/snippets/csharp/new-in-6/string-interpolation.cs#InterpolationFormattingExample)]  

O item acima resultaria em:

```
998        5,177.67
999        6,719.30
1000       9,910.61
1001       529.34
1002       1,349.86
1003       2,660.82
1004       6,227.77
```

Se um nome de variável não for encontrado, será gerado um erro em tempo de compilação.

Por exemplo:

```csharp
var animal = "fox";
var localizeMe = $"The {adj} brown {animal} jumped over the lazy {otheranimal}";
var adj = "quick";
Console.WriteLine(localizeMe);
```

Se compilar isso, você obterá erros:
 
* `Cannot use local variable 'adj' before it is declared` – a variável `adj` não foi declarada até *depois* da cadeia de caracteres interpolada.
* `The name 'otheranimal' does not exist in the current context` – uma variável chamada `otheranimal` nunca foi declarada

## <a name="localization-and-internationalization"></a>Internacionalização e localização

Uma cadeia de caracteres interpolada dá suporte a `IFormattable` e `FormattableString`, o que pode ser útil para internacionalização.

Por padrão, uma cadeia de caracteres interpolada usa a cultura atual. Para usar uma cultura diferente, você pode convertê-la como `IFormattable`

Por exemplo:

[!code-csharp[Exemplo de internacionalização de interpolação](../../../samples/snippets/csharp/new-in-6/string-interpolation.cs#InterpolationInternationalizationExample)]  

## <a name="conclusion"></a>Conclusão 

Neste tutorial, você aprendeu como usar recursos de interpolação de cadeia de caracteres de C# 6. Ele é basicamente uma maneira mais concisa de gravar instruções `String.Format` simples, com algumas restrições para usos mais avançados.

