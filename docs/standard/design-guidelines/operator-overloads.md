---
title: Sobrecargas de operador
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- operators [.NET Framework], overloads
- names [.NET Framework], overloaded operators
- member design guidelines, operators
- overloaded operators
ms.assetid: 37585bf2-4c27-4dee-849a-af70e3338cc1
author: KrzysztofCwalina
ms.openlocfilehash: d1b9d8bc1f5f6f83a50dbd798894f94937320d2b
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53152130"
---
# <a name="operator-overloads"></a>Sobrecargas de operador
Sobrecargas de operador permitem que os tipos de framework apareçam como se fossem primitivos de linguagem internas.  
  
 Embora seja permitido e úteis em algumas situações, sobrecargas de operador devem ser usadas com cuidado. Há muitos casos em que operador sobrecarga tem foi violada, como quando os designers do framework iniciado a usar os operadores para operações que devem ser métodos simples. As diretrizes a seguir devem ajudá-lo a decidir quando e como usar sobrecarga de operador.  
  
 **X AVOID** definindo sobrecargas de operador, exceto em tipos que devem se parecer com os tipos primitivos (internos).  
  
 **✓ CONSIDER** definindo sobrecargas de operador em um tipo que deve se parecer com um tipo primitivo.  
  
 Por exemplo, <xref:System.String?displayProperty=nameWithType> tem `operator==` e `operator!=` definido.  
  
 **✓ DO** definir sobrecargas de operador em estruturas que representam números (como <xref:System.Decimal?displayProperty=nameWithType>).  
  
 **X DO NOT** ser bonita ao definir sobrecargas de operador.  
  
 Sobrecarga de operador é útil em casos em que ela é imediatamente óbvio qual será o resultado da operação. Por exemplo, faz sentido conseguir subtraia um <xref:System.DateTime> de outro `DateTime` e obter um <xref:System.TimeSpan>. No entanto, não é apropriado usar o operador de união lógico para consultas união de dois bancos de dados ou usar o operador de deslocamento para gravar em um fluxo.  
  
 **X DO NOT** fornecer sobrecargas de operador, a menos que pelo menos um dos operandos é do tipo que define a sobrecarga.  
  
 **✓ DO** sobrecarregar os operadores de forma simétrica.  
  
 Por exemplo, se você sobrecarregar o `operator==`, você também deve sobrecarregar o `operator!=`. Da mesma forma, se você sobrecarregar o `operator<`, você também deve sobrecarregar o `operator>`e assim por diante.  
  
 **✓ CONSIDER** fornecer métodos com nomes amigáveis que correspondem a cada operador sobrecarregado.  
  
 Muitas linguagens não suportam sobrecarga de operador. Por esse motivo, é recomendável que os tipos que sobrecarregam os operadores incluem um método secundário com um nome específico do domínio apropriado que fornece a funcionalidade equivalente.  
  
 A tabela a seguir contém uma lista de operadores e os nomes amigáveis de método correspondentes.  
  
