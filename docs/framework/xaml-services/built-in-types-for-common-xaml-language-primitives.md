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
ms.openlocfilehash: c6af46fe2ea21d081e693ee83949651bd388a045
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74837266"
---
# <a name="built-in-types-for-common-xaml-language-primitives"></a>Tipos inseridos para primitivos de linguagem XML comuns
O XAML 2009 apresenta suporte no nível da linguagem XAML para vários tipos de dados que são primitivos usados com frequência no Common Language Runtime (CLR) e em outras linguagens de programação. O XAML 2009 adiciona suporte para esses primitivos: `x:Object`, `x:Boolean`, `x:Char`, `x:String`, `x:Decimal`, `x:Single`, `x:Double`, `x:Int16`, `x:Int32`, `x:Int64`, `x:TimeSpan`, `x:Uri`, `x:Byte`e `x:Array`  
  
<a name="previous_techniques_for_language_primitives_in_xaml_markup"></a>   
## <a name="previous-techniques-for-language-primitives-in-xaml-markup"></a>Técnicas anteriores para primitivos de linguagem na marcação XAML  
 No XAML para versões anteriores do WPF, você pode referenciar primitivos de linguagem do CLR mapeando o assembly e o namespace que continham uma classe de definição primitiva do CLR para o.NET Framework. A maioria deles está no assembly mscorlib e no namespace <xref:System>. Por exemplo, para usar <xref:System.Int32>, você poderia declarar o seguinte mapeamento (com um uso de exemplo mostrado daí em diante):  
  
```xaml  
<Application xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"   
xmlns:sys="clr-namespace:System;assembly=mscorlib">  
  <Application.Resources>  
    <sys:Int32 x:Key="intMeaning">42</sys:Int32>  
  </Application.Resources>  
</Application>  
```  
  
<a name="xaml_2009_language_primitives"></a>   
## <a name="xaml-2009-language-primitives"></a>Primitivas de linguagem de XAML2009  
 Por convenção, primitivos de linguagem para XAML e todos os outros elementos de linguagem XAML são mostrados, incluindo o prefixo de `x:`. É assim que os elementos da linguagem XAML são normalmente usados em situações reais de marcação. Esta convenção é seguida na documentação conceitual para XAML no WPF e também na especificação XAML.  
  
### <a name="xobject"></a>x:Object  
 Para o CLR de retorno, a primitiva de `x:Object` corresponde a <xref:System.Object>.  
  
 Este primitivo geralmente não é usado na marcação do aplicativo, mas pode ser útil para alguns cenários, como verificar a capacidade de atribuição em um sistema do tipo XAML.  
  
### <a name="xboolean"></a>x:Boolean  
 Para o CLR de retorno, a primitiva de `x:Boolean` corresponde a <xref:System.Boolean>.  
  
 Valores de análise XAML para `x:Boolean` não diferencia maiúsculas de minúsculas. Observe que `x:Bool` não é uma alternativa aceita. Para a definição de especificação da linguagem XAML, consulte [\[MS-XAML\] seções 5.2.17 e 5.4.11](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).  
  
### <a name="xchar"></a>x:Char  
 Para o CLR de retorno, a primitiva de `x:Char` corresponde a <xref:System.Char>.  
  
 Os tipos de cadeia de caracteres e de caracteres têm interação com a codificação geral do arquivo no nível XML. Para a definição de especificação da linguagem XAML, consulte [\[MS-XAML\] seções 5.2.7 e 5.4.1](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).  
  
### <a name="xstring"></a>x:String  
 Para o CLR de retorno, a primitiva de `x:String` corresponde a <xref:System.String>.  
  
 Os tipos de cadeia de caracteres e de caracteres têm interação com a codificação geral do arquivo no nível XML. Para a definição de especificação da linguagem XAML, consulte [\[MS-XAML\] seções 5.2.6](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).  
  
### <a name="xdecimal"></a>x:Decimal  
 Para o CLR de retorno, a primitiva de `x:Decimal` corresponde a <xref:System.Decimal>.  
  
 Observe que a análise XAML é feita de forma inerente na cultura de `en-US`. Na cultura `en-US`, o separador correto para componentes de um decimal é sempre um ponto (`.`) independentemente das configurações de cultura do ambiente de desenvolvimento ou de destino eventual de cliente em que o XAML é carregado no tempo de execução.  
  
 Para a definição de especificação da linguagem XAML, consulte [\[MS-XAML\] seções 5.2.14 e 5.4.8](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).  
  
### <a name="xsingle"></a>x:Single  
 Para o CLR de retorno, a primitiva de `x:Single` corresponde a <xref:System.Single>.  
  
 Além dos valores numéricos, a sintaxe de texto para `x:Single` também permite os tokens `Infinity`, `-Infinity` e `NaN`. Esses tokens diferenciam maiúsculas e minúsculas.  
  
 `x:Single` pode suportar valores no formulário de notação científica, se o primeiro caractere na sintaxe de texto é `e` ou `E`.  
  
 Para a definição de especificação da linguagem XAML, consulte [\[MS-XAML\] seções 5.2.8 e tópico 5.4.2](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).  
  
