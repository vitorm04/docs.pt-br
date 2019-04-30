---
title: Convenções de maiúsculas e minúsculas
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- camel-case names [.NET Framework]
- class library design guidelines [.NET Framework], capitalization
- Pascal-case names [.NET Framework]
- case sensitivity, capitalization conventions
- names [.NET Framework], capitalization
ms.assetid: 4c4ea526-9203-486f-b72d-29d61c5b3c6d
author: KrzysztofCwalina
ms.openlocfilehash: 9a4cf94ca7fcada7dfc0886422b373abc807a0fe
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61966472"
---
# <a name="capitalization-conventions"></a>Convenções de maiúsculas e minúsculas
As diretrizes neste capítulo dispor de um método simples para usar o caso, que, quando aplicadas de forma consistente, os identificadores de marca para tipos, membros e parâmetros de fácil leitura.  
  
## <a name="capitalization-rules-for-identifiers"></a>Regras de maiusculas e minúsculas de identificadores  
 Para diferenciar as palavras em um identificador, maiuscula a primeira letra de cada palavra no identificador. Não use sublinhados para diferenciar as palavras, ou, de fato, em qualquer lugar em identificadores. Há duas maneiras de apropriado para capitalizar identificadores, dependendo do uso do identificador:  
  
- PascalCasing  
  
- camelCasing  
  
 A convenção de PascalCasing, usada para todos os identificadores, exceto os nomes de parâmetro, escreve o primeiro caractere de cada palavra (incluindo acrônimos ao longo de duas letras), conforme mostrado nos exemplos a seguir:  
  
 `PropertyDescriptor`  
 `HtmlTag`  
  
 Um caso especial é feito para as abreviações de duas letras em que as duas letras estão em maiusculas, de conforme mostrado na seguinte identificador:  
  
 `IOStream`  
  
 A convenção de camelCasing, usada somente para os nomes de parâmetro, escreve o primeiro caractere de cada palavra, exceto a primeira palavra, conforme mostrado nos exemplos a seguir. Como o exemplo também mostra, acrônimos de duas letras que começam a um identificador em camel case estão em minúsculas.  
  
 `propertyDescriptor`  
 `ioStream`  
 `htmlTag`  
  
 **✓ DO** usar PascalCasing para todos os membros, tipo e namespace nomes públicos consiste em várias palavras.  
  
 **✓ DO** usar camelCasing para nomes de parâmetro.  
  
 A tabela a seguir descreve as regras de maiusculas e minúsculas para diferentes tipos de identificadores.  
  
|Identificador|Maiúsculas|Exemplo|  
|----------------|------------|-------------|  
|Namespace|Pascal|`namespace System.Security { ... }`|  
|Tipo|Pascal|`public class StreamReader { ... }`|  
|Interface|Pascal|`public interface IEnumerable { ... }`|  
|Método|Pascal|`public class Object {` <br />  `public virtual string ToString();` <br /> `}`|  
|Propriedade|Pascal|`public class String {` <br />  `public int Length { get; }` <br /> `}`|  
|evento|Pascal|`public class Process {` <br />  `public event EventHandler Exited;` <br /> `}`|  
|Campo|Pascal|`public class MessageQueue {` <br />  `public static readonly TimeSpan` <br /> `InfiniteTimeout;` <br /> `}` <br /> `public struct UInt32 {` <br />  `public const Min = 0;` <br /> `}`|  
|Valor de enumeração|Pascal|`public enum FileMode {` <br />  `Append,` <br />  `...` <br /> `}`|  
|Parâmetro|Camel|`public class Convert {` <br />  `public static int ToInt32(string value);` <br /> `}`|  
  
## <a name="capitalizing-compound-words-and-common-terms"></a>Aproveitando a palavras compostas e termos comuns  
 A maioria dos termos compostos são tratados como palavras individuais para fins de maiusculas e minúsculas.  
  
 **X DO NOT** cada palavra em palavras compostas de forma fechada chamadas em maiuscula.  
  
 Essas são as palavras compostas escritas como uma única palavra, como o ponto de extremidade. Para fins de diretrizes de maiusculas e minúsculas, trate uma palavra composta do formulário fechado como uma única palavra. Use um dicionário atual para determinar se uma palavra composta é escrita em forma fechada.  
  
|Pascal|Camel|não|  
|------------|-----------|---------|  
|`BitFlag`|`bitFlag`|`Bitflag`|  
|`Callback`|`callback`|`CallBack`|  
|`Canceled`|`canceled`|`Cancelled`|  
|`DoNot`|`doNot`|`Don't`|  
|`Email`|`email`|`EMail`|  
|`Endpoint`|`endpoint`|`EndPoint`|  
|`FileName`|`fileName`|`Filename`|  
|`Gridline`|`gridline`|`GridLine`|  
|`Hashtable`|`hashtable`|`HashTable`|  
|`Id`|`id`|`ID`|  
|`Indexes`|`indexes`|`Indices`|  
|`LogOff`|`logOff`|`LogOut`|  
|`LogOn`|`logOn`|`LogIn`|  
|`Metadata`|`metadata`|`MetaData, metaData`|  
|`Multipanel`|`multipanel`|`MultiPanel`|  
|`Multiview`|`multiview`|`MultiView`|  
|`Namespace`|`namespace`|`NameSpace`|  
|`Ok`|`ok`|`OK`|  
|`Pi`|`pi`|`PI`|  
|`Placeholder`|`placeholder`|`PlaceHolder`|  
|`SignIn`|`signIn`|`SignOn`|  
|`SignOut`|`signOut`|`SignOff`|  
|`UserName`|`userName`|`Username`|  
|`WhiteSpace`|`whiteSpace`|`Whitespace`|  
|`Writable`|`writable`|`Writeable`|  
  
## <a name="case-sensitivity"></a>Diferenciação de maiúsculas e minúsculas  
 Idiomas que podem ser executados no CLR não são necessários para dar suporte a diferenciação de maiusculas e minúsculas, embora alguns façam. Mesmo se a linguagem dá suporte a ele, outras linguagens que podem acessar sua estrutura, não. Todas as APIs sejam acessíveis externamente, portanto, não podem contar caso sozinho para distinguir entre os dois nomes no mesmo contexto.  
  
 **X DO NOT** suponha que todas as linguagens de programação diferenciam maiusculas de minúsculas. Eles não são. Nomes não podem diferir por caso sozinho.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*  
  
 *Reimpresso com permissão da Pearson Education, Inc. de [as diretrizes de Design do Framework: As convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicados 22 de outubro de 2008 pela Addison-Wesley Professional, como parte da série de desenvolvimento do Microsoft Windows.*  
  
## <a name="see-also"></a>Consulte também

- [Diretrizes de design do Framework](../../../docs/standard/design-guidelines/index.md)
- [Diretrizes de nomenclatura](../../../docs/standard/design-guidelines/naming-guidelines.md)
