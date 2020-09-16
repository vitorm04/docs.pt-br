---
title: Tipos inseridos para primitivos de linguagem XML comuns
ms.date: 03/30/2017
helpviewer_keywords:
- XAML language primitives [XAML Services]
- XAML [XAML Services], built-in types
- x:String [XAML Services]
- x:TimeSpan [XAML Services]
- x:Byte [XAML Services]
- x:Double [XAML Services]
- XAML [XAML Services], types
- x:Uri [XAML Services]
- XAML built-in types [XAML Services]
- x:Int64 [XAML Services]
- x:Single [XAML Services]
- x:Int32 [XAML Services]
ms.assetid: 11de2f08-5b95-4989-b5ec-5178eb968184
ms.openlocfilehash: ec0e2a29a191d5057ce66a5f3272d00e92b01bd7
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90540023"
---
# <a name="built-in-types-for-common-xaml-language-primitives"></a>Tipos internos para primitivos comuns de linguagem XAML

O XAML 2009 apresenta suporte no nível da linguagem XAML para vários tipos de dados que são primitivos usados com frequência no Common Language Runtime (CLR) e em outras linguagens de programação. O XAML 2009 adiciona suporte para esses primitivos:,,,,,,, `x:Object` `x:Boolean` ,,,, `x:Char` `x:String` `x:Decimal` `x:Single` `x:Double` `x:Int16` `x:Int32` `x:Int64` `x:TimeSpan` `x:Uri` `x:Byte` e `x:Array`

## <a name="previous-techniques-for-language-primitives-in-xaml-markup"></a>Técnicas anteriores para primitivas de idioma na marcação XAML

 Em XAML para versões anteriores do WPF, você pode referenciar os primitivos de linguagem CLR mapeando o assembly e o namespace que continham uma classe de definição de CLR primitivo para o .NET Framework. A maioria deles está no assembly e no <xref:System> namespace mscorlib. Por exemplo, para usar <xref:System.Int32> o, você pode declarar o seguinte mapeamento (com um exemplo de uso mostrado em seguida):

```xaml
<Application xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
xmlns:sys="clr-namespace:System;assembly=mscorlib">
  <Application.Resources>
    <sys:Int32 x:Key="intMeaning">42</sys:Int32>
  </Application.Resources>
</Application>
```

## <a name="xaml-2009-language-primitives"></a>Primitivos de linguagem XAML 2009

Por convenção, os primitivos de idioma para XAML e todos os outros elementos de linguagem XAML são mostrados, incluindo o `x:` prefixo. É assim que os elementos da linguagem XAML são normalmente usados em situações reais de marcação. Essa convenção é seguida da documentação conceitual para XAML no WPF e também na especificação XAML.

### <a name="xobject"></a>x:Object

Para o backup do CLR, o `x:Object` primitivo corresponde a <xref:System.Object> .

Normalmente, esse primitivo não é usado na marcação do aplicativo, mas pode ser útil para alguns cenários, como a verificação da atribuição em um sistema de tipos XAML.

### <a name="xboolean"></a>x:Boolean

Para o backup do CLR, o `x:Boolean` primitivo corresponde a <xref:System.Boolean> .

O XAML analisa valores `x:Boolean` como não diferencia maiúsculas de minúsculas. Observe que `x:Bool` não é uma alternativa aceita. Para a definição de especificação da linguagem XAML, consulte [ \[ seções do MS-XAML \] 5.2.17 e 5.4.11](/previous-versions/msp-n-p/ff650760(v=pandp.10)).

### <a name="xchar"></a>x:Char

Para o backup do CLR, o `x:Char` primitivo corresponde a <xref:System.Char> .

Tipos de cadeia de caracteres e caracteres têm interação com a codificação geral do arquivo no nível de XML. Para a definição de especificação da linguagem XAML, consulte [ \[ seções do MS-XAML \] 5.2.7 e 5.4.1](/previous-versions/msp-n-p/ff650760(v=pandp.10)).

### <a name="xstring"></a>x:String

Para o backup do CLR, o `x:String` primitivo corresponde a <xref:System.String> .

Tipos de cadeia de caracteres e caracteres têm interação com a codificação geral do arquivo no nível de XML. Para a definição de especificação da linguagem XAML, consulte as [ \[ seções do MS-XAML \] 5.2.6](/previous-versions/msp-n-p/ff650760(v=pandp.10)).

### <a name="xdecimal"></a>x:Decimal

Para o backup do CLR, o `x:Decimal` primitivo corresponde a <xref:System.Decimal> .

A análise de XAML é feita de forma inerente em `en-US` Culture. Em `en-US` Culture, o separador correto para os componentes de um decimal é sempre um ponto ( `.` ), independentemente das configurações de cultura do ambiente de desenvolvimento, ou do destino de cliente eventual em que o XAML é carregado em tempo de execução.

Para a definição de especificação da linguagem XAML, consulte [ \[ seções do MS-XAML \] 5.2.14 e 5.4.8](/previous-versions/msp-n-p/ff650760(v=pandp.10)).

### <a name="xsingle"></a>x:Single

Para o backup do CLR, o `x:Single` primitivo corresponde a <xref:System.Single> .

Além dos valores numéricos, a sintaxe de texto para `x:Single` também permite os tokens `Infinity` , `-Infinity` e `NaN` . Esses tokens são tratados como diferenciando maiúsculas de minúsculas.

