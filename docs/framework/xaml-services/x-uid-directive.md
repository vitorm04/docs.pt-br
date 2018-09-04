---
title: Diretiva x:Uid
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], localizable content attribute
- XAML [XAML Services], x:Uid attribute
- x:Uid attribute [XAML Services]
- Uid attribute [XAML Services]
ms.assetid: 81defade-483b-4a89-b76d-9b25bba34010
ms.openlocfilehash: 7075f8258e617d2d13d4585fdd5fb7aefaa50664
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43528382"
---
# <a name="xuid-directive"></a>Diretiva x:Uid
Fornece um identificador exclusivo para elementos de marcação. Em muitos cenários, este identificador exclusivo é usado por ferramentas e processos de localização do XAML.  
  
## <a name="xaml-attribute-usage"></a>Uso do Atributo XAML  
  
```xaml  
<object x:Uid="identifier"... />  
```  
  
## <a name="xaml-values"></a>Valores XAML  
  
|||  
|-|-|  
|`identifier`|Uma criada manualmente ou cadeia de caracteres gerada automaticamente que deve ser exclusiva em um arquivo quando ele é interpretado por um `x:Uid` consumidor.|  
  
## <a name="remarks"></a>Comentários  
 No [MS-XAML] `x:Uid` é definido como uma diretiva. Para obter mais informações, consulte [ \[MS-XAML\] seção 5.3.6](https://go.microsoft.com/fwlink/?LinkId=114525).  
  
 `x:Uid` é discreto de `x:Name` ambos devido ao cenário de localização do XAML indicado e para que os identificadores que são usados para a localização não têm dependências quanto as implicações de modelo de programação de `x:Name`. Além disso, `x:Name` é regido pelo namescope XAML; no entanto, `x:Uid` não é controlado por nenhum conceito de linguagem definida de XAML de imposição de exclusividade. Processadores XAML em um sentido mais amplo (processadores que não fazem parte do processo de localização) não são esperados para impor exclusividade do `x:Uid` valores. Essa responsabilidade é conceitualmente do gerador de valores. A expectativa de exclusividade de `x:Uid` valores dentro de uma única fonte XAML é razoável para os consumidores dos valores, como processos de globalização dedicado ou de ferramentas. O modelo de exclusividade típico é que `x:Uid` valores são exclusivos dentro de um arquivo codificado em XML que representa o XAML.  
  
 Ferramentas que têm conhecimento significativo de um determinado esquema XAML podem optar por aplicar `x:Uid` somente para true cadeias de caracteres localizáveis, em vez de para todos os casos em que um valor de cadeia de caracteres de texto for encontrado na marcação.  
  
 Estruturas podem especificar uma propriedade específica em seu modelo de objeto para ser um alias para `x:Uid` aplicando o atributo <xref:System.Windows.Markup.UidPropertyAttribute> para a definição de tipo. Se uma estrutura Especifica uma propriedade em particular, não é válido especificar ambos `x:Uid` e o membro de um alias no mesmo objeto. Se os dois `x:Uid` e o membro com alias forem especificados, a API de serviços de XAML do .NET Framework normalmente gera <xref:System.Xaml.XamlDuplicateMemberException> para esse caso.  
  
## <a name="wpf-usage-notes"></a>Notas de uso do WPF  
 Para obter mais informações sobre a função do `x:Uid` no processo de localização do WPF e no formato BAML de XAML, consulte [globalização do WPF](../../../docs/framework/wpf/advanced/globalization-for-wpf.md) ou <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A>  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A>  
 <xref:Microsoft.Build.Tasks.Windows.UidManager>  
 [Globalização para WPF](../../../docs/framework/wpf/advanced/globalization-for-wpf.md)
