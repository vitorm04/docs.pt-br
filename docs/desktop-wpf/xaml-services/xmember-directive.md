---
title: Diretiva x:Member
ms.date: 03/30/2017
ms.assetid: 4d8394ef-644c-4331-b6c5-be855d392980
ms.openlocfilehash: 1c5b26b405e574290af54b29b22fb5e19e4b6b95
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90548241"
---
# <a name="xmember-directive"></a>Diretiva x:Member
Declara um membro XAML na marcação.

## <a name="xaml-object-element-usage"></a>Uso de elemento Object do XAML

```xaml
<object x:Class="className">
  <x:Members>
    <x:Member Name="propertyName"/>
    additionalMembers
  </x:Members>
</object>
```

## <a name="xaml-values"></a>Valores XAML

|||
|-|-|
|`className`|Nome da classe de backup ou da classe parcial para a produção XAML.|
|`memberName`|Nome do membro da propriedade que está sendo definida.|

## <a name="remarks"></a>Comentários

Na implementação de serviços XAML .NET,. `x:Member` Não tem um tipo direto de backup, mas é suportado pela <xref:System.Windows.Markup.MemberDefinition> classe. Em um fluxo de nó XAML, um `x:Member` elemento é representado como um membro chamado `Member` , do namespace XAML da linguagem XAML. O membro `Member` mantém atributos como declarados pela marcação.

O significado de `Name` e `Type` não são atribuídos no nível de serviços XAML .net. Eles são armazenados no fluxo do nó XAML inicial como valores de cadeia de caracteres, para serem interpretados posteriormente sob as regras que podem ser impostas por estruturas específicas. O significado pode ser alinhado a um nome XAML e ao tipo XAML significado, ou só pode ser válido em um sistema de tipo de apoio, dependendo da implementação.

Para dar suporte a um uso prático de `x:Members` como um meio de especificar definições de membro na marcação, os membros devem ser associados a uma classe que pode ser modificada. O modelo pretendido é que `x:Members` existe como um membro de um tipo que especifica um `x:Class` . No entanto, o mecanismo para associar tipos e membros ou para produzir definições de membros dinâmicos não tem suporte no nível de serviços XAML .NET. Isso é deixado para estruturas individuais que têm modelos de aplicativo que dão suporte a definições de membro do XAML. Normalmente, as ações de compilação do MSBUILD que marcam a marcação XAML e a integram com code-behind ou geram assemblies puros de XAML são necessários para dar suporte a esse recurso.

## <a name="xproperty-for-windows-workflow-foundation"></a>x:Property para Windows Workflow Foundation

Por Windows Workflow Foundation, `x:Property` define os membros de uma atividade personalizada composta inteiramente em XAML ou membros dinâmicos definidos pelo XAML para um designer de atividade com code-behind. `x:Class` também deve ser especificado no elemento raiz da produção XAML. Isso não é um requisito no nível de serviços XAML .NET, mas se torna um requisito quando a produção XAML é carregada pelas ações de compilação do MSBUILD que dão suporte a atividades personalizadas e Windows Workflow Foundation XAML em geral. Windows Workflow Foundation não usa o nome do tipo puro XAML como seu valor pretendido para o `x:Property` `Type` atributo e, em vez disso, usa uma convenção que não está documentada aqui. Para obter mais informações, consulte [criação de DynamicActivity](/previous-versions/dotnet/netframework-4.0/dd807392(v=vs.100)).