### <a name="xdouble"></a>x:Double  
 Para o CLR de retorno, a primitiva de `x:Double` corresponde a <xref:System.Double>.  
  
 Além dos valores numéricos, a sintaxe de texto para `x:Double` permite os tokens `Infinity`, `-Infinity` e `NaN`. Esses tokens diferenciam maiúsculas e minúsculas.  
  
 `x:Double` pode suportar valores no formulário de notação científica. Use o caractere `e` ou `E` para apresentar a parte do expoente.  
  
 Para a definição de especificação da linguagem XAML, consulte [\[MS-XAML\] seções 5.2.9 e 5.4.3](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).  
  
### <a name="xint16"></a>x:Int16  
 Para apoio ao CLR, o primitivo `x:Int16` corresponde a <xref:System.Int16> e `x:Int16` é tratado como assinado. No XAML, a ausência de um sinal de mais (`+`) na sintaxe do texto considerada como um valor de sinal positivo.  
  
 Para a definição de especificação da linguagem XAML, consulte [\[MS-XAML\] seções 5.2.11 e 5.4.5](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).  
  
### <a name="xint32"></a>x:Int32  
 Para o CLR de retorno, a primitiva de `x:Int32` corresponde a <xref:System.Int32>. `x:Int32` é tratado como assinado. No XAML, a ausência de um sinal de mais (`+`) na sintaxe do texto considerada como um valor de sinal positivo.  
  
 Para a definição de especificação da linguagem XAML, consulte [\[MS-XAML\] seções 5.2.12 e 5.4.6](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).  
  
### <a name="xint64"></a>x:Int64  
 Para o CLR de retorno, a primitiva de `x:Int64` corresponde a <xref:System.Int64>. `x:Int64` é tratado como assinado. No XAML, a ausência de um sinal de mais (`+`) na sintaxe do texto considerada como um valor de sinal positivo.  
  
 Para a definição de especificação da linguagem XAML, consulte [\[MS-XAML\] seções 5.2.13 e 5.4.7](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).  
  
### <a name="xtimespan"></a>x:TimeSpan  
 Para o CLR de retorno, a primitiva de `x:TimeSpan` corresponde a <xref:System.TimeSpan>.  
  
 Observe que a análise XAML para o formato de data e hora é feita de forma inerente na cultura de `en-US`.  
  
 Para a definição de especificação da linguagem XAML, consulte [\[MS-XAML\] seções 5.2.16 e 5.4.10](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).  
  
### <a name="xuri"></a>x:Uri  
 Para o CLR de retorno, a primitiva de `x:Uri` corresponde a <xref:System.Uri>.  
  
 A verificação de protocolos não faz parte da definição de XAML para `x:Uri`.  
  
 Para a definição de especificação da linguagem XAML, consulte [\[MS-XAML\] seções 5.2.15 e 5.4.9](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).  
  
### <a name="xbyte"></a>x:Byte  
 Para o CLR de retorno, a primitiva de `x:Byte` corresponde a <xref:System.Byte>. Um <xref:System.Byte> / `x:Byte` é tratado como não assinado.  
  
 Para a definição de especificação da linguagem XAML, consulte [\[MS-XAML\] seções 5.2.10 e 5.4.4](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).  
  
### <a name="xarray"></a>x:Array  
 Para o CLR de retorno, a primitiva de `x:Array` corresponde a <xref:System.Array>.  
  
 Você pode definir uma matriz em XAML 2006 usando uma sintaxe de extensão de marcação; no entanto, a sintaxe XAML 2009 é um primitivo definido por linguagem que não requer acesso a uma extensão de marcação. Para obter mais informações sobre o suporte a XAML 2006, consulte [extensão de marcação x:array](x-array-markup-extension.md).  
  
 Para a definição de especificação da linguagem XAML, consulte [\[MS-XAML\] seções 5.2.18](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).  
  
<a name="wpf_support"></a>   
## <a name="wpf-support"></a>Suporte a WPF  
 No WPF, você pode usar os recursos do XAML 2009, mas somente para XAML que não seja compilado por marcação. O XAML com compilação de marcação para WPF e a forma de BAML do XAML atualmente não dão suporte às palavras-chave e aos recursos do XAML 2009.  
  
 Um cenário em que você pode usar recursos XAML 2009 junto com o WPF é se você criar um XAML livre e, em seguida, carregar esse XAML em um grafo de tempo de execução e de objeto do WPF com <xref:System.Windows.Markup.XamlReader.Load%2A?displayProperty=nameWithType>. O <xref:System.Windows.Markup.XamlReader?displayProperty=nameWithType> do WPF e seus <xref:System.Windows.Markup.XamlReader.Load%2A> podem processar palavras-chave de linguagem XAML 2009 e recursos em uma representação de grafo de objeto válido.
