---
ms.openlocfilehash: dc733ee32184db5af59bb06e294cd73765977581
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77449539"
---
### <a name="fieldinfosetvalue-throws-exception-for-static-init-only-fields"></a>FieldInfo. SetValue gera uma exceção para campos estáticos somente de inicialização

A partir do .NET Core 3,0, uma exceção é lançada quando você tenta definir um valor em um campo estático <xref:System.Reflection.FieldAttributes.InitOnly> chamando <xref:System.Reflection.FieldInfo.SetValue%2A?displayProperty=fullName>.

#### <a name="change-description"></a>Alterar descrição

Em .NET Framework e versões do .NET Core anteriores a 3,0, você pode definir o valor de um campo estático que é constante depois que ele é inicializado ([ReadOnly C# ](~/docs/csharp/language-reference/keywords/readonly.md)) chamando <xref:System.Reflection.FieldInfo.SetValue%2A?displayProperty=fullName>. No entanto, a definição desse campo dessa forma resultou em um comportamento imprevisível com base na estrutura de destino e nas configurações de otimização.

No .NET Core 3,0 e versões posteriores, quando você chama <xref:System.Reflection.FieldInfo.SetValue%2A> em um campo estático <xref:System.Reflection.FieldAttributes.InitOnly>, uma exceção <xref:System.FieldAccessException?displayProperty=nameWithType> é lançada.

> [!TIP]
> Um campo de <xref:System.Reflection.FieldAttributes.InitOnly> é aquele que só pode ser definido no momento em que é declarado ou no construtor para a classe que a contém. Em outras palavras, é constante depois que ela é inicializada.

#### <a name="version-introduced"></a>Versão introduzida

3.0

#### <a name="recommended-action"></a>Ação recomendada

Inicializar os campos estáticos <xref:System.Reflection.FieldAttributes.InitOnly> em um construtor estático. Isso se aplica a tipos dinâmicos e não dinâmicos.

Como alternativa, você pode remover o atributo <xref:System.Reflection.FieldAttributes.InitOnly?displayProperty=nameWithType> do campo e, em seguida, chamar <xref:System.Reflection.FieldInfo.SetValue%2A?displayProperty=nameWithType>.

#### <a name="category"></a>Categoria

CoreFx

#### <a name="affected-apis"></a>APIs afetadas

- <xref:System.Reflection.FieldInfo.SetValue(System.Object,System.Object)?displayProperty=nameWithType>
- <xref:System.Reflection.FieldInfo.SetValue(System.Object,System.Object,System.Reflection.BindingFlags,System.Reflection.Binder,System.Globalization.CultureInfo)?displayProperty=nameWithType>

<!--

### Affected APIs

- `M:System.Reflection.FieldInfo.SetValue(System.Object,System.Object)`
- `M:System.Reflection.FieldInfo.SetValue(System.Object,System.Object,System.Reflection.BindingFlags,System.Reflection.Binder,System.Globalization.CultureInfo)`

-->
