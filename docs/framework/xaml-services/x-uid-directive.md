---
title: Diretiva x:Uid
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XAML [XAML Services], localizable content attribute
- XAML [XAML Services], x:Uid attribute
- x:Uid attribute [XAML Services]
- Uid attribute [XAML Services]
ms.assetid: 81defade-483b-4a89-b76d-9b25bba34010
caps.latest.revision: "12"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.openlocfilehash: 4d49e9630b481b2daf103feabd225dd5ef0c8ca2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="xuid-directive"></a>Diretiva x:Uid
Fornece um identificador exclusivo para elementos de marcação. Em muitos cenários, este identificador exclusivo é usado por processos de localização de XAML e ferramentas.  
  
## <a name="xaml-attribute-usage"></a>Uso do Atributo XAML  
  
```xaml  
<object x:Uid="identifier"... />  
```  
  
## <a name="xaml-values"></a>Valores XAML  
  
|||  
|-|-|  
|`identifier`|Uma criada manualmente ou cadeia de caracteres gerada automaticamente que deve ser exclusiva em um arquivo quando ele é interpretado por um `x:Uid` consumidor.|  
  
## <a name="remarks"></a>Comentários  
 Em [MS-XAML] `x:Uid` é definido como uma diretiva. Para obter mais informações, consulte [ \[XAML MS\] seção 5.3.6](http://go.microsoft.com/fwlink/?LinkId=114525).  
  
 `x:Uid`é discreto de `x:Name` ambos devido o cenário de localização de XAML indicado e para que os identificadores que são usados para localização não têm dependências nas implicações de modelo de programação de `x:Name`. Além disso, `x:Name` é controlado por namescope a XAML; no entanto, `x:Uid` não é controlado por nenhum conceito de idioma definido XAML de imposição de exclusividade. Processadores XAML em um sentido mais amplo (processadores que não fazem parte do processo de localização) não deverão impor exclusividade de `x:Uid` valores. Essa responsabilidade é conceitualmente do gerador de valores. A expectativa de exclusividade de `x:Uid` valores dentro de uma única fonte XAML é razoável para os consumidores dos valores, como ferramentas ou processos de globalização dedicado. O modelo de exclusividade típica é que `x:Uid` valores são exclusivos dentro de um arquivo codificado por XML que representa o XAML.  
  
 Ferramentas que têm bastante conhecimento de um determinado esquema XAML podem optar por aplicar `x:Uid` apenas para true cadeias de caracteres localizáveis, em vez de para todos os casos em que um valor de cadeia de caracteres de texto for encontrado na marcação.  
  
 Estruturas podem especificar uma determinada propriedade em seu modelo de objeto para ser um alias para `x:Uid` aplicando o atributo <xref:System.Windows.Markup.UidPropertyAttribute> para a definição de tipo. Se uma estrutura Especifica uma propriedade em particular, não é válido para especificar ambos `x:Uid` e o membro de um alias no mesmo objeto. Se ambos os `x:Uid` e o membro de um alias for especificado, a API de serviços do .NET Framework XAML normalmente gera <xref:System.Xaml.XamlDuplicateMemberException> para este caso.  
  
## <a name="wpf-usage-notes"></a>Observações de uso do WPF  
 Para obter mais informações sobre a função do `x:Uid` no processo de localização do WPF e na forma BAML de XAML, consulte [globalização para WPF](../../../docs/framework/wpf/advanced/globalization-for-wpf.md) ou<xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A>  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A>  
 <xref:Microsoft.Build.Tasks.Windows.UidManager>  
 [Globalização para WPF](../../../docs/framework/wpf/advanced/globalization-for-wpf.md)
