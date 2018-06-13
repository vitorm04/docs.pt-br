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
ms.openlocfilehash: 15c359a9a7f9797fc03ce20c453905af01f925d7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33564346"
---
# <a name="built-in-types-for-common-xaml-language-primitives"></a>Tipos inseridos para primitivos de linguagem XML comuns
XAML 2009 introduz o suporte ao nível de linguagem XAML vários tipos de dados que são usados com frequência primitivos no common language runtime (CLR) e em outras linguagens de programação. XAML 2009 adiciona suporte para esses primitivos: `x:Object`, `x:Boolean`, `x:Char`, `x:String`, `x:Decimal`, `x:Single`, `x:Double`, `x:Int16`, `x:Int32`, `x:Int64`, `x:TimeSpan`, `x:Uri`, `x:Byte`, e `x:Array`  
  
<a name="previous_techniques_for_language_primitives_in_xaml_markup"></a>   
## <a name="previous-techniques-for-language-primitives-in-xaml-markup"></a>Técnicas anteriores para primitivos de linguagem de marcação XAML  
 Em XAML para versões anteriores do WPF, você pode referenciar os primitivos de linguagem CLR mapeando o assembly e o namespace que continha uma classe de definição primitivo do CLR para o .NET Framework. A maioria deles está no assembly mscorlib e <xref:System> namespace. Por exemplo, para usar <xref:System.Int32>, você pode declarar o seguinte mapeamento (com um uso de exemplo mostrado posteriormente):  
  
```  
<Application xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"   
xmlns:sys="clr-namespace:System;assembly=mscorlib">  
  <Application.Resources>  
    <sys:Int32 x:Key="intMeaning">42</sys:Int32>  
  </Application.Resources>  
</Application>  
```  
  
<a name="xaml_2009_language_primitives"></a>   
## <a name="xaml-2009-language-primitives"></a>Primitivos de linguagem XAML 2009  
 Por convenção, os primitivos de linguagem XAML e todos os outros elementos de linguagem XAML são mostrados, incluindo o `x:` prefixo. Isso é como os elementos de linguagem XAML normalmente são usados na marcação do mundo real. Essa convenção é seguida na documentação conceitual do XAML em WPF e também na especificação do XAML.  
  
### <a name="xobject"></a>x: o objeto  
 Para backups de CLR, o `x:Object` primitivo corresponde ao <xref:System.Object>.  
  
 Esse primitivo geralmente não é usado na marcação de aplicativo, mas pode ser útil para alguns cenários, como verificação de assignability em um sistema de tipo XAML.  
  
