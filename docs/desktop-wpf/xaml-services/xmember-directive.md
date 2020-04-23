---
title: Diretiva x:Member
ms.date: 03/30/2017
ms.assetid: 4d8394ef-644c-4331-b6c5-be855d392980
ms.openlocfilehash: e82bb6397404ee466a12ab438585ae1898c34d1a
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071468"
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
|`className`|Nome da classe de apoio ou classe parcial para a produção xaml.|
|`memberName`|Nome do membro da propriedade que está sendo definido.|

## <a name="remarks"></a>Comentários

Na implementação do .NET XAML Services, . `x:Member`não tem um tipo direto de apoio, <xref:System.Windows.Markup.MemberDefinition> mas é suportado pela classe. Em um fluxo de nó `x:Member` XAML, um `Member`elemento é representado como um membro chamado , a partir do espaço de nome XAML. O `Member` membro possui atributos declarados pela marcação.

O significado `Name` `Type` de e não são atribuídos ao nível de Serviços .NET XAML. Eles são armazenados no fluxo inicial do nó XAML como valores de seqüência, a serem interpretados posteriormente sob as regras que podem ser impostas por estruturas específicas. O significado pode se alinhar a um nome XAML e ao significado do tipo XAML, ou pode ser válido apenas em um sistema de tipo de backup, dependendo da implementação.

Para apoiar um `x:Members` uso prático de como um meio de especificar definições de membros na marcação, os membros devem ser associados a uma classe que pode ser modificada. O modelo pretendido `x:Members` é que existe como um `x:Class`membro de um tipo que especifica um . No entanto, o mecanismo para associar tipos e membros ou para produzir definições dinâmicas de membros não é suportado no nível de Serviços .NET XAML. Isso é deixado para estruturas individuais que têm modelos de aplicativos que suportam definições de membros a partir de XAML. Normalmente, o MSBUILD constrói ações que compilam o XAML e o integram com o código-atrás ou produzem conjuntos puros de XAML para suportar esse recurso.

## <a name="xproperty-for-windows-workflow-foundation"></a>x:Propriedade para Windows Workflow Foundation

Para o Windows `x:Property` Workflow Foundation, define os membros de uma atividade personalizada composta inteiramente em XAML, ou XAML – membros dinâmicos definidos para um designer de atividades com código atrás. `x:Class`também deve ser especificado no elemento raiz da produção XAML. Isso não é um requisito no nível de Serviços XAML .NET, mas se torna um requisito quando a produção XAML é carregada pelas ações de compilação do MSBUILD que suportam atividades personalizadas e o Windows Workflow Foundation XAML em geral. O Windows Workflow Foundation não usa o nome do tipo `x:Property` `Type` XAML puro como seu valor pretendido para o atributo e, em vez disso, usa uma convenção que não está documentada aqui. Para obter mais informações, consulte [DynamicActivity Creation](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd807392(v=vs.100)).
