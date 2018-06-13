---
title: Convenções de nomenclatura gerais
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bc54b8bdc96a5038dc75111d9833e70e7ffd2e9e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33578034"
---
# <a name="general-naming-conventions"></a>Convenções de nomenclatura gerais
Esta seção descreve gerais convenções de nomenclatura relacionadas à escolha de palavra, diretrizes sobre o uso de abreviações e acrônimos e recomendações sobre como evitar o uso de nomes específicos do idioma.  
  
## <a name="word-choice"></a>Opções do Word  
 **FAZER ✓** Escolha nomes de identificador facilmente legível.  
  
 Por exemplo, uma propriedade chamada `HorizontalAlignment` é mais legível para o inglês do que `AlignmentHorizontal`.  
  
 **FAZER ✓** favorecer legibilidade por questão de brevidade.  
  
 O nome da propriedade `CanScrollHorizontally` é melhor do que `ScrollableX` (uma referência para o eixo x obscura).  
  
 **X não** usar outros caracteres não alfanuméricos, hífens ou sublinhados.  
  
 **X não** usar notação húngara.  
  
 **X Evite** usando identificadores que entrem em conflito com palavras-chave de amplamente usados linguagens de programação.  
  
 De acordo com a regra 4 do Common Language Specification (CLS), todos os idiomas compatíveis devem fornecer um mecanismo que permite o acesso a itens nomeados que usar uma palavra-chave de idioma como um identificador. C#, por exemplo, usa o @ logon como um mecanismo de escape nesse caso. No entanto, ainda é uma boa ideia para evitar palavras-chave comuns porque ele é muito mais difícil de usar um método com a sequência de escape que sem ele.  
  
## <a name="using-abbreviations-and-acronyms"></a>Usando siglas e abreviações  
 **X não** usar abreviações ou contrações como parte dos nomes de identificador.  
  
 Por exemplo, use `GetWindow` em vez de `GetWin`.  
  
 **X não** usar os acrônimos que não são amplamente aceitas e até mesmo se elas forem, somente quando necessário.  
  
## <a name="avoiding-language-specific-names"></a>Evitando nomes específicos do idioma  
 **FAZER ✓** usar nomes semanticamente interessantes em vez de palavras-chave para nomes de tipo.  
  
 Por exemplo, `GetLength` é um nome de melhor `GetInt`.  
  
 **FAZER ✓** usar um nome de tipo genérico do CLR, em vez de um nome de idioma específico, em casos raros, quando um identificador não tem nenhum significado semântico, além de seu tipo.  
  
 Por exemplo, um método de conversão em <xref:System.Int64> devem ser nomeados `ToInt64`, não `ToLong` (porque <xref:System.Int64> é um nome CLR para c#-alias específico `long`). A tabela a seguir apresenta vários tipos de dados base usando os nomes de tipo CLR (bem como os nomes de tipo correspondente do c#, Visual Basic e C++).  
  
|C#|Visual Basic|C++|CLR|  
|---------|------------------|-----------|---------|  
|**sbyte**|**SByte**|**char**|**SByte**|  
|**byte**|**Byte**|**unsigned char**|**Byte**|  
|**short**|**Short**|**short**|**Int16**|  
|**ushort**|**UInt16**|**unsigned short**|**UInt16**|  
|**int**|**Integer**|**int**|**Int32**|  
|**uint**|**UInt32**|**unsigned int**|**UInt32**|  
|**long**|**Long**|**__int64**|**Int64**|  
|**ulong**|**UInt64**|**unsigned __int64**|**UInt64**|  
|**float**|**Simples**|**float**|**Simples**|  
|**double**|**Duplo**|**double**|**Duplo**|  
|**bool**|**Booliano**|**bool**|**Booliano**|  
|**char**|**Char**|**wchar_t**|**Char**|  
|**string**|**Cadeia de caracteres**|**Cadeia de caracteres**|**Cadeia de caracteres**|  
|**object**|**Object**|**Object**|**Object**|  
  
 **FAZER ✓** usar um nome comum, como `value` ou `item`, em vez de repetir o nome do tipo, em casos raros, quando um identificador não tem nenhum significado semântico e o tipo do parâmetro não é importante.  
  
## <a name="naming-new-versions-of-existing-apis"></a>Nomenclatura novas versões de APIs existentes  
 **FAZER ✓** usar um nome semelhante à API antigo durante a criação de novas versões de uma API existente.  
  
 Isso ajuda a realçar a relação entre as APIs.  
  
 **FAZER ✓** preferir adicionando um sufixo, em vez de um prefixo para indicar uma nova versão de uma API existente.  
  
 Isso ajudará a descoberta ao procurar a documentação, ou usando o Intellisense. A versão antiga da API será organizada perto de novas APIs, como a maioria dos navegadores e Intellisense mostram identificadores em ordem alfabética.  
  
 **✓ CONSIDERE** usando um identificador de novo, mas significativo, em vez de adicionar um prefixo ou um sufixo.  
  
 **FAZER ✓** use um sufixo numérico para indicar uma nova versão de uma API existente, especialmente se o nome existente da API é o único nome que faça sentido (ou seja, se ele é um padrão da indústria) e se adicionando significativo qualquer sufixo (ou a alteração do nome) não é um aplicativo opção de ropriate.  
  
 **X não** usar "Ex" (ou similar) sufixo para um identificador para distingui-lo de uma versão anterior da mesma API.  
  
 **FAZER ✓** usam o sufixo "64" quando apresentando as versões de APIs que operam em um inteiro de 64 bits (um inteiro longo) em vez de um inteiro de 32 bits. Você só precisa usar essa abordagem à API de 32 bits existente existe; não faça isso para APIs totalmente novo com apenas uma versão de 64 bits.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*  
  
 *Reimpressas pela permissão de Pearson educação, Inc. de [diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicados 22 de outubro de 2008, Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*  
  
## <a name="see-also"></a>Consulte também  
 [Diretrizes de design do Framework](../../../docs/standard/design-guidelines/index.md)  
 [Diretrizes de nomenclatura](../../../docs/standard/design-guidelines/naming-guidelines.md)
