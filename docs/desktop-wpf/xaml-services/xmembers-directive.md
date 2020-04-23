---
title: Diretiva x:Members
ms.date: 03/30/2017
ms.assetid: 155b393d-3b49-4c5a-8c9e-b3d9893af4e4
ms.openlocfilehash: c751a4f1cdea8dce7ef5165f5225ab3a825c7344
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071461"
---
# <a name="xmembers-directive"></a>Diretiva x:Members
Contém um conjunto de membros definidos na marcação, que se aplicam à classe x:classe do elemento pai.

## <a name="xaml-attribute-usage"></a>Uso do Atributo XAML

```xaml
<object x:Class="className">
<x:Members>
  oneOrMoreMembers
</x:Members
</object>
```

## <a name="xaml-values"></a>Valores XAML

|||
|-|-|
|`className`|Nome da classe de apoio ou classe parcial para a produção xaml. Consulte Observações.|
|`oneOrMoreMembers`|Um ou mais elementos de objeto que representam definições de membros. Normalmente, estes são `x:Property` elementos do objeto. Consulte Observações.|

## <a name="remarks"></a>Comentários

Na implementação do .NET XAML Services, não há `x:Members`classe de backup ou implementação de membros subjacentes para . `x:Members`é um membro XAML especial que pode existir como membro em qualquer tipo. Em um fluxo de nó `x:Members` XAML, `Members`é representado como um membro chamado , a partir do namespace xaml da linguagem XAML. O `Members` membro contém uma lista `Member` genérica de objetos somente leitura. Na marcação típica, os membros `x:Property` individuais são especificados como elementos de propriedade. `x:Property`é um tipo mais preciso especificamente para propriedades `x:Member`de tipos e é atribuído a . Para obter mais informações, consulte [x:Diretiva de propriedade](xproperty-directive.md).

Para apoiar um `x:Members` uso prático de como um meio de especificar definições de membros na marcação, os membros devem ser associados a uma classe que pode ser modificada. O modelo pretendido `x:Members` é que existe como um `x:Class`membro de um tipo que especifica um . No entanto, o mecanismo para associar tipos e membros ou para produzir definições dinâmicas de membros não é suportado no nível de Serviços .NET XAML. Isso é deixado para estruturas individuais que têm modelos de aplicativos que suportam definições de membros a partir de XAML. Normalmente, o MSBUILD constrói ações que compilam o XAML e o integram com o código-atrás ou produzem conjuntos puros de XAML para suportar esse recurso.

## <a name="xmembers-for-windows-workflow-foundation"></a>x:Membros da Windows Workflow Foundation

Para o Windows `x:Members` Workflow Foundation, contém os membros de uma atividade personalizada composta inteiramente em XAML, ou XAML – membros dinâmicos definidos para um designer de atividades com código atrás. `x:Class`também deve ser especificado no elemento raiz da produção XAML. Isso não é um requisito no nível de Serviços XAML .NET, mas se torna um requisito quando a produção XAML é carregada pelas ações de compilação do MSBUILD que suportam atividades personalizadas e o Windows Workflow Foundation XAML em geral. `x:Members`deve ser o primeiro elemento filho na marcação `x:Class`do elemento objeto que declara o .
