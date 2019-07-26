---
title: Diretiva x:FieldModifier
ms.date: 03/30/2017
helpviewer_keywords:
- FieldModifier attribute in XAML [XAML Services]
- x:FieldModifier attribute [XAML Services]
- XAML [XAML Services], x:FieldModifier attribute
ms.assetid: ed427cd4-2f35-4d24-bd2f-0fa7b71ec248
ms.openlocfilehash: 646ad1ca99d83f9fb2994f3c394eca27a60c0eac
ms.sourcegitcommit: 4b9c2d893b45d47048c6598b4182ba87759b1b59
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/25/2019
ms.locfileid: "68484721"
---
# <a name="xfieldmodifier-directive"></a>Diretiva x:FieldModifier
Modifica o comportamento de compilação XAML para que os <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> campos de referências a objetos nomeados sejam definidos com acesso em vez do comportamento padrão.  
  
## <a name="xaml-attribute-usage"></a>Uso do Atributo XAML  
  
```xaml  
<object x:FieldModifier="Public".../>  
```  
  
## <a name="xaml-values"></a>Valores XAML  
  
|||  
|-|-|  
|*Público*|A cadeia de caracteres exata que você <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> passa <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> para especificar versus varia, dependendo da linguagem de programação code-behind usada. Consulte Observações.|  
  
## <a name="dependencies"></a>Dependências  
 Se uma produção XAML usar `x:FieldModifier` em qualquer lugar, o elemento raiz dessa produção XAML deverá declarar uma [diretiva x:Class](x-class-directive.md).  
  
## <a name="remarks"></a>Comentários  
 `x:FieldModifier`Não é relevante para declarar o nível de acesso geral de uma classe ou seus membros. Ele é relevante apenas para o comportamento de processamento XAML quando um determinado objeto XAML que faz parte de uma produção XAML é processado e torna-se um objeto potencialmente acessível no grafo de objeto de um aplicativo. Por padrão, a referência de campo para tal objeto é mantida privada, o que impede que os consumidores de controle modifiquem o gráfico de objetos diretamente. Em vez disso, os consumidores de controle devem modificar o grafo de objeto usando padrões padrão habilitados por modelos de programação, como ao obter a raiz do layout, as coleções de elementos filho, as propriedades públicas dedicadas e assim por diante.  
  
 O valor `x:FieldModifier` do atributo varia de acordo com a linguagem de programação e sua finalidade pode variar em estruturas específicas. A cadeia de caracteres a ser usada depende de como cada <xref:System.CodeDom.Compiler.CodeDomProvider> idioma implementa seu e os conversores de tipo que ele retorna para <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> definir <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>os significados para e e se esse idioma diferencia maiúsculas de minúsculas.  
  
- Para C#, a cadeia de caracteres a ser passada <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> para `public`designar é.  
  
- Para o Microsoft Visual Basic .net, a cadeia de caracteres a ser <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> passada `Public`para designar é.  
  
- Para C++a/CLI, não existem destinos para XAML no momento; Portanto, a cadeia de caracteres a ser passada é indefinida.  
  
 Você também pode especificar <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> (`internal` in C#, `Friend` in Visual Basic), mas <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> especificar é incomum `NotPublic` porque, como o comportamento já é o padrão.  
  
 <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>é o comportamento padrão porque não é frequente que o código fora do assembly que compilou o XAML precise de acesso a um elemento criado por XAML. A arquitetura de segurança do WPF junto com o comportamento de compilação XAML não declarará campos que armazenam instâncias de elemento como `x:FieldModifier` públicas, a menos que você defina especificamente o para permitir acesso público.  
  
 `x:FieldModifier`é relevante apenas para elementos com uma [diretiva x:Name](x-name-directive.md) porque esse nome é usado para referenciar o campo depois que ele é público.  
  
 Por padrão, a classe parcial para o elemento raiz é pública; no entanto, você pode torná-lo não público usando a [diretiva x:ClassModifier](x-classmodifier-directive.md). A [diretiva x:ClassModifier](x-classmodifier-directive.md) também afeta o nível de acesso da instância da classe de elemento raiz. Você pode colocar ambos `x:Name` e `x:FieldModifier` no elemento raiz, mas isso faz apenas uma cópia de campo público do elemento raiz, com o nível de acesso verdadeiro de classe de elemento raiz ainda controlado pela [diretiva x:ClassModifier](x-classmodifier-directive.md).  
  
## <a name="see-also"></a>Consulte também

- [XAML e classes personalizadas para WPF](../wpf/advanced/xaml-and-custom-classes-for-wpf.md)
- [Code-behind e XAML no WPF](../wpf/advanced/code-behind-and-xaml-in-wpf.md)
- [Diretiva x:Name](x-name-directive.md)
- [Como compilar um aplicativo WPF (WPF)](../wpf/app-development/building-a-wpf-application-wpf.md)
- [Diretiva x:ClassModifier](x-classmodifier-directive.md)
