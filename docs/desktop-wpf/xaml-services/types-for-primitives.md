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
ms.openlocfilehash: 3bd486ee66c5f9a32621416638bb7575025f7dee
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "82071832"
---
# <a name="built-in-types-for-common-xaml-language-primitives"></a>Tipos incorporados para primitivos comuns da linguagem XAML

XAML 2009 introduz suporte em nível de linguagem XAML para vários tipos de dados que são frequentemente usados primitivos no tempo de execução da linguagem comum (CLR) e em outras linguagens de programação. XAML 2009 adiciona suporte a `x:Object` `x:Boolean`estes primitivos: `x:Int16` `x:Int32`, `x:Int64` `x:TimeSpan`, `x:Uri` `x:Char`, `x:String` `x:Decimal`, `x:Single`, `x:Double`, , , , , , , , `x:Byte`, , e`x:Array`

## <a name="previous-techniques-for-language-primitives-in-xaml-markup"></a>Técnicas anteriores para primitivos linguísticos na marcação XAML

 Em XAML para versões Anteriores do WPF, você pode referenciar os primitivos da linguagem CLR mapeando o conjunto e o namespace que continha uma classe de definição primitiva CLR para o Quadro .NET. A maioria deles está na montagem <xref:System> mscorlib e namespace. Por exemplo, <xref:System.Int32>para usar, você pode declarar o seguinte mapeamento (com um uso de exemplo mostrado posteriormente):

```xaml
<Application xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
xmlns:sys="clr-namespace:System;assembly=mscorlib">
  <Application.Resources>
    <sys:Int32 x:Key="intMeaning">42</sys:Int32>
  </Application.Resources>
</Application>
```

## <a name="xaml-2009-language-primitives"></a>XAML 2009 Língua primitiva

Por convenção, os primitivos da linguagem para XAML e todos `x:` os outros elementos da linguagem XAML são mostrados, incluindo o prefixo. É assim que os elementos da linguagem XAML são normalmente usados em situações reais de marcação. Esta convenção é seguida na documentação conceitual para XAML na WPF e também na especificação XAML.

### <a name="xobject"></a>x:Objeto

Para o apoio `x:Object` da CLR, o primitivo corresponde a <xref:System.Object>.

Este primitivo não é normalmente usado na marcação de aplicativos, mas pode ser útil para alguns cenários, como verificar a atribuibilidade em um sistema tipo XAML.

### <a name="xboolean"></a>x:Boolean

Para o apoio `x:Boolean` da CLR, o primitivo corresponde a <xref:System.Boolean>.

XAML analisa valores `x:Boolean` como caso insensível. Note `x:Bool` que não é uma alternativa aceita. Para obter a definição de especificação do idioma XAML, consulte [ \[as seções MS-XAML\] 5.2.17 e 5.4.11](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).

### <a name="xchar"></a>x:Char

Para o apoio `x:Char` da CLR, o primitivo corresponde a <xref:System.Char>.

Os tipos de string e char têm interação com a codificação geral do arquivo no nível XML. Para obter a definição de especificação do idioma XAML, consulte [ \[as seções MS-XAML\] 5.2.7 e 5.4.1](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).

### <a name="xstring"></a>x:String

Para o apoio `x:String` da CLR, o primitivo corresponde a <xref:System.String>.

Os tipos de string e char têm interação com a codificação geral do arquivo no nível XML. Para obter a definição de especificação do idioma XAML, consulte [ \[As seções MS-XAML\] 5.2.6](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).

### <a name="xdecimal"></a>x:Decimal

Para o apoio `x:Decimal` da CLR, o primitivo corresponde a <xref:System.Decimal>.

O parsing XAML é `en-US` inerentemente feito sob a cultura. Segundo `en-US` a cultura, o separador correto para os componentes`.`de uma decimal é sempre um período ( ) independentemente das configurações de cultura do ambiente de desenvolvimento, ou do eventual alvo do cliente onde o XAML é carregado em tempo de execução.

Para obter a definição de especificação do idioma XAML, consulte [ \[as seções MS-XAML\] 5.2.14 e 5.4.8](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).

### <a name="xsingle"></a>x:Único

Para o apoio `x:Single` da CLR, o primitivo corresponde a <xref:System.Single>.

Além dos valores numéricos, a `x:Single` sintaxe `Infinity`de `-Infinity`texto `NaN`para também permite os tokens, e . Esses tokens são tratados como sensíveis ao caso.

`x:Single`pode apoiar valores na forma de notação científica, `e` se `E`o primeiro caractere na sintaxe de texto for ou .

