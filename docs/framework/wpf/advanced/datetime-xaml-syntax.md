---
title: Sintaxe DateTime (XAML)
ms.date: 03/30/2017
helpviewer_keywords:
- DateTime XAML syntax [WPF], strings for
- DateTime XAML syntax [WPF], where used
- short date format [WPF], DateTime
- DateTime XAML syntax [WPF]
- DateTime XAML text [WPF]
- DateTime XAML syntax [WPF], format strings for
ms.assetid: 5901710a-609b-40c8-9d65-f0016cd9090b
ms.openlocfilehash: 36066d6b2405051a3d35befffe53af8895e26220
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964831"
---
# <a name="datetime-xaml-syntax"></a>Sintaxe DateTime (XAML)
Alguns controles, <xref:System.Windows.Controls.Calendar> como e <xref:System.Windows.Controls.DatePicker>, têm propriedades que usam o <xref:System.DateTime> tipo. Embora você normalmente especifique uma data ou horário inicial para esses controles no code-behind no tempo de execução, você poderá especificar uma data ou horário inicial na linguagem XAML. O analisador XAML WPF lida com a análise <xref:System.DateTime> de valores usando uma sintaxe de texto XAML interna. Este tópico descreve as especificidades da sintaxe <xref:System.DateTime> de texto XAML.  

<a name="where_datetime_xaml_syntax_is_used"></a>   
## <a name="when-to-use-datetime-xaml-syntax"></a>Quando usar a sintaxe DateTime (XAML)  
 A configuração das datas na linguagem XAML nem sempre é necessária e pode nem mesmo ser desejável. Por exemplo, você pode usar a <xref:System.DateTime.Now%2A?displayProperty=nameWithType> propriedade para inicializar uma data em tempo de execução, ou você pode fazer todos os ajustes de data de um calendário no code-behind com base na entrada do usuário. No entanto, há cenários em que você talvez queira embutir as datas em <xref:System.Windows.Controls.Calendar> um <xref:System.Windows.Controls.DatePicker> e em um modelo de controle. A <xref:System.DateTime> sintaxe XAML deve ser usada para esses cenários.  
  
### <a name="datetime-xaml-syntax-is-a-native-behavior"></a>A sintaxe DateTime (XAML) é um comportamento nativo  
 <xref:System.DateTime>é uma classe que é definida nas bibliotecas de classes base do CLR. Devido a como as bibliotecas de classe base se relacionam com o restante do CLR, não é possível aplicar <xref:System.ComponentModel.TypeConverterAttribute> à classe e usar um conversor de tipo para processar cadeias de caracteres do XAML e <xref:System.DateTime> convertê-las em no modelo de objeto de tempo de execução. Não há nenhuma classe `DateTimeConverter` que fornece o comportamento de conversão; o comportamento de conversão descrito neste tópico é nativo para o analisador de XAML do WPF.  
  
<a name="format_strings_for_datetime_xaml_syntax"></a>   
## <a name="format-strings-for-datetime-xaml-syntax"></a>Cadeias de caracteres de formato para obter a sintaxe DateTime (XAML)  
 Você pode especificar o formato de um <xref:System.DateTime> com uma cadeia de caracteres de formato. As cadeias de caracteres de formato formalizam a sintaxe de texto que pode ser usada para criar um valor. <xref:System.DateTime>os valores para os controles existentes do WPF geralmente usam apenas os componentes <xref:System.DateTime> de data do e não os componentes de tempo.  
  
 Ao especificar um <xref:System.DateTime> em XAML, você pode usar qualquer uma das cadeias de caracteres de formato de forma intercambiável.  
  
 Você também pode usar os formatos e as cadeias de caracteres de formato que não são mostradas especificamente neste tópico. Tecnicamente, o XAML para qualquer <xref:System.DateTime> valor especificado e, em seguida, analisado pelo analisador XAML do WPF usa uma chamada interna <xref:System.DateTime.Parse%2A?displayProperty=nameWithType>para, portanto, você pode usar qualquer cadeia <xref:System.DateTime.Parse%2A?displayProperty=nameWithType> de caracteres aceita pelo para sua entrada XAML. Para obter mais informações, consulte <xref:System.DateTime.Parse%2A?displayProperty=nameWithType>.  
  
