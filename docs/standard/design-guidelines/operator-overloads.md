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
ms.openlocfilehash: 0999e94c8d77396b237522e89c51206ce1226718
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400564"
---
# <a name="operator-overloads"></a>Sobrecargas de operador
As sobrecargas dos operadores permitem que os tipos de estruturas apareçam como se fossem primitivos de linguagem embutidos.

 Embora permitido e útil em algumas situações, as sobrecargas do operador devem ser usadas com cautela. Há muitos casos em que a sobrecarga dos operadores foi abusada, como quando os designers de estruturas começaram a usar operadores para operações que deveriam ser métodos simples. As seguintes diretrizes devem ajudá-lo a decidir quando e como usar a sobrecarga do operador.

 ❌EVITE definir sobrecargas de operadores, exceto em tipos que devem parecer tipos primitivos (embutidos).

 ✔️ CONSIDEREm definir sobrecargas de operadores em um tipo que deve parecer um tipo primitivo.

 Por <xref:System.String?displayProperty=nameWithType> exemplo, `operator==` `operator!=` tem e definiu.

 ✔️ DO definem sobrecargas de operadores em <xref:System.Decimal?displayProperty=nameWithType>estruturas que representam números (como ).

 ❌NÃO seja fofo ao definir sobrecargas do operador.

 A sobrecarga do operador é útil nos casos em que é imediatamente óbvio qual será o resultado da operação. Por exemplo, faz sentido ser capaz <xref:System.DateTime> de `DateTime` subtrair <xref:System.TimeSpan>um do outro e obter um . No entanto, não é apropriado usar o operador lógico do sindicato para sociar duas consultas de banco de dados, ou usar o operador de turno para escrever para um fluxo.

 ❌NÃO forneça sobrecargas ao operador, a menos que pelo menos uma das operações seja do tipo que define a sobrecarga.

 ✔️ os operadores de sobrecarga DO de forma simétrica.

 Por exemplo, se `operator==`você sobrecarregar o `operator!=`, você também deve sobrecarregar o . Da mesma forma, `operator<`se você sobrecarregar `operator>`o , você também deve sobrecarregar o , e assim por diante.

 ✔️ considerem fornecer métodos com nomes amigáveis que correspondam a cada operador sobrecarregado.

 Muitos idiomas não suportam sobrecarga de operadores. Por essa razão, recomenda-se que os tipos que sobrecarregam os operadores incluam um método secundário com um nome específico de domínio apropriado que forneça funcionalidade equivalente.

 A tabela a seguir contém uma lista de operadores e os nomes de métodos amigáveis correspondentes.

|Símbolo do operador C#|Nome de metadados|Nome amigável|
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

### <a name="overloading-operator-"></a>Operador de sobrecarga ==
 Sobrecarga `operator ==` é bastante complicado. A semântica do operador precisa ser compatível <xref:System.Object.Equals%2A?displayProperty=nameWithType>com vários outros membros, tais como .

### <a name="conversion-operators"></a>Operadores de conversão
 Os operadores de conversão são operadores não ários que permitem a conversão de um tipo para outro. Os operadores devem ser definidos como membros estáticos no operato ou no tipo de retorno. Existem dois tipos de operadores de conversão: implícito e explícito.

 ❌NÃO forneça um operador de conversão se tal conversão não for claramente esperada pelos usuários finais.

 ❌NÃO defina operadores de conversão fora do domínio de um tipo.

 Por <xref:System.Int32>exemplo, <xref:System.Double>e <xref:System.Decimal> são todos os tipos <xref:System.DateTime> numéricos, enquanto que não são. Portanto, não deve haver operador de `Double(long)` conversão `DateTime`para converter a para a . Um construtor é preferido nesse caso.

 ❌NÃO forneça um operador de conversão implícita se a conversão for potencialmente perdida.

 Por exemplo, não deve haver `Double` uma `Int32` `Double` conversão implícita de `Int32`para porque tem um alcance maior do que . Um operador de conversão explícita pode ser fornecido mesmo que a conversão seja potencialmente deficitária.

 ❌NÃO jogue exceções de moldes implícitos.

 É muito difícil para os usuários finais entenderem o que está acontecendo, porque eles podem não estar cientes de que uma conversão está ocorrendo.

 ✔️ DO <xref:System.InvalidCastException?displayProperty=nameWithType> jogar se uma chamada para um operador de elenco resultar em uma conversão de perda e o contrato do operador não permite conversões de perdas.

 *Partes © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*

 *Reimpresso com permissão da Pearson Education, Inc. das [Diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicado em 22 de outubro de 2008 por Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*

## <a name="see-also"></a>Confira também

- [Diretrizes de design de membro](../../../docs/standard/design-guidelines/member.md)
- [Diretrizes de design do Framework](../../../docs/standard/design-guidelines/index.md)
