---
title: Convenções de nomenclatura gerais
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- names [.NET Framework], conflicts
- type names, conflicts
- language-specific type names
- names [.NET Framework], about naming guidelines
- names [.NET Framework], abbreviations
- abbreviation naming guidelines
- acronym naming guidelines
- Hungarian notation
- names [.NET Framework], type names
- names [.NET Framework], acronyms
ms.assetid: d3a77ea1-75d2-4969-a8c3-3e1e3e1aaedc
ms.openlocfilehash: ef4a8f571a67477739bbc59d3103ba78dea47177
ms.sourcegitcommit: 1c1a1f9ec0bd1efb3040d86a79f7ee94e207cca5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/03/2020
ms.locfileid: "80635915"
---
# <a name="general-naming-conventions"></a>Convenções de nomenclatura gerais

Esta seção descreve convenções gerais de nomeação que se relacionam com a escolha de palavras, diretrizes sobre o uso de abreviaturas e siglas e recomendações sobre como evitar o uso de nomes específicos do idioma.

## <a name="word-choice"></a>Escolha do Palavra
 ✔️ DO escolha nomes identificadores facilmente legíveis.

 Por exemplo, uma `HorizontalAlignment` propriedade nomeada é `AlignmentHorizontal`mais legível em inglês do que .

 ✔️ favor da legibilidade sobre a brevidade.

 O nome `CanScrollHorizontally` da `ScrollableX` propriedade é melhor do que (uma referência obscura ao eixo X).

 ❌NÃO use sublinhados, hífens ou quaisquer outros caracteres não alfanuméricos.

 ❌NÃO use notação húngara.

 ❌EVITE usar identificadores que conflitem com palavras-chave de linguagens de programação amplamente utilizadas.

 De acordo com a regra 4 da Especificação da Linguagem Comum (CLS), todas as línguas compatíveis devem fornecer um mecanismo que permita o acesso a itens nomeados que usam uma palavra-chave dessa língua como um identificador. C#, por exemplo, usa o sinal @ como mecanismo de fuga neste caso. No entanto, ainda é uma boa idéia evitar palavras-chave comuns porque é muito mais difícil usar um método com a seqüência de fuga do que um sem ele.

## <a name="using-abbreviations-and-acronyms"></a>Usando abreviaturas e siglas
 ❌NÃO use abreviaturas ou contrações como parte de nomes identificadores.

 Por exemplo, `GetWindow` use `GetWin`em vez de .

 ❌NÃO use nenhuma sigla que não seja amplamente aceita, e mesmo que sejam, somente quando necessário.

## <a name="avoiding-language-specific-names"></a>Evitando nomes específicos do idioma
 ✔️ DO usam nomes semanticamente interessantes em vez de palavras-chave específicas do idioma para nomes de tipos.

 Por exemplo, `GetLength` é um `GetInt`nome melhor do que .

 ✔️ USO de um nome genérico do tipo CLR, em vez de um nome específico da linguagem, nos raros casos em que um identificador não tem significado semântico além de seu tipo.

 Por exemplo, um método <xref:System.Int64> de `ToInt64`conversão `ToLong` para <xref:System.Int64> deve ser nomeado , não (porque `long`é um nome CLR para o alias c#específico ). A tabela a seguir apresenta vários tipos de dados básicos usando os nomes do tipo CLR (bem como os nomes de tipo correspondentes para C#, Visual Basic e C++).

|C#|Visual Basic|C++|CLR|
|---------|------------------|-----------|---------|
|**sbyte**|**Sbyte**|**char**|**Sbyte**|
|**byte**|**Byte**|**unsigned char**|**Byte**|
|**Curto**|**Curto**|**Curto**|**Int16**|
|**ushort**|**UInt16**|**unsigned short**|**UInt16**|
|**Int**|**Inteiro**|**Int**|**Int32**|
|**uint**|**UInt32**|**unsigned int**|**UInt32**|
|**Longas**|**Longas**|**__int64**|**Int64**|
|**Ulong**|**UInt64**|**unsigned __int64**|**UInt64**|
|**Flutuar**|**Único**|**Flutuar**|**Único**|
|**double**|**Duplo**|**double**|**Duplo**|
|**bool**|**Boolean**|**bool**|**Boolean**|
|**char**|**Char**|**Wchar_t**|**Char**|
|**cadeia de caracteres**|**Cadeia de caracteres**|**Cadeia de caracteres**|**Cadeia de caracteres**|
|**Objeto**|**Objeto**|**Objeto**|**Objeto**|

 ✔️ USO de um nome `value` `item`comum, como ou , em vez de repetir o nome do tipo, nos raros casos em que um identificador não tem significado semântico e o tipo de parâmetro não é importante.

## <a name="naming-new-versions-of-existing-apis"></a>Nomeando novas versões de APIs existentes
 ✔️ USO de um nome semelhante à API antiga ao criar novas versões de uma API existente.

 Isso ajuda a destacar a relação entre as APIs.

 ✔️ DO preferem adicionar um sufixo em vez de um prefixo para indicar uma nova versão de uma API existente.

 Isso ajudará a detecção ao navegar na documentação ou usar o IntelliSense. A versão antiga da API será organizada perto das novas APIs, porque a maioria dos navegadores e intelliSense mostram identificadores em ordem alfabética.

 ✔️ considero usar um identificador novo, mas significativo, em vez de adicionar um sufixo ou um prefixo.

 ✔️ USO de um sufixo numérico para indicar uma nova versão de uma API existente, particularmente se o nome existente da API é o único nome que faz sentido (ou seja, se é um padrão da indústria) e se adicionar qualquer sufixo significativo (ou alterar o nome) não é uma opção apropriada.

 ❌NÃO use o sufixo "Ex" (ou um similar) para um identificador para distingui-lo de uma versão anterior da mesma API.

 ✔️ DO use o sufixo "64" ao introduzir versões de APIs que operam em um inteiro de 64 bits (um inteiro longo) em vez de um inteiro de 32 bits. Você só precisa tomar essa abordagem quando a API de 32 bits existente existir; não faça isso para novas APIs com apenas uma versão de 64 bits.

 *Porções &copy; 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*

 *Reimpresso com permissão da Pearson Education, Inc. das [Diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicado em 22 de outubro de 2008 por Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*

## <a name="see-also"></a>Confira também

- [Diretrizes de design de estrutura](../../../docs/standard/design-guidelines/index.md)
- [Diretrizes de nomeação](../../../docs/standard/design-guidelines/naming-guidelines.md)
- [Convenções de nomenclatura .NET para EditorConfig](/visualstudio/ide/editorconfig-naming-conventions)