> [!IMPORTANT]
> A sintaxe de DateTime XAML sempre `en-us` usa como <xref:System.Globalization.CultureInfo> o para sua conversão nativa. Isso não é influenciado <xref:System.Windows.FrameworkElement.Language%2A> pelo valor `xml:lang` ou valor no XAML, porque a conversão do tipo de nível de atributo XAML age sem esse contexto. Não tente interpolar as cadeias de caracteres de formato mostradas aqui devido a variações culturais, como a ordem na qual o dia e o mês aparecem. As cadeias de caracteres de formato mostradas aqui são as cadeias de caracteres de formato exato usadas durante a análise de XAML, independentemente de outras configurações de cultura.  
  
 As seções a seguir descrevem algumas das cadeias de caracteres de formato comuns <xref:System.DateTime> .  
  
### <a name="short-date-pattern-d"></a>Padrão de data abreviada ("d")  
 O seguinte mostra o formato de data abreviada <xref:System.DateTime> para um em XAML:  
  
 `M/d/YYYY`  
  
 Essa é a forma mais simples que especifica todas as informações necessárias para usos típicos por controles do WPF e não pode ser influenciada por deslocamentos de fuso horário acidentais em relação a um componente de tempo e, portanto, recomendável em outros formatos.  
  
 Por exemplo, para especificar a data do dia 1 de junho de 2010, use a seguinte cadeia de caracteres:  
  
 `3/1/2010`  
  
 Para obter mais informações, consulte <xref:System.Globalization.DateTimeFormatInfo.ShortDatePattern%2A?displayProperty=nameWithType>.  
  
### <a name="sortable-datetime-pattern-s"></a>Padrão DateTime classificável ("s")  
 O seguinte é mostrado o <xref:System.DateTime> padrão classificável em XAML:  
  
 `yyyy'-'MM'-'dd'T'HH':'mm':'ss`  
  
 Por exemplo, para especificar a data do dia 1 de junho de 2010, use a seguinte cadeia de caracteres (os componentes de tempo são todos inseridos como 0):  
  
 `2010-06-01T000:00:00`  
  
### <a name="rfc1123-pattern-r"></a>Padrão RFC1123 ("r")  
 O padrão RFC1123 é útil porque ele pode ser uma entrada de cadeia de caracteres de outros geradores de data que também usam o padrão RFC1123 por motivos invariáveis de cultura. O seguinte mostra o padrão <xref:System.DateTime> rfc1123 em XAML:  
  
 `ddd, dd MMM yyyy HH':'mm':'ss 'UTC'`  
  
 Por exemplo, para especificar a data do dia 1 de junho de 2010, use a seguinte cadeia de caracteres (os componentes de tempo são todos inseridos como 0):  
  
 `Mon, 01 Jun 2010 00:00:00 UTC`  
  
### <a name="other-formats-and-patterns"></a>Outros formatos e padrões  
 Como mencionado anteriormente, um <xref:System.DateTime> em XAML pode ser especificado como qualquer cadeia de caracteres aceitável como entrada para <xref:System.DateTime.Parse%2A?displayProperty=nameWithType>. Isso inclui outros formatos formalizados (por exemplo <xref:System.Globalization.DateTimeFormatInfo.UniversalSortableDateTimePattern%2A>) e formatos que não são formalizados como um formulário específico <xref:System.Globalization.DateTimeFormatInfo> . Por exemplo, o formulário `YYYY/mm/dd` é aceitável como entrada para <xref:System.DateTime.Parse%2A?displayProperty=nameWithType>. Este tópico não tenta descrever todos os formatos possíveis do trabalho e, como alternativa, recomenda o padrão de data abreviada como uma prática padrão.  
  
## <a name="see-also"></a>Consulte também

- [Visão geral de XAML (WPF)](xaml-overview-wpf.md)
