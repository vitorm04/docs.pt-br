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
ms.openlocfilehash: f6225dfcc02b90da58ccafd5c70726b6f80f29d4
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47210104"
---
# <a name="built-in-types-for-common-xaml-language-primitives"></a>Tipos inseridos para primitivos de linguagem XML comuns
XAML 2009 introduz o suporte de nível de linguagem XAML para vários tipos de dados que são usados com frequência primitivas no common language runtime (CLR) e em outras linguagens de programação. XAML 2009 adiciona suporte para esses primitivos: `x:Object`, `x:Boolean`, `x:Char`, `x:String`, `x:Decimal`, `x:Single`, `x:Double`, `x:Int16`, `x:Int32`, `x:Int64`, `x:TimeSpan`, `x:Uri`, `x:Byte`, e `x:Array`  
  
<a name="previous_techniques_for_language_primitives_in_xaml_markup"></a>   
## <a name="previous-techniques-for-language-primitives-in-xaml-markup"></a>Técnicas anteriores para primitivos de linguagem na marcação XAML  
 No XAML para versões anteriores do WPF, você poderia fazer referência os primitivos de linguagem do CLR mapeando o assembly e namespace que continham uma classe de definição Primitiva do CLR para o .NET Framework. A maioria deles está no assembly mscorlib e <xref:System> namespace. Por exemplo, para usar <xref:System.Int32>, você poderia declarar o seguinte mapeamento (com um uso de exemplo mostrado daí em diante):  
  
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
 Por convenção, primitivos de linguagem para XAML e todos os outros elementos de linguagem XAML são mostrados, incluindo o `x:` prefixo. Isso é como os elementos de linguagem XAML geralmente são usados na marcação do mundo real. Essa convenção é seguida na documentação conceitual para XAML no WPF e também na especificação XAML.  
  
### <a name="xobject"></a>x: objeto  
 Para o CLR de retorno, o `x:Object` primitiva corresponde ao <xref:System.Object>.  
  
 Este primitivo geralmente não é usado na marcação de aplicativo, mas pode ser útil para alguns cenários, como verificar a capacidade de atribuição em um sistema de tipo XAML.  
  
