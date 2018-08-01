---
title: Sobrecargas de operador
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- operators [.NET Framework], overloads
- names [.NET Framework], overloaded operators
- member design guidelines, operators
- overloaded operators
ms.assetid: 37585bf2-4c27-4dee-849a-af70e3338cc1
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 747fc21aceae60e362c72391ae265e45d6f8445f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33579297"
---
# <a name="operator-overloads"></a>Sobrecargas de operador
Sobrecargas de operador permitem que os tipos de estrutura apareçam como se fossem primitivos de linguagem internas.  
  
 Embora permitido e útil em algumas situações, as sobrecargas de operador devem ser usadas com cautela. Há muitos casos, no qual operador sobrecarga tem sido seja explorada, como quando os designers do framework iniciado usar operadores para operações que devem ser métodos simples. As diretrizes a seguir devem ajudar a decidir quando e como usar sobrecarga de operador.  
  
 **X AVOID** definindo sobrecargas de operador, exceto em tipos que devem se parecer com os tipos primitivos (internos).  
  
 **✓ CONSIDER** definindo sobrecargas de operador em um tipo que deve se parecer com um tipo primitivo.  
  
 Por exemplo, <xref:System.String?displayProperty=nameWithType> tem `operator==` e `operator!=` definido.  
  
 **✓ DO** definir sobrecargas de operador em estruturas que representam números (como <xref:System.Decimal?displayProperty=nameWithType>).  
  
 **X DO NOT** ser bonita ao definir sobrecargas de operador.  
  
 Sobrecarga de operador é útil em casos em que é imediatamente óbvio qual será o resultado da operação. Por exemplo, faz sentido para poder subtrair um <xref:System.DateTime> de outro `DateTime` e obter um <xref:System.TimeSpan>. No entanto, não é apropriado usar o operador de união lógico para consultas união de dois bancos de dados ou usar o operador de deslocamento para gravar em um fluxo.  
  
 **X DO NOT** fornecer sobrecargas de operador, a menos que pelo menos um dos operandos é do tipo que define a sobrecarga.  
  
 **✓ DO** sobrecarregar os operadores de forma simétrica.  
  
 Por exemplo, se você sobrecarregar o `operator==`, você também deve sobrecarregar o `operator!=`. Da mesma forma, se você sobrecarregar o `operator<`, você também deve sobrecarregar o `operator>`, e assim por diante.  
  
 **✓ CONSIDER** fornecer métodos com nomes amigáveis que correspondem a cada operador sobrecarregado.  
  
 Muitos idiomas não dão suporte a sobrecarga de operador. Por esse motivo, é recomendável que tipos de operadores de sobrecarga incluem um método secundário com um nome específico do domínio apropriado que fornece funcionalidade equivalente.  
  
 A tabela a seguir contém uma lista de operadores e os nomes de método amigável correspondentes.  
  
|Símbolo do operador c#|Nome de metadados|Nome Amigável|  
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
  
### <a name="overloading-operator-"></a>Sobrecarga de operador = =  
 Sobrecarga `operator ==` é bastante complicada. A semântica do operador precisa ser compatível com vários membros, como <xref:System.Object.Equals%2A?displayProperty=nameWithType>.  
  
### <a name="conversion-operators"></a>Operadores de conversão  
 Operadores de conversão são operadores unários que permitem que a conversão de um tipo para outro. Os operadores devem ser definidos como membros estáticos em um operando ou o tipo de retorno. Há dois tipos de operadores de conversão: implícitas e explícitas.  
  
 **X DO NOT** fornecer um operador de conversão se tal conversão não é esperado claramente pelos usuários finais.  
  
 **X DO NOT** definir operadores de conversão fora do domínio do tipo.  
  
 Por exemplo, <xref:System.Int32>, <xref:System.Double>, e <xref:System.Decimal> são todos os tipos numéricos, enquanto <xref:System.DateTime> não é. Portanto, não deve haver nenhum operador de conversão para converter um `Double(long)` para um `DateTime`. Um construtor é preferido nesse caso.  
  
 **X DO NOT** fornecer um operador de conversão implícita, se a conversão é potencialmente com perdas.  
  
 Por exemplo, não deve haver uma conversão implícita de `Double` para `Int32` porque `Double` tem um intervalo maior que `Int32`. Um operador de conversão explícita pode ser fornecido, mesmo se a conversão é potencialmente com perdas.  
  
 **X DO NOT** lançam exceções de conversões implícitas.  
  
 É muito difícil para os usuários finais entender o que está acontecendo, porque ele podem não estar ciente de que uma conversão está ocorrendo.  
  
 **✓ DO** gerar <xref:System.InvalidCastException?displayProperty=nameWithType> se uma chamada para um operador de conversão resulta em uma conversão de perdas e o contrato do operador não permite conversões com perdas.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*  
  
 *Reimpressas pela permissão de Pearson educação, Inc. de [diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicados 22 de outubro de 2008, Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*  
  
## <a name="see-also"></a>Consulte também  
 [Diretrizes de design de membro](../../../docs/standard/design-guidelines/member.md)  
 [Diretrizes de design do Framework](../../../docs/standard/design-guidelines/index.md)
