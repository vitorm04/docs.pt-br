---
title: Diretiva x:FieldModifier
ms.date: 03/30/2017
helpviewer_keywords:
- FieldModifier attribute in XAML [XAML Services]
- x:FieldModifier attribute [XAML Services]
- XAML [XAML Services], x:FieldModifier attribute
ms.assetid: ed427cd4-2f35-4d24-bd2f-0fa7b71ec248
ms.openlocfilehash: 3e104b4c464d545e048f29901701c1c3dbb68229
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071524"
---
# <a name="xfieldmodifier-directive"></a>Diretiva x:FieldModifier
Modifica o comportamento de compilação XAML para que <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> os campos <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> para referências de objeto saem definidos com acesso em vez do comportamento padrão.

## <a name="xaml-attribute-usage"></a>Uso do Atributo XAML

```xaml
<object x:FieldModifier="Public".../>
```

## <a name="xaml-values"></a>Valores XAML

|||
|-|-|
|*Pública*|A seqüência exata <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> que você passa para especificar versus varia, dependendo da linguagem de programação por trás do código que é usada. Consulte Observações.|

## <a name="dependencies"></a>Dependências

 Se uma produção XAML for em `x:FieldModifier` qualquer lugar, o elemento raiz dessa produção XAML deve declarar uma diretiva [x:Class](xclass-directive.md).

## <a name="remarks"></a>Comentários

`x:FieldModifier`não é relevante para declarar o nível geral de acesso de uma classe ou de seus membros. É relevante apenas para o comportamento de processamento XAML quando um objeto XAML específico que faz parte de uma produção XAML é processado e se torna um objeto potencialmente acessível no gráfico de objetos de um aplicativo. Por padrão, a referência de campo para tal objeto é mantida privada, o que impede que os consumidores de controle modifiquem diretamente o gráfico do objeto. Em vez disso, espera-se que os consumidores de controle modifiquem o gráfico do objeto usando padrões padrão que são habilitados por modelos de programação, como a obtenção da raiz do layout, as coleções de elementos infantis, as propriedades públicas dedicadas e assim por diante.

O valor `x:FieldModifier` para o atributo varia de acordo com a linguagem de programação, e seu propósito pode variar em estruturas específicas. A seqüência de string a ser <xref:System.CodeDom.Compiler.CodeDomProvider> usada depende de como cada idioma <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> implementa o seu e os conversores do tipo que ele retorna para definir os significados para e <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>, e se essa linguagem é sensível a casos.

- Para C#, a string <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> para `public`passar para designar é .

- Para o Microsoft Visual Basic .NET, <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> `Public`a seqüência de transferências para designar é .

- Para C++/CLI, não existem metas para XAML atualmente; portanto, a string para passar é indefinida.

Você também <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> pode`internal` especificar `Friend` (em C#, <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> no Visual `NotPublic` Basic), mas especificar é incomum porque como o comportamento já é o padrão.

<xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>é o comportamento padrão porque é pouco freqüente que o código fora do conjunto que compilou o XAML precisa de acesso a um elemento criado pelo XAML. A arquitetura de segurança do WPF, juntamente com o comportamento de compilação `x:FieldModifier` XAML, não declarará campos que armazenam instâncias de elementos como públicos, a menos que você defina especificamente o para permitir o acesso público.

`x:FieldModifier`só é relevante para elementos com uma [Diretiva x:Nome](xname-directive.md) porque esse nome é usado para referenciar o campo depois que ele é público.

Por padrão, a classe parcial para o elemento raiz é pública; no entanto, você pode torná-lo não público usando a [diretiva x:ClassModifier](xclassmodifier-directive.md). A [diretiva x:ClassModifier](xclassmodifier-directive.md) também afeta o nível de acesso da instância da classe elemento raiz. Você pode `x:Name` colocar `x:FieldModifier` ambos e no elemento raiz, mas isso só faz uma cópia de campo público do elemento raiz, com o nível de acesso de classe de elemento raiz real ainda controlado por [x:Diretiva ClassModifier](xclassmodifier-directive.md).

## <a name="see-also"></a>Confira também

- [XAML e classes personalizadas para WPF](../../framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md)
- [Code-behind e XAML no WPF](../../framework/wpf/advanced/code-behind-and-xaml-in-wpf.md)
- [Diretiva x:Name](xname-directive.md)
- [Construindo um WPF Application (WPF)](../../framework/wpf/app-development/building-a-wpf-application-wpf.md)
- [Diretiva x:ClassModifier](xclassmodifier-directive.md)
