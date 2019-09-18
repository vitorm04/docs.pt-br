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
ms.openlocfilehash: 85fd0c04a40b9de64979e4da1459dbf8953a93bf
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053889"
---
# <a name="built-in-types-for-common-xaml-language-primitives"></a>Tipos inseridos para primitivos de linguagem XML comuns
O XAML 2009 apresenta suporte no nível da linguagem XAML para vários tipos de dados que são primitivos usados com frequência no Common Language Runtime (CLR) e em outras linguagens de programação. O XAML 2009 adiciona suporte para esses primitivos `x:Object`: `x:Boolean` `x:Char`, `x:Single` `x:String` `x:Decimal` ,,`x:Double`,,,,,, ,,`x:TimeSpan` `x:Int16` `x:Int32` `x:Int64` `x:Uri`, e`x:Byte``x:Array`  
  
<a name="previous_techniques_for_language_primitives_in_xaml_markup"></a>   
## <a name="previous-techniques-for-language-primitives-in-xaml-markup"></a>Técnicas anteriores para primitivas de idioma na marcação XAML  
 Em XAML para versões anteriores do WPF, você pode referenciar os primitivos de linguagem CLR mapeando o assembly e o namespace que continham uma classe de definição de CLR primitivo para o .NET Framework. A maioria deles está no assembly e <xref:System> no namespace mscorlib. Por exemplo, para usar <xref:System.Int32>o, você pode declarar o seguinte mapeamento (com um exemplo de uso mostrado em seguida):  
  
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
## <a name="xaml-2009-language-primitives"></a>Primitivos de linguagem XAML 2009  
 Por convenção, os primitivos de idioma para XAML e todos os outros elementos de linguagem XAML são mostrados, incluindo o `x:` prefixo. É assim que os elementos de linguagem XAML normalmente são usados na marcação do mundo real. Essa convenção é seguida da documentação conceitual para XAML no WPF e também na especificação XAML.  
  
### <a name="xobject"></a>x:Object  
 Para o backup do CLR, `x:Object` o primitivo corresponde <xref:System.Object>a.  
  
 Normalmente, esse primitivo não é usado na marcação do aplicativo, mas pode ser útil para alguns cenários, como a verificação da atribuição em um sistema de tipos XAML.  
  