`x:Single` pode dar suporte a valores no formato de notação científica, se o primeiro caractere na sintaxe de texto for `e` ou `E` .

Para a definição de especificação da linguagem XAML, consulte [ \[ seções do MS-XAML \] 5.2.8 e tópico 5.4.2](/previous-versions/msp-n-p/ff650760(v=pandp.10)).

### <a name="xdouble"></a>x:Double

Para o backup do CLR, o `x:Double` primitivo corresponde a <xref:System.Double> .

Além dos valores numéricos, a sintaxe de texto para `x:Double` permite os tokens `Infinity` , `-Infinity` e `NaN` . Esses tokens são tratados como diferenciando maiúsculas de minúsculas.

`x:Double` pode dar suporte a valores no formato de notação científica. Use o caractere `e` ou `E` para introduzir a parte do expoente.

Para a definição de especificação da linguagem XAML, consulte [ \[ seções do MS-XAML \] 5.2.9 e 5.4.3](/previous-versions/msp-n-p/ff650760(v=pandp.10)).

### <a name="xint16"></a>x:Int16

Para o backup do CLR, o `x:Int16` primitivo corresponde a <xref:System.Int16> e `x:Int16` é tratado como assinado. Em XAML, a ausência de uma sintaxe de texto de sinal de adição ( `+` ) é implícita como um valor assinado positivo.

Para a definição de especificação da linguagem XAML, consulte [ \[ seções do MS-XAML \] 5.2.11 e 5.4.5](/previous-versions/msp-n-p/ff650760(v=pandp.10)).

### <a name="xint32"></a>x:Int32

Para o backup do CLR, o `x:Int32` primitivo corresponde a <xref:System.Int32> . `x:Int32` é tratado como assinado. Em XAML, a ausência de uma sintaxe de texto de sinal de adição ( `+` ) é implícita como um valor assinado positivo.

Para a definição de especificação da linguagem XAML, consulte [ \[ seções do MS-XAML \] 5.2.12 e 5.4.6](/previous-versions/msp-n-p/ff650760(v=pandp.10)).

### <a name="xint64"></a>x:Int64

Para o backup do CLR, o `x:Int64` primitivo corresponde a <xref:System.Int64> . `x:Int64` é tratado como assinado. Em XAML, a ausência de uma sintaxe de texto de sinal de adição ( `+` ) é implícita como um valor assinado positivo.

Para a definição de especificação da linguagem XAML, consulte [ \[ seções do MS-XAML \] 5.2.13 e 5.4.7](/previous-versions/msp-n-p/ff650760(v=pandp.10)).

### <a name="xtimespan"></a>x:TimeSpan

Para o backup do CLR, o `x:TimeSpan` primitivo corresponde a <xref:System.TimeSpan> .

A análise XAML para o formato de data e hora é inerentemente feita em `en-US` cultura.

Para a definição de especificação da linguagem XAML, consulte [ \[ seções do MS-XAML \] 5.2.16 e 5.4.10](/previous-versions/msp-n-p/ff650760(v=pandp.10)).

### <a name="xuri"></a>x:Uri

Para o backup do CLR, o `x:Uri` primitivo corresponde a <xref:System.Uri> .

A verificação de protocolos não faz parte da definição XAML para `x:Uri` .

Para a definição de especificação da linguagem XAML, consulte [ \[ seções do MS-XAML \] 5.2.15 e 5.4.9](/previous-versions/msp-n-p/ff650760(v=pandp.10)).

### <a name="xbyte"></a>x:Byte

Para o backup do CLR, o `x:Byte` primitivo corresponde a <xref:System.Byte> . Um <xref:System.Byte>  /  `x:Byte` é tratado como não assinado.

Para a definição de especificação da linguagem XAML, consulte [ \[ seções do MS-XAML \] 5.2.10 e 5.4.4](/previous-versions/msp-n-p/ff650760(v=pandp.10)).

### <a name="xarray"></a>x:Array

Para o backup do CLR, o `x:Array` primitivo corresponde a <xref:System.Array> .

Você pode definir uma matriz em XAML 2006 usando uma sintaxe de extensão de marcação; no entanto, a sintaxe XAML 2009 é um primitivo definido por linguagem que não requer acesso a uma extensão de marcação. Para obter mais informações sobre o suporte a XAML 2006, consulte [extensão de marcação x:array](xarray-markup-extension.md).

Para a definição de especificação da linguagem XAML, consulte as [ \[ seções do MS-XAML \] 5.2.18](/previous-versions/msp-n-p/ff650760(v=pandp.10)).

## <a name="wpf-support"></a>Suporte do WPF

No WPF, você pode usar os recursos do XAML 2009, mas somente para XAML que não seja compilado por marcação. O XAML com compilação de marcação para WPF e a forma de BAML do XAML atualmente não dão suporte às palavras-chave e aos recursos do XAML 2009.

Um cenário em que você pode usar recursos XAML 2009 junto com o WPF é se você criar um XAML livre e, em seguida, carregar esse XAML em um grafo de tempo de execução e de objeto do WPF com <xref:System.Windows.Markup.XamlReader.Load%2A?displayProperty=nameWithType> . O WPF <xref:System.Windows.Markup.XamlReader?displayProperty=nameWithType> e seu <xref:System.Windows.Markup.XamlReader.Load%2A> pode processar palavras-chave de linguagem XAML 2009 e recursos em uma representação de grafo de objeto válido.
