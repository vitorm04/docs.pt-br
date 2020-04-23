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
ms.openlocfilehash: 436204774c2d59b43a77865c666aed702f7681db
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/25/2020
ms.locfileid: "82072028"
---
# <a name="xclassmodifier-directive"></a>Diretiva x:ClassModifier
Modifica o comportamento de `x:Class` compilação XAML quando também é fornecida. Especificamente, em vez `class` de criar `Public` uma parcial que tenha `x:Class` um nível de `NotPublic` acesso (o padrão), o fornecido é criado com um nível de acesso. Esse comportamento afeta o nível de acesso da classe nas assembléias geradas.

## <a name="xaml-attribute-usage"></a>Uso do Atributo XAML

```xaml
<object x:Class="namespace.classname" x:ClassModifier="NotPublic">
   ...
</object>
```

## <a name="xaml-values"></a>Valores XAML

|||
|-|-|
|*Notpublic*|A seqüência exata <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> a ser aprovada para especificar versus varia, dependendo da linguagem de programação por trás do código que você usa. Consulte Observações.|

## <a name="dependencies"></a>Dependências

[x:A classe](xclass-directive.md) também deve ser fornecida no mesmo elemento, e esse elemento deve ser o elemento raiz em uma página. Para obter mais informações, consulte [ \[\] MS-XAML Seção 4.3.1.8](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).

## <a name="remarks"></a>Comentários

O valor `x:ClassModifier` do uso do .NET XAML Services varia de acordo com a linguagem de programação. A seqüência de string a ser <xref:System.CodeDom.Compiler.CodeDomProvider> usada depende de como cada idioma <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> implementa o seu e os conversores do tipo que ele retorna para definir os significados para e <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>, e se essa linguagem é sensível a casos.

- Para C#, a string <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> para `internal`passar para designar é .

- Para o Microsoft Visual Basic .NET, <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> `Friend`a seqüência de transferências para designar é .

- Para C++/CLI, não existem alvos que suportem a compilação do XAML; portanto, o valor para passar não é especificado.

Você também <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> pode`public` especificar `Public` (em C#, no Visual Basic); no entanto, especificar <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> é <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> pouco feito porque já é o comportamento padrão.

Outros valores com restrições equivalentes ao `private` nível de acesso ao `x:ClassModifier` código do usuário, como em C#, não são <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> relevantes porque as referências de classe aninhadas não são suportadas em XAML e, portanto, o modificador tem o mesmo efeito.

## <a name="security-notes"></a>Observações sobre segurança

O nível de acesso `x:ClassModifier` declarado ainda está sujeito à interpretação por estruturas particulares e suas capacidades. O WPF inclui recursos para carregar `x:ClassModifier` e `internal`instanciar tipos onde está, se essa classe for referenciada a partir de um recurso WPF através de uma referência URI de pacote. Como consequência deste caso e potencialmente outros como ele implementado por `x:ClassModifier` outros quadros, não dependem exclusivamente de bloquear todas as tentativas de instanciação possíveis.

## <a name="see-also"></a>Confira também

- [Diretiva x:Class](xclass-directive.md)
- [Code-behind e XAML no WPF](../../framework/wpf/advanced/code-behind-and-xaml-in-wpf.md)
- [Diretiva x:FieldModifier](xfieldmodifier-directive.md)
- [Segurança (WPF)](../../framework/wpf/security-wpf.md)
- [Tipos migrados do WPF para System.Xaml](../../framework/wpf/advanced/types-migrated-from-wpf-to-system.md)