### <a name="xboolean"></a>x:Boolean  
 Para o backup do CLR, `x:Boolean` o primitivo corresponde <xref:System.Boolean>a.  
  
 O XAML analisa valores como `x:Boolean` não diferencia maiúsculas de minúsculas. Observe que `x:Bool` não é uma alternativa aceita. Para a definição de especificação da linguagem XAML, consulte [ \[seções\] do MS-XAML 5.2.17 e 5.4.11](https://go.microsoft.com/fwlink/?LinkId=114525).  
  
### <a name="xchar"></a>x:Char  
 Para o backup do CLR, `x:Char` o primitivo corresponde <xref:System.Char>a.  
  
 Tipos de cadeia de caracteres e caracteres têm interação com a codificação geral do arquivo no nível de XML. Para a definição de especificação da linguagem XAML, consulte [ \[seções\] do MS-XAML 5.2.7 e 5.4.1](https://go.microsoft.com/fwlink/?LinkId=114525).  
  
### <a name="xstring"></a>x:String  
 Para o backup do CLR, `x:String` o primitivo corresponde <xref:System.String>a.  
  
 Tipos de cadeia de caracteres e caracteres têm interação com a codificação geral do arquivo no nível de XML. Para a definição de especificação da linguagem XAML, consulte [ \[as\] seções do MS-XAML 5.2.6](https://go.microsoft.com/fwlink/?LinkId=114525).  
  
### <a name="xdecimal"></a>x:Decimal  
 Para o backup do CLR, `x:Decimal` o primitivo corresponde <xref:System.Decimal>a.  
  
 Observe que a análise XAML é feita de forma inerente `en-US` em Culture. Em `en-US` Culture, o separador correto para os componentes de um decimal é sempre um`.`ponto (), independentemente das configurações de cultura do ambiente de desenvolvimento, ou do destino de cliente eventual em que o XAML é carregado em tempo de execução.  
  
 Para a definição de especificação da linguagem XAML, consulte [ \[seções\] do MS-XAML 5.2.14 e 5.4.8](https://go.microsoft.com/fwlink/?LinkId=114525).  
  
### <a name="xsingle"></a>x:Single  
 Para o backup do CLR, `x:Single` o primitivo corresponde <xref:System.Single>a.  
  
 Além dos valores numéricos, a sintaxe de texto `x:Single` para também permite os `Infinity`tokens, `NaN` `-Infinity`e. Esses tokens são tratados como diferenciando maiúsculas de minúsculas.  
  
 `x:Single`pode dar suporte a valores no formato de notação científica, se o primeiro caractere `e` na `E`sintaxe de texto for ou.  
  
 Para a definição de especificação da linguagem XAML, consulte [ \[seções\] do MS-XAML 5.2.8 e tópico 5.4.2](https://go.microsoft.com/fwlink/?LinkId=114525).  
  
### <a name="xdouble"></a>x:Double  
 Para o backup do CLR, `x:Double` o primitivo corresponde <xref:System.Double>a.  
  
 Além dos valores numéricos, a sintaxe de texto `x:Double` para permite os `Infinity`tokens, `NaN` `-Infinity`e. Esses tokens são tratados como diferenciando maiúsculas de minúsculas.  
  
 `x:Double`pode dar suporte a valores no formato de notação científica. Use o caractere `e` ou `E` para introduzir a parte do expoente.  
  
 Para a definição de especificação da linguagem XAML, consulte [ \[seções\] do MS-XAML 5.2.9 e 5.4.3](https://go.microsoft.com/fwlink/?LinkId=114525).  
  
### <a name="xint16"></a>x:Int16  
 Para o backup do CLR, `x:Int16` o primitivo corresponde <xref:System.Int16> a `x:Int16` e é tratado como assinado. Em XAML, a ausência de uma sintaxe de`+`texto de sinal de adição () é implícita como um valor assinado positivo.  
  
 Para a definição de especificação da linguagem XAML, consulte [ \[seções\] do MS-XAML 5.2.11 e 5.4.5](https://go.microsoft.com/fwlink/?LinkId=114525).  
  
### <a name="xint32"></a>x:Int32  
 Para o backup do CLR, `x:Int32` o primitivo corresponde <xref:System.Int32>a. `x:Int32`é tratado como assinado. Em XAML, a ausência de uma sintaxe de`+`texto de sinal de adição () é implícita como um valor assinado positivo.  
  
 Para a definição de especificação da linguagem XAML, consulte [ \[seções\] do MS-XAML 5.2.12 e 5.4.6](https://go.microsoft.com/fwlink/?LinkId=114525).  
  
### <a name="xint64"></a>x:Int64  
 Para o backup do CLR, `x:Int64` o primitivo corresponde <xref:System.Int64>a. `x:Int64`é tratado como assinado. Em XAML, a ausência de uma sintaxe de`+`texto de sinal de adição () é implícita como um valor assinado positivo.  
  
 Para a definição de especificação da linguagem XAML, consulte [ \[seções\] do MS-XAML 5.2.13 e 5.4.7](https://go.microsoft.com/fwlink/?LinkId=114525).  
  
### <a name="xtimespan"></a>x:TimeSpan  
 Para o backup do CLR, `x:TimeSpan` o primitivo corresponde <xref:System.TimeSpan>a.  
  
 Observe que a análise de XAML para o formato de data e hora é inerentemente feita em `en-US` cultura.  
  
 Para a definição de especificação da linguagem XAML, consulte [ \[seções\] do MS-XAML 5.2.16 e 5.4.10](https://go.microsoft.com/fwlink/?LinkId=114525).  
  
### <a name="xuri"></a>x:Uri  
 Para o backup do CLR, `x:Uri` o primitivo corresponde <xref:System.Uri>a.  
  
 A verificação de protocolos não faz parte da definição XAML para `x:Uri`.  
  
 Para a definição de especificação da linguagem XAML, consulte [ \[seções\] do MS-XAML 5.2.15 e 5.4.9](https://go.microsoft.com/fwlink/?LinkId=114525).  
  
### <a name="xbyte"></a>x:Byte  
 Para o backup do CLR, `x:Byte` o primitivo corresponde <xref:System.Byte>a. Um <xref:System.Byte>  /  é tratado como nãoassinado.`x:Byte`  
  
 Para a definição de especificação da linguagem XAML, consulte [ \[seções\] do MS-XAML 5.2.10 e 5.4.4](https://go.microsoft.com/fwlink/?LinkId=114525).  
  
### <a name="xarray"></a>x:Array  
 Para o backup do CLR, `x:Array` o primitivo corresponde <xref:System.Array>a.  
  
 Você pode definir uma matriz em XAML 2006 usando uma sintaxe de extensão de marcação; no entanto, a sintaxe XAML 2009 é um primitivo definido por linguagem que não requer acesso a uma extensão de marcação. Para obter mais informações sobre o suporte a XAML 2006, consulte [extensão de marcação x:array](x-array-markup-extension.md).  
  
 Para a definição de especificação da linguagem XAML, consulte [ \[as\] seções do MS-XAML 5.2.18](https://go.microsoft.com/fwlink/?LinkId=114525).  
  
<a name="wpf_support"></a>   
## <a name="wpf-support"></a>Suporte do WPF  
 No WPF, você pode usar os recursos do XAML 2009, mas somente para XAML que não seja compilado por marcação. O XAML com compilação de marcação para WPF e a forma de BAML do XAML atualmente não dão suporte às palavras-chave e aos recursos do XAML 2009.  
  
 Um cenário em que você pode usar recursos XAML 2009 junto com o WPF é se você criar um XAML livre e, em seguida, carregar esse XAML em um grafo <xref:System.Windows.Markup.XamlReader.Load%2A?displayProperty=nameWithType>de tempo de execução e de objeto do WPF com. O WPF <xref:System.Windows.Markup.XamlReader?displayProperty=nameWithType> e seu <xref:System.Windows.Markup.XamlReader.Load%2A> pode processar palavras-chave de linguagem XAML 2009 e recursos em uma representação de grafo de objeto válido.
