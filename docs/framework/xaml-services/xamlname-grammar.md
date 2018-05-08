---
title: Gramática XamlName
ms.date: 03/30/2017
helpviewer_keywords:
- DottedXamlName grammar [XAML Services]
- grammar [XAML Services], DottedXamlName
- grammar [XAML Services], XamlName
- names in XAML [XAML Services]
- XamlName grammar [XAML Services]
ms.assetid: 11e4cada-41d2-494d-9531-0d3df4dfcbe3
ms.openlocfilehash: 32fd7b7b952ebbc853e41c0a8276d1ab487e619f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="xamlname-grammar"></a>Gramática XamlName
Gramática XamlName é uma gramática específica que está definida na especificação de linguagem XAML [MS-XAML], que é reproduzida aqui por conveniência.  
  
## <a name="from-the-xaml-specification"></a>Da especificação XAML.  
 A especificação de [MS-XAML] define a gramática XamlName para identificar o conjunto de identificadores simbólicos legais utilizados para tipos e propriedades.  
  
 Cadeia de caracteres valores que são do tipo XamlName deve estar de acordo com a gramática a seguir:  
  
```  
XamlName ::= NameStartChar ( NameChar )*   
NameStartChar ::= LetterCharacter | '_'   
NameChar ::= NameStartChar | DecimalDigit | CombiningCharacter   
LetterCharacter ::= UnicodeLu | UnicodeLl | UnicodeLo | UnicodeLt | UnicodeNl   
DecimalDigit ::= UnicodeNd   
CombiningCharacter ::= UnicodeMn | UnicodeMc  
```  
  
 Que assume os seguintes valores de categoria geral, conforme definido no banco de dados de caractere Unicode  
  
```  
Lu  
Letter, Uppercase  
Ll  
Letter, Lowercase  
Lt  
Letter, Titlecase  
Lm  
Letter, Modifier  
Lo  
Letter, Other  
Mn  
Mark, Non-Spacing  
Mc  
Mark, Spacing Combining  
Nd  
Number, Decimal  
Nl  
Number, Letter  
```  
  
 XAML define uma segunda gramática, DottedXamlName, que é usado para a propriedade e evento referências qualificadas e também membros anexos. Para obter mais informações, consulte <xref:System.Windows.DependencyProperty> e [visão geral de XAML (WPF)](../../../docs/framework/wpf/advanced/xaml-overview-wpf.md).  
  
 Cadeia de caracteres valores que são do tipo XamlName deve estar de acordo com a gramática a seguir:  
  
```  
DottedXamlName ::= XamlName '.' XamlName  
```  
  
## <a name="remarks"></a>Comentários  
 Para a especificação completa, consulte [ \[XAML MS\]](http://go.microsoft.com/fwlink/?LinkId=114525).
