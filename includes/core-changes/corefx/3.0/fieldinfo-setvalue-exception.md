---
ms.openlocfilehash: dc733ee32184db5af59bb06e294cd73765977581
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77449539"
---
### <a name="fieldinfosetvalue-throws-exception-for-static-init-only-fields"></a>FieldInfo.SetValue lança exceção para campos estáticos e somente somente init

A partir do .NET Core 3.0, uma exceção é lançada <xref:System.Reflection.FieldAttributes.InitOnly> quando <xref:System.Reflection.FieldInfo.SetValue%2A?displayProperty=fullName>você tenta definir um valor em um campo estático, chamando .

#### <a name="change-description"></a>Descrição da alteração

Em .NET Framework e versões do .NET Core antes de 3.0, você pode definir o valor de um <xref:System.Reflection.FieldInfo.SetValue%2A?displayProperty=fullName>campo estático que é constante depois de inicializado[(readonly in C#](~/docs/csharp/language-reference/keywords/readonly.md)) chamando . No entanto, a definição desse campo dessa forma resultou em um comportamento imprevisível com base no quadro-alvo e nas configurações de otimização.

Nas versões .NET Core 3.0 <xref:System.Reflection.FieldInfo.SetValue%2A> e posteriores, quando você chama um <xref:System.Reflection.FieldAttributes.InitOnly> campo estático, uma exceção <xref:System.FieldAccessException?displayProperty=nameWithType> é lançada.

> [!TIP]
> Um <xref:System.Reflection.FieldAttributes.InitOnly> campo é aquele que só pode ser definido no momento em que é declarado ou no construtor para a classe de contenção. Em outras palavras, é constante depois de ser inicializado.

#### <a name="version-introduced"></a>Versão introduzida

3.0

#### <a name="recommended-action"></a>Ação recomendada

Inicialize estática, <xref:System.Reflection.FieldAttributes.InitOnly> campos em um construtor estático. Isso se aplica tanto aos tipos dinâmicos quanto aos não dinâmicos.

Alternativamente, você pode <xref:System.Reflection.FieldAttributes.InitOnly?displayProperty=nameWithType> remover o atributo <xref:System.Reflection.FieldInfo.SetValue%2A?displayProperty=nameWithType>do campo e, em seguida, chamar .

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
