---
title: Diretiva x:ClassModifier
ms.date: 03/30/2017
f1_keywords:
- xClassModifier
- x:ClassModifier
- ClassModifier
helpviewer_keywords:
- XAML [XAML Services], x:ClassModifier attribute
- x:ClassModifier attribute [XAML Services]
- ClassModifier attribute in XAML [XAML Services]
ms.assetid: ef30ab78-d334-4668-917d-c9f66c3b6aea
ms.openlocfilehash: 73732a06029cca3a4c6c6d82762d5263c5b8c955
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90544811"
---
# <a name="xclassmodifier-directive"></a>Diretiva x:ClassModifier
Modifica o comportamento de compilação XAML quando `x:Class` também é fornecido. Especificamente, em vez de criar um parcial `class` que tenha um `Public` nível de acesso (o padrão), o fornecido `x:Class` é criado com um nível de `NotPublic` acesso. Esse comportamento afeta o nível de acesso para a classe nos assemblies gerados.

## <a name="xaml-attribute-usage"></a>Uso do Atributo XAML

```xaml
<object x:Class="namespace.classname" x:ClassModifier="NotPublic">
   ...
</object>
```

## <a name="xaml-values"></a>Valores XAML

|||
|-|-|
|*Não público*|A cadeia de caracteres exata a ser passada para especificar <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> versus <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> varia, dependendo da linguagem de programação code-behind que você usa. Consulte Observações.|

## <a name="dependencies"></a>Dependências

[x:Class](xclass-directive.md) também deve ser fornecida no mesmo elemento, e esse elemento deve ser o elemento raiz em uma página. Para obter mais informações, consulte [ \[ a \] seção MS-XAML 4.3.1.8](/previous-versions/msp-n-p/ff650760(v=pandp.10)).

## <a name="remarks"></a>Comentários

O valor do `x:ClassModifier` uso dos serviços XAML .NET varia de acordo com a linguagem de programação. A cadeia de caracteres a ser usada depende de como cada idioma implementa seu <xref:System.CodeDom.Compiler.CodeDomProvider> e os conversores de tipo que ele retorna para definir os significados para <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> e e <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> se esse idioma diferencia maiúsculas de minúsculas.

- Para o C#, a cadeia de caracteres a ser passada para designar <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> é `internal` .

- Para o Microsoft Visual Basic .NET, a cadeia de caracteres a ser passada para designar <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> é `Friend` .

- Para C++/CLI, não existem destinos que dão suporte à compilação de XAML; Portanto, o valor a ser passado não é especificado.

Você também pode especificar <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> ( `public` em C#, `Public` em Visual Basic); no entanto, a especificação <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> é feita com pouca frequência porque <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> já é o comportamento padrão.

Outros valores com restrições de nível de acesso do código do usuário equivalentes, como `private` em C#, não são relevantes para o `x:ClassModifier` porque não há suporte para referências de classe aninhadas em XAML e, portanto, o <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> modificador tem o mesmo efeito.

## <a name="security-notes"></a>Observações sobre segurança

O nível de acesso como declarado em `x:ClassModifier` ainda está sujeito à interpretação por estruturas específicas e seus recursos. O WPF inclui recursos para carregar e criar uma instância de tipos onde `x:ClassModifier` está `internal` , se essa classe for referenciada de um recurso do WPF por meio de uma referência de URI pack. Como consequência desse caso e, potencialmente, outras pessoas, como as implementadas por outras estruturas, não se baseiam exclusivamente `x:ClassModifier` para bloquear todas as possíveis tentativas de instanciação.

## <a name="see-also"></a>Confira também

- [Diretiva x:Class](xclass-directive.md)
- [Code-behind e XAML no WPF](/dotnet/desktop/wpf/advanced/code-behind-and-xaml-in-wpf)
- [Diretiva x:FieldModifier](xfieldmodifier-directive.md)
- [Segurança (WPF)](/dotnet/desktop/wpf/security-wpf)
- [Tipos migrados do WPF para System.Xaml](/dotnet/desktop/wpf/advanced/types-migrated-from-wpf-to-system)
