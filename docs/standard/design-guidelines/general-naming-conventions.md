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
ms.openlocfilehash: d1b01fac7368ffeceb554c6f12aecb8f8760fa1d
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709329"
---
# <a name="general-naming-conventions"></a>Convenções de nomenclatura gerais
Esta seção descreve as convenções de nomenclatura gerais relacionadas à escolha do Word, diretrizes sobre como usar abreviações e acrônimos e recomendações sobre como evitar o uso de nomes específicos à linguagem.  
  
## <a name="word-choice"></a>Opção de palavra  
 **✓ DO** Escolha nomes de identificador facilmente legível.  
  
 Por exemplo, uma propriedade chamada `HorizontalAlignment` é mais legível do que `AlignmentHorizontal`.  
  
 **✓ DO** favorecer legibilidade por questão de brevidade.  
  
 O nome da propriedade `CanScrollHorizontally` é melhor do que `ScrollableX` (uma referência obscura para o eixo X).  
  
 **X DO NOT** usar outros caracteres não alfanuméricos, hífens ou sublinhados.  
  
 **X DO NOT** usar notação húngara.  
  
 **X AVOID** usando identificadores que entrem em conflito com palavras-chave de amplamente usados linguagens de programação.  
  
 De acordo com a regra 4 do Common Language Specification (CLS), todos os idiomas compatíveis devem fornecer um mecanismo que permita o acesso a itens nomeados que usam uma palavra-chave desse idioma como um identificador. C#, por exemplo, usa o sinal @ como um mecanismo de escape nesse caso. No entanto, ainda é uma boa ideia evitar palavras-chave comuns, pois é muito mais difícil usar um método com a sequência de escape de um sem ele.  
  
## <a name="using-abbreviations-and-acronyms"></a>Usando abreviações e acrônimos  
 **X DO NOT** usar abreviações ou contrações como parte dos nomes de identificador.  
  
 Por exemplo, use `GetWindow` em vez de `GetWin`.  
  
 **X DO NOT** usar os acrônimos que não são amplamente aceitas e até mesmo se elas forem, somente quando necessário.  
  
## <a name="avoiding-language-specific-names"></a>Evitando nomes específicos de idioma  
 **✓ DO** usar nomes semanticamente interessantes em vez de palavras-chave para nomes de tipo.  
  
 Por exemplo, `GetLength` é um nome melhor do que `GetInt`.  
  
 **✓ DO** usar um nome de tipo genérico do CLR, em vez de um nome de idioma específico, em casos raros, quando um identificador não tem nenhum significado semântico, além de seu tipo.  
  
 Por exemplo, um método que converte para <xref:System.Int64> deve ser nomeado `ToInt64`, não `ToLong` (porque <xref:System.Int64> é um nome CLR para C#o alias específico `long`). A tabela a seguir apresenta vários tipos de dados base usando os nomes de tipo CLR (bem como os nomes de C#tipos correspondentes para, C++Visual Basic e).  
  
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
  
 **✓ DO** usar um nome comum, como `value` ou `item`, em vez de repetir o nome do tipo, em casos raros, quando um identificador não tem nenhum significado semântico e o tipo do parâmetro não é importante.  
  
## <a name="naming-new-versions-of-existing-apis"></a>Nomeando novas versões de APIs existentes  
 **✓ DO** usar um nome semelhante à API antigo durante a criação de novas versões de uma API existente.  
  
 Isso ajuda a destacar a relação entre as APIs.  
  
 **✓ DO** preferir adicionando um sufixo, em vez de um prefixo para indicar uma nova versão de uma API existente.  
  
 Isso auxiliará a descoberta ao procurar a documentação ou usar o IntelliSense. A versão antiga da API será organizada perto das novas APIs, pois a maioria dos navegadores e o IntelliSense mostram identificadores em ordem alfabética.  
  
 **✓ CONSIDER** usando um identificador de novo, mas significativo, em vez de adicionar um prefixo ou um sufixo.  
  
 **✓ DO** use um sufixo numérico para indicar uma nova versão de uma API existente, especialmente se o nome existente da API é o único nome que faça sentido (ou seja, se ele é um padrão da indústria) e se adicionando significativo qualquer sufixo (ou a alteração do nome) não é um aplicativo opção de ropriate.  
  
 **X DO NOT** usar "Ex" (ou similar) sufixo para um identificador para distingui-lo de uma versão anterior da mesma API.  
  
 **✓ DO** usam o sufixo "64" quando apresentando as versões de APIs que operam em um inteiro de 64 bits (um inteiro longo) em vez de um inteiro de 32 bits. Você só precisa tomar essa abordagem quando existir a API de 32 bits existente; Não faça isso para APIs totalmente novas com uma versão de 64 bits.  
  
 *Partes © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*  
  
 *Reimpresso com permissão da Pearson Education, Inc. das [Diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicado em 22 de outubro de 2008 por Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*  
  
## <a name="see-also"></a>Veja também

- [Diretrizes de design do Framework](../../../docs/standard/design-guidelines/index.md)
- [Diretrizes de nomenclatura](../../../docs/standard/design-guidelines/naming-guidelines.md)
