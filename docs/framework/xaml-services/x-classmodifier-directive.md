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
ms.openlocfilehash: c3c08f61b49a6367663cf02099dda86d1a692284
ms.sourcegitcommit: 4b9c2d893b45d47048c6598b4182ba87759b1b59
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/25/2019
ms.locfileid: "68484755"
---
# <a name="xclassmodifier-directive"></a>Diretiva x:ClassModifier
Modifica o comportamento de compilação XAML `x:Class` quando também é fornecido. Especificamente, em vez de criar um `class` parcial que tenha `Public` um nível de acesso (o padrão), `x:Class` o fornecido é criado `NotPublic` com um nível de acesso. Esse comportamento afeta o nível de acesso para a classe nos assemblies gerados.  
  
## <a name="xaml-attribute-usage"></a>Uso do Atributo XAML  
  
```  
<object x:Class="namespace.classname" x:ClassModifier="NotPublic">  
   ...  
</object>  
```  
  
## <a name="xaml-values"></a>Valores XAML  
  
|||  
|-|-|  
|*NotPublic*|A cadeia de caracteres exata a ser <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> passada <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> para especificar versus varia, dependendo da linguagem de programação code-behind que você usa. Consulte Observações.|  
  
## <a name="dependencies"></a>Dependências  
 [x:Class](x-class-directive.md) também deve ser fornecida no mesmo elemento, e esse elemento deve ser o elemento raiz em uma página. Para obter mais informações, consulte [ \[a seção\] MS-XAML 4.3.1.8](https://go.microsoft.com/fwlink/?LinkId=114525).  
  
## <a name="remarks"></a>Comentários  
 O valor de `x:ClassModifier` no .NET Framework uso de serviços XAML varia de acordo com a linguagem de programação. A cadeia de caracteres a ser usada depende de como cada <xref:System.CodeDom.Compiler.CodeDomProvider> idioma implementa seu e os conversores de tipo que ele retorna para <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> definir <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>os significados para e e se esse idioma diferencia maiúsculas de minúsculas.  
  
- Para C#, a cadeia de caracteres a ser passada <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> para `internal`designar é.  
  
- Para o Microsoft Visual Basic .net, a cadeia de caracteres a ser <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> passada `Friend`para designar é.  
  
- Para C++/CLI, não existem destinos que dão suporte à compilação de XAML; Portanto, o valor a ser passado não é especificado.  
  
 Você também pode especificar <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> (`public` in C#, `Public` in Visual Basic); no entanto <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> , a especificação é feita <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> com pouca frequência porque já é o comportamento padrão.  
  
 Outros valores com restrições de nível `private` de acesso do código do usuário equivalentes, como no C#, não `x:ClassModifier` são relevantes para o porque não há suporte para referências de classe aninhadas <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> em XAML e, portanto, o modificador tem o mesmo efeito .  
  
## <a name="security-notes"></a>Observações de segurança  
 O nível de acesso como declarado `x:ClassModifier` em ainda está sujeito à interpretação por estruturas específicas e seus recursos. O WPF inclui recursos para carregar e criar uma `x:ClassModifier` instância `internal`de tipos onde está, se essa classe for referenciada de um recurso do WPF por meio de uma referência de URI pack. Como consequência desse caso e, potencialmente, outras pessoas, como as implementadas por outras estruturas, não `x:ClassModifier` se baseiam exclusivamente para bloquear todas as possíveis tentativas de instanciação.  
  
## <a name="see-also"></a>Consulte também

- [Diretiva x:Class](x-class-directive.md)
- [Code-behind e XAML no WPF](../wpf/advanced/code-behind-and-xaml-in-wpf.md)
- [Diretiva x:FieldModifier](x-fieldmodifier-directive.md)
- [Segurança (WPF)](../wpf/security-wpf.md)
- [Tipos migrados do WPF para System.Xaml](types-migrated-from-wpf-to-system-xaml.md)
