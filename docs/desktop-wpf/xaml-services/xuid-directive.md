---
title: Diretiva x:Uid
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], localizable content attribute
- XAML [XAML Services], x:Uid attribute
- x:Uid attribute [XAML Services]
- Uid attribute [XAML Services]
ms.assetid: 81defade-483b-4a89-b76d-9b25bba34010
ms.openlocfilehash: 3de02702e6fd2be63bc2d099dad11f896b281ad1
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90543492"
---
# <a name="xuid-directive"></a>Diretiva x:Uid

Fornece um identificador exclusivo para elementos de marcação. Em muitos cenários, esse identificador exclusivo é usado por ferramentas e processos de localização XAML.

## <a name="xaml-attribute-usage"></a>Uso do Atributo XAML

```xaml
<object x:Uid="identifier"... />
```

## <a name="xaml-values"></a>Valores XAML

|||
|-|-|
|`identifier`|Uma cadeia de caracteres criada manualmente ou automaticamente que deve ser exclusiva em um arquivo quando é interpretada por um `x:Uid` consumidor.|

## <a name="remarks"></a>Comentários

Em [MS-XAML], `x:Uid` é definido como uma diretiva. Para obter mais informações, consulte [ \[ a \] seção MS-XAML 5.3.6](/previous-versions/msp-n-p/ff650760(v=pandp.10)).

`x:Uid` é discreto de `x:Name` ambos devido ao cenário de localização XAML declarado e, portanto, os identificadores que são usados para localização não têm dependências sobre as implicações do modelo de programação do `x:Name` . Além disso, `x:Name` o é regido pelo NAMESCOPE XAML; no entanto, `x:Uid` não é regido por nenhum conceito de linguagem XAML definido de imposição de exclusividade. Os processadores XAML em um sentido amplo (processadores que não fazem parte do processo de localização) não devem impor a exclusividade dos `x:Uid` valores. Essa responsabilidade é conceitualmente no originador dos valores. A expectativa de exclusividade de `x:Uid` valores em uma única fonte XAML é razoável para os consumidores dos valores, como processos ou ferramentas de globalização dedicados. O modelo de exclusividade típico é que os `x:Uid` valores são exclusivos em um arquivo codificado em XML que representa o XAML.

As ferramentas que têm um conhecimento significativo de um esquema XAML específico podem optar por se aplicar `x:Uid` somente a cadeias de caracteres localizáveis verdadeiras, em vez de para todos os casos em que um valor de cadeia de caracteres de texto é encontrado na marcação.

As estruturas podem especificar uma propriedade específica em seu modelo de objeto para ser um alias para `x:Uid` , aplicando o atributo <xref:System.Windows.Markup.UidPropertyAttribute> ao tipo de definição. Se uma estrutura especificar uma determinada propriedade, ela não será válida para especificar ambos `x:Uid` e o membro com alias no mesmo objeto. Se ambos `x:Uid` e o membro com alias forem especificados, a API de serviços XAML .net normalmente será lançada <xref:System.Xaml.XamlDuplicateMemberException> para esse caso.

## <a name="wpf-usage-notes"></a>Notas de uso do WPF

Para obter mais informações sobre a função do `x:Uid` no processo de localização do WPF e na forma de BAML do XAML, consulte [globalização para WPF](/dotnet/desktop/wpf/advanced/globalization-for-wpf) ou <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A>

## <a name="see-also"></a>Confira também

- <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A>
- <xref:Microsoft.Build.Tasks.Windows.UidManager>
- [Globalização do WPF](/dotnet/desktop/wpf/advanced/globalization-for-wpf)