### <a name="xboolean"></a>x: Boolean  
 Para backups de CLR, o `x:Boolean` primitivo corresponde ao <xref:System.Boolean>.  
  
 XAML analisa os valores para `x:Boolean` como maiusculas e minúsculas. Observe que `x:Bool` não é uma alternativa aceita. Para a definição de especificação de linguagem XAML, consulte [ \[XAML MS\] seções 5.2.17 e 5.4.11](http://go.microsoft.com/fwlink/?LinkId=114525).  
  
### <a name="xchar"></a>x: Char  
 Para backups de CLR, o `x:Char` primitivo corresponde ao <xref:System.Char>.  
  
 Tipos de cadeia de caracteres e caracteres têm interação com a codificação geral do arquivo no nível do XML. Para a definição de especificação de linguagem XAML, consulte [ \[XAML MS\] seções 5.2.7 e 5.4.1](http://go.microsoft.com/fwlink/?LinkId=114525).  
  
### <a name="xstring"></a>x: cadeia de caracteres  
 Para backups de CLR, o `x:String` primitivo corresponde ao <xref:System.String>.  
  
 Tipos de cadeia de caracteres e caracteres têm interação com a codificação geral do arquivo no nível do XML. Para a definição de especificação de linguagem XAML, consulte [ \[XAML MS\] seções 5.2.6](http://go.microsoft.com/fwlink/?LinkId=114525).  
  
### <a name="xdecimal"></a>x: Decimal  
 Para backups de CLR, o `x:Decimal` primitivo corresponde ao <xref:System.Decimal>.  
  
 Observe que a análise de XAML inerentemente é feita em `en-US` cultura. Em `en-US` cultura, o separador correto para os componentes de um decimal é sempre um período (`.`), independentemente das configurações de cultura do ambiente de desenvolvimento ou de destino eventual cliente onde o XAML é carregado no tempo de execução.  
  
 Para a definição de especificação de linguagem XAML, consulte [ \[XAML MS\] seções 5.2.14 e 5.4.8](http://go.microsoft.com/fwlink/?LinkId=114525).  
  
### <a name="xsingle"></a>x: único  
 Para backups de CLR, o `x:Single` primitivo corresponde ao <xref:System.Single>.  
  
 Além de valores numéricos, sintaxe de texto para `x:Single` também permite que os tokens `Infinity`, `-Infinity`, e `NaN`. Esses tokens são tratados como maiusculas e minúsculas.  
  
 `x:Single` pode dar suporte a valores no formulário de notação científica, se o primeiro caractere na sintaxe do texto é `e` ou `E`.  
  
 Para a definição de especificação de linguagem XAML, consulte [ \[XAML MS\] seções 5.2.8 e 5.4.2](http://go.microsoft.com/fwlink/?LinkId=114525).  
  
### <a name="xdouble"></a>x: duplo  
 Para backups de CLR, o `x:Double` primitivo corresponde ao <xref:System.Double>.  
  
 Além de valores numéricos, sintaxe de texto para `x:Double` permite que os tokens `Infinity`, `-Infinity`, e `NaN`. Esses tokens são tratados como maiusculas e minúsculas.  
  
 `x:Double` pode dar suporte a valores no formulário de notação científica. Use o caractere `e` ou `E` para apresentar a parte expoente.  
  
 Para a definição de especificação de linguagem XAML, consulte [ \[XAML MS\] seções 5.2.9 e 5.4.3](http://go.microsoft.com/fwlink/?LinkId=114525).  
  
### <a name="xint16"></a>x: Int16  
 Para backups de CLR, o `x:Int16` primitivo corresponde à <xref:System.Int16> e `x:Int16` é tratado como assinado. Em XAML, a ausência de um sinal de mais (`+`) entrada na sintaxe de texto indicada como um valor de sinal positivo.  
  
 Para a definição de especificação de linguagem XAML, consulte [ \[XAML MS\] seções 5.2.11 e 5.4.5](http://go.microsoft.com/fwlink/?LinkId=114525).  
  
### <a name="xint32"></a>x:Int32  
 Para backups de CLR, o `x:Int32` primitivo corresponde ao <xref:System.Int32>. `x:Int32` é tratado como assinado. Em XAML, a ausência de um sinal de mais (`+`) entrada na sintaxe de texto indicada como um valor de sinal positivo.  
  
 Para a definição de especificação de linguagem XAML, consulte [ \[XAML MS\] seções 5.2.12 e 5.4.6](http://go.microsoft.com/fwlink/?LinkId=114525).  
  
### <a name="xint64"></a>x: Int64  
 Para backups de CLR, o `x:Int64` primitivo corresponde ao <xref:System.Int64>. `x:Int64` é tratado como assinado. Em XAML, a ausência de um sinal de mais (`+`) entrada na sintaxe de texto indicada como um valor de sinal positivo.  
  
 Para a definição de especificação de linguagem XAML, consulte [ \[XAML MS\] seções 5.2.13 e 5.4.7](http://go.microsoft.com/fwlink/?LinkId=114525).  
  
### <a name="xtimespan"></a>X:TimeSpan  
 Para backups de CLR, o `x:TimeSpan` primitivo corresponde ao <xref:System.TimeSpan>.  
  
 Observe que XAML análise para o formato de data / hora é feito inerentemente `en-US` cultura.  
  
 Para a definição de especificação de linguagem XAML, consulte [ \[XAML MS\] seções 5.2.16 e 5.4.10](http://go.microsoft.com/fwlink/?LinkId=114525).  
  
### <a name="xuri"></a>x: Uri  
 Para backups de CLR, o `x:Uri` primitivo corresponde ao <xref:System.Uri>.  
  
 A verificação de protocolos não é parte da definição de XAML para `x:Uri`.  
  
 Para a definição de especificação de linguagem XAML, consulte [ \[XAML MS\] seções 5.2.15 e 5.4.9](http://go.microsoft.com/fwlink/?LinkId=114525).  
  
### <a name="xbyte"></a>x: Byte  
 Para backups de CLR, o `x:Byte` primitivo corresponde ao <xref:System.Byte>. Um <xref:System.Byte>  /  `x:Byte` é tratado como não assinados.  
  
 Para a definição de especificação de linguagem XAML, consulte [ \[XAML MS\] seções 5.2.10 e 5.4.4](http://go.microsoft.com/fwlink/?LinkId=114525).  
  
### <a name="xarray"></a>X:array  
 Para backups de CLR, o `x:Array` primitivo corresponde ao <xref:System.Array>.  
  
 Você pode definir uma matriz em XAML 2006 usando uma sintaxe de extensão de marcação; No entanto, a sintaxe XAML 2009 é um primitivo de idioma definido que não requer acesso a uma extensão de marcação. Para obter mais informações sobre o suporte de 2006 XAML, consulte [extensão de marcação X:array](../../../docs/framework/xaml-services/x-array-markup-extension.md).  
  
 Para a definição de especificação de linguagem XAML, consulte [ \[XAML MS\] seções 5.2.18](http://go.microsoft.com/fwlink/?LinkId=114525).  
  
<a name="wpf_support"></a>   
## <a name="wpf-support"></a>Suporte a WPF  
 No WPF, você pode usar recursos XAML 2009 mas somente para XAML não marcação-compilado. Compilação de marcação XAML WPF e do formulário BAML do XAML atualmente não dão os recursos e as palavras-chave de XAML 2009.  
  
 Um cenário onde você pode usar recursos XAML 2009 junto com WPF é se você criar XAML livre e você, em seguida, carregar esse XAML em um gráfico de tempo de execução e o objeto WPF com <xref:System.Windows.Markup.XamlReader.Load%2A?displayProperty=nameWithType>. O WPF <xref:System.Windows.Markup.XamlReader?displayProperty=nameWithType> e sua <xref:System.Windows.Markup.XamlReader.Load%2A> pode processar palavras-chave de linguagem XAML 2009 e recursos em uma representação de gráfico de objeto válido.
