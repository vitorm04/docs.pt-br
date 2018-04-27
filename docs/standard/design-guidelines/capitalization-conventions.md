---
title: Convenções de maiusculas e minúsculas
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- camel-case names [.NET Framework]
- class library design guidelines [.NET Framework], capitalization
- Pascal-case names [.NET Framework]
- case sensitivity, capitalization conventions
- names [.NET Framework], capitalization
ms.assetid: 4c4ea526-9203-486f-b72d-29d61c5b3c6d
caps.latest.revision: 16
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 248a787c8858d62e77725d159e9826fabfa37ee1
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2018
---
# <a name="capitalization-conventions"></a>Convenções de maiusculas e minúsculas
As diretrizes neste capítulo dispor de um método simples para o uso de caso que, quando aplicadas de forma consistente, criar identificadores de tipos, membros e parâmetros de fácil leitura.  
  
## <a name="capitalization-rules-for-identifiers"></a>Regras de maiusculas e minúsculas de identificadores  
 Para diferenciar as palavras em um identificador, colocar em maiuscula a primeira letra de cada palavra no identificador. Não use sublinhados para diferenciar palavras, ou para esse fim, em qualquer lugar em identificadores. Há duas maneiras apropriadas para colocar em maiuscula identificadores, dependendo do uso do identificador:  
  
-   PascalCasing  
  
-   camelCasing  
  
 A convenção de PascalCasing, usada para todos os identificadores exceto nomes de parâmetro, explora o primeiro caractere de cada palavra (incluindo acrônimos em duas letras), conforme mostrado nos exemplos a seguir:  
  
 `PropertyDescriptor`  
 `HtmlTag`  
  
 Um caso especial é feito de duas letras acrônimos em que ambas as letras estão em maiusculas, conforme mostrado na seguinte identificador:  
  
 `IOStream`  
  
 A convenção de camelCasing, usada somente para os nomes de parâmetro, explora o primeiro caractere de cada palavra exceto a primeira palavra, conforme mostrado nos exemplos a seguir. Como o exemplo também mostra, siglas de duas letras que iniciam um identificador concatenados estão em minúsculas.  
  
 `propertyDescriptor`  
 `ioStream`  
 `htmlTag`  
  
 **FAZER ✓** usar PascalCasing para todos os membros, tipo e namespace nomes públicos consiste em várias palavras.  
  
 **FAZER ✓** usar camelCasing para nomes de parâmetro.  
  
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
|Parâmetro|Ter|`public class Convert {` <br />  `public static int ToInt32(string value);` <br /> `}`|  
  
## <a name="capitalizing-compound-words-and-common-terms"></a>Palavras compostas de maiusculas e termos comuns  
 A maioria dos termos compostos são tratados como palavras individuais para fins de maiusculas e minúsculas.  
  
 **X não** cada palavra em palavras compostas de forma fechada chamadas em maiuscula.  
  
 Esses são gravadas como uma única palavra, como ponto de extremidade de palavras compostas. Para fins de diretrizes de maiusculas e minúsculas, trate uma palavra composta de forma fechada como uma única palavra. Use um dicionário atual para determinar se uma palavra composta é gravada na forma fechada.  
  
|Pascal|Ter|Não|  
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
 Idiomas que podem ser executados no CLR não são necessários para dar suporte a diferenciação de maiusculas e minúsculas, embora alguns fazer. Mesmo se o seu idioma oferece suporte a ele, outros idiomas que podem acessar a estrutura não. Quaisquer APIs que são acessíveis, portanto, não pode depender caso sozinho para distinguir entre os dois nomes no mesmo contexto.  
  
 **X não** suponha que todas as linguagens de programação diferenciam maiusculas de minúsculas. Eles não são. Nomes não podem diferir somente maiusculas e minúsculas.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*  
  
 *Reimpressas pela permissão de Pearson educação, Inc. de [diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicados 22 de outubro de 2008, Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*  
  
## <a name="see-also"></a>Consulte também  
 [Diretrizes de design do Framework](../../../docs/standard/design-guidelines/index.md)  
 [Diretrizes de nomenclatura](../../../docs/standard/design-guidelines/naming-guidelines.md)
