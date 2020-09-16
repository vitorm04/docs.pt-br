---
title: Diretiva x:FieldModifier
ms.date: 03/30/2017
helpviewer_keywords:
- FieldModifier attribute in XAML [XAML Services]
- x:FieldModifier attribute [XAML Services]
- XAML [XAML Services], x:FieldModifier attribute
ms.assetid: ed427cd4-2f35-4d24-bd2f-0fa7b71ec248
ms.openlocfilehash: 4e67a6dac49b8d6a7d316526f99a1519b08fd68b
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90554469"
---
# <a name="xfieldmodifier-directive"></a>Diretiva x:FieldModifier
Modifica o comportamento de compilação XAML para que os campos de referências a objetos nomeados sejam definidos com <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> acesso em vez do <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> comportamento padrão.

## <a name="xaml-attribute-usage"></a>Uso do Atributo XAML

```xaml
<object x:FieldModifier="Public".../>
```

## <a name="xaml-values"></a>Valores XAML

|||
|-|-|
|*Pública*|A cadeia de caracteres exata que você passa para especificar <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> versus <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> varia, dependendo da linguagem de programação code-behind usada. Consulte Observações.|

## <a name="dependencies"></a>Dependências

 Se uma produção XAML usar `x:FieldModifier` em qualquer lugar, o elemento raiz dessa produção XAML deverá declarar uma [diretiva x:Class](xclass-directive.md).

## <a name="remarks"></a>Comentários

`x:FieldModifier` Não é relevante para declarar o nível de acesso geral de uma classe ou seus membros. Ele é relevante apenas para o comportamento de processamento XAML quando um determinado objeto XAML que faz parte de uma produção XAML é processado e torna-se um objeto potencialmente acessível no grafo de objeto de um aplicativo. Por padrão, a referência de campo para tal objeto é mantida privada, o que impede que os consumidores de controle modifiquem o gráfico de objetos diretamente. Em vez disso, os consumidores de controle devem modificar o grafo de objeto usando padrões padrão habilitados por modelos de programação, como ao obter a raiz do layout, as coleções de elementos filho, as propriedades públicas dedicadas e assim por diante.

O valor do `x:FieldModifier` atributo varia de acordo com a linguagem de programação e sua finalidade pode variar em estruturas específicas. A cadeia de caracteres a ser usada depende de como cada idioma implementa seu <xref:System.CodeDom.Compiler.CodeDomProvider> e os conversores de tipo que ele retorna para definir os significados para <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> e e <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> se esse idioma diferencia maiúsculas de minúsculas.

- Para o C#, a cadeia de caracteres a ser passada para designar <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> é `public` .

- Para o Microsoft Visual Basic .NET, a cadeia de caracteres a ser passada para designar <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> é `Public` .

- Para C++/CLI, não existem destinos para XAML no momento; Portanto, a cadeia de caracteres a ser passada é indefinida.

Você também pode especificar <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> ( `internal` em C#, `Friend` em Visual Basic), mas especificar <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> é incomum porque `NotPublic` , como o comportamento já é o padrão.

<xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> é o comportamento padrão porque não é frequente que o código fora do assembly que compilou o XAML precise de acesso a um elemento criado por XAML. A arquitetura de segurança do WPF junto com o comportamento de compilação XAML não declarará campos que armazenam instâncias de elemento como públicas, a menos que você defina especificamente o `x:FieldModifier` para permitir acesso público.

`x:FieldModifier` é relevante apenas para elementos com uma [diretiva x:Name](xname-directive.md) porque esse nome é usado para referenciar o campo depois que ele é público.

Por padrão, a classe parcial para o elemento raiz é pública; no entanto, você pode torná-lo não público usando a [diretiva x:ClassModifier](xclassmodifier-directive.md). A [diretiva x:ClassModifier](xclassmodifier-directive.md) também afeta o nível de acesso da instância da classe de elemento raiz. Você pode colocar ambos `x:Name` e `x:FieldModifier` no elemento raiz, mas isso faz apenas uma cópia de campo público do elemento raiz, com o nível de acesso verdadeiro de classe de elemento raiz ainda controlado pela [diretiva x:ClassModifier](xclassmodifier-directive.md).

## <a name="see-also"></a>Confira também

- [XAML e classes personalizadas para WPF](/dotnet/desktop/wpf/advanced/xaml-and-custom-classes-for-wpf)
- [Code-behind e XAML no WPF](/dotnet/desktop/wpf/advanced/code-behind-and-xaml-in-wpf)
- [Diretiva x:Name](xname-directive.md)
- [Criando um aplicativo WPF (WPF)](/dotnet/desktop/wpf/app-development/building-a-wpf-application-wpf)
- [Diretiva x:ClassModifier](xclassmodifier-directive.md)