|Símbolo do operador do c#|Nome de metadados|Nome Amigável|  
|-------------------------|-------------------|-------------------|  
|`N/A`|`op_Implicit`|`To<TypeName>/From<TypeName>`|  
|`N/A`|`op_Explicit`|`To<TypeName>/From<TypeName>`|  
|`+ (binary)`|`op_Addition`|`Add`|  
|`- (binary)`|`op_Subtraction`|`Subtract`|  
|`* (binary)`|`op_Multiply`|`Multiply`|  
|`/`|`op_Division`|`Divide`|  
|`%`|`op_Modulus`|`Mod or Remainder`|  
|`^`|`op_ExclusiveOr`|`Xor`|  
|`& (binary)`|`op_BitwiseAnd`|`BitwiseAnd`|  
|<code>&#124;</code>|`op_BitwiseOr`|`BitwiseOr`|  
|`&&`|`op_LogicalAnd`|`And`|  
|<code>&#124;&#124;</code>|`op_LogicalOr`|`Or`|  
|`=`|`op_Assign`|`Assign`|  
|`<<`|`op_LeftShift`|`LeftShift`|  
|`>>`|`op_RightShift`|`RightShift`|  
|`N/A`|`op_SignedRightShift`|`SignedRightShift`|  
|`N/A`|`op_UnsignedRightShift`|`UnsignedRightShift`|  
|`==`|`op_Equality`|`Equals`|  
|`!=`|`op_Inequality`|`Equals`|  
|`>`|`op_GreaterThan`|`CompareTo`|  
|`<`|`op_LessThan`|`CompareTo`|  
|`>=`|`op_GreaterThanOrEqual`|`CompareTo`|  
|`<=`|`op_LessThanOrEqual`|`CompareTo`|  
|`*=`|`op_MultiplicationAssignment`|`Multiply`|  
|`-=`|`op_SubtractionAssignment`|`Subtract`|  
|`^=`|`op_ExclusiveOrAssignment`|`Xor`|  
|`<<=`|`op_LeftShiftAssignment`|`LeftShift`|  
|`%=`|`op_ModulusAssignment`|`Mod`|  
|`+=`|`op_AdditionAssignment`|`Add`|  
|`&=`|`op_BitwiseAndAssignment`|`BitwiseAnd`|  
|<code>&#124;=</code>|`op_BitwiseOrAssignment`|`BitwiseOr`|  
|`,`|`op_Comma`|`Comma`|  
|`/=`|`op_DivisionAssignment`|`Divide`|  
|`--`|`op_Decrement`|`Decrement`|  
|`++`|`op_Increment`|`Increment`|  
|`- (unary)`|`op_UnaryNegation`|`Negate`|  
|`+ (unary)`|`op_UnaryPlus`|`Plus`|  
|`~`|`op_OnesComplement`|`OnesComplement`|  
  
### <a name="overloading-operator-"></a>Sobrecarregando o operador = =  
 Sobrecarregando `operator ==` é bastante complicado. A semântica do operador precisa ser compatível com vários outros membros, como <xref:System.Object.Equals%2A?displayProperty=nameWithType>.  
  
### <a name="conversion-operators"></a>Operadores de conversão  
 Operadores de conversão são operadores unários que permitem a conversão de um tipo para outro. Os operadores devem ser definidos como membros estáticos em operando ou o tipo de retorno. Há dois tipos de operadores de conversão: implícitas e explícitas.  
  
 **X DO NOT** fornecer um operador de conversão se tal conversão não é esperado claramente pelos usuários finais.  
  
 **X DO NOT** definir operadores de conversão fora do domínio do tipo.  
  
 Por exemplo, <xref:System.Int32>, <xref:System.Double>, e <xref:System.Decimal> são todos os tipos numéricos, enquanto <xref:System.DateTime> não é. Portanto, não deve haver nenhum operador de conversão para converter um `Double(long)` para um `DateTime`. Um construtor é preferido nesse caso.  
  
 **X DO NOT** fornecer um operador de conversão implícita, se a conversão é potencialmente com perdas.  
  
 Por exemplo, não deve haver uma conversão implícita da `Double` à `Int32` porque `Double` tem um intervalo maior que `Int32`. Um operador de conversão explícita pode ser fornecido, mesmo se a conversão é potencialmente com perdas.  
  
 **X DO NOT** lançam exceções de conversões implícitas.  
  
 É muito difícil para os usuários finais entender o que está acontecendo, pois eles podem não estar cientes de que uma conversão está ocorrendo.  
  
 **✓ DO** gerar <xref:System.InvalidCastException?displayProperty=nameWithType> se uma chamada para um operador de conversão resulta em uma conversão de perdas e o contrato do operador não permite conversões com perdas.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*  
  
 *Reimpresso com permissão da Pearson Education, Inc. de [as diretrizes de Design do Framework: As convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicados 22 de outubro de 2008 pela Addison-Wesley Professional, como parte da série de desenvolvimento do Microsoft Windows.*  
  
## <a name="see-also"></a>Consulte também

- [Diretrizes de design de membro](../../../docs/standard/design-guidelines/member.md)  
- [Diretrizes de design do Framework](../../../docs/standard/design-guidelines/index.md)