Para obter a definição de especificação do idioma XAML, consulte [ \[as seções MS-XAML\] 5.2.8 e 5.4.2](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).

### <a name="xdouble"></a>x:Double

Para o apoio `x:Double` da CLR, o primitivo corresponde a <xref:System.Double>.

Além dos valores numéricos, a `x:Double` sintaxe `Infinity` `-Infinity`de `NaN`texto para permitir os tokens, e . Esses tokens são tratados como sensíveis ao caso.

`x:Double`pode apoiar valores na forma de notação científica. Use o `e` `E` caractere ou para introduzir a parte expoente.

Para obter a definição de especificação do idioma XAML, consulte [ \[as seções MS-XAML\] 5.2.9 e 5.4.3](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).

### <a name="xint16"></a>x:Int16

Para o apoio `x:Int16` da CLR, o primitivo corresponde <xref:System.Int16> e `x:Int16` é tratado como assinado. No XAML, a ausência`+`de um sinal de aplus ( ) na sintaxe de texto está implícita como um valor assinado positivo.

Para obter a definição de especificação do idioma XAML, consulte [ \[as seções MS-XAML\] 5.2.11 e 5.4.5](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).

### <a name="xint32"></a>x:Int32

Para o apoio `x:Int32` da CLR, o primitivo corresponde a <xref:System.Int32>. `x:Int32`é tratado como assinado. No XAML, a ausência`+`de um sinal de aplus ( ) na sintaxe de texto está implícita como um valor assinado positivo.

Para obter a definição de especificação do idioma XAML, consulte [ \[as seções MS-XAML\] 5.2.12 e 5.4.6](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).

### <a name="xint64"></a>x:Int64

Para o apoio `x:Int64` da CLR, o primitivo corresponde a <xref:System.Int64>. `x:Int64`é tratado como assinado. No XAML, a ausência`+`de um sinal de aplus ( ) na sintaxe de texto está implícita como um valor assinado positivo.

Para obter a definição de especificação do idioma XAML, consulte [ \[as seções MS-XAML\] 5.2.13 e 5.4.7](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).

### <a name="xtimespan"></a>x:TimeSpan

Para o apoio `x:TimeSpan` da CLR, o primitivo corresponde a <xref:System.TimeSpan>.

O parsing XAML para o formato `en-US` de data-hora é inerentemente feito sob a cultura.

Para obter a definição de especificação do idioma XAML, consulte [ \[as seções MS-XAML\] 5.2.16 e 5.4.10](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).

### <a name="xuri"></a>x:Uri

Para o apoio `x:Uri` da CLR, o primitivo corresponde a <xref:System.Uri>.

Verificar os protocolos não faz parte da `x:Uri`definição XAML para .

Para obter a definição de especificação do idioma XAML, consulte [ \[as seções MS-XAML\] 5.2.15 e 5.4.9](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).

### <a name="xbyte"></a>x:Byte

Para o apoio `x:Byte` da CLR, o primitivo corresponde a <xref:System.Byte>. <xref:System.Byte>  /  A `x:Byte` é tratado como não assinado.

Para obter a definição de especificação do idioma XAML, consulte [ \[as seções MS-XAML\] 5.2.10 e 5.4.4](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).

### <a name="xarray"></a>x:Array

Para o apoio `x:Array` da CLR, o primitivo corresponde a <xref:System.Array>.

Você pode definir uma matriz no XAML 2006 usando uma sintaxe de extensão de marcação; no entanto, a sintaxe XAML 2009 é um primitivo definido pela linguagem que não requer acesso a uma extensão de marcação. Para obter mais informações sobre o suporte ao XAML 2006, consulte [x:Array Markup Extension](xarray-markup-extension.md).

Para obter a definição de especificação do idioma XAML, consulte [ \[As seções MS-XAML\] 5.2.18](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).

## <a name="wpf-support"></a>Suporte wpf

No WPF, você pode usar recursos XAML 2009, mas apenas para XAML que não é compilado por marcação. O XAML compilado por marcação para WPF e a forma BAML de XAML não suportam atualmente as palavras-chave e recursos do XAML 2009.

Um cenário onde você pode usar os recursos do XAML 2009 juntamente com o WPF é se você escrever <xref:System.Windows.Markup.XamlReader.Load%2A?displayProperty=nameWithType>XAML solto e, em seguida, carregar esse XAML em um gráfico de tempo de execução wpf e objeto com . O WPF <xref:System.Windows.Markup.XamlReader?displayProperty=nameWithType> <xref:System.Windows.Markup.XamlReader.Load%2A> e seus podem processar palavras-chave de linguagem XAML 2009 e recursos em uma representação de gráfico de objeto válida.
