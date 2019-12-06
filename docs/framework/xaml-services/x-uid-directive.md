---
title: Diretiva x:Uid
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], localizable content attribute
- XAML [XAML Services], x:Uid attribute
- x:Uid attribute [XAML Services]
- Uid attribute [XAML Services]
ms.assetid: 81defade-483b-4a89-b76d-9b25bba34010
ms.openlocfilehash: 32cfd9ab0cf6037c731b619e81a7504ac92d5fb9
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74837175"
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
|`identifier`|Uma cadeia de caracteres criada manualmente ou automaticamente que deve ser exclusiva em um arquivo quando é interpretada por um consumidor de `x:Uid`.|  
  
## <a name="remarks"></a>Comentários  
 Em [MS-XAML], `x:Uid` é definido como uma diretiva. Para obter mais informações, consulte [\[MS-XAML\] seção 5.3.6](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).  
  
 `x:Uid` é discreta do `x:Name` devido ao cenário de localização XAML declarado e, portanto, os identificadores que são usados para localização não têm dependências das implicações do modelo de programação de `x:Name`. Além disso, `x:Name` é governada pelo namescope XAML; no entanto, `x:Uid` não é governada por qualquer conceito de aplicação de exclusividade definido pela linguagem XAML. Os processadores XAML em um sentido amplo (processadores que não fazem parte do processo de localização) não devem impor a exclusividade dos valores de `x:Uid`. Essa responsabilidade é conceitualmente no originador dos valores. A expectativa de exclusividade dos valores de `x:Uid` dentro de uma única fonte XAML é razoável para os consumidores dos valores, como ferramentas ou processos de globalização dedicados. O modelo de exclusividade típico é que `x:Uid` valores são exclusivos em um arquivo codificado em XML que representa o XAML.  
  
 As ferramentas que têm um conhecimento significativo de um esquema XAML específico podem optar por aplicar `x:Uid` apenas para cadeias de caracteres localizáveis verdadeiras, em vez de para todos os casos em que um valor de cadeia de caracteres de texto é encontrado na marcação.  
  
 As estruturas podem especificar que uma propriedade específica em seu modelo de objeto seja um alias para `x:Uid` aplicando o atributo <xref:System.Windows.Markup.UidPropertyAttribute> ao tipo de definição. Se uma estrutura especificar uma determinada propriedade, ela não será válida para especificar `x:Uid` e o membro com alias no mesmo objeto. Se ambos `x:Uid` e o membro com alias forem especificados, a API de serviços XAML .NET Framework normalmente lançará <xref:System.Xaml.XamlDuplicateMemberException> para esse caso.  
  
## <a name="wpf-usage-notes"></a>Observações de uso do WPF  
 Para obter mais informações sobre a função de `x:Uid` no processo de localização do WPF e na forma de BAML do XAML, consulte [globalização para WPF](../wpf/advanced/globalization-for-wpf.md) ou <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A>  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A>
- <xref:Microsoft.Build.Tasks.Windows.UidManager>
- [Globalização para WPF](../wpf/advanced/globalization-for-wpf.md)
