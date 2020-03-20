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
ms.openlocfilehash: 57b73d3b80f0392b99aacfbfac4d8709f72d52e9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186324"
---
# <a name="datetime-xaml-syntax"></a>Sintaxe DateTime (XAML)
Alguns controles, <xref:System.Windows.Controls.Calendar> como <xref:System.Windows.Controls.DatePicker>e , têm <xref:System.DateTime> propriedades que usam o tipo. Embora você normalmente especifique uma data ou horário inicial para esses controles no code-behind no tempo de execução, você poderá especificar uma data ou horário inicial na linguagem XAML. O analisador WPF XAML lida <xref:System.DateTime> com a análise de valores usando uma sintaxe de texto XAML incorporada. Este tópico descreve as especificidades da sintaxe de texto <xref:System.DateTime> XAML.  

<a name="where_datetime_xaml_syntax_is_used"></a>
## <a name="when-to-use-datetime-xaml-syntax"></a>Quando usar a sintaxe DateTime (XAML)  
 A configuração das datas na linguagem XAML nem sempre é necessária e pode nem mesmo ser desejável. Por exemplo, você <xref:System.DateTime.Now%2A?displayProperty=nameWithType> pode usar a propriedade para inicializar uma data no tempo de execução, ou você pode fazer todos os seus ajustes de data para um calendário no código atrás com base na entrada do usuário. No entanto, há cenários em que você <xref:System.Windows.Controls.Calendar> <xref:System.Windows.Controls.DatePicker> pode querer codificar datas em um modelo de controle. A <xref:System.DateTime> sintaxe XAML deve ser usada para esses cenários.  
  
### <a name="datetime-xaml-syntax-is-a-native-behavior"></a>A sintaxe DateTime (XAML) é um comportamento nativo  
 <xref:System.DateTime>é uma classe que é definida nas bibliotecas de classe base da CLR. Devido à forma como as bibliotecas de classe base se relacionam <xref:System.ComponentModel.TypeConverterAttribute> com o resto do CLR, não é possível aplicar <xref:System.DateTime> à classe e usar um conversor de tipo para processar strings de XAML e convertê-las no modelo de objeto de tempo de execução. Não há nenhuma classe `DateTimeConverter` que fornece o comportamento de conversão; o comportamento de conversão descrito neste tópico é nativo para o analisador de XAML do WPF.  
  
<a name="format_strings_for_datetime_xaml_syntax"></a>
## <a name="format-strings-for-datetime-xaml-syntax"></a>Cadeias de caracteres de formato para obter a sintaxe DateTime (XAML)  
 Você pode especificar <xref:System.DateTime> o formato de a com uma seqüência de formato. As cadeias de caracteres de formato formalizam a sintaxe de texto que pode ser usada para criar um valor. <xref:System.DateTime>os valores para os controles WPF existentes geralmente <xref:System.DateTime> usam apenas os componentes de data e não os componentes de tempo.  
  
 Ao especificar <xref:System.DateTime> um em XAML, você pode usar qualquer uma das strings de formato intercambiavelmente.  
  
 Você também pode usar os formatos e as cadeias de caracteres de formato que não são mostradas especificamente neste tópico. Tecnicamente, o XAML <xref:System.DateTime> para qualquer valor especificado e depois analisado pelo analisador WPF <xref:System.DateTime.Parse%2A?displayProperty=nameWithType>XAML usa uma chamada <xref:System.DateTime.Parse%2A?displayProperty=nameWithType> interna para, portanto, você pode usar qualquer string aceita pela sua entrada XAML. Para obter mais informações, consulte <xref:System.DateTime.Parse%2A?displayProperty=nameWithType>.  
  
> [!IMPORTANT]
> A sintaxe DateTime XAML sempre usa `en-us` como <xref:System.Globalization.CultureInfo> para sua conversão nativa. Isso não é <xref:System.Windows.FrameworkElement.Language%2A> influenciado `xml:lang` pelo valor ou valor no XAML, porque a conversão do tipo de atributo XAML age sem esse contexto. Não tente interpolar as cadeias de caracteres de formato mostradas aqui devido a variações culturais, como a ordem na qual o dia e o mês aparecem. As cadeias de caracteres de formato mostradas aqui são as cadeias de caracteres de formato exato usadas durante a análise de XAML, independentemente de outras configurações de cultura.  
  
 As seções a seguir <xref:System.DateTime> descrevem algumas das strings de formato comum.  
  
### <a name="short-date-pattern-d"></a>Padrão de data abreviada ("d")  
 A seguir, mostra o <xref:System.DateTime> formato de data curta para um em XAML:  
  
 `M/d/YYYY`  
  
 Essa é a forma mais simples que especifica todas as informações necessárias para usos típicos por controles do WPF e não pode ser influenciada por deslocamentos de fuso horário acidentais em relação a um componente de tempo e, portanto, recomendável em outros formatos.  
  
 Por exemplo, para especificar a data do dia 1 de junho de 2010, use a seguinte cadeia de caracteres:  
  
 `3/1/2010`  
  
 Para obter mais informações, consulte <xref:System.Globalization.DateTimeFormatInfo.ShortDatePattern%2A?displayProperty=nameWithType>.  
  
### <a name="sortable-datetime-pattern-s"></a>Padrão DateTime classificável ("s")  
 A seguir, mostra <xref:System.DateTime> o padrão classificável em XAML:  
  
 `yyyy'-'MM'-'dd'T'HH':'mm':'ss`  
  
 Por exemplo, para especificar a data do dia 1 de junho de 2010, use a seguinte cadeia de caracteres (os componentes de tempo são todos inseridos como 0):  
  
 `2010-06-01T000:00:00`  
  
### <a name="rfc1123-pattern-r"></a>Padrão RFC1123 ("r")  
 O padrão RFC1123 é útil porque ele pode ser uma entrada de cadeia de caracteres de outros geradores de data que também usam o padrão RFC1123 por motivos invariáveis de cultura. A seguir, mostra o padrão <xref:System.DateTime> RFC1123 em XAML:  
  
 `ddd, dd MMM yyyy HH':'mm':'ss 'UTC'`  
  
 Por exemplo, para especificar a data do dia 1 de junho de 2010, use a seguinte cadeia de caracteres (os componentes de tempo são todos inseridos como 0):  
  
 `Mon, 01 Jun 2010 00:00:00 UTC`  
  
### <a name="other-formats-and-patterns"></a>Outros formatos e padrões  
 Como dito anteriormente, um <xref:System.DateTime> em XAML pode ser especificado como <xref:System.DateTime.Parse%2A?displayProperty=nameWithType>qualquer string que seja aceitável como entrada para . Isso inclui outros formatos formalizados <xref:System.Globalization.DateTimeFormatInfo.UniversalSortableDateTimePattern%2A>(por exemplo), e formatos <xref:System.Globalization.DateTimeFormatInfo> que não são formalizados como uma forma específica. Por exemplo, `YYYY/mm/dd` o formulário é <xref:System.DateTime.Parse%2A?displayProperty=nameWithType>aceitável como entrada para . Este tópico não tenta descrever todos os formatos possíveis do trabalho e, como alternativa, recomenda o padrão de data abreviada como uma prática padrão.  
  
## <a name="see-also"></a>Confira também

- [Visão geral xaml (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
