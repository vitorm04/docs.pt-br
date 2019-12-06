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
ms.openlocfilehash: a24277a4d5fbc4870157b6c8ba00ba71ba61e656
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74837227"
---
# <a name="xclassmodifier-directive"></a>Diretiva x:ClassModifier
Modifica o comportamento de compilação XAML quando `x:Class` também é fornecido. Especificamente, em vez de criar um `class` parcial que tenha um nível de acesso de `Public` (o padrão), o `x:Class` fornecido é criado com um nível de acesso `NotPublic`. Esse comportamento afeta o nível de acesso para a classe nos assemblies gerados.  
  
## <a name="xaml-attribute-usage"></a>Uso do Atributo XAML  
  
```xaml  
<object x:Class="namespace.classname" x:ClassModifier="NotPublic">  
   ...  
</object>  
```  
  
## <a name="xaml-values"></a>Valores XAML  
  
|||  
|-|-|  
|*NotPublic*|A cadeia de caracteres exata a ser passada para especificar <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> versus <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> varia, dependendo da linguagem de programação code-behind usada. Consulte Observações.|  
  
## <a name="dependencies"></a>Dependências  
 [x:Class](x-class-directive.md) também deve ser fornecida no mesmo elemento, e esse elemento deve ser o elemento raiz em uma página. Para obter mais informações, consulte [\[MS-XAML\] seção 4.3.1.8](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).  
  
## <a name="remarks"></a>Comentários  
 O valor de `x:ClassModifier` no uso de serviços XAML .NET Framework varia de acordo com a linguagem de programação. A cadeia de caracteres a ser usada depende de como cada idioma implementa sua <xref:System.CodeDom.Compiler.CodeDomProvider> e os conversores de tipo que ele retorna para definir os significados para <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> e <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>e se esse idioma diferencia maiúsculas de minúsculas.  
  
- Para C#, a cadeia de caracteres a ser passada para designar <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> é `internal`.  
  
- Para o Microsoft Visual Basic .NET, a cadeia de caracteres a ser passada para designar <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> é `Friend`.  
  
- Para C++/CLI, não existem destinos que dão suporte à compilação de XAML; Portanto, o valor a ser passado não é especificado.  
  
 Você também pode especificar <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> (`public` no C#`Public` Visual Basic); no entanto, a especificação de <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> é feita com pouca frequência porque <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> já é o comportamento padrão.  
  
 Outros valores com restrições de nível de acesso do código do usuário equivalentes, C#como `private` no, não são relevantes para `x:ClassModifier` porque não há suporte para referências de classes aninhadas em XAML e, portanto, o modificador de <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> tem o mesmo efeito.  
  
## <a name="security-notes"></a>Observações sobre segurança  
 O nível de acesso como declarado em `x:ClassModifier` ainda está sujeito à interpretação por estruturas específicas e seus recursos. O WPF inclui recursos para carregar e criar uma instância de tipos em que `x:ClassModifier` é `internal`, se essa classe for referenciada de um recurso do WPF por meio de uma referência de URI de pacote. Como consequência desse caso e, potencialmente, outras pessoas como ela é implementada por outras estruturas, não dependa exclusivamente de `x:ClassModifier` para bloquear todas as possíveis tentativas de instanciação.  
  
## <a name="see-also"></a>Consulte também

- [Diretiva x:Class](x-class-directive.md)
- [Code-behind e XAML no WPF](../wpf/advanced/code-behind-and-xaml-in-wpf.md)
- [Diretiva x:FieldModifier](x-fieldmodifier-directive.md)
- [Segurança (WPF)](../wpf/security-wpf.md)
- [Tipos migrados do WPF para System.Xaml](types-migrated-from-wpf-to-system-xaml.md)