### <a name="xboolean"></a>x: booliano  
 Para o CLR de retorno, o `x:Boolean` primitiva corresponde ao <xref:System.Boolean>.  
  
 XAML analisa valores para `x:Boolean` como diferencia maiusculas de minúsculas. Observe que `x:Bool` não é uma alternativa aceita. Para a definição da especificação da linguagem XAML, consulte [ \[MS-XAML\] seções 5.2.17 e 5.4.11](https://go.microsoft.com/fwlink/?LinkId=114525).  
  
### <a name="xchar"></a>x: Char  
 Para o CLR de retorno, o `x:Char` primitiva corresponde ao <xref:System.Char>.  
  
 Tipos de cadeia de caracteres e char têm interação com a codificação geral do arquivo no nível do XML. Para a definição da especificação da linguagem XAML, consulte [ \[MS-XAML\] seções 5.2.7 e 5.4.1](https://go.microsoft.com/fwlink/?LinkId=114525).  
  
### <a name="xstring"></a>x: cadeia de caracteres  
 Para o CLR de retorno, o `x:String` primitiva corresponde ao <xref:System.String>.  
  
 Tipos de cadeia de caracteres e char têm interação com a codificação geral do arquivo no nível do XML. Para a definição da especificação da linguagem XAML, consulte [ \[MS-XAML\] seções 5.2.6](https://go.microsoft.com/fwlink/?LinkId=114525).  
  
### <a name="xdecimal"></a>x: Decimal  
 Para o CLR de retorno, o `x:Decimal` primitiva corresponde ao <xref:System.Decimal>.  
  
 Observe que a análise de XAML é feita de forma inerente em `en-US` cultura. Sob `en-US` cultura, o separador correto para os componentes de um decimal é sempre um ponto (`.`), independentemente das configurações de cultura do ambiente de desenvolvimento ou de destino eventual de cliente em que o XAML é carregado no tempo de execução.  
  
 Para a definição da especificação da linguagem XAML, consulte [ \[MS-XAML\] seções 5.2.14 e 5.4.8](https://go.microsoft.com/fwlink/?LinkId=114525).  
  
### <a name="xsingle"></a>X:Single  
 Para o CLR de retorno, o `x:Single` primitiva corresponde ao <xref:System.Single>.  
  
 Além de valores numéricos, a sintaxe de texto para `x:Single` também permite que os tokens `Infinity`, `-Infinity`, e `NaN`. Esses tokens diferenciam maiusculas e minúsculas.  
  
 `x:Single` pode suportar valores no formulário de notação científica, se for o primeiro caractere na sintaxe de texto `e` ou `E`.  
  
 Para a definição da especificação da linguagem XAML, consulte [ \[MS-XAML\] seções 5.2.8 e 5.4.2](https://go.microsoft.com/fwlink/?LinkId=114525).  
  
### <a name="xdouble"></a>X:Double  
 Para o CLR de retorno, o `x:Double` primitiva corresponde ao <xref:System.Double>.  
  
 Além de valores numéricos, a sintaxe de texto para `x:Double` permite que os tokens `Infinity`, `-Infinity`, e `NaN`. Esses tokens diferenciam maiusculas e minúsculas.  
  
 `x:Double` pode suportar valores no formulário de notação científica. Use o caractere `e` ou `E` para introduzir a parte do expoente.  
  
 Para a definição da especificação da linguagem XAML, consulte [ \[MS-XAML\] seções 5.2.9 e 5.4.3](https://go.microsoft.com/fwlink/?LinkId=114525).  
  
### <a name="xint16"></a>x: Int16  
 Para o CLR de retorno, o `x:Int16` primitiva corresponde ao <xref:System.Int16> e `x:Int16` é tratado como assinado. No XAML, a ausência de um sinal de adição (`+`) sinal na sintaxe de texto é inferido como um valor de sinal positivo.  
  
 Para a definição da especificação da linguagem XAML, consulte [ \[MS-XAML\] seções 5.2.11 e 5.4.5](https://go.microsoft.com/fwlink/?LinkId=114525).  
  
### <a name="xint32"></a>x:Int32  
 Para o CLR de retorno, o `x:Int32` primitiva corresponde ao <xref:System.Int32>. `x:Int32` é tratado como assinado. No XAML, a ausência de um sinal de adição (`+`) sinal na sintaxe de texto é inferido como um valor de sinal positivo.  
  
 Para a definição da especificação da linguagem XAML, consulte [ \[MS-XAML\] seções 5.2.12 e 5.4.6](https://go.microsoft.com/fwlink/?LinkId=114525).  
  
### <a name="xint64"></a>x:Int64  
 Para o CLR de retorno, o `x:Int64` primitiva corresponde ao <xref:System.Int64>. `x:Int64` é tratado como assinado. No XAML, a ausência de um sinal de adição (`+`) sinal na sintaxe de texto é inferido como um valor de sinal positivo.  
  
 Para a definição da especificação da linguagem XAML, consulte [ \[MS-XAML\] seções 5.2.13 e 5.4.7](https://go.microsoft.com/fwlink/?LinkId=114525).  
  
### <a name="xtimespan"></a>X:TimeSpan  
 Para o CLR de retorno, o `x:TimeSpan` primitiva corresponde ao <xref:System.TimeSpan>.  
  
 Observe que essa análise XAML para o formato de data / hora é feito de forma inerente em `en-US` cultura.  
  
 Para a definição da especificação da linguagem XAML, consulte [ \[MS-XAML\] seções 5.2.16 e 5.4.10](https://go.microsoft.com/fwlink/?LinkId=114525).  
  
### <a name="xuri"></a>x: Uri  
 Para o CLR de retorno, o `x:Uri` primitiva corresponde ao <xref:System.Uri>.  
  
 Verificação de protocolos não faz parte da definição de XAML para `x:Uri`.  
  
 Para a definição da especificação da linguagem XAML, consulte [ \[MS-XAML\] seções 5.2.15 e 5.4.9](https://go.microsoft.com/fwlink/?LinkId=114525).  
  
### <a name="xbyte"></a>x: Byte  
 Para o CLR de retorno, o `x:Byte` primitiva corresponde ao <xref:System.Byte>. Um <xref:System.Byte>  /  `x:Byte` é tratado como não assinado.  
  
 Para a definição da especificação da linguagem XAML, consulte [ \[MS-XAML\] seções 5.2.10 e 5.4.4](https://go.microsoft.com/fwlink/?LinkId=114525).  
  
### <a name="xarray"></a>X:array  
 Para o CLR de retorno, o `x:Array` primitiva corresponde ao <xref:System.Array>.  
  
 Você pode definir uma matriz em XAML 2006 usando uma sintaxe de extensão de marcação; No entanto, a sintaxe de XAML 2009 é uma primitiva de linguagem definida que não requer acessar uma extensão de marcação. Para obter mais informações sobre o suporte do XAML 2006, consulte [extensão de marcação X:array](../../../docs/framework/xaml-services/x-array-markup-extension.md).  
  
 Para a definição da especificação da linguagem XAML, consulte [ \[MS-XAML\] seções 5.2.18](https://go.microsoft.com/fwlink/?LinkId=114525).  
  
<a name="wpf_support"></a>   
## <a name="wpf-support"></a>Suporte a WPF  
 No WPF, você pode usar os recursos do XAML 2009 mas somente para XAML que não é compilado por marcação. Compilado por marcação XAML para WPF e o formato BAML de XAML têm suporte no momento, as palavras-chave do XAML 2009 e os recursos.  
  
 Um cenário onde você pode usar os recursos do XAML 2009 junto com o WPF é se você criar o XAML flexível e, em seguida, carregar esse XAML em um gráfico de tempo de execução e o objeto do WPF com <xref:System.Windows.Markup.XamlReader.Load%2A?displayProperty=nameWithType>. O WPF <xref:System.Windows.Markup.XamlReader?displayProperty=nameWithType> e seu <xref:System.Windows.Markup.XamlReader.Load%2A> podem processar palavras-chave de linguagem XAML 2009 e recursos em uma representação de gráfico de objeto válido.
