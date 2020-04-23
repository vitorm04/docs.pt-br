---
title: Diretiva x:Uid
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], localizable content attribute
- XAML [XAML Services], x:Uid attribute
- x:Uid attribute [XAML Services]
- Uid attribute [XAML Services]
ms.assetid: 81defade-483b-4a89-b76d-9b25bba34010
ms.openlocfilehash: b5b480016d2183268422dea861510c6a169ac27b
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071335"
---
# <a name="xuid-directive"></a>Diretiva x:Uid

Fornece um identificador exclusivo para elementos de marcação. Em muitos cenários, este identificador exclusivo é usado por processos e ferramentas de localização XAML.

## <a name="xaml-attribute-usage"></a>Uso do Atributo XAML

```xaml
<object x:Uid="identifier"... />
```

## <a name="xaml-values"></a>Valores XAML

|||
|-|-|
|`identifier`|Uma seqüência de string criada manualmente ou autogerada que `x:Uid` deve ser única em um arquivo quando é interpretada por um consumidor.|

## <a name="remarks"></a>Comentários

Em [MS-XAML], `x:Uid` é definido como uma diretiva. Para obter mais informações, consulte [ \[\] MS-XAML Seção 5.3.6](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).

`x:Uid`é discreta tanto `x:Name` por causa do cenário de localização XAML declarado quanto para que os identificadores utilizados para `x:Name`localização não tenham dependências das implicações do modelo de programação de . Além `x:Name` disso, é regido pelo namescope XAML; no `x:Uid` entanto, não é regido por qualquer conceito de linguagem XAML definido de aplicação da exclusividade. Os processadores XAML em um sentido amplo (processadores que não fazem parte do `x:Uid` processo de localização) não são esperados para impor a singularidade dos valores. Essa responsabilidade é conceitualmente sobre o criador dos valores. A expectativa de `x:Uid` singularidade de valores dentro de uma única fonte XAML é razoável para os consumidores dos valores, como processos ou ferramentas dedicadas de globalização. O modelo típico de `x:Uid` exclusividade é que os valores são únicos dentro de um arquivo codificado por XML que representa XAML.

Ferramentas que tenham conhecimento significativo de um esquema XAML específico podem optar por aplicar `x:Uid` apenas para cadeias localizadas verdadeiras, em vez de para todos os casos em que um valor de seqüência de texto é encontrado na marcação.

Os frameworks podem especificar uma propriedade específica em `x:Uid` seu modelo <xref:System.Windows.Markup.UidPropertyAttribute> de objeto para ser um alias aplicando o atributo ao tipo definidor. Se uma estrutura especificar uma propriedade específica, `x:Uid` não é válido especificar tanto o membro com aliasno no mesmo objeto. Se `x:Uid` ambos e o membro de suinoxidade forem especificados, a API de Serviços .NET XAML normalmente será aoferecida <xref:System.Xaml.XamlDuplicateMemberException> para este caso.

## <a name="wpf-usage-notes"></a>Notas de uso do WPF

Para obter mais informações `x:Uid` sobre o papel do processo de localização do WPF e na forma BAML de XAML, consulte [Globalização para WPF](../../framework/wpf/advanced/globalization-for-wpf.md) ou<xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A>

## <a name="see-also"></a>Confira também

- <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A>
- <xref:Microsoft.Build.Tasks.Windows.UidManager>
- [Globalização do WPF](../../framework/wpf/advanced/globalization-for-wpf.md)
